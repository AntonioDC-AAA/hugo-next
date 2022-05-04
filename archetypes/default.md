---
title: "{{ .TranslationBaseName | title }}"
url: "{{ dateFormat "2006-01-01" .Date }}/{{ lower (substr .TranslationBaseName 6) }}.html"
date: "{{ .Date }}"
draft: false
categories:
 - "xx"
tags:
 - "xxx"
 - "xxx"
toc: true
---
