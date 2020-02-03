---
title: Přizpůsobení zařazování struktury – .NET
description: Naučte se, jak přizpůsobit, jak .NET zařazování vašich struktur do nativní reprezentace.
ms.date: 01/18/2019
dev_langs:
- csharp
- cpp
ms.openlocfilehash: 7f8d1ad93633d6feef9c3c6f5d19aad52105968c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741528"
---
# <a name="customizing-structure-marshaling"></a><span data-ttu-id="a0f0c-103">Přizpůsobení zařazování struktur</span><span class="sxs-lookup"><span data-stu-id="a0f0c-103">Customizing structure marshaling</span></span>

<span data-ttu-id="a0f0c-104">Někdy výchozí pravidla zařazování pro struktury nejsou přesně to, co potřebujete.</span><span class="sxs-lookup"><span data-stu-id="a0f0c-104">Sometimes the default marshaling rules for structures aren't exactly what you need.</span></span> <span data-ttu-id="a0f0c-105">Moduly runtime .NET poskytují několik rozšiřovacích bodů pro přizpůsobení rozložení struktury a způsobu, jakým jsou pole zařazena.</span><span class="sxs-lookup"><span data-stu-id="a0f0c-105">The .NET runtimes provide a few extension points for you to customize your structure's layout and how fields are marshaled.</span></span>

## <a name="customizing-structure-layout"></a><span data-ttu-id="a0f0c-106">Přizpůsobení rozložení struktury</span><span class="sxs-lookup"><span data-stu-id="a0f0c-106">Customizing structure layout</span></span>

<span data-ttu-id="a0f0c-107">Rozhraní .NET poskytuje atribut <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=nameWithType> a výčet <xref:System.Runtime.InteropServices.LayoutKind?displayProperty=nameWithType>, který umožňuje přizpůsobit, jak jsou pole umístěna v paměti.</span><span class="sxs-lookup"><span data-stu-id="a0f0c-107">.NET provides the <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=nameWithType> attribute and the <xref:System.Runtime.InteropServices.LayoutKind?displayProperty=nameWithType> enumeration to allow you to customize how fields are placed in memory.</span></span> <span data-ttu-id="a0f0c-108">Následující pokyny vám pomůžou vyhnout se běžným problémům.</span><span class="sxs-lookup"><span data-stu-id="a0f0c-108">The following guidance will help you avoid common issues.</span></span>

<span data-ttu-id="a0f0c-109">✔️ Zvažte použití `LayoutKind.Sequential`, kdykoli to bude možné.</span><span class="sxs-lookup"><span data-stu-id="a0f0c-109">✔️ CONSIDER using `LayoutKind.Sequential` whenever possible.</span></span>

<span data-ttu-id="a0f0c-110">✔️ použít `LayoutKind.Explicit` v zařazování pouze v případě, že nativní struktura má také explicitní rozložení, jako je například sjednocení.</span><span class="sxs-lookup"><span data-stu-id="a0f0c-110">✔️ DO only use `LayoutKind.Explicit` in marshaling when your native struct is also has an explicit layout, such as a union.</span></span>

<span data-ttu-id="a0f0c-111">❌ se vyhnout použití `LayoutKind.Explicit` při zařazování struktur na platformách jiných než Windows, pokud potřebujete cílit na modul runtime před .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="a0f0c-111">❌ AVOID using `LayoutKind.Explicit` when marshaling structures on non-Windows platforms if you need to target runtimes before .NET Core 3.0.</span></span> <span data-ttu-id="a0f0c-112">Modul runtime .NET Core před 3,0 nepodporuje předávání explicitních struktur podle hodnot nativním funkcím na systémy, které nepoužívají procesory Intel nebo AMD 64.</span><span class="sxs-lookup"><span data-stu-id="a0f0c-112">The .NET Core runtime before 3.0 doesn't support passing explicit structures by value to native functions on Intel or AMD 64-bit non-Windows systems.</span></span> <span data-ttu-id="a0f0c-113">Modul runtime však podporuje předávání explicitních struktur odkazem na všechny platformy.</span><span class="sxs-lookup"><span data-stu-id="a0f0c-113">However, the runtime supports passing explicit structures by reference on all platforms.</span></span>

