---
title: "Výchozí zařazování pro objekty"
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
- objects, interop marshaling
- interop marshaling, objects
ms.assetid: c2ef0284-b061-4e12-b6d3-6a502b9cc558
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b49575bb7f16b942a56a48e9ad3f5a44edfb373a
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="default-marshaling-for-objects"></a>Výchozí zařazování pro objekty
Parametry a pole zadán jako <xref:System.Object?displayProperty=nameWithType> mohou být zpřístupněny nespravovaného kódu jako jeden z následujících typů:  
  
-   Hodnotu typu variant, pokud je objekt parametr.  
  
-   Rozhraní, pokud je objekt struktura pole.  
  
 Pouze spoluprací COM podporuje zařazování pro typy objektů. Výchozí chování je zařazování objektů COM variant. Tato pravidla platí pouze pro typ **objekt** a nevztahují se na silného typu objekty, které jsou odvozeny od **objekt** třídy.  
  
 Toto téma obsahuje následující doplňkové informace o zařazování typy objektů:  
  
-   [Zařazování možnosti](#cpcondefaultmarshalingforobjectsanchor7)  
  
-   [Zařazování objekt rozhraní](#cpcondefaultmarshalingforobjectsanchor2)  
  
-   [Export objektu na Variant](#cpcondefaultmarshalingforobjectsanchor3)  
  
-   [Zařazování Variant objektu](#cpcondefaultmarshalingforobjectsanchor4)  
  
-   [Zařazování ByRef variant](#cpcondefaultmarshalingforobjectsanchor6)  
  
<a name="cpcondefaultmarshalingforobjectsanchor7"></a>   
## <a name="marshaling-options"></a>Zařazování možnosti  
 Následující tabulka uvádí možnosti zařazování **objekt** datového typu. <xref:System.Runtime.InteropServices.MarshalAsAttribute> Atribut nabízí několik <xref:System.Runtime.InteropServices.UnmanagedType> hodnoty výčtu k zařazení objekty.  
  
|Typ výčtu|Popis nespravované formátu|  
|----------------------|-------------------------------------|  
|**UnmanagedType.Struct**<br /><br /> (výchozí nastavení pro parametry)|Hodnotu typu variant COM stylu.|  
|**UnmanagedType.Interface**|**IDispatch** rozhraní, pokud je to možné; jinak **IUnknown** rozhraní.|  
|**UnmanagedType.IUnknown**<br /><br /> (výchozí nastavení pro pole)|**IUnknown** rozhraní.|  
|**UnmanagedType.IDispatch**|**IDispatch** rozhraní.|  
  
 Následující příklad ukazuje definici spravovaného rozhraní `MarshalObject`.  
  
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
  
 Následující kód exportuje `MarshalObject` rozhraní pro knihovny typů.  
  
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
>  Spolupráce vláken automaticky uvolní všechny přidělené objekt uvnitř varianta po volání.  
  
 Následující příklad ukazuje typ formátovanou hodnotu.  
  
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
  
 Následující kód exportuje formátovaný typ do knihovny typů.  
  
```  
struct ObjectHolder {  
   VARIANT o1;  
   IDispatch *o2;  
}  
```  
  
<a name="cpcondefaultmarshalingforobjectsanchor2"></a>   
## <a name="marshaling-object-to-interface"></a>Zařazování objekt rozhraní  
 Pokud objekt je vystaven objektům modelu COM jako rozhraní, tento rozhraní je třída rozhraní pro spravovaný typ <xref:System.Object> ( **_Object** rozhraní). Toto rozhraní je zadán jako **IDispatch** (<xref:System.Runtime.InteropServices.UnmanagedType>) nebo **IUnknown** (**UnmanagedType.IUnknown**) v knihovně výsledný typ. Klienti COM můžete vyvolat dynamicky členy spravované třídy nebo žádné členy implementované jejich odvozené třídy prostřednictvím **_Object** rozhraní. Klient může také volat **QueryInterface** získat všechny rozhraní, které explicitně implementované spravovaného typu.  
  
<a name="cpcondefaultmarshalingforobjectsanchor3"></a>   
## <a name="marshaling-object-to-variant"></a>Export objektu na Variant  
 Pokud je objekt zařazen do hodnotu typu variant, interní typ varianty se určuje v době běhu na základě následujících pravidel:  
  
-   Pokud objekt odkaz má hodnotu null (**nic** v jazyce Visual Basic), objekt je zařazen do hodnotu typu variant typu **VT_EMPTY**.  
  
-   Pokud se objekt instance libovolného typu uvedené v následující tabulce, výsledný typ varianty je určen podle pravidel integrovaných do zařazování a uvedené v tabulce.  
  
-   Můžete implementovat jiné objekty, které je potřeba explicitně řídit chování zařazování <xref:System.IConvertible> rozhraní. V takovém případě je typ varianty dáno kód typ vrácený <xref:System.IConvertible.GetTypeCode%2A?displayProperty=nameWithType> metoda. Jinak je objekt zařazené jako typ variant typu **VT_UNKNOWN**.  
  
### <a name="marshaling-system-types-to-variant"></a>Zařazování typy systémů Variant  
 V následující tabulce jsou uvedeny typy spravovaných objektů a jejich odpovídající typy variant COM. Tyto typy budou převedené jenom v případě, že podpis metody volané je typu <xref:System.Object?displayProperty=nameWithType>.  
  
|typ objektu|Typ varianty COM|  
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
  
 Pomocí `MarshalObject` rozhraní definované v předchozím příkladu následující příklad kódu ukazuje, jak mají být předány různé typy variant COM server.  
  
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
  
 Typy modelu COM, které nemají odpovídající spravované typy může být zařazeno pomocí Obálka – třídy, jako třeba <xref:System.Runtime.InteropServices.ErrorWrapper>, <xref:System.Runtime.InteropServices.DispatchWrapper>, <xref:System.Runtime.InteropServices.UnknownWrapper>, a <xref:System.Runtime.InteropServices.CurrencyWrapper>. Následující příklad kódu ukazuje, jak používat tyto obálky předat různé typy variant COM server.  
  
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
 Typy jiné než jsou uvedeny v předchozí části můžete řídit, jak jsou zařazené implementací <xref:System.IConvertible> rozhraní. Pokud objekt implementuje **IConvertible** rozhraní, typ varianty COM je určen v době běhu hodnotou <xref:System.TypeCode> výčtu vrácená z <xref:System.IConvertible.GetTypeCode%2A?displayProperty=nameWithType> metoda.  
  
 V následující tabulce jsou uvedeny možné hodnoty **typ objektu TypeCode** výčet a odpovídající typ varianty COM pro každou hodnotu.  
  
|TypeCode|Typ varianty COM|  
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
  
 Hodnotu typu variant COM je dáno volání **IConvertible.To** *typ* rozhraní, kde **k** *typu* je převod rutiny, která odpovídá typu, který byl vrácen ze **IConvertible.GetTypeCode**. Například objekt, který vrátí **TypeCode.Double** z **IConvertible.GetTypeCode** je zařazené jako hodnotu typu variant COM typu **VT_R8**. Můžete získat hodnotu varianta (uložené v **dblVal** pole varianty COM) podle přetypování k **IConvertible** rozhraní a volání <xref:System.IConvertible.ToDouble%2A> metoda.  
  
<a name="cpcondefaultmarshalingforobjectsanchor4"></a>   
## <a name="marshaling-variant-to-object"></a>Zařazování Variant objektu  
 Při zařazování hodnotu typu variant pro objekt, typ a někdy hodnotu zařazené variant Určuje typ objektu vytvořil. V následující tabulce jsou uvedeny každý typ varianty a odpovídající typ objektu, který zařazování vytvoří, když hodnotu typu variant předána z COM rozhraní .NET Framework.  
  
|Typ varianty COM|typ objektu|  
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
|**VT_ARRAY** &#124; **VT_\***|<xref:System.Array?displayProperty=nameWithType>|  
|**VT_CY**|<xref:System.Decimal?displayProperty=nameWithType>|  
|**VT_RECORD**|Odpovídající typ zabalené hodnoty.|  
|**VT_VARIANT**|Není podporováno.|  
  
 Variant typy předat z COM pro spravovaný kód a potom zpět do modelu COM nemusí zachovat stejný typ varianty po dobu trvání volání. Zvažte, co se stane, když hodnotu typu variant typu **VT_DISPATCH** předaný z COM rozhraní .NET Framework. Při zařazování, varianta jsou převedeny na <xref:System.Object?displayProperty=nameWithType>. Pokud **objekt** byl následně předán zpět do modelu COM, je zařazené zpět na hodnotu typu variant typu **VT_UNKNOWN**. Není zaručeno, že bude variant vytváří, když je objekt zařazené ze spravovaného kódu do modelu COM stejného typu jako typ variant původně použitý k vytvoření objektu.  
  
<a name="cpcondefaultmarshalingforobjectsanchor6"></a>   
## <a name="marshaling-byref-variants"></a>Zařazování ByRef variant  
 I když hodnotou nebo odkazem, se dá předat variant sami **VT_BYREF** příznak lze také s žádným typem variant indikující, že obsah varianta jsou předávány odkazem místo podle hodnoty. Rozdíl mezi zařazování variant odkazem a zařazování hodnotu typu variant s **VT_BYREF** nastaven příznak může být matoucí. Na následujícím obrázku vysvětluje rozdíly.  
  
 ![Variant předán v zásobníku](../../../docs/framework/interop/media/interopvariant.gif "interopvariant")  
Variant předán podle hodnoty a podle reference  
  
 **Výchozí chování zařazování objekty a variant podle hodnoty**  
  
-   Při předávání objektů ze spravovaného kódu do modelu COM, obsah objektu se zkopírují do nové varianty vytvořené vláken, pomocí pravidla definovaná v [zařazování objekt typu Variant](#cpcondefaultmarshalingforobjectsanchor3). Změny provedené v typu variant na nespravované straně nebudou rozšířeny zpět na původní objekt pro návrat z volání.  
  
-   Při předávání variant do spravovaného kódu z modelu COM, obsah varianty se zkopíruje na nově vytvořený objekt, pomocí pravidla definovaná v [zařazování Variant objekt](#cpcondefaultmarshalingforobjectsanchor4). Změny provedené v objektu na straně pro spravované nebudou rozšířeny zpět na původní typu variant pro návrat z volání.  
  
 **Výchozí chování zařazování objekty a variant odkazem**  
  
 Rozšíří změny zpět do volající, musí být předán parametry odkazem. Například můžete použít **ref** – klíčové slovo v jazyce C# (nebo **ByRef** v jazyce Visual Basic spravovaný kód) předat parametry odkazem. V modelu COM, odkaz parametry se jí předávají pomocí ukazatele, jako třeba **variant \*** .  
  
-   Při předávání objektu COM odkazem, zařazování vytvoří nové typu variant a zkopíruje obsah odkaz na objekt do varianta než při volání. Varianta předaný funkci nespravované kde je mohou změnit obsah varianta uživatele. Při návratu z volání všechny změny typu variant na nespravované straně rozšířeny zpět na původní objekt. Pokud typ varianty se liší od typu variant předána volání funkce, změny rozšířeny zpět do objektu jiného typu. To znamená typ objektu, který je předán do volání se může lišit od typ objektu vrácená z volání.  
  
-   Při předávání hodnotu typu variant pro spravovaný kód podle reference, zařazování vytvoří nový objekt a zkopíruje obsah varianta do objektu před uskutečněním hovoru. Odkaz na objekt předaný spravovaná funkce, kde je mohou změnit objekt uživatele. Při návratu z volání všechny změny odkazovaného objektu rozšířeny zpět na původní variant. Pokud typ objektu, se liší od typ objektu předané do volání, se změní typ původní typu variant a je hodnota rozšířena zpět do varianta. Znovu typ variant předaný do volání se může lišit od typu variant vrácená z volání.  
  
 **Výchozí chování zařazování hodnotu typu variant nastaven příznak VT_BYREF**  
  
-   Může mít hodnotu typu variant předávány do spravovaného kódu podle hodnoty **VT_BYREF** nastaven příznak indikující, že varianta obsahuje odkaz místo hodnotu. V takovém případě je varianta stále zařazené k objektu, protože varianta je předáván podle hodnoty. Zařazování automaticky dereferences obsah varianta a zkopíruje je do nově vytvořený objekt před uskutečněním hovoru. Objekt je předána do spravované funkce; Při návratu z volání, však není objekt rozšíří zpět do původní variant. Změny spravovaného objektu jsou ztraceny.  
  
    > [!CAUTION]
    >  Neexistuje žádný způsob, jak změnit hodnotu typu variant předaná hodnota, i když má varianta **VT_BYREF** nastaven příznak.  
  
-   Může mít hodnotu typu variant předávány do spravovaného kódu odkazem **VT_BYREF** nastaven příznak indikující, že varianta obsahuje odkaz na jiný. Pokud ano, je varianta zařazen do **ref** objekt, protože varianta je předávána odkazem. Zařazování automaticky dereferences obsah varianta a zkopíruje je do nově vytvořený objekt před uskutečněním hovoru. Při návratu z volání je hodnota objektu rozšířena zpět na odkaz v původní variant pouze v případě, že objekt je stejného typu jako objekt předaný v. To znamená, šíření nezmění typ variant s **VT_BYREF** nastaven příznak. Pokud je během volání změnit typ objektu <xref:System.InvalidCastException> proběhne vrátit z volání.  
  
 Následující tabulka shrnuje pravidla šíření variant a objekty.  
  
|From|Chcete-li|Změny rozšířeny zpět|  
|----------|--------|-----------------------------|  
|**Variant***v* |**Objekt***o* |Nikdy|  
|**Objekt***o* |**Variant***v* |Nikdy|  
|**Variant*****\*****pv* |**REF objekt***o* |Vždy|  
|**REF objekt***o* |**Variant*****\*****pv* |Vždy|  
|**Variant**  *v* **(VT_BYREF** *&#124;* **VT_\*)**|**Objekt***o* |Nikdy|  
|**Variant**  *v* **(VT_BYREF** *&#124;* **VT_)**|**REF objekt***o* |Pouze v případě, že typ nebyl změněn.|  
  
## <a name="see-also"></a>Viz také  
 [Výchozí chování zařazování](../../../docs/framework/interop/default-marshaling-behavior.md)  
 [Přenositelné a nepřenositelné typy](../../../docs/framework/interop/blittable-and-non-blittable-types.md)  
 [Směrovou atributy](http://msdn.microsoft.com/library/241ac5b5-928e-4969-8f58-1dbc048f9ea2)  
 [Kopírování a přichycování](../../../docs/framework/interop/copying-and-pinning.md)
