# ZZYAudio
这是一款基于AudioUnit的支持语音对讲的框架



如何使用：


1、开始语音对讲

/**
 开始语音对讲
 */
 
- (void)startRecordAndPlay;



2、获取音频数据并传进语音框架进行播放

/**
播放音频数据

pcmData        音频数据（PCM、AAC等音频格式均支持）

length         数据长度

waveFrameType  采样率
*/

- (void)play:(void*)pcmData length:(unsigned int)length waveFrameType:(int)waveFrameType;



3、结束语音对讲

/**
 停止语音对讲
 */
 
- (void)stopRecordAndPlay;



4、如何将采集到的移动端的数据发送出去

在.m文件中，会有一个采集移动端音频数据的回调函数

#pragma mark - callback function

//采集客户端音频数据传输回调，并将数据返回给设备侧

static OSStatus RecordCallback(void *inRefCon,

                               AudioUnitRenderActionFlags *ioActionFlags,
                               
                               const AudioTimeStamp *inTimeStamp,
                               
                               UInt32 inBusNumber,
                               
                               UInt32 inNumberFrames,
                               
                               AudioBufferList *ioData) {
                               
    ......
    ......
    /*在这里将采集好的音频数据进行处理后，可以将它推出去，无论通过SDK或其他方式都可以，
    将数据传递出去
    */
    。
                         
}
                              
