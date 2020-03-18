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
# <a name="customizing-structure-marshaling"></a><span data-ttu-id="8fd82-103">Přizpůsobení zařazování struktur</span><span class="sxs-lookup"><span data-stu-id="8fd82-103">Customizing structure marshaling</span></span>

<span data-ttu-id="8fd82-104">Někdy výchozí zařazování pravidla pro struktury nejsou přesně to, co potřebujete.</span><span class="sxs-lookup"><span data-stu-id="8fd82-104">Sometimes the default marshaling rules for structures aren't exactly what you need.</span></span> <span data-ttu-id="8fd82-105">Runtimes rozhraní .NET poskytují několik rozšiřujících bodů pro přizpůsobení rozložení struktury a způsobu, jakým jsou zařazována pole.</span><span class="sxs-lookup"><span data-stu-id="8fd82-105">The .NET runtimes provide a few extension points for you to customize your structure's layout and how fields are marshaled.</span></span>

## <a name="customizing-structure-layout"></a><span data-ttu-id="8fd82-106">Přizpůsobení rozložení struktury</span><span class="sxs-lookup"><span data-stu-id="8fd82-106">Customizing structure layout</span></span>

<span data-ttu-id="8fd82-107">Rozhraní .NET <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=nameWithType> poskytuje <xref:System.Runtime.InteropServices.LayoutKind?displayProperty=nameWithType> atribut a výčet, které umožňují přizpůsobit způsob umístění polí do paměti.</span><span class="sxs-lookup"><span data-stu-id="8fd82-107">.NET provides the <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=nameWithType> attribute and the <xref:System.Runtime.InteropServices.LayoutKind?displayProperty=nameWithType> enumeration to allow you to customize how fields are placed in memory.</span></span> <span data-ttu-id="8fd82-108">Následující pokyny vám pomohou vyhnout se běžným problémům.</span><span class="sxs-lookup"><span data-stu-id="8fd82-108">The following guidance will help you avoid common issues.</span></span>

<span data-ttu-id="8fd82-109">✔️ ZVÁŽIT `LayoutKind.Sequential` použití, kdykoli je to možné.</span><span class="sxs-lookup"><span data-stu-id="8fd82-109">✔️ CONSIDER using `LayoutKind.Sequential` whenever possible.</span></span>

<span data-ttu-id="8fd82-110">✔️ do `LayoutKind.Explicit` použít pouze při zařazování, pokud vaše nativní struktura má také explicitní rozložení, jako je například unie.</span><span class="sxs-lookup"><span data-stu-id="8fd82-110">✔️ DO only use `LayoutKind.Explicit` in marshaling when your native struct is also has an explicit layout, such as a union.</span></span>

<span data-ttu-id="8fd82-111">❌Vyhněte se použití `LayoutKind.Explicit` při zařazování struktur na platformách jiných než Windows, pokud potřebujete cílit na runtimes před .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="8fd82-111">❌ AVOID using `LayoutKind.Explicit` when marshaling structures on non-Windows platforms if you need to target runtimes before .NET Core 3.0.</span></span> <span data-ttu-id="8fd82-112">Runtime .NET Core před 3.0 nepodporuje předávání explicitních struktur podle hodnoty nativním funkcím v systémech Intel nebo AMD 64bitových mimo systém Windows.</span><span class="sxs-lookup"><span data-stu-id="8fd82-112">The .NET Core runtime before 3.0 doesn't support passing explicit structures by value to native functions on Intel or AMD 64-bit non-Windows systems.</span></span> <span data-ttu-id="8fd82-113">Však runtime podporuje předávání explicitní struktury odkazem na všech platformách.</span><span class="sxs-lookup"><span data-stu-id="8fd82-113">However, the runtime supports passing explicit structures by reference on all platforms.</span></span>

## <a name="customizing-boolean-field-marshaling"></a><span data-ttu-id="8fd82-114">Přizpůsobení zařazování logického pole</span><span class="sxs-lookup"><span data-stu-id="8fd82-114">Customizing boolean field marshaling</span></span>

