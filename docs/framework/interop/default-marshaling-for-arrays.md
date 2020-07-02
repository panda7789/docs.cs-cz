---
title: Výchozí zařazování pro pole
description: Pochopte Výchozí zařazování pro pole. Zkontrolujte spravovaná pole, nespravovaná pole, předávání parametrů pole do kódu .NET a předávání polí do modelu COM.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- interop marshaling, arrays
- arrays, interop marshaling
ms.assetid: 8a3cca8b-dd94-4e3d-ad9a-9ee7590654bc
ms.openlocfilehash: eafed0e0a0150923aae0fa68a1b96e6d9d66b07a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622559"
---
# <a name="default-marshaling-for-arrays"></a>Výchozí zařazování pro pole
V aplikaci, která se skládá výhradně ze spravovaného kódu, modul common language runtime předá typy polí jako vstupně-výstupní parametry. Naproti tomu zařazovací modul Interop předá pole jako parametry ve výchozím nastavení.  
  
 S [optimalizací připnutí](copying-and-pinning.md)se může při interakci s objekty ve stejném objektu Apartment zdát, že se jako parametr v/v funguje přenositelná pole. Nicméně pokud později exportujete kód do knihovny typů, která se používá k vygenerování mezipočítačového proxy serveru, a tato knihovna slouží k zařazování volání napříč objekty Apartment, volání se mohou vrátit na hodnotu true v chování parametrů.  
  
 Pole jsou složitá podle povahy a rozdíly mezi spravovanými a nespravovanými poli opravňují více informací než jiné nepřenositelné typy.  
  
## <a name="managed-arrays"></a>Spravovaná pole  
 Typy spravovaných polí se mohou lišit. <xref:System.Array?displayProperty=nameWithType>Třída je však základní třídou všech typů polí. Třída **System. Array** má vlastnosti pro určení pořadí, délky a dolních a horních mezí pole a také metod pro přístup, řazení, hledání, kopírování a vytváření polí.  
  
 Tyto typy polí jsou dynamické a nemají odpovídající statický typ definovaný v knihovně základních tříd. Je vhodné si představit každou kombinaci typu prvku a seřadit jako odlišný typ pole. Proto jednorozměrné pole celých čísel je jiného typu než jednorozměrné pole typu Double. Podobně dvourozměrné pole celých čísel je jiné než jednorozměrné pole celých čísel. Hranice pole se při porovnávání typů neberou v potaz.  
  
 Jak ukazuje následující tabulka, jakákoli instance spravovaného pole musí být konkrétního typu prvku, pořadí a dolní mez.  
  
|Typ spravovaného pole|Typ elementu|Rank|Dolní mez|Zápis signatury|  
|------------------------|------------------|----------|-----------------|------------------------|  
|**ELEMENT_TYPE_ARRAY**|Zadáno podle typu.|Určeno podle pořadí.|Volitelně určené hranicemi.|*typ* **[** *n*,*m* **]**|  
|**ELEMENT_TYPE_CLASS**|Není známo|Není známo|Není známo|**System. Array**|  
|**ELEMENT_TYPE_SZARRAY**|Zadáno podle typu.|1|0|*typ* **[** *n* **]**|  
  
## <a name="unmanaged-arrays"></a>Nespravovaná pole  
 Nespravovaná pole jsou buď bezpečná pole ve stylu COM, nebo pole ve stylu jazyka C s pevnou nebo proměnnou délkou. Bezpečná pole jsou samy popisující pole, která přenesou typ, pořadí a meze přidružených dat pole. Pole stylu C jsou jednorozměrná typová pole s pevně nastavenou dolní mezí 0. Zařazovací služba má omezené podpory pro oba typy polí.  
  
## <a name="passing-array-parameters-to-net-code"></a>Předávání parametrů pole do kódu .NET  
 Pole stylu C a bezpečná pole mohou být předány do kódu .NET z nespravovaného kódu jako bezpečné pole nebo pole ve stylu jazyka C. Následující tabulka ukazuje nespravovaný typ hodnoty a importovaný typ.  
  
