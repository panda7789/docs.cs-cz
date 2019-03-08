---
title: Přizpůsobení struktury zařazování – .NET
description: Zjistěte, jak přizpůsobit, jak .NET zařazuje struktury na nativní reprezentaci.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/18/2019
dev_langs:
- csharp
- cpp
ms.openlocfilehash: 5bce891a0061bb1810559febf1ab904a5fb6fc94
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/08/2019
ms.locfileid: "57675781"
---
# <a name="customizing-structure-marshalling"></a>Přizpůsobení zařazování pro struktury

Někdy sběrného systému výchozí pravidla pro struktury nejsou přesně, co potřebujete. Moduly runtime .NET poskytují několik Rozšiřovací body můžete přizpůsobit rozvržení struktury vaší a jak zařadit pole.

## <a name="customizing-structure-layout"></a>Přizpůsobení rozložení struktury

Poskytuje rozhraní .NET <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=nameWithType> atribut a <xref:System.Runtime.InteropServices.LayoutKind?displayProperty=nameWithType> výčet, aby bylo možné přizpůsobit, jak jsou pole umístěné v paměti. Následující pokyny se snáze vyhnete běžných problémů.

**✔️ ZVAŽTE** pomocí `LayoutKind.Sequential` kdykoli je to možné.

**PROVEĎTE ✔️** používat pouze `LayoutKind.Explicit` v zařazení při nativní struktury je také má explicitní rozložení, jako je například sjednocení.

**❌ Nepoužívejte** pomocí `LayoutKind.Explicit` při zařazování pro struktury na platformách než Windows. Modul runtime .NET Core nepodporuje explicitní struktury předání hodnotou na nativní funkce v systémech než Windows Intel nebo AMD 64-bit. Modul runtime však podporuje struktury, předávání explicitní odkaz na všech platformách.

## <a name="customizing-boolean-field-marshalling"></a>Přizpůsobení zařazování pro logické pole

Nativní kód má mnoho různých logický reprezentací. Na Windows samostatně existují tři způsoby, jak reprezentaci logické hodnoty. Modul runtime nebude vědět nativní definice struktury, proto je nejlepší, co můžete dělat hádat o tom, jak zařadit logické hodnoty. Modul .NET runtime poskytuje způsob, jak určují, jak zařadit logická pole. Následující příklady ukazují, jak zařadit .NET `bool` do různých nativních typů boolean.

