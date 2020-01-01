### PRD 价值主张设计 

#### PRD1.加值宣言

本产品主要应用百度智能人脸识别，身份证识别，文本识别和语音合成功
能，用于用户对图书馆位置和书籍的预约。
- 用户先在图书馆预约APP进行空位预定，可对图书馆空位进行预约。到预定时间时，用户前往图书馆预约系统进行人脸识别或身份证识别后，即可到达预定位置。

- 每个座位都有一个小的感应器：

1.在没人预约时不显颜色则表示无人预约。

2.在用户预约时间内显示为红色以提醒其他用户此座位或书籍的预约人正在过来。

3.当用户签到后感应灯才能为绿色。

4.同时感应器也能读取时间后通过百度云平台语音合成以语音轻生提示一次用户的预约时间，以提示当前座位的人。

5. 当用户想借书籍时，只需通过人脸与书籍编码的合照，再通过文本识别和人脸识别来读取用户信息。
#### PRD2.核心价值 

核心价值宣言：着重于当前最紧迫的需求，解决用户的占座问题，提供最合理最简便的占座服务。

#### PRD3.核心价值与用户痛点 

用户痛点宣言：
1.图书馆没有占座系统，用户想要在图书馆学习但因被一些其他用户通过放书等方式盲目占座而受到影响。

2.图书馆已有占座系统，但大部分用户不会理会，大部分时间已占座的用户也不好意思与其沟通，甚至会产生冲突。

3.图书馆已有占座系统，但很多用户占座之后并不会返回，从而占用了图书馆的座位。

4.用户通常需要通过复杂的流程来借书。

#### PRD4.人工智能概率性与用户痛点 

####1.  身份证识别：
依托百度优秀的图像处理技术和海量优质数据，支持识别各角度身份证照片，并对各少数民族身份证进行专项优化，识别准确率超过99%。
####2.  文本识别：
依托百度优秀的图像处理技术和海量优质数据，支持识别各种不规则手写字体，并对字迹潦草、模糊等情况进行专项优化，手写中文识别准确率可达90%以上
####3.  人脸识别:
人脸识别技术国际领先，识别准确率超过99%，在多个国际公开竞赛排名第一
####4. 语音合成:
支持中文、英文、中英文混读合成，提供基础音库和精品音库共9种音库供您选择，让您的应用拥有个性化的声音,准确率超过90%以上。

#### PRD5.需求列表与人工智能API加值 
| 用户案例 | 对应功能 | 重要程度 |
|--  | --  | -- |
| 用户进行身份认证 | 人脸识别和身份证识别 | 重要 |
| 用户借书时数据读取 | 文本识别 | 重要 |
| 感应器语音提示 | 语音合成 | 次重要 |

### 原型 

#### 原型1.交互及界面设计 

交互及界面设计：在PRD文件中是否有说明且原型是否有做到：交互及界面设计的某个核心交互环节使用了人工智能的加值

#### 原型2.信息设计 

信息设计：在PRD文件中是否有说明且原型是否有做到：信息设计的某个核心信息或设计使用了人工智能的加值

#### 原型3.原型文档 

原型文档：多少程度上有提供MVP可交互的原型文档，供它人在Github上下载使用

#### 原型4.口头操作说明 

口头操作说明：多少程度上在2-3分钟时间限制内，对听众留下了「的确这是个可行丶可用的人工智能加值产品」的印象

### API 产品使用关键AI或机器学习之API的输出入展示

#### API1.使用水平 

使用水平：在PRD文件中是否有说明且展示，核心功能所应用的API之输入及输出

###### 1.API：人脸识别
- 输入：
```
# encoding:utf-8

import requests

'''
身份验证
'''

request_url = "https://aip.baidubce.com/rest/2.0/face/v3/person/verify"

params = "{\"image\":\"sfasq35sadvsvqwr5q...\",\"image_type\":\"BASE64\",\"id_card_number\":\"110...\",\"name\":\"张三\",\"quality_control\":\"LOW\",\"liveness_control\":\"HIGH\"}"
access_token = '24.16f347bf6beaaad30df497e3c87b6f2b.2592000.1580204143.282335-17604552'
request_url = request_url + "?access_token=24.16f347bf6beaaad30df497e3c87b6f2b.2592000.1580204143.282335-17604552" + access_token
headers = {'content-type': 'application/json'}
response = requests.post(request_url, data=params, headers=headers)
if response:
    print (response.json())
```

