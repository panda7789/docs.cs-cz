---
title: Přizpůsobení zařazování struktury – .NET
description: Naučte se, jak přizpůsobit, jak .NET zařazování struktur do nativní reprezentace.
ms.date: 01/18/2019
dev_langs:
- csharp
- cpp
ms.openlocfilehash: c82e0099c44b8033cad241d69bdd284243711a50
ms.sourcegitcommit: e7748001b1cee80ced691d8a76ca814c0b02dd9b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/14/2020
ms.locfileid: "86374530"
---
# <a name="customize-structure-marshaling"></a><span data-ttu-id="922f2-103">Přizpůsobení zařazování struktur</span><span class="sxs-lookup"><span data-stu-id="922f2-103">Customize structure marshaling</span></span>

<span data-ttu-id="922f2-104">Někdy výchozí pravidla zařazování pro struktury nejsou přesně to, co potřebujete.</span><span class="sxs-lookup"><span data-stu-id="922f2-104">Sometimes the default marshaling rules for structures aren't exactly what you need.</span></span> <span data-ttu-id="922f2-105">Moduly runtime .NET poskytují několik rozšiřovacích bodů pro přizpůsobení rozložení struktury a způsobu, jakým jsou pole zařazena.</span><span class="sxs-lookup"><span data-stu-id="922f2-105">The .NET runtimes provide a few extension points for you to customize your structure's layout and how fields are marshaled.</span></span>

## <a name="customizing-structure-layout"></a><span data-ttu-id="922f2-106">Přizpůsobení rozložení struktury</span><span class="sxs-lookup"><span data-stu-id="922f2-106">Customizing structure layout</span></span>

<span data-ttu-id="922f2-107">Rozhraní .NET poskytuje <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=nameWithType> atribut a <xref:System.Runtime.InteropServices.LayoutKind?displayProperty=nameWithType> výčet, aby bylo možné přizpůsobit, jak jsou pole umístěna v paměti.</span><span class="sxs-lookup"><span data-stu-id="922f2-107">.NET provides the <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=nameWithType> attribute and the <xref:System.Runtime.InteropServices.LayoutKind?displayProperty=nameWithType> enumeration to allow you to customize how fields are placed in memory.</span></span> <span data-ttu-id="922f2-108">Následující pokyny vám pomůžou vyhnout se běžným problémům.</span><span class="sxs-lookup"><span data-stu-id="922f2-108">The following guidance will help you avoid common issues.</span></span>

<span data-ttu-id="922f2-109">✔️ ZVÁŽIT použití `LayoutKind.Sequential` , kdykoli je to možné.</span><span class="sxs-lookup"><span data-stu-id="922f2-109">✔️ CONSIDER using `LayoutKind.Sequential` whenever possible.</span></span>

<span data-ttu-id="922f2-110">✔️ použít pouze `LayoutKind.Explicit` v zařazování, pokud má nativní struktura také explicitní rozložení, jako je například sjednocení.</span><span class="sxs-lookup"><span data-stu-id="922f2-110">✔️ DO only use `LayoutKind.Explicit` in marshaling when your native struct also has an explicit layout, such as a union.</span></span>

<span data-ttu-id="922f2-111">❌Nepoužívejte `LayoutKind.Explicit` při zařazování struktur na platformách jiných než Windows, pokud potřebujete cílit na modul runtime před .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="922f2-111">❌ AVOID using `LayoutKind.Explicit` when marshaling structures on non-Windows platforms if you need to target runtimes before .NET Core 3.0.</span></span> <span data-ttu-id="922f2-112">Modul runtime .NET Core před 3,0 nepodporuje předávání explicitních struktur podle hodnot nativním funkcím na systémy, které nepoužívají procesory Intel nebo AMD 64.</span><span class="sxs-lookup"><span data-stu-id="922f2-112">The .NET Core runtime before 3.0 doesn't support passing explicit structures by value to native functions on Intel or AMD 64-bit non-Windows systems.</span></span> <span data-ttu-id="922f2-113">Modul runtime však podporuje předávání explicitních struktur odkazem na všechny platformy.</span><span class="sxs-lookup"><span data-stu-id="922f2-113">However, the runtime supports passing explicit structures by reference on all platforms.</span></span>

