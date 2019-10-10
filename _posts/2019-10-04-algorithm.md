---
layout: post
title:  "2019 09 카카오 코딩 테스트"
date:   2019-09-08 14:00:00 +0900
categories: 코딩테스트
tag: kakao, algorithm
comments : true
---

# 문제 풀러 가기

https://tech.kakao.com/2019/10/02/kakao-blind-recruitment-2020-round1/

# 1번 문제 풀이

## 석원
```
function solution(s) {
    var answer = 0;
    let iteration = s.length/2;
    let compressed = [];

    for(var i = 1; i <= iteration; i++){
        let number = [];
        let chars = [];
        let compressing = s;
        chars.push(compressing.slice(0,i));
        number.push(1);
        compressing = compressing.slice(i);
        //console.log('start here',number, chars,compressing, i);
        while(compressing.length >= i){
            if(chars[chars.length-1] == compressing.slice(0,i)){
                number[number.length-1]++;
            }
            else{
                number.push(1);
                chars.push(compressing.slice(0,i));
            }
            compressing = compressing.slice(i);
            //console.log(compressing, number, chars, i)
        }
        if(compressing.length > 0){
            chars[chars.length-1]+=compressing;
        }
        console.log(number, chars);
        let temp = '';
        for(var j = 0; j < number.length; j++){
            if(number[j] == 1){
                temp+=chars[j];
            }
            else{
                temp+=number[j].toString();
                temp+=chars[j];
            }
            //console.log('temp', temp);
        }
        compressed.push(temp);

    }
    console.log(compressed);
    compressed.sort(function(a,b){
        return a.length - b.length;
    })
    answer = compressed[0].length;
    return answer;
}
```

# 2번 문제 풀이

## 석원
```
function solution(p) {
    var answer = '';
    var u = '';
    var v = '';
    if(p == ''){
        return answer;
    }
    for(let j = 1; j <= p.length; j++){
        u = p.slice(0,j);
        v = p.slice(j);
        if(balance(u)){
            console.log('uv',u,v,j);
            break;
        }
        else{
            continue;
        }
    }

    if(!isBalanced(u)){
        let temp = u;
        let ghost = '(';
        ghost += this.solution(v);
        ghost += ')';
        u=u.slice(1,-1);
        for(let i = 0; i <= u.length-1; i++){
            if(u[i] == '('){
                u = replaceAt(u,i,')');
            }
            else{
                u = replaceAt(u,i,'(');
            }
        }
        ghost+=u;
        answer = ghost;
        console.log('answer u',answer);
        return answer;
    }
    else{
        answer = u+this.solution(v);
        console.log('answer v', answer);
        return answer;
    }
}
function balance(s){
    let b = [0,0];
    if(s.length%2!=0){
        return false;
    }
    for(let i = 0; i < s.length; i++){
        if(s[i] == '('){
            b[0]++;
        }
        else{
            b[1]++;
        }
    }
    if(b[0] != b[1]){
        return false;
    }
    else {
        return true;
    }
}
function replaceAt(string, index, replace) {
  return string.substring(0, index) + replace + string.substring(index + 1);
}
function isBalanced(s){
    let leftChars = [];
    for(let i = 0; i < s.length;i++){
        if(s[i] == '('){
            leftChars.push(s[i]);
        }
        else{
            if(leftChars===''){
                return false;
            }
            if(s[i] == ')' && leftChars[leftChars.length-1] != '('){
                return false;
            }
            leftChars.pop();
        }
    }
    if(leftChars.length <= 0){
        return true;
    }
    else{
        return false;
    }
}
```

# 4번 문제 풀이

## 석원
```
function solution(words, queries) {
    var answer = [];
    queries.forEach((query)=>{
        answer.push(0);
        let length = query.length;
        let findQ = query.split("?");
        if(query[0] != '?'){
            words.forEach((word)=>{
                if(word.length == length){
                    var regex = new RegExp("^"+findQ[0])
                    if(regex.test(word)){
                        answer[answer.length-1]++;
                    }
                }
            });
        }
        else{
            words.forEach((word)=>{
                if(word.length == length){
                    var regex = new RegExp(findQ[findQ.length-1]+"$")
                    if(regex.test(word)){
                        answer[answer.length-1]++;
                    }
                }
            });
        }
    })

    return answer;
}
```