- 输出：
```
{
    "log_id": 123,
    "result":
    {
        "score": 20.1
    }
}
```
###### 2.API：身份证识别
- 输入：

```import requests
import base64
request_url = "https://aip.baidubce.com/rest/2.0/ocr/v1/idcard"
f = open('C:/Users/Administrator/Desktop/本学期/身份证/099677d61ff4591a47d0c7146228b63.jpg', 'rb')
img = base64.b64encode(f.read())
params = {"id_card_side":"front","image":img}
access_token = '24.16f347bf6beaaad30df497e3c87b6f2b.2592000.1580204143.282335-17604552'
request_url = request_url + "?access_token=24.16f347bf6beaaad30df497e3c87b6f2b.2592000.1580204143.282335-17604552" + access_token
headers = {'content-type': 'application/x-www-form-urlencoded'}
response = requests.post(request_url, data=params, headers=headers)
if response:
    print (response.json())
```
- 输出：
```{
    "log_id": 2648325511,
    "direction": 0,
    "image_status": "normal",
    "idcard_type": "normal",
    "edit_tool": "Adobe Photoshop CS3 Windows",
    "photo": "/9j/4AAQSkZJRgABA......",
    "photo_location": {
        "width": 1189,
        "top": 638,
        "left": 2248,
        "height": 1483
    },
    "words_result": {
        "住址": {
            "location": {
                "left": 267,
                "top": 453,
                "width": 459,
                "height": 99
            },
            "words": "南京市江宁区弘景大道3889号"
        },
        "公民身份号码": {
            "location": {
                "left": 443,
                "top": 681,
                "width": 589,
                "height": 45
            },
            "words": "330881199904173914"
        },
        "出生": {
            "location": {
                "left": 270,
                "top": 355,
                "width": 357,
                "height": 45
            },
            "words": "19990417"
        },
        "姓名": {
            "location": {
                "left": 267,
                "top": 176,
                "width": 152,
                "height": 50
            },
            "words": "伍云龙"
        },
        "性别": {
            "location": {
                "left": 269,
                "top": 262,
                "width": 33,
                "height": 52
            },
            "words": "男"
        },
        "民族": {
            "location": {
                "left": 492,
                "top": 279,
                "width": 30,
                "height": 37
            },
            "words": "汉"
        }
    },
    "words_result_num": 6
}
```
###### 3.API：语音合成
- 输入：
```
# coding=utf-8
import sys
import json

IS_PY3 = sys.version_info.major == 3
if IS_PY3:
    from urllib.request import urlopen
    from urllib.request import Request
    from urllib.error import URLError
    from urllib.parse import urlencode
    from urllib.parse import quote_plus
else:
    import urllib2
    from urllib import quote_plus
    from urllib2 import urlopen
    from urllib2 import Request
    from urllib2 import URLError
    from urllib import urlencode

API_KEY = '04gRhPzYRVf4pRdho5h6TGzg'
SECRET_KEY = 'PvPag0on9Fq1BbchpfUVdyAdn6OSp0mG'

TEXT = "您的座位已被预订，用户即将到达，请您尽快更换座位。"

# 发音人选择, 基础音库：0为度小美，1为度小宇，3为度逍遥，4为度丫丫，
# 精品音库：5为度小娇，103为度米朵，106为度博文，110为度小童，111为度小萌，默认为度小美 
PER = 4
# 语速，取值0-15，默认为5中语速
SPD = 5
# 音调，取值0-15，默认为5中语调
PIT = 5
# 音量，取值0-9，默认为5中音量
VOL = 5
# 下载的文件格式, 3：mp3(default) 4： pcm-16k 5： pcm-8k 6. wav
AUE = 3

FORMATS = {3: "mp3", 4: "pcm", 5: "pcm", 6: "wav"}
FORMAT = FORMATS[AUE]

CUID = "123456PYTHON"

TTS_URL = 'http://tsn.baidu.com/text2audio'


class DemoError(Exception):
    pass


"""  TOKEN start """

TOKEN_URL = 'http://openapi.baidu.com/oauth/2.0/token'
SCOPE = 'audio_tts_post'  # 有此scope表示有tts能力，没有请在网页里勾选


def fetch_token():
    print("fetch token begin")
    params = {'grant_type': 'client_credentials',
              'client_id': aerD9Q0Y9GwVrhRNUVtPV4BB,
              'client_secret': EU7ls559y9MYg2Y2tPqpGtinGqNDwKKy}
    post_data = urlencode(params)
    if (IS_PY3):
        post_data = post_data.encode('utf-8')
    req = Request(TOKEN_URL, post_data)
    try:
        f = urlopen(req, timeout=5)
        result_str = f.read()
    except URLError as err:
        print('token http response http code : ' + str(err.code))
        result_str = err.read()
    if (IS_PY3):
        result_str = result_str.decode()

    print(result_str)
    result = json.loads(result_str)
    print(result)
    if ('access_token' in result.keys() and 'scope' in result.keys()):
        if not SCOPE in result['scope'].split(' '):
            raise DemoError('scope is not correct')
        print('SUCCESS WITH TOKEN: %s ; EXPIRES IN SECONDS: %s' % (result['access_token'], result['expires_in']))
        return result['access_token']
    else:
        raise DemoError('MAYBE API_KEY or SECRET_KEY not correct: access_token or scope not found in token response')


"""  TOKEN end """

if __name__ == '__main__':
    token = fetch_token()
    tex = quote_plus(TEXT)  # 此处TEXT需要两次urlencode
    print(tex)
    params = {'tok': token, 'tex': tex, 'per': PER, 'spd': SPD, 'pit': PIT, 'vol': VOL, 'aue': AUE, 'cuid': CUID,
              'lan': 'zh', 'ctp': 1}  # lan ctp 固定参数

    data = urlencode(params)
    print('test on Web Browser' + TTS_URL + '?' + data)

    req = Request(TTS_URL, data.encode('utf-8'))
    has_error = False
    try:
        f = urlopen(req)
        result_str = f.read()

        headers = dict((name.lower(), value) for name, value in f.headers.items())

        has_error = ('content-type' not in headers.keys() or headers['content-type'].find('audio/') < 0)
    except  URLError as err:
        print('asr http response http code : ' + str(err.code))
        result_str = err.read()
        has_error = True

    save_file = "error.txt" if has_error else 'result.' + FORMAT
    with open(save_file, 'wb') as of:
        of.write(result_str)

    if has_error:
        if (IS_PY3):
            result_str = str(result_str, 'utf-8')
        print("tts api  error:" + result_str)

    print("result saved as :" + save_file)
```
- 输出：
```
fetch token begin
{"access_token":"24.5c1930a9b9d159e201f6c025f5bac13a.2592000.1573821079.282335-17543637","session_key":"9mzdDtGXjykfzyZKxBFmsfEXkn++lBUt4SH1aHX\/p8UcjzNjBlq6hlH37Cdqzp\/\/EbARdVjNP32R9FPOmtk91MyDGhBUUA==","scope":"audio_voice_assistant_get brain_enhanced_asr audio_tts_post public brain_all_scope picchain_test_picchain_api_scope wise_adapt lebo_resource_base lightservice_public hetu_basic lightcms_map_poi kaidian_kaidian ApsMisTest_Test\u6743\u9650 vis-classify_flower lpq_\u5f00\u653e cop_helloScope ApsMis_fangdi_permission smartapp_snsapi_base iop_autocar oauth_tp_app smartapp_smart_game_openapi oauth_sessionkey smartapp_swanid_verify smartapp_opensource_openapi smartapp_opensource_recapi fake_face_detect_\u5f00\u653eScope","refresh_token":"25.9cb835ccba70373574d455faccdd1413.315360000.1886589079.282335-17543637","session_secret":"c0e0fea2a7329d1e79d629f0ef1fc4f3","expires_in":2592000}

{'access_token': '24.5c1930a9b9d159e201f6c025f5bac13a.2592000.1573821079.282335-17543637', 'session_key': '9mzdDtGXjykfzyZKxBFmsfEXkn++lBUt4SH1aHX/p8UcjzNjBlq6hlH37Cdqzp//EbARdVjNP32R9FPOmtk91MyDGhBUUA==', 'scope': 'audio_voice_assistant_get brain_enhanced_asr audio_tts_post public brain_all_scope picchain_test_picchain_api_scope wise_adapt lebo_resource_base lightservice_public hetu_basic lightcms_map_poi kaidian_kaidian ApsMisTest_Test权限 vis-classify_flower lpq_开放 cop_helloScope ApsMis_fangdi_permission smartapp_snsapi_base iop_autocar oauth_tp_app smartapp_smart_game_openapi oauth_sessionkey smartapp_swanid_verify smartapp_opensource_openapi smartapp_opensource_recapi fake_face_detect_开放Scope', 'refresh_token': '25.9cb835ccba70373574d455faccdd1413.315360000.1886589079.282335-17543637', 'session_secret': 'c0e0fea2a7329d1e79d629f0ef1fc4f3', 'expires_in': 2592000}
SUCCESS WITH TOKEN: 24.5c1930a9b9d159e201f6c025f5bac13a.2592000.1573821079.282335-17543637 ; EXPIRES IN SECONDS: 2592000
%E5%BC%A0%E6%9D%B0%E8%AF%B7%E6%88%91%E5%90%83%E5%AE%B5%E5%A4%9C
test on Web Browserhttp://tsn.baidu.com/text2audio?tok=24.5c1930a9b9d159e201f6c025f5bac13a.2592000.1573821079.282335-17543637&tex=%25E5%25BC%25A0%25E6%259D%25B0%25E8%25AF%25B7%25E6%2588%2591%25E5%2590%2583%25E5%25AE%25B5%25E5%25A4%259C&per=4&spd=5&pit=5&vol=5&aue=3&cuid=123456PYTHON&lan=zh&ctp=1
result saved as :result.mp3
```
###### 4.API：文本识别
- 输入：
```
# encoding:utf-8

import requests
import base64

request_url = "https://aip.baidubce.com/rest/2.0/ocr/v1/general"

f = open('图书照片', 'rb')
img = base64.b64encode(f.read())

params = {"image":img}
access_token='25.9cb835ccba70373574d455faccdd1413.315360000.1886589079.282335-17543637'
request_url = request_url + "?access_token=25.9cb835ccba70373574d455faccdd1413.315360000.1886589079.282335-17543637" + access_token
headers = {'content-type': 'application/x-www-form-urlencoded'}
response = requests.post(request_url, data=params, headers=headers)
if response:
    print (response.json())
```
- 输出：
```
Content-Type: application/json;charset=UTF-8
{
"log_id": 3523983603,
"direction": 0, //detect_direction=true时存在
"words_result_num": 2,
"words_result": [
    {
        "location": {
            "left": 35,
            "top": 53,
            "width": 193,
            "height": 109
        },
        "words": "感动",
        "chars": [    //recognize_granularity=small时存在
            {
                "location": {
                    "left": 56,
                    "top": 65,
                    "width": 69,
                    "height": 88
                },
                "char": "感"
            },
            {
                "location": {
                    "left": 140,
                    "top": 65,
                    "width": 70,
                    "height": 88
                },
                "char": "动"
            }
        ]
    }
    ...
]
}
```

