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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e3eb5c9686f54bcaacef8d593f0ace4804d4ae60
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59098218"
---
# <a name="default-marshaling-for-arrays"></a>Výchozí zařazování pro pole
V případě aplikace tvořené zcela spravovaný kód modul common language runtime předá typy polí jako vstup a výstup parametry. Naproti tomu interoperační zařazovač předá pole jako parametry in ve výchozím nastavení.  
  
 S [Připnutí optimalizace](copying-and-pinning.md), pole typu blittable můžou zdánlivě pracovat jako vstupně -výstupní parametr při práci s objekty ve stejném objektu apartment. Ale pokud později exportovat do knihovny typů sloužící ke generování mezi počítači proxy kód a tuto knihovnu je použitý k zařazování volání napříč objekty apartment, volání můžete vrátit na hodnotu true parametru chování.  
  
 Pole jsou komplexní podle povahy a rozdíly mezi spravovanými a nespravovanými pole vyžadují více informace než jiné nepřenositelné typy.  
  
## <a name="managed-arrays"></a>Spravovaná pole  
 Spravované pole, které mohou být různé typy; ale <xref:System.Array?displayProperty=nameWithType> třída je základní třídou všechny typy polí. **System.Array** třída obsahuje vlastnosti pro určení pořadí, délku a dolní a horní hranice pole, jakož i metody pro přístup k řazení, hledání, kopírování a tvorba polí.  
  
 Tyto typy polí jsou dynamické vzorce a nemají odpovídající statický typ definovaný v knihovně základních tříd. Je možné mluvit o každou kombinaci typ elementu a řazení jako odlišný typ pole. Jednorozměrné pole celých čísel je proto jiného typu než jednorozměrné pole typu double. Podobně dvourozměrné pole celých čísel se liší od jednorozměrné pole celých čísel. Při porovnávání typů, nejsou považovány za hranice pole.  
  
 V následující tabulce jsou uvedeny, všechny instance spravovaného pole musí být konkrétní elementu typu, pořadí a dolní mez.  
  
|Spravovaná pole|Typ elementu|pořadí|Dolní mez|Zápis podpis|  
|------------------------|------------------|----------|-----------------|------------------------|  
|**ELEMENT_TYPE_ARRAY**|Určený typem.|Určené pořadí.|Volitelně můžete zadat pomocí hranice.|*typ* **[** *n*,*m* **]**|  
|**ELEMENT_TYPE_CLASS**|Neznámé|Neznámé|Neznámé|**System.Array** |  
|**ELEMENT_TYPE_SZARRAY**|Určený typem.|1|0|*typ* **[** *n* **]**|  
  
## <a name="unmanaged-arrays"></a>Nespravované pole  
 Nespravované pole jsou bezpečné pole stylu modelu COM nebo pole stylu C s pevným nebo variabilním délkou. Zabezpečeným polím popisující samy sebe, pole, která mají typ, pořadí a rozsah dat přidružené pole. Pole stylu jazyka C jsou jednorozměrné typovaná pole s pevnou dolní mez 0. Zařazovací služby má omezenou podporu pro oba typy polí.  
  
## <a name="passing-array-parameters-to-net-code"></a>Předávání parametrů pole pro kód .NET  
 Pole stylu C a zabezpečeným polím lze předat kód .NET z nespravovaného kódu jako bezpečné pole nebo pole stylu C. Následující tabulka uvádí hodnotu nespravovaný typ a importovaným typem.  
  
|Nespravovaný typ|Importovaný typ.|  
|--------------------|-------------------|  
|**SafeArray (** *typ* **)**|**ELEMENT_TYPE_SZARRAY** **\<** *ConvertedType* **>**<br /><br /> Pořadí = 1, dolní mez = 0. Velikosti je znám pouze v případě, že součástí spravovaný podpis. Zabezpečeným polím, které nejsou pořadí = 1 nebo dolní mez = 0 nelze zařadit jako **SZARRAY**.|  
|*Typ* **]** |**ELEMENT_TYPE_SZARRAY** **\<** *ConvertedType* **>**<br /><br /> Pořadí = 1, dolní mez = 0. Velikosti je znám pouze v případě, že součástí spravovaný podpis.|  
  
