---
title: "Výchozí zařazování pro pole"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- interop marshaling, arrays
- arrays, interop marshaling
ms.assetid: 8a3cca8b-dd94-4e3d-ad9a-9ee7590654bc
caps.latest.revision: "19"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 91df17448a57f7495dc95fb2b4ab1fa63dd8a27f
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="default-marshaling-for-arrays"></a>Výchozí zařazování pro pole
V aplikaci, která obsahuje jenom spravovaného kódu modul common language runtime předá typy polí jako vstupně -výstupní parametry. Naproti tomu spolupráce vláken předá pole jako parametry ve výchozím nastavení.  
  
 S [Připnutí optimalizace](../../../docs/framework/interop/copying-and-pinning.md), pole přenositelné můžou zdánlivě pracovat jako ve vstupně -výstupnímu parametru při interakci s objekty ve stejném typu apartment. Ale pokud později exportovat kód do knihovny typů sloužící ke generování proxy serveru mezi počítači a že knihovna se používá k zařazování voláními napříč apartment, volání obnovit na hodnotu true v parametru chování.  
  
 Pole jsou svou povahou komplexní a rozdíly mezi spravovanými a nespravovanými pole zaručit informace než jiné nepřenositelné typy. Toto téma obsahuje následující informace na zařazování pole:  
  