#### API2.使用比较分析 
### 1.身份证识别
- #####百度AI（规定次数内免费）

1.全字段识别：
支持对二代居民身份证正反两面全部字段的结构化识别，能够满足身份证使用场景中对任意字段的识别需求。

2.证件风险检测：
检测上传的图片是否为身份证复印件、临时身份证、屏幕翻拍身份证或被PS过的身份证，并返回对应的风险类型。

3.端上质量校验
提供移动端SDK，使用时能实时检测取景框中是否包含身份证，是否存在模糊、欠/过曝等情况，并提示用户矫正，提高采集质量，提升准确率。

- #####阿里云（收费）

1.自动定位身份证图片区域。

2.准确率高，识别速度快，服务稳定。

- #####腾讯云（收费）

1.通用性强：不仅支持证照类图片，还支持多种复杂场景的文字识别，如街景门店、印刷图文等。

2.适应性强：适应各种实际应用中的异常情况，如光照不均、倾斜、模糊等，具备非常高的复杂环境可用性。

###### 总结：
总体来说，阿里云的优势在于准确率高，识别速度快，服务稳定，腾讯云百度AI提供的API优势在于通用性和适应性强，但在风险检测、字段识别和质量校验等方面百度AI提供的API占据着绝对的优势。

### 2..文本识别
- #####百度AI（规定次数内免费）

