---
title: Výchozí zařazování pro objekty
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- objects, interop marshaling
- interop marshaling, objects
ms.assetid: c2ef0284-b061-4e12-b6d3-6a502b9cc558
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1b05d5c72491265b7617950550935e3c719421f3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59076157"
---
# <a name="default-marshaling-for-objects"></a>Výchozí zařazování pro objekty
Parametry a pole typu <xref:System.Object?displayProperty=nameWithType> daly vystavit do nespravovaného kódu jako jeden z následujících typů:  
  
-   Hodnotu typu variant, když je parametr objekt.  
  
-   Rozhraní, když je objekt pole struktury.  
  
 Jenom komunikace s objekty COM podporuje zařazování pro typy objektů. Výchozí chování je zařadit objektů variant modelu COM. Tato pravidla se vztahují pouze na typ **objekt** a se nedá použít u objektů se silným typem, které jsou odvozeny z **objekt** třídy.  
  
## <a name="marshaling-options"></a>Zařazování možnosti  
 V následující tabulce jsou uvedeny možnosti zařazování pro **objekt** datového typu. <xref:System.Runtime.InteropServices.MarshalAsAttribute> Atribut nabízí několik <xref:System.Runtime.InteropServices.UnmanagedType> na objekty zařazování hodnot výčtu.  
  
|Typ výčtu|Popis nespravované formátu|  
|----------------------|-------------------------------------|  
|**UnmanagedType.Struct**<br /><br /> (výchozí nastavení pro parametry)|Hodnotu typu variant modelu COM-style.|  
|**UnmanagedType.Interface**|**IDispatch** rozhraní, pokud je to možné, jinak **IUnknown** rozhraní.|  
|**UnmanagedType.IUnknown**<br /><br /> (výchozí nastavení pro pole)|**IUnknown** rozhraní.|  
|**UnmanagedType.IDispatch**|**IDispatch** rozhraní.|  
  
 Následující příklad ukazuje použití spravovaného rozhraní definice `MarshalObject`.  
  
```vb  
Interface MarshalObject  
   Sub SetVariant(o As Object)  
   Sub SetVariantRef(ByRef o As Object)  
   Function GetVariant() As Object  
  
   Sub SetIDispatch( <MarshalAs(UnmanagedType.IDispatch)> o As Object)  
   Sub SetIDispatchRef(ByRef <MarshalAs(UnmanagedType.IDispatch)> o _  
      As Object)  
   Function GetIDispatch() As <MarshalAs(UnmanagedType.IDispatch)> Object  
   Sub SetIUnknown( <MarshalAs(UnmanagedType.IUnknown)> o As Object)  
   Sub SetIUnknownRef(ByRef <MarshalAs(UnmanagedType.IUnknown)> o _  
      As Object)  
   Function GetIUnknown() As <MarshalAs(UnmanagedType.IUnknown)> Object  
End Interface  
```  
  
```csharp  
interface MarshalObject {  
   void SetVariant(Object o);  
   void SetVariantRef(ref Object o);  
   Object GetVariant();  
  
   void SetIDispatch ([MarshalAs(UnmanagedType.IDispatch)]Object o);  
   void SetIDispatchRef([MarshalAs(UnmanagedType.IDispatch)]ref Object o);  
   [MarshalAs(UnmanagedType.IDispatch)] Object GetIDispatch();  
   void SetIUnknown ([MarshalAs(UnmanagedType.IUnknown)]Object o);  
   void SetIUnknownRef([MarshalAs(UnmanagedType.IUnknown)]ref Object o);  
   [MarshalAs(UnmanagedType.IUnknown)] Object GetIUnknown();  
}  
```  
  
 Následující kód exporty `MarshalObject` rozhraní do knihovny typů.  
  
```  
interface MarshalObject {  
   HRESULT SetVariant([in] VARIANT o);  
   HRESULT SetVariantRef([in,out] VARIANT *o);  
   HRESULT GetVariant([out,retval] VARIANT *o)   
   HRESULT SetIDispatch([in] IDispatch *o);  
   HRESULT SetIDispatchRef([in,out] IDispatch **o);  
   HRESULT GetIDispatch([out,retval] IDispatch **o)   
   HRESULT SetIUnknown([in] IUnknown *o);  
   HRESULT SetIUnknownRef([in,out] IUnknown **o);  
   HRESULT GetIUnknown([out,retval] IUnknown **o)   
}  
```  
  
