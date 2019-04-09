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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3c15e24fbe2a131435fe71782c8a55f416f71d62
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59129321"
---
# <a name="default-marshaling-behavior"></a>Výchozí chování zařazování
Zařazování spolupráce funguje v pravidlech této diktování chování data související s parametry metody během mezi spravovanými a nespravovanými paměti. Tato integrovaná pravidla takové zařazování aktivity jako typ transformace dat, řízení, zda volaný můžete změnit data předaná do ní a tyto změny vrátit volající a pod kterým okolností, aby zařazování odvozovalo poskytuje optimalizace výkonu.  
  
 Tato část popisuje výchozí chování vlastnosti zprostředkovatele komunikace s objekty zařazování služby. Představuje podrobné informace o zařazování polí, logické typy, typy char, delegátů, tříd, objektů, řetězce a struktury.  
  
> [!NOTE]
>  Zařazování obecných typů není podporováno. Další informace najdete v tématu [spolupráce pomocí obecných typů](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229590(v=vs.100)).  
  
## <a name="memory-management-with-the-interop-marshaler"></a>Správa paměti zařazovacím modulem spolupráce  
 Interoperační zařazovač se vždy pokusí uvolnit paměť přidělaná nespravovaného kódu. Toto chování v souladu s pravidly správy paměti modelu COM, ale liší se od pravidel, kterými se řídí nativní kód C++.  
  
 Pokud očekáváte, že nativní chování jazyka C++ (žádná uvolnění paměti) může dojít k záměně při používání platformy vyvolat, který automaticky uvolní paměť pro ukazatele. Například volání následující nespravované metody z knihovny DLL C++ neuvolní automaticky paměti.  
  
### <a name="unmanaged-signature"></a>Nespravovanému podpisu  
  
```cpp  
BSTR MethodOne (BSTR b) {  
     return b;  
}  
```  
  
 Nicméně pokud definujete metodu jako prototyp vyvolání platformy, nahraďte, každé **BSTR** typ s <xref:System.String> zadejte a volat `MethodOne`, modul common language runtime pokusí uvolnit `b` dvakrát. Můžete změnit chování zařazování pomocí <xref:System.IntPtr> typy spíše než **řetězec** typy.  
  
 Vždy používá modul runtime **CoTaskMemFree** metodu pro uvolnění paměti. Pokud nebyla přidělena paměť pracujete s **CoTaskMemAlloc** metoda, je nutné použít **IntPtr** a uvolňují paměť ručně pomocí odpovídající metodu. Podobně můžete vyhnout automatické paměti uvolnění v situacích, kde by nikdy být uvolnit paměť, například jako při použití **GetCommandLine** funkce ze souboru Kernel32.dll, které vrací ukazatel na paměť jádra. Podrobnosti o ručně uvolnění paměti, najdete v článku [vyrovnávací paměti – ukázka](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/x3txb6xc(v=vs.100)).  
  
