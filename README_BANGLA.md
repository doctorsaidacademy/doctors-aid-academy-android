# Doctors Aid Academy — Android APK Build

এই প্রজেক্টটি একটি ছোট Android WebView অ্যাপ। এটি `https://doctorsaidacademy.pages.dev/` খুলবে। পোর্টালের বিজ্ঞাপন, লগইন, ইউজার আইডি, Google Sheets এবং Apps Script backend ওয়েবসাইটের মতোই থাকবে। অ্যাপের ভিতরে আলাদা ডাটাবেস নেই।

## বিনামূল্যে APK বানানোর পদ্ধতি (GitHub Actions)

1. GitHub.com-এ একটি ফ্রি অ্যাকাউন্ট খুলুন/লগইন করুন।
2. New repository তৈরি করুন: `doctors-aid-academy-android` (Public বা Private)।
3. এই ZIP-এর ভেতরের সব ফাইল ও ফোল্ডার repository-তে upload করুন। `.github` ফোল্ডারটিও অবশ্যই upload করবেন।
4. `gradlew` wrapper ফাইলটি এই প্যাকেজে ইচ্ছাকৃতভাবে রাখা হয়নি; GitHub repository-তে Android Gradle build-এর আগে wrapper bootstrap দরকার। GitHub Actions-এ `gradle/actions/setup-gradle` বা gradle wrapper bootstrap step যোগ করে build করতে হবে.
5. Repository → Actions → “Build Doctors Aid Academy APK” → Run workflow.
6. Build শেষ হলে workflow run-এর Artifacts অংশে `DoctorsAidAcademy-APK` নামের artifact পাবেন। সেটি download করে ZIP খুললে `DoctorsAidAcademy.apk` পাবেন।
7. APK Google Drive-এ upload করুন। Share → General access → Anyone with the link → Viewer দিন।
8. Public portal-এর Download App বাটনে ওই Drive download URL যুক্ত করুন। Drive URL-এর ফরম্যাট: `https://drive.google.com/uc?export=download&id=FILE_ID`।

## গুরুত্বপূর্ণ
- এই build হলো debug-signed APK; নিজের/পরিচিতদের মধ্যে বিনামূল্যে sideload করে ব্যবহার করা যাবে। Play Store-এ প্রকাশের জন্য আলাদা release signing ও Play Console প্রয়োজন।
- Android-এ Download-এর পর ব্যবহারকারীকে “Install unknown apps” অনুমতি দিয়ে Install চাপতে হবে। ওয়েবসাইট/Drive থেকে নীরবে install সম্ভব নয়।
- পোর্টালের live URL বদলালে `MainActivity.java`-এর `PORTAL_URL` বদলাতে হবে।
- এই অ্যাপ online-only: ইন্টারনেট ছাড়া portal/login চলবে না।
- প্রথম APK build-এর আগে আপনার portal domain-টি ঠিকমতো live আছে কি না যাচাই করুন।
