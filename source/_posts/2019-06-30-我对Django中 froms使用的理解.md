---
title: 我对 Django 中 froms 使用的理解
date: 2019-06-30 22:10:37
tags: [python, django]
---
这篇文章谈一下我对 Django 中 forms的简单理解，确切的说像是一种代码的说明。

我觉得 Django 中的forms 就是view用与渲染成html语言的代码。用来帮助我们减少写html的工作量。

下面的代码就是本博客实现评论功能的forms。

    from django import forms
    from .models import Comment
    
    import mistune
    
    
    class CommentForm(forms.ModelForm):
        nickname = forms.CharField(
            label='昵称',
            max_length=50,
            widget=forms.widgets.Input(
                attrs={'class': 'form-control', 'style': 'width: 60%;'}
            )
        )
        email = forms.CharField(
            label='Email',
            max_length=50,
            widget=forms.widgets.Input(
                attrs={'class': 'form-control', 'style': 'width: 60%;'}
            )
        )
    
        website = forms.CharField(
            label='网站',
            max_length=100,
            widget=forms.widgets.URLInput(
                attrs={'class': 'form-control', 'style': 'width: 60%;'}
            )
        )
    
        content = forms.CharField(
            label='内容',
            max_length=500,
            widget=forms.widgets.Textarea(
                attrs={'row': 6, 'class': 'form-control'}
            )
        )
    
        def clean_content(self):
            content = self.cleaned_data.get('content')
            if len(content) < 10:
                raise forms.ValidationError('内容长度太短了！')
            content = mistune.markdown(content)
            return content
        
        class Meta:
            model = Comment
            fields = ['nickname', 'email', 'website', 'content']
           
    
    
下面我一段一段的解释一下：

    from django import forms  # 导入 forms 模块
    from .models import Comment  # 导入Comment模型，评论的需要填写的字段均来自于此
    
    import mistune  # 导入 mistune 模块，为了使评论支持markdown语法
    class CommentForm(forms.ModelForm):  # 我们写的CommentForm 继承了forms模块中的ModelForm类
        nickname = forms.CharField(  # 这里我们对模型中的每一个字段对应的表单进行设置
            label='昵称',  # 这里对应html label标签中的文字
            max_length=50,  # 设置表单中填写的最大长度
            widget=forms.widgets.Input(  # 设置html中的标签类型为input
                attrs={'class': 'form-control', 'style': 'width: 60%;'}  # 规定input的样式
            )
        )

    def clean_content(self):  # 判断评论长度和表单数据验证
            content = self.cleaned_data.get('content')
            if len(content) < 10:
                raise forms.ValidationError('内容长度太短了！')
            content = mistune.markdown(content)
            return content

    class Meta:  # 规定类的元数据
            model = Comment  
            fields = ['nickname', 'email', 'website', 'content']