1.通用文字识别:对图片中的文字进行检测和识别，支持中、英、法、俄、西、葡、德、意、日、韩、中英混合等多语种识别，同时支持中、英、日、韩四语种的类型检测。

2.高精度版：在通用文字识别的基础上，提供更高精度的识别服务，并将字库从1w+扩展到2w+，能识别所有常用字和大部分生僻字。

3.含位置信息版：在通用文字识别的基础上，返回文字在图片中的位置信息，方便用户进行版式的二次处理。

4.高精度含位置版：在通用文字识别（高精度版）的基础上，返回文字在图片中的位置信息，方便用户进行版式的二次处理。

- #####阿里云（收费）

1.自动定位任意图片区域。

2.高准确率，高实时性，且支持海量数据。

- #####腾讯云（收费）

1.通用性强：产品优势
通用性强：不仅支持证照类图片，还支持多种复杂场景的文字识别，如街景门店、印刷图文等。

2.适应性强：适应各种实际应用中的异常情况，如光照不均、倾斜、模糊等，具备非常高的复杂环境可用性。
######总结：
总体来说，阿里云的优势在于自动定位任意图片区域，腾讯云百度AI提供的API优势在于通用性和适应性强，但在精准度、位置信息和文字识别类别的广度等方面百度AI提供的API占据着绝对的优势。

