# Neko-Tomo  
ruby.bin 注音对照  
systemtext.bin 大多系统提示文字  
dx00.bin 2.0.0版新游戏开幕对话  
  
文本末尾以00 00为结束标志  
开头标志（对话文本基本以FF FF FF nn开头，其他地方的文本有的会在结束标志后紧接着开始下一条文本）  
对话文本里出现的：  
FF FF FF 00 后紧跟着正文  
FF FF FF 02 00 后紧跟着正文  
FF FF FF 04 00 后紧跟着正文  
FF FF FF 05 后紧跟着意义不明的一字节（0x42），后紧跟着正文  
FF FF FF 06 后紧跟着一串意义不明的字节（含末尾的00约为6字节），以单字节00结束，后紧跟着正文  
FF FF FF 09 00 后紧跟着正文  
FF FF FF 0A 00 后紧跟着正文  
FF FF FF 0B 后紧跟着一串疑似文件名的ASCII单字节，以单字节00结束，后紧跟着正文  
FF FF FF 0C 00 后紧跟着正文  
FF FF FF 0D 00 后紧跟着正文  
FF FF FF 16 后紧跟着一串意义不明的字节（含末尾的00约为2字节、FF 00），以单字节00结束，后紧跟着正文  
  
# 转义符（控制符）  
已知开头都需要跟着一个\v（0B 00）表示转义符开始，然后转义符本身都是单字节  
\v col1 文字颜色，后面跟着四字节RGBA  
\v rept 名词代换，后面跟着两字节由ASCII字母和数字直接表示的十六进制数  
\v rstr 无参数  
\v rst2 无参数？  
\v rst3 无参数？  
\v numb 无参数？  
\v rscs 无参数？  
\v rsds 无参数？  
  
\v selc 选择肢，无空位紧接着第一个选项名，选项名之间用00 00分隔且每个选项名开头有一字节的序号，最后一个选项后00 00再一个\r（0D，单字节）标志结束  
\v setn 设置名称栏，无空位紧接着名称，00 00结束  
\v mnit 紧跟着意义不明的两字节，然后紧跟着文本，00 00结束  
\v iprt 时间经过转场，无空位紧接着转场时显示文本，00 00结束  
\v stbg 设置背景？，紧跟着四字节  
\v chbg 紧跟着一字节  
\v bgm0 更改BGM，紧跟着九字节？第二个字节开始是单字节文件名，剩余部分用00填充  
\v wait 紧跟着四字节（推测为等待时间）  
\v fadi 画面淡出，紧跟着五字节  
\v fado 画面淡入，紧跟着四？字节  
\v eevd 画面特效？，紧跟着两字节  
\v loca 紧跟着一字节  
\v act2 动作和对话，紧跟着三字节，后面接对话文本（开头标志）？（第一个字节决定了动作者，00为第一只猫、01为第二只猫、FF为旁白）  
\v mark 标签，紧跟着一字节  
\v goto 跳转标签，紧跟着一字节  
\v face 角色表情，紧跟着两字节（第一个为动作者，第二个为表情ID）  
\v moti 角色动作，紧跟着两字节（第一个为动作者，第二个为动作ID）  
\v stat 紧跟着九字节  
\v inct 紧跟着两字节  
\v scee 无参数  
\v ofck 无参数  
\v dlac 无参数  
\v crbe 无参数  
\v sted 无参数  
\v cmmi 无参数  
\v cmms 无参数  
\v cmmo 无参数  
\v flag 紧跟着三字节  
\v wind 修改对话窗口皮肤？，紧跟着两字节  
\v scef 紧跟着一字节  
\v skku 无参数  
\v basc 无参数  
\v end0 整篇脚本结束的标志，放在最后，无空无参数  
  
考虑到没有脚本开始的标志，可以用第一个转义符（00 00 0b 00）来判断开始【另外通常第一个转义符是mark，参数为00】  
wind 01 00 对话框移出屏幕  
wind 00 01 旁白对话框皮肤+移入屏幕？  
wind 00 00 小猫对话框皮肤？  
  
\v $!!$     jaJP_langDic_40c_R2.bin中的442BDD位置发现，应该不是  
\v u0u0  
\v i0i0  
\v u0_0  
\v g0o0  
\v o0c0  
  
\v patt  
\v deef  
\v rtbc  
\v oemi  
\v rand  
\v dflt  
\v acth  
\v sete  
\v ogel  
\v scpt  
\v ssin  
\v ssse  
\v ssou  
\v inft  
\v se01  
\v chtt  
\v onub  
\v asel  
\v qsel  
\v lasl  
\v laqs  
\v prge  
\v heti  
\v ckhe  
\v edhe  
\v wapw  
\v cecg  
\v decg  
\v stde  
\v cbg2  
\v hawr  
\v stse  
\v depw  
\v oprf  
\v strl  
\v debe  
\v ofcl  
\v ccos  
\v topb  
\v psgi  
\v atph  
\v deph  
\v elac  
\v gets  
\v sclo  
\v ntpl  
\v nted  
\v ntin  
\v stny  
\v upcp  
\v upup  
\v upap  
\v rnsc  
\v gvse  
\v opto  
\v sttc  
\v seft  
\v rpct  
\v upcw  
\v reti  
\v chwo  
\v ifte  
\v scrt  
