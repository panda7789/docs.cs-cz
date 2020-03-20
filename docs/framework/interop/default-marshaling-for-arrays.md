---
title: Výchozí zařazování pro pole
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- interop marshaling, arrays
- arrays, interop marshaling
ms.assetid: 8a3cca8b-dd94-4e3d-ad9a-9ee7590654bc
ms.openlocfilehash: f0094ac572834b2cf0d74fb53c94877da55669e2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181447"
---
# <a name="default-marshaling-for-arrays"></a>Výchozí zařazování pro pole
V aplikaci, která se skládá výhradně ze spravovaného kódu, předává soubor typu common jazyka typem pole jako parametry In/Out. Naproti tomu interop zařazovací zařízení ve výchozím nastavení předá pole jako parametry In.  
  
 S [připnutí optimalizace](copying-and-pinning.md), přenositelné pole se může jevit jako in/out parametr při interakci s objekty ve stejném apartment. Pokud však později exportujete kód do knihovny typů, která slouží ke generování proxy serveru mezi počítači, a tato knihovna se používá k zařazování volání mezi byty, volání se mohou vrátit k chování parametrů true In.  
  
 Pole jsou komplexní povahy a rozdíly mezi spravovanými a nespravovanými poli vyžadují více informací než jiné typy, které nejsou přenositelné.  
  
## <a name="managed-arrays"></a>Spravovaná pole  
 Typy spravovaných polí se mohou lišit. <xref:System.Array?displayProperty=nameWithType> třída je však základní třídou všech typů polí. Třída **System.Array** má vlastnosti pro určení pořadí, délky a dolnía horní hranice pole, stejně jako metody pro přístup, řazení, vyhledávání, kopírování a vytváření polí.  
  
 Tyto typy polí jsou dynamické a nemají odpovídající statický typ definovaný v knihovně základní třídy. Je vhodné si myslet, že každá kombinace typu prvku a pořadí jako odlišný typ pole. Proto jednorozměrné pole celá čísla je jiného typu než jednorozměrné pole dvojité typy. Podobně dvojrozměrné pole celá čísla se liší od jednorozměrné pole celá čísla. Hranice pole nejsou považovány za při porovnávání typů.  
  
 Jak ukazuje následující tabulka, každá instance spravovaného pole musí mít určitý typ prvku, pořadí a dolní mez.  
  
|Typ spravovaného pole|Typ prvku|Rank|Dolní mez|Zápis podpisu|  
|------------------------|------------------|----------|-----------------|------------------------|  
|**ELEMENT_TYPE_ARRAY**|Zadaný podle typu.|Určeno pořadím.|Volitelně zadaná hranicemi.|*typ* **[** *n*,*m* **]**|  
|**ELEMENT_TYPE_CLASS**|Není známo|Není známo|Není známo|**System.array**|  
|**ELEMENT_TYPE_SZARRAY**|Zadaný podle typu.|1|0|*typ* **[** *n* **]**|  
  
## <a name="unmanaged-arrays"></a>Nespravovaná pole  
 Nespravovaná pole jsou buď bezpečná pole ve stylu COM, nebo pole ve stylu C s pevnou nebo proměnnou délkou. Bezpečná pole jsou pole popisující sám sebe, která nesou typ, pořadí a hranice přidružených dat pole. Pole ve stylu C jsou jednorozměrná pole s pevnou dolní mezí 0. Zařazovací služba má omezenou podporu pro oba typy polí.  
  
## <a name="passing-array-parameters-to-net-code"></a>Předání parametrů pole kódu .NET  
 Pole ve stylu C i bezpečná pole mohou být předána kódu .NET z nespravovaného kódu jako bezpečné pole nebo pole ve stylu C. V následující tabulce je uvedena hodnota nespravovaného typu a importovaný typ.  
  
