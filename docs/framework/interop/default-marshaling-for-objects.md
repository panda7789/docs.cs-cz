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
ms.openlocfilehash: b2c6e8a013d6486ec55723b91d6bfb6b838c9be5
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044170"
---
# <a name="default-marshaling-for-objects"></a>Výchozí zařazování pro objekty

Parametry a pole, které <xref:System.Object?displayProperty=nameWithType> jsou zadány jako mohou být zpřístupněny nespravovanému kódu jako jeden z následujících typů:

- Varianta, pokud je objekt parametrem.

- Rozhraní, když je objekt polem struktury.

Zařazování pro typy objektů podporuje pouze zprostředkovatel komunikace s objekty COM. Výchozím chováním je zařazování objektů do variant modelu COM. Tato pravidla se vztahují pouze na **objekt** typu a nevztahují se na objekty silného typu, které jsou odvozeny z třídy **Object** .

## <a name="marshaling-options"></a>Možnosti zařazování

V následující tabulce jsou uvedeny možnosti zařazování pro datový typ **objektu** . Atribut poskytuje několik <xref:System.Runtime.InteropServices.UnmanagedType> hodnot výčtu pro zařazování objektů. <xref:System.Runtime.InteropServices.MarshalAsAttribute>

|Typ výčtu|Popis nespravovaného formátu|
|----------------------|-------------------------------------|
|**UnmanagedType. struct**<br /><br /> (výchozí pro parametry)|Variant ve stylu modelu COM.|
|**UnmanagedType.Interface**|Rozhraní **IDispatch** , pokud je to možné; v opačném případě rozhraní **IUnknown** .|
|**UnmanagedType. IUnknown**<br /><br /> (výchozí pro pole)|Rozhraní **IUnknown** .|
|**UnmanagedType. IDispatch**|Rozhraní **IDispatch** .|

Následující příklad ukazuje definici spravovaného rozhraní pro `MarshalObject`.

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

Následující kód exportuje `MarshalObject` rozhraní do knihovny typů.