|Nespravovaný typ|Importovaný typ|  
|--------------------|-------------------|  
|**SAFEARRAY (** *typ* **)**|**ELEMENT_TYPE_SZARRAY****\<** *ConvertedType* **>**<br /><br /> Rank = 1, dolní mez = 0. Velikost je známá pouze v případě, že je k dispozici ve spravovaném podpisu. Bezpečná pole, která nejsou pořadí = 1 nebo dolní mez = 0, nelze zařadit jako **SZARRAY**.|  
|*Typ*  **[]**|**ELEMENT_TYPE_SZARRAY****\<** *ConvertedType* **>**<br /><br /> Rank = 1, dolní mez = 0. Velikost je známá pouze v případě, že je k dispozici ve spravovaném podpisu.|  
  
### <a name="safe-arrays"></a>Bezpečná pole  
 Když je bezpečné pole importováno z knihovny typů do sestavení .NET, pole je převedeno na jednorozměrné pole známého typu (například **int**). Stejná pravidla převodu typů, která platí pro parametry, platí také pro prvky pole. Například bezpečné pole typů **BSTR** se stávají spravovaným polem řetězců a bezpečné pole variant se stávají spravovaným polem objektů. Typ elementu **SAFEARRAY** je zachycen z knihovny typů a uložen v hodnotě **SAFEARRAY** <xref:System.Runtime.InteropServices.UnmanagedType> výčtu.  
  
 Vzhledem k tomu, že pořadí a meze bezpečného pole nelze určit z knihovny typů, předpokládá se, že pořadí je rovno 1 a dolní mez je rovna 0. Pořadí a meze musí být definovány ve spravovaném podpisu vytvořeném modulem pro [Import knihovny typů (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md). Pokud pořadí předané metodě v době běhu se liší, <xref:System.Runtime.InteropServices.SafeArrayRankMismatchException> je vyvolána. Pokud se typ pole předaného v době běhu liší, <xref:System.Runtime.InteropServices.SafeArrayTypeMismatchException> je vyvolána. Následující příklad zobrazuje bezpečná pole ve spravovaném a nespravovaném kódu.  
  
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
  
 Vícerozměrné nebo nenulové bezpečné pole, lze zařadit do spravovaného kódu, pokud je podpis metody vytvořený pomocí Tlbimp.exe změněn tak, aby označoval typ prvku **ELEMENT_TYPE_ARRAY** namísto **ELEMENT_TYPE_SZARRAY**. Alternativně můžete použít přepínač **/sysarray** s Tlbimp.exe pro import všech polí jako <xref:System.Array?displayProperty=nameWithType> objektů. V případech, kdy je předávané pole známo multidimenzionální, můžete upravit kód jazyka MSIL (Microsoft Intermediate Language) vytvořený pomocí Tlbimp.exe a poté jej znovu zkompilovat. Podrobnosti o tom, jak upravit kód jazyka MSIL, najdete v tématu [přizpůsobení obálek za běhu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100)), které lze volat.  
  
### <a name="c-style-arrays"></a>Pole stylu C  
 Když je pole ve stylu jazyka C importováno z knihovny typů do sestavení .NET, pole je převedeno na **ELEMENT_TYPE_SZARRAY**.  
  
 Typ prvku pole je určen z knihovny typů a zůstane během importu. Stejná pravidla převodu, která platí pro parametry, platí také pro prvky pole. Například pole typů **typem LPStr** se stávají polem typů **řetězců** . Tlbimp.exe zachycuje typ prvku pole a aplikuje <xref:System.Runtime.InteropServices.MarshalAsAttribute> atribut na parametr.  
  
 Předpokládá se, že se rozměr pole rovná 1. Pokud je pořadí větší než 1, pole je zařazeno jako jednorozměrné pole v pořadí podle sloupců. Dolní mez se vždycky rovná 0.  
  
 Knihovny typů mohou obsahovat pole s pevnou nebo proměnlivou délkou. Tlbimp.exe mohou importovat pouze pole s pevnou délkou z knihoven typů, protože knihovny typů nemají informace potřebné pro zařazování polí s proměnnou délkou. S poli s pevnou délkou je velikost importována z knihovny typů a zachycena v **MarshalAsAttribute** , která je použita pro parametr.  
  
 Je nutné ručně definovat knihovny typů obsahující pole s proměnnou délkou, jak je znázorněno v následujícím příkladu.  
  
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
  
 I když můžete použít atributy **size_is** nebo **length_is** na pole ve zdroji rozhraní IDL (Interface Definition Language) pro předávání velikosti klientovi, kompilátor rozhraní Microsoft Interface Definition Language (MIDL) tyto informace nerozšíří do knihovny typů. Bez znalosti velikosti nemůže služba interop marshaling zařadit prvky pole. V důsledku toho se pole s proměnlivou délkou importují jako argumenty reference. Příklad:  
  
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
  
 Zařazovacímu programu můžete poskytnout velikost pole úpravou kódu jazyka MSIL (Microsoft Intermediate Language) vytvořeného pomocí Tlbimp.exe a opětovnou kompilací. Podrobnosti o tom, jak upravit kód jazyka MSIL, najdete v tématu [přizpůsobení obálek za běhu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100)), které lze volat. Chcete-li určit počet prvků v poli, použijte <xref:System.Runtime.InteropServices.MarshalAsAttribute> typ pro parametr pole definice spravované metody jedním z následujících způsobů:  
  
