---
title: Přizpůsobení zařazování struktury - .NET
description: Zjistěte, jak přizpůsobit, jak zařazuje .NET struktury nativní reprezentaci.
ms.date: 01/18/2019
dev_langs:
- csharp
- cpp
ms.openlocfilehash: 7f8d1ad93633d6feef9c3c6f5d19aad52105968c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400370"
---
# <a name="customizing-structure-marshaling"></a>Přizpůsobení zařazování struktur

Někdy výchozí zařazování pravidla pro struktury nejsou přesně to, co potřebujete. Runtimes rozhraní .NET poskytují několik rozšiřujících bodů pro přizpůsobení rozložení struktury a způsobu, jakým jsou zařazována pole.

## <a name="customizing-structure-layout"></a>Přizpůsobení rozložení struktury

Rozhraní .NET <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=nameWithType> poskytuje <xref:System.Runtime.InteropServices.LayoutKind?displayProperty=nameWithType> atribut a výčet, které umožňují přizpůsobit způsob umístění polí do paměti. Následující pokyny vám pomohou vyhnout se běžným problémům.

✔️ ZVÁŽIT `LayoutKind.Sequential` použití, kdykoli je to možné.

✔️ do `LayoutKind.Explicit` použít pouze při zařazování, pokud vaše nativní struktura má také explicitní rozložení, jako je například unie.

❌Vyhněte se použití `LayoutKind.Explicit` při zařazování struktur na platformách jiných než Windows, pokud potřebujete cílit na runtimes před .NET Core 3.0. Runtime .NET Core před 3.0 nepodporuje předávání explicitních struktur podle hodnoty nativním funkcím v systémech Intel nebo AMD 64bitových mimo systém Windows. Však runtime podporuje předávání explicitní struktury odkazem na všech platformách.

## <a name="customizing-boolean-field-marshaling"></a>Přizpůsobení zařazování logického pole

Nativní kód má mnoho různých logických reprezentací. Samotné ho systému Windows existují tři způsoby, jak představují logické hodnoty. Runtime nezná nativní definici vaší struktury, takže to nejlepší, co může udělat, je odhadnout, jak zařadit logické hodnoty. Runtime rozhraní .NET poskytuje způsob, jak označit, jak zařazovat logické pole. Následující příklady ukazují, jak `bool` zařadit rozhraní .NET do různých nativních logických typů.