|Nespravovaný typ|Importovaný typ|  
|--------------------|-------------------|  
|**SafeArray(** *Typ* **)**|**ELEMENT_TYPE_SZARRAY** **\<** *převedený typ***>**<br /><br /> Pořadí = 1, dolní mez = 0. Velikost je známa pouze v případě, že je k dispozici ve spravovaném podpisu. Bezpečná pole, která nejsou kategorie = 1 nebo dolní mez = 0 nelze zařadit jako **SZARRAY**.|  
|*Typ*  **[]**|**ELEMENT_TYPE_SZARRAY** **\<** *převedený typ***>**<br /><br /> Pořadí = 1, dolní mez = 0. Velikost je známa pouze v případě, že je k dispozici ve spravovaném podpisu.|  
  
### <a name="safe-arrays"></a>Bezpečná pole  
 Při importu bezpečného pole z knihovny typů do sestavení .NET je pole převedeno na jednorozměrné pole známého typu (například **int).** Stejná pravidla převodu typu, která platí pro parametry, platí také pro prvky pole. Například bezpečné pole **bstr** typů se stane spravované pole řetězců a bezpečné pole variant se stane spravované pole objektů. Typ prvku **SAFEARRAY** je zachycen z knihovny typů a uložen <xref:System.Runtime.InteropServices.UnmanagedType> v hodnotě **SAFEARRAY** výčtu.  
  
 Vzhledem k tomu, že pořadí a hranice bezpečného pole nelze určit z knihovny typů, předpokládá se, že pořadí se rovná 1 a dolní mez se rovná 0. Pořadí a hranice musí být definovány ve spravovaném podpisu vytvořeném [typem knihovny Dovozce (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md). Pokud pořadí předán metodě v době běhu <xref:System.Runtime.InteropServices.SafeArrayRankMismatchException> se liší, je vyvolána. Pokud se typ pole předaný za <xref:System.Runtime.InteropServices.SafeArrayTypeMismatchException> běhu liší, je vyvolána. Následující příklad ukazuje bezpečná pole ve spravovaném a nespravovaném kódu.  
  
 **Nespravovaný podpis**  
  
```cpp
HRESULT New1([in] SAFEARRAY( int ) ar);  
HRESULT New2([in] SAFEARRAY( DATE ) ar);  
HRESULT New3([in, out] SAFEARRAY( BSTR ) *ar);  
```  
  
 **Spravovaný podpis**  
  
```vb  
Sub New1(<MarshalAs(UnmanagedType.SafeArray, SafeArraySubType:=VT_I4)> _  
   ar() As Integer)  
Sub New2(<MarshalAs(UnmanagedType.SafeArray, SafeArraySubType:=VT_DATE)> _
   ar() As DateTime)  
Sub New3(ByRef <MarshalAs(UnmanagedType.SafeArray, SafeArraySubType:=VT_BSTR)> _
   ar() As String)  
```  
  
```csharp  
void New1([MarshalAs(UnmanagedType.SafeArray, SafeArraySubType=VT_I4)] int[] ar) ;  
void New2([MarshalAs(UnmanagedType.SafeArray, SafeArraySubType=VT_DATE)]
   DateTime[] ar);  
void New3([MarshalAs(UnmanagedType.SafeArray, SafeArraySubType=VT_BSTR)]
   ref String[] ar);  
```  
  
 Multidimenzionální nebo nenulová bezpečná pole mohou být zařazena do spravovaného kódu, pokud je podpis metody vytvořený programem Tlbimp.exe upraven tak, aby označoval typ prvku **ELEMENT_TYPE_ARRAY** namísto **ELEMENT_TYPE_SZARRAY**. Alternativně můžete použít přepínač **/sysarray** s tlbimp.exe k <xref:System.Array?displayProperty=nameWithType> importu všech polí jako objektů. V případech, kdy je předané pole známo, že je vícerozměrné, můžete upravit kód zprostředkující jazyk společnosti Microsoft (MSIL) vytvořený souborem Tlbimp.exe a poté jej znovu zkompilovat. Podrobnosti o úpravě kódu MSIL naleznete [v tématu Přizpůsobení reložiových obkladů volání runtime](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100)).  
  