## <a name="customizing-boolean-field-marshaling"></a><span data-ttu-id="a0f0c-114">Přizpůsobení zařazování logických polí</span><span class="sxs-lookup"><span data-stu-id="a0f0c-114">Customizing boolean field marshaling</span></span>

<span data-ttu-id="a0f0c-115">Nativní kód má mnoho různých logických reprezentace.</span><span class="sxs-lookup"><span data-stu-id="a0f0c-115">Native code has many different boolean representations.</span></span> <span data-ttu-id="a0f0c-116">Pouze v systému Windows existují tři způsoby reprezentace logických hodnot.</span><span class="sxs-lookup"><span data-stu-id="a0f0c-116">On Windows alone, there are three ways to represent boolean values.</span></span> <span data-ttu-id="a0f0c-117">Běhový modul neví nativní definici struktury, takže to nejlepší je udělat, abyste se seznámili s tím, jak vaše logické hodnoty zařadit.</span><span class="sxs-lookup"><span data-stu-id="a0f0c-117">The runtime doesn't know the native definition of your structure, so the best it can do is make a guess on how to marshal your boolean values.</span></span> <span data-ttu-id="a0f0c-118">Modul runtime .NET poskytuje způsob, jak určit, jak zařadit vaše logické pole.</span><span class="sxs-lookup"><span data-stu-id="a0f0c-118">The .NET runtime provides a way to indicate how to marshal your boolean field.</span></span> <span data-ttu-id="a0f0c-119">Následující příklady ukazují, jak zařadit `bool` .NET do různých nativních logických typů.</span><span class="sxs-lookup"><span data-stu-id="a0f0c-119">The following examples show how to marshal .NET `bool` to different native boolean types.</span></span>

