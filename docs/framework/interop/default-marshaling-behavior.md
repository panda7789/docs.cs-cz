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
ms.openlocfilehash: 83bb8b0305e47ca7b354db03c7a9a3dd02f62d41
ms.sourcegitcommit: f9e38d31288fe5962e6be5b0cc286da633482873
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2018
ms.locfileid: "37028068"
---
# <a name="default-marshaling-behavior"></a>Výchozí chování zařazování
Zařazování spolupráce funguje v pravidlech že tu určují chování data související s parametry metody jak předává mezi spravovanými a nespravovanými paměti. Tyto vestavěné pravidla řízení takové zařazování aktivitám v podobě transformace typu dat, zda volaný můžete změnit data do ní předán a tyto změny vrátit volajícímu, a pod kterým okolností zařazování poskytuje optimalizace výkonu.  
  
 Tato část identifikuje výchozí chování charakteristika zprostředkovatel komunikace s objekty zařazování služby. Představuje podrobné informace o zařazování polí, logická hodnota typy, typy char, delegáti, tříd, objekty, řetězce a struktury.  
  
> [!NOTE]
>  Zařazování obecných typů není podporována. Další informace najdete v tématu [spolupráce pomocí obecných typů](https://msdn.microsoft.com/library/26b88e03-085b-4b53-94ba-a5a9c709ce58(v=vs.100)).  
  
## <a name="memory-management-with-the-interop-marshaler"></a>Správa paměti s spolupráce zařazování vláken  
 Zařazování spolupráce se vždy pokusí volné paměti přidělené nespravovaného kódu. Toto chování je v souladu s COM pravidla správy paměti, ale se liší od pravidla, která řídí nativní C++.  
  
 Pokud očekáváte, že nativní chování C++ (bez uvolnění paměti) může dojít k záměně při použití platformy vyvolání, které automaticky uvolní paměť pro ukazatele. Například volání následující nespravovanou metodu z knihovny DLL C++ neuvolní automaticky libovolná paměť.  
  
### <a name="unmanaged-signature"></a>Nespravované podpis  
  
```  
BSTR MethodOne (BSTR b) {  
     return b;  
}  
```  
  
 Ale pokud definujete metodu jako vyvolání prototypu platformy, nahraďte, každý **BSTR** zadejte s <xref:System.String> zadejte a volání `MethodOne`, modul se pokusí volné `b` dvakrát. Chování zařazování můžete změnit pomocí <xref:System.IntPtr> typy místo **řetězec** typy.  
  
 Modul runtime vždy používá **CoTaskMemFree** metodu pro uvolnění paměti. Pokud nebyl přiřazen paměti, že pracujete s **CoTaskMemAlloc** metodu, musíte použít **IntPtr** a volné paměti ručně pomocí odpovídající metodu. Podobně se můžete vyhnout automatické paměti uvolňování v situacích, kde by nikdy uvolnit paměť, například jako při použití **GetCommandLine** funkce z Kernel32.dll, který vrací ukazatel na paměti jádra. Podrobnosti o ručně uvolnění paměti najdete v tématu [vyrovnávací paměti ukázka](http://msdn.microsoft.com/library/e30d36e8-d7c4-4936-916a-8fdbe4d9ffd5(v=vs.100)).  
  
## <a name="default-marshaling-for-classes"></a>Výchozí zařazování pro třídy  
 Třídy mohou být zařazena pouze pomocí zprostředkovatele komunikace s objekty COM a jsou vždycky zařazené jako rozhraní. V některých případech rozhraní sloužící k zařazování třídy se nazývá rozhraní třídy. Informace o přepsání třídy rozhraní s rozhraním zvoleného najdete v tématu [představení rozhraní třídy](com-callable-wrapper.md#introducing-the-class-interface).  
  
### <a name="passing-classes-to-com"></a>Předávání tříd do modelu COM  
 Když spravovanou třídou předána do modelu COM, spolupráce vláken automaticky zabalí třídy pomocí modelu COM serveru proxy a předá rozhraní třída vyprodukované proxy server a volání metody COM. Proxy server pak deleguje všechna volání na rozhraní třída zpět do spravovaného objektu. Proxy server taky zpřístupňuje další rozhraní, která nejsou explicitně implementované v třídě. Proxy server, jako automaticky implementuje rozhraní **IUnknown** a **IDispatch** jménem třídy.  
  
### <a name="passing-classes-to-net-code"></a>Předávání tříd pro kód .NET  
 Třídy typu coclass se obvykle nepoužívá jako argumenty metoda v modelu COM. Místo toho výchozí rozhraní se obvykle předává místo coclass.  
  
 Když rozhraní předána do spravovaného kódu, je zodpovědná za zabalení rozhraní s správné obálku a předání obálku spravované metoda spolupráce vláken. Určení, které obálka pro použití může být obtížné. Všechny instance objektu COM má jeden, jedinečné obálku, bez ohledu na to, kolik rozhraní implementuje objekt. Například jeden objekt COM, který implementuje rozhraní pět různých má jenom jeden obálku. Stejné obálku zpřístupní všechny pět rozhraní. Pokud jsou vytvořeny dva instance objektu COM, vytvoří se dvě instance obálku.  
  
 Pro obálku zachování stejného typu v průběhu své životnosti musí spolupráce vláken identifikovat správný obálku prvním rozhraní vystavené objektu je předána vláken. Zařazování identifikuje objekt pohledem na jednu z rozhraní, které implementuje objekt.  
  
 Například zařazování Určuje, že obálku třída by měla slouží k zabalení rozhraní, který byl předán do spravovaného kódu. Když rozhraní nejprve předána zařazování, zařazování zkontroluje, zda rozhraní pochází od známých objektu. Tato kontrola probíhá ve dvou situacích:  
  
-   Rozhraní se implementuje jiný spravovaný objekt, který byl předán COM jinde. Zařazování můžete snadno identifikovat rozhraní vystavené spravované objekty a může tak, aby odpovídaly rozhraní s spravovaný objekt, který poskytuje implementaci. Spravovaného objektu je předána metodě a je zapotřebí žádné obálku.  
  
-   Objekt, který už je zabalená je implementace rozhraní. Pokud chcete zjistit, jestli se jedná o tento případ, dotazuje se vláken objektu pro jeho **IUnknown** rozhraní a porovná rozhraní vrácený rozhraní jiné objekty, které jsou již uzavřen. Pokud rozhraní je stejný jako u jiného obálky, objekty mají stejnou identitu a existující obálky je předaný metodě.  
  
 Pokud není rozhraní z objektu známé, zařazování provede následující akce:  
  
1.  Objekt pro dotazy zařazování vláken **IProvideClassInfo2** rozhraní. Pokud je zadán, zařazování používá CLSID vrácená z **IProvideClassInfo2.GetGUID** k identifikaci třída typu coclass poskytuje rozhraní. S CLSID najdou zařazování obálku z registru, pokud sestavení již byla zaregistrována.  
  
2.  Rozhraní pro dotazy zařazování vláken **IProvideClassInfo** rozhraní. Pokud zadaná, používá zařazování **ITypeInfo** vrácená z **IProvideClassInfo.GetClassinfo** k určení CLSID třídy vystavení rozhraní. Zařazování lze CLSID vyhledat metadata pro obálku.  
  
3.  Pokud stále zařazování nemůže určovat třídu, zabalí rozhraní s obecné obálku třídy s názvem **System.__ComObject**.  
  
## <a name="default-marshaling-for-delegates"></a>Výchozí zařazování pro delegáti  
 Spravované delegáta je zařazené jako rozhraní modelu COM nebo jako ukazatel na funkci založené na mechanismu volání:  
  
-   Pro platformu vyvolání, delegáta je zařazené jako ukazatel Nespravované funkce ve výchozím nastavení.  
  
-   Pro zprostředkovatele komunikace s objekty COM, je delegáta zařazené jako rozhraní modelu COM typu **_Delegate** ve výchozím nastavení. **_Delegate** rozhraní je definována v knihovně typů Mscorlib.tlb a obsahuje <xref:System.Delegate.DynamicInvoke%2A?displayProperty=nameWithType> metodu, která umožňuje volat metodu, která odkazuje na delegát.  
  
 V následující tabulce jsou zařazování možnosti pro datový typ spravovaného delegáta. <xref:System.Runtime.InteropServices.MarshalAsAttribute> Atribut nabízí několik <xref:System.Runtime.InteropServices.UnmanagedType> hodnoty výčtu k zařazení delegáti.  
  
|Typ výčtu|Popis nespravované formátu|  
|----------------------|-------------------------------------|  
|**UnmanagedType.FunctionPtr**|Ukazatel Nespravované funkce.|  
|**UnmanagedType.Interface**|Rozhraní typu **_Delegate**, jak jsou definovány v Mscorlib.tlb.|  
  
 Vezměte v úvahu následující příklad kódu, ve kterém metody `DelegateTestInterface` jsou vyexportovány do knihovny typů COM. Všimněte si, že pouze deleguje označené jako **ref** (nebo **ByRef**) – klíčové slovo jsou předávány jako vstupně -výstupní parametry.  
  
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
  
### <a name="type-library-representation"></a>Typ knihovny reprezentace  
  
```  
importlib("mscorlib.tlb");  
interface DelegateTest : IDispatch {  
[id(…)] HRESULT m1([in] _Delegate* d);  
[id(…)] HRESULT m2([in] _Delegate* d);  
[id(…)] HRESULT m3([in, out] _Delegate** d);  
[id()] HRESULT m4([in] int d);  
[id()] HRESULT m5([in, out] int *d);  
   };  
```  
  
 Ukazatel na funkci můžete přímo odkázat, stejně jako všechny ostatní nespravované – ukazatel na funkci můžete zrušením odkazu.  

V tomto příkladu, pokud dva delegáty jsou zařazené jako <xref:System.Runtime.InteropServices.UnmanagedType.FunctionPtr?displayProperty=nameWithType>, výsledkem je `int` a ukazatel na `int`. Protože typů delegátů přeuspořádány, `int` zde představuje ukazatel void (`void*`), který je adresa delegáta v paměti. Jinými slovy, je tento výsledek specifické pro systémy Windows 32-bit, protože `int` zde představuje velikost ukazatel na funkci.

> [!NOTE]
>  Odkaz na ukazatel funkce na spravované delegáta držené nespravovaného kódu nezabrání modul common language runtime v provádění uvolňování paměti na spravovaného objektu.  
  
 Například následující kód je nesprávný protože odkaz na `cb` předaný objekt `SetChangeHandler` metody nezachovat `cb` zachování připojení mimo dobu životnosti `Test` metoda. Jednou `cb` objekt uvolnění z paměti, ukazatel na funkci předaný `SetChangeHandler` již není platný.  
  
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
  
 Pro kompenzaci neočekávané uvolňování paměti, volající musíte zajistit, aby `cb` objektu je udržováno aktivní, dokud ukazatel Nespravované funkce je používán. Volitelně může mít nespravovaného kódu upozornit spravovaného kódu, pokud ukazatel na funkci již nepotřebujete, jak ukazuje následující příklad.  
  
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
 Většina typy hodnot, jako je například celá čísla a čísla s plovoucí desetinnou čárkou, jsou [přenositelné](blittable-and-non-blittable-types.md) a nevyžadují zařazování. Další [nepřenositelné](blittable-and-non-blittable-types.md) typy mají odlišné reprezentace v paměti spravovanými a nespravovanými a vyžadují kódování. Jiné typy stále vyžadují explicitní formátování mezi součinnosti hranic.  
  
 Toto téma obsahuje informace postupujte podle kroků pro typy formátovanou hodnotu:  
  
-   [Typy hodnot, které jsou používány platformy vyvolání](#cpcondefaultmarshalingforvaluetypesanchor2)  
  
-   [Typy hodnot, které jsou používány zprostředkovatel komunikace s objekty COM](#cpcondefaultmarshalingforvaluetypesanchor3)  
  
 Kromě popisující formátovaný typy, toto téma popisuje [typy hodnot systému](#cpcondefaultmarshalingforvaluetypesanchor1) které mají neobvyklé chování zařazování.  
  
 Formátovaný typ je komplexní typ, který obsahuje informace, které explicitně určuje rozložení její členy v paměti. Informace o rozvržení člen je prováděno pomocí <xref:System.Runtime.InteropServices.StructLayoutAttribute> atribut. Rozložení může být jedna z následujících <xref:System.Runtime.InteropServices.LayoutKind> hodnot výčtu:  
  
-   **LayoutKind.Automatic**  
  
     Označuje, že je modul common language runtime volné chcete změnit pořadí členů typ efektivitu. Pokud však typ hodnoty je předán nespravovaného kódu, rozložení členy nebude předvídatelný. Pokus o zařazování tato struktura automaticky dojde k výjimce.  
  
-   **LayoutKind.Sequential**  
  
     Označuje, že členy typu jsou k nastíněny v nespravované paměti ve stejném pořadí, ve kterém se zobrazí v definici spravovaného typu.  
  
-   **LayoutKind.Explicit**  
  
     Označuje, že členové jsou nastíněny podle <xref:System.Runtime.InteropServices.FieldOffsetAttribute> součástí každého pole.  
  
<a name="cpcondefaultmarshalingforvaluetypesanchor2"></a>   
### <a name="value-types-used-in-platform-invoke"></a>Typy hodnot, které jsou používány platformy vyvolání  
 V následujícím příkladu `Point` a `Rect` typy poskytovat člen informace o rozložení pomocí **StructLayoutAttribute**.  
  
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
  
 Při zařazen do nespravovaného kódu, tyto formátovaný typy jsou zařazené jako struktury stylu jazyka C. To poskytuje snadný způsob volání nespravovaného rozhraní API, která má struktura argumenty. Například `POINT` a `RECT` struktury se dá předat do rozhraní API Win32 Microsoft **PtInRect** funkce následujícím způsobem:  
  
```  
BOOL PtInRect(const RECT *lprc, POINT pt);  
```  
  
 Abyste mohli předávat struktury používá následující platforma vyvolání definice:  
  
```vb  
Class Win32API      
   Declare Auto Function PtInRect Lib "User32.dll" _  
    (ByRef r As Rect, p As Point) As Boolean  
End Class  
```  
  
```csharp  
class Win32API {  
   [DllImport("User32.dll")]  
   public static extern Bool PtInRect(ref Rect r, Point p);  
}  
```  
  
 `Rect` Typ hodnoty musí být předán odkazem, protože očekává ukazatel na nespravovaného rozhraní API `RECT` mají být předány funkce. `Point` Typ hodnoty je předaná hodnota protože očekává nespravovaného rozhraní API `POINT` mají být předány v zásobníku. Tento jemně rozdíl je velmi důležité. Odkazy jsou předány na nespravovaný kód jako ukazatele. Hodnoty jsou předávány nespravovaného kódu v zásobníku.  
  
> [!NOTE]
>  Když formátovaný typ se zařadit jako strukturu, jsou přístupné pouze pole v rámci typu. Pokud má typ metody, vlastnosti nebo události, jsou nedostupná z nespravovaného kódu.  
  
 Třídy můžete také zařazeno na nespravovaný kód jako stylu jazyka C struktury zadaný opravení člen rozložení. Informace o třídě rozložení člen je také součástí <xref:System.Runtime.InteropServices.StructLayoutAttribute> atribut. Hlavní rozdíl mezi typy hodnot s pevné rozložení a tříd pomocí pevné rozložení je způsob, ve kterém jsou zařazené na nespravovaný kód. Typy hodnot se předávají hodnotou (v zásobníku) a v důsledku toho nejsou vidět všechny změny provedené u členů typu volaného volající. Odkazové typy jsou předaná odkaz (odkaz na typ je předán v zásobníku); v důsledku toho jsou všechny změny provedené volaného na členy typu blittable typu pohledu volající.  
  
> [!NOTE]
>  Pokud odkazového typu členy nepřenositelné typy, převod je požadovaná dvakrát: poprvé, když je argument předaný nespravované straně a druhý čas na vrátit z volání. Z důvodu to přidat režie vstup/výstup parametry musí explicitně u argument v případě volající chce vidět změny provedené volaného.  
  
 V následujícím příkladu `SystemTime` třída má sekvenční člen rozložení a se dá předat do rozhraní API Win32 **GetSystemTime** funkce.  
  
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
  
 **GetSystemTime** funkce je definován následujícím způsobem:  
  
```  
void GetSystemTime(SYSTEMTIME* SystemTime);  
```  
  
 Definice pro vyvolání ekvivalentní platformy **GetSystemTime** vypadá takto:  
  
```vb  
Public Class Win32  
   Declare Auto Sub GetSystemTime Lib "Kernel32.dll" (ByVal sysTime _  
   As SystemTime)  
End Class  
```  
  
```csharp  
class Win32API {  
   [DllImport("Kernel32.dll", CharSet=CharSet.Auto)]  
   public static extern void GetSystemTime(SystemTime st);  
}  
```  
  
 Všimněte si, že `SystemTime` argument není zadán jako argument typu odkaz, protože `SystemTime` je třída, není typ hodnoty. Na rozdíl od typy hodnot jsou vždy třídy předán odkazem.  
  
 Následující příklad kódu ukazuje jiné `Point` třídu, která má metodu s názvem `SetXY`. Protože má tento typ sekvenční rozložení, můžete předaný nespravovaného kódu a zařazené jako strukturu. Ale `SetXY` člen není možné volat z nespravovaného kódu, i když je objekt předaný odkazem.  
  
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
  
<a name="cpcondefaultmarshalingforvaluetypesanchor3"></a>   
### <a name="value-types-used-in-com-interop"></a>Typy hodnot, které jsou používány zprostředkovatel komunikace s objekty COM  
 Formátovaný typy lze předat také volání metody zprostředkovatele komunikace s objekty COM. Ve skutečnosti při exportu do knihovny typů, typů hodnot se automaticky převedou na struktury. Jak ukazuje následující příklad, `Point` typ hodnoty se změní na definici typu (typedef) s názvem `Point`. Všechny odkazy na `Point` typ hodnoty jinde v knihovně typů jsou nahrazeny `Point` typedef.  
  
 **Typ knihovny reprezentace**  
  
```  
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
  
 Stejná pravidla použitý k zařazování hodnoty a odkazy na platformě vyvolat volání se používají při zařazování prostřednictvím rozhraní modelu COM. Například když instanci `Point` typ hodnoty je předán z rozhraní .NET Framework do modelu COM, `Point` je předaná hodnota. Pokud `Point` typ hodnoty je předán odkazem ukazatel na `Point` je předán v zásobníku. Spolupráce vláken nepodporuje vyšší úrovně dereference (**bodu** \* \*) v obou směrech.  
  
> [!NOTE]
>  Struktury, že <xref:System.Runtime.InteropServices.LayoutKind> nastavena na hodnotu výčtu **explicitní** nelze použít v zprostředkovatel komunikace s objekty COM, protože knihovny exportovaný typů nelze express explicitní rozložení.  
  
<a name="cpcondefaultmarshalingforvaluetypesanchor1"></a>   
### <a name="system-value-types"></a>Typy hodnot systému  
 <xref:System> Oboru názvů má několik typů hodnoty, které představují zabalené formu runtime primitivní typy. Například hodnota typu <xref:System.Int32?displayProperty=nameWithType> struktura představuje zabalené formu **ELEMENT_TYPE_I4**. Místo zařazování tyto typy jako struktury, jako jsou i další typy formátovaný, můžete zařazování je stejným způsobem jako primitivní typy, které budou pole. **System.Int32** je proto zařazené jako **ELEMENT_TYPE_I4** místo jako strukturu obsahující jednoho člena typu **dlouho**. Následující tabulka obsahuje seznam typů hodnot v **systému** obor názvů, které jsou pevně určené reprezentace primitivní typy.  
  
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
  
 Jinou hodnotu typy, které do **systému** obor názvů jsou zpracovány jinak. Protože nespravovaného kódu už má zavedené formátů pro tyto typy, zařazování má zvláštní pravidla pro zařazování je. Následující tabulka uvádí typy speciální hodnot v **systému** obor názvů, a také nespravovaný typ jsou zařazené do.  
  
|Typ hodnoty systému|Typ IDL|  
|-----------------------|--------------|  
|<xref:System.DateTime?displayProperty=nameWithType>|**DATUM**|  
|<xref:System.Decimal?displayProperty=nameWithType>|**DECIMAL**|  
|<xref:System.Guid?displayProperty=nameWithType>|**GUID**|  
|<xref:System.Drawing.Color?displayProperty=nameWithType>|**OLE_COLOR**|  
  
 Následující kód ukazuje definici nespravované typy **datum**, **GUID**, **DECIMAL**, a **OLE_COLOR** v Stdole2 typu Knihovna.  
  
#### <a name="type-library-representation"></a>Typ knihovny reprezentace  
  
```  
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
  
 Následující kód ukazuje odpovídající definice v spravovaný `IValueTypes` rozhraní.  
  
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
  
#### <a name="type-library-representation"></a>Typ knihovny reprezentace  
  
```  
[…]  
interface IValueTypes : IDispatch {  
   HRESULT M1([in] DATE d);  
   HRESULT M2([in] GUID d);  
   HRESULT M3([in] DECIMAL d);  
   HRESULT M4([in] OLE_COLOR d);  
};  
```  
  
## <a name="see-also"></a>Viz také  
 [Přenositelné a nepřenositelné typy](blittable-and-non-blittable-types.md)  
 [Kopírování a přichycování](copying-and-pinning.md)  
 [Výchozí zařazování pro pole](default-marshaling-for-arrays.md)  
 [Výchozí zařazování pro objekty](default-marshaling-for-objects.md)  
 [Výchozí zařazování pro řetězce](default-marshaling-for-strings.md)
