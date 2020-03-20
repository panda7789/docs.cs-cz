---
title: Výchozí chování zařazování
ms.date: 06/26/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- interop marshaling, default
- interoperation with unmanaged code, marshaling
- marshaling behavior
ms.assetid: c0a9bcdf-3df8-4db3-b1b6-abbdb2af809a
ms.openlocfilehash: 18282d14540027e4fae4fe152d3867ad8c223c37
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181485"
---
# <a name="default-marshaling-behavior"></a>Výchozí chování zařazování
Interop zařazování pracuje na pravidla, která určují, jak se chovají data spojená s parametry metody, jak prochází mezi spravované a nespravované paměti. Tato předdefinovaná pravidla řídí takové zařazovací aktivity jako transformace datového typu, zda volaný může změnit data předávaná a vrátit tyto změny volajícímu a za jakých okolností zařazování poskytuje optimalizace výkonu.  
  
 Tato část identifikuje výchozí charakteristiky chování interop zařazování služby. Představuje podrobné informace o zařazování polí, booleovské typy, char typy, delegáti, třídy, objekty, řetězce a struktury.  
  
> [!NOTE]
> Zařazování obecných typů není podporováno. Další informace naleznete v tématu [Spolupráce pomocí obecných typů](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229590(v=vs.100)).  
  
## <a name="memory-management-with-the-interop-marshaler"></a>Správa paměti s interop zařazovacím zařízením  
 Interop zařazovací vždy pokusí uvolnit paměť přidělenou nespravovaný kód. Toto chování je v souladu s pravidly správy paměti modelu COM, ale liší se od pravidel, která řídí nativní C++.  
  
 Zmatek může vzniknout, pokud očekáváte nativní chování jazyka C++ (bez uvolnění paměti) při použití platformy invoke, která automaticky uvolní paměť pro ukazatele. Například volání následující nespravované metody z dll C++ automaticky neuvolní žádnou paměť.  
  
### <a name="unmanaged-signature"></a>Nespravovaný podpis  
  
```cpp  
BSTR MethodOne (BSTR b) {  
     return b;  
}  
```  
  
 Pokud však definujete metodu jako platformu vyvolat prototyp, <xref:System.String> nahraďte `MethodOne`každý typ **BSTR** typem `b` a volání , běžný jazyk runtime pokusí uvolnit dvakrát. Chování zařazování můžete <xref:System.IntPtr> změnit pomocí typů, nikoli typů **String.**  
  
 Runtime vždy používá **CoTaskMemFree** metoda uvolnit paměť. Pokud paměť, se kterou pracujete, nebyla přidělena metodou **CoTaskMemAlloc,** musíte použít **IntPtr** a uvolnit paměť ručně pomocí příslušné metody. Podobně se můžete vyhnout automatickému uvolnění paměti v situacích, kdy by paměť neměla být nikdy uvolněna, například při použití funkce **GetCommandLine** z kernel32.dll, která vrací ukazatel na paměť jádra. Podrobnosti o ručním uvolnění paměti naleznete v [tématu Ukázka vyrovnávacích pamětí](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/x3txb6xc(v=vs.100)).  
  