### <a name="c-style-arrays"></a>Pole ve stylu C  
 Při importu pole ve stylu C z knihovny typů do sestavení .NET je pole převedeno na **ELEMENT_TYPE_SZARRAY**.  
  
 Typ prvku pole je určen z knihovny typů a během importu se zachová. Stejná pravidla převodu, která platí pro parametry, platí také pro prvky pole. Například pole **LPStr** typy se stane pole **String** typy. Tlbimp.exe zachycuje typ prvku pole a <xref:System.Runtime.InteropServices.MarshalAsAttribute> aplikuje atribut na parametr.  
  
 Pořadí pole se předpokládá, že se rovná 1. Pokud je pořadí větší než 1, pole je zařazeno jako jednorozměrné pole v pořadí sloupce hlavní. Dolní mez se vždy rovná 0.  
  
 Knihovny typů mohou obsahovat pole s pevnou nebo proměnnou délkou. Tlbimp.exe lze importovat pouze pole s pevnou délkou z knihoven typů, protože knihovny typů postrádají informace potřebné k zařazování polí s proměnnou délkou. U polí s pevnou délkou je velikost importována z knihovny typů a zachycena v **atributu MarshalAsAttribute,** který je použit pro parametr.  
  
 Je nutné ručně definovat knihovny typů obsahující pole proměnné délky, jak je znázorněno v následujícím příkladu.  
  
 **Nespravovaný podpis**  
  
```cpp
HRESULT New1(int ar[10]);  
HRESULT New2(double ar[10][20]);  
HRESULT New3(LPWStr ar[10]);  
```  
  
 **Spravovaný podpis**  
  
```vb  
Sub New1(<MarshalAs(UnmanagedType.LPArray, SizeConst=10)> _  
   ar() As Integer)  
Sub New2(<MarshalAs(UnmanagedType.LPArray, SizeConst=200)> _  
   ar() As Double)  
Sub New2(<MarshalAs(UnmanagedType.LPArray, _  
   ArraySubType=UnmanagedType.LPWStr, SizeConst=10)> _  
   ar() As String)  
```  
  
```csharp  
void New1([MarshalAs(UnmanagedType.LPArray, SizeConst=10)] int[] ar);  
void New2([MarshalAs(UnmanagedType.LPArray, SizeConst=200)] double[] ar);  
void New2([MarshalAs(UnmanagedType.LPArray,
   ArraySubType=UnmanagedType.LPWStr, SizeConst=10)] String[] ar);  
```  
  
 Přestože můžete použít **atributy size_is** nebo **length_is** na pole ve zdroji IDL (Interface Definition Language) pro přenos velikosti klientovi, kompilátor jazyka MIDL (Microsoft Interface Definition Language) tyto informace do knihovny typů nerozšíří. Bez znalosti velikosti nemůže zařazovací služba interop zařazovat prvky pole. V důsledku toho jsou pole proměnné délky importována jako referenční argumenty. Například:  
  
 **Nespravovaný podpis**  
  
```cpp
HRESULT New1(int ar[]);  
HRESULT New2(int ArSize, [size_is(ArSize)] double ar[]);  
HRESULT New3(int ElemCnt, [length_is(ElemCnt)] LPStr ar[]);  
```  
  
 **Spravovaný podpis**  
  
```vb  
Sub New1(ByRef ar As Integer)  
Sub New2(ByRef ar As Double)  
Sub New3(ByRef ar As String)  
```  
  
```csharp  
void New1(ref int ar);
void New2(ref double ar);
void New3(ref String ar);
```  
  
 Zařazování můžete poskytnout velikost pole úpravou kódu MSIL (MSIL) společnosti Microsoft vytvořeného souborem Tlbimp.exe a jeho opětovnou kompilací. Podrobnosti o úpravě kódu MSIL naleznete [v tématu Přizpůsobení reložiových obkladů volání runtime](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100)). Chcete-li označit počet prvků v <xref:System.Runtime.InteropServices.MarshalAsAttribute> poli, použijte typ na parametr pole definice spravované metody jedním z následujících způsobů:  
  
