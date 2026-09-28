# Buyurtma-holati-enum-va-literal-types
ypeScript
// ==========================================
// 1. String Enum
// ==========================================
enum BuyurtmaHolati {
    Kutilmoqda = "Kutilmoqda",
    Tasdiqlandi = "Tasdiqlandi",
    BekorQilindi = "Bekor Qilindi"
}

function holatniChopEt(holat: BuyurtmaHolati): void {
    console.log(`Buyurtma hozirgi holati: ${holat}`);
}

// Ishlatilishi:
holatniChopEt(BuyurtmaHolati.Tasdiqlandi);


// ==========================================
// 2. Literal Type Union va Narx Hisoblash
// ==========================================
type Olcham = "kichik" | "o'rta" | "katta";

function narxHisoblash(olcham: Olcham): number {
    switch (olcham) {
        case "kichik":
            return 15000;
        case "o'rta":
            return 25000;
        case "katta":
            return 35000;
    }
}

// Ishlatilishi:
const narx = narxHisoblash("o'rta"); // 25000


// ==========================================
# 3. Numeric Enum
// ==========================================
// Avtomatik ravishda 0'dan boshlab raqamlanadi:
// Past = 0, Orta = 1, Yuqori = 2
enum Prioritet {
    Past,
    Orta,
    Yuqori
}

const joriyPrioritet: Prioritet = Prioritet.Orta;
console.log(joriyPrioritet); // Natija konsolga 1 chiqaradi


// ==========================================
# 4. As Const (Const Assertion)
// ==========================================
const dokkonSozlamalari = {
    valyuta: "UZS",
    yetkazishMuddatiKun: 2,
    filiallarToshkentda: true
} as const;

// dokkonSozlamalari.valyuta = "USD"; 
// XATO: 'valyuta' o'qish uchun (readonly) chunki 'as const' uni o'zgarmas qilgan.


// ==========================================
# 5. Xato qiymat berishga urinish va tushuntirish
// ==========================================

// --- Xato 1: Literal turga mos kelmagan qiymat
// const notoGriOlmach: Olcham = "juda_katta"; 
/* 
   XATOLIK TUSHUNTIRISHI:
   TypeScript quyidagi xatoni beradi: 
   Type '"juda_katta"' is not assignable to type 'Olmach'.
   Sababi: 'Olmach' turi faqat aniq 3 ta ("kichik" | "o'rta" | "katta") matnli qiymatni 
   qabul qilishi mumkin. Boshqa har qanday matn ruxsat etilmaydi.
*/

// --- Xato 2: String Enum'ga mavjud bo'lmagan qiymatni berish
// const notoGriHolat: BuyurtmaHolati = "Bajarildi";
/* 
   XATOLIK TUSHUNTIRISHI:
   'BuyurtmaHolati' string enum'i faqat uning ichida e'lon qilingan a'zolarni 
   (Kutilmoqda, Tasdiqlandi, BekorQilindi) qabul qiladi. "Bajarildi" matni 
   bu enum ro'yxatida yo'qligi uchun TypeScript xato qaytaradi.
*/
Modulning asosiy qismlari qanday ishlaydi?
String Enum (BuyurtmaHolati): Matnli qiymatlarni aniq nomlar bilan bog'lab qo'yish uchun xizmat qiladi.

Literal Type (Olmach): O'zgaruvchiga faqat bitta yoki bir nechta aniq satrlarni (string) o'zlashtirish imkonini beradi.

Numeric Enum (Prioritet): Raqamli indekslar bilan ishlaydigan qiymatlar to'plami bo'lib, sukut bo'yicha 0 dan boshlab raqamlanadi.

as const: Oddiy obyektni to'liq readonly (o'qish uchun) holatga o'tkazib, uning xossalarini oddiy turdan aniq literal turga o'giradi.