```cpp
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
> Zařazovací modul Interop automaticky uvolňuje všechny přidělené objekty v rámci varianty po volání.

Následující příklad ukazuje formátovaný typ hodnoty.

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

```cpp
struct ObjectHolder {
   VARIANT o1;
   IDispatch *o2;
}
```

## <a name="marshaling-object-to-interface"></a>Zařazování objektu na rozhraní

Když je objekt v modelu COM vystaven jako rozhraní, toto rozhraní je rozhraní třídy pro spravovaný typ <xref:System.Object> (rozhraní **_object** ). Toto rozhraní je typu **IDispatch** (<xref:System.Runtime.InteropServices.UnmanagedType>) nebo **IUnknown** (**UnmanagedType. IUnknown**) ve výsledné knihovně typů. Klienti modelu COM mohou dynamicky volat členy spravované třídy nebo všech členů implementovaných svými odvozenými třídami prostřednictvím rozhraní **_object** . Klient může také volat metodu **QueryInterface** , aby získala jakékoli jiné rozhraní explicitně implementované spravovaným typem.

## <a name="marshaling-object-to-variant"></a>Zařazování objektu na typ variant

Při zařazování objektu na variantu je interní typ variant určen za běhu na základě následujících pravidel:

- Pokud odkaz na objekt má hodnotu null (**Nothing** v Visual Basic), objekt je zařazen do varianty typu **VT_EMPTY**.

- Je-li objekt instancí libovolného typu, který je uveden v následující tabulce, je výsledný typ variant určen pravidly integrovanými do zařazovacího modulu a zobrazeným v tabulce.

- Další objekty, které potřebují explicitně řídit chování zařazování, mohou implementovat <xref:System.IConvertible> rozhraní. V takovém případě typ variant je určen kódem typu vráceným z <xref:System.IConvertible.GetTypeCode%2A?displayProperty=nameWithType> metody. V opačném případě je objekt zařazen jako typ variant typu **VT_UNKNOWN**.

### <a name="marshaling-system-types-to-variant"></a>Zařazování typů systému do varianty

V následující tabulce jsou uvedeny typy spravovaných objektů a jejich odpovídající typy variant modelu COM. Tyto typy jsou převedeny pouze v případě, že signatura volané metody je typu <xref:System.Object?displayProperty=nameWithType>.

|typ objektu|Typ variant modelu COM|
|-----------------|----------------------|
|Nulový odkaz na objekt (**Nothing** v Visual Basic)|**VT_EMPTY**|
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

V následujícím příkladu kódu ukazuje, jak předat různé typy variant do serveru com, pomocí rozhranídefinovanéhovpředchozímpříkladu.`MarshalObject`

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

Typy modelu COM, které nemají odpovídající spravované <xref:System.Runtime.InteropServices.ErrorWrapper>typy, lze zařadit pomocí tříd obálky <xref:System.Runtime.InteropServices.UnknownWrapper>, jako jsou <xref:System.Runtime.InteropServices.DispatchWrapper>,, a <xref:System.Runtime.InteropServices.CurrencyWrapper>. Následující příklad kódu ukazuje, jak tyto obálky použít k předávání různých typů variant serveru COM.

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

### <a name="marshaling-the-iconvertible-interface-to-variant"></a>Zařazování rozhraní IConvertible k variantě

Jiné typy než ty, které jsou uvedeny v předchozí části, mohou řídit, jak jsou zařazeny <xref:System.IConvertible> implementací rozhraní. Pokud objekt implementuje rozhraní **IConvertible** , typ variant modelu COM je určen za běhu podle hodnoty <xref:System.TypeCode> <xref:System.IConvertible.GetTypeCode%2A?displayProperty=nameWithType> výčtu vráceného z metody.

V následující tabulce jsou uvedeny možné hodnoty pro výčet **TypeCode** a odpovídající typ variant modelu COM pro každou hodnotu.

|TypeCode|Typ variant modelu COM|
|--------------|----------------------|
|**TypeCode. Empty**|**VT_EMPTY**|
|**TypeCode.Object**|**VT_UNKNOWN**|
|**TypeCode.DBNull**|**VT_NULL**|
|**TypeCode. Boolean**|**VT_BOOL**|
|**TypeCode.Char**|**VT_UI2**|
|**TypeCode. SByte**|**VT_I1**|
|**TypeCode.Byte**|**VT_UI1**|
|**TypeCode.Int16**|**VT_I2**|
|**TypeCode.UInt16**|**VT_UI2**|
|**TypeCode.Int32**|**VT_I4**|
|**TypeCode.UInt32**|**VT_UI4**|
|**TypeCode.Int64**|**VT_I8**|
|**TypeCode.UInt64**|**VT_UI8**|
|**TypeCode. Single**|**VT_R4**|
|**TypeCode. Double**|**VT_R8**|
|**TypeCode.Decimal**|**VT_DECIMAL**|
|**TypeCode.DateTime**|**VT_DATE**|
|**TypeCode. String**|**VT_BSTR**|
|Není podporováno.|**VT_INT**|
|Není podporováno.|**VT_UINT**|
|Není podporováno.|**VT_ARRAY**|
|Není podporováno.|**VT_RECORD**|
|Není podporováno.|**VT_CY**|
|Není podporováno.|**VT_VARIANT**|

Hodnota variant modelu COM je určena voláním rozhraní *typu* **IConvertible.to** , kde **pro** *typ* je rutina převodu, která odpovídá typu, který byl vrácen z **IConvertible. GetTypeCode**. Například objekt, který vrací **TypeCode. Double** z **IConvertible. GetTypeCode** je zařazen jako typ variant modelu COM typu **VT_R8**. Můžete získat hodnotu Variant (uloženou v poli **dblVal** variant modelu COM) přetypováním do rozhraní **IConvertible** <xref:System.IConvertible.ToDouble%2A> a voláním metody.

## <a name="marshaling-variant-to-object"></a>Zařazování variant do objektu

Při zařazování variant do objektu, typ a někdy hodnota pro zařazování variant určuje typ vytvořeného objektu. Následující tabulka určuje každý typ variant a odpovídající typ objektu, který zařazovací modul vytvoří, když je hodnota typu variant předána z modelu COM do .NET Framework.

|Typ variant modelu COM|typ objektu|
|----------------------|-----------------|
|**VT_EMPTY**|Nulový odkaz na objekt (**Nothing** v Visual Basic)|
|**VT_NULL**|<xref:System.DBNull?displayProperty=nameWithType>|
|**VT_DISPATCH**|**System. __ComObject** nebo null if (pdispVal = = null)|
|**VT_UNKNOWN**|**System. __ComObject** nebo null if (punkVal = = null)|
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
|**VT_ARRAY** &#124; **VT_** \*|<xref:System.Array?displayProperty=nameWithType>|
|**VT_CY**|<xref:System.Decimal?displayProperty=nameWithType>|
|**VT_RECORD**|Odpovídající zabalený typ hodnoty.|
|**VT_VARIANT**|Není podporováno.|

Typy variant předané z modelu COM do spravovaného kódu a poté zpět do modelu COM nemusí zachovat stejný typ variant pro dobu trvání volání. Zvažte, co se stane, když je hodnota variant typu **VT_DISPATCH** předána z modelu COM do .NET Framework. V průběhu zařazování je varianta převedena na <xref:System.Object?displayProperty=nameWithType>. Pokud je **objekt** předán zpět do modelu COM, je zařazen zpět na variantu typu **VT_UNKNOWN**. Není nijak zaručeno, že varianta vytvořená při zařazování objektu ze spravovaného kódu do modelu COM bude stejného typu jako původně použitá varianta k vytvoření objektu.

## <a name="marshaling-byref-variants"></a>Zařazování variant typu ByRef

I když samotné varianty mohou být předány hodnotou nebo odkazem, příznak **VT_BYREF** lze také použít s libovolným typem variant k označení toho, že obsah varianty je předáván odkazem namísto hodnoty. Rozdíl mezi zařazováním variant podle odkazu a zařazováním typu variant se sadou příznaků **VT_BYREF** může být matoucí. Rozdíly jsou znázorněny na následujícím obrázku:

![Diagram, který zobrazuje variantu předanou v zásobníku.](./media/default-marshaling-for-objects/interop-variant-passed-value-reference.gif)
Varianty předané hodnotou a odkazem

**Výchozí chování zařazování objektů a variant podle hodnoty**

- Při předávání objektů ze spravovaného kódu do modelu COM je obsah objektu zkopírován do nového objektu variant vytvořeného zařazováním pomocí pravidel definovaných v [zařazování objektu na typ variant](#marshaling-object-to-variant). Změny provedené v variantě na nespravované straně nejsou šířeny zpět do původního objektu při návratu ze volání.

- Při předávání variant z modelu COM do spravovaného kódu je obsah varianty zkopírován do nově vytvořeného objektu pomocí pravidel definovaných v [zařazování variant do objektu](#marshaling-variant-to-object). Změny provedené u objektu na spravované straně nejsou šířeny zpět do původní varianty při návratu ze volání.

**Výchozí chování zařazování objektů a variant podle odkazu**

Chcete-li rozšířit změny zpět volajícímu, musí být parametry předány odkazem. Například můžete použít klíčové slovo **ref** v C# (nebo **ByRef** v Visual Basic spravovaném kódu) k předání parametrů odkazem. V modelu COM, odkaz parametry se jí předávají pomocí ukazatele, jako třeba **variant \*** .

- Při předání objektu modelu COM odkazem vytvoří zařazovací objekt novou variantu a před provedením volání zkopíruje obsah odkazu na objekt do objektu variant. Hodnota variant je předána nespravované funkci, kde uživatel je bezplatný pro změnu obsahu varianty. Při návratu ze volání se všechny změny provedené v variantě nespravované strany rozšíří zpátky na původní objekt. Pokud se typ variant liší od typu variant předaného volání, pak jsou změny šířeny zpět do objektu jiného typu. To znamená, že typ objektu předaný do volání se může lišit od typu objektu vráceného voláním.

- Při předávání typu variant ke spravovanému kódu odkazem vytvoří zařazovací modul nový objekt a před provedením volání zkopíruje obsah objektu variant do objektu. Odkaz na objekt je předán do spravované funkce, kde je uživatel volné pro změnu objektu. Při návratu ze volání jsou všechny změny provedené v odkazovaném objektu postoupeny zpět do původní varianty. Pokud se typ objektu liší od typu objektu předaného volání, je změněn typ původní varianty a hodnota je rozšířena zpět do varianty. Typ variant předaný do volání se pak může lišit od typu variant vráceného voláním.

 **Výchozí chování při zařazování variant se sadou příznaků VT_BYREF**

- Typ variant předávaný do spravovaného kódu podle hodnoty může mít nastaven příznak **VT_BYREF** , který označuje, že varianta obsahuje odkaz namísto hodnoty. V tomto případě je varianta stále zařazena do objektu, protože varianta je předávána hodnotou. Zařazovací modul automaticky vyhodnotí obsah varianty a před provedením volání zkopíruje je do nově vytvořeného objektu. Objekt je následně předán do spravované funkce; Při návratu ze volání se však objekt nerozšíří zpátky do původní varianty. Změny provedené ve spravovaném objektu jsou ztraceny.

  > [!CAUTION]
  > Neexistuje žádný způsob, jak změnit hodnotu variant předanou hodnotou, i když má varianta nastaven příznak **VT_BYREF** .

- Typ variant předávaný do spravovaného kódu odkazem může mít také nastaven příznak **VT_BYREF** , který označuje, že varianta obsahuje jiný odkaz. V takovém případě je varianta zařazena do objektu **ref** , protože varianta je předávána odkazem. Zařazovací modul automaticky vyhodnotí obsah varianty a před provedením volání zkopíruje je do nově vytvořeného objektu. Při návratu ze volání je hodnota objektu postoupena zpět na odkaz v rámci původní varianty pouze v případě, že objekt je stejného typu jako předaný objekt. To znamená, že rozšíření nemění typ variant s nastaveným příznakem **VT_BYREF** . Pokud se typ objektu změní během volání, <xref:System.InvalidCastException> dojde při návratu z volání.

Následující tabulka shrnuje pravidla šíření pro varianty a objekty.

|From|Chcete-li|Změny šířené zpět|
|----------|--------|-----------------------------|
|**Typ variant** *verze v*|**Objekt** *o*|Nikdy|
|**Objekt** *o*|**Typ variant** *verze v*|Nikdy|
|**Variantní**   ***\****  *pv*|**Ref – objekt** *o*|Vždy|
|**Ref – objekt** *o*|**Variantní**   ***\****  *pv*|Vždy|
|**Typ variant** *v* **(VT_BYREF** *&#124;* **VT_\*)**|**Objekt** *o*|Nikdy|
|**Typ variant** *v* **(VT_BYREF** *&#124;* **VT_)**|**Ref – objekt** *o*|Pouze v případě, že se typ nezměnil.|

## <a name="see-also"></a>Viz také:

- [Výchozí chování zařazování](default-marshaling-behavior.md)
- [Přenositelné a nepřenositelné typy](blittable-and-non-blittable-types.md)
- [Směrové atributy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))
- [Kopírování a přichycování](copying-and-pinning.md)