Výchozí zařazování pro jako nativní 4bajtový Win32 hodnoty logická hodnota [ `BOOL` ](/windows/desktop/winprog/windows-data-types#BOOL) hodnoty, jak je znázorněno v následujícím příkladu:

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

Pokud chcete explicitně, můžete použít <xref:System.Runtime.InteropServices.UnmanagedType.Bool?displayProperty=nameWithType> hodnota, která má stejné chování, jak je uvedeno výše:

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

Použití `UnmanagedType.U1` nebo `UnmanagedType.I1` níže uvedených hodnot, poznáte, modul runtime k zařazování `b` pole 1bajtových nativní `bool` typu.

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

Na Windows, můžete použít <xref:System.Runtime.InteropServices.UnmanagedType.VariantBool?displayProperty=nameWithType> hodnotu říct runtime k zařazení vaší logickou hodnotu k 2 bajtů `VARIANT_BOOL` hodnotu:

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
> `VARIANT_BOOL` se liší od většinu typů bool v dané `VARIANT_TRUE = -1` a `VARIANT_FALSE = 0`. Kromě toho všechny hodnoty, které se rovná `VARIANT_TRUE` jsou považovány za hodnotu false.

## <a name="customizing-array-field-marshalling"></a>Přizpůsobení zařazování pro pole pole

.NET zahrnuje také několik způsobů, jak přizpůsobit zařazování pro pole.

Ve výchozím nastavení zařazuje .NET pole jako ukazatel na seznam souvislých prvků:

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

Pokud se propojení s rozhraními API modelu COM, bude pravděpodobně nutné zařazování pole jako `SAFEARRAY*` objekty. Můžete použít <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> a <xref:System.Runtime.InteropServices.UnmanagedType.SafeArray?displayProperty=nameWithType> říct runtime k zařazování pole jako hodnotu `SAFEARRAY*`:

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

Pokud chcete přizpůsobit, jaký typ prvku je v `SAFEARRAY`, můžete použít <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArraySubType?displayProperty=nameWithType> a <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArrayUserDefinedSubType?displayProperty=nameWithType> polí pro přizpůsobení elementu přesný typ `SAFEARRAY`.

Pokud potřebujete pole na místě, můžete použít <xref:System.Runtime.InteropServices.UnmanagedType.ByValArray?displayProperty=nameWithType> hodnotu říct, aby zařazování odvozovalo zařazování pole na místě. Při použití této zařazování, můžete také musíte zadat hodnotu, která <xref:System.Runtime.InteropServices.MarshalAsAttribute.SizeConst?displayProperty=nameWithType> pole pro počet prvků v poli, aby modul runtime může správně přidělit místo pro strukturu.

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
> .NET nepodporuje zařazování pro pole s proměnnou délkou pole jako člena flexibilního pole C99.

## <a name="customizing-string-field-marshalling"></a>Přizpůsobení zařazování pro pole řetězce

.NET také poskytuje širokou škálu vlastní nastavení pro zařazování pro pole řetězců.

Ve výchozím nastavení zařazuje .NET řetězec jako ukazatel na řetězec zakončený hodnotou null. Kódování závisí na hodnotě <xref:System.Runtime.InteropServices.StructLayoutAttribute.CharSet?displayProperty=nameWithType> pole <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=nameWithType>. Pokud není zadán žádný atribut, kódování, výchozí kódování ANSI.

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

Pokud budete muset použít jiné kódování pro různá pole nebo jen dáváte přednost více explicitně v definici struktury, můžete použít <xref:System.Runtime.InteropServices.UnmanagedType.LPStr?displayProperty=nameWithType> nebo <xref:System.Runtime.InteropServices.UnmanagedType.LPWStr?displayProperty=nameWithType> hodnoty na <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> atribut.

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

Pokud chcete k zařazení vaší řetězce s kódováním UTF-8, můžete použít <xref:System.Runtime.InteropServices.UnmanagedType.LPUTF8Str?displayProperty=nameWithType> hodnota ve vaší <xref:System.Runtime.InteropServices.MarshalAsAttribute>.


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
> Pomocí <xref:System.Runtime.InteropServices.UnmanagedType.LPUTF8Str?displayProperty=nameWithType> vyžaduje rozhraní .NET Framework 4.7 (nebo novější verze) nebo .NET Core 1.1 (nebo novější verze). Není k dispozici v rozhraní .NET Standard 2.0.

Pokud pracujete s rozhraními API modelu COM, budete muset řetězec jako `BSTR`. Použití <xref:System.Runtime.InteropServices.UnmanagedType.BStr?displayProperty=nameWithType> hodnota, které by mohl zařazovat řetězec jako `BSTR`.

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

Při použití rozhraní API založené na WinRT, budete muset řetězec jako `HSTRING`.  Použití <xref:System.Runtime.InteropServices.UnmanagedType.HString?displayProperty=nameWithType> hodnota, které by mohl zařazovat řetězec jako `HSTRING`.

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

Pokud vaše rozhraní API vyžaduje, abyste ve struktuře předat řetězec v místě, můžete použít <xref:System.Runtime.InteropServices.UnmanagedType.ByValTStr?displayProperty=nameWithType> hodnotu. Všimněte si, že kódování pro řetězce zařazeno ve `ByValTStr` se určí na základě `CharSet` atribut. Navíc se vyžaduje, aby délka řetězce je předaný odkazem <xref:System.Runtime.InteropServices.MarshalAsAttribute.SizeConst?displayProperty=nameWithType> pole.

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

## <a name="customizing-decimal-field-marshalling"></a>Přizpůsobení zařazování desítkové pole

Pokud pracujete ve Windows, může dojít některá rozhraní API, použít nativní [ `CY` nebo `CURRENCY` ](/windows/desktop/api/wtypes/ns-wtypes-tagcy) struktury. Ve výchozím nastavení, .NET `decimal` zadejte marshals na nativní [ `DECIMAL` ](/windows/desktop/api/wtypes/ns-wtypes-tagdec) struktury. Však můžete použít <xref:System.Runtime.InteropServices.MarshalAsAttribute> s <xref:System.Runtime.InteropServices.UnmanagedType.Currency?displayProperty=nameWithType> hodnotu dáte pokyn, aby zařazování pro převod `decimal` hodnotu na nativní `CY` hodnotu.

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

## <a name="marshalling-systemobjects"></a>Zařazování `System.Object`s

Na Windows, které by mohl zařazovat `object`– zadané pole do nativního kódu. By mohl zařazovat těchto polí do jednoho ze tří typů:
- [`VARIANT`](/windows/desktop/api/oaidl/ns-oaidl-tagvariant)
- [`IUnknown*`](/windows/desktop/api/unknwn/nn-unknwn-iunknown)
- [`IDispatch*`](/windows/desktop/api/oaidl/nn-oaidl-idispatch)

Ve výchozím nastavení `object`-typovaná pole bude zařazeno do `IUnknown*` , která zabalí objekt.

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

Pokud chcete přeuspořádat polem objektu do `IDispatch*`, přidat <xref:System.Runtime.InteropServices.MarshalAsAttribute> s <xref:System.Runtime.InteropServices.UnmanagedType.IDispatch?displayProperty=nameWithType> hodnotu.

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

Pokud chcete zařadit jako `VARIANT`, přidejte <xref:System.Runtime.InteropServices.MarshalAsAttribute> s <xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType> hodnotu.

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

Následující tabulka popisuje, jak různé typy runtime `obj` mapování polí na různé typy, které jsou uložené v `VARIANT`:

| Typ formátu .NET | Typ VARIANT | | Typ formátu .NET | Typ VARIANT |
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
