1.  前面先用github desk git clone cv86092.github.io
2.  我要先測試要放md還是html檔上github , 才會讓markdown and mermaid 秀出來
    * 我先直接內嵌bootstrap , markdown 在 html 但不會顯示出來
    ```
        <!DOCTYPE html>
        <html lang="en">
        <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1">
        <title>Bootstrap 5 Sidebar Example</title>
        
        <!-- Bootstrap 5 CSS -->
        <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0-alpha1/dist/css/bootstrap.min.css" rel="stylesheet">

        </head>
        <body>
        ## This is markdown syntax
        ### This is also a markdown syntax


        <!-- Bootstrap 5 JS and dependencies -->
        <script src="https://cdn.jsdelivr.net/npm/@popperjs/core@2.11.6/dist/umd/popper.min.js"></script>
        <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0-alpha1/dist/js/bootstrap.min.js"></script>
        
        </body>
        </html>

    ```
    *顯示結果   
    ```## This is markdown syntax ### This is also a markdown syntax```

    -->md 檔裡面包含markdown 和 mermaid 無法由xxx.github.io/xxx.md 跑出來   
    -->但可以從github repository 點檔案出來看就會支援mermaid 和 markdown    
    -->`但如果xxx.md 直接用xxx.github.io/xxx.html ` 改掉副檔名變成html , markdown 可以跑出來，但沒辦法跑出mermaid



3.  `最後我使用hackmd` ，有什麼好處?    
      * 可以跟github sync 
      * 可以讓markdown 的大標直接變成目錄，登入hackmd 後可以直接看到    
      * 好像就只是放在網頁上可以給人看到
      * 結果直接在github 上面就可以用目錄式的看到了，覺得很無聊
      * 我覺得我**很智障**，別人要搞一個小時的東西我可以花很多時間在那個上面
      * **現在好啦，一直叫別人寫gitbook，結果現在在readme.md 就 可以辦到了，那現在要幹嘛~?**

    