## <a name="customizing-boolean-field-marshaling"></a><span data-ttu-id="922f2-114">Přizpůsobení zařazování logických polí</span><span class="sxs-lookup"><span data-stu-id="922f2-114">Customizing boolean field marshaling</span></span>

<span data-ttu-id="922f2-115">Nativní kód má mnoho různých logických reprezentace.</span><span class="sxs-lookup"><span data-stu-id="922f2-115">Native code has many different boolean representations.</span></span> <span data-ttu-id="922f2-116">Pouze v systému Windows existují tři způsoby reprezentace logických hodnot.</span><span class="sxs-lookup"><span data-stu-id="922f2-116">On Windows alone, there are three ways to represent boolean values.</span></span> <span data-ttu-id="922f2-117">Běhový modul neví nativní definici struktury, takže to nejlepší je udělat, abyste se seznámili s tím, jak vaše logické hodnoty zařadit.</span><span class="sxs-lookup"><span data-stu-id="922f2-117">The runtime doesn't know the native definition of your structure, so the best it can do is make a guess on how to marshal your boolean values.</span></span> <span data-ttu-id="922f2-118">Modul runtime .NET poskytuje způsob, jak určit, jak zařadit vaše logické pole.</span><span class="sxs-lookup"><span data-stu-id="922f2-118">The .NET runtime provides a way to indicate how to marshal your boolean field.</span></span> <span data-ttu-id="922f2-119">Následující příklady ukazují, jak zařadit rozhraní .NET `bool` do různých nativních typů Boolean.</span><span class="sxs-lookup"><span data-stu-id="922f2-119">The following examples show how to marshal .NET `bool` to different native boolean types.</span></span>

