---
title: Přizpůsobení zařazování struktury – .NET
description: Naučte se, jak přizpůsobit, jak .NET zařazování vašich struktur do nativní reprezentace.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/18/2019
dev_langs:
- csharp
- cpp
ms.openlocfilehash: b174a817e82f9a9f123c79581656cc8e7179b435
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929042"
---
# <a name="customizing-structure-marshaling"></a>Přizpůsobení zařazování struktur

Někdy výchozí pravidla zařazování pro struktury nejsou přesně to, co potřebujete. Moduly runtime .NET poskytují několik rozšiřovacích bodů pro přizpůsobení rozložení struktury a způsobu, jakým jsou pole zařazena.

## <a name="customizing-structure-layout"></a>Přizpůsobení rozložení struktury

Rozhraní .NET poskytuje <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=nameWithType> atribut <xref:System.Runtime.InteropServices.LayoutKind?displayProperty=nameWithType> a výčet, aby bylo možné přizpůsobit, jak jsou pole umístěna v paměti. Následující pokyny vám pomůžou vyhnout se běžným problémům.

**✔️ zvážit** použití `LayoutKind.Sequential` , kdykoli je to možné.

**✔️** použít `LayoutKind.Explicit` pouze v zařazování, pokud má nativní struktura také explicitní rozložení, jako je například sjednocení.

**❌ Se vyhnout** použití `LayoutKind.Explicit` při zařazování struktur na platformách jiných než Windows. Modul runtime .NET Core nepodporuje předávání explicitních struktur podle hodnot do nativních funkcí v systémech, které nejsou systémy Windows a Intel nebo AMD 64. Modul runtime však podporuje předávání explicitních struktur odkazem na všechny platformy.

## <a name="customizing-boolean-field-marshaling"></a>Přizpůsobení zařazování logických polí

Nativní kód má mnoho různých logických reprezentace. Pouze v systému Windows existují tři způsoby reprezentace logických hodnot. Běhový modul neví nativní definici struktury, takže to nejlepší je udělat, abyste se seznámili s tím, jak vaše logické hodnoty zařadit. Modul runtime .NET poskytuje způsob, jak určit, jak zařadit vaše logické pole. Následující příklady ukazují, jak zařadit rozhraní `bool` .NET do různých nativních typů Boolean.