## <a name="default-marshaling-for-classes"></a>Výchozí zařazování pro třídy  
 Třídy mohou být zařazeny pouze pomocí interop com a jsou vždy zařazeny jako rozhraní. V některých případech rozhraní slouží k zařazovací třídy je označována jako rozhraní třídy. Informace o přepsání rozhraní třídy s rozhraním podle vašeho výběru naleznete [v tématu Zavedení rozhraní třídy](../../standard/native-interop/com-callable-wrapper.md#introducing-the-class-interface).  
  
### <a name="passing-classes-to-com"></a>Předávání tříd com  
 Pokud je spravovaná třída předána com, interop zařazování automaticky zabalí třídu s proxy com a předá rozhraní třídy vytvořené proxy volání metody COM. Proxy pak deleguje všechna volání na rozhraní třídy zpět na spravovaný objekt. Proxy také zveřejňuje další rozhraní, které nejsou explicitně implementovány třídy. Proxy server automaticky implementuje rozhraní, jako je **Například IUnknown** a **IDispatch** jménem třídy.  
  
### <a name="passing-classes-to-net-code"></a>Předávání tříd do kódu .NET  
 Coclasses nejsou obvykle používány jako argumenty metody v com. Místo toho je výchozí rozhraní obvykle předáno místo coclass.  
  
 Při předání rozhraní do spravovaného kódu interop zařazovací modul je zodpovědný za zabalení rozhraní s správné obálky a předání obálky spravované metody. Určení, který obal použít může být obtížné. Každá instance objektu COM má jeden jedinečný obal bez ohledu na to, kolik rozhraní objekt implementuje. Například jeden objekt COM, který implementuje pět odlišných rozhraní má pouze jeden obálku. Stejný obálka zveřejňuje všech pět rozhraní. Pokud jsou vytvořeny dvě instance objektu COM, pak jsou vytvořeny dvě instance obálky.  
  
 Aby obálka zachovala stejný typ po celou dobu jeho životnosti, zařazovací modul interop musí identifikovat správné obálky při prvním průchodu rozhraní vystaveného objektem prostřednictvím zařazovacího modulu. Zařazovací objekt identifikuje objekt při pohledu na jedno z rozhraní, které objekt implementuje.  
  
 Například zařazování určuje, že obálka třídy by měla být použita k zalomení rozhraní, které bylo předáno do spravovaného kódu. Při prvním předání rozhraní prostřednictvím zařazovacího modulu zařazovací modul, zařazovací objekt zkontroluje, zda rozhraní pochází ze známého objektu. Tato kontrola se vyskytuje ve dvou situacích:  
  
- Rozhraní je implementováno jiným spravovaným objektem, který byl předán com jinde. Zařazovací modul může snadno identifikovat rozhraní vystavená spravovanými objekty a je schopen spárovat rozhraní se spravovaným objektem, který poskytuje implementaci. Spravovaný objekt je pak předán metodě a není potřeba žádné obálky.  
  
- Objekt, který již byl zabalen, implementuje rozhraní. Chcete-li zjistit, zda se jedná o tento případ, zařazovací zařízení dotazuje objekt pro jeho **rozhraní IUnknown** a porovná vrácené rozhraní rozhraní jiných objektů, které jsou již zabaleny. Pokud je rozhraní stejné jako u jiné obálky, objekty mají stejnou identitu a existující obálka je předána metodě.  
  
 Pokud rozhraní není z známého objektu, zařazovací provádí následující akce:  
  
1. Zařazovací objekt dotazuje objekt pro rozhraní **IProvideClassInfo2.** Pokud je k dispozici, zařazování používá CLSID vrácené z **IProvideClassInfo2.GetGUID** k identifikaci coclass poskytující rozhraní. Pomocí CLSID zařazování můžete vyhledat obálku z registru, pokud sestavení bylo dříve registrováno.  
  
2. Zařazovací zařízení dotazuje rozhraní pro rozhraní **IProvideClassInfo.** Pokud je k dispozici, zařazování používá **ITypeInfo** vrácené z **IProvideClassInfo.GetClassinfo** k určení CLSID třídy vystavení rozhraní. Zařazování můžete použít CLSID vyhledejte metadata pro obálku.  
  
3. Pokud zařazování stále nemůže identifikovat třídu, zabalí rozhraní s obecnou třídou obálky nazvanou **System.__ComObject**.  
  
## <a name="default-marshaling-for-delegates"></a>Výchozí zařazování delegátů  
 Spravovaný delegát je zařazen jako rozhraní COM nebo jako ukazatel funkce na základě volajícího mechanismu:  
  
- Pro vyvolání platformy delegát adekvátní je zařazen jako ukazatel nespravované funkce ve výchozím nastavení.  
  
- Pro interop COM delegát je zařazen jako com rozhraní typu **_Delegate** ve výchozím nastavení. Rozhraní **_Delegate** je definováno v knihovně typů Mscorlib.tlb a obsahuje metodu, <xref:System.Delegate.DynamicInvoke%2A?displayProperty=nameWithType> která umožňuje volat metodu, na kterou delegát odkazuje.  
  
 V následující tabulce jsou uvedeny možnosti zařazování pro datový typ spravovaného delegáta. Atribut <xref:System.Runtime.InteropServices.MarshalAsAttribute> poskytuje <xref:System.Runtime.InteropServices.UnmanagedType> několik hodnot výčtu pro delegáty zařazování.  
  
|Typ výčtu|Popis nespravovaného formátu|  
|----------------------|-------------------------------------|  
|**UnmanagedType.FunctionPtr**|Ukazatel nespravované funkce.|  
|**UnmanagedType.Interface**|Rozhraní typu **_Delegate**, jak je definováno v mscorlib.tlb.|  
  
 Zvažte následující příklad kódu, `DelegateTestInterface` ve kterém jsou metody exportovány do knihovny typů COM. Všimněte si, že pouze delegáti označené **ref** (nebo **ByRef**) klíčové slovo jsou předány jako In/Out parametry.  
  
```csharp  
using System;  
using System.Runtime.InteropServices;  
  
public interface DelegateTest {  
void m1(Delegate d);  
void m2([MarshalAs(UnmanagedType.Interface)] Delegate d);
void m3([MarshalAs(UnmanagedType.Interface)] ref Delegate d);
void m4([MarshalAs(UnmanagedType.FunctionPtr)] Delegate d);
void m5([MarshalAs(UnmanagedType.FunctionPtr)] ref Delegate d);
}  
```  
  
### <a name="type-library-representation"></a>Reprezentace knihovny typů  
  
```cpp  
importlib("mscorlib.tlb");  
interface DelegateTest : IDispatch {  
[id(…)] HRESULT m1([in] _Delegate* d);  
[id(…)] HRESULT m2([in] _Delegate* d);  
[id(…)] HRESULT m3([in, out] _Delegate** d);  
[id()] HRESULT m4([in] int d);  
[id()] HRESULT m5([in, out] int *d);  
   };  
```  
  
 Ukazatel funkce může být odkazován, stejně jako jakýkoli jiný ukazatel nespravované funkce může být dereferenced.  

V tomto příkladu při dva delegáti jsou zařazeny jako <xref:System.Runtime.InteropServices.UnmanagedType.FunctionPtr?displayProperty=nameWithType>, výsledkem `int` je a ukazatel na . `int` Vzhledem k tomu, `int` že jsou zařazovány typy delegátů, představuje zde ukazatel na void (`void*`), což je adresa delegáta v paměti. Jinými slovy, tento výsledek je specifický pro 32bitové systémy Windows, protože `int` zde představuje velikost ukazatele funkce.

> [!NOTE]
> Odkaz na ukazatel funkce na spravovaného delegáta drženého nespravovaným kódem nebrání tomu, aby soubor RUNTIME společného jazyka provedl uvolňování paměti spravovaného objektu.  
  
 Například následující kód je nesprávný, `cb` protože odkaz na `SetChangeHandler` objekt, předaný metodě, neudržuje `cb` naživu mimo životnost `Test` metody. Jakmile `cb` je objekt uvolněn, ukazatel funkce `SetChangeHandler` předaný již není platný.  
  
```csharp  
public class ExternalAPI {  
   [DllImport("External.dll")]  
   public static extern void SetChangeHandler(  
      [MarshalAs(UnmanagedType.FunctionPtr)]ChangeDelegate d);  
}  
public delegate bool ChangeDelegate([MarshalAs(UnmanagedType.LPWStr) string S);  
public class CallBackClass {  
   public bool OnChange(string S){ return true;}  
}  
internal class DelegateTest {  
   public static void Test() {  
      CallBackClass cb = new CallBackClass();  
      // Caution: The following reference on the cb object does not keep the
      // object from being garbage collected after the Main method
      // executes.  
      ExternalAPI.SetChangeHandler(new ChangeDelegate(cb.OnChange));
   }  
}  
```  
  
 Chcete-li kompenzovat neočekávané uvolnění paměti, volající musí zajistit, že `cb` objekt je udržována naživu tak dlouho, dokud nespravované funkce ukazatel je používán. Volitelně můžete mít nespravovaný kód upozornit spravovaný kód, když ukazatel funkce již není potřeba, jak ukazuje následující příklad.  
  
```csharp  
internal class DelegateTest {  
   CallBackClass cb;  
   // Called before ever using the callback function.  
   public static void SetChangeHandler() {  
      cb = new CallBackClass();  
      ExternalAPI.SetChangeHandler(new ChangeDelegate(cb.OnChange));  
   }  
   // Called after using the callback function for the last time.  
   public static void RemoveChangeHandler() {  
      // The cb object can be collected now. The unmanaged code is
      // finished with the callback function.  
      cb = null;  
   }  
}  
```  
  
## <a name="default-marshaling-for-value-types"></a>Výchozí zařazování pro typy hodnot  
 Většina typů hodnot, například celá čísla a čísla s plovoucí desetinnou desetinnou hodnotou, jsou [přenositelná](blittable-and-non-blittable-types.md) a nevyžadují zařazování. Jiné [nepřenositelné](blittable-and-non-blittable-types.md) typy mají odlišné reprezentace ve spravované a nespravované paměti a vyžadují zařazování. Ještě jiné typy vyžadují explicitní formátování přes hranice spolupráce.  
  
 Tato část obsahuje informace o následujících formátovaných typech hodnot:  
  
- [Typy hodnot používané v vyvolání platformy](#value-types-used-in-platform-invoke)  
  
- [Typy hodnot používané v interopu com](#value-types-used-in-com-interop)  
  
 Kromě popisu formátované typy, toto téma identifikuje [typy systémových hodnot,](#system-value-types) které mají neobvyklé zařazování chování.  
  
 Formátovaný typ je komplexní typ, který obsahuje informace, které explicitně řídí rozložení svých členů v paměti. Informace o rozložení člena jsou <xref:System.Runtime.InteropServices.StructLayoutAttribute> k dispozici pomocí atributu. Rozložení může být jedna <xref:System.Runtime.InteropServices.LayoutKind> z následujících hodnot výčtu:  
  
- **LayoutKind.Automatic**  
  
     Označuje, že běžný jazyk runtime je zdarma ke snížení pořadí členů typu pro efektivitu. Však při zadání typu hodnoty do nespravovaného kódu, rozložení členů je předvídatelné. Pokus o zařazovací takové struktury automaticky způsobí výjimku.  
  
- **LayoutKind.Sekvenční**  
  
     Označuje, že členy typu mají být rozloženy v nespravované paměti ve stejném pořadí, ve kterém se zobrazí v definici spravovaného typu.  
  
- **LayoutKind.Explicit**  
  
     Označuje, že členy jsou rozloženy podle dodaného <xref:System.Runtime.InteropServices.FieldOffsetAttribute> s každým polem.  
  
### <a name="value-types-used-in-platform-invoke"></a>Typy hodnot používané v vyvolání platformy  
 V následujícím `Point` příkladu `Rect` a typy poskytují informace o rozložení členů pomocí **atributu StructLayoutAttribute**.  
  
```vb  
Imports System.Runtime.InteropServices  
<StructLayout(LayoutKind.Sequential)> Public Structure Point  
   Public x As Integer  
   Public y As Integer  
End Structure  
<StructLayout(LayoutKind.Explicit)> Public Structure Rect  
   <FieldOffset(0)> Public left As Integer  
   <FieldOffset(4)> Public top As Integer  
   <FieldOffset(8)> Public right As Integer  
   <FieldOffset(12)> Public bottom As Integer  
End Structure  
```  
  
```csharp  
using System.Runtime.InteropServices;  
[StructLayout(LayoutKind.Sequential)]  
public struct Point {  
   public int x;  
   public int y;  
}
  
[StructLayout(LayoutKind.Explicit)]  
public struct Rect {  
   [FieldOffset(0)] public int left;  
   [FieldOffset(4)] public int top;  
   [FieldOffset(8)] public int right;  
   [FieldOffset(12)] public int bottom;  
}  
```  
  
 Při zařazené do nespravovaného kódu jsou tyto formátované typy zařazeny jako struktury stylu C. To poskytuje snadný způsob volání nespravovanérozhraní API, které má argumenty struktury. Například `POINT` a struktury mohou být předány microsoft windows api **PtInRect** funkce takto: `RECT`  
  
```cpp  
BOOL PtInRect(const RECT *lprc, POINT pt);  
```  
  
 Můžete předat struktury pomocí následující platformy vyvolat definici:  
  
```vb
Friend Class NativeMethods
    Friend Declare Auto Function PtInRect Lib "User32.dll" (
        ByRef r As Rect, p As Point) As Boolean
End Class
```
  
```csharp
internal static class NativeMethods
{
   [DllImport("User32.dll")]
   internal static extern bool PtInRect(ref Rect r, Point p);
}
```
  
 Typ `Rect` hodnoty musí být předán odkazem, protože nespravované `RECT` rozhraní API očekává ukazatel na a, který má být předán funkci. Typ `Point` hodnoty je předán hodnotou, protože nespravované rozhraní API očekává, že `POINT` bude předán v zásobníku. Tento jemný rozdíl je velmi důležitý. Odkazy jsou předávány nespravovanému kódu jako ukazatele. Hodnoty jsou předávány nespravovanému kódu v zásobníku.  
  
> [!NOTE]
> Pokud formátovaný typ je zařazen jako struktura, pouze pole v rámci typu jsou přístupné. Pokud typ má metody, vlastnosti nebo události, jsou nepřístupné z nespravovaného kódu.  
  
 Třídy mohou být také zařazeny do nespravovaného kódu jako struktury ve stylu C za předpokladu, že mají pevné rozložení členů. Informace o rozložení člena pro třídu <xref:System.Runtime.InteropServices.StructLayoutAttribute> jsou také k dispozici s atributem. Hlavní rozdíl mezi typy hodnot s pevným rozložením a třídami s pevným rozložením je způsob, jakým jsou zařazeny do nespravovaného kódu. Typy hodnot jsou předávány hodnotou (v zásobníku) a následně všechny změny provedené na členy typu volaného nejsou vidět volající. Typy odkazů jsou předávány odkazem (odkaz na typ je předán v zásobníku); v důsledku toho všechny změny provedené na blittable typu členů typu volaného jsou vidět volajícího.  
  
> [!NOTE]
> Pokud typ odkazu má členy non-přenositelné typy, převod je vyžadován dvakrát: při prvním při předání argumentu na nespravované straně a podruhé při návratu z volání. Z důvodu této přidané režie In/Out parametry musí být explicitně použita na argument, pokud volající chce zobrazit změny provedené volaným.  
  
 V následujícím příkladu `SystemTime` má třída sekvenční rozložení členů a může být předána funkci **GetSystemTime** rozhraní API systému Windows.  
  
```vb  
<StructLayout(LayoutKind.Sequential)> Public Class SystemTime  
   Public wYear As System.UInt16  
   Public wMonth As System.UInt16  
   Public wDayOfWeek As System.UInt16  
   Public wDay As System.UInt16  
   Public wHour As System.UInt16  
   Public wMinute As System.UInt16  
   Public wSecond As System.UInt16  
   Public wMilliseconds As System.UInt16  
End Class  
```  
  
```csharp  
[StructLayout(LayoutKind.Sequential)]  
   public class SystemTime {  
   public ushort wYear;
   public ushort wMonth;  
   public ushort wDayOfWeek;
   public ushort wDay;
   public ushort wHour;
   public ushort wMinute;
   public ushort wSecond;
   public ushort wMilliseconds;
}  
```  
  
 Funkce **GetSystemTime** je definována takto:  
  
```cpp  
void GetSystemTime(SYSTEMTIME* SystemTime);  
```  
  
 Ekvivalentní definice vyvolání platformy pro **GetSystemTime** je následující:  
  
```vb
Friend Class NativeMethods
    Friend Declare Auto Sub GetSystemTime Lib "Kernel32.dll" (
        ByVal sysTime As SystemTime)
End Class
```
  
```csharp
internal static class NativeMethods
{
   [DllImport("Kernel32.dll", CharSet = CharSet.Auto)]
   internal static extern void GetSystemTime(SystemTime st);
}
```
  
 Všimněte `SystemTime` si, že argument není zadán `SystemTime` jako referenční argument, protože je třída, nikoli typ hodnoty. Na rozdíl od typů hodnot jsou třídy vždy předávány odkazem.  
  
 Následující příklad kódu ukazuje `Point` jinou třídu, která má metodu nazvanou `SetXY`. Vzhledem k tomu, že typ má sekvenční rozložení, může být předán do nespravovaného kódu a zařazen jako struktura. `SetXY` Člen však není volatelný z nespravovaného kódu, i když je objekt předán odkazem.  
  
```vb  
<StructLayout(LayoutKind.Sequential)> Public Class Point  
   Private x, y As Integer  
   Public Sub SetXY(x As Integer, y As Integer)  
      Me.x = x  
      Me.y = y  
   End Sub  
End Class  
```  
  
```csharp  
[StructLayout(LayoutKind.Sequential)]  
public class Point {  
   int x, y;  
   public void SetXY(int x, int y){
      this.x = x;  
      this.y = y;  
   }  
}  
```  
  
### <a name="value-types-used-in-com-interop"></a>Typy hodnot používané v interopu com  
 Formátované typy lze také předat volání metod interop com. Ve skutečnosti při exportu do knihovny typů jsou typy hodnot automaticky převedeny na struktury. Jak ukazuje následující příklad, typ `Point` hodnoty se stane definicí `Point`typu (typedef) s názvem . Všechny odkazy na `Point` typ hodnoty jinde v knihovně `Point` typů jsou nahrazeny typedef.  
  
 **Reprezentace knihovny typů**  
  
```cpp  
typedef struct tagPoint {  
   int x;  
   int y;  
} Point;  
interface _Graphics {  
   …  
   HRESULT SetPoint ([in] Point p)  
   HRESULT SetPointRef ([in,out] Point *p)  
   HRESULT GetPoint ([out,retval] Point *p)  
}  
```  
  
 Stejná pravidla používaná k zařazování hodnot a odkazů na volání vyvolání platformy se používají při zařazování prostřednictvím rozhraní COM. Například při předání instance `Point` typu hodnoty z rozhraní COM frameworku `Point` .NET, je předána hodnotou. Pokud `Point` je typ hodnoty předán odkazem, `Point` je v zásobníku předán ukazatel na a. Interop zařazování nepodporuje vyšší úrovně dereference **(Point)** \* \*v obou směrech.  
  
> [!NOTE]
> Struktury s <xref:System.Runtime.InteropServices.LayoutKind> hodnotou výčtu nastavenou na **explicit** nelze použít v interop u com, protože exportovaná knihovna typů nemůže vyjádřit explicitní rozložení.  
  
### <a name="system-value-types"></a>Typy systémových hodnot  
 Obor <xref:System> názvů má několik typů hodnot, které představují zabalenou formu primitivních typů runtime. Například struktura typu <xref:System.Int32?displayProperty=nameWithType> hodnoty představuje zarámečkovou formu **ELEMENT_TYPE_I4**. Namísto zařazování těchto typů jako struktury, jako jsou jiné formátované typy, zařazujete je stejným způsobem jako primitivní typy, které zadávají. **System.Int32** je proto zařazen jako **ELEMENT_TYPE_I4** namísto jako struktura obsahující jeden člen typu **long**. Následující tabulka obsahuje seznam typů hodnot v oboru názvů **Systém,** které jsou v rámečku reprezentace primitivních typů.  
  
|Typ systémové hodnoty|Typ prvku|  
|-----------------------|------------------|  
|<xref:System.Boolean?displayProperty=nameWithType>|**ELEMENT_TYPE_BOOLEAN**|  
|<xref:System.SByte?displayProperty=nameWithType>|**ELEMENT_TYPE_I1**|  
|<xref:System.Byte?displayProperty=nameWithType>|**ELEMENT_TYPE_UI1**|  
|<xref:System.Char?displayProperty=nameWithType>|**ELEMENT_TYPE_CHAR**|  
|<xref:System.Int16?displayProperty=nameWithType>|**ELEMENT_TYPE_I2**|  
|<xref:System.UInt16?displayProperty=nameWithType>|**ELEMENT_TYPE_U2**|  
|<xref:System.Int32?displayProperty=nameWithType>|**ELEMENT_TYPE_I4**|  
|<xref:System.UInt32?displayProperty=nameWithType>|**ELEMENT_TYPE_U4**|  
|<xref:System.Int64?displayProperty=nameWithType>|**ELEMENT_TYPE_I8**|  
|<xref:System.UInt64?displayProperty=nameWithType>|**ELEMENT_TYPE_U8**|  
|<xref:System.Single?displayProperty=nameWithType>|**ELEMENT_TYPE_R4**|  
|<xref:System.Double?displayProperty=nameWithType>|**ELEMENT_TYPE_R8**|  
|<xref:System.String?displayProperty=nameWithType>|**ELEMENT_TYPE_STRING**|  
|<xref:System.IntPtr?displayProperty=nameWithType>|**ELEMENT_TYPE_I**|  
|<xref:System.UIntPtr?displayProperty=nameWithType>|**ELEMENT_TYPE_U**|  
  
 Některé další typy hodnot v oboru názvů **systému** jsou zpracovány odlišně. Vzhledem k tomu, že nespravovaný kód již má dobře zavedené formáty pro tyto typy, zařazování má zvláštní pravidla pro jejich zařazování. V následující tabulce jsou uvedeny speciální typy hodnot v oboru názvů **Systém** a také nespravovaný typ, do kterého jsou zařazeny.  
  
|Typ systémové hodnoty|Typ IDL|  
|-----------------------|--------------|  
|<xref:System.DateTime?displayProperty=nameWithType>|**Datum**|  
|<xref:System.Decimal?displayProperty=nameWithType>|**Desetinných**|  
|<xref:System.Guid?displayProperty=nameWithType>|**Identifikátor guid**|  
|<xref:System.Drawing.Color?displayProperty=nameWithType>|**OLE_COLOR**|  
  
 Následující kód zobrazuje definici nespravovaných typů **DATE**, **GUID**, **DECIMAL**a **OLE_COLOR** v knihovně typů Stdole2.  
  
#### <a name="type-library-representation"></a>Reprezentace knihovny typů  
  
```cpp  
typedef double DATE;  
typedef DWORD OLE_COLOR;  
  
typedef struct tagDEC {  
    USHORT    wReserved;  
    BYTE      scale;  
    BYTE      sign;  
    ULONG     Hi32;  
    ULONGLONG Lo64;  
} DECIMAL;  
  
typedef struct tagGUID {  
    DWORD Data1;  
    WORD  Data2;  
    WORD  Data3;  
    BYTE  Data4[ 8 ];  
} GUID;  
```  
  
 Následující kód zobrazuje odpovídající definice ve `IValueTypes` spravovaném rozhraní.  
  
```vb  
Public Interface IValueTypes  
   Sub M1(d As System.DateTime)  
   Sub M2(d As System.Guid)  
   Sub M3(d As System.Decimal)  
   Sub M4(d As System.Drawing.Color)  
End Interface  
```  
  
```csharp  
public interface IValueTypes {  
   void M1(System.DateTime d);  
   void M2(System.Guid d);  
   void M3(System.Decimal d);  
   void M4(System.Drawing.Color d);  
}  
```  
  
#### <a name="type-library-representation"></a>Reprezentace knihovny typů  
  
```cpp  
[…]  
interface IValueTypes : IDispatch {  
   HRESULT M1([in] DATE d);  
   HRESULT M2([in] GUID d);  
   HRESULT M3([in] DECIMAL d);  
   HRESULT M4([in] OLE_COLOR d);  
};  
```  
  
## <a name="see-also"></a>Viz také

- [Přenositelné a nepřenositelné typy](blittable-and-non-blittable-types.md)
- [Kopírování a přichycování](copying-and-pinning.md)
- [Výchozí zařazování pro pole](default-marshaling-for-arrays.md)
- [Výchozí zařazování pro objekty](default-marshaling-for-objects.md)
- [Výchozí zařazování pro řetězce](default-marshaling-for-strings.md)
