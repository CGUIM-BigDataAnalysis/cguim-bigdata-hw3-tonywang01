長庚大學 大數據分析方法 作業三
================

網站資料爬取
------------

``` r
#這是R Code Chunk
#install.packages("rvest")
#install.packages("XML")
#install.packages("knitr")
#install.packages("rmarkdown")
library(rvest) 
```

    ## Warning: package 'rvest' was built under R version 3.3.3

    ## Loading required package: xml2

``` r
pttTech1<-NULL
pttTech<-"https://www.ptt.cc/bbs/Tech_Job/index.html"
pttTechContent<-read_html(pttTech)
post_title <- pttTechContent %>% html_nodes(".title") %>% html_text()
post_NumPush<- pttTechContent %>% html_nodes(".nrec") %>% html_text()
post_author<- pttTechContent %>% html_nodes(".author") %>% html_text()
pttTech1<-data.frame(post_title,post_NumPush,post_author)
for(i in 1:10)
{
library(rvest)
post_front<- pttTechContent %>% html_nodes(".btn") %>% html_attr("href")
pttTech<-paste0("https://www.ptt.cc",post_front[4])
pttTechContent<-read_html(pttTech)
post_title <- pttTechContent %>% html_nodes(".title") %>% html_text()
post_NumPush<- pttTechContent %>% html_nodes(".nrec") %>% html_text()
post_author<- pttTechContent %>% html_nodes(".author") %>% html_text()
pttTech2<-data.frame(post_title,post_NumPush,post_author)
pttTech1<-rbind(pttTech1,pttTech2)
}
```

爬蟲結果呈現
------------

``` r
#這是R Code Chunk
library(knitr)
```

    ## Warning: package 'knitr' was built under R version 3.3.3

``` r
knitr::kable(pttTech1) 
```