Logické hodnoty jsou ve výchozím nastavení zařazování jako nativní [`BOOL`](/windows/desktop/winprog/windows-data-types#BOOL) hodnota 4 bajtů, jak je znázorněno v následujícím příkladu:

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

Pokud chcete být explicitní, můžete použít <xref:System.Runtime.InteropServices.UnmanagedType.Bool?displayProperty=nameWithType> hodnotu k získání stejného chování jako v předchozích krocích:

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

Pomocí níže uvedených `UnmanagedType.I1` hodnot `b` nebo můžete určit, že modul runtime bude zařazovat pole jako nativní `bool` typ 1 bajt. `UnmanagedType.U1`

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

Ve Windows můžete použít <xref:System.Runtime.InteropServices.UnmanagedType.VariantBool?displayProperty=nameWithType> hodnotu k oznámení, že modul runtime zařadí vaši logickou hodnotu do hodnoty 2 bajty: `VARIANT_BOOL`

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
> `VARIANT_BOOL`se liší od většiny typů bool v tomto `VARIANT_TRUE = -1` a `VARIANT_FALSE = 0`. Kromě toho všechny hodnoty, které nejsou rovny `VARIANT_TRUE` , jsou považovány za NEPRAVDA.

## <a name="customizing-array-field-marshaling"></a>Přizpůsobení zařazování polí pole

Rozhraní .NET také obsahuje několik způsobů, jak přizpůsobit zařazování pole.

Ve výchozím nastavení rozhraní .NET zařazuje pole jako ukazatel na souvislý seznam elementů:

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

Pokud pracujete s rozhraními API modelu COM, možná budete muset zařadit pole `SAFEARRAY*` jako objekty. Hodnotu amůžete<xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> použít k oznámení, že modul runtime zařadí pole jako `SAFEARRAY*`: <xref:System.Runtime.InteropServices.UnmanagedType.SafeArray?displayProperty=nameWithType>

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

Pokud potřebujete přizpůsobit `SAFEARRAY`, jaký typ prvku je v, pak můžete <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArraySubType?displayProperty=nameWithType> použít pole a <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArrayUserDefinedSubType?displayProperty=nameWithType> `SAFEARRAY`k přizpůsobení přesného typu prvku.

Pokud je nutné zařadit pole na místě, můžete použít <xref:System.Runtime.InteropServices.UnmanagedType.ByValArray?displayProperty=nameWithType> hodnotu k oznámení zařazovacímu modulu k zařazení pole na místě. Při použití tohoto zařazování musíte také zadat hodnotu do <xref:System.Runtime.InteropServices.MarshalAsAttribute.SizeConst?displayProperty=nameWithType> pole pro počet prvků v poli, aby modul runtime mohl správně přidělit prostor pro strukturu.

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
> Rozhraní .NET nepodporuje zařazování pole proměnné délky jako C99 flexibilního člena pole.

## <a name="customizing-string-field-marshaling"></a>Přizpůsobení zařazování polí řetězců

Rozhraní .NET také poskytuje širokou škálu přizpůsobení pro zařazování polí řetězců.

Ve výchozím nastavení .NET zařazování řetězce jako ukazatele na řetězec zakončený hodnotou null. Kódování závisí na hodnotě <xref:System.Runtime.InteropServices.StructLayoutAttribute.CharSet?displayProperty=nameWithType> pole <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=nameWithType>v. Pokud není zadán žádný atribut, kódování je standardně kódování ANSI.

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

Pokud potřebujete použít různá kódování pro různá pole nebo pouze preferovat explicitní použití v definici struktury, můžete použít <xref:System.Runtime.InteropServices.UnmanagedType.LPStr?displayProperty=nameWithType> hodnoty nebo <xref:System.Runtime.InteropServices.UnmanagedType.LPWStr?displayProperty=nameWithType> v <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> atributu.

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

Chcete-li zařadit řetězce pomocí kódování UTF-8, můžete použít <xref:System.Runtime.InteropServices.UnmanagedType.LPUTF8Str?displayProperty=nameWithType> hodnotu <xref:System.Runtime.InteropServices.MarshalAsAttribute>v.

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
> Použití <xref:System.Runtime.InteropServices.UnmanagedType.LPUTF8Str?displayProperty=nameWithType> vyžaduje buď .NET Framework 4,7 (nebo novější verze), nebo .NET Core 1,1 (nebo novější verze). Není k dispozici v .NET Standard 2,0.

Pokud pracujete s rozhraními API modelu COM, může být nutné zařadit řetězec jako `BSTR`. Pomocí hodnoty můžete zařadit řetězec `BSTR`jako. <xref:System.Runtime.InteropServices.UnmanagedType.BStr?displayProperty=nameWithType>

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

Při použití rozhraní API založeného na WinRT může být nutné zařadit řetězec jako `HSTRING`.  Pomocí hodnoty můžete zařadit řetězec `HSTRING`jako. <xref:System.Runtime.InteropServices.UnmanagedType.HString?displayProperty=nameWithType>

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

Pokud vaše rozhraní API vyžaduje předání řetězce na místě ve struktuře, můžete použít <xref:System.Runtime.InteropServices.UnmanagedType.ByValTStr?displayProperty=nameWithType> hodnotu. Všimněte si, že kódování pro řetězec zařazování `ByValTStr` je určeno `CharSet` z atributu. Kromě toho vyžaduje, aby <xref:System.Runtime.InteropServices.MarshalAsAttribute.SizeConst?displayProperty=nameWithType> pole předalo délku řetězce.

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

Pokud pracujete v systému Windows, můžete se setkat s některými rozhraními API, která používají nativní [ `CY` nebo `CURRENCY` ](/windows/win32/api/wtypes/ns-wtypes-cy~r1) strukturu. Ve výchozím nastavení je typ `decimal` .NET zařazování do nativní [`DECIMAL`](/windows/win32/api/wtypes/ns-wtypes-decimal~r1) struktury. Můžete <xref:System.Runtime.InteropServices.MarshalAsAttribute> však použít <xref:System.Runtime.InteropServices.UnmanagedType.Currency?displayProperty=nameWithType> s hodnotou k instruování `decimal` zařazovacího modulu, aby převedl hodnotu na nativní `CY` hodnotu.

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

Ve Windows můžete zařadit `object`pole typu do nativního kódu. Tato pole můžete zařadit do jednoho ze tří typů:

- [`VARIANT`](/windows/win32/api/oaidl/ns-oaidl-variant)
- [`IUnknown*`](/windows/desktop/api/unknwn/nn-unknwn-iunknown)
- [`IDispatch*`](/windows/desktop/api/oaidl/nn-oaidl-idispatch)

Ve výchozím nastavení `object`bude pole typového typu zařazeno `IUnknown*` do objektu, který tento objekt zabalí.

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

Chcete-li zařadit pole objektu do `IDispatch*`objektu, <xref:System.Runtime.InteropServices.MarshalAsAttribute> přidejte s <xref:System.Runtime.InteropServices.UnmanagedType.IDispatch?displayProperty=nameWithType> hodnotou.

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

Pokud ho chcete zařadit jako a `VARIANT`, <xref:System.Runtime.InteropServices.MarshalAsAttribute> přidejte s <xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType> hodnotou.

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

Následující tabulka popisuje, jak jsou různé typy `obj` modulu runtime mapovány na různé typy uložené `VARIANT`v poli:

| Typ .NET | Typ VARIANT | | Typ .NET | Typ VARIANT |
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