### 3.人脸识别

1.防作弊能力强：提供6种在线/离线活体检测方案，支持图片质量校验、多帧图片识别，有效抵御照片、视频翻拍、3D模型等作弊行为。

2.多种交互形态：支持APP、H5、PC、设备端4种接入方式，产品形态全面丰富，灵活组合使用，满足各类场景需求。

3.高精度识别：人脸识别技术国际领先，识别准确率超过99%，在多个国际公开竞赛排名第一。

4.个性化配置：人脸SDK支持自定义设置人脸质量参数及活体检测动作，同时接口返回参数、阈值可根据业务需求灵活配置。

- #####阿里云（收费）
1.识别效率高：支持实时识别。

2.识别精准度高：人脸检测识别等算法精度处于业内领先水平。

- #####腾讯云（收费）
1.样本丰富：立足于腾讯社交大数据平台收集的海量训练集，成功标注千万张人脸。

2.跨年龄识别：在保证通用场景识别能力的同时，实现跨年龄算法不断升级。
###### 总结：
总体来说，阿里云的优势在于识别效率高，腾讯云百度AI提供的API优势在于能跨年龄识别，但在防作弊能力、交互形态和集个性化配置等方面百度AI提供的API占据着绝对的优势。

### 4.语音合成

- #####百度AI（规定次数内免费）

1.支持多语言多音色：支持中文、英文、中英文混读合成，提供基础音库和精品音库共9种音库供您选择，让您的应用拥有个性化的声音。

2.丰富的场景应用：支持纯在线、在线离线融合两种应用方式，支持在弱网环境下的合成播报，满足不同的场景需求。

3.方便快捷的集成方式：提供REST API接口，方便可发起网络请求的设备进行合成；提供Android、iOS SDK，轻巧简便，便于手机、智能硬件快速集成。
- #####阿里云（收费）
1.听感自然：使用海量的音频数据训练合成数据，合成音真实饱满、抑扬顿挫、富有表现力，MOS评分达到业内顶级水准。

2.技术领先：技术上兼顾了多级韵律停顿，达到自然的合成韵律目的，综合利用声学参数和语言学参数，建立基于深度学习的多重自动预测模型。

- #####腾讯云（收费）
1.在线服务:可靠的在线服务，低延迟高并发，为语音合成效果保驾护航。

2.效果自然：语音合成效果流畅自然，近乎真人发声，极致体验。

##### 总结:
总体来说，阿里云的优势在于技术比较领先，腾讯云百度AI提供的API优势在于听感良好，但在音色种类、场景应用和集成方式等方面百度AI提供的API占据着绝对的优势。

### API3.使用后风险报告 


- #####身份证识别API与人脸识别API
###### 面临的挑战
比较容易给其他方式，如识别图书馆身份需要一张图书卡即可，特别是中老年人（对身份证识别和人脸识别不熟悉）的群体。
###### 目前和未来发展性
身份证识别和人脸识别API的应用已经遍布全球，凭借着其简单方便等特性很有未来发展性。



- #####语音合成API
###### 面临的挑战
总体来说，目前语音合成的技术没有达到最成熟化，偶尔还是会出现一些偏差，如语调和情感等的结合。
###### 目前和未来发展性
语音合成目前在各个行业运用相对广泛，其作用也无可替代，在未来的很长时间都会产生巨大效应。


- #####文本识别API
###### 面临的挑战
在目前文本识别还没有做到很高的准确率，特别是文字的亮度，曲度或清晰度不理想的情况下更为明显。
###### 目前和未来发展性
文字识别技术诞生20余年来，经历从实验室技术到产品的转变，已经进入行业应用开发的成熟阶段。在未来随着文本识别的精确度不断上升此功能会变得更为重要。

