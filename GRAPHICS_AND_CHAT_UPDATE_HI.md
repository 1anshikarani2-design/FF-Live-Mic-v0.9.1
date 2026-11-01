# FF Live Mic — Graphics और YouTube Chat अपडेट (v0.9.0)

## इस अपडेट में लागू
- 720p और 1080p output size selection. Capture source से बड़ी resolution पर upscale नहीं किया जाता।
- 30 FPS और 60 FPS selection. 60 FPS डिवाइस encoder और नेटवर्क पर निर्भर है; असफल होने पर 30 FPS चुनें।
- 4, 6 और 8 Mbps video bitrate selection. कमजोर/अस्थिर नेटवर्क पर 720p, 30 FPS, 4 Mbps से शुरू करें।
- App versionCode 9 / versionName 0.9.0.

## सुझाई गई सेटिंग
| परिस्थिति | Resolution | FPS | Bitrate |
|---|---:|---:|---:|
| कमजोर नेटवर्क / गर्म फोन | 720p | 30 | 4 Mbps |
| अच्छा नेटवर्क | 720p | 60 | 6 Mbps |
| मजबूत फोन + स्थिर अपलोड | 1080p | 30 | 6 Mbps |
| बहुत मजबूत फोन + स्थिर अपलोड | 1080p | 60 | 8 Mbps |

ये presets गारंटीकृत गुणवत्ता नहीं हैं। वास्तविक परिणाम फोन के display size, encoder, thermal throttling, Wi-Fi/mobile upload और YouTube ingest पर निर्भर है। 1080p चुनने पर भी फोन की मूल स्क्रीन resolution से ऊपर upscale नहीं किया जाता।

## YouTube Live Chat की स्थिति
इस v0.9.0 build में दर्शकों के YouTube Live comments को गेम/स्ट्रीम पर overlay करने की सुविधा अभी लागू नहीं है। केवल RTMP video/audio भेजना YouTube chat पढ़ने की अनुमति नहीं देता। वास्तविक chat integration के लिए YouTube Data API का `liveChatMessages.list`/`streamList` endpoint, Google OAuth consent, सुरक्षित token storage, active liveChatId lookup, rate-limit handling और overlay rendering जोड़ना होगा। API credentials या OAuth token को APK/ZIP में hard-code नहीं करना चाहिए।

## माइक्रोफोन और Accessibility सीमा
Accessibility Service Android के concurrent microphone capture नियमों को bypass नहीं कर सकती। इस प्रोजेक्ट में Accessibility permission नहीं जोड़ी गई है। Free Fire Voice Chat mic को प्राथमिकता दे सकता है; यदि ऐसा हो तो सुरक्षित विकल्प दूसरा फोन या compatible external audio mixer/interface है।

## Build / test स्थिति
Source files और ZIP संरचना अपडेट की गई है। इस वातावरण में Android SDK/Gradle build और वास्तविक फोन/YouTube live test नहीं चलाया गया। GitHub Actions पर नया commit push करके APK build करें और पहले unlisted test stream में जाँचें।