- Identifikujte jiný parametr, který obsahuje počet prvků v poli. Parametry jsou identifikovány podle pozice, počínaje prvním parametrem jako číslo 0.
  
    ```vb  
    Sub [New](ElemCnt As Integer, _  
       \<MarshalAs(UnmanagedType.LPArray, SizeParamIndex:=1)> _  
       ar() As Integer)  
    ```  
  
    ```csharp  
    void New(  
       int ElemCnt,
       [MarshalAs(UnmanagedType.LPArray, SizeParamIndex=0)] int[] ar );  
    ```  
  
- Definujte velikost pole jako konstantu. Například:  
  
    ```vb  
    Sub [New](\<MarshalAs(UnmanagedType.LPArray, SizeConst:=128)> _  
       ar() As Integer)  
    ```  
  
    ```csharp  
    void New(  
       [MarshalAs(UnmanagedType.LPArray, SizeConst=128)] int[] ar );  
    ```  
  
 Při zařazování polí z nespravovaného kódu na spravovaný kód zařazuje **marshalAsAttribute** přidružený k parametru k určení velikosti pole. Pokud není zadána velikost pole, je zařazen pouze jeden prvek.  
  
> [!NOTE]
> **MarshalAsAttribute** nemá žádný vliv na zařazování spravovaných polí do nespravovaného kódu. V tomto směru je velikost pole určena vyšetřením. Neexistuje žádný způsob, jak zařadit podmnožinu spravovaného pole.  
  
 Interop zařazování používá **CoTaskMemAlloc** a **CoTaskMemFree** metody přidělit a načíst paměť. Přidělení paměti prováděné nespravovaným kódem musí také používat tyto metody.  
  
## <a name="passing-arrays-to-com"></a>Předávání polí com  
 Všechny typy spravovaných polí lze předat nespravovanému kódu ze spravovaného kódu. V závislosti na spravovaném typu a atributech, které jsou na něj použity, lze k poli přistupovat jako k bezpečnému poli nebo poli ve stylu C, jak je znázorněno v následující tabulce.  
  
|Typ spravovaného pole|Exportováno jako|  
|------------------------|-----------------|  
|**typ ELEMENT_TYPE_SZARRAY** **\<** *type***>**|<xref:System.Runtime.InteropServices.UnmanagedType>**. SafeArray(** *typ* **)**<br /><br /> **UnmanagedType.LPArray**<br /><br /> Typ je k dispozici v podpisu. Pořadí je vždy 1, dolní mez je vždy 0. Velikost je vždy známa za běhu.|  
|**ELEMENT_TYPE_ARRAY** **\<** *pořadí* **>** **\<** *rank* **\<** *bounds* **>** typů [ hranice ] **>**|**UnmanagedType.SafeArray(** *typ* **)**<br /><br /> **UnmanagedType.LPArray**<br /><br /> Typ, hodnost, hranice jsou uvedeny v podpisu. Velikost je vždy známa za běhu.|  
|**ELEMENT_TYPE_CLASS****\<**<xref:System.Array?displayProperty=nameWithType>**>**|**UT_Interface**<br /><br /> **UnmanagedType.SafeArray(** *typ* **)**<br /><br /> Typ, pořadí, hranice a velikost jsou vždy známy za běhu.|  
  
 Existuje omezení v ole automatizace týkající se polí struktur, které obsahují LPSTR nebo LPWSTR.  Proto **string** pole musí být zařazeny jako **UnmanagedType.BSTR**. V opačném případě bude vyvolána výjimka.  
  
