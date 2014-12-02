#Safari Web Content Guide

### 一、建立完善的页面内容
1.    **使用标准的页面协议**
    +    在页面中加入标准的"DOCTYPE"协议，如：HTML5的DOCTYPE
    +    将HTML，CSS和JS文件分别存放到不同的文件中
    +    要使用良好的HTML结构
    +    使用浏览器所支持的页面特性以及功能
    
2.   **Safari中能否使用Framesets框架**
    +    一般情况下framesets是带有滚动条的，而在IOS中framesets是没有滚动条的。
    
          ![image](https://developer.apple.com/library/ios/documentation/AppleApplications/Reference/SafariWebContent/Art/framesets.jpg)            
         所在说在PC的浏览器中Framesets是带有滚动条的，而在IOS中是将左右类型的框架进行平分且没有滚动条；因此如果想要在IOS中使用Framesets的话，需要用CSS将页面进人工分隔以达到框架的效果。
         
     +    使用列和块
             
           使用列和块来布局页面，可以使页面具有更好的可读性以及IOS对其进行“双击”时更加友好。使用列进行布局并不会破坏页面的整体样式，反而会有利于阅读以及方便IOS的“***双击***”事件。
           
           ![image](https://developer.apple.com/library/ios/documentation/AppleApplications/Reference/SafariWebContent/Art/columns.jpg)
           
           当用户对页面进行“双击”操作时，IOS会去寻找被双击过的元素，即闭合良好的区块（如，div, ul, li 等）或是图片。***假如IOS找到的元素是页面中的一个区块，那IOS则会放大这部分内容使其宽度来填充整个屏幕的大小同时在将其居中。如果是图片则会放大以适应屏幕大小后在居中显示，反之如果在此之前元素已经是被放大的话，那通过双击操作后此元素则会被缩小。***
           
3.   **IOS对资源的限制**
    +    一个低于256M RAM的IOS对GIF, PNG和TIFF的图片的最大尺寸要求是3百万像素；如果是要支持5百万像素的刚必须是最低为256M的RAM。
          
         >  *如果IOS的RAM仍然是以前老式的手机且存储量小于256M时，就要确保图片的尺寸（***width * height <= 3 * 1024 * 1024***）要小于256M的RAM。因为图片解码后的大小一定会大于图片的编码大小。*
    +    一个JPEG的图片经过二次采样后的解码大小可以达到320万像素。
    +    低于256M的IOS设备中的canvas最大能支持3百万像素的图片，而高于256M的则可以支持5百万像素以上的图片。
    +    JS的执行周期被限制为10秒去循环一次顶级事件。
    
        >  *如果自定义的JS的执行周期长于其默认的10秒，则IOS在解释其代码并执行的过程中会在随机的在代码的任意位置停止，这样就会对JS执行的总线程造成影响，从而产生一些意想不到的效果。*
    +    IOS对页面打开的数量也是有个数限制的。
    
        > *iphone为8个；ipad为9个*
        
           还需要使用合适的图像，不要依赖浏览器对图像的缩放。
           > *不要把一个100 * 100的图像放到一个10 * 10的img元素中，也不要使用大的背景图片。*
           
           传统意义上来说，一个页面的大小在30M以下，则在IIOS中会比较好的显示出来。
           
    +    使用IOS支持的JS功能
    
          - 弹窗
              
              IOS支持系统原生的弹出窗事件，如：alert，confirm，print和prompt。调用这些系统的弹出窗事件后，IOS会使用自己所特定的页面展示效果来显示；并不是像PC中的页面弹出效果。
              
        - Content Typpe和IOS特性
        
            在IOS中对于PDF和视频也是有很好的支持。在iphone和ipad中，video和audio在被触发后只会进行全屏显示的；它们会在用户进行旋转的过程中进行屏幕的自适应。在ipad中video和audio会在页面中或是全屏模式下进行工作。
            
            ![image](https://developer.apple.com/library/ios/documentation/AppleApplications/Reference/SafariWebContent/Art/video_playback.jpg)
            
            PDF文档的打开与video很相似，用户可以通过点击页面中的链接来显示PDF内容，同时也可以通过旋转屏幕来缩放文档的大小。
            
            ![image](https://developer.apple.com/library/ios/documentation/AppleApplications/Reference/SafariWebContent/Art/pdf_documents.jpg)
            
            IOS在预览文档格式的范围也可以包括MS Office（Word，Excel和PPT），iWork（Pages，Numbers和Keynote ）和RTF文档（Rich Text Format，即富文本格式）。如果有第三方的应用在IOS中可以打开以上的文档的话，那么在该文档被触发后将会被调用以显示文档内容；但是也有一种情况就是第三方应用虽然支持此文件格式的预览，但IOS不允许其页面打开原生的APP的话，则在ipad中将会被下载后再用此软件进行打开。
            
         - HTML5 Audio和Video
         
             在iphone中的video是全屏播放的；ipad是内联在页面中，并且它们都需要人为的触发进行播放；在ipad中可以获得播放文件。
          
         - 使用IOS所支持的富媒体类型
         
             MIME type |  描 述 |    扩展名
            ---------|-----|-------
            audio/3gpp| 3GPP media  | 3gp, 3gpp
            audio/3gpp2 | 3GPP2 media | 3g2, 3gp2
            audio/aiff      |  AIFF audio    |    aiff, aif, aifc, cdda
            audio/x-aiff |    AIFF audio    |   aiff, aif, aifc, cdda
            audio/amr    |    AMR audio    |    amr
            audio/mp3    |    MP3 audio    |    mp3, swa
            audio/mpeg3    |    MP3 audio    | mp3, swa
            audio/x-mp3   |    MP3 audio    | mp3, swa
            audio/x-mpeg3   |    MP3 audio    | mp3, swa
            audio/mp4    | MPEG-4 media    |    mp4
            audio/mpeg    |    MPEG-4 media    |    mp4
            audio/x-mpeg    |     MPEG-4 media    |    mp4
            audio/wav    |    WAVE audio    |    wav, bwf
            audio/x-wav    |     WAVE audio    |    wav, bwf
            audio/x-m4a    |    AAC audio    |    m4a
            audio/x-m4b    |    AAC audio book    |    m4b
            audio/x-m4p    |    AAC audio（protected）    |    m4p
            video/3gpp    |    3GPP media    |    3gp, 3gp2
            video/3gpp2    |    3GPP2 media    |    3g2, 3gp2
            video/mp4    |    MPEG-4 media    |    mp4
            video/quicktime    |    QuickTime Movie    | mov, qt, mqv
            video/x-m4v    | Video    | m4v
          
          
          