## <a name="default-marshaling-for-classes"></a>Výchozí zařazování pro třídy  
 Třídy lze zařadit pouze pomocí zprostředkovatele komunikace s objekty COM a jsou vždy zařadit jako rozhraní. V některých případech rozhraní použitý k zařazování třídy se nazývá třídy rozhraní. Informace o přepsání rozhraní třídy s rozhraním podle vašeho výběru, najdete v části [představení rozhraní třídy](com-callable-wrapper.md#introducing-the-class-interface).  
  
### <a name="passing-classes-to-com"></a>Předání třídy modelu COM  
 Pokud spravované třídy je předán do modelu COM, interoperační zařazovač automaticky zabalí třídy pomocí serveru proxy modelu COM a předává třídu rozhraní vytvořené metodou proxy k volání metody COM. Proxy server potom postoupí všechna volání rozhraní třídy zpět do spravovaného objektu. Proxy server také poskytuje jiného rozhraní, které nejsou explicitně implementováno třídou. Proxy server automaticky implementuje rozhraní, jako například **IUnknown** a **IDispatch** jménem třídy.  
  
### <a name="passing-classes-to-net-code"></a>Předávání tříd pro kód .NET  
 Třídy typu coclass nejsou obvykle používají jako argumenty metody v modelu COM. Místo toho výchozí rozhraní se obvykle předává místo coclass.  
  
 Rozhraní je předána do spravovaného kódu, interoperační zařazovač zodpovídá za obtékání rozhraní s obálkou správné a předání obálku spravované metody. Určení, které obálky použití může být obtížné. Každá instance objektu COM má jeden, jedinečné obálku, bez ohledu na to, kolik rozhraní implementuje objekt. Například jeden objekt modelu COM, který implementuje rozhraní pět různých má pouze jeden obálky. Zpřístupňuje stejné obálky všech pět rozhraní. Pokud se vytvoří dvě instance objektu COM, jsou vytvořeny dva výskyty obálku.  
  
 Pro obálku zachovat stejný typ v průběhu svého životního cyklu interoperační zařazovač musí zjistit správné obálky, při prvním rozhraní vystavené objektu předána zařazování. Aby zařazování odvozovalo identifikuje objekt podle jednoho z rozhraní, které implementuje objekt.  
  
 V následujícím příkladu, aby zařazování odvozovalo Určuje, že by měl být obálkové třídy slouží k zabalení rozhraní, které bylo předáno do spravovaného kódu. Při zařazování se nejprve předává rozhraní, aby zařazování odvozovalo kontroluje, zda rozhraní pochází ze známého objektu. Tato kontrola probíhá ve dvou situacích:  
  
-   Rozhraní je prováděna jiný spravovaný objekt, který byl předán COM jinde. Zařazování mohli snadno identifikovat rozhraní vystavené spravovaných objektů a bude schopen odpovídat rozhraní s spravovaný objekt, který poskytuje implementaci. Spravovaný objekt je pak předán do metody a je zapotřebí žádné obálky.  
  
-   Objekt, který už je zabalená implementuje rozhraní. Pokud chcete zjistit, zda se jedná o tento případ, aby zařazování odvozovalo dotaz se týká objektu pro jeho **IUnknown** rozhraní a porovnává rozhraní vrácená rozhraním jiné objekty, které už jsou zabaleny. Pokud rozhraní je stejný jako u jiného obálky, objekty mají stejnou identitu a existující obálky je předán metodě.  
  
 Pokud rozhraní není od známých objektu, aby zařazování odvozovalo provede následující akce:  
  
1.  Aby zařazování odvozovalo dotaz se týká objektu pro **IProvideClassInfo2** rozhraní. Pokud je zadán, aby zařazování odvozovalo používá CLSID vrácená z **IProvideClassInfo2.GetGUID** k identifikaci coclass poskytuje rozhraní. S identifikátorem CLSID aby zařazování odvozovalo najdou obálky z registru Pokud sestavení byl dříve zaregistrován.  
  
2.  Aby zařazování odvozovalo dotazuje rozhraní pro **iprovideclassinfo –** rozhraní. Pokud je zadán, aby zařazování odvozovalo používá **ITypeInfo** vrácená **IProvideClassInfo.GetClassinfo** určit identifikátor CLSID třídy vystavení rozhraní. Zařazování lze použít k vyhledání metadat pro obálku identifikátor CLSID.  
  
3.  Pokud stále zařazování nemůže určovat třídu, zabalí rozhraní s obecný Obálkový třídu s názvem **System.__ComObject**.  
  
## <a name="default-marshaling-for-delegates"></a>Výchozí zařazování pro delegáty  
 Spravované delegáta je zařadit jako rozhraní modelu COM nebo jako ukazatel na funkci, na základě mechanismu volání:  
  
-   Pro platformu vyvolání, delegát je zařadit jako ukazatele nespravované funkce ve výchozím nastavení.  
  
-   Pro komunikace s objekty COM, delegát zařadit jako rozhraní modelu COM typu **_Delegate** ve výchozím nastavení. **_Delegate** rozhraní je definovaný v knihovně typů Mscorlib.tlb a obsahuje <xref:System.Delegate.DynamicInvoke%2A?displayProperty=nameWithType> metodu, která umožňuje volat metodu, která odkazuje na delegáta.  
  
 V následující tabulce jsou uvedeny zařazování možnosti pro datový typ spravovaného delegáta. <xref:System.Runtime.InteropServices.MarshalAsAttribute> Atribut nabízí několik <xref:System.Runtime.InteropServices.UnmanagedType> zařazování delegátů hodnot výčtu.  
  
|Typ výčtu|Popis nespravované formátu|  
|----------------------|-------------------------------------|  
|**UnmanagedType.FunctionPtr**|Ukazatel nespravované funkci.|  
|**UnmanagedType.Interface**|Rozhraní typu **_Delegate**, jak jsou definovány v knihovnu Mscorlib.tlb.|  
  
 Zvažte následující příklad kódu, ve kterém metody `DelegateTestInterface` jsou exportovány do knihovny typů modelu COM. Všimněte si, že pouze deleguje označené **ref** (nebo **ByRef**) – klíčové slovo jsou předány jako vstup a výstup parametry.  
  
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
  
### <a name="type-library-representation"></a>Knihovna reprezentaci typu  
  
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
  
 Ukazatel na funkci může být dereferencován, stejně jako může být dereferencován druhý ukazatel nespravované funkci.  

V tomto příkladu, pokud dva delegáty, které jsou zařazeny jako <xref:System.Runtime.InteropServices.UnmanagedType.FunctionPtr?displayProperty=nameWithType>, výsledek je `int` a ukazatel `int`. Protože se právě zařazovat typy delegátů, `int` zde představuje ukazatel na typu void (`void*`), což je adresa delegáta v paměti. Jinými slovy, tento výsledek je specifická pro 32bitové systémy Windows, v od té doby `int` zde představuje velikost ukazatele funkce.

> [!NOTE]
>  Odkaz na ukazatel funkce na spravované delegáta drží nespravovaný kód nezabrání modul common language runtime v provádění uvolnění paměti na spravovaný objekt.  
  
 Například následující kód je nesprávný protože odkaz na `cb` objekt předaný `SetChangeHandler` metody neudržuje `cb` aktivní za dobu životnosti `Test` – metoda. Jednou `cb` vynuceno uvolnění paměti je objekt, předán ukazatel funkce `SetChangeHandler` již není platný.  
  
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
  
 Pro kompenzaci neočekávané uvolňování paměti, volající musíte zajistit, aby `cb` objektu, zůstane aktivní, dokud se ukazatel Nespravované funkce používá. Volitelně můžete mít nespravovaný kód upozornit spravovaného kódu na ukazatel funkce už je nepotřebujete, jak ukazuje následující příklad.  
  
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
 Většina typy hodnot, jako jsou celá čísla a čísla s plovoucí desetinnou čárkou, jsou [blittable](blittable-and-non-blittable-types.md) a nevyžadují, aby zařazování. Další [nepřenositelné](blittable-and-non-blittable-types.md) typy mají odlišné reprezentace v spravované a nespravované paměti a nevyžadují zařazování. Jiné typy stále vyžadují explicitní formátování napříč hranicemi.  
  
 Tato část obsahuje informace o následujících typech formátovaná hodnota:  
  
-   [Typy hodnot používá v platformě vyvolání](#value-types-used-in-platform-invoke)  
  
-   [Typy hodnot používá ve spolupráci s COM](#value-types-used-in-com-interop)  
  
 Kromě popisující typy formátovaný, toto téma popisuje [systém hodnotou typy](#system-value-types) , které mají neobvyklé chování zařazování.  
  
 Formátovaný typ je komplexní typ, který obsahuje informace, které explicitně určuje rozložení z jejích členů v paměti. Informace o rozložení člen je prováděno pomocí <xref:System.Runtime.InteropServices.StructLayoutAttribute> atribut. Rozložení může být jedna z následujících <xref:System.Runtime.InteropServices.LayoutKind> hodnot výčtu:  
  
-   **LayoutKind.Automatic**  
  
     Označuje, že je modul common language runtime můžete změnit pořadí členů typu efektivitu. Pokud typ hodnoty je předán do nespravovaného kódu, rozložení členy ale předvídatelné. Pokus o zařazení takovouto strukturu automaticky dojde k výjimce.  
  
-   **LayoutKind.Sequential**  
  
     Označuje, že členy typu rozloží v nespravované paměti ve stejném pořadí, v jakém jsou uvedeny v definici spravovaného typu.  
  
-   **LayoutKind.Explicit**  
  
     Označuje, že členové jsou rozloženy podle <xref:System.Runtime.InteropServices.FieldOffsetAttribute> součástí každé pole.  
  
### <a name="value-types-used-in-platform-invoke"></a>Typy hodnot používá v platformě vyvolání  
 V následujícím příkladu `Point` a `Rect` typy poskytují člen informace o rozložení pomocí **StructLayoutAttribute –**.  
  
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
  
 Při zařazení na nespravovaný kód, jsou tyto typy formátovaný zařadit jako struktury C-style. To poskytuje snadný způsob volání nespravovaného rozhraní API, která má strukturu argumenty. Například `POINT` a `RECT` struktury mohou být předány do rozhraní API Microsoft Windows **PtInRect** funkce takto:  
  
```cpp  
BOOL PtInRect(const RECT *lprc, POINT pt);  
```  
  
 Můžete předat struktury použití následující platformy vyvolat definice:  
  
```vb
Friend Class WindowsAPI
    Friend Shared Declare Auto Function PtInRect Lib "User32.dll" (
        ByRef r As Rect, p As Point) As Boolean
End Class
```
  
```csharp
internal static class WindowsAPI
{
   [DllImport("User32.dll")]
   internal static extern bool PtInRect(ref Rect r, Point p);
}
```
  
 `Rect` Hodnotový typ musí být předány podle odkazu, protože nespravované rozhraní API očekává ukazatel `RECT` má být předán funkci. `Point` Typ hodnoty je předán podle hodnoty, protože nespravované rozhraní API očekává, že `POINT` mají být předány do zásobníku. Tento malý rozdíl je velmi důležité. Odkazy jsou předány do nespravovaného kódu jako ukazatele. Hodnoty jsou předány na nespravovaný kód v zásobníku.  
  
> [!NOTE]
>  Když formátovaný typ je zařazen jako strukturu, jsou přístupné pouze na pole v rámci typu. Pokud má typ metody, vlastnosti nebo události, je přístupný z nespravovaného kódu.  
  
 Třídy mohou také být zařazení na nespravovaný kód jako struktury stylu C, pokud došlo k nápravě rozložení. Informace o rozložení člen třídy je také součástí <xref:System.Runtime.InteropServices.StructLayoutAttribute> atribut. Hlavní rozdíl mezi typy hodnot s pevně rozložení a třídy s pevným rozložením je způsob, ve kterém jsou zařazení na nespravovaný kód. Typy hodnot jsou předávány hodnotou (v zásobníku), a proto neuvidí všechny změny provedené členy typu volaným volajícím. Typy odkazů jsou předány podle odkazu (odkaz na typ je předány do zásobníku); v důsledku toho se zobrazují všechny změny provedené na členy typu typu blittable volaným volajícím.  
  
> [!NOTE]
>  Pokud je odkazový typ členy nepřenositelné typy, je vyžadován převod dvakrát: poprvé, když je argument předaný do nespravované oblasti a druhý čas při návratu z volání. Kvůli tomu nároky parametry In nebo Out musí explicitně použít pro argument Pokud volající požaduje zobrazíte změny volaným.  
  
 V následujícím příkladu `SystemTime` třída má sekvenční rozložení a mohou být předány do rozhraní API Windows **GetSystemTime** funkce.  
  
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
  
 **GetSystemTime** funkce je definována takto:  
  
```cpp  
void GetSystemTime(SYSTEMTIME* SystemTime);  
```  
  
 Definice pro vyvolání ekvivalentní platformy **GetSystemTime** vypadá takto:  
  
```vb
Friend Class WindowsAPI
    Friend Shared Declare Auto Sub GetSystemTime Lib "Kernel32.dll" (
        ByVal sysTime As SystemTime)
End Class
```
  
```csharp
internal static class WindowsAPI
{
   [DllImport("Kernel32.dll", CharSet = CharSet.Auto)]
   internal static extern void GetSystemTime(SystemTime st);
}
```
  
 Všimněte si, že `SystemTime` argument není zadána jako argument typu odkaz, protože `SystemTime` je třída, nikoli typu hodnoty. Na rozdíl od typy hodnot jsou vždy třídy předány podle odkazu.  
  
 Následující příklad kódu ukazuje jiné `Point` třídu, která obsahuje metodu nazvanou `SetXY`. Protože tento typ nemá sekvenční rozložení, může být předán nespravovanému kódu a zařadit jako struktury. Ale `SetXY` člen se nedá volat z nespravovaného kódu i v případě, že objekt je předán odkazem.  
  
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
  
### <a name="value-types-used-in-com-interop"></a>Typy hodnot používá ve spolupráci s COM  
 Volání metody vzájemné spolupráce COM může být předán také formátovaný typy. Ve skutečnosti při exportu do knihovny typů, typů hodnot se automaticky převedou na struktury. Jak ukazuje následující příklad `Point` typ hodnoty změní typ definice (typedef) s názvem `Point`. Všude, kde `Point` jsou nahrazeny typ hodnoty jinde v knihovně typů `Point` typedef.  
  
 **Knihovna reprezentaci typu**  
  
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
  
 Stejná pravidla použitý k zařazování hodnoty a odkazy na platformu vyvolání volání se používají při zařazování prostřednictvím rozhraní modelu COM. Například, pokud instance `Point` z rozhraní .NET Framework do modelu COM, je předán typ hodnoty `Point` je předán podle hodnoty. Pokud `Point` typ hodnoty je předána odkazem, ukazatel `Point` předány v zásobníku. Interoperační zařazovač nepodporuje vyšší úrovní dereference (**bodu** \* \*) v obou směrech.  
  
> [!NOTE]
>  Struktury s <xref:System.Runtime.InteropServices.LayoutKind> nastavena na hodnotu výčtu **explicitní** nelze použít ve spolupráci s COM, protože exportované knihovny typů nemůže express s explicitním rozložením.  
  
### <a name="system-value-types"></a>Systém typů hodnot  
 <xref:System> Obor názvů má několik typy hodnot, které představují v podobě boxed primitivních typů modulu runtime. Například typ hodnoty <xref:System.Int32?displayProperty=nameWithType> struktura představuje v podobě boxed z **ELEMENT_TYPE_I4**. Místo zařazování typů jako struktury, jako ostatní typy formátovaný můžete přeuspořádat je stejným způsobem jako primitivní typy, které jsou pole. **System.Int32** proto zařazena jako **ELEMENT_TYPE_I4** místo jako struktura obsahující jednoho člena typu **dlouhé**. Následující tabulka obsahuje seznam typů hodnot v **systému** obor názvů, který jsou zabalené reprezentace primitivní typy.  
  
|Typ hodnoty systému|Typ elementu|  
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
  
 Některé hodnoty typů v **systému** obor názvů jsou zpracovány jinak. Protože nespravovaný kód už má zavedené formáty pro tyto typy, aby zařazování odvozovalo má zvláštní pravidla pro zařazování je. Následující tabulka uvádí typy zvláštní hodnota v **systému** obor názvů, a také jsou zařazeny do nespravovaného typu.  
  
|Typ hodnoty systému|IDL – typ|  
|-----------------------|--------------|  
|<xref:System.DateTime?displayProperty=nameWithType>|**DATE (Datum)**|  
|<xref:System.Decimal?displayProperty=nameWithType>|**DECIMAL**|  
|<xref:System.Guid?displayProperty=nameWithType>|**GUID**|  
|<xref:System.Drawing.Color?displayProperty=nameWithType>|**OLE_COLOR**|  
  
 Následující kód znázorňuje definici nespravovaných typů **datum**, **GUID**, **DESÍTKOVÉ**, a **OLE_COLOR** Stdole2 typu Knihovna.  
  
#### <a name="type-library-representation"></a>Knihovna reprezentaci typu  
  
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
  
 Následující kód ukazuje odpovídající definice v spravovanou `IValueTypes` rozhraní.  
  
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
  
#### <a name="type-library-representation"></a>Knihovna reprezentaci typu  
  
```cpp  
[…]  
interface IValueTypes : IDispatch {  
   HRESULT M1([in] DATE d);  
   HRESULT M2([in] GUID d);  
   HRESULT M3([in] DECIMAL d);  
   HRESULT M4([in] OLE_COLOR d);  
};  
```  
  
## <a name="see-also"></a>Viz také:

- [Přenositelné a nepřenositelné typy](blittable-and-non-blittable-types.md)
- [Kopírování a přichycování](copying-and-pinning.md)
- [Výchozí zařazování pro pole](default-marshaling-for-arrays.md)
- [Výchozí zařazování pro objekty](default-marshaling-for-objects.md)
- [Výchozí zařazování pro řetězce](default-marshaling-for-strings.md)