### <a name="element_type_szarray"></a>ELEMENT_TYPE_SZARRAY  
 Při exportu metody obsahující **parametr ELEMENT_TYPE_SZARRAY** (jednorozměrné pole) ze sestavení .NET do knihovny typů je parametr pole převeden na **SAFEARRAY** daného typu. Stejná pravidla převodu platí pro typy prvků pole. Obsah spravovaného pole se automaticky zkopíruje ze spravované paměti do **safearray**. Například:  
  
#### <a name="managed-signature"></a>Spravovaný podpis  
  
```vb  
Sub [New](ar() As Long)  
Sub [New](ar() As String)  
```  
  
```csharp  
void New(long[] ar );  
void New(String[] ar );  
```  
  
#### <a name="unmanaged-signature"></a>Nespravovaný podpis  
  
```cpp
HRESULT New([in] SAFEARRAY( long ) ar);
HRESULT New([in] SAFEARRAY( BSTR ) ar);  
```  
  
 Pořadí bezpečných polí je vždy 1 a dolní mez je vždy 0. Velikost je určena v době běhu podle velikosti předávaného spravovaného pole.  
  
 Pole lze také zařadit jako pole stylu <xref:System.Runtime.InteropServices.MarshalAsAttribute> C pomocí atributu. Například:  
  
#### <a name="managed-signature"></a>Spravovaný podpis  
  
```vb  
Sub [New](<MarshalAs(UnmanagedType.LPArray, SizeParamIndex:=1)> _  
   ar() As Long, size as Integer)  
Sub [New](<MarshalAs(UnmanagedType.LPArray, SizeParamIndex:=1)> _  
   ar() As String, size as Integer)  
Sub [New](<MarshalAs(UnmanagedType.LPArray, _  
   ArraySubType= UnmanagedType.LPStr, SizeParamIndex:=1)> _  
   ar() As String, size as Integer)  
```  
  
```csharp  
void New([MarshalAs(UnmanagedType.LPArray, SizeParamIndex=1)]
   long [] ar, int size );  
void New([MarshalAs(UnmanagedType.LPArray, SizeParamIndex=1)]
   String [] ar, int size );  
void New([MarshalAs(UnmanagedType.LPArray, ArraySubType=
   UnmanagedType.LPStr, SizeParamIndex=1)]
   String [] ar, int size );  
```  
  
#### <a name="unmanaged-signature"></a>Nespravovaný podpis  
  
```cpp
HRESULT New(long ar[]);
HRESULT New(BSTR ar[]);
HRESULT New(LPStr ar[]);  
```  
  
 Přestože zařazovací zařízení má informace o délce potřebné k zařazovací pole, délka pole je obvykle předána jako samostatný argument pro předávání délky volaného.  
  
### <a name="element_type_array"></a>ELEMENT_TYPE_ARRAY  
 Při exportu metody obsahující **parametr ELEMENT_TYPE_ARRAY** z sestavení .NET do knihovny typů je parametr pole převeden na **SAFEARRAY** daného typu. Obsah spravovaného pole se automaticky zkopíruje ze spravované paměti do **safearray**. Například:  
  
#### <a name="managed-signature"></a>Spravovaný podpis  
  
```vb  
Sub [New](ar(,) As Long)  
Sub [New](ar(,) As String)  
```  
  
```csharp  
void New( long [,] ar );  
void New( String [,] ar );  
```  
  
#### <a name="unmanaged-signature"></a>Nespravovaný podpis  
  
```cpp
HRESULT New([in] SAFEARRAY( long ) ar);
HRESULT New([in] SAFEARRAY( BSTR ) ar);  
```  
  
 Pořadí, velikost a hranice bezpečných polí jsou určeny za běhu charakteristikami spravovaného pole.  
  
 Pole lze také zařadit jako pole stylu <xref:System.Runtime.InteropServices.MarshalAsAttribute> C použitím atributu. Například:  
  
#### <a name="managed-signature"></a>Spravovaný podpis  
  