### <a name="safe-arrays"></a>Zabezpečeným polím  
 Když bezpečné pole je importována z knihovny typů na sestavení .NET, pole, je převedena na jednorozměrné pole známý typ (například **int**). Stejné pravidel převodu typů, které se vztahují na parametry platí také pro prvky pole. Například bezpečné pole z **BSTR** typy stane spravovaného pole řetězců a bezpečné pole variant stane spravovaného pole objektů. **SAFEARRAY** typ prvku je zachycená z knihovny typů a uložili v **SAFEARRAY** hodnotu <xref:System.Runtime.InteropServices.UnmanagedType> výčtu.  
  
 Vzhledem k tomu, že z knihovny typů nelze určit počet rozměrů a hranice bezpečné pole, počet rozměrů předpokládá, že je rovno 1 a dolní mez předpokládá, že je rovna 0. Počet rozměrů a hranice musí být definován v spravovaný podpis vytvářených [Importér knihovny typů (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md). Pokud se počet rozměrů předaný metodě v době běhu liší, <xref:System.Runtime.InteropServices.SafeArrayRankMismatchException> je vyvolána výjimka. Pokud je předán typ pole za běhu liší, <xref:System.Runtime.InteropServices.SafeArrayTypeMismatchException> je vyvolána výjimka. Následující příklad ukazuje zabezpečeným polím v spravovaným a nespravovaným kódem.  
  
 **Nespravovanému podpisu**  
  
```  
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
  
 Multidimenzionální nebo nenulovou vázané zabezpečeným polím, může být zařazována do spravovaného kódu, pokud se změní podpis metody vytvářených Tlbimp.exe označující typ elementu **ELEMENT_TYPE_ARRAY** místo **ELEMENT_ TYPE_SZARRAY**. Alternativně můžete použít **/sysarray** přepnout pomocí Tlbimp.exe importujte všechna pole jako <xref:System.Array?displayProperty=nameWithType> objekty. V případech, kde je znám jako multidimenzionální pole předávaný můžete upravit Microsoft kód intermediate language (MSIL) vytvořený pomocí Tlbimp.exe a pak ji znovu zkompilovat. Podrobnosti o tom, jak upravovat kód jazyka MSIL, najdete v článku [přizpůsobení obálek Volatelných za běhu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100)).  
  
### <a name="c-style-arrays"></a>Pole stylu C  
 Když pole stylu C je importována z knihovny typů na sestavení .NET, pole, je převedena na **ELEMENT_TYPE_SZARRAY**.  
  
 Typ prvku pole je určen z knihovny typů a zachovají během importu. Stejná pravidla převodu, které se vztahují na parametry platí také pro prvky pole. Například pole **LPStr** typy stává polem o **řetězec** typy. Tlbimp.exe zaznamená typ elementu pole a vztahuje <xref:System.Runtime.InteropServices.MarshalAsAttribute> atribut parametru.  
  
 Rozměr pole je považován za rovnat 1. Pokud pořadí je větší než 1, pole se zařadit jako jednorozměrné pole v pořadí preferujícím sloupce. Dolní mez se vždy rovná 0.  
  
 Knihovny typů mohou obsahovat pole s pevným nebo variabilním délku. Tlbimp.exe můžete importovat pouze pevné délky pole z knihovny typů, protože knihovny typů chybí informace potřebné k zařazení pole proměnné délky. S pevnou délkou pole, velikost naimportované z knihovny typů a zaznamenány **MarshalAsAttribute** , která je použita na parametr.  
  
 Knihovnu typů obsahující pole proměnné délky, je nutné definovat ručně, jak je znázorněno v následujícím příkladu.  
  
 **Nespravovanému podpisu**  
  
```  
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
  
 I když můžete použít **size_is** nebo **length_is –** atributy pole ve zdroji rozhraní Definition Language (IDL) k předání velikosti klientovi definice jazyka MIDL (Microsoft Interface) Kompilátor nešíří tyto informace do knihovny typů. Nainstalovat bez mého velikosti, nelze zařadit zprostředkovatele komunikace s objekty zařazování služby prvků pole. Pole proměnné délky v důsledku toho jsou naimportované jako argumenty odkazu. Příklad:  
  
 **Nespravovanému podpisu**  
  
```  
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
  
 Aby zařazování odvozovalo můžete poskytnout velikost pole úpravou Microsoft kód intermediate language (MSIL) vytvořený pomocí Tlbimp.exe a poté opětovné kompilace. Podrobnosti o tom, jak upravovat kód jazyka MSIL, najdete v článku [přizpůsobení obálek Volatelných za běhu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100)). Chcete-li určit počet prvků v poli, použijte <xref:System.Runtime.InteropServices.MarshalAsAttribute> typ pro parametr pole definici spravované metody v jednom z následujících způsobů:  
  
-   Určete další parametr, který obsahuje počet prvků v poli. Parametry jsou označeny pozici, počínaje první parametr jako číslo 0.     
  
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
  
-   Definujte velikost pole jako konstanta. Příklad:  
  
    ```vb  
    Sub [New](\<MarshalAs(UnmanagedType.LPArray, SizeConst:=128)> _  
       ar() As Integer)  
    ```  
  
    ```csharp  
    void New(  
       [MarshalAs(UnmanagedType.LPArray, SizeConst=128)] int[] ar );  
    ```  
  
 Při zařazování polí z nespravovaného kódu pro spravovaný kód, aby zařazování odvozovalo kontroluje, **MarshalAsAttribute** spojené s parametrem určit velikost pole. Pokud nezadáte velikost pole, je zařadit pouze jeden element.  
  
> [!NOTE]
>  **MarshalAsAttribute** nemá žádný vliv na zařazování spravované pole na nespravovaný kód. V tomto směru velikost pole je určeno zkoumání. Neexistuje žádný způsob, jak zařadit podmnožinu spravovaného pole.  
  
 Interoperační zařazovač používá **CoTaskMemAlloc** a **CoTaskMemFree** metody přidělení a načítat paměti. Přidělení paměti provedené nespravovaný kód musí taky používat tyto metody.  
  
## <a name="passing-arrays-to-com"></a>Předávání polí do modelu COM  
 Všechny typy spravovaného pole může být předán nespravovanému kódu ze spravovaného kódu. V závislosti na spravovaný typ a atributy použité na jeho pole je přístupná jako bezpečné pole nebo pole stylu C, jak je znázorněno v následující tabulce.  
  
|Spravovaná pole|Exportovat jako|  
|------------------------|-----------------|  
|**ELEMENT_TYPE_SZARRAY** **\<** *typu* **>**|<xref:System.Runtime.InteropServices.UnmanagedType> **. SafeArray (** *typ* **)**<br /><br /> **UnmanagedType.LPArray**<br /><br /> Typ je poskytován v podpisu. Pořadí je vždy 1, dolní mez je vždy 0. Velikost je vždy známý v době běhu.|  
|**ELEMENT_TYPE_ARRAY** **\<** *typ* **>** **\<** *pořadí* **>**[**\<** *hranice* **>**]|**UnmanagedType.SafeArray (** *typ* **)**<br /><br /> **UnmanagedType.LPArray**<br /><br /> Typ, řadit, hranice jsou k dispozici v podpisu. Velikost je vždy známý v době běhu.|  
|**ZA ŘETĚZCEM ELEMENT_TYPE_CLASS** **\<**<xref:System.Array?displayProperty=nameWithType>**>**|**UT_Interface**<br /><br /> **UnmanagedType.SafeArray (** *typ* **)**<br /><br /> Typ, hodnocení, hranice a velikosti jsou vždy známý v době běhu.|  
  
 Existuje omezení v automatizace OLE týkající se pole struktur, které obsahují LPSTR, LPWSTR nebo.  Proto **řetězec** pole mají být zařazena jako **UnmanagedType.BSTR**. V opačném případě bude vyvolána výjimka.  
  
### <a name="elementtypeszarray"></a>ELEMENT_TYPE_SZARRAY  
 Pokud metoda obsahuje **ELEMENT_TYPE_SZARRAY** parametr (jednorozměrné pole) je exportována z .NET sestavení na knihovnu typů, protože parametr pole je převedena na **SAFEARRAY** daného typu. Stejný převod pravidla se vztahují na typy prvků pole. Obsah spravovaného pole se automaticky zkopírují ze spravované paměti do **SAFEARRAY**. Příklad:  
  
#### <a name="managed-signature"></a>Spravovaný podpis  
  
```vb  
Sub [New](ar() As Long)  
Sub [New](ar() As String)  
```  
  
```csharp  
void New(long[] ar );  
void New(String[] ar );  
```  
  
#### <a name="unmanaged-signature"></a>Nespravovanému podpisu  
  
```  
HRESULT New([in] SAFEARRAY( long ) ar);   
HRESULT New([in] SAFEARRAY( BSTR ) ar);  
```  
  
 Řád objektu zabezpečeným polím je vždy 1 a dolní mez je vždy 0. Velikost je určena v době běhu velikostí spravovaného pole předávána.  
  
 Pole můžete také zařadit jako pole stylu jazyka C pomocí <xref:System.Runtime.InteropServices.MarshalAsAttribute> atribut. Příklad:  
  
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
  
#### <a name="unmanaged-signature"></a>Nespravovanému podpisu  
  
```  
HRESULT New(long ar[]);   
HRESULT New(BSTR ar[]);   
HRESULT New(LPStr ar[]);  
```  
  
 I když zařazování má délku informace potřebné k zařazení pole, délka pole je obvykle předán jako samostatné argument k předání délka volaného.  
  
### <a name="elementtypearray"></a>ELEMENT_TYPE_ARRAY  
 Pokud metoda obsahuje **ELEMENT_TYPE_ARRAY** parametr se exportuje z .NET sestavení na knihovnu typů, je parametr pole převedena na **SAFEARRAY** daného typu. Obsah spravovaného pole se automaticky zkopírují ze spravované paměti do **SAFEARRAY**. Příklad:  
  
#### <a name="managed-signature"></a>Spravovaný podpis  
  
```vb  
Sub [New](ar(,) As Long)  
Sub [New](ar(,) As String)  
```  
  
```csharp  
void New( long [,] ar );  
void New( String [,] ar );  
```  
  
#### <a name="unmanaged-signature"></a>Nespravovanému podpisu  
  
```  
HRESULT New([in] SAFEARRAY( long ) ar);   
HRESULT New([in] SAFEARRAY( BSTR ) ar);  
```  
  
 Počet rozměrů, velikost a hranice zabezpečeným polím jsou určeny v době běhu vlastnosti spravovaného pole.  
  
 Pole můžete také zařadit jako pole stylu C použitím <xref:System.Runtime.InteropServices.MarshalAsAttribute> atribut. Příklad:  
  
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
  
#### <a name="unmanaged-signature"></a>Nespravovanému podpisu  
  
```  
HRESULT New(long ar[]);   
HRESULT New(LPStr ar[]);  
```  
  
 Vnořená pole nelze zařadit. Například následující podpis dojde k chybě při exportu s [Exportér knihovny typů (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md).  
  
#### <a name="managed-signature"></a>Spravovaný podpis  
  
```vb  
Sub [New](ar()()() As Long)  
```  
  
```csharp  
void New(long [][][] ar );  
```  
  
### <a name="elementtypeclass-systemarray"></a>Za řetězcem ELEMENT_TYPE_CLASS \<System.Array >  
 Pokud metoda obsahuje <xref:System.Array?displayProperty=nameWithType> parametr se exportuje z .NET sestavení na knihovnu typů, je parametr pole převedena na **_pole** rozhraní. Obsah spravovaného pole jsou přístupné pouze prostřednictvím metody a vlastnosti **_pole** rozhraní. **Objekt System.Array** můžete také zařadit jako **SAFEARRAY** pomocí <xref:System.Runtime.InteropServices.MarshalAsAttribute> atribut. Při zařazení jako bezpečné pole prvků pole, jsou zařazeny jako variant. Příklad:  
  
#### <a name="managed-signature"></a>Spravovaný podpis  
  
```vb  
Sub New1( ar As System.Array )  
Sub New2( <MarshalAs(UnmanagedType.Safe array)> ar As System.Array )  
```  
  
```csharp  
void New1( System.Array ar );  
void New2( [MarshalAs(UnmanagedType.Safe array)] System.Array ar );  
```  
  
#### <a name="unmanaged-signature"></a>Nespravovanému podpisu  
  
```  
HRESULT New([in] _Array *ar);   
HRESULT New([in] SAFEARRAY(VARIANT) ar);  
```  
  
### <a name="arrays-within-structures"></a>Pole v rámci struktury  
 Nespravované struktury mohou obsahovat vloženého pole. Ve výchozím nastavení jsou zařazeny tyto vložené pole jako SAFEARRAY. V následujícím příkladu `s1` je vložené pole, která je přidělena přímo v rámci struktury samotné.  
  
#### <a name="unmanaged-representation"></a>Nespravované reprezentace  
  
```  
struct MyStruct {  
    short s1[128];  
}  
```  
  
 Pole může být zařazována jako <xref:System.Runtime.InteropServices.UnmanagedType>, což vyžaduje, abyste nastavili <xref:System.Runtime.InteropServices.MarshalAsAttribute> pole. Velikost lze nastavit pouze jako konstanta. Následující kód ukazuje příslušné spravované definici `MyStruct`.  
  
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