<span data-ttu-id="8fd82-115">Nativní kód má mnoho různých logických reprezentací.</span><span class="sxs-lookup"><span data-stu-id="8fd82-115">Native code has many different boolean representations.</span></span> <span data-ttu-id="8fd82-116">Samotné ho systému Windows existují tři způsoby, jak představují logické hodnoty.</span><span class="sxs-lookup"><span data-stu-id="8fd82-116">On Windows alone, there are three ways to represent boolean values.</span></span> <span data-ttu-id="8fd82-117">Runtime nezná nativní definici vaší struktury, takže to nejlepší, co může udělat, je odhadnout, jak zařadit logické hodnoty.</span><span class="sxs-lookup"><span data-stu-id="8fd82-117">The runtime doesn't know the native definition of your structure, so the best it can do is make a guess on how to marshal your boolean values.</span></span> <span data-ttu-id="8fd82-118">Runtime rozhraní .NET poskytuje způsob, jak označit, jak zařazovat logické pole.</span><span class="sxs-lookup"><span data-stu-id="8fd82-118">The .NET runtime provides a way to indicate how to marshal your boolean field.</span></span> <span data-ttu-id="8fd82-119">Následující příklady ukazují, jak `bool` zařadit rozhraní .NET do různých nativních logických typů.</span><span class="sxs-lookup"><span data-stu-id="8fd82-119">The following examples show how to marshal .NET `bool` to different native boolean types.</span></span>