<span data-ttu-id="a0f0c-120">Logické hodnoty jsou ve výchozím nastavení zařazování jako nativní 4 bajtové [`BOOL`](/windows/desktop/winprog/windows-data-types#BOOL) hodnota, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="a0f0c-120">Boolean values default to marshaling as a native 4-byte Win32 [`BOOL`](/windows/desktop/winprog/windows-data-types#BOOL) value as shown in the following example:</span></span>

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

<span data-ttu-id="a0f0c-121">Pokud chcete být explicitní, můžete pomocí hodnoty <xref:System.Runtime.InteropServices.UnmanagedType.Bool?displayProperty=nameWithType> získat stejné chování jako v předchozích krocích:</span><span class="sxs-lookup"><span data-stu-id="a0f0c-121">If you want to be explicit, you can use the <xref:System.Runtime.InteropServices.UnmanagedType.Bool?displayProperty=nameWithType> value to get the same behavior as above:</span></span>

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

<span data-ttu-id="a0f0c-122">Pomocí níže uvedených hodnot `UnmanagedType.U1` nebo `UnmanagedType.I1` můžete určit, že modul runtime zařadí pole `b` jako nativní typ `bool` 1 bajt.</span><span class="sxs-lookup"><span data-stu-id="a0f0c-122">Using the `UnmanagedType.U1` or `UnmanagedType.I1` values below, you can tell the runtime to marshal the `b` field as a 1-byte native `bool` type.</span></span>

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

<span data-ttu-id="a0f0c-123">V systému Windows můžete použít hodnotu <xref:System.Runtime.InteropServices.UnmanagedType.VariantBool?displayProperty=nameWithType> k informování modulu runtime o zařazení vaší logické hodnoty na 2 bajtovou hodnotu `VARIANT_BOOL`:</span><span class="sxs-lookup"><span data-stu-id="a0f0c-123">On Windows, you can use the <xref:System.Runtime.InteropServices.UnmanagedType.VariantBool?displayProperty=nameWithType> value to tell the runtime to marshal your boolean value to a 2-byte `VARIANT_BOOL` value:</span></span>

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
> <span data-ttu-id="a0f0c-124">`VARIANT_BOOL` se liší od většiny typů bool v daném `VARIANT_TRUE = -1` a `VARIANT_FALSE = 0`.</span><span class="sxs-lookup"><span data-stu-id="a0f0c-124">`VARIANT_BOOL` is different than most bool types in that `VARIANT_TRUE = -1` and `VARIANT_FALSE = 0`.</span></span> <span data-ttu-id="a0f0c-125">Kromě toho všechny hodnoty, které nejsou rovny `VARIANT_TRUE`, se považují za NEPRAVDA.</span><span class="sxs-lookup"><span data-stu-id="a0f0c-125">Additionally, all values that aren't equal to `VARIANT_TRUE` are considered false.</span></span>

## <a name="customizing-array-field-marshaling"></a><span data-ttu-id="a0f0c-126">Přizpůsobení zařazování polí pole</span><span class="sxs-lookup"><span data-stu-id="a0f0c-126">Customizing array field marshaling</span></span>

<span data-ttu-id="a0f0c-127">Rozhraní .NET také obsahuje několik způsobů, jak přizpůsobit zařazování pole.</span><span class="sxs-lookup"><span data-stu-id="a0f0c-127">.NET also includes a few ways to customize array marshaling.</span></span>

<span data-ttu-id="a0f0c-128">Ve výchozím nastavení rozhraní .NET zařazuje pole jako ukazatel na souvislý seznam elementů:</span><span class="sxs-lookup"><span data-stu-id="a0f0c-128">By default, .NET marshals arrays as a pointer to a contiguous list of the elements:</span></span>

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

<span data-ttu-id="a0f0c-129">Pokud pracujete s rozhraními API modelu COM, možná budete muset zařadit pole jako objekty `SAFEARRAY*`.</span><span class="sxs-lookup"><span data-stu-id="a0f0c-129">If you're interfacing with COM APIs, you may have to marshal arrays as `SAFEARRAY*` objects.</span></span> <span data-ttu-id="a0f0c-130"><xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> a hodnotu <xref:System.Runtime.InteropServices.UnmanagedType.SafeArray?displayProperty=nameWithType> můžete použít k oznámení, že modul runtime bude zařazovat pole jako `SAFEARRAY*`:</span><span class="sxs-lookup"><span data-stu-id="a0f0c-130">You can use the <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> and the <xref:System.Runtime.InteropServices.UnmanagedType.SafeArray?displayProperty=nameWithType> value to tell the runtime to marshal an array as a `SAFEARRAY*`:</span></span>

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

<span data-ttu-id="a0f0c-131">Pokud potřebujete přizpůsobit typ prvku, který je v `SAFEARRAY`, pak můžete použít pole <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArraySubType?displayProperty=nameWithType> a <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArrayUserDefinedSubType?displayProperty=nameWithType> k přizpůsobení přesného typu prvku `SAFEARRAY`.</span><span class="sxs-lookup"><span data-stu-id="a0f0c-131">If you need to customize what type of element is in the `SAFEARRAY`, then you can use the <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArraySubType?displayProperty=nameWithType> and <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArrayUserDefinedSubType?displayProperty=nameWithType> fields to customize the exact element type of the `SAFEARRAY`.</span></span>

<span data-ttu-id="a0f0c-132">Pokud je nutné zařadit pole na místě, můžete použít hodnotu <xref:System.Runtime.InteropServices.UnmanagedType.ByValArray?displayProperty=nameWithType> k oznámení zařazovacímu modulu k zařazení pole na místě.</span><span class="sxs-lookup"><span data-stu-id="a0f0c-132">If you need to marshal the array in-place, you can use the <xref:System.Runtime.InteropServices.UnmanagedType.ByValArray?displayProperty=nameWithType> value to tell the marshaler to marshal the array in-place.</span></span> <span data-ttu-id="a0f0c-133">Při použití tohoto zařazování je také nutné zadat hodnotu do pole <xref:System.Runtime.InteropServices.MarshalAsAttribute.SizeConst?displayProperty=nameWithType> pro počet prvků v poli, aby modul runtime mohl správně přidělit prostor pro strukturu.</span><span class="sxs-lookup"><span data-stu-id="a0f0c-133">When you're using this marshaling, you also must supply a value to the <xref:System.Runtime.InteropServices.MarshalAsAttribute.SizeConst?displayProperty=nameWithType> field  for the number of elements in the array so the runtime can correctly allocate space for the structure.</span></span>

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
> <span data-ttu-id="a0f0c-134">Rozhraní .NET nepodporuje zařazování pole proměnné délky jako C99 flexibilního člena pole.</span><span class="sxs-lookup"><span data-stu-id="a0f0c-134">.NET doesn't support marshaling a variable length array field as a C99 Flexible Array Member.</span></span>

## <a name="customizing-string-field-marshaling"></a><span data-ttu-id="a0f0c-135">Přizpůsobení zařazování polí řetězců</span><span class="sxs-lookup"><span data-stu-id="a0f0c-135">Customizing string field marshaling</span></span>

<span data-ttu-id="a0f0c-136">Rozhraní .NET také poskytuje širokou škálu přizpůsobení pro zařazování polí řetězců.</span><span class="sxs-lookup"><span data-stu-id="a0f0c-136">.NET also provides a wide variety of customizations for marshaling string fields.</span></span>

<span data-ttu-id="a0f0c-137">Ve výchozím nastavení .NET zařazování řetězce jako ukazatele na řetězec zakončený hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="a0f0c-137">By default, .NET marshals a string as a pointer to a null-terminated string.</span></span> <span data-ttu-id="a0f0c-138">Kódování závisí na hodnotě pole <xref:System.Runtime.InteropServices.StructLayoutAttribute.CharSet?displayProperty=nameWithType> v <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a0f0c-138">The encoding depends on the value of the <xref:System.Runtime.InteropServices.StructLayoutAttribute.CharSet?displayProperty=nameWithType> field in the <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=nameWithType>.</span></span> <span data-ttu-id="a0f0c-139">Pokud není zadán žádný atribut, kódování je standardně kódování ANSI.</span><span class="sxs-lookup"><span data-stu-id="a0f0c-139">If no attribute is specified, the encoding defaults to an ANSI encoding.</span></span>

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

<span data-ttu-id="a0f0c-140">Pokud potřebujete použít různá kódování pro různá pole nebo pouze preferovat explicitní použití v definici struktury, můžete použít hodnoty <xref:System.Runtime.InteropServices.UnmanagedType.LPStr?displayProperty=nameWithType> nebo <xref:System.Runtime.InteropServices.UnmanagedType.LPWStr?displayProperty=nameWithType> v atributu <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a0f0c-140">If you need to use different encodings for different fields or just prefer to be more explicit in your struct definition, you can use the <xref:System.Runtime.InteropServices.UnmanagedType.LPStr?displayProperty=nameWithType> or <xref:System.Runtime.InteropServices.UnmanagedType.LPWStr?displayProperty=nameWithType> values on a <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> attribute.</span></span>

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

<span data-ttu-id="a0f0c-141">Chcete-li zařadit řetězce pomocí kódování UTF-8, můžete použít hodnotu <xref:System.Runtime.InteropServices.UnmanagedType.LPUTF8Str?displayProperty=nameWithType> v <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span><span class="sxs-lookup"><span data-stu-id="a0f0c-141">If you want to marshal your strings using the UTF-8 encoding, you can use the <xref:System.Runtime.InteropServices.UnmanagedType.LPUTF8Str?displayProperty=nameWithType> value in your <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span></span>

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
> <span data-ttu-id="a0f0c-142">Použití <xref:System.Runtime.InteropServices.UnmanagedType.LPUTF8Str?displayProperty=nameWithType> vyžaduje buď .NET Framework 4,7 (nebo novější verze), nebo .NET Core 1,1 (nebo novější verze).</span><span class="sxs-lookup"><span data-stu-id="a0f0c-142">Using <xref:System.Runtime.InteropServices.UnmanagedType.LPUTF8Str?displayProperty=nameWithType> requires either .NET Framework 4.7 (or later versions) or .NET Core 1.1 (or later versions).</span></span> <span data-ttu-id="a0f0c-143">Není k dispozici v .NET Standard 2,0.</span><span class="sxs-lookup"><span data-stu-id="a0f0c-143">It isn't available in .NET Standard 2.0.</span></span>

<span data-ttu-id="a0f0c-144">Pokud pracujete s rozhraními API modelu COM, může být nutné zařadit řetězec jako `BSTR`.</span><span class="sxs-lookup"><span data-stu-id="a0f0c-144">If you're working with COM APIs, you may need to marshal a string as a `BSTR`.</span></span> <span data-ttu-id="a0f0c-145">Pomocí <xref:System.Runtime.InteropServices.UnmanagedType.BStr?displayProperty=nameWithType> hodnoty můžete zařadit řetězec jako `BSTR`.</span><span class="sxs-lookup"><span data-stu-id="a0f0c-145">Using the <xref:System.Runtime.InteropServices.UnmanagedType.BStr?displayProperty=nameWithType> value, you can marshal a string as a `BSTR`.</span></span>

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

<span data-ttu-id="a0f0c-146">Při použití rozhraní API založeného na WinRT bude možná potřeba zařadit řetězec jako `HSTRING`.</span><span class="sxs-lookup"><span data-stu-id="a0f0c-146">When using a WinRT-based API, you may need to marshal a string as an `HSTRING`.</span></span>  <span data-ttu-id="a0f0c-147">Pomocí <xref:System.Runtime.InteropServices.UnmanagedType.HString?displayProperty=nameWithType> hodnoty můžete zařadit řetězec jako `HSTRING`.</span><span class="sxs-lookup"><span data-stu-id="a0f0c-147">Using the <xref:System.Runtime.InteropServices.UnmanagedType.HString?displayProperty=nameWithType> value, you can marshal a string as a `HSTRING`.</span></span>

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

<span data-ttu-id="a0f0c-148">Pokud vaše rozhraní API vyžaduje předání řetězce na místě ve struktuře, můžete použít hodnotu <xref:System.Runtime.InteropServices.UnmanagedType.ByValTStr?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a0f0c-148">If your API requires you to pass the string in-place in the structure, you can use the <xref:System.Runtime.InteropServices.UnmanagedType.ByValTStr?displayProperty=nameWithType> value.</span></span> <span data-ttu-id="a0f0c-149">Všimněte si, že kódování pro řetězec zařazený pomocí `ByValTStr` je určeno z atributu `CharSet`.</span><span class="sxs-lookup"><span data-stu-id="a0f0c-149">Do note that the encoding for a string marshaled by `ByValTStr` is determined from the `CharSet` attribute.</span></span> <span data-ttu-id="a0f0c-150">Kromě toho vyžaduje, aby pole <xref:System.Runtime.InteropServices.MarshalAsAttribute.SizeConst?displayProperty=nameWithType> předalo délku řetězce.</span><span class="sxs-lookup"><span data-stu-id="a0f0c-150">Additionally, it requires that a string length is passed by the <xref:System.Runtime.InteropServices.MarshalAsAttribute.SizeConst?displayProperty=nameWithType> field.</span></span>

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

## <a name="customizing-decimal-field-marshaling"></a><span data-ttu-id="a0f0c-151">Přizpůsobení zařazování desetinných polí</span><span class="sxs-lookup"><span data-stu-id="a0f0c-151">Customizing decimal field marshaling</span></span>

<span data-ttu-id="a0f0c-152">Pokud pracujete v systému Windows, můžete se setkat s některými rozhraními API, která používají nativní [`CY` nebo strukturu `CURRENCY`](/windows/win32/api/wtypes/ns-wtypes-cy~r1) .</span><span class="sxs-lookup"><span data-stu-id="a0f0c-152">If you're working on Windows, you might encounter some APIs that use the native [`CY` or `CURRENCY`](/windows/win32/api/wtypes/ns-wtypes-cy~r1) structure.</span></span> <span data-ttu-id="a0f0c-153">Ve výchozím nastavení je typ `decimal` .NET zařazování do nativní struktury [`DECIMAL`](/windows/win32/api/wtypes/ns-wtypes-decimal~r1) .</span><span class="sxs-lookup"><span data-stu-id="a0f0c-153">By default, the .NET `decimal` type marshals to the native [`DECIMAL`](/windows/win32/api/wtypes/ns-wtypes-decimal~r1) structure.</span></span> <span data-ttu-id="a0f0c-154">Můžete však použít <xref:System.Runtime.InteropServices.MarshalAsAttribute> s hodnotou <xref:System.Runtime.InteropServices.UnmanagedType.Currency?displayProperty=nameWithType> a dát zařazovacímu programu pokyn k převedení `decimal` hodnoty na nativní `CY` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="a0f0c-154">However, you can use a <xref:System.Runtime.InteropServices.MarshalAsAttribute> with the <xref:System.Runtime.InteropServices.UnmanagedType.Currency?displayProperty=nameWithType> value to instruct the marshaler to convert a `decimal` value to a native `CY` value.</span></span>

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

## <a name="marshaling-systemobjects"></a><span data-ttu-id="a0f0c-155">Zařazování `System.Object`s</span><span class="sxs-lookup"><span data-stu-id="a0f0c-155">Marshaling `System.Object`s</span></span>

<span data-ttu-id="a0f0c-156">V systému Windows můžete zařadit pole typu `object`do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="a0f0c-156">On Windows, you can marshal `object`-typed fields to native code.</span></span> <span data-ttu-id="a0f0c-157">Tato pole můžete zařadit do jednoho ze tří typů:</span><span class="sxs-lookup"><span data-stu-id="a0f0c-157">You can marshal these fields to one of three types:</span></span>

- [`VARIANT`](/windows/win32/api/oaidl/ns-oaidl-variant)
- [`IUnknown*`](/windows/desktop/api/unknwn/nn-unknwn-iunknown)
- [`IDispatch*`](/windows/desktop/api/oaidl/nn-oaidl-idispatch)

<span data-ttu-id="a0f0c-158">Ve výchozím nastavení se pole `object`ho typu zazařazuje do `IUnknown*`, který tento objekt zabalí.</span><span class="sxs-lookup"><span data-stu-id="a0f0c-158">By default, an `object`-typed field will be marshaled to an `IUnknown*` that wraps the object.</span></span>

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

<span data-ttu-id="a0f0c-159">Chcete-li zařadit pole objektu do `IDispatch*`, přidejte <xref:System.Runtime.InteropServices.MarshalAsAttribute> s hodnotou <xref:System.Runtime.InteropServices.UnmanagedType.IDispatch?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a0f0c-159">If you want to marshal an object field to an `IDispatch*`, add a <xref:System.Runtime.InteropServices.MarshalAsAttribute> with the <xref:System.Runtime.InteropServices.UnmanagedType.IDispatch?displayProperty=nameWithType> value.</span></span>

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

<span data-ttu-id="a0f0c-160">Pokud ho chcete zařadit jako `VARIANT`, přidejte <xref:System.Runtime.InteropServices.MarshalAsAttribute> s hodnotou <xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a0f0c-160">If you want to marshal it as a `VARIANT`, add a <xref:System.Runtime.InteropServices.MarshalAsAttribute> with the <xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType> value.</span></span>

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

<span data-ttu-id="a0f0c-161">Následující tabulka popisuje, jak různé typy modulu runtime `obj` mapovat na různé typy uložené v `VARIANT`:</span><span class="sxs-lookup"><span data-stu-id="a0f0c-161">The following table describes how different runtime types of the `obj` field map to the various types stored in a `VARIANT`:</span></span>

| <span data-ttu-id="a0f0c-162">Typ .NET</span><span class="sxs-lookup"><span data-stu-id="a0f0c-162">.NET Type</span></span> | <span data-ttu-id="a0f0c-163">Typ VARIANT</span><span class="sxs-lookup"><span data-stu-id="a0f0c-163">VARIANT Type</span></span> | | <span data-ttu-id="a0f0c-164">Typ .NET</span><span class="sxs-lookup"><span data-stu-id="a0f0c-164">.NET Type</span></span> | <span data-ttu-id="a0f0c-165">Typ VARIANT</span><span class="sxs-lookup"><span data-stu-id="a0f0c-165">VARIANT Type</span></span> |
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
