# Listen 1 (Web)
[![Software License](https://img.shields.io/badge/license-MIT-brightgreen.svg)](LICENSE)

中文 | [English](./README_EN.md)

fork from [listen1/listen1_chrome_extension](https://github.com/listen1/listen1_chrome_extension)  
[`listen1 chrome扩展版本`](https://github.com/listen1/listen1_chrome_extension)的web版，不保证所有功能都能正常使用。

## 缘起

[`listen1`](https://github.com/listen1)是一个优秀的开源项目，提供了各个平台的版本，但Web版却没直接提供，所以fork了一份chrome扩展版本，做了一些修改，使其可以直接在浏览器中打开。

已改造的音乐平台

- [x] 网易云音乐
- [x] QQ 音乐
- [x] 酷狗音乐
- [x] 酷我音乐
- [ ] bilibili
- [ ] 咪咕音乐
- [ ] 千千音乐

## 如何使用

由于请求各个音乐平台的api涉及到跨域问题，所以需要在本地搭建一个代理服务器，这里使用的是`nginx`，配置如下：
```nginx
  # 网易云音乐
  location ^~/netease/ {
    proxy_pass   https://music.163.com/;
    # 必须，不然网易云搜索接口没有返回值
    proxy_set_header Cookie "NMTID=1";
  }

  location ^~/neteaseinterface/ {
    proxy_pass   https://interface3.music.163.com/;
  }

  # QQ 音乐
  location ^~/qq/ {
    proxy_pass   https://y.qq.com/;
    proxy_set_header Referer "https://y.qq.com/";
  }
		
  location ^~/cqq/ {
    proxy_pass   https://c.y.qq.com/;
    proxy_set_header Referer "https://y.qq.com/";
  }
		
  location ^~/iqq/ {
    proxy_pass   https://i.y.qq.com/;
    proxy_set_header Referer "https://y.qq.com/";
  }
		
  location ^~/uqq/ {
    proxy_pass   https://u.y.qq.com/;
    proxy_set_header Referer "https://y.qq.com/";
  }

  # 酷狗音乐
  location ^~/kugou/ {
    proxy_pass   https://www.kugou.com/;
    proxy_set_header Referer "https://www.kugou.com/";
  }
		
  location ^~/kugoum/ {
    proxy_pass   https://m.kugou.com/;
    proxy_set_header User-Agent "Mozilla/5.0 (iPhone; CPU iPhone OS 14_3 like Mac OS X) AppleWebKit/534.30 (KHTML, like Gecko) Version/4.0 Mobile Safari/534.30";
  }
		
  location ^~/kugousearch/ {
    proxy_pass   https://songsearch.kugou.com/;
    proxy_set_header Referer "https://www.kugou.com/";
  }
		
  location ^~/kugoumobile/ {
    proxy_pass   http://mobilecdnbj.kugou.com/;
    proxy_set_header Referer "https://www.kugou.com/";
  }
		
  location ^~/kugouapi/ {
    proxy_pass   https://wwwapi.kugou.com/;
    proxy_set_header Referer "https://www.kugou.com/";
  }

  # 酷我音乐
  location ^~/kuwo/ {
    proxy_pass   https://www.kuwo.cn/;
    proxy_set_header Referer "https://www.kuwo.cn/";
    proxy_set_header Origin "https://www.kuwo.cn/";
  }
  
  location ^~/kuwoanti/ {
    proxy_pass   https://antiserver.kuwo.cn/;
    proxy_set_header Referer "https://www.kuwo.cn/";
  }
  
  location ^~/kuwom/ {
    proxy_pass   https://m.kuwo.cn/;
    proxy_set_header Referer "https://www.kuwo.cn/";
  }
  
  location ^~/kuwosearch/ {
    proxy_pass   https://search.kuwo.cn/;
    proxy_set_header Referer "https://www.kuwo.cn/";
  }
  
  location ^~/kuwonpl/ {
    proxy_pass   https://nplserver.kuwo.cn/;
    proxy_set_header Referer "https://www.kuwo.cn/";
  }
```

随后在浏览器中打开如`http://{ip}:{port}/`即可。

## License

MIT
