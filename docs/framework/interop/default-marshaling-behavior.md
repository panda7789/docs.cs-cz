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
ms.openlocfilehash: c6de6091b8970fde4a958148acf32dcefe1a6726
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69946561"
---
# <a name="default-marshaling-behavior"></a>Výchozí chování zařazování
Zařazování Interop funguje s pravidly, která určují, jak se data přidružená k parametrům metody chovají při průchodu mezi spravovanou a nespravovanou pamětí. Tato Vestavěná pravidla řídí tyto aktivity zařazování jako transformace datových typů, ať už volaný může změnit předaných dat a vracet tyto změny volajícímu a za kterých okolnosti zařazování poskytuje optimalizace výkonu.  
  
 Tato část identifikuje výchozí charakteristiky chování služby interop marshaling. Zobrazuje podrobné informace o zařazovacích polích, logických typech, typech znaků, delegátů, třídách, objektech, řetězcích a strukturách.  
  
> [!NOTE]
> Zařazování obecných typů se nepodporuje. Další informace najdete v tématu [spolupráce pomocí obecných typů](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229590(v=vs.100)).  
  
## <a name="memory-management-with-the-interop-marshaler"></a>Správa paměti pomocí zařazovacího modulu spolupráce  
 Zařazování Interop se vždy pokouší uvolnit paměť přidělenou nespravovaným kódem. Toto chování je v souladu s pravidly správy paměti modelu COM, ale liší se od pravidel, C++která se řídí nativním.  
  
 K záměně může dojít, pokud při C++ použití vyvolání platformy očekáváte nativní chování (bez uvolnění paměti), které automaticky uvolňuje paměť pro ukazatele. Například volání následující nespravované metody z C++ knihovny DLL automaticky neuvolní žádnou paměť.  
  
### <a name="unmanaged-signature"></a>Nespravovaný podpis  
  
```cpp  
BSTR MethodOne (BSTR b) {  
     return b;  
}  
```  
  
 Pokud však definujete metodu jako prototyp vyvolání platformy, nahraďte každý typ <xref:System.String> **BSTR** typem a voláním `MethodOne`, modul CLR (Common Language Runtime) se pokusí uvolnit `b` dvakrát. Chování zařazování lze změnit pomocí <xref:System.IntPtr> typů namísto **řetězcových** typů.  
  
 Modul runtime vždy používá metodu **CoTaskMemFree** k uvolnění paměti. Pokud paměť, se kterou pracujete, nebyla přidělena pomocí metody **CoTaskMemAlloc** , musíte použít **IntPtr** a uvolnit paměť ručně pomocí vhodné metody. Podobně se můžete vyhnout automatickému uvolňování paměti v situacích, kdy by paměť neměla být nikdy uvolněna, například při použití funkce GetCommandLine z Kernel32. dll, která vrací ukazatel na paměť jádra. Podrobnosti o ručním uvolnění paměti najdete v [ukázce vyrovnávací paměti](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/x3txb6xc(v=vs.100)).  
  
