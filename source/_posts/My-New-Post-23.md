---
title: 2021年4月2日
date: 2021-04-02 21:40:55
categories: 
    - R语言
tags: 
    - 编程
    - NLP
comments: true
---

开始学习R语言啰，感觉比Python简单好多。感谢被Python狂虐的时光。

<center><mark>以下是今天安装和使用的步骤</mark></center>

1. [安装使用参考网址](https://bookdown.org/qiyuandong/intro_r/)
2. [x] [XQuartz-2.8.0.dmg](https://www.xquartz.org/)安装
3. [x] [R 4.0.5](https://cran.r-project.org/)安装
4. [x] [R studio](https://www.rstudio.com/products/rstudio/download/#download)安装
5. [x] issue的解决
    - 开始执行，出现问题：`WARNING: You're using a non-UTF8 locale, therefore only ASCII`
    - [参考网页](https://stackoverflow.com/questions/9689104/installing-r-on-mac-warning-messages-setting-lc-ctype-failed-using-c)，解决方式参考第一个回答
    - 终端输入`defaults write org.R-project.R force.LANG en_US.UTF-8`，重启R语言软件，解决


&nbsp;

<center><mark>学习进度</mark></center>

2 新手上路 R Basics 1
2.1 [x] R的数学运算：
2.2 [x] 赋值
2.3 [x] 使用 ? or help() 查询
2.4 [x] 功能包
2.5 [x] 查看路径和设置路径
2.6 [x] 数据类型
2.7 [x] 数据结构
2.8 [x] 常用函数


&nbsp;

<center><mark>2021年4月27日</mark></center>

顺便存一下`R语言`积累的代码，也算是学到`Text Analysis with R`的`Chapter 5`了。

```
text_v <- scan("~/Documents/TAWR2/data/text/melville.txt", what = "character", sep = "\n")

text_v <- scan("~/Documents/TAWR2/data/text/melville.txt", what="character", sep="\n") 
start_v <- which(text_v == "CHAPTER 1. Loomings.") 
novel_lines_v <- text_v[start_v:length(text_v)] 
novel_v <- paste(novel_lines_v, collapse = " ") 
novel_lower_v <- tolower(novel_v) 
moby_words_l <- strsplit(novel_lower_v,"\\W") 
moby_word_v <- unlist(moby_words_l) 
not_blanks_v <- which(moby_word_v != "") 
moby_word_v <- moby_word_v[not_blanks_v]

num_vector_v <- c(1, 2, 3, 4, 5) 
num_vector_v * 10

plot(
  sorted_moby_rel_freqs_t[1:10], type = "b", 
  xlab = "Top Ten Words in Moby Dick", 
  ylab = "Percentage of Full Text", 
  xaxt = "n"
  ) 
axis( 
  1, 1:10, 
  labels = names(sorted_moby_rel_freqs_t [1:10])
  )

text_v <- scan("~/Documents/TAWR2/data/text/melville.txt", what = "character", sep = "\n") 
start_v <- which(text_v == "CHAPTER 1. Loomings.") 
novel_lines_v <- text_v[start_v:length(text_v)] 
novel_v <- paste(novel_lines_v, collapse = " ") 
novel_lower_v <- tolower(novel_v) 
moby_words_l <- strsplit(novel_lower_v, "\\W")
moby_word_v <- unlist(moby_words_l) 
not_blanks_v <- which(moby_word_v != "") 
moby_word_v <- moby_word_v[not_blanks_v]

plot( 
  w_count_v, 
  main = "Dispersion Plot of 'whale' in Moby Dick", 
  xlab = "Novel Time", 
  ylab = "whale", 
  type = "h", 
  ylim = c(0, 1), 
  yaxt = 'n'
  )

ahabs_v <- which(moby_word_v == "ahab") # find 'ahab' 
a_count_v <- rep(NA, length(n_time_v))
# change 'w' to 'a' to keep whales and ahabs in separate variables 
a_count_v[ahabs_v] <- 1 # mark the occurrences with a 1 
plot( 
  a_count_v, 
  main = "Dispersion Plot of 'ahab' in Moby Dick", 
  xlab = "Novel Time", 
  ylab = "ahab", 
  type = "h", 
  ylim = c(0, 1), 
  yaxt = 'n'
  )

whale_hits <- grep(
  "whale|whales|whale's|monster|leviathan", moby_word_v 
  ) 
ahab_hits <- grep(
    "ahab|ahabs|ahab's|captain", moby_word_v
  )

length(whales_v); length(whale_hits)
## [1] 1150 ## [1] 1746 
length(ahabs_v); length(ahab_hits)
## [1] 511
## [1] 863

eg_v <- "this is a _test_ to see if we can keep ahab's and other words such as contractions like can't and ain't. it will also allow us to see some other oddities." 
strsplit(eg_v, "\\W")

strsplit(eg_v, "[^A-Za-z0-9']")

text_v <- scan("~/Documents/TAWR2/data/text/melville.txt", what = "character", sep = "\n") 
start_v <- which(text_v == "CHAPTER 1. Loomings.") 
novel_lines_v <- text_v[start_v:length(text_v)] 
novel_v <- paste(novel_lines_v, collapse=" ") 
novel_lower_v <- tolower(novel_v)
moby_words_l <- strsplit(novel_lower_v, "[^A-Za-z0-9']") 
moby_word_v <- unlist(moby_words_l) 
not_blanks_v <- which(moby_word_v != "") 
moby_word_v <- moby_word_v[not_blanks_v]

whale_hits_new <- grep(
  "whale|whales|whale's|monster|leviathan", moby_word_v 
  ) 
ahab_hits_new <- grep(
    "ahab|ahabs|ahab's|captain", moby_word_v
  )

whale_varients_v <- moby_word_v[whale_hits_new] 
ahab_varients_v <- moby_word_v[ahab_hits_new]

length(which(whale_varients_v == "whale"))
## [1] 1030 
length(grep("whale", whale_varients_v))
## [1] 1585
```