- Identifikujte další parametr, který obsahuje počet prvků v poli. Parametry jsou identifikovány podle pozice počínaje prvním parametrem jako číslo 0.
  
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
  
- Definujte velikost pole jako konstantu. Příklad:  
  
    ```vb  
    Sub [New](\<MarshalAs(UnmanagedType.LPArray, SizeConst:=128)> _  
       ar() As Integer)  
    ```  
  
    ```csharp  
    void New(  
       [MarshalAs(UnmanagedType.LPArray, SizeConst=128)] int[] ar );  
    ```  
  
 Při zařazování polí z nespravovaného kódu do spravovaného kódu zařazovací modul zkontroluje **MarshalAsAttribute** přidružený k parametru a určí velikost pole. Pokud není určena velikost pole, je zařazen pouze jeden prvek.  
  
> [!NOTE]
> **MarshalAsAttribute** nemá žádný vliv na zařazování spravovaných polí do nespravovaného kódu. V tomto směru je velikost pole určena kontrolou. Neexistuje žádný způsob, jak zařadit podmnožinu spravovaného pole.  
  
 Zařazovací modul Interop používá metody **CoTaskMemAlloc** a **CoTaskMemFree** k přidělení a načtení paměti. Tyto metody musí používat i přidělení paměti prováděné nespravovaným kódem.  
  
## <a name="passing-arrays-to-com"></a>Předávání polí do modelu COM  
 Všechny typy spravovaných polí lze předat nespravovanému kódu ze spravovaného kódu. V závislosti na spravovaném typu a použitých atributech může být pole dostupné jako bezpečné pole nebo ve stylu jazyka C, jak je znázorněno v následující tabulce.  
  
|Typ spravovaného pole|Exportováno jako|  
|------------------------|-----------------|  
|**ELEMENT_TYPE_SZARRAY****\<** *type* **>**|<xref:System.Runtime.InteropServices.UnmanagedType>**. SafeArray (** *typ* **)**<br /><br /> **UnmanagedType. typy LPArray**<br /><br /> V signatuře je uveden typ. Pořadí je vždy 1, dolní hranice je vždy 0. Velikost je vždy známá v době běhu.|  
|**ELEMENT_TYPE_ARRAY** **\<** *type* **>** **\<** *rank* **>**[**\<** *bounds* **>**]|**UnmanagedType. SAFEARRAY (** *typ* **)**<br /><br /> **UnmanagedType. typy LPArray**<br /><br /> Typ, rozsah, meze jsou k dispozici v signatuře. Velikost je vždy známá v době běhu.|  
|**ELEMENT_TYPE_CLASS****\<**<xref:System.Array?displayProperty=nameWithType>**>**|**UT_Interface**<br /><br /> **UnmanagedType. SAFEARRAY (** *typ* **)**<br /><br /> Typ, pořadí, meze a velikost jsou vždy známy v době běhu.|  
  
 V automatizaci OLE existuje omezení související s poli struktur, která obsahují typem LPStr nebo LPWSTR.  Proto musí být pole **řetězců** zařazena jako **UnmanagedType. BSTR**. V opačném případě bude vyvolána výjimka.  
  
