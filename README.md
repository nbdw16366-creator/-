import 'package:flutter/material.dart';

void main() {
  runApp(const BankakApp());
}

class BankakApp extends StatelessWidget {
  const BankakApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      debugShowCheckedModeBanner: false,
      title: 'بنكك',
      theme: ThemeData(
        primarySwatch: Colors.red,
        fontFamily: 'Cairo', // يفضل استخدام خط عربي مناسب
      ),
      home: const LoginScreen(),
    );
  }
}

class LoginScreen extends StatelessWidget {
  const LoginScreen({super.key});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      backgroundColor: Colors.white,
      body: Directionality(
        textDirection: TextDirection.rtl,
        child: Column(
          children: [
            // القسم العلوي الأحمر
            Container(
              width: double.infinity,
              height: MediaQuery.of(context).size.height * 0.42,
              color: const Color(0xFFD32F2F), // لون أحمر مشابه لتطبيق بنكك
              child: SafeArea(
                child: Padding(
                  padding: const EdgeInsets.symmetric(horizontal: 16.0),
                  child: Column(
                    crossAxisAlignment: CrossAxisAlignment.start,
                    children: [
                      // زر تغيير اللغة في الأعلى
                      Align(
                        alignment: Alignment.topLeft,
                        child: Container(
                          padding: const EdgeInsets.symmetric(horizontal: 8, vertical: 4),
                          decoration: BoxDecoration(
                            color: Colors.white,
                            borderRadius: BorderRadius.circular(4),
                          ),
                          child: const Text(
                            'A / ع',
                            style: TextStyle(
                              color: Color(0xFFD32F2F),
                              fontWeight: FontWeight.bold,
                              fontSize: 12,
                            ),
                          ),
                        ),
                      ),
                      const Spacer(),
                      // شعار بنكك
                      Center(
                        child: Column(
                          children: [
                            RichText(
                              text: const TextSpan(
                                children: [
                                  TextSpan(
                                    text: 'بنكك',
                                    style: TextStyle(
                                      color: Colors.white,
                                      fontSize: 42,
                                      fontWeight: FontWeight.bold,
                                    ),
                                  ),
                                  // أيقونة الإشارة الصغيرة بجانب الشعار (اختياري)
                                ],
                              ),
                            ),
                            const Text(
                              'bankak',
                              style: TextStyle(
                                color: Color(0xFFFFD54F), // لون أصفر ذهبي للشعار الإنجليزي
                                fontSize: 26,
                                fontWeight: FontWeight.bold,
                                letterSpacing: 1.5,
                              ),
                            ),
                          ],
                        ),
                      ),
                      const Spacer(),
                    ],
                  ),
                ),
              ),
            ),

            // القسم السفلي الأبيض مع حقول الإدخال
            Expanded(
              child: Padding(
                padding: const EdgeInsets.all(24.0),
                child: SingleChildScrollView(
                  child: Column(
                    children: [
                      const SizedBox(height: 10),
                      // حقل رقم المعرف
                      TextField(
                        decoration: InputDecoration(
                          hintText: 'أدخل رقم المعرف (رقم الحساب أو 2...)',
                          hintStyle: const TextStyle(color: Colors.grey, fontSize: 14),
                          prefixIcon: const Icon(Icons.badge_outlined, color: Colors.grey),
                          filled: true,
                          fillColor: Colors.white,
                          contentPadding: const EdgeInsets.symmetric(vertical: 16),
                          enabledBorder: OutlineInputBorder(
                            borderRadius: BorderRadius.circular(8),
                            borderSide: const BorderSide(color: Colors.grey, width: 0.8),
                          ),
                          focusedBorder: OutlineInputBorder(
                            borderRadius: BorderRadius.circular(8),
                            borderSide: const BorderSide(color: Color(0xFFD32F2F), width: 1.5),
                          ),
                        ),
                      ),
                      const SizedBox(height: 16),
                      // حقل كلمة المرور
                      TextField(
                        obscureText: true,
                        decoration: InputDecoration(
                          hintText: 'أدخل كلمة المرور',
                          hintStyle: const TextStyle(color: Colors.grey, fontSize: 14),
                          prefixIcon: const Icon(Icons.visibility_off_outlined, color: Colors.grey),
                          filled: true,
                          fillColor: Colors.white,
                          contentPadding: const EdgeInsets.symmetric(vertical: 16),
                          enabledBorder: OutlineInputBorder(
                            borderRadius: BorderRadius.circular(8),
                            borderSide: const BorderSide(color: Colors.grey, width: 0.8),
                          ),
                          focusedBorder: OutlineInputBorder(
                            borderRadius: BorderRadius.circular(8),
                            borderSide: const BorderSide(color: Color(0xFFD32F2F), width: 1.5),
                          ),
                        ),
                      ),
                      const SizedBox(height: 24),
                      // زر تسجيل الدخول
                      SizedBox(
                        width: double.infinity,
                        height: 50,
                        child: ElevatedButton(
                          onPressed: () {},
                          style: ElevatedButton.styleFrom(
                            backgroundColor: const Color(0xFFD32F2F),
                            shape: RoundedRectangleBorder(
                              borderRadius: BorderRadius.circular(8),
                            ),
                            elevation: 3,
                          ),
                          child: const Text(
                            'تسجيل الدخول',
                            style: TextStyle(
                              color: Colors.white,
                              fontSize: 16,
                              fontWeight: FontWeight.bold,
                            ),
                          ),
                        ),
                      ),
                      const SizedBox(height: 24),
                      // روابط التسجيل والمساعدة
                      const Row(
                        mainAxisAlignment: MainAxisAlignment.spaceBetween,
                        children: [
                          Text(
                            'لا تستطيع تسجيل الدخول؟',
                            style: TextStyle(color: Colors.grey, fontSize: 13),
                          ),
                          Text(
                            'تسجيل جديد؟',
                            style: TextStyle(color: Colors.grey, fontSize: 13),
                          ),
                        ],
                      ),
                      const SizedBox(height: 40),
                      // الأيقونات السفلية (بنك الخرطوم، المساعدة، المواقع، فيسبوك)
                      const Row(
                        mainAxisAlignment: MainAxisAlignment.spaceAround,
                        children: [
                          FooterIcon(icon: Icons.account_balance, label: 'بنك الخرطوم', color: Colors.green),
                          FooterIcon(icon: Icons.location_on, label: 'مواقعنا', color: Colors.red),
                          FooterIcon(icon: Icons.headset_mic, label: 'المساعدة', color: Colors.green),
                          FooterIcon(icon: Icons.facebook, label: 'فيس بوك', color: Colors.blue),
                        ],
                      ),
                    ],
                  ),
                ),
              ),
            ),
          ],
        ),
      ),
    );
  }
}

// ودجت مخصصة للأيقونات السفلية
class FooterIcon extends StatelessWidget {
  const FooterIcon({super.key, required this.icon, required this.label, required this.color});

  final IconData icon;
  final String label;
  final Color color;

  @override
  Widget build(BuildContext context) {
    return Column(
      children: [
        Container(
          padding: const EdgeInsets.all(10),
          decoration: BoxDecoration(
            shape: BoxShape.circle,
            border: Border.all(color: color, width: 1.5),
          ),
          child: Icon(icon, color: color, size: 22),
        ),
        const SizedBox(height: 6),
        Text(
          label,
          style: const TextStyle(color: Colors.grey, fontSize: 11),
        ),
      ],
    );
  }
}