> [!NOTE]
>  Interoperační zařazovač automaticky uvolní všechny přidělené objektu uvnitř varianty po volání.  
  
 Následující příklad ukazuje typ formátovaná hodnota.  
  
```vb  
Public Structure ObjectHolder  
   Dim o1 As Object  
   <MarshalAs(UnmanagedType.IDispatch)> Public o2 As Object  
End Structure  
```  
  
```csharp  
public struct ObjectHolder {  
   Object o1;  
   [MarshalAs(UnmanagedType.IDispatch)]public Object o2;  
}  
```  
  
 Následující kód exportuje typ formátovaný do knihovny typů.  
  
```  
struct ObjectHolder {  
   VARIANT o1;  
   IDispatch *o2;  
}  
```  
  
## <a name="marshaling-object-to-interface"></a>Zařazování objektu rozhraní  
 Pokud objekt je vystavit rozhraní COM jako rozhraní, toto rozhraní je rozhraní pro spravovaný typ <xref:System.Object> ( **d_ostupné** rozhraní). Toto rozhraní je zadán jako **IDispatch** (<xref:System.Runtime.InteropServices.UnmanagedType>) nebo **IUnknown** (**UnmanagedType.IUnknown**) v výslednou knihovnu typů. Klienti modelu COM může vyvolat dynamicky členy spravovanou třídu nebo všechny členy implementovány z příslušných odvozených tříd prostřednictvím **d_ostupné** rozhraní. Klient může také volat **QueryInterface** získat žádné jiné rozhraní explicitně implementovaných spravovaného typu.  
  
## <a name="marshaling-object-to-variant"></a>Zařazování objektu Variant  
 Při objektu je zařazení na hodnotu typu variant, interní variantního typu se určuje v době běhu na základě následujících pravidel:  
  
-   Pokud odkaz na objekt má hodnotu null (**nic** v jazyce Visual Basic), objekt je zařazeno do variant typu **VT_EMPTY**.  
  
-   Pokud se objekt instance libovolného typu, které jsou uvedeny v následující tabulce, je výsledný typ variant určeno pravidla součástí zařazování a uvedené v tabulce.  
  
-   Můžete implementovat další objekty, které je potřeba explicitně řídit chování zařazování <xref:System.IConvertible> rozhraní. V takovém případě je typ variant určeno kód typu vrácených <xref:System.IConvertible.GetTypeCode%2A?displayProperty=nameWithType> metody. V opačném případě je objekt zařazen jako typ variant typu **VT_UNKNOWN**.  
  
### <a name="marshaling-system-types-to-variant"></a>Zařazování typu Variant typy systémů  
 V následující tabulce jsou uvedeny typy spravovaných objektů a jejich odpovídající typy variant modelu COM. Tyto typy jsou převeden pouze v případě, že podpis volané metody je typu <xref:System.Object?displayProperty=nameWithType>.  
  
