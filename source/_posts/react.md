---
title: react的一些技巧
date: 2021-09-23 14:37:00
tags:
image: './image/wallhaven-x8jx7v.jpg'
---

# showComponentUpdate
```
showComponentUpdate(nextProps, nextState){
    if(nextProps.content !== this.props.content){
        return true;
    } else {
        return false;
    } 
}
```
React 组件中 父组件在渲染时会带动子组件进行渲染，在子组件中加入这段代码可防止子组件进行重新渲染，提高性能

# EasyMock
使用easyMock