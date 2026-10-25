# مبيعات بلس — نسخة تأسيسية أونلاين

## 1. إعداد Supabase
1. أنشئ مشروعًا مجانيًا على https://supabase.com
2. افتح SQL Editor والصق ملف `supabase.sql` كاملًا ثم Run.
3. من Project Settings > API انسخ Project URL و anon/public key.
4. ضع القيمتين في أول ملف `app.js`. لا تضع service_role key داخل ملفات الموقع.

## 2. إنشاء حساب المدير
1. من Authentication > Users أنشئ مستخدمًا ببريدك وكلمة مرور قوية.
2. انسخ UUID الخاص بالمستخدم.
3. في SQL Editor نفّذ الأمر التالي بعد استبدال القيم:
```sql
insert into public.employees(id,full_name,email,role,salary,leave_balance)
values('UUID-HERE','مدير النظام','YOUR-EMAIL@example.com','admin',0,21);
```

## 3. إضافة موظفين
أنشئ كل حساب من Authentication > Users في Supabase، ثم سجّل UUID والاسم والبريد من صفحة الموظفون داخل الموقع. لا تفتح التسجيل العام للناس.

## 4. النشر على Vercel
ارفع الملفات إلى GitHub ثم استورد المستودع من https://vercel.com. هذا موقع static ولا يحتاج build command. الكاميرا تعمل على رابط HTTPS.

## ملاحظات
- كود QR صالح 10 دقائق ويسجل وقت الخادم، لكن تصوير الكود أو مشاركة الحساب قد يسمح بالتلاعب؛ QR وحده لا يثبت وجود الموظف.
- خصم الإجازة تقديري: الراتب ÷ 30 × الأيام الزائدة. اضبط السياسة حسب نظام الشركة والقانون المحلي.
- هذه نسخة أولية؛ اختبرها ببيانات تجريبية قبل وضع بيانات موظفين حقيقية.