|typ objektu|Typ variant modelu COM|  
|-----------------|----------------------|  
|Odkaz na objekt s hodnotou Null (**nic** v jazyce Visual Basic).|**VT_EMPTY**|  
|<xref:System.DBNull?displayProperty=nameWithType>|**VT_NULL**|  
|<xref:System.Runtime.InteropServices.ErrorWrapper?displayProperty=nameWithType>|**VT_ERROR**|  
|<xref:System.Reflection.Missing?displayProperty=nameWithType>|**VT_ERROR** s **E_PARAMNOTFOUND**|  
|<xref:System.Runtime.InteropServices.DispatchWrapper?displayProperty=nameWithType>|**VT_DISPATCH**|  
|<xref:System.Runtime.InteropServices.UnknownWrapper?displayProperty=nameWithType>|**VT_UNKNOWN**|  
|<xref:System.Runtime.InteropServices.CurrencyWrapper?displayProperty=nameWithType>|**VT_CY**|  
|<xref:System.Boolean?displayProperty=nameWithType>|**VT_BOOL**|  
|<xref:System.SByte?displayProperty=nameWithType>|**VT_I1**|  
|<xref:System.Byte?displayProperty=nameWithType>|**VT_UI1**|  
|<xref:System.Int16?displayProperty=nameWithType>|**VT_I2**|  
|<xref:System.UInt16?displayProperty=nameWithType>|**VT_UI2**|  
|<xref:System.Int32?displayProperty=nameWithType>|**VT_I4**|  
|<xref:System.UInt32?displayProperty=nameWithType>|**VT_UI4**|  
|<xref:System.Int64?displayProperty=nameWithType>|**VT_I8**|  
|<xref:System.UInt64?displayProperty=nameWithType>|**VT_UI8**|  
|<xref:System.Single?displayProperty=nameWithType>|**VT_R4**|  
|<xref:System.Double?displayProperty=nameWithType>|**VT_R8**|  
|<xref:System.Decimal?displayProperty=nameWithType>|**VT_DECIMAL**|  
|<xref:System.DateTime?displayProperty=nameWithType>|**VT_DATE**|  
|<xref:System.String?displayProperty=nameWithType>|**VT_BSTR**|  
|<xref:System.IntPtr?displayProperty=nameWithType>|**VT_INT**|  
|<xref:System.UIntPtr?displayProperty=nameWithType>|**VT_UINT**|  
|<xref:System.Array?displayProperty=nameWithType>|**VT_ARRAY**|  
  
 Použití `MarshalObject` rozhraní definované v předchozím příkladu následující příklad kódu ukazuje, jak předat různé typy Variant modelu COM serveru.  
  
```vb  
Dim mo As New MarshalObject()  
mo.SetVariant(Nothing)         ' Marshal as variant of type VT_EMPTY.  
mo.SetVariant(System.DBNull.Value) ' Marshal as variant of type VT_NULL.  
mo.SetVariant(CInt(27))        ' Marshal as variant of type VT_I2.  
mo.SetVariant(CLng(27))        ' Marshal as variant of type VT_I4.  
mo.SetVariant(CSng(27.0))      ' Marshal as variant of type VT_R4.  
mo.SetVariant(CDbl(27.0))      ' Marshal as variant of type VT_R8.  
```  
  
```csharp  
MarshalObject mo = new MarshalObject();  
mo.SetVariant(null);            // Marshal as variant of type VT_EMPTY.  
mo.SetVariant(System.DBNull.Value); // Marshal as variant of type VT_NULL.  
mo.SetVariant((int)27);          // Marshal as variant of type VT_I2.  
mo.SetVariant((long)27);          // Marshal as variant of type VT_I4.  
mo.SetVariant((single)27.0);   // Marshal as variant of type VT_R4.  
mo.SetVariant((double)27.0);   // Marshal as variant of type VT_R8.  
```  
  
 Typy modelu COM, které nemají odpovídající spravovaných typů může být zařazována pomocí obálkové třídy, například <xref:System.Runtime.InteropServices.ErrorWrapper>, <xref:System.Runtime.InteropServices.DispatchWrapper>, <xref:System.Runtime.InteropServices.UnknownWrapper>, a <xref:System.Runtime.InteropServices.CurrencyWrapper>. Následující příklad kódu ukazuje, jak používat tyto obálky pro předávání různých typů variant modelu COM serveru.  
  
```vb  
Imports System.Runtime.InteropServices  
' Pass inew as a variant of type VT_UNKNOWN interface.  
mo.SetVariant(New UnknownWrapper(inew))  
' Pass inew as a variant of type VT_DISPATCH interface.  
mo.SetVariant(New DispatchWrapper(inew))  
' Pass a value as a variant of type VT_ERROR interface.  
mo.SetVariant(New ErrorWrapper(&H80054002))  
' Pass a value as a variant of type VT_CURRENCY interface.  
mo.SetVariant(New CurrencyWrapper(New Decimal(5.25)))  
```  
  
```csharp  
using System.Runtime.InteropServices;  
// Pass inew as a variant of type VT_UNKNOWN interface.  
mo.SetVariant(new UnknownWrapper(inew));  
// Pass inew as a variant of type VT_DISPATCH interface.  
mo.SetVariant(new DispatchWrapper(inew));  
// Pass a value as a variant of type VT_ERROR interface.  
mo.SetVariant(new ErrorWrapper(0x80054002));  
// Pass a value as a variant of type VT_CURRENCY interface.  
mo.SetVariant(new CurrencyWrapper(new Decimal(5.25)));  
```  
  
 Obálkové třídy jsou definovány v <xref:System.Runtime.InteropServices> oboru názvů.  
  