<span data-ttu-id="922f2-120">Logické hodnoty jsou ve výchozím nastavení zařazování jako nativní hodnota 4 bajtů, [`BOOL`](/windows/desktop/winprog/windows-data-types#BOOL) jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="922f2-120">Boolean values default to marshaling as a native 4-byte Win32 [`BOOL`](/windows/desktop/winprog/windows-data-types#BOOL) value as shown in the following example:</span></span>

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

<span data-ttu-id="922f2-121">Pokud chcete být explicitní, můžete použít <xref:System.Runtime.InteropServices.UnmanagedType.Bool?displayProperty=nameWithType> hodnotu k získání stejného chování jako v předchozích krocích:</span><span class="sxs-lookup"><span data-stu-id="922f2-121">If you want to be explicit, you can use the <xref:System.Runtime.InteropServices.UnmanagedType.Bool?displayProperty=nameWithType> value to get the same behavior as above:</span></span>

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

<span data-ttu-id="922f2-122">Pomocí `UnmanagedType.U1` `UnmanagedType.I1` níže uvedených hodnot nebo můžete určit, že modul runtime bude zařazovat `b` pole jako nativní typ 1 bajt `bool` .</span><span class="sxs-lookup"><span data-stu-id="922f2-122">Using the `UnmanagedType.U1` or `UnmanagedType.I1` values below, you can tell the runtime to marshal the `b` field as a 1-byte native `bool` type.</span></span>

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

<span data-ttu-id="922f2-123">Ve Windows můžete použít <xref:System.Runtime.InteropServices.UnmanagedType.VariantBool?displayProperty=nameWithType> hodnotu k oznámení, že modul runtime zařadí vaši logickou hodnotu do hodnoty 2 bajty `VARIANT_BOOL` :</span><span class="sxs-lookup"><span data-stu-id="922f2-123">On Windows, you can use the <xref:System.Runtime.InteropServices.UnmanagedType.VariantBool?displayProperty=nameWithType> value to tell the runtime to marshal your boolean value to a 2-byte `VARIANT_BOOL` value:</span></span>

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
> <span data-ttu-id="922f2-124">`VARIANT_BOOL`se liší od většiny typů bool v tomto `VARIANT_TRUE = -1` a `VARIANT_FALSE = 0` .</span><span class="sxs-lookup"><span data-stu-id="922f2-124">`VARIANT_BOOL` is different than most bool types in that `VARIANT_TRUE = -1` and `VARIANT_FALSE = 0`.</span></span> <span data-ttu-id="922f2-125">Kromě toho všechny hodnoty, které nejsou rovny, `VARIANT_TRUE` jsou považovány za NEPRAVDA.</span><span class="sxs-lookup"><span data-stu-id="922f2-125">Additionally, all values that aren't equal to `VARIANT_TRUE` are considered false.</span></span>

## <a name="customizing-array-field-marshaling"></a><span data-ttu-id="922f2-126">Přizpůsobení zařazování polí pole</span><span class="sxs-lookup"><span data-stu-id="922f2-126">Customizing array field marshaling</span></span>

<span data-ttu-id="922f2-127">Rozhraní .NET také obsahuje několik způsobů, jak přizpůsobit zařazování pole.</span><span class="sxs-lookup"><span data-stu-id="922f2-127">.NET also includes a few ways to customize array marshaling.</span></span>

<span data-ttu-id="922f2-128">Ve výchozím nastavení rozhraní .NET zařazuje pole jako ukazatel na souvislý seznam elementů:</span><span class="sxs-lookup"><span data-stu-id="922f2-128">By default, .NET marshals arrays as a pointer to a contiguous list of the elements:</span></span>

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

<span data-ttu-id="922f2-129">Pokud pracujete s rozhraními API modelu COM, možná budete muset zařadit pole jako `SAFEARRAY*` objekty.</span><span class="sxs-lookup"><span data-stu-id="922f2-129">If you're interfacing with COM APIs, you may have to marshal arrays as `SAFEARRAY*` objects.</span></span> <span data-ttu-id="922f2-130">Hodnotu a můžete použít <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> <xref:System.Runtime.InteropServices.UnmanagedType.SafeArray?displayProperty=nameWithType> k oznámení, že modul runtime zařadí pole jako `SAFEARRAY*` :</span><span class="sxs-lookup"><span data-stu-id="922f2-130">You can use the <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> and the <xref:System.Runtime.InteropServices.UnmanagedType.SafeArray?displayProperty=nameWithType> value to tell the runtime to marshal an array as a `SAFEARRAY*`:</span></span>

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

<span data-ttu-id="922f2-131">Pokud potřebujete přizpůsobit, jaký typ prvku je v `SAFEARRAY` , pak můžete použít <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArraySubType?displayProperty=nameWithType> <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArrayUserDefinedSubType?displayProperty=nameWithType> pole a k přizpůsobení přesného typu prvku `SAFEARRAY` .</span><span class="sxs-lookup"><span data-stu-id="922f2-131">If you need to customize what type of element is in the `SAFEARRAY`, then you can use the <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArraySubType?displayProperty=nameWithType> and <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArrayUserDefinedSubType?displayProperty=nameWithType> fields to customize the exact element type of the `SAFEARRAY`.</span></span>

<span data-ttu-id="922f2-132">Pokud je nutné zařadit pole na místě, můžete použít <xref:System.Runtime.InteropServices.UnmanagedType.ByValArray?displayProperty=nameWithType> hodnotu k oznámení zařazovacímu modulu k zařazení pole na místě.</span><span class="sxs-lookup"><span data-stu-id="922f2-132">If you need to marshal the array in-place, you can use the <xref:System.Runtime.InteropServices.UnmanagedType.ByValArray?displayProperty=nameWithType> value to tell the marshaler to marshal the array in-place.</span></span> <span data-ttu-id="922f2-133">Při použití tohoto zařazování musíte také zadat hodnotu do <xref:System.Runtime.InteropServices.MarshalAsAttribute.SizeConst?displayProperty=nameWithType> pole pro počet prvků v poli, aby modul runtime mohl správně přidělit prostor pro strukturu.</span><span class="sxs-lookup"><span data-stu-id="922f2-133">When you're using this marshaling, you also must supply a value to the <xref:System.Runtime.InteropServices.MarshalAsAttribute.SizeConst?displayProperty=nameWithType> field  for the number of elements in the array so the runtime can correctly allocate space for the structure.</span></span>

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
> <span data-ttu-id="922f2-134">Rozhraní .NET nepodporuje zařazování pole proměnné délky jako C99 flexibilního člena pole.</span><span class="sxs-lookup"><span data-stu-id="922f2-134">.NET doesn't support marshaling a variable length array field as a C99 Flexible Array Member.</span></span>

## <a name="customizing-string-field-marshaling"></a><span data-ttu-id="922f2-135">Přizpůsobení zařazování polí řetězců</span><span class="sxs-lookup"><span data-stu-id="922f2-135">Customizing string field marshaling</span></span>

<span data-ttu-id="922f2-136">Rozhraní .NET také poskytuje širokou škálu přizpůsobení pro zařazování polí řetězců.</span><span class="sxs-lookup"><span data-stu-id="922f2-136">.NET also provides a wide variety of customizations for marshaling string fields.</span></span>

<span data-ttu-id="922f2-137">Ve výchozím nastavení .NET zařazování řetězce jako ukazatele na řetězec zakončený hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="922f2-137">By default, .NET marshals a string as a pointer to a null-terminated string.</span></span> <span data-ttu-id="922f2-138">Kódování závisí na hodnotě <xref:System.Runtime.InteropServices.StructLayoutAttribute.CharSet?displayProperty=nameWithType> pole v <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="922f2-138">The encoding depends on the value of the <xref:System.Runtime.InteropServices.StructLayoutAttribute.CharSet?displayProperty=nameWithType> field in the <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=nameWithType>.</span></span> <span data-ttu-id="922f2-139">Pokud není zadán žádný atribut, kódování je standardně kódování ANSI.</span><span class="sxs-lookup"><span data-stu-id="922f2-139">If no attribute is specified, the encoding defaults to an ANSI encoding.</span></span>

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

<span data-ttu-id="922f2-140">Pokud potřebujete použít různá kódování pro různá pole nebo pouze preferovat explicitní použití v definici struktury, můžete použít <xref:System.Runtime.InteropServices.UnmanagedType.LPStr?displayProperty=nameWithType> <xref:System.Runtime.InteropServices.UnmanagedType.LPWStr?displayProperty=nameWithType> hodnoty nebo v <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> atributu.</span><span class="sxs-lookup"><span data-stu-id="922f2-140">If you need to use different encodings for different fields or just prefer to be more explicit in your struct definition, you can use the <xref:System.Runtime.InteropServices.UnmanagedType.LPStr?displayProperty=nameWithType> or <xref:System.Runtime.InteropServices.UnmanagedType.LPWStr?displayProperty=nameWithType> values on a <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> attribute.</span></span>

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

<span data-ttu-id="922f2-141">Chcete-li zařadit řetězce pomocí kódování UTF-8, můžete použít <xref:System.Runtime.InteropServices.UnmanagedType.LPUTF8Str?displayProperty=nameWithType> hodnotu v <xref:System.Runtime.InteropServices.MarshalAsAttribute> .</span><span class="sxs-lookup"><span data-stu-id="922f2-141">If you want to marshal your strings using the UTF-8 encoding, you can use the <xref:System.Runtime.InteropServices.UnmanagedType.LPUTF8Str?displayProperty=nameWithType> value in your <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span></span>

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
> <span data-ttu-id="922f2-142">Použití <xref:System.Runtime.InteropServices.UnmanagedType.LPUTF8Str?displayProperty=nameWithType> vyžaduje buď .NET Framework 4,7 (nebo novější verze), nebo .NET Core 1,1 (nebo novější verze).</span><span class="sxs-lookup"><span data-stu-id="922f2-142">Using <xref:System.Runtime.InteropServices.UnmanagedType.LPUTF8Str?displayProperty=nameWithType> requires either .NET Framework 4.7 (or later versions) or .NET Core 1.1 (or later versions).</span></span> <span data-ttu-id="922f2-143">Není k dispozici v .NET Standard 2,0.</span><span class="sxs-lookup"><span data-stu-id="922f2-143">It isn't available in .NET Standard 2.0.</span></span>

<span data-ttu-id="922f2-144">Pokud pracujete s rozhraními API modelu COM, může být nutné zařadit řetězec jako `BSTR` .</span><span class="sxs-lookup"><span data-stu-id="922f2-144">If you're working with COM APIs, you may need to marshal a string as a `BSTR`.</span></span> <span data-ttu-id="922f2-145">Pomocí <xref:System.Runtime.InteropServices.UnmanagedType.BStr?displayProperty=nameWithType> hodnoty můžete zařadit řetězec jako `BSTR` .</span><span class="sxs-lookup"><span data-stu-id="922f2-145">Using the <xref:System.Runtime.InteropServices.UnmanagedType.BStr?displayProperty=nameWithType> value, you can marshal a string as a `BSTR`.</span></span>

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

<span data-ttu-id="922f2-146">Při použití rozhraní API založeného na WinRT může být nutné zařadit řetězec jako `HSTRING` .</span><span class="sxs-lookup"><span data-stu-id="922f2-146">When using a WinRT-based API, you may need to marshal a string as an `HSTRING`.</span></span> <span data-ttu-id="922f2-147">Pomocí <xref:System.Runtime.InteropServices.UnmanagedType.HString?displayProperty=nameWithType> hodnoty můžete zařadit řetězec jako `HSTRING` .</span><span class="sxs-lookup"><span data-stu-id="922f2-147">Using the <xref:System.Runtime.InteropServices.UnmanagedType.HString?displayProperty=nameWithType> value, you can marshal a string as a `HSTRING`.</span></span>

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

<span data-ttu-id="922f2-148">Pokud vaše rozhraní API vyžaduje předání řetězce na místě ve struktuře, můžete použít <xref:System.Runtime.InteropServices.UnmanagedType.ByValTStr?displayProperty=nameWithType> hodnotu.</span><span class="sxs-lookup"><span data-stu-id="922f2-148">If your API requires you to pass the string in-place in the structure, you can use the <xref:System.Runtime.InteropServices.UnmanagedType.ByValTStr?displayProperty=nameWithType> value.</span></span> <span data-ttu-id="922f2-149">Všimněte si, že kódování pro řetězec zařazování `ByValTStr` je určeno z `CharSet` atributu.</span><span class="sxs-lookup"><span data-stu-id="922f2-149">Do note that the encoding for a string marshaled by `ByValTStr` is determined from the `CharSet` attribute.</span></span> <span data-ttu-id="922f2-150">Kromě toho vyžaduje, aby pole předalo délku řetězce <xref:System.Runtime.InteropServices.MarshalAsAttribute.SizeConst?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="922f2-150">Additionally, it requires that a string length is passed by the <xref:System.Runtime.InteropServices.MarshalAsAttribute.SizeConst?displayProperty=nameWithType> field.</span></span>

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

## <a name="customizing-decimal-field-marshaling"></a><span data-ttu-id="922f2-151">Přizpůsobení zařazování desetinných polí</span><span class="sxs-lookup"><span data-stu-id="922f2-151">Customizing decimal field marshaling</span></span>

<span data-ttu-id="922f2-152">Pokud pracujete v systému Windows, můžete se setkat s některými rozhraními API, která používají nativní [ `CY` nebo `CURRENCY` ](/windows/win32/api/wtypes/ns-wtypes-cy-r1) strukturu.</span><span class="sxs-lookup"><span data-stu-id="922f2-152">If you're working on Windows, you might encounter some APIs that use the native [`CY` or `CURRENCY`](/windows/win32/api/wtypes/ns-wtypes-cy-r1) structure.</span></span> <span data-ttu-id="922f2-153">Ve výchozím nastavení je `decimal` typ .NET zařazování do nativní [`DECIMAL`](/windows/win32/api/wtypes/ns-wtypes-decimal-r1) struktury.</span><span class="sxs-lookup"><span data-stu-id="922f2-153">By default, the .NET `decimal` type marshals to the native [`DECIMAL`](/windows/win32/api/wtypes/ns-wtypes-decimal-r1) structure.</span></span> <span data-ttu-id="922f2-154">Můžete však použít <xref:System.Runtime.InteropServices.MarshalAsAttribute> s <xref:System.Runtime.InteropServices.UnmanagedType.Currency?displayProperty=nameWithType> hodnotou k instruování zařazovacího modulu, aby převedl `decimal` hodnotu na nativní `CY` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="922f2-154">However, you can use a <xref:System.Runtime.InteropServices.MarshalAsAttribute> with the <xref:System.Runtime.InteropServices.UnmanagedType.Currency?displayProperty=nameWithType> value to instruct the marshaler to convert a `decimal` value to a native `CY` value.</span></span>

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

## <a name="marshal-systemobject"></a><span data-ttu-id="922f2-155">Sdružení`System.Object`</span><span class="sxs-lookup"><span data-stu-id="922f2-155">Marshal `System.Object`</span></span>

<span data-ttu-id="922f2-156">Ve Windows můžete zařadit `object` pole typu do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="922f2-156">On Windows, you can marshal `object`-typed fields to native code.</span></span> <span data-ttu-id="922f2-157">Tato pole můžete zařadit do jednoho ze tří typů:</span><span class="sxs-lookup"><span data-stu-id="922f2-157">You can marshal these fields to one of three types:</span></span>

- [`VARIANT`](/windows/win32/api/oaidl/ns-oaidl-variant)
- [`IUnknown*`](/windows/desktop/api/unknwn/nn-unknwn-iunknown)
- [`IDispatch*`](/windows/desktop/api/oaidl/nn-oaidl-idispatch)

<span data-ttu-id="922f2-158">Ve výchozím nastavení `object` bude pole typového typu zařazeno do `IUnknown*` objektu, který tento objekt zabalí.</span><span class="sxs-lookup"><span data-stu-id="922f2-158">By default, an `object`-typed field will be marshaled to an `IUnknown*` that wraps the object.</span></span>

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

<span data-ttu-id="922f2-159">Chcete-li zařadit pole objektu do objektu `IDispatch*` , přidejte <xref:System.Runtime.InteropServices.MarshalAsAttribute> s <xref:System.Runtime.InteropServices.UnmanagedType.IDispatch?displayProperty=nameWithType> hodnotou.</span><span class="sxs-lookup"><span data-stu-id="922f2-159">If you want to marshal an object field to an `IDispatch*`, add a <xref:System.Runtime.InteropServices.MarshalAsAttribute> with the <xref:System.Runtime.InteropServices.UnmanagedType.IDispatch?displayProperty=nameWithType> value.</span></span>

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

<span data-ttu-id="922f2-160">Pokud ho chcete zařadit jako a `VARIANT` , přidejte <xref:System.Runtime.InteropServices.MarshalAsAttribute> s <xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType> hodnotou.</span><span class="sxs-lookup"><span data-stu-id="922f2-160">If you want to marshal it as a `VARIANT`, add a <xref:System.Runtime.InteropServices.MarshalAsAttribute> with the <xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType> value.</span></span>

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

<span data-ttu-id="922f2-161">Následující tabulka popisuje, jak jsou různé typy modulu runtime `obj` mapovány na různé typy uložené v poli `VARIANT` :</span><span class="sxs-lookup"><span data-stu-id="922f2-161">The following table describes how different runtime types of the `obj` field map to the various types stored in a `VARIANT`:</span></span>

| <span data-ttu-id="922f2-162">Typ .NET</span><span class="sxs-lookup"><span data-stu-id="922f2-162">.NET Type</span></span> | <span data-ttu-id="922f2-163">Typ VARIANT</span><span class="sxs-lookup"><span data-stu-id="922f2-163">VARIANT Type</span></span> | | <span data-ttu-id="922f2-164">Typ .NET</span><span class="sxs-lookup"><span data-stu-id="922f2-164">.NET Type</span></span> | <span data-ttu-id="922f2-165">Typ VARIANT</span><span class="sxs-lookup"><span data-stu-id="922f2-165">VARIANT Type</span></span> |
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
