空的 Gitbook 範本
=================

基本概念是利用 Github 的 gh-pages 架設 Gitbook

但是我們會希望一旦我們編輯 Markdown 檔案時，線上的 Gitbook 會自動更新

所以我們採用 travis 作為自動更新的手段，並且把 build 好的 Gitbook push 到 gh-pages branch

但是要自動 push 的話我們需要使用 Github token 做身份驗證

但是 travis 上不適合放上明文的 token，所以我們需要先加密 token 


基本步驟如下：
1. Fork 這個專案，或是 clone 在修改 up-stream
2. 建立 Github token
    * https://github.com/settings/tokens/new
    * 只要勾選 public_repo 即可
3. 使用 travis 加密 token 與帳號資訊
    * 刪除 .travis.yml 的 env -> global -> secure 部分
    * `travis encrypt 'GIT_NAME=[USER-NAME] GIT_EMAIL=[USER-EMAIL] GH_TOKEN=[剛剛的Token]] GH_REPO=[pdis/gitbook-template]' --add`
    * GH_REPO=[pdis/gitbook-template] 要記得改成自己的
    * run 完指令後可打開 .travis.yml 確認是否有 env -> global -> secure
4. 設定 travis
    * https://travis-ci.org/profile/[GITHUB帳號]
5. push Gitbook 內容上 remote repo 即可