### <a name="marshaling-the-iconvertible-interface-to-variant"></a>Zařazování rozhraní IConvertible Variant  
 Typy jiné než uvedené v předchozí části můžete řídit, jak jsou zařazeny implementací <xref:System.IConvertible> rozhraní. Pokud objekt implementuje **IConvertible** rozhraní, typ variant modelu COM je stanovena v době běhu hodnotou <xref:System.TypeCode> vrácená z výčtu <xref:System.IConvertible.GetTypeCode%2A?displayProperty=nameWithType> metoda.  
  
 V následující tabulce jsou uvedeny možné hodnoty pro **TypeCode** výčet a odpovídající typ variant modelu COM pro každou hodnotu.  
  
|TypeCode|Typ variant modelu COM|  
|--------------|----------------------|  
|**TypeCode.Empty**|**VT_EMPTY**|  
|**TypeCode.Object**|**VT_UNKNOWN**|  
|**TypeCode.DBNull**|**VT_NULL**|  
|**TypeCode.Boolean**|**VT_BOOL**|  
|**TypeCode.Char**|**VT_UI2**|  
|**TypeCode.Sbyte**|**VT_I1**|  
|**TypeCode.Byte**|**VT_UI1**|  
|**TypeCode.Int16**|**VT_I2**|  
|**TypeCode.UInt16**|**VT_UI2**|  
|**TypeCode.Int32**|**VT_I4**|  
|**TypeCode.UInt32**|**VT_UI4**|  
|**TypeCode.Int64**|**VT_I8**|  
|**TypeCode.UInt64**|**VT_UI8**|  
|**TypeCode.Single**|**VT_R4**|  
|**TypeCode.Double**|**VT_R8**|  
|**TypeCode.Decimal**|**VT_DECIMAL**|  
|**TypeCode.DateTime**|**VT_DATE**|  
|**TypeCode.String**|**VT_BSTR**|  
|Není podporováno.|**VT_INT**|  
|Není podporováno.|**VT_UINT**|  
|Není podporováno.|**VT_ARRAY**|  
|Není podporováno.|**VT_RECORD**|  
|Není podporováno.|**VT_CY**|  
|Není podporováno.|**VT_VARIANT**|  
  
 Hodnota variant modelu COM je určena voláním **IConvertible.To** *typ* rozhraní, ve kterém **k** *typ* je převod rutiny, která odpovídá typu, který byl vrácen z **IConvertible.GetTypeCode**. Například objekt, který vrátí **TypeCode.Double** z **IConvertible.GetTypeCode** zařazena jako hodnotu typu variant modelu COM typu **VT_R8**. Můžete získat hodnotu objektu variant (uložené v **dblVal** pole z variant modelu COM) pomocí přetypování na **IConvertible** rozhraní a volání <xref:System.IConvertible.ToDouble%2A> metoda.  
  
## <a name="marshaling-variant-to-object"></a>Zařazování typu Variant pro objekt  
 Při zařazování typu variant pro objekt, typ a někdy hodnota zařazené varianty Určuje typ objektu vytvořený. V následující tabulce jsou uvedeny každý typ variant a odpovídající typ objektu, který vytváří zařazování při hodnotu typu variant je předán z modelu COM pro rozhraní .NET Framework.  
  