<span data-ttu-id="8fd82-120">Logické hodnoty, které jsou ve výchozím nastavení zařazovány jako nativní 4bajtová hodnota Win32, [`BOOL`](/windows/desktop/winprog/windows-data-types#BOOL) jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="8fd82-120">Boolean values default to marshaling as a native 4-byte Win32 [`BOOL`](/windows/desktop/winprog/windows-data-types#BOOL) value as shown in the following example:</span></span>

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

<span data-ttu-id="8fd82-121">Pokud chcete být explicitní, můžete <xref:System.Runtime.InteropServices.UnmanagedType.Bool?displayProperty=nameWithType> použít hodnotu získat stejné chování jako výše:</span><span class="sxs-lookup"><span data-stu-id="8fd82-121">If you want to be explicit, you can use the <xref:System.Runtime.InteropServices.UnmanagedType.Bool?displayProperty=nameWithType> value to get the same behavior as above:</span></span>

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

<span data-ttu-id="8fd82-122">Pomocí `UnmanagedType.U1` níže `UnmanagedType.I1` uvedených hodnot nebo můžete při `b` spuštění sdělit, aby `bool` zařazuje pole jako nativní typ o 1 bajt.</span><span class="sxs-lookup"><span data-stu-id="8fd82-122">Using the `UnmanagedType.U1` or `UnmanagedType.I1` values below, you can tell the runtime to marshal the `b` field as a 1-byte native `bool` type.</span></span>

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

<span data-ttu-id="8fd82-123">V systému Windows <xref:System.Runtime.InteropServices.UnmanagedType.VariantBool?displayProperty=nameWithType> můžete použít hodnotu k sděluje za běhu `VARIANT_BOOL` zařazovat logickou hodnotu na hodnotu 2 bajty:</span><span class="sxs-lookup"><span data-stu-id="8fd82-123">On Windows, you can use the <xref:System.Runtime.InteropServices.UnmanagedType.VariantBool?displayProperty=nameWithType> value to tell the runtime to marshal your boolean value to a 2-byte `VARIANT_BOOL` value:</span></span>

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
> <span data-ttu-id="8fd82-124">`VARIANT_BOOL`je jiný než většina `VARIANT_TRUE = -1` bool typy v tom a `VARIANT_FALSE = 0`.</span><span class="sxs-lookup"><span data-stu-id="8fd82-124">`VARIANT_BOOL` is different than most bool types in that `VARIANT_TRUE = -1` and `VARIANT_FALSE = 0`.</span></span> <span data-ttu-id="8fd82-125">Navíc všechny hodnoty, které nejsou `VARIANT_TRUE` rovny jsou považovány za false.</span><span class="sxs-lookup"><span data-stu-id="8fd82-125">Additionally, all values that aren't equal to `VARIANT_TRUE` are considered false.</span></span>

## <a name="customizing-array-field-marshaling"></a><span data-ttu-id="8fd82-126">Přizpůsobení zařazování polí pole pole</span><span class="sxs-lookup"><span data-stu-id="8fd82-126">Customizing array field marshaling</span></span>

<span data-ttu-id="8fd82-127">Rozhraní .NET také obsahuje několik způsobů, jak přizpůsobit zařazování polí.</span><span class="sxs-lookup"><span data-stu-id="8fd82-127">.NET also includes a few ways to customize array marshaling.</span></span>

<span data-ttu-id="8fd82-128">Ve výchozím nastavení jsou pole .NET marshals jako ukazatel na souvislý seznam prvků:</span><span class="sxs-lookup"><span data-stu-id="8fd82-128">By default, .NET marshals arrays as a pointer to a contiguous list of the elements:</span></span>

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

<span data-ttu-id="8fd82-129">Pokud propojíte s com API, bude pravděpodobně muset `SAFEARRAY*` zařazovat pole jako objekty.</span><span class="sxs-lookup"><span data-stu-id="8fd82-129">If you're interfacing with COM APIs, you may have to marshal arrays as `SAFEARRAY*` objects.</span></span> <span data-ttu-id="8fd82-130">Hodnotu <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> <xref:System.Runtime.InteropServices.UnmanagedType.SafeArray?displayProperty=nameWithType> a můžete použít k správě za běhu, `SAFEARRAY*`aby bylo pole zařazováno jako :</span><span class="sxs-lookup"><span data-stu-id="8fd82-130">You can use the <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> and the <xref:System.Runtime.InteropServices.UnmanagedType.SafeArray?displayProperty=nameWithType> value to tell the runtime to marshal an array as a `SAFEARRAY*`:</span></span>

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

<span data-ttu-id="8fd82-131">Pokud potřebujete přizpůsobit, jaký typ prvku `SAFEARRAY`je v , <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArraySubType?displayProperty=nameWithType> <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArrayUserDefinedSubType?displayProperty=nameWithType> pak můžete použít pole a `SAFEARRAY`přizpůsobit přesný typ prvku .</span><span class="sxs-lookup"><span data-stu-id="8fd82-131">If you need to customize what type of element is in the `SAFEARRAY`, then you can use the <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArraySubType?displayProperty=nameWithType> and <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArrayUserDefinedSubType?displayProperty=nameWithType> fields to customize the exact element type of the `SAFEARRAY`.</span></span>

<span data-ttu-id="8fd82-132">Pokud potřebujete zařadit pole na místě, <xref:System.Runtime.InteropServices.UnmanagedType.ByValArray?displayProperty=nameWithType> můžete použít hodnotu sdělit zařazovací zařízení zařazovat pole na místě.</span><span class="sxs-lookup"><span data-stu-id="8fd82-132">If you need to marshal the array in-place, you can use the <xref:System.Runtime.InteropServices.UnmanagedType.ByValArray?displayProperty=nameWithType> value to tell the marshaler to marshal the array in-place.</span></span> <span data-ttu-id="8fd82-133">Při použití tohoto zařazování, musíte také <xref:System.Runtime.InteropServices.MarshalAsAttribute.SizeConst?displayProperty=nameWithType> zadat hodnotu pole pro počet prvků v poli, aby runtime můžete správně přidělit prostor pro strukturu.</span><span class="sxs-lookup"><span data-stu-id="8fd82-133">When you're using this marshaling, you also must supply a value to the <xref:System.Runtime.InteropServices.MarshalAsAttribute.SizeConst?displayProperty=nameWithType> field  for the number of elements in the array so the runtime can correctly allocate space for the structure.</span></span>

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
> <span data-ttu-id="8fd82-134">Rozhraní .NET nepodporuje zařazování pole pole proměnné délky jako člen flexibilního pole C99.</span><span class="sxs-lookup"><span data-stu-id="8fd82-134">.NET doesn't support marshaling a variable length array field as a C99 Flexible Array Member.</span></span>

## <a name="customizing-string-field-marshaling"></a><span data-ttu-id="8fd82-135">Přizpůsobení zařazování pole řetězce</span><span class="sxs-lookup"><span data-stu-id="8fd82-135">Customizing string field marshaling</span></span>

<span data-ttu-id="8fd82-136">Rozhraní .NET také poskytuje širokou škálu vlastních nastavení pro zařazování řetězcových polí.</span><span class="sxs-lookup"><span data-stu-id="8fd82-136">.NET also provides a wide variety of customizations for marshaling string fields.</span></span>

<span data-ttu-id="8fd82-137">Ve výchozím nastavení zařazuje rozhraní .NET řetězec jako ukazatel na řetězec ukončený nulou.</span><span class="sxs-lookup"><span data-stu-id="8fd82-137">By default, .NET marshals a string as a pointer to a null-terminated string.</span></span> <span data-ttu-id="8fd82-138">Kódování závisí na hodnotě <xref:System.Runtime.InteropServices.StructLayoutAttribute.CharSet?displayProperty=nameWithType> pole v <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=nameWithType>oblasti .</span><span class="sxs-lookup"><span data-stu-id="8fd82-138">The encoding depends on the value of the <xref:System.Runtime.InteropServices.StructLayoutAttribute.CharSet?displayProperty=nameWithType> field in the <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=nameWithType>.</span></span> <span data-ttu-id="8fd82-139">Pokud není zadán žádný atribut, kódování je výchozí pro kódování ANSI.</span><span class="sxs-lookup"><span data-stu-id="8fd82-139">If no attribute is specified, the encoding defaults to an ANSI encoding.</span></span>

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

<span data-ttu-id="8fd82-140">Pokud potřebujete použít různá kódování pro různá pole nebo prostě chcete být v definici <xref:System.Runtime.InteropServices.UnmanagedType.LPWStr?displayProperty=nameWithType> struktury <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> konkrétnější, můžete použít hodnoty <xref:System.Runtime.InteropServices.UnmanagedType.LPStr?displayProperty=nameWithType> nebo na atributu.</span><span class="sxs-lookup"><span data-stu-id="8fd82-140">If you need to use different encodings for different fields or just prefer to be more explicit in your struct definition, you can use the <xref:System.Runtime.InteropServices.UnmanagedType.LPStr?displayProperty=nameWithType> or <xref:System.Runtime.InteropServices.UnmanagedType.LPWStr?displayProperty=nameWithType> values on a <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> attribute.</span></span>

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

<span data-ttu-id="8fd82-141">Pokud chcete zařadit řetězce pomocí kódování UTF-8, můžete <xref:System.Runtime.InteropServices.UnmanagedType.LPUTF8Str?displayProperty=nameWithType> použít <xref:System.Runtime.InteropServices.MarshalAsAttribute>hodnotu ve vašem .</span><span class="sxs-lookup"><span data-stu-id="8fd82-141">If you want to marshal your strings using the UTF-8 encoding, you can use the <xref:System.Runtime.InteropServices.UnmanagedType.LPUTF8Str?displayProperty=nameWithType> value in your <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span></span>

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
> <span data-ttu-id="8fd82-142">Použití <xref:System.Runtime.InteropServices.UnmanagedType.LPUTF8Str?displayProperty=nameWithType> vyžaduje buď rozhraní .NET Framework 4.7 (nebo novější verze) nebo .NET Core 1.1 (nebo novější verze).</span><span class="sxs-lookup"><span data-stu-id="8fd82-142">Using <xref:System.Runtime.InteropServices.UnmanagedType.LPUTF8Str?displayProperty=nameWithType> requires either .NET Framework 4.7 (or later versions) or .NET Core 1.1 (or later versions).</span></span> <span data-ttu-id="8fd82-143">Není k dispozici v rozhraní .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="8fd82-143">It isn't available in .NET Standard 2.0.</span></span>

<span data-ttu-id="8fd82-144">Pokud pracujete s com API, budete muset zařadit `BSTR`řetězec jako .</span><span class="sxs-lookup"><span data-stu-id="8fd82-144">If you're working with COM APIs, you may need to marshal a string as a `BSTR`.</span></span> <span data-ttu-id="8fd82-145">Pomocí <xref:System.Runtime.InteropServices.UnmanagedType.BStr?displayProperty=nameWithType> hodnoty můžete zařadit řetězec `BSTR`jako .</span><span class="sxs-lookup"><span data-stu-id="8fd82-145">Using the <xref:System.Runtime.InteropServices.UnmanagedType.BStr?displayProperty=nameWithType> value, you can marshal a string as a `BSTR`.</span></span>

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

<span data-ttu-id="8fd82-146">Při použití rozhraní API založené na WinRT, budete `HSTRING`muset zařadit řetězec jako .</span><span class="sxs-lookup"><span data-stu-id="8fd82-146">When using a WinRT-based API, you may need to marshal a string as an `HSTRING`.</span></span>  <span data-ttu-id="8fd82-147">Pomocí <xref:System.Runtime.InteropServices.UnmanagedType.HString?displayProperty=nameWithType> hodnoty můžete zařadit řetězec `HSTRING`jako .</span><span class="sxs-lookup"><span data-stu-id="8fd82-147">Using the <xref:System.Runtime.InteropServices.UnmanagedType.HString?displayProperty=nameWithType> value, you can marshal a string as a `HSTRING`.</span></span>

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

<span data-ttu-id="8fd82-148">Pokud vaše rozhraní API vyžaduje, abyste předat řetězec na místě <xref:System.Runtime.InteropServices.UnmanagedType.ByValTStr?displayProperty=nameWithType> ve struktuře, můžete použít hodnotu.</span><span class="sxs-lookup"><span data-stu-id="8fd82-148">If your API requires you to pass the string in-place in the structure, you can use the <xref:System.Runtime.InteropServices.UnmanagedType.ByValTStr?displayProperty=nameWithType> value.</span></span> <span data-ttu-id="8fd82-149">Všimněte si, že kódování pro `ByValTStr` řetězec zařazen `CharSet` podle je určena z atributu.</span><span class="sxs-lookup"><span data-stu-id="8fd82-149">Do note that the encoding for a string marshaled by `ByValTStr` is determined from the `CharSet` attribute.</span></span> <span data-ttu-id="8fd82-150">Navíc vyžaduje, aby délka řetězce je <xref:System.Runtime.InteropServices.MarshalAsAttribute.SizeConst?displayProperty=nameWithType> předána polem.</span><span class="sxs-lookup"><span data-stu-id="8fd82-150">Additionally, it requires that a string length is passed by the <xref:System.Runtime.InteropServices.MarshalAsAttribute.SizeConst?displayProperty=nameWithType> field.</span></span>

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

## <a name="customizing-decimal-field-marshaling"></a><span data-ttu-id="8fd82-151">Přizpůsobení zařazování desetinných polí</span><span class="sxs-lookup"><span data-stu-id="8fd82-151">Customizing decimal field marshaling</span></span>

<span data-ttu-id="8fd82-152">Pokud pracujete v systému Windows, může dojít k [ `CY` `CURRENCY` ](/windows/win32/api/wtypes/ns-wtypes-cy~r1) některých api, které používají nativní nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="8fd82-152">If you're working on Windows, you might encounter some APIs that use the native [`CY` or `CURRENCY`](/windows/win32/api/wtypes/ns-wtypes-cy~r1) structure.</span></span> <span data-ttu-id="8fd82-153">Ve výchozím nastavení `decimal` zařazuje [`DECIMAL`](/windows/win32/api/wtypes/ns-wtypes-decimal~r1) typ .NET do nativní struktury.</span><span class="sxs-lookup"><span data-stu-id="8fd82-153">By default, the .NET `decimal` type marshals to the native [`DECIMAL`](/windows/win32/api/wtypes/ns-wtypes-decimal~r1) structure.</span></span> <span data-ttu-id="8fd82-154">Však můžete použít <xref:System.Runtime.InteropServices.MarshalAsAttribute> s <xref:System.Runtime.InteropServices.UnmanagedType.Currency?displayProperty=nameWithType> hodnotou pokyn zařazovací převést hodnotu `decimal` na nativní `CY` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="8fd82-154">However, you can use a <xref:System.Runtime.InteropServices.MarshalAsAttribute> with the <xref:System.Runtime.InteropServices.UnmanagedType.Currency?displayProperty=nameWithType> value to instruct the marshaler to convert a `decimal` value to a native `CY` value.</span></span>

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

## <a name="marshaling-systemobjects"></a><span data-ttu-id="8fd82-155">Zařazování `System.Object`s</span><span class="sxs-lookup"><span data-stu-id="8fd82-155">Marshaling `System.Object`s</span></span>

<span data-ttu-id="8fd82-156">V systému Windows `object`můžete zařazovat pole typu nativní kód.</span><span class="sxs-lookup"><span data-stu-id="8fd82-156">On Windows, you can marshal `object`-typed fields to native code.</span></span> <span data-ttu-id="8fd82-157">Tato pole můžete zařadit do jednoho ze tří typů:</span><span class="sxs-lookup"><span data-stu-id="8fd82-157">You can marshal these fields to one of three types:</span></span>

- [`VARIANT`](/windows/win32/api/oaidl/ns-oaidl-variant)
- [`IUnknown*`](/windows/desktop/api/unknwn/nn-unknwn-iunknown)
- [`IDispatch*`](/windows/desktop/api/oaidl/nn-oaidl-idispatch)

<span data-ttu-id="8fd82-158">Ve výchozím `object`nastavení bude zadané pole zařazeno `IUnknown*` do pole, které objekt zabalí.</span><span class="sxs-lookup"><span data-stu-id="8fd82-158">By default, an `object`-typed field will be marshaled to an `IUnknown*` that wraps the object.</span></span>

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

<span data-ttu-id="8fd82-159">Pokud chcete zařadit pole `IDispatch*`objektu <xref:System.Runtime.InteropServices.MarshalAsAttribute> do <xref:System.Runtime.InteropServices.UnmanagedType.IDispatch?displayProperty=nameWithType> , přidejte hodnotu.</span><span class="sxs-lookup"><span data-stu-id="8fd82-159">If you want to marshal an object field to an `IDispatch*`, add a <xref:System.Runtime.InteropServices.MarshalAsAttribute> with the <xref:System.Runtime.InteropServices.UnmanagedType.IDispatch?displayProperty=nameWithType> value.</span></span>

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

<span data-ttu-id="8fd82-160">Pokud chcete zařadit `VARIANT`jako , <xref:System.Runtime.InteropServices.MarshalAsAttribute> přidejte s hodnotou. <xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="8fd82-160">If you want to marshal it as a `VARIANT`, add a <xref:System.Runtime.InteropServices.MarshalAsAttribute> with the <xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType> value.</span></span>

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

<span data-ttu-id="8fd82-161">Následující tabulka popisuje, jak různé typy `obj` běhu pole mapují na `VARIANT`různé typy uložené v aplikaci :</span><span class="sxs-lookup"><span data-stu-id="8fd82-161">The following table describes how different runtime types of the `obj` field map to the various types stored in a `VARIANT`:</span></span>

| <span data-ttu-id="8fd82-162">Typ .NET</span><span class="sxs-lookup"><span data-stu-id="8fd82-162">.NET Type</span></span> | <span data-ttu-id="8fd82-163">TYP VARIANTY</span><span class="sxs-lookup"><span data-stu-id="8fd82-163">VARIANT Type</span></span> | | <span data-ttu-id="8fd82-164">Typ .NET</span><span class="sxs-lookup"><span data-stu-id="8fd82-164">.NET Type</span></span> | <span data-ttu-id="8fd82-165">TYP VARIANTY</span><span class="sxs-lookup"><span data-stu-id="8fd82-165">VARIANT Type</span></span> |
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