| post\_title                                                     | post\_NumPush | post\_author |
|:----------------------------------------------------------------|:--------------|:-------------|
| \[請益\] 台積RD工程師                                           | 2             | darkdanger   |
| \[討論\] 亞瑟萊特/興訊/世平/陸聯/宣昶/旭德/雍智                 |               | catdogter    |
| \[討論\] MTK的研發能力                                          | 35            | yohowo       |
| \[新聞\] 五角大廈警告：阿里巴巴等中資6年砸近兆臺幣 資助矽谷新秀 | 6             | AAAB         |
| \[請益\] 關於進公司後的第一份薪水                               | 13            | henry8168    |
| \[請益\] 世界先進-廠務工程師                                    | 2             | hank5115     |
| (本文已被刪除) \[magic704226\]                                  | 4             | -            |
| Re: \[討論\] MTK的研發能力                                      | 8             | pponywong    |
| \[新聞\] 英特爾：GPU已過時，Nvidia的人工智慧之                  | 6             | lazy321      |
| \[討論\] 關於同公司內部轉調                                     | 2             | Ferrara      |
| Re: \[討論\] MTK的研發能力                                      | 1             | ftrain       |
| \[公告\] 停止'年薪高但被砍月薪或是月薪' 討論串                  |               | mmkntust     |
| 律師為您解惑－線上勞動法免費諮詢即日為勞工 …                    | 爆            | pzs          |
| \[公告\] Tech\_Job板板規 2014.03.01                             | 7             | mmkntust     |
| \[公告\] 置底 檢舉/推薦 文章                                    | 爆            | mmkntust     |
| \[免費\]工作人生顧問                                            | 爆            | zodiac       |
| \[請益\] 林口美光 台中美光                                      | 16            | lponnn       |
| Re: \[請益\] 年薪高但被砍月薪或是月薪高的選擇                   |               | inji         |
| \[請益\] Zestron這間有人聽說過嗎?                               |               | roryman      |
| Re: \[請益\] 年薪高但被砍月薪或是月薪高的選擇                   | 7             | Ommm5566     |
| \[請益\] 美光RDA(real time defect analysis)                     | 16            | WEIRUNTSAO   |
| Re: \[請益\] 年薪高但被砍月薪或是月薪高的選擇                   |               | oneheat      |
| Re: \[請益\] 年薪高但被砍月薪或是月薪高的選擇                   | 7             | shinza       |
| \[請益\] 【請益】聯發科 軟韌體測試工程師(約聘)                  | 10            | similarsmile |
| \[新聞\] 中科徵才台積電徵150名操作員 千人面試                   | 24            | alterna      |
| (本文已被刪除) \[imch543\]                                      | 1             | -            |
| \[請益\] 美光是不是很不錯阿???                                  | 24            | wer11        |
| (本文已被刪除) \[LongRanger\]                                   |               | -            |
| \[徵才\] 開酷科技徵雷達系統工程主管                             |               | lucyyu       |
| (本文已被刪除) \[ggggggh\]                                      |               | -            |
| Fw: \[討論\] 稅金疑問                                           | 2             | ggggggh      |
| \[討論\] MTK現在還值得去嗎?                                     | 56            | Laplace5566  |
| (本文已被刪除) \[kingfsg7326\]                                  |               | -            |
| \[討論\] 特助這職位的功用？                                     | 29            | a78914124    |
| \[請益\] 美商蕎鑫 品保工程師&RD製程/樣品工程師                  | 1             | iamholan     |
| \[新聞\] 台積電本月開始生產蘋果A11處理器，第2季達到最高6萬      | 19            | DickMartin   |
| \[請益\] 國喬石化公司 研發工程師筆試與面談                      | 11            | sanford888   |
| \[請益\] 台積MTC工程師                                          | 22            | Maora        |
| (已被mmkntust刪除) <BG89> 版規一                                |               | -            |
| Re: \[請益\] 年薪高但被砍月薪或是月薪高的選擇                   | 12            | DrTech       |
| \[請益\] 系統廠SW/FW的轉職方向                                  | 8             | heerodream   |
| (本文已被刪除) \[lululun\]                                      | 1             | -            |
| Re: \[請益\] 年薪高但被砍月薪或是月薪高的選擇                   | 6             | baseband112  |
| \[新聞\] 中信銀 深耕數位創新服務                                |               | AAAB         |
| Re: \[請益\] 年薪高但被砍月薪或是月薪高的選擇                   | 44            | tw689        |
| \[新聞\] 東芝半導體恐侵犯旺宏專利、ITC將著手調                  |               | cychine      |
| Re: \[請益\] 年薪高但被砍月薪或是月薪高的選擇                   | 1             | ggggggh      |
| \[請益\] HTC business analyst 一面準備方向                      |               | the4days     |
| \[新聞\] 日商來台徵工程師 年薪164萬起                           | 4             | zzzz8931     |
| Re: \[請益\] 年薪高但被砍月薪或是月薪高的選擇                   | 5             | SMIC5566     |
| \[新聞\] 台積電共同執行長魏哲家 當選TSIA理事長                  | 4             | cychine      |
| \[討論\] 海邊發股票的問題                                       | 13            | su27         |
| \[請益\] 美光的黃光製程工程師                                   | 26            | toaste791214 |
| (本文已被刪除) \[screwup\]                                      | 6             | -            |
| \[新聞\] 中科科技大廠聯合徵才 釋出1934職缺                      | 6             | zwitter      |
| Re: \[請益\] 年薪高但被砍月薪或是月薪高的選擇                   | 8             | baseband112  |
| \[討論\] 今年IC設計是不是很難進                                 | 21            | yian820508   |
| \[請益\] 華勻整合 日文翻譯                                      | 1             | mizunopro214 |
| \[請益\] 機械 自控組 offer請益 志聖 歐益                        | 2             | x246libra    |
| \[請益\] offer選擇 (南日月光/華新科)                            | 6             | basketball08 |
| \[請益\] 面試 文曄 VSR採購管理師，CSR訂單管理師                 | 5             | Lamigirl     |
| \[徵才\] 法務部調查局/科技發展計畫 碩士級研究助理               | 2             | weiwei0306   |
| \[請益\] 信邦電子 業務工程師                                    | 3             | bertsandy    |
| \[新聞\] 三星估Q1獲利飆48%　S8更將助本季創新高                  | 3             | cychine      |
| Re: \[新聞\] 晶圓代工誰技術領先？ 英特爾：我最強                | 8             | quartzr      |
| \[聘書\] offer選擇 康寧/ASML                                    | 43            | twinkler     |
| (已被mmkntust刪除) <yens1> 版規六                               | 6             | -            |
| \[請益\] IC design的世界 哪些是HW可以轉的?                      | 14            | endurant     |
| \[請益\] 凌群電腦的現況                                         | 3             | bill12332197 |
| \[請益\] 創王光電                                               | 2             | kinoe        |
| \[新聞\] 台積電評估設廠 台水：可增水12.5萬噸                    | 22            | Lanaroh      |
| \[請益\] 年薪高但被砍月薪或是月薪高的選擇                       | 32            | tw689        |
| \[新聞\] 潘健成：不排除與友好廠商投資入股東芝半                 | 2             | cychine      |
| (本文已被刪除) \[kazamisie\]                                    | 12            | -            |
| \[討論\] 大家都是下一份薪水高多少才跳?                          | 20            | endurant     |
| Re: \[請益\] 年薪高但被砍月薪或是月薪高的選擇                   | 19            | accessdenied |
| \[情報\] 自強基金會 - 半導體製程實作                            |               | a6931791     |
| \[新聞\] 鴻海併購東芝志在必得　出價逾8300億台幣                 | 26            | qazxc1156892 |
| \[請益\] 醫電鼎眾Mitcorp面試                                    | 1             | kleinerHai   |
| \[請益\] SGS                                                    | 2             | bobo30       |
| \[請益\] EMC工程師證照                                          | 3             | talon0222    |
| \[請益\] 華信光電                                               | 2             | lude71       |
| \[請益\] 美光 力成 選擇                                         | 15            | leonard123   |
| \[新聞\] 8300億豪氣出價東芝　台積電退出                         | 11            | cychine      |
| \[請益\] 關於應材面試題目                                       | 12            | sos44450     |
| \[請益\] 世界先進 超豐 選擇                                     | 8             | yukigod      |
| \[情報\] 2017外貿協會新進人員招考起跑(4/10-5/2)                 |               | SuperModel   |
| Re: \[請益\] 同事問薪水該怎麼辦                                 | 5             | ftrain       |
| Re: \[新聞\] 晶圓代工誰技術領先？ 英特爾：我最強                | 31            | chickandcow  |
| \[請益\] 駐點專約的意思                                         |               | CPU100       |
| Fw: \[爆卦\] Ptt法務部行政報告 201703---八卦板版本              | 27            | mmkntust     |
| \[問卷\] 請在科技業就職的版友們幫忙(P幣+抽獎)                   | 62            | im33024      |
| \[徵才\] 台大生機盧彥文老師實驗室誠徵專任助理                   |               | doifish312   |
| \[請益\] 名世科技                                               |               | weiyumystery |
| \[討論\] 台積DNA 這本書                                         | 19            | ballyeah5566 |
| \[請益\] 原公司 & 聯電選擇                                      | 19            | IDAY         |
| \[徵才\] 國衛院醫工奈米所/碩士級研究助理                        |               | yuxing       |
| \[請益\] 同事問薪水該怎麼辦                                     | 60            | billkaulitz  |
| Re: \[新聞\] 三星遭控侵權 中國法院判賠華為 3.5億台              |               | dakkk        |
| Re: \[請益\] 瑞昱面試請益                                       | 7             | twicm        |
| \[請益\] pmc 嘉義 自動控制工程師                                | 1             | LP111        |
| \[請益\] (代PO)約聘&正職Offer請益                               | 3             | ahhhwoo      |
| \[心得\] 台塑安衛環二面                                         | 14            | Difier       |
| Re: \[請益\] 同事問薪水該怎麼辦                                 | 12            | yamakazi     |
| \[新聞\] 明清定韜光 聯發需養晦 創新又升級                       | 13            | youkiller    |
| \[請益\] 天邁科技                                               | 1             | hibaba       |
| \[請益\] 想進台積電製程工程師                                   | 11            | ffelix1202tw |
| \[心得\] 台中康寧面試分享                                       | 15            | charlieab    |
| Re: \[新聞\] 晶圓代工誰技術領先？ 英特爾：我最強                | 20            | apoenzyme0   |
| \[新聞\] 三星吞2900多億大單　蘋果訂9200萬片OLED                 | 15            | cychine      |
| \[新聞\] 光電部門表現亮眼　光寶科Q1營收年增3%                   | 7             | qazxc1156892 |
| \[請益\] 雲創通訊(M2Comm)                                       |               | FacetheFaith |
| Re: \[新聞\] 晶圓代工誰技術領先？ 英特爾：我最強                | 16            | XXXD         |
| Re: \[新聞\]一例一休被抱怨 林全當面打臉許勝雄                   |               | coolidea     |
| \[新聞\] 三星為何能切入晶圓代工　網友這樣分析                   |               | kof70380     |
| Re: \[請益\] 同事問薪水該怎麼辦                                 | 14            | MattOrz      |
| \[請益\] 請問有人聽過廣錠嗎                                     | 2             | mioeboy      |
| \[情報\] 中科4/8產業趨勢講座－台灣美光柯經理                    |               | TaiwanJobs   |
| \[請益\] 力晶 穩懋                                              | 16            | annwi        |
| Fw: \[新聞\] 國產L牌 未發動停車庫 自燃火燒車                    |               | PauFrank5566 |
| \[請益\] offer請益抉擇駐廠台積電 VS 友良                        | 6             | hhhahhhahhha |
| \[請益\] 仙境三廠擴散製程                                       | 5             | v510520      |
| \[請益\] 台中應材客服                                           | 5             | lacio        |
| \[請益\] 瑞昱面試請益                                           | 6             | alasha828    |
| \[請益\] 遇到學經歷豐富的後進這種情形該怎麼辦~                  | 33            | st80027      |
| Re: \[請益\] 遇到學經歷豐富的後進這種情形該怎麼辦~              | 9             | Sex5F        |
| \[新聞\] 台積電赴美投資 政院經濟部環保署急滅火                  | 12            | cychine      |
| 旺宏設備問題                                                    | 3             | lucke21531   |
| Re: \[請益\] 瑞昱面試請益                                       | 25            | AlanRikkin   |
| \[請益\] 石頭 品質技術工程師 MB                                 | 8             | pamaer       |
| \[請益\] 求職建議                                               | 4             | haha58       |
| \[新聞\] 人造突觸可以自主學習                                   | 1             | ljsnonocat2  |
| Re: \[請益\] 遇到學經歷豐富的後進這種情形該怎麼辦~              | 16            | wizard7442   |
| \[請益\] 綠點捷普(彰化廠)                                       | 8             | ian5130992   |
| Fw: \[問題\] 群暉/Synology 行銷專員面試                         | 6             | dragon0518   |
| \[新聞\] 三星遭控侵權 中國法院判賠華為 3.5億台                  | 28            | Hittait      |
| \[新聞\] 到矽谷招才回流　陳良基：台灣永遠歡迎                   | 6             | zzzz8931     |
| Re: \[討論\] 三口真的這麼慘嗎?                                  |               | stennis      |
| \[情報\] 區塊鏈帶給共享經濟不一樣的價值                         |               | chunnitu     |
| \[請益\] 圓展科技機構近況                                       | 3             | thatismyway  |
| Re: \[討論\] 三口真的這麼慘嗎?                                  | 38            | DamnKobe     |
| \[討論\] 陪老外拜訪廠商當翻譯就好的缺？                         | 16            | mimi0254didi |
| \[分享\] AppWorks School iOS 第四班開始招生                     |               | jadesoul     |
| Re: \[新聞\] 矽品男員工猝死 同事質疑過勞所致                    |               | zxc0312      |
| \[新聞\] 兩大營收成長引擎失速 英特爾轉戰晶圓代                  | 13            | wahaha23     |
| \[請益\] 南亞科 測試工程師                                      | 2             | chinhao      |
| Re: \[新聞\] 到矽谷招才回流　陳良基：台灣永遠歡迎               | 6             | appledavid   |
| \[請益\] 請問有人聽過海派通訊嘛?                                | 12            | tiyico       |
| \[新聞\] 重手反擊陸廠挖角 美光傳提告百人                        | 24            | cychine      |
| \[討論\] 三星為何能切入晶圓代工?                                | 14            | ado1923      |
| Re: \[討論\] 三星為何能切入晶圓代工?                            | 4             | bluejade1235 |
| \[請益\] 台積電OP和政府機關人員                                 | 64            | mobymoby     |
| \[請益\] 個資法新規定                                           | 6             | Ferrara      |
| \[聘書\] 華新科技 & 群創                                        | 9             | ichior       |
| \[請益\] 請問有人聽過鐳揚創智科技嗎？？                         |               | leonardwu    |
| Re: \[討論\] 三星為何能切入晶圓代工?                            | 9             | mainsa       |
| \[討論\]機械系較高職缺年薪一起分享                              | 爆            | enjoy1230    |
| \[請益\] 台灣凱為半導體                                         |               | lovemars     |
| \[討論\] Google台灣的薪水有多高？                               | 37            | Gphone       |
| Fw: \[徵才\] 新加坡 Altizen 徵 Firmware Engineer                |               | dolinian     |
| Re: \[請益\] 電機系PM                                           | 3             | odiewu       |
| Re: \[討論\] Google台灣的薪水有多高？                           | 32            | brave00      |
| \[請益\] 台元的大家都住哪邊?                                    | 30            | ggggggh      |
| \[新聞\] 暴虧160億！郭董養5年「小金雞」慘變賠                   | 12            | wahaha23     |
| \[新聞\] 半導體業分紅 台積電每位員工領得金額破                  | 23            | DickMartin   |
| \[問卷\]高科技產業工程師生涯&職場經驗調查                       | 6             | shinri0702   |
| \[請益\] 關於華邦行動記憶體DRAM產品工程師面試                   | 6             | yushenliu    |
| \[新聞\] 美H-1B簽證將變嚴 衝擊高科技業                          | 6             | zzzz8931     |
| \[新聞\] 凌晨3點工作到一半…突然昏倒趴機台！                     | 20            | jujang       |
| \[討論\] 包子開獎啦                                             | 38            | oa0416       |
| \[新聞\] 【好羨慕】剛結完財報　這3家科技廠宣布                  | 13            | qazxc1156892 |
| \[請益\] offer請益 : 群光、緯創                                 | 9             | poor978      |
| \[請益\] 佳必琪                                                 | 4             | yangyu       |
| \[新聞\] 蘋果傳出自製GPU 原供應商股價重挫70％                   | 14            | Daron309     |
| \[討論\] 三口真的這麼慘嗎?                                      | 9             | DamnKobe     |
| \[新聞\] 矽品男員工猝死 同事質疑過勞所致                        | 15            | kellywu      |
| \[請益\] 現職(外派)/GG/中油/餐飲店                              | 53            | mayola5566   |
| \[面試\] 啟碁 品保工程師                                        | 7             | hcney        |
| Re: \[請益\] 電機系PM                                           | 8             | realtreasure |
| \[討論\] 台積/面試/電話/GG/測試/針卡                            | 9             | double131    |
| Re: \[新聞\] 年終20月 群暉科技開130職缺                         | 20            | magic704226  |
| \[新聞\] 全民支持世大運　牧德晉用體優生                         | 14            | zzzz8931     |
| \[請益\] 內政部核定的研替結果出來沒??                           |               | benchin      |
| \[討論\] 中鋼碳素 及 台灣志氯                                   | 18            | handsomeman  |
| \[新聞\] 英特爾、思科等美大廠 擬洽來台設研發中                  | 14            | On10n        |
| Re: \[請益\] 電機系PM                                           | 6             | jeromeshih   |
| \[面試\]奇美實業/寶理塑膠/長春-大連化工                         | 42            | wwwee1230    |
| \[新聞\] 郭台銘投資日本<U+583A>工廠 去年大虧160億               | 9             | cychine      |
| Re: \[心得\]小寶跟大寶 真的不一樣                               | 8             | ABCcomputer  |
| \[請益\] 請問藍德資本                                           | 1             | think93723   |
| \[新聞\] 【鴻海連傳2利空～】富智康發獲利預警                    | 4             | qazxc1156892 |
| \[討論\] 面試中碰到不會回答的問題                               | 6             | naticom      |
| Re: \[請益\] 電機系PM                                           | 13            | join183club  |
| \[面試\] Synology 研替面試                                      | 32            | orz811017    |
| \[新聞\] 英特爾、思科、惠普 將來台設研發中心                    | 14            | wer11        |
| \[新聞\] 簽什<U+9EBD>MOU,就差這一張啦! (外商研發中心~           | 4             | SMIC5566     |
| \[請益\] 台達/鴻海/光寶 機構工程師                              |               | enjoy1230    |
| (本文已被刪除) \[ramire\]                                       | 3             | -            |
| (本文已被刪除) \[lululun\]                                      | 8             | -            |
| \[請益\] 頎邦科技                                               | 2             | william30520 |
| (本文已被刪除) \[Vinxer\]                                       | 16            | -            |
| \[請益\] 前段私碩跟後段國立畢業差異                             | 34            | dumbdragon   |
| \[請益\] 履歷自傳求批                                           | 19            | kradptt      |
| \[請益\] 台積EUV RD installation vs 原職位                      | 14            | GGCLSH       |
| Re: \[請益\] 電機系PM                                           |               | PuzzleDragon |
| \[討論\] 遇到強勢老闆該怎辦?                                    | 22            | dreamdrink   |
| Re: \[討論\] 遇到強勢老闆該怎辦?                                | 12            | birdyman     |
| Re: \[請益\] 電機系PM                                           | 5             | Ommm5566     |
| Re: \[請益\] 電機系PM                                           | 2             | fester       |
| \[討論\] 硬體廠傳產化？                                         | 6             | l10O         |
| \[請益\] 台積後段測試工程師                                     | 41            | cool288      |
| \[討論\] Reference Call                                         | 8             | Ferrara      |
| Re: \[討論\] 遇到強勢老闆該怎辦?                                | 11            | aloness      |
| \[請益\] 普遍科技板定義的PM是什麼                               | 26            | taccor7788   |
| Re: \[討論\] 遇到強勢老闆該怎辦?                                | 1             | Sex5F        |
| \[討論\] 人力資源都怎麼獵人頭的阿                               | 7             | kc092444     |

解釋爬蟲結果
------------

``` r
#這是R Code Chunk
dim(pttTech1)
```

    ## [1] 216   3

共爬出216篇文章

``` r
#這是R Code Chunk
sort(table(pttTech1$post_author),decreasing = T)
```

    ## 
    ##            -      cychine     mmkntust     zzzz8931 qazxc1156892 
    ##           13            9            4            4            4 
    ##      Ferrara      ggggggh         AAAB       ftrain   DickMartin 
    ##            3            3            2            2            2 
    ##     Ommm5566        wer11  baseband112     SMIC5566        tw689 
    ##            2            2            2            2            2 
    ##     endurant        Sex5F     DamnKobe     wahaha23    enjoy1230 
    ##            2            2            2            2            2 
    ##    catdogter   darkdanger     hank5115    henry8168      lazy321 
    ##            1            1            1            1            1 
    ##    pponywong          pzs       yohowo       zodiac    a78914124 
    ##            1            1            1            1            1 
    ##      alterna     iamholan         inji  Laplace5566       lponnn 
    ##            1            1            1            1            1 
    ##       lucyyu      oneheat      roryman       shinza similarsmile 
    ##            1            1            1            1            1 
    ##   WEIRUNTSAO       DrTech   heerodream        Maora   sanford888 
    ##            1            1            1            1            1 
    ##         su27     the4days toaste791214      zwitter accessdenied 
    ##            1            1            1            1            1 
    ## basketball08    bertsandy bill12332197        kinoe     Lamigirl 
    ##            1            1            1            1            1 
    ##      Lanaroh mizunopro214      quartzr     twinkler   weiwei0306 
    ##            1            1            1            1            1 
    ##    x246libra   yian820508     a6931791 ballyeah5566       bobo30 
    ##            1            1            1            1            1 
    ##  chickandcow       CPU100   doifish312         IDAY      im33024 
    ##            1            1            1            1            1 
    ##   kleinerHai   leonard123       lude71     sos44450   SuperModel 
    ##            1            1            1            1            1 
    ##    talon0222 weiyumystery      yukigod      ahhhwoo   apoenzyme0 
    ##            1            1            1            1            1 
    ##  billkaulitz    charlieab     coolidea        dakkk       Difier 
    ##            1            1            1            1            1 
    ## FacetheFaith ffelix1202tw       hibaba     kof70380        LP111 
    ##            1            1            1            1            1 
    ##      MattOrz        twicm         XXXD     yamakazi    youkiller 
    ##            1            1            1            1            1 
    ##       yuxing   AlanRikkin    alasha828        annwi   dragon0518 
    ##            1            1            1            1            1 
    ##       haha58 hhhahhhahhha      Hittait   ian5130992        lacio 
    ##            1            1            1            1            1 
    ##  ljsnonocat2   lucke21531      mioeboy       pamaer PauFrank5566 
    ##            1            1            1            1            1 
    ##      st80027   TaiwanJobs      v510520   wizard7442      ado1923 
    ##            1            1            1            1            1 
    ##   appledavid bluejade1235      chinhao     chunnitu       ichior 
    ##            1            1            1            1            1 
    ##     jadesoul    leonardwu       mainsa mimi0254didi     mobymoby 
    ##            1            1            1            1            1 
    ##      stennis  thatismyway       tiyico      zxc0312      brave00 
    ##            1            1            1            1            1 
    ##     Daron309     dolinian       Gphone       jujang      kellywu 
    ##            1            1            1            1            1 
    ##     lovemars       oa0416       odiewu      poor978   shinri0702 
    ##            1            1            1            1            1 
    ##       yangyu    yushenliu  ABCcomputer      benchin    double131 
    ##            1            1            1            1            1 
    ##  handsomeman        hcney   jeromeshih  join183club  magic704226 
    ##            1            1            1            1            1 
    ##   mayola5566      naticom        On10n    orz811017 realtreasure 
    ##            1            1            1            1            1 
    ##   think93723    wwwee1230      aloness     birdyman      cool288 
    ##            1            1            1            1            1 
    ##   dreamdrink   dumbdragon       fester       GGCLSH     kc092444 
    ##            1            1            1            1            1 
    ##      kradptt         l10O PuzzleDragon   taccor7788 william30520 
    ##            1            1            1            1            1

哪個作者的文章數最多? 被刪除的作者文章數最多XD

爬到2000多篇文章後發現作者發文最多的都是被刪除的人XD