|Typ variant modelu COM|typ objektu|  
|----------------------|-----------------|  
|**VT_EMPTY**|Odkaz na objekt s hodnotou Null (**nic** v jazyce Visual Basic).|  
|**VT_NULL**|<xref:System.DBNull?displayProperty=nameWithType>|  
|**VT_DISPATCH**|**System.__ComObject** nebo hodnota null, pokud (pdispVal == null)|  
|**VT_UNKNOWN**|**System.__ComObject** nebo hodnota null, pokud (punkVal == null)|  
|**VT_ERROR**|<xref:System.UInt32?displayProperty=nameWithType>|  
|**VT_BOOL**|<xref:System.Boolean?displayProperty=nameWithType>|  
|**VT_I1**|<xref:System.SByte?displayProperty=nameWithType>|  
|**VT_UI1**|<xref:System.Byte?displayProperty=nameWithType>|  
|**VT_I2**|<xref:System.Int16?displayProperty=nameWithType>|  
|**VT_UI2**|<xref:System.UInt16?displayProperty=nameWithType>|  
|**VT_I4**|<xref:System.Int32?displayProperty=nameWithType>|  
|**VT_UI4**|<xref:System.UInt32?displayProperty=nameWithType>|  
|**VT_I8**|<xref:System.Int64?displayProperty=nameWithType>|  
|**VT_UI8**|<xref:System.UInt64?displayProperty=nameWithType>|  
|**VT_R4**|<xref:System.Single?displayProperty=nameWithType>|  
|**VT_R8**|<xref:System.Double?displayProperty=nameWithType>|  
|**VT_DECIMAL**|<xref:System.Decimal?displayProperty=nameWithType>|  
|**VT_DATE**|<xref:System.DateTime?displayProperty=nameWithType>|  
|**VT_BSTR**|<xref:System.String?displayProperty=nameWithType>|  
|**VT_INT**|<xref:System.Int32?displayProperty=nameWithType>|  
|**VT_UINT**|<xref:System.UInt32?displayProperty=nameWithType>|  
|**VT_ARRAY** &#124; **VT_**\*|<xref:System.Array?displayProperty=nameWithType>|  
|**VT_CY**|<xref:System.Decimal?displayProperty=nameWithType>|  
|**VT_RECORD**|Odpovídající zabalený typ hodnoty.|  
|**VT_VARIANT**|Není podporováno.|  
  
 Variantních typů předávaného z modelu COM pro spravovaný kód a pak zpátky do modelu COM nemusí uchovávat stejný typ variant po dobu trvání volání. Zvažte, co se stane, když variant typu **VT_DISPATCH** je předán z modelu COM pro rozhraní .NET Framework. Při zařazování, varianty převést na <xref:System.Object?displayProperty=nameWithType>. Pokud **objekt** je pak předán zpět do modelu COM, je zařazené zpět na hodnotu typu variant typu **VT_UNKNOWN**. Není zaručeno, že typ variant vytvořen, pokud objekt je zařazení ze spravovaného kódu na COM bude stejného typu jako typ variant původně použitý k vytvoření objektu.  
  
## <a name="marshaling-byref-variants"></a>Zařazování varianty ByRef  
 I když varianty sami mohou být předány podle hodnoty nebo podle odkazu, **VT_BYREF** příznak můžete také použít s žádným typem variant k označení, že se obsah objektu variant předávají odkazem místo podle hodnoty. Rozdíl mezi zařazování varianty podle odkazu a zařazování variantpro s **VT_BYREF** nastaven příznak může být matoucí. Na následujícím obrázku vysvětluje rozdíly:  
  
 ![Diagram zobrazující průběh variant předány do zásobníku.](./media/default-marshaling-for-objects/interop-variant-passed-value-reference.gif)  
Varianty předán podle hodnoty a podle reference  
  
 **Výchozí chování zařazování objektů a proměnných typu Variant podle hodnoty**  
  