## <a name="default-marshaling-for-classes"></a>Výchozí zařazování pro třídy  
 Třídy lze zařadit pouze pomocí zprostředkovatele komunikace s objekty COM a jsou vždy zařazeny jako rozhraní. V některých případech je rozhraní použité k zařazení třídy známé jako rozhraní třídy. Informace o přepsání rozhraní třídy s rozhraním dle vašeho výběru naleznete v tématu [Představujeme rozhraní třídy](../../standard/native-interop/com-callable-wrapper.md#introducing-the-class-interface).  
  
### <a name="passing-classes-to-com"></a>Předávání tříd do modelu COM  
 Když je do modelu COM předána spravovaná třída, zařazovací služba interoperability automaticky zabalí třídu s proxy COM a předá rozhraní třídy vytvořené proxy serverem volání metody COM. Proxy potom deleguje všechna volání rozhraní třídy zpátky do spravovaného objektu. Proxy také zveřejňuje jiná rozhraní, která nejsou explicitně implementována třídou. Proxy automaticky implementuje rozhraní, jako je **IUnknown** a **IDispatch** jménem třídy.  
  
### <a name="passing-classes-to-net-code"></a>Předávání tříd do kódu .NET  
 Třídy coclass nejsou obvykle používány jako argumenty metody v modelu COM. Místo toho je obvykle předán výchozí rozhraní místo třídy typu coclass.  
  
 Když je rozhraní předáno do spravovaného kódu, zařazovací modul Interop zodpovídá za balení rozhraní se správnou obálkou a předání obálky spravované metodě. Určení, která obálka se má použít, může být obtížné. Každá instance objektu COM má jedinou jedinečnou obálku bez ohledu na to, kolik rozhraní objekt implementuje. Například jeden objekt COM, který implementuje pět různých rozhraní, má pouze jednu obálku. Stejná obálka zpřístupňuje všechna pět rozhraní. Pokud se vytvoří dvě instance objektu COM, vytvoří se dvě instance obálky.  
  
 Aby obálka zachovala stejný typ během své životnosti, musí zařazovací modul Interop identifikovat správnou obálku, když je rozhraní vystavené objektem předáno prostřednictvím zařazovacího modulu. Zařazovací modul identifikuje objekt tím, že prohlíží jedno z rozhraní, které objekt implementuje.  
  
 Například zařazovací modul určí, že obálka třídy by měla být použita k zabalení rozhraní, které bylo předáno do spravovaného kódu. Když je rozhraní nejprve předáno prostřednictvím zařazovacího modulu, zařazovací modul zkontroluje, zda rozhraní přichází ze známého objektu. Tato kontrolu probíhá ve dvou situacích:  
  
- Rozhraní je implementováno jiným spravovaným objektem, který byl předán do modelu COM jinde. Zařazovací modul může snadno identifikovat rozhraní vystavená spravovanými objekty a může odpovídat rozhraní se spravovaným objektem, který poskytuje implementaci. Spravovaný objekt je pak předán metodě a není nutná žádná obálka.  
  
- Objekt, který již byl zabalen, implementuje rozhraní. Chcete-li zjistit, zda se jedná o tento případ, zařazovací modul dotazuje objekt pro jeho rozhraní **IUnknown** a porovná vrácené rozhraní s rozhraními jiných objektů, které jsou již zabaleny. Pokud je rozhraní stejné jako jiné obálky, objekty mají stejnou identitu a stávající obálka je předána metodě.  
  
 Pokud rozhraní nepochází ze známého objektu, zařazovací modul provede následující:  
  
1. Zařazovací modul se dotazuje objektu pro rozhraní **IProvideClassInfo2** . Pokud je k dispozici, zařazovací modul používá identifikátor CLSID vrácený z **IProvideClassInfo2. GetGUID** k identifikaci třídy coclass poskytující rozhraní. S identifikátorem CLSID může zařazovací modul najít obálku z registru, pokud bylo sestavení dříve registrováno.  
  
2. Zařazovací modul vyžádá rozhraní pro rozhraní **IProvideClassInfo** . Pokud je k dispozici, zařazovací modul používá **volání ITypeInfo** vrácenou z **IProvideClassInfo. GetClassInfo** k určení identifikátoru CLSID třídy, která toto rozhraní zveřejňuje. Zařazovací modul může pomocí identifikátoru CLSID najít metadata pro obálku.  
  
3. Pokud zařazovací modul stále nemůže identifikovat třídu, zabalí rozhraní s obecnou obálkovou třídou s názvem **System. __ComObject**.  
  
## <a name="default-marshaling-for-delegates"></a>Výchozí zařazování pro delegáty  
 Spravovaný delegát je zařazen jako rozhraní modelu COM nebo jako ukazatel na funkci na základě volajícího mechanismu:  
  
- V případě vyvolání platformy je delegát ve výchozím nastavení zařazen jako nespravovaný ukazatel na funkci.  
  
- Pro zprostředkovatele komunikace s objekty COM je delegát ve výchozím nastavení zařazen jako rozhraní COM typu **_Delegate** . Rozhraní **_Delegate** je definováno v knihovně typů mscorlib. tlb a obsahuje <xref:System.Delegate.DynamicInvoke%2A?displayProperty=nameWithType> metodu, která umožňuje zavolat metodu, na kterou odkazuje delegát.  
  
 V následující tabulce jsou uvedeny možnosti zařazování pro datový typ spravovaného delegáta. Atribut poskytuje několik <xref:System.Runtime.InteropServices.UnmanagedType> hodnot výčtu pro zařazení delegátů. <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
  
|Typ výčtu|Popis nespravovaného formátu|  
|----------------------|-------------------------------------|  
|**UnmanagedType.FunctionPtr**|Nespravovaný ukazatel na funkci.|  
|**UnmanagedType.Interface**|Rozhraní typu **_Delegate**, jak je definováno v mscorlib. tlb.|  
  
 Vezměte v úvahu následující vzorový kód, ve kterém metody `DelegateTestInterface` jsou exportovány do knihovny typů modelu COM. Všimněte si, že jako vstupně-výstupní parametry jsou předány pouze Delegáti označeni klíčovým slovem **ref** (nebo **ByRef**).  
  
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
  
 Na ukazatel na funkci lze odkázat stejným způsobem, jako jakýkoli jiný nespravovaný ukazatel na funkci lze odkázat.  

V tomto příkladu, když jsou dva Delegáti zařazeni jako <xref:System.Runtime.InteropServices.UnmanagedType.FunctionPtr?displayProperty=nameWithType>, výsledek `int` je `int`a ukazatel na. Vzhledem k tomu, že typy delegátů `int` jsou zařazeny, zde představuje ukazatel na`void*`typ void (), což je adresa delegáta v paměti. Jinými slovy, tento výsledek je specifický pro 32 systémy Windows, protože `int` tady představuje velikost ukazatele na funkci.

> [!NOTE]
> Odkaz na ukazatel funkce na spravovaný delegát, který uchovává nespravovaný kód, nebrání modulu Common Language Runtime v provádění uvolňování paměti ve spravovaném objektu.  
  
 Například následující kód je nesprávný, `cb` protože odkaz na objekt, který je předán `SetChangeHandler` metodě, nezůstane `cb` po dobu životnosti `Test` metody aktivní. Jakmile je `SetChangeHandler` objekt uvolněn z paměti, ukazatel funkce předaný do již není platný. `cb`  
  
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
  
 Aby bylo možné kompenzovat neočekávané uvolňování paměti, volající musí zajistit `cb` , že objekt zůstane aktivní, dokud se nepoužívá ukazatel nespravované funkce. V případě potřeby může být nespravovaný kód upozorněn na spravovaný kód, pokud ukazatel na funkci již není potřeba, jak ukazuje následující příklad.  
  
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
 Většina typů hodnot, jako jsou celá čísla a čísla s plovoucí desetinnou čárkou, jsou přenositelná a nevyžadují zařazování. [](blittable-and-non-blittable-types.md) Jiné [](blittable-and-non-blittable-types.md) nepřenositelní typy mají odlišné reprezentace ve spravované a nespravované paměti a vyžadují zařazování. Stále jiné typy vyžadují explicitní formátování napříč hranicí vzájemných operací.  
  
 Tato část poskytuje informace o následujících formátovaných hodnotách:  
  
- [Typy hodnot používané při vyvolání platformy](#value-types-used-in-platform-invoke)  
  
- [Typy hodnot používané při zprostředkovateli komunikace s objekty COM](#value-types-used-in-com-interop)  
  
 Kromě popisných formátovaných typů toto téma identifikuje [typy systémových hodnot](#system-value-types) , které mají neobvyklé chování při zařazování.  
  
 Zformátovaný typ je komplexní typ, který obsahuje informace, které explicitně řídí rozložení jeho členů v paměti. Informace o rozložení členů jsou k dispozici <xref:System.Runtime.InteropServices.StructLayoutAttribute> pomocí atributu. Rozložení může být jedna z následujících <xref:System.Runtime.InteropServices.LayoutKind> hodnot výčtu:  
  
- **LayoutKind. Automatic**  
  
     Označuje, že modul CLR (Common Language Runtime) je bezplatný pro změnu pořadí členů typu pro zajištění efektivity. Pokud je však typ hodnoty předán nespravovanému kódu, je rozložení členů předvídatelné. Pokus o zařazení takové struktury automaticky způsobí výjimku.  
  
- **LayoutKind.Sequential**  
  
     Označuje, že členové typu mají být rozloženi v nespravované paměti ve stejném pořadí, v jakém jsou uvedeny v definici spravovaného typu.  
  
- **LayoutKind. Explicit**  
  
     Označuje, že jsou členové rozloženi podle <xref:System.Runtime.InteropServices.FieldOffsetAttribute> zadaného pole.  
  
### <a name="value-types-used-in-platform-invoke"></a>Typy hodnot používané při vyvolání platformy  
 V následujícím příkladu `Point` typy a `Rect` poskytují informace o rozložení členů pomocí **StructLayoutAttribute**.  
  
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
  
 Při zařazení do nespravovaného kódu jsou tyto formátované typy zařazeny jako struktury ve stylu jazyka C. To poskytuje snadný způsob volání nespravovaného rozhraní API, které má argumenty struktury. Například `POINT` struktury a `RECT` lze předat funkci **PtInRect** rozhraní API systému Microsoft Windows následujícím způsobem:  
  
```cpp  
BOOL PtInRect(const RECT *lprc, POINT pt);  
```  
  
 Struktury můžete předat pomocí následující definice vyvolání platformy:  
  
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
  
 Typ hodnoty musí být předán odkazem, protože nespravované rozhraní API očekává ukazatel na objekt `RECT` , který má být předán funkci. `Rect` Typ hodnoty je předán podle hodnoty, protože nespravované rozhraní API očekává `POINT` , že má být předán do zásobníku. `Point` Tento drobný rozdíl je velmi důležitý. Odkazy jsou předány nespravovanému kódu jako ukazatelé. Hodnoty jsou předány nespravovanému kódu v zásobníku.  
  
> [!NOTE]
> Při zařazování formátovaného typu jako struktury jsou k dispozici pouze pole v rámci tohoto typu. Pokud typ obsahuje metody, vlastnosti nebo události, jsou nepřístupné z nespravovaného kódu.  
  
 Třídy lze také zařadit do nespravovaného kódu jako struktury ve stylu jazyka C za předpokladu, že mají pevně dané rozložení členů. Informace o rozložení členů pro třídu jsou také k dispozici s <xref:System.Runtime.InteropServices.StructLayoutAttribute> atributem. Hlavní rozdíl mezi typy hodnot s pevným rozložením a třídami s pevným rozložením je způsob, jakým jsou zařazeny do nespravovaného kódu. Typy hodnot jsou předávány hodnotou (v zásobníku) a v důsledku toho se žádné změny provedené u členů typu volaného nevidí volajícím. Odkazové typy jsou předávány odkazem (odkaz na typ je předán do zásobníku); v důsledku toho volající vytvoří všechny změny provedené u členů typu přenositelné jako typ volaný.  
  
> [!NOTE]
> Pokud typ odkazu obsahuje členy nepřenositelného typu, je převod požadován dvakrát: při prvním předání argumentu na nespravovanou stranu a při návratu z volání. Z důvodu těchto přidaných režijních nákladů musí být parametry nebo výstupy explicitně aplikovány na argument, pokud volající chce zobrazit změny provedené volaným.  
  
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
  
 Všimněte si, `SystemTime` že argument není zadán jako argument odkazu, protože `SystemTime` je třída, nikoli typ hodnoty. Na rozdíl od hodnotových typů jsou třídy vždy předány odkazem.  
  
 Následující příklad kódu ukazuje jinou `Point` třídu, která má metodu s názvem. `SetXY` Vzhledem k tomu, že typ má sekvenční rozložení, lze jej předat nespravovanému kódu a zařadit jako strukturu. `SetXY` Člen však nelze volat z nespravovaného kódu, i když je objekt předán odkazem.  
  
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
  
### <a name="value-types-used-in-com-interop"></a>Typy hodnot používané při zprostředkovateli komunikace s objekty COM  
 Naformátované typy lze také předat voláním metody spolupráce modelu COM. Ve skutečnosti platí, že při exportu do knihovny typů jsou typy hodnot automaticky převedeny na struktury. Jak ukazuje následující příklad, `Point` typ hodnoty se stal definicí typu (typedef) s názvem. `Point` Všechny odkazy na `Point` typ hodnoty jinde v knihovně typů jsou nahrazeny `Point` definicí typedef.  
  
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
  
 Stejná pravidla, která se používají k zařazování hodnot a odkazů na volání vyvolání platformy, se používají při zařazování přes rozhraní COM. Například když je instance `Point` typu hodnoty předána z .NET Framework do modelu COM `Point` , je předána hodnotou. Pokud je typ `Point` hodnotypředánpomocíodkazu,ukazatelnaobjektje`Point` předán do zásobníku. Zařazovací modul Interop nepodporuje v obou směrech vyšší úroveň dereference (**Point** \* \*).  
  
> [!NOTE]
> Struktury s <xref:System.Runtime.InteropServices.LayoutKind> hodnotou výčtu nastavenou na hodnotu **Explicit** nelze použít v zprostředkovatele komunikace s objekty COM, protože exportovaná knihovna typů nemůže vyjádřit explicitní rozložení.  
  
### <a name="system-value-types"></a>Typy systémových hodnot  
 <xref:System> Obor názvů má několik typů hodnot, které reprezentují zabalený formát primitivních typů modulu runtime. Například struktura typu <xref:System.Int32?displayProperty=nameWithType> hodnoty představuje pevně podobu **ELEMENT_TYPE_I4**. Namísto zařazování těchto typů jako struktur, jako jiné formátované typy, jste je zařadíi stejným způsobem jako primitivní typy, které jsou v poli. Hodnota **System. Int32** je proto zařazena jako **ELEMENT_TYPE_I4** namísto struktury obsahující jednoho člena typu **Long**. Následující tabulka obsahuje seznam typů hodnot v oboru názvů **System** , které jsou zabaleny do reprezentace primitivních typů.  
  
|Typ systémové hodnoty|Typ elementu|  
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
  
 Některé jiné typy hodnot v oboru názvů **System** jsou zpracovávány jinak. Vzhledem k tomu, že nespravovaný kód již obsahuje dobře zavedený formát pro tyto typy, má zařazovací modul zvláštní pravidla pro jejich zařazování. V následující tabulce jsou uvedeny typy zvláštních hodnot v oboru názvů **System** a také nespravovaný typ, na který jsou zařazeny.  
  
|Typ systémové hodnoty|Typ IDL|  
|-----------------------|--------------|  
|<xref:System.DateTime?displayProperty=nameWithType>|**DATUM**|  
|<xref:System.Decimal?displayProperty=nameWithType>|**NOTACI**|  
|<xref:System.Guid?displayProperty=nameWithType>|**GUID**|  
|<xref:System.Drawing.Color?displayProperty=nameWithType>|**OLE_COLOR**|  
  
 Následující kód ukazuje definici nespravovaných typů **Date**, **GUID**, **Decimal**a **OLE_COLOR** v knihovně typů Stdole2.  
  
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
  
 Následující kód ukazuje odpovídající definice ve spravovaném `IValueTypes` rozhraní.  
  
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
  
## <a name="see-also"></a>Viz také:

- [Přenositelné a nepřenositelné typy](blittable-and-non-blittable-types.md)
- [Kopírování a přichycování](copying-and-pinning.md)
- [Výchozí zařazování pro pole](default-marshaling-for-arrays.md)
- [Výchozí zařazování pro objekty](default-marshaling-for-objects.md)
- [Výchozí zařazování pro řetězce](default-marshaling-for-strings.md)