```vb  
Sub [New](<MarshalAs(UnmanagedType.LPARRAY, SizeParamIndex:=1)> _  
   ar(,) As Long, size As Integer)  
Sub [New](<MarshalAs(UnmanagedType.LPARRAY, _  
   ArraySubType:=UnmanagedType.LPStr, SizeParamIndex:=1)> _  
   ar(,) As String, size As Integer)  
```  
  
```csharp  
void New([MarshalAs(UnmanagedType.LPARRAY, SizeParamIndex=1)]
   long [,] ar, int size );  
void New([MarshalAs(UnmanagedType.LPARRAY,
   ArraySubType= UnmanagedType.LPStr, SizeParamIndex=1)]
   String [,] ar, int size );  
```  
  
#### <a name="unmanaged-signature"></a>Nespravovaný podpis  
  
```cpp
HRESULT New(long ar[]);
HRESULT New(LPStr ar[]);  
```  
  
 Vnořená pole nelze zařadit. Například následující podpis generuje chybu při exportu s [Type Library Exporter (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md).  
  
#### <a name="managed-signature"></a>Spravovaný podpis  
  
```vb  
Sub [New](ar()()() As Long)  
```  
  
```csharp  
void New(long [][][] ar );  
```  
  
### <a name="element_type_class-systemarray"></a>> \<ELEMENT_TYPE_CLASS System.Array  
 Při exportu metody <xref:System.Array?displayProperty=nameWithType> obsahující parametr ze sestavení .NET do knihovny typů je parametr pole převeden na **_Array** rozhraní. Obsah spravovaného pole jsou přístupné pouze prostřednictvím metod a vlastností **rozhraní _Array.** **System.Array** lze také zařadit jako **SAFEARRAY** pomocí atributu. <xref:System.Runtime.InteropServices.MarshalAsAttribute> Při zařazené jako bezpečné pole, prvky pole jsou zařazeny jako varianty. Například:  
  
#### <a name="managed-signature"></a>Spravovaný podpis  
  
```vb  
Sub New1( ar As System.Array )  
Sub New2( <MarshalAs(UnmanagedType.Safe array)> ar As System.Array )  
```  
  
```csharp  
void New1( System.Array ar );  
void New2( [MarshalAs(UnmanagedType.Safe array)] System.Array ar );  
```  
  
#### <a name="unmanaged-signature"></a>Nespravovaný podpis  
  
```cpp
HRESULT New([in] _Array *ar);
HRESULT New([in] SAFEARRAY(VARIANT) ar);  
```  
  
### <a name="arrays-within-structures"></a>Pole v rámci struktur  
 Nespravované struktury mohou obsahovat vložená pole. Ve výchozím nastavení jsou tato vložená pole polí zařazena jako SAFEARRAY. V následujícím příkladu je vložené pole, `s1` které je přiděleno přímo v rámci samotné struktury.  
  
#### <a name="unmanaged-representation"></a>Nespravovaná reprezentace  
  
```cpp
struct MyStruct {  
    short s1[128];  
}  
```  
  
 Pole mohou být zařazena jako <xref:System.Runtime.InteropServices.UnmanagedType>, což <xref:System.Runtime.InteropServices.MarshalAsAttribute> vyžaduje nastavení pole. Velikost lze nastavit pouze jako konstantu. Následující kód ukazuje odpovídající spravovanou definici . `MyStruct`  
  
```vb  
Public Structure <StructLayout(LayoutKind.Sequential)> MyStruct  
   Public <MarshalAs(UnmanagedType.ByValArray, SizeConst := 128)> _  
     s1() As Short  
End Structure  
```  
  
```csharp  
[StructLayout(LayoutKind.Sequential)]  
public struct MyStruct {  
   [MarshalAs(UnmanagedType.ByValArray, SizeConst=128)] public short[] s1;  
}  
```  
  
## <a name="see-also"></a>Viz také

- [Výchozí chování zařazování](default-marshaling-behavior.md)
- [Přenositelné a nepřenositelné typy](blittable-and-non-blittable-types.md)
- [Směrové atributy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))
- [Kopírování a přichycování](copying-and-pinning.md)