-   [Spravovaná pole](#cpcondefaultmarshalingforarraysanchor1)  
  
-   [Nespravované pole](#cpcondefaultmarshalingforarraysanchor2)  
  
-   [Předávání parametrů pole pro kód .NET](#cpcondefaultmarshalingforarraysanchor3)  
  
-   [Předávání polí do modelu COM](#cpcondefaultmarshalingforarraysanchor4)  
  
<a name="cpcondefaultmarshalingforarraysanchor1"></a>   
## <a name="managed-arrays"></a>Spravovaná pole  
 Spravovaná pole, které mohou být různé typy; ale <xref:System.Array?displayProperty=nameWithType> třída je základní třída všech typů pole. **System.Array** třída má vlastnosti pro určení pořadí, délku a dolní a horní meze pole, jakož i metody pro přístup k, řazení, hledání, kopírování a vytvoření pole.  
  
 Tyto typy polí je dynamická a nemají odpovídající statické typem definovaným v knihovně základní třídy. Je vhodné zamyslet nad každou kombinaci typ elementu a pořadí jako odlišné typ pole. Jednorozměrné pole celých čísel je proto jiného typu než jednorozměrné pole dvojité typů. Podobně se liší od jednorozměrné pole celých čísel na dvourozměrné pole celých čísel. Při porovnávání typů, nejsou považovány za hranice pole.  
  
 Jak ukazuje následující tabulka, všechny instance spravovaného pole musí být typu konkrétní elementu, pořadí a dolní mez.  
  
|Spravovaný typ pole.|Typ elementu|Pořadí|Dolní mez|Zápis podpis|  
|------------------------|------------------|----------|-----------------|------------------------|  
|**ELEMENT_TYPE_ARRAY**|Zadaný typ.|Zadaný pořadí.|Volitelně zadaný rozsah.|*typ* **[**  *n* ,*m* **]**|  
|**ELEMENT_TYPE_CLASS**|Neznámé|Neznámé|Neznámé|**System.Array**|  
|**ELEMENT_TYPE_SZARRAY**|Zadaný typ.|1|0|*typ* **[**  *n*  **]**|  
  
<a name="cpcondefaultmarshalingforarraysanchor2"></a>   
## <a name="unmanaged-arrays"></a>Nespravované pole  
 Nespravované pole je COM stylu bezpečné pole nebo pole stylu jazyka C s pevnou velikostí, nebo proměnnou délkou. Bezpečné pole jsou popisující samy sebe pole, které zajišťují typu, pořadí a rozsah dat přidružené žádné pole. Pole stylu jazyka C jsou jednorozměrné typovaná pole s pevnou dolní mez 0. Služba zařazování má omezenou podporu pro oba typy polí.  
  
<a name="cpcondefaultmarshalingforarraysanchor3"></a>   
## <a name="passing-array-parameters-to-net-code"></a>Předávání parametrů pole pro kód .NET  
 Pole stylu jazyka C a bezpečné pole lze předat kód .NET z nespravovaného kódu jako bezpečné pole nebo pole ve stylu jazyka. Následující tabulka uvádí nespravovaný typ hodnoty a typ importované.  
  
|Nespravovaný typ|Importovaný typ|  
|--------------------|-------------------|  
|**SafeArray (** *typ* **)**|**ELEMENT_TYPE_SZARRAY**  **\<**  *ConvertedType***>**<br /><br /> Pořadí = 1, dolní mez = 0. Velikost je známý jenom v případě, že součástí spravované podpis. Bezpečné pole, které nejsou rank = 1, nebo dolní mez = 0 nelze zařadit jako **SZARRAY**.|  
|*Typ***]** |**ELEMENT_TYPE_SZARRAY**  **\<**  *ConvertedType***>**<br /><br /> Pořadí = 1, dolní mez = 0. Velikost je známý jenom v případě, že součástí spravované podpis.|  
  
### <a name="safe-arrays"></a>Bezpečné pole  
 Při importu bezpečným polím z knihovny typů pro sestavení .NET pole jsou převedeny na jednorozměrné pole známé typu (například **int**). Stejné pravidel převodu typů, které se vztahují na parametry platí také pro elementy pole. Například bezpečným polím z **BSTR** typy bude spravované pole řetězců a bezpečným polím variant bude spravované pole objektů. **SAFEARRAY** zaznamenat z knihovny typů a uložit v typu elementu **SAFEARRAY** hodnotu <xref:System.Runtime.InteropServices.UnmanagedType> výčtu.  
  
 Protože pořadí a hranice bezpečné pole nelze určit z knihovny typů, pořadí se předpokládá, že rovno 1 a dolní hranice se předpokládá, že rovna 0. Pořadí a rozsah musí být definován v spravované podpis vyprodukované [Importér knihovny typů (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md). Pokud se liší pořadí předaný metodě za běhu, <xref:System.Runtime.InteropServices.SafeArrayRankMismatchException> je vyvolána výjimka. Pokud v době běhu byl předán typ pole se liší, <xref:System.Runtime.InteropServices.SafeArrayTypeMismatchException> je vyvolána výjimka. Následující příklad ukazuje bezpečné pole v spravovanými a nespravovanými kódu.  
  
 **Nespravované podpis**  
  
```  
HRESULT New1([in] SAFEARRAY( int ) ar);  
HRESULT New2([in] SAFEARRAY( DATE ) ar);  
HRESULT New3([in, out] SAFEARRAY( BSTR ) *ar);  
```  
  
 **Spravované podpis**  
  
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
  
 Multidimenzionální nebo nenulové hodnoty svázané bezpečné pole, může být zařazeno do spravovaného kódu, pokud metoda podpis vyprodukované Tlbimp.exe je upravit tak, aby označuje typ elementu **ELEMENT_TYPE_ARRAY** místo **ELEMENT_ TYPE_SZARRAY**. Alternativně můžete použít **/sysarray** přepínač s Tlbimp.exe k importu všech polí jako <xref:System.Array?displayProperty=nameWithType> objekty. V případech, kde je znám být multidimenzionální pole předávány můžete upravit Microsoft (MSIL intermediate language) kódu vytvořeného pomocí Tlbimp.exe a pak ji znovu zkompilovat. Podrobnosti o tom, jak upravit MSIL kódu najdete v tématu [přizpůsobení běhové obálky s možností](http://msdn.microsoft.com/library/4652beaf-77d0-4f37-9687-ca193288c0be).  
  
### <a name="c-style-arrays"></a>Pole stylu jazyka C  
 Pokud pole ve stylu jazyka je importované z knihovny typů do sestavení .NET, pole je převést na **ELEMENT_TYPE_SZARRAY**.  
  
 Typ elementu pole je určen z knihovny typů a zachovají během importu. Stejná pravidla převodu, které se vztahují na parametry platí také pro elementy pole. Například pole **LPStr** typy stane pole **řetězec** typy. Tlbimp.exe zaznamená typ elementu pole a použije <xref:System.Runtime.InteropServices.MarshalAsAttribute> atribut parametr.  
  
 Pole pořadí se předpokládá, že rovnat 1. Pokud pořadí je větší než 1, je pole zařazené jako jednorozměrné pole uváděnými sloupce. Dolní mez se vždy rovná 0.  
  
 Knihovny typů může obsahovat pole Délka pevné nebo proměnné. Tlbimp.exe můžete importovat pouze pevnou délkou pole z knihovny typů, protože knihovny typů neobsahují informace potřebné pro zařazování proměnlivou délkou pole. S pevnou délkou pole velikost naimportované z knihovny typů a zachyceného **MarshalAsAttribute** který se použije pro parametr.  
  
 Knihovny typů s proměnlivou délkou pole, je nutné zadat ručně, jak je znázorněno v následujícím příkladu.  
  
 **Nespravované podpis**  
  
```  
HRESULT New1(int ar[10]);  
HRESULT New2(double ar[10][20]);  
HRESULT New3(LPWStr ar[10]);  
```  
  
 **Spravované podpis**  
  
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
  
 I když můžete použít **size_is –** nebo **length_is –** atributy na pole ve zdroji definice jazyka IDL (Interface) pro vyjádření velikost ke klientovi, jazyk definice rozhraní Microsoft (MIDL) kompilátoru nešířily tyto informace do knihovny typů. Aniž by věděly, velikost, nelze zprostředkovatel komunikace s objekty zařazování služby zařazování prvků pole. V důsledku toho se importují proměnlivou délkou pole jako argumenty odkaz. Příklad:  
  
 **Nespravované podpis**  
  
```  
HRESULT New1(int ar[]);  
HRESULT New2(int ArSize, [size_is(ArSize)] double ar[]);  
HRESULT New3(int ElemCnt, [length_is(ElemCnt)] LPStr ar[]);  
```  
  
 **Spravované podpis**  
  
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
  
 Zařazování můžete poskytnout velikost pole úpravou Microsoft (MSIL intermediate language) kódu vytvořeného pomocí Tlbimp.exe a pak kompilovat znovu. Podrobnosti o tom, jak upravit MSIL kódu najdete v tématu [přizpůsobení běhové obálky s možností](http://msdn.microsoft.com/library/4652beaf-77d0-4f37-9687-ca193288c0be). Pokud chcete zadat počet prvků v poli, použít <xref:System.Runtime.InteropServices.MarshalAsAttribute> typ pro parametr pole spravované metoda definice v jednom z následujících způsobů:  
  
-   Identifikujte jiný parametr, který obsahuje počet prvků v poli. Parametry jsou identifikovány pozice, počínaje první parametr jako číslo 0.     
  
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
  
-   Zadejte velikost pole jako konstanta. Příklad:  
  
    ```vb  
    Sub [New](\<MarshalAs(UnmanagedType.LPArray, SizeConst:=128)> _  
       ar() As Integer)  
    ```  
  
    ```csharp  
    void New(  
       [MarshalAs(UnmanagedType.LPArray, SizeConst=128)] int[] ar );  
    ```  
  
 Při zařazování polí z nespravovaného kódu do spravovaného kódu, zkontroluje zařazování **MarshalAsAttribute** přidružené parametr k určení velikosti pole. Pokud není zadán velikost pole, je zařadit pouze jeden element.  
  
> [!NOTE]
>  **MarshalAsAttribute** nemá žádný vliv na zařazování spravované pole na nespravovaný kód. Velikost pole v tomto směru, je dáno prozkoumání. Neexistuje žádný způsob, jak zařazování podmnožinu spravovaného pole.  
  
 Používá zprostředkovatele komunikace s objekty vláken **CoTaskMemAlloc** a **CoTaskMemFree** metody přidělit a načtení paměti. Přidělení paměti provádí nespravovaného kódu musíte taky použít tyto metody.  
  
<a name="cpcondefaultmarshalingforarraysanchor4"></a>   
## <a name="passing-arrays-to-com"></a>Předávání polí do modelu COM  
 Všechny typy spravované pole lze předat nespravovaného kódu ze spravovaného kódu. V závislosti na spravovaný typ a atributy použité na jeho pole můžou mít přístup bezpečné pole nebo pole stylu jazyka C, jak je znázorněno v následující tabulce.  
  
|Spravovaný typ pole.|Exportovat jako|  
|------------------------|-----------------|  
|**ELEMENT_TYPE_SZARRAY**  **\<**  *typ***>**|<xref:System.Runtime.InteropServices.UnmanagedType>**. SafeArray (** *typ* **)**<br /><br /> **UnmanagedType.LPArray**<br /><br /> Typ je součástí podpis. Pořadí je vždy 1, dolní mez je vždy 0. Velikost se vždy označuje za běhu.|  
|**ELEMENT_TYPE_ARRAY**  **\<**  *typ*  **>**   **\<**  *pořadí*  **>** [ **\<**  *hranice*  **>** ]|**UnmanagedType.SafeArray (** *typ* **)**<br /><br /> **UnmanagedType.LPArray**<br /><br /> Rank, hranice typu, jsou uvedeny v podpis. Velikost se vždy označuje za běhu.|  
|**ELEMENT_TYPE_CLASS****\<**<xref:System.Array?displayProperty=nameWithType>**>**|**UT_Interface**<br /><br /> **UnmanagedType.SafeArray (** *typ* **)**<br /><br /> Typ, pořadí, rozsah a velikosti jsou vždy známé za běhu.|  
  
 Existuje omezení v automatizace OLE týkající se pole struktur, které obsahují LPSTR nebo LPWSTR.  Proto **řetězec** pole mají být zařazena jako **UnmanagedType.BSTR**. Jinak bude vyvolána výjimka.  
  
### <a name="elementtypeszarray"></a>ELEMENT_TYPE_SZARRAY  
 Když metoda obsahuje **ELEMENT_TYPE_SZARRAY** parametr (jednorozměrné pole) se exportují z sestavení .NET do knihovny typů, parametr pole jsou převedeny na **SAFEARRAY** daného typu. Stejná pravidla převodu platí pro pole typů elementů. Obsah bude spravované pole se automaticky zkopírují ze spravované paměti do **SAFEARRAY**. Příklad:  
  
#### <a name="managed-signature"></a>Spravované podpis  
  
```vb  
Sub [New](ar() As Long)  
Sub [New](ar() As String)  
```  
  
```csharp  
void New(long[] ar );  
void New(String[] ar );  
```  
  
#### <a name="unmanaged-signature"></a>Nespravované podpis  
  
```  
HRESULT New([in] SAFEARRAY( long ) ar);   
HRESULT New([in] SAFEARRAY( BSTR ) ar);  
```  
  
 Pořadí bezpečné pole je vždy 1 a dolní hranice je vždy 0. Velikost je určena v době běhu velikostí spravované pole předávány.  
  
 Pole můžete také zařazeno jako pole ve stylu jazyka C pomocí <xref:System.Runtime.InteropServices.MarshalAsAttribute> atribut. Příklad:  
  
#### <a name="managed-signature"></a>Spravované podpis  
  
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
  
#### <a name="unmanaged-signature"></a>Nespravované podpis  
  
```  
HRESULT New(long ar[]);   
HRESULT New(BSTR ar[]);   
HRESULT New(LPStr ar[]);  
```  
  
 I když zařazování má délku informace potřebné pro zařazování pole, délka pole je obvykle předat jako samostatné argument pro vyjádření délka volaného.  
  
### <a name="elementtypearray"></a>ELEMENT_TYPE_ARRAY  
 Když metoda obsahuje **ELEMENT_TYPE_ARRAY** parametr exportují z sestavení .NET do knihovny typů, parametr pole jsou převedeny na **SAFEARRAY** daného typu. Obsah bude spravované pole se automaticky zkopírují ze spravované paměti do **SAFEARRAY**. Příklad:  
  
#### <a name="managed-signature"></a>Spravované podpis  
  
```vb  
Sub [New](ar(,) As Long)  
Sub [New](ar(,) As String)  
```  
  
```csharp  
void New( long [,] ar );  
void New( String [,] ar );  
```  
  
#### <a name="unmanaged-signature"></a>Nespravované podpis  
  
```  
HRESULT New([in] SAFEARRAY( long ) ar);   
HRESULT New([in] SAFEARRAY( BSTR ) ar);  
```  
  
 Pořadí, velikost a rozsah bezpečné polí jsou určena v době běhu charakteristikami spravované pole.  
  
 Pole můžete také zařazeno jako pole ve stylu jazyka C s použitím <xref:System.Runtime.InteropServices.MarshalAsAttribute> atribut. Příklad:  
  
#### <a name="managed-signature"></a>Spravované podpis  
  
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
  
#### <a name="unmanaged-signature"></a>Nespravované podpis  
  
```  
HRESULT New(long ar[]);   
HRESULT New(LPStr ar[]);  
```  
  
 Vnořená pole nelze zařadit. Například následující podpis, vygeneruje se chyba při exportu se [Exportér knihovny typů (Tlbexp.exe)](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md).  
  
#### <a name="managed-signature"></a>Spravované podpis  
  
```vb  
Sub [New](ar()()() As Long)  
```  
  
```csharp  
void New(long [][][] ar );  
```  
  
### <a name="elementtypeclass-systemarray"></a>ELEMENT_TYPE_CLASS \<System.Array >  
 Když metoda obsahuje <xref:System.Array?displayProperty=nameWithType> parametr exportují z sestavení .NET do knihovny typů, parametr pole jsou převedeny na **_Array** rozhraní. Obsah bude spravované pole je přístupné pouze prostřednictvím metody a vlastnosti **_Array** rozhraní. **System.Array** můžete také zařazené jako **SAFEARRAY** pomocí <xref:System.Runtime.InteropServices.MarshalAsAttribute> atribut. Když zařazené jako bezpečné pole, elementy pole jsou zařazené jako varianty. Příklad:  
  
#### <a name="managed-signature"></a>Spravované podpis  
  
```vb  
Sub New1( ar As System.Array )  
Sub New2( <MarshalAs(UnmanagedType.Safe array)> ar As System.Array )  
```  
  
```csharp  
void New1( System.Array ar );  
void New2( [MarshalAs(UnmanagedType.Safe array)] System.Array ar );  
```  
  
#### <a name="unmanaged-signature"></a>Nespravované podpis  
  
```  
HRESULT New([in] _Array *ar);   
HRESULT New([in] SAFEARRAY(VARIANT) ar);  
```  
  
### <a name="arrays-within-structures"></a>Pole v rámci struktury  
 Nespravované struktury může obsahovat vložené pole. Ve výchozím nastavení tato vložená pole jsou zařazené jako SAFEARRAY. V následujícím příkladu `s1` je vložená pole, které je přidělen přímo v rámci struktury sám sebe.  
  
#### <a name="unmanaged-representation"></a>Nespravované reprezentace  
  
```  
struct MyStruct {  
    short s1[128];  
}  
```  
  
 Pole můžou být zařazené jako <xref:System.Runtime.InteropServices.UnmanagedType>, který vyžaduje, abyste nastavili <xref:System.Runtime.InteropServices.MarshalAsAttribute> pole. Velikost lze nastavit pouze jako konstanta. Následující kód ukazuje odpovídající spravované definice `MyStruct`.  
  
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
 [Výchozí chování zařazování](../../../docs/framework/interop/default-marshaling-behavior.md)  
 [Přenositelné a nepřenositelné typy](../../../docs/framework/interop/blittable-and-non-blittable-types.md)  
 [Směrovou atributy](http://msdn.microsoft.com/library/241ac5b5-928e-4969-8f58-1dbc048f9ea2)  
 [Kopírování a přichycování](../../../docs/framework/interop/copying-and-pinning.md)
