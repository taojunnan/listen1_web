# Listen 1 (Web)
[![Software License](https://img.shields.io/badge/license-MIT-brightgreen.svg)](LICENSE)

[中文](./README.md) | English

fork from [listen1/listen1_chrome_extension](https://github.com/listen1/listen1_chrome_extension)  
Web version for [`listen1 chrome extension`](https://github.com/listen1/listen1_chrome_extension)

## Begin

now you can use

- [x] Netease
- [x] QQ
- [x] Kugou
- [x] Kuwo
- [ ] Bilibili
- [ ] Migu
- [ ] Qianqian (taihe)

## How to use

set up an nginx reverse proxy, like this:
```nginx
  # Netease
  location ^~/netease/ {
    proxy_pass   https://music.163.com/;
    # necessary
    proxy_set_header Cookie "NMTID=1";
  }

  location ^~/neteaseinterface/ {
    proxy_pass   https://interface3.music.163.com/;
  }

  # QQ
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

  # Kugou
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

  # Kuwo
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

then open `http://{ip}:{port}/` in your browser.

## License

MIT