### <a name="element_type_szarray"></a>ELEMENT_TYPE_SZARRAY  
 Pokud je metoda obsahující **ELEMENT_TYPE_SZARRAY** parametr (jednorozměrné pole) exportována ze sestavení .NET do knihovny typů, je parametr pole převeden na hodnotu **SAFEARRAY** daného typu. Stejná pravidla převodu se vztahují na typy prvků pole. Obsah spravovaného pole se automaticky zkopíruje ze spravované paměti do pole **SAFEARRAY**. Příklad:  
  
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
  
 Rozsah bezpečných polí je vždycky 1 a dolní hranice je vždycky 0. Velikost je určena v době běhu podle velikosti předávaného spravovaného pole.  
  
 Pole lze také zařadit jako pole ve stylu jazyka C pomocí <xref:System.Runtime.InteropServices.MarshalAsAttribute> atributu. Příklad:  
  
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
  
 I když zařazovací jednotka má informace o délce potřebné k zařazení pole, délka pole je obvykle předána jako samostatný argument pro vyjádření délky volaného.  
  
### <a name="element_type_array"></a>ELEMENT_TYPE_ARRAY  
 Pokud je metoda obsahující **ELEMENT_TYPE_ARRAY** parametr exportována ze sestavení .NET do knihovny typů, je parametr pole převeden na hodnotu **SAFEARRAY** daného typu. Obsah spravovaného pole se automaticky zkopíruje ze spravované paměti do pole **SAFEARRAY**. Příklad:  
  
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
  
 Pořadí, velikost a hranice bezpečných polí jsou určeny za běhu podle vlastností spravovaného pole.  
  
 Pole lze také zařadit jako pole ve stylu jazyka C použitím <xref:System.Runtime.InteropServices.MarshalAsAttribute> atributu. Příklad:  
  
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
  
 Vnořená pole nelze zařadit. Například následující signatura generuje chybu při exportu pomocí [typu Exportér knihovny typů (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md).  
  
#### <a name="managed-signature"></a>Spravovaný podpis  
  
```vb  
Sub [New](ar()()() As Long)  
```  
  
```csharp  
void New(long [][][] ar );  
```  
  
### <a name="element_type_class-systemarray"></a>ELEMENT_TYPE_CLASS\<System.Array>  
 Je-li metoda, která obsahuje <xref:System.Array?displayProperty=nameWithType> parametr, exportována ze sestavení .NET do knihovny typů, je parametr pole převeden na **_array** rozhraní. Obsah spravovaného pole je přístupný pouze prostřednictvím metod a vlastností rozhraní **_array** . **System. Array** se dá také zařadit jako **SAFEARRAY** pomocí <xref:System.Runtime.InteropServices.MarshalAsAttribute> atributu. Při zařazování jako bezpečné pole jsou prvky pole zařazeny jako varianty. Příklad:  
  
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
  
### <a name="arrays-within-structures"></a>Pole ve strukturách  
 Nespravované struktury mohou obsahovat vložená pole. Ve výchozím nastavení jsou tato vložená pole pole zařazena jako SAFEARRAY. V následujícím příkladu `s1` je vloženo pole, které je přiděleno přímo v rámci struktury samotné.  
  
#### <a name="unmanaged-representation"></a>Nespravované reprezentace  
  
```cpp
struct MyStruct {  
    short s1[128];  
}  
```  
  
 Pole lze zařadit jako <xref:System.Runtime.InteropServices.UnmanagedType> , což vyžaduje, abyste nastavili <xref:System.Runtime.InteropServices.MarshalAsAttribute> pole. Velikost lze nastavit pouze jako konstantu. Následující kód ukazuje odpovídající spravovanou definici `MyStruct` .  
  
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
  
## <a name="see-also"></a>Viz také:

- [Výchozí chování zařazování](default-marshaling-behavior.md)
- [Přenositelné a nepřenositelné typy](blittable-and-non-blittable-types.md)
- [Směrové atributy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))
- [Kopírování a přichycování](copying-and-pinning.md)
