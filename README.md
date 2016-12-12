# 一些常用的函数

## 数组去重

```
1. function unique(arr){
  return Array.from(new Set(arr))
}

function unique(arr){
  return [...new Set(arr)]
}

2. function unique(arr){
  let tempArr = []
  arr.map((v)=>{
    if(!(v in tempArr)){
      tempArr[tempArr.length] = v
    }
  })  
  return tempArr
}
```

当然还有很多其他的写法

## 获取随机颜色值

```
function getRandomColor(){
  let color = '#',
      letters = '0123456789abcdef'
  for(let i = 0;i<6;i++){
    color += letters[Math.round(Math.random() * letters.length)]
  }    
  return color
}
```

## 数组乱序

```
function shuffle(arr) {
    for (let i = arr.length; i; i--) {
        let j = Math.floor(Math.random() * i);
        [arr[i - 1], arr[j]] = [arr[j], arr[i - 1]];
    }
}
```

## 数字求和

```
function forSum(n){
  if(typeof n !== 'number'){
    return
  }
  let sum = 0
  for(n;n >= 1;n--){
    sum += n
  }
  return sum
}
```

## 冒泡排序

```
function bubbleSort(arr){
  for(let i = 0;i<arr.length-1;i++){
    for(let j = i +1; j < arr.length;j++){
      let cur = arr[i],next = arr[j]
      if(cur > next){
        arr[i] = next
        arr[j] = cur   
      }
    }
  }
  return arr
}
```
<<<<<<< HEAD
##字符串重复
```
String.prototype.repeatify = String.prototype.repeatify ||
function(n){
  if(typeof n !== 'number') return
  let str =''
  for(let i=0;i<n;i++){
      str += this
  }
  return str
}
=======

## 对象深拷贝

```
function deepCopy(parent,child){
  child = child || {}
  if(typeof parent !== 'object'){
    return
  }  
  for(let item in parent){
    if(parent.hasOwnProperty(item)){
      if(typeof p[item] === 'object'){
        child[item] = Array.isArray(parent[item])? [] : {}
        deepCopy(parent[item],child[item])   
      }else{
        child[item] = parent[item]
      }
    }
  }
  return child
}
```
## 变量交换
```
function change(a,b){
  return  [a,b] = [b,a]
}
```
## 寻找数组中最大值与最小值得差值
```
function diff(arr){
  return Math.max(...arr) - Math.min(...arr)
}
```
## 获取n天前/后的日期
```
function getDayBeforeAfter(date,type,days){
  date = date || new Date()
  type = type || 'after'
  days = days || 1

  if(!(date instanceof Date)){
    if(date.indexOf('-') != -1){
      date.replace(/\-/g,'/')
    }
    date = new Date(date)
  }
  let newDate = date
  switch (type){
    case "after":
        newDate = new Date(date.getTime() + (days * 24 * 60 * 60 * 1000))      
        break  
    case "before":
        newDate = new Date(date.getTime() - (days * 24 * 60 * 60 * 1000))
        break  
  }
  return `${newDate.getFullYear()}/` + `${newDate.getMonth() + 1}/` + `${newDate.getDate()}`
}
```
## 使用Promise对象处理ajax请求
```
function promiseAjax(url){
  return new Promise(function(resolve,reject){
    const xhr = new XMLHttpRequest()
    xhr.open('GET',url,true)
    xhr.onload = function(){
      if(xhr.status >= 200 && xhr.status < 400 ){
        let data = JSON.parse(xhr.responseText)
        resovle(data)
      }else{
        reject(new Error(xhr.statusText))
      }
    }
    xhr.onerror = function(){
      reject(new Error(xhr.statusText))
    }
    xhr.send()
  })
}
let URL = 'http://news-at.zhihu.com/api/4/news/latest'
promiseAjax(URL).then(function(data){
  console.log(data)
}).catch(function(err){
  console.log(err)
})
>>>>>>> 37ca0f9772db1414524106a8f34aa87f5122c705
```