Logické hodnoty, které jsou ve výchozím nastavení zařazovány jako nativní 4bajtová hodnota Win32, [`BOOL`](/windows/desktop/winprog/windows-data-types#BOOL) jak je znázorněno v následujícím příkladu:

```csharp
public struct WinBool
{
    public bool b;
}
```

```cpp
struct WinBool
{
    public BOOL b;
};
```

Pokud chcete být explicitní, můžete <xref:System.Runtime.InteropServices.UnmanagedType.Bool?displayProperty=nameWithType> použít hodnotu získat stejné chování jako výše:

```csharp
public struct WinBool
{
    [MarshalAs(UnmanagedType.Bool)]
    public bool b;
}
```

```cpp
struct WinBool
{
    public BOOL b;
};
```

Pomocí `UnmanagedType.U1` níže `UnmanagedType.I1` uvedených hodnot nebo můžete při `b` spuštění sdělit, aby `bool` zařazuje pole jako nativní typ o 1 bajt.

```csharp
public struct CBool
{
    [MarshalAs(UnmanagedType.U1)]
    public bool b;
}
```

```cpp
struct CBool
{
    public bool b;
};
```

V systému Windows <xref:System.Runtime.InteropServices.UnmanagedType.VariantBool?displayProperty=nameWithType> můžete použít hodnotu k sděluje za běhu `VARIANT_BOOL` zařazovat logickou hodnotu na hodnotu 2 bajty:

```csharp
public struct VariantBool
{
    [MarshalAs(UnmanagedType.VariantBool)]
    public bool b;
}
```

```cpp
struct VariantBool
{
    public VARIANT_BOOL b;
};
```

> [!NOTE]
> `VARIANT_BOOL`je jiný než většina `VARIANT_TRUE = -1` bool typy v tom a `VARIANT_FALSE = 0`. Navíc všechny hodnoty, které nejsou `VARIANT_TRUE` rovny jsou považovány za false.

## <a name="customizing-array-field-marshaling"></a>Přizpůsobení zařazování polí pole pole

Rozhraní .NET také obsahuje několik způsobů, jak přizpůsobit zařazování polí.

Ve výchozím nastavení jsou pole .NET marshals jako ukazatel na souvislý seznam prvků:

```csharp
public struct DefaultArray
{
    public int[] values;
}
```

```cpp
struct DefaultArray
{
    int* values;
};
```

Pokud propojíte s com API, bude pravděpodobně muset `SAFEARRAY*` zařazovat pole jako objekty. Hodnotu <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> <xref:System.Runtime.InteropServices.UnmanagedType.SafeArray?displayProperty=nameWithType> a můžete použít k správě za běhu, `SAFEARRAY*`aby bylo pole zařazováno jako :

```csharp
public struct SafeArrayExample
{
    [MarshalAs(UnmanagedType.SafeArray)]
    public int[] values;
}
```

```cpp
struct SafeArrayExample
{
    SAFEARRAY* values;
};
```

Pokud potřebujete přizpůsobit, jaký typ prvku `SAFEARRAY`je v , <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArraySubType?displayProperty=nameWithType> <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArrayUserDefinedSubType?displayProperty=nameWithType> pak můžete použít pole a `SAFEARRAY`přizpůsobit přesný typ prvku .

Pokud potřebujete zařadit pole na místě, <xref:System.Runtime.InteropServices.UnmanagedType.ByValArray?displayProperty=nameWithType> můžete použít hodnotu sdělit zařazovací zařízení zařazovat pole na místě. Při použití tohoto zařazování, musíte také <xref:System.Runtime.InteropServices.MarshalAsAttribute.SizeConst?displayProperty=nameWithType> zadat hodnotu pole pro počet prvků v poli, aby runtime můžete správně přidělit prostor pro strukturu.

```csharp
public struct InPlaceArray
{
    [MarshalAs(UnmanagedType.ByValArray, SizeConst = 4)]
    public int[] values;
}
```

```cpp
struct InPlaceArray
{
    int values[4];
};
```

> [!NOTE]
> Rozhraní .NET nepodporuje zařazování pole pole proměnné délky jako člen flexibilního pole C99.

## <a name="customizing-string-field-marshaling"></a>Přizpůsobení zařazování pole řetězce

Rozhraní .NET také poskytuje širokou škálu vlastních nastavení pro zařazování řetězcových polí.

Ve výchozím nastavení zařazuje rozhraní .NET řetězec jako ukazatel na řetězec ukončený nulou. Kódování závisí na hodnotě <xref:System.Runtime.InteropServices.StructLayoutAttribute.CharSet?displayProperty=nameWithType> pole v <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=nameWithType>oblasti . Pokud není zadán žádný atribut, kódování je výchozí pro kódování ANSI.

```csharp
[StructLayout(LayoutKind.Sequential, CharSet = CharSet.Ansi)]
public struct DefaultString
{
    public string str;
}
```

```cpp
struct DefaultString
{
    char* str;
};
```

```csharp
[StructLayout(LayoutKind.Sequential, CharSet = CharSet.Unicode)]
public struct DefaultString
{
    public string str;
}
```

```cpp
struct DefaultString
{
    char16_t* str; // Could also be wchar_t* on Windows.
};
```

Pokud potřebujete použít různá kódování pro různá pole nebo prostě chcete být v definici <xref:System.Runtime.InteropServices.UnmanagedType.LPWStr?displayProperty=nameWithType> struktury <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> konkrétnější, můžete použít hodnoty <xref:System.Runtime.InteropServices.UnmanagedType.LPStr?displayProperty=nameWithType> nebo na atributu.

```csharp
public struct AnsiString
{
    [MarshalAs(UnmanagedType.LPStr)]
    public string str;
}
```

```cpp
struct AnsiString
{
    char* str;
};
```

```csharp
public struct UnicodeString
{
    [MarshalAs(UnmanagedType.LPWStr)]
    public string str;
}
```

```cpp
struct UnicodeString
{
    char16_t* str; // Could also be wchar_t* on Windows.
};
```

Pokud chcete zařadit řetězce pomocí kódování UTF-8, můžete <xref:System.Runtime.InteropServices.UnmanagedType.LPUTF8Str?displayProperty=nameWithType> použít <xref:System.Runtime.InteropServices.MarshalAsAttribute>hodnotu ve vašem .

```csharp
public struct UTF8String
{
    [MarshalAs(UnmanagedType.LPUTF8Str)]
    public string str;
}
```

```cpp
struct UTF8String
{
    char* str;
};
```

> [!NOTE]
> Použití <xref:System.Runtime.InteropServices.UnmanagedType.LPUTF8Str?displayProperty=nameWithType> vyžaduje buď rozhraní .NET Framework 4.7 (nebo novější verze) nebo .NET Core 1.1 (nebo novější verze). Není k dispozici v rozhraní .NET Standard 2.0.

Pokud pracujete s com API, budete muset zařadit `BSTR`řetězec jako . Pomocí <xref:System.Runtime.InteropServices.UnmanagedType.BStr?displayProperty=nameWithType> hodnoty můžete zařadit řetězec `BSTR`jako .

```csharp
public struct BString
{
    [MarshalAs(UnmanagedType.BStr)]
    public string str;
}
```

```cpp
struct BString
{
    BSTR str;
};
```

Při použití rozhraní API založené na WinRT, budete `HSTRING`muset zařadit řetězec jako .  Pomocí <xref:System.Runtime.InteropServices.UnmanagedType.HString?displayProperty=nameWithType> hodnoty můžete zařadit řetězec `HSTRING`jako .

```csharp
public struct HString
{
    [MarshalAs(UnmanagedType.HString)]
    public string str;
}
```

```cpp
struct BString
{
    HSTRING str;
};
```

Pokud vaše rozhraní API vyžaduje, abyste předat řetězec na místě <xref:System.Runtime.InteropServices.UnmanagedType.ByValTStr?displayProperty=nameWithType> ve struktuře, můžete použít hodnotu. Všimněte si, že kódování pro `ByValTStr` řetězec zařazen `CharSet` podle je určena z atributu. Navíc vyžaduje, aby délka řetězce je <xref:System.Runtime.InteropServices.MarshalAsAttribute.SizeConst?displayProperty=nameWithType> předána polem.

```csharp
[StructLayout(LayoutKind.Sequential, CharSet = CharSet.Ansi)]
public struct DefaultString
{
    [MarshalAs(UnmanagedType.ByValTStr, SizeConst = 4)]
    public string str;
}
```

```cpp
struct DefaultString
{
    char str[4];
};
```

```csharp
[StructLayout(LayoutKind.Sequential, CharSet = CharSet.Unicode)]
public struct DefaultString
{
    [MarshalAs(UnmanagedType.ByValTStr, SizeConst = 4)]
    public string str;
}
```

```cpp
struct DefaultString
{
    char16_t str[4]; // Could also be wchar_t[4] on Windows.
};
```

## <a name="customizing-decimal-field-marshaling"></a>Přizpůsobení zařazování desetinných polí

Pokud pracujete v systému Windows, může dojít k [ `CY` `CURRENCY` ](/windows/win32/api/wtypes/ns-wtypes-cy~r1) některých api, které používají nativní nebo struktury. Ve výchozím nastavení `decimal` zařazuje [`DECIMAL`](/windows/win32/api/wtypes/ns-wtypes-decimal~r1) typ .NET do nativní struktury. Však můžete použít <xref:System.Runtime.InteropServices.MarshalAsAttribute> s <xref:System.Runtime.InteropServices.UnmanagedType.Currency?displayProperty=nameWithType> hodnotou pokyn zařazovací převést hodnotu `decimal` na nativní `CY` hodnotu.

```csharp
public struct Currency
{
    [MarshalAs(UnmanagedType.Currency)]
    public decimal dec;
}
```

```cpp
struct Currency
{
    CY dec;
};
```

## <a name="marshaling-systemobjects"></a>Zařazování `System.Object`s

V systému Windows `object`můžete zařazovat pole typu nativní kód. Tato pole můžete zařadit do jednoho ze tří typů:

- [`VARIANT`](/windows/win32/api/oaidl/ns-oaidl-variant)
- [`IUnknown*`](/windows/desktop/api/unknwn/nn-unknwn-iunknown)
- [`IDispatch*`](/windows/desktop/api/oaidl/nn-oaidl-idispatch)

Ve výchozím `object`nastavení bude zadané pole zařazeno `IUnknown*` do pole, které objekt zabalí.

```csharp
public struct ObjectDefault
{
    public object obj;
}
```

```cpp
struct ObjectDefault
{
    IUnknown* obj;
};
```

Pokud chcete zařadit pole `IDispatch*`objektu <xref:System.Runtime.InteropServices.MarshalAsAttribute> do <xref:System.Runtime.InteropServices.UnmanagedType.IDispatch?displayProperty=nameWithType> , přidejte hodnotu.

```csharp
public struct ObjectDispatch
{
    [MarshalAs(UnmanagedType.IDispatch)]
    public object obj;
}
```

```cpp
struct ObjectDispatch
{
    IDispatch* obj;
};
```

Pokud chcete zařadit `VARIANT`jako , <xref:System.Runtime.InteropServices.MarshalAsAttribute> přidejte s hodnotou. <xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType>

```csharp
public struct ObjectVariant
{
    [MarshalAs(UnmanagedType.Struct)]
    public object obj;
}
```

```cpp
struct ObjectVariant
{
    VARIANT obj;
};
```

Následující tabulka popisuje, jak různé typy `obj` běhu pole mapují na `VARIANT`různé typy uložené v aplikaci :

| Typ .NET | TYP VARIANTY | | Typ .NET | TYP VARIANTY |
|------------|--------------|-|----------|--------------|
|  `byte`  | `VT_UI1` |     | `System.Runtime.InteropServices.BStrWrapper` | `VT_BSTR` |
| `sbyte`  | `VT_I1`  |     | `object`  | `VT_DISPATCH` |
| `short`  | `VT_I2`  |     | `System.Runtime.InteropServices.UnknownWrapper` | `VT_UNKNOWN` |
| `ushort` | `VT_UI2` |     | `System.Runtime.InteropServices.DispatchWrapper` | `VT_DISPATCH` |
| `int`    | `VT_I4`  |     | `System.Reflection.Missing` | `VT_ERROR` |
| `uint`   | `VT_UI4` |     | `(object)null` | `VT_EMPTY` |
| `long`   | `VT_I8`  |     | `bool` | `VT_BOOL` |
| `ulong`  | `VT_UI8` |     | `System.DateTime` | `VT_DATE` |
| `float`  | `VT_R4`  |     | `decimal` | `VT_DECIMAL` |
| `double` | `VT_R8`  |     | `System.Runtime.InteropServices.CurrencyWrapper` | `VT_CURRENCY` |
| `char`   | `VT_UI2` |     | `System.DBNull` | `VT_NULL` |
| `string` | `VT_BSTR`|