-   Při předávání objektů modelu COM ze spravovaného kódu, obsah objektu se zkopíruje do novou variantu vytvořili zařazováním použitím z pravidel definovaných v [zařazování objektu Variant](#marshaling-object-to-variant). Změny provedené v variant v nespravované oblasti nejsou šířeny zpět do původního objektu při návratu z volání.  
  
-   Při předání proměnných typu Variant z modelu COM pro spravovaný kód, obsah objektu variant zkopírují do nově vytvořeného objektu pomocí pravidel definovaných v [zařazování typu Variant pro objekt](#marshaling-variant-to-object). Změny provedené v objektu na spravované straně nejsou šířeny zpět do původní typ variant při návratu z volání.  
  
 **Výchozí chování zařazování objektů a proměnných typu Variant odkazem.**  
  
 Šíření změny zpět do volajícího, musí být parametry předány podle odkazu. Například můžete použít **ref** – klíčové slovo v C# (nebo **ByRef** v jazyce Visual Basic spravovaného kódu) pro předání parametrů podle odkazu. V modelu COM, odkaz parametry se jí předávají pomocí ukazatele, jako třeba **variant \***.  
  
-   Při předávání objektů modelu COM pomocí odkazu, aby zařazování odvozovalo vytvoří novou variantu a zkopíruje obsah odkaz na objekt do varianty předtím, než se provádí volání. Varianty je předán nespravované funkci, kde uživatel je zdarma pro změnu obsahu objektu variant. Při návratu z volání všechny změny provedené v nespravované oblasti varianty jsou šířeny zpět na původní objekt. Pokud se typ objektu variant liší od typu variant předává do volání, změny jsou šířeny zpět do objektu jiného typu. To znamená typ objektu předaný do volání se může lišit od typu objektu vrácená z volání.  
  
-   Při předávání hodnotu typu variant na spravovaný kód podle odkazu, aby zařazování odvozovalo vytvoří nový objekt a zkopíruje obsah objektu variant do objektu před uskutečněním hovoru. Odkaz na objekt je předán spravované funkce, kde uživatel je zdarma, chcete-li změnit objekt. Při návratu z volání jsou všechny změny provedené odkazovaný objekt šířeny zpět do původní typ variant. Pokud typ objektu se liší od typu objektu předaného do volání, změnit typ původní typ variant a hodnota se šíří zpět do variantu. Znovu typ objektu variant předaná do volání se může lišit od typu hodnota variant vrácená z volání.  
  
 **Výchozí chování zařazování variantpro s příznakem VT_BYREF**  
  
-   Může mít hodnotu typu variant předávaný spravovaný kód podle hodnoty **VT_BYREF** nastaven příznak označující, že varianty obsahuje odkaz na místo hodnoty. V takovém případě je varianty stále zařazeno do objektu vzhledem k tomu, že varianta je předáván podle hodnoty. Zařazování automaticky přístupů přes ukazatel, obsah objektu variant a zkopíruje se do nově vytvořeného objektu před uskutečněním hovoru. Objekt je pak předán do spravované funkci. Při návratu z volání však není objekt šířeny zpět do původní typ variant. Změny provedené na spravovaný objekt se ztratí.  
  
    > [!CAUTION]
    >  Neexistuje žádný způsob, jak změnit hodnotu typu variant předán podle hodnoty, i v případě varianty **VT_BYREF** nastaven příznak.  
  
-   Hodnotu typu variant předávaný odkazem na spravovaný kód může mít také **VT_BYREF** nastaven příznak označující, že varianty obsahuje odkaz na jiný. Pokud ano, varianty je zařazeno do **ref** objektu, protože varianty je předáván odkazem. Zařazování automaticky přístupů přes ukazatel, obsah objektu variant a zkopíruje se do nově vytvořeného objektu před uskutečněním hovoru. Při návratu z volání hodnotu objektu se šíří zpět k odkazu v rámci původní typ variant pouze v případě, že objekt je stejného typu jako objekt předaný v. To znamená, šíření nezmění typu variant s **VT_BYREF** nastaven příznak. Pokud se změní typ objektu v průběhu hovoru, <xref:System.InvalidCastException> dojde k návratu z volání.  
  
 Následující tabulka shrnuje pravidla pro šíření variant a objektů.  
  
|From|Chcete-li|Změny šířeny zpět|  
|----------|--------|-----------------------------|  
|**Varianty***v*|**Objekt***o*|Nikdy|  
|**Objekt***o*|**Varianty***v*|Nikdy|  
|**Varianty*****\*****pv*|**Objekt REF***o*|Vždy|  
|**Objekt REF***o*|**Varianty*****\*****pv*|Vždy|  
|**Varianty***v* **(VT_BYREF** *&#124;* **typ VT_\*)** |**Objekt***o*|Nikdy|  
|**Varianty***v* **(VT_BYREF** *&#124;* **typ VT_)** |**Objekt REF***o*|Pouze v případě, že nedošlo ke změně typu.|  
  
## <a name="see-also"></a>Viz také:

- [Výchozí chování zařazování](default-marshaling-behavior.md)
- [Přenositelné a nepřenositelné typy](blittable-and-non-blittable-types.md)
- [Směrové atributy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))
- [Kopírování a přichycování](copying-and-pinning.md)
