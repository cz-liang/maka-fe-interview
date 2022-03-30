# 空格替换

已知一段 html 格式的字符串，实现 replaceWhitespace 函数将其内容的空格替换成 &nbsp;
注意：html tag 标签中的空格不要替换
```js
const content = `<body><div style="padding: 1px">12           3</div></body>`

function replaceWhitespace(htmlStr: string): string {}

replaceWhitespace(content)
// 输出结果 <body><div style="padding: 1px">12&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;3</div></body>
```
typescript解答：
```js
const content : string = `<body><div style="padding: 1px">12           3</div></body>`

function replaceWhitespace(htmlStr : string): string {
    let arr: string[] = htmlStr .split('')
    let new_arr: string[] = []
    let new_str: string = ``
    for(let i = 0;i<arr.length;i++) {
        if(arr[i] === '<') new_arr.push(arr[i])
        if(arr[i] === '>') new_arr = []
        if(arr[i] === ' ' && new_arr.length === 0) {
            new_str = new_str + `&nbsp;`
        }else {
            new_str = new_str + arr[i]
        }
    }
    return new_str
}
let result: string = replaceWhitespace(content)
console.log(result)
```
解答思路：html字符串转数组，遍历数组，遇到<>标签，直接拼接字符串，不在<>包含内的转空格为`$nbsp;`
