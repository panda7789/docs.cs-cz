---
title: Přizpůsobení struktury zařazování – .NET
description: Zjistěte, jak přizpůsobit, jak .NET zařazuje struktury na nativní reprezentaci.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/18/2019
dev_langs:
- csharp
- cpp
ms.openlocfilehash: b07851a0d26f5bfe7edc2115d7276a8e96ba0917
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59101325"
---
# <a name="customizing-structure-marshalling"></a><span data-ttu-id="02650-103">Přizpůsobení zařazování pro struktury</span><span class="sxs-lookup"><span data-stu-id="02650-103">Customizing structure marshalling</span></span>

<span data-ttu-id="02650-104">Někdy sběrného systému výchozí pravidla pro struktury nejsou přesně, co potřebujete.</span><span class="sxs-lookup"><span data-stu-id="02650-104">Sometimes the default marshalling rules for structures aren't exactly what you need.</span></span> <span data-ttu-id="02650-105">Moduly runtime .NET poskytují několik Rozšiřovací body můžete přizpůsobit rozvržení struktury vaší a jak zařadit pole.</span><span class="sxs-lookup"><span data-stu-id="02650-105">The .NET runtimes provide a few extension points for you to customize your structure's layout and how fields are marshaled.</span></span>

## <a name="customizing-structure-layout"></a><span data-ttu-id="02650-106">Přizpůsobení rozložení struktury</span><span class="sxs-lookup"><span data-stu-id="02650-106">Customizing structure layout</span></span>

<span data-ttu-id="02650-107">Poskytuje rozhraní .NET <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=nameWithType> atribut a <xref:System.Runtime.InteropServices.LayoutKind?displayProperty=nameWithType> výčet, aby bylo možné přizpůsobit, jak jsou pole umístěné v paměti.</span><span class="sxs-lookup"><span data-stu-id="02650-107">.NET provides the <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=nameWithType> attribute and the <xref:System.Runtime.InteropServices.LayoutKind?displayProperty=nameWithType> enumeration to allow you to customize how fields are placed in memory.</span></span> <span data-ttu-id="02650-108">Následující pokyny se snáze vyhnete běžných problémů.</span><span class="sxs-lookup"><span data-stu-id="02650-108">The following guidance will help you avoid common issues.</span></span>

<span data-ttu-id="02650-109">**✔️ ZVAŽTE** pomocí `LayoutKind.Sequential` kdykoli je to možné.</span><span class="sxs-lookup"><span data-stu-id="02650-109">**✔️ CONSIDER** using `LayoutKind.Sequential` whenever possible.</span></span>

<span data-ttu-id="02650-110">**PROVEĎTE ✔️** používat pouze `LayoutKind.Explicit` v zařazení při nativní struktury je také má explicitní rozložení, jako je například sjednocení.</span><span class="sxs-lookup"><span data-stu-id="02650-110">**✔️ DO** only use `LayoutKind.Explicit` in marshalling when your native struct is also has an explicit layout, such as a union.</span></span>

<span data-ttu-id="02650-111">**❌ Nepoužívejte** pomocí `LayoutKind.Explicit` při zařazování pro struktury na platformách než Windows.</span><span class="sxs-lookup"><span data-stu-id="02650-111">**❌ AVOID** using `LayoutKind.Explicit` when marshalling structures on non-Windows platforms.</span></span> <span data-ttu-id="02650-112">Modul runtime .NET Core nepodporuje explicitní struktury předání hodnotou na nativní funkce v systémech než Windows Intel nebo AMD 64-bit.</span><span class="sxs-lookup"><span data-stu-id="02650-112">The .NET Core runtime doesn't support passing explicit structures by value to native functions on Intel or AMD 64-bit non-Windows systems.</span></span> <span data-ttu-id="02650-113">Modul runtime však podporuje struktury, předávání explicitní odkaz na všech platformách.</span><span class="sxs-lookup"><span data-stu-id="02650-113">However, the runtime supports passing explicit structures by reference on all platforms.</span></span>

## <a name="customizing-boolean-field-marshalling"></a><span data-ttu-id="02650-114">Přizpůsobení zařazování pro logické pole</span><span class="sxs-lookup"><span data-stu-id="02650-114">Customizing boolean field marshalling</span></span>

<span data-ttu-id="02650-115">Nativní kód má mnoho různých logický reprezentací.</span><span class="sxs-lookup"><span data-stu-id="02650-115">Native code has many different boolean representations.</span></span> <span data-ttu-id="02650-116">Na Windows samostatně existují tři způsoby, jak reprezentaci logické hodnoty.</span><span class="sxs-lookup"><span data-stu-id="02650-116">On Windows alone, there are three ways to represent boolean values.</span></span> <span data-ttu-id="02650-117">Modul runtime nebude vědět nativní definice struktury, proto je nejlepší, co můžete dělat hádat o tom, jak zařadit logické hodnoty.</span><span class="sxs-lookup"><span data-stu-id="02650-117">The runtime doesn't know the native definition of your structure, so the best it can do is make a guess on how to marshal your boolean values.</span></span> <span data-ttu-id="02650-118">Modul .NET runtime poskytuje způsob, jak určují, jak zařadit logická pole.</span><span class="sxs-lookup"><span data-stu-id="02650-118">The .NET runtime provides a way to indicate how to marshal your boolean field.</span></span> <span data-ttu-id="02650-119">Následující příklady ukazují, jak zařadit .NET `bool` do různých nativních typů boolean.</span><span class="sxs-lookup"><span data-stu-id="02650-119">The following examples show how to marshal .NET `bool` to different native boolean types.</span></span>

<span data-ttu-id="02650-120">Výchozí zařazování pro jako nativní 4bajtový Win32 hodnoty logická hodnota [ `BOOL` ](/windows/desktop/winprog/windows-data-types#BOOL) hodnoty, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="02650-120">Boolean values default to marshalling as a native 4-byte Win32 [`BOOL`](/windows/desktop/winprog/windows-data-types#BOOL) value as shown in the following example:</span></span>

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

<span data-ttu-id="02650-121">Pokud chcete explicitně, můžete použít <xref:System.Runtime.InteropServices.UnmanagedType.Bool?displayProperty=nameWithType> hodnota, která má stejné chování, jak je uvedeno výše:</span><span class="sxs-lookup"><span data-stu-id="02650-121">If you want to be explicit, you can use the <xref:System.Runtime.InteropServices.UnmanagedType.Bool?displayProperty=nameWithType> value to get the same behavior as above:</span></span>

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

<span data-ttu-id="02650-122">Použití `UnmanagedType.U1` nebo `UnmanagedType.I1` níže uvedených hodnot, poznáte, modul runtime k zařazování `b` pole 1bajtových nativní `bool` typu.</span><span class="sxs-lookup"><span data-stu-id="02650-122">Using the `UnmanagedType.U1` or `UnmanagedType.I1` values below, you can tell the runtime to marshal the `b` field as a 1-byte native `bool` type.</span></span>

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

<span data-ttu-id="02650-123">Na Windows, můžete použít <xref:System.Runtime.InteropServices.UnmanagedType.VariantBool?displayProperty=nameWithType> hodnotu říct runtime k zařazení vaší logickou hodnotu k 2 bajtů `VARIANT_BOOL` hodnotu:</span><span class="sxs-lookup"><span data-stu-id="02650-123">On Windows, you can use the <xref:System.Runtime.InteropServices.UnmanagedType.VariantBool?displayProperty=nameWithType> value to tell the runtime to marshal your boolean value to a 2-byte `VARIANT_BOOL` value:</span></span>

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
> <span data-ttu-id="02650-124">`VARIANT_BOOL` se liší od většinu typů bool v dané `VARIANT_TRUE = -1` a `VARIANT_FALSE = 0`.</span><span class="sxs-lookup"><span data-stu-id="02650-124">`VARIANT_BOOL` is different than most bool types in that `VARIANT_TRUE = -1` and `VARIANT_FALSE = 0`.</span></span> <span data-ttu-id="02650-125">Kromě toho všechny hodnoty, které se rovná `VARIANT_TRUE` jsou považovány za hodnotu false.</span><span class="sxs-lookup"><span data-stu-id="02650-125">Additionally, all values that aren't equal to `VARIANT_TRUE` are considered false.</span></span>

## <a name="customizing-array-field-marshalling"></a><span data-ttu-id="02650-126">Přizpůsobení zařazování pro pole pole</span><span class="sxs-lookup"><span data-stu-id="02650-126">Customizing array field marshalling</span></span>

<span data-ttu-id="02650-127">.NET zahrnuje také několik způsobů, jak přizpůsobit zařazování pro pole.</span><span class="sxs-lookup"><span data-stu-id="02650-127">.NET also includes a few ways to customize array marshalling.</span></span>

<span data-ttu-id="02650-128">Ve výchozím nastavení zařazuje .NET pole jako ukazatel na seznam souvislých prvků:</span><span class="sxs-lookup"><span data-stu-id="02650-128">By default, .NET marshals arrays as a pointer to a contiguous list of the elements:</span></span>

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

<span data-ttu-id="02650-129">Pokud se propojení s rozhraními API modelu COM, bude pravděpodobně nutné zařazování pole jako `SAFEARRAY*` objekty.</span><span class="sxs-lookup"><span data-stu-id="02650-129">If you're interfacing with COM APIs, you may have to marshal arrays as `SAFEARRAY*` objects.</span></span> <span data-ttu-id="02650-130">Můžete použít <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> a <xref:System.Runtime.InteropServices.UnmanagedType.SafeArray?displayProperty=nameWithType> říct runtime k zařazování pole jako hodnotu `SAFEARRAY*`:</span><span class="sxs-lookup"><span data-stu-id="02650-130">You can use the <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> and the <xref:System.Runtime.InteropServices.UnmanagedType.SafeArray?displayProperty=nameWithType> value to tell the runtime to marshal an array as a `SAFEARRAY*`:</span></span>

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

<span data-ttu-id="02650-131">Pokud chcete přizpůsobit, jaký typ prvku je v `SAFEARRAY`, můžete použít <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArraySubType?displayProperty=nameWithType> a <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArrayUserDefinedSubType?displayProperty=nameWithType> polí pro přizpůsobení elementu přesný typ `SAFEARRAY`.</span><span class="sxs-lookup"><span data-stu-id="02650-131">If you need to customize what type of element is in the `SAFEARRAY`, then you can use the <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArraySubType?displayProperty=nameWithType> and <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArrayUserDefinedSubType?displayProperty=nameWithType> fields to customize the exact element type of the `SAFEARRAY`.</span></span>

<span data-ttu-id="02650-132">Pokud potřebujete pole na místě, můžete použít <xref:System.Runtime.InteropServices.UnmanagedType.ByValArray?displayProperty=nameWithType> hodnotu říct, aby zařazování odvozovalo zařazování pole na místě.</span><span class="sxs-lookup"><span data-stu-id="02650-132">If you need to marshal the array in-place, you can use the <xref:System.Runtime.InteropServices.UnmanagedType.ByValArray?displayProperty=nameWithType> value to tell the marshaler to marshal the array in-place.</span></span> <span data-ttu-id="02650-133">Při použití této zařazování, můžete také musíte zadat hodnotu, která <xref:System.Runtime.InteropServices.MarshalAsAttribute.SizeConst?displayProperty=nameWithType> pole pro počet prvků v poli, aby modul runtime může správně přidělit místo pro strukturu.</span><span class="sxs-lookup"><span data-stu-id="02650-133">When you're using this marshalling, you also must supply a value to the <xref:System.Runtime.InteropServices.MarshalAsAttribute.SizeConst?displayProperty=nameWithType> field  for the number of elements in the array so the runtime can correctly allocate space for the structure.</span></span>

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
> <span data-ttu-id="02650-134">.NET nepodporuje zařazování pro pole s proměnnou délkou pole jako člena flexibilního pole C99.</span><span class="sxs-lookup"><span data-stu-id="02650-134">.NET doesn't support marshalling a variable length array field as a C99 Flexible Array Member.</span></span>

## <a name="customizing-string-field-marshalling"></a><span data-ttu-id="02650-135">Přizpůsobení zařazování pro pole řetězce</span><span class="sxs-lookup"><span data-stu-id="02650-135">Customizing string field marshalling</span></span>

<span data-ttu-id="02650-136">.NET také poskytuje širokou škálu vlastní nastavení pro zařazování pro pole řetězců.</span><span class="sxs-lookup"><span data-stu-id="02650-136">.NET also provides a wide variety of customizations for marshalling string fields.</span></span>

<span data-ttu-id="02650-137">Ve výchozím nastavení zařazuje .NET řetězec jako ukazatel na řetězec zakončený hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="02650-137">By default, .NET marshals a string as a pointer to a null-terminated string.</span></span> <span data-ttu-id="02650-138">Kódování závisí na hodnotě <xref:System.Runtime.InteropServices.StructLayoutAttribute.CharSet?displayProperty=nameWithType> pole <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="02650-138">The encoding depends on the value of the <xref:System.Runtime.InteropServices.StructLayoutAttribute.CharSet?displayProperty=nameWithType> field in the <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=nameWithType>.</span></span> <span data-ttu-id="02650-139">Pokud není zadán žádný atribut, kódování, výchozí kódování ANSI.</span><span class="sxs-lookup"><span data-stu-id="02650-139">If no attribute is specified, the encoding defaults to an ANSI encoding.</span></span>

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

<span data-ttu-id="02650-140">Pokud budete muset použít jiné kódování pro různá pole nebo jen dáváte přednost více explicitně v definici struktury, můžete použít <xref:System.Runtime.InteropServices.UnmanagedType.LPStr?displayProperty=nameWithType> nebo <xref:System.Runtime.InteropServices.UnmanagedType.LPWStr?displayProperty=nameWithType> hodnoty na <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> atribut.</span><span class="sxs-lookup"><span data-stu-id="02650-140">If you need to use different encodings for different fields or just prefer to be more explicit in your struct definition, you can use the <xref:System.Runtime.InteropServices.UnmanagedType.LPStr?displayProperty=nameWithType> or <xref:System.Runtime.InteropServices.UnmanagedType.LPWStr?displayProperty=nameWithType> values on a <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> attribute.</span></span>

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

<span data-ttu-id="02650-141">Pokud chcete k zařazení vaší řetězce s kódováním UTF-8, můžete použít <xref:System.Runtime.InteropServices.UnmanagedType.LPUTF8Str?displayProperty=nameWithType> hodnota ve vaší <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span><span class="sxs-lookup"><span data-stu-id="02650-141">If you want to marshal your strings using the UTF-8 encoding, you can use the <xref:System.Runtime.InteropServices.UnmanagedType.LPUTF8Str?displayProperty=nameWithType> value in your <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span></span>

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
> <span data-ttu-id="02650-142">Pomocí <xref:System.Runtime.InteropServices.UnmanagedType.LPUTF8Str?displayProperty=nameWithType> vyžaduje rozhraní .NET Framework 4.7 (nebo novější verze) nebo .NET Core 1.1 (nebo novější verze).</span><span class="sxs-lookup"><span data-stu-id="02650-142">Using <xref:System.Runtime.InteropServices.UnmanagedType.LPUTF8Str?displayProperty=nameWithType> requires either .NET Framework 4.7 (or later versions) or .NET Core 1.1 (or later versions).</span></span> <span data-ttu-id="02650-143">Není k dispozici v rozhraní .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="02650-143">It isn't available in .NET Standard 2.0.</span></span>

<span data-ttu-id="02650-144">Pokud pracujete s rozhraními API modelu COM, budete muset řetězec jako `BSTR`.</span><span class="sxs-lookup"><span data-stu-id="02650-144">If you're working with COM APIs, you may need to marshal a string as a `BSTR`.</span></span> <span data-ttu-id="02650-145">Použití <xref:System.Runtime.InteropServices.UnmanagedType.BStr?displayProperty=nameWithType> hodnota, které by mohl zařazovat řetězec jako `BSTR`.</span><span class="sxs-lookup"><span data-stu-id="02650-145">Using the <xref:System.Runtime.InteropServices.UnmanagedType.BStr?displayProperty=nameWithType> value, you can marshal a string as a `BSTR`.</span></span>

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

<span data-ttu-id="02650-146">Při použití rozhraní API založené na WinRT, budete muset řetězec jako `HSTRING`.</span><span class="sxs-lookup"><span data-stu-id="02650-146">When using a WinRT-based API, you may need to marshal a string as an `HSTRING`.</span></span>  <span data-ttu-id="02650-147">Použití <xref:System.Runtime.InteropServices.UnmanagedType.HString?displayProperty=nameWithType> hodnota, které by mohl zařazovat řetězec jako `HSTRING`.</span><span class="sxs-lookup"><span data-stu-id="02650-147">Using the <xref:System.Runtime.InteropServices.UnmanagedType.HString?displayProperty=nameWithType> value, you can marshal a string as a `HSTRING`.</span></span>

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

<span data-ttu-id="02650-148">Pokud vaše rozhraní API vyžaduje, abyste ve struktuře předat řetězec v místě, můžete použít <xref:System.Runtime.InteropServices.UnmanagedType.ByValTStr?displayProperty=nameWithType> hodnotu.</span><span class="sxs-lookup"><span data-stu-id="02650-148">If your API requires you to pass the string in-place in the structure, you can use the <xref:System.Runtime.InteropServices.UnmanagedType.ByValTStr?displayProperty=nameWithType> value.</span></span> <span data-ttu-id="02650-149">Všimněte si, že kódování pro řetězce zařazeno ve `ByValTStr` se určí na základě `CharSet` atribut.</span><span class="sxs-lookup"><span data-stu-id="02650-149">Do note that the encoding for a string marshalled by `ByValTStr` is determined from the `CharSet` attribute.</span></span> <span data-ttu-id="02650-150">Navíc se vyžaduje, aby délka řetězce je předaný odkazem <xref:System.Runtime.InteropServices.MarshalAsAttribute.SizeConst?displayProperty=nameWithType> pole.</span><span class="sxs-lookup"><span data-stu-id="02650-150">Additionally, it requires that a string length is passed by the <xref:System.Runtime.InteropServices.MarshalAsAttribute.SizeConst?displayProperty=nameWithType> field.</span></span>

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

## <a name="customizing-decimal-field-marshalling"></a><span data-ttu-id="02650-151">Přizpůsobení zařazování desítkové pole</span><span class="sxs-lookup"><span data-stu-id="02650-151">Customizing decimal field marshalling</span></span>

<span data-ttu-id="02650-152">Pokud pracujete ve Windows, může dojít některá rozhraní API, použít nativní [ `CY` nebo `CURRENCY` ](/windows/desktop/api/wtypes/ns-wtypes-tagcy) struktury.</span><span class="sxs-lookup"><span data-stu-id="02650-152">If you're working on Windows, you might encounter some APIs that use the native [`CY` or `CURRENCY`](/windows/desktop/api/wtypes/ns-wtypes-tagcy) structure.</span></span> <span data-ttu-id="02650-153">Ve výchozím nastavení, .NET `decimal` zadejte marshals na nativní [ `DECIMAL` ](/windows/desktop/api/wtypes/ns-wtypes-tagdec) struktury.</span><span class="sxs-lookup"><span data-stu-id="02650-153">By default, the .NET `decimal` type marshals to the native [`DECIMAL`](/windows/desktop/api/wtypes/ns-wtypes-tagdec) structure.</span></span> <span data-ttu-id="02650-154">Však můžete použít <xref:System.Runtime.InteropServices.MarshalAsAttribute> s <xref:System.Runtime.InteropServices.UnmanagedType.Currency?displayProperty=nameWithType> hodnotu dáte pokyn, aby zařazování pro převod `decimal` hodnotu na nativní `CY` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="02650-154">However, you can use a <xref:System.Runtime.InteropServices.MarshalAsAttribute> with the <xref:System.Runtime.InteropServices.UnmanagedType.Currency?displayProperty=nameWithType> value to instruct the marshaler to convert a `decimal` value to a native `CY` value.</span></span>

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

## <a name="marshalling-systemobjects"></a><span data-ttu-id="02650-155">Zařazování `System.Object`s</span><span class="sxs-lookup"><span data-stu-id="02650-155">Marshalling `System.Object`s</span></span>

<span data-ttu-id="02650-156">Na Windows, které by mohl zařazovat `object`– zadané pole do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="02650-156">On Windows, you can marshal `object`-typed fields to native code.</span></span> <span data-ttu-id="02650-157">By mohl zařazovat těchto polí do jednoho ze tří typů:</span><span class="sxs-lookup"><span data-stu-id="02650-157">You can marshal these fields to one of three types:</span></span>
- [`VARIANT`](/windows/desktop/api/oaidl/ns-oaidl-tagvariant)
- [`IUnknown*`](/windows/desktop/api/unknwn/nn-unknwn-iunknown)
- [`IDispatch*`](/windows/desktop/api/oaidl/nn-oaidl-idispatch)

<span data-ttu-id="02650-158">Ve výchozím nastavení `object`-typovaná pole bude zařazeno do `IUnknown*` , která zabalí objekt.</span><span class="sxs-lookup"><span data-stu-id="02650-158">By default, an `object`-typed field will be marshalled to an `IUnknown*` that wraps the object.</span></span>

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

<span data-ttu-id="02650-159">Pokud chcete přeuspořádat polem objektu do `IDispatch*`, přidat <xref:System.Runtime.InteropServices.MarshalAsAttribute> s <xref:System.Runtime.InteropServices.UnmanagedType.IDispatch?displayProperty=nameWithType> hodnotu.</span><span class="sxs-lookup"><span data-stu-id="02650-159">If you want to marshal an object field to an `IDispatch*`, add a <xref:System.Runtime.InteropServices.MarshalAsAttribute> with the <xref:System.Runtime.InteropServices.UnmanagedType.IDispatch?displayProperty=nameWithType> value.</span></span>

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

<span data-ttu-id="02650-160">Pokud chcete zařadit jako `VARIANT`, přidejte <xref:System.Runtime.InteropServices.MarshalAsAttribute> s <xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType> hodnotu.</span><span class="sxs-lookup"><span data-stu-id="02650-160">If you want to marshal it as a `VARIANT`, add a <xref:System.Runtime.InteropServices.MarshalAsAttribute> with the <xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType> value.</span></span>

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

<span data-ttu-id="02650-161">Následující tabulka popisuje, jak různé typy runtime `obj` mapování polí na různé typy, které jsou uložené v `VARIANT`:</span><span class="sxs-lookup"><span data-stu-id="02650-161">The following table describes how different runtime types of the `obj` field map to the various types stored in a `VARIANT`:</span></span>

| <span data-ttu-id="02650-162">Typ formátu .NET</span><span class="sxs-lookup"><span data-stu-id="02650-162">.NET Type</span></span> | <span data-ttu-id="02650-163">Typ VARIANT</span><span class="sxs-lookup"><span data-stu-id="02650-163">VARIANT Type</span></span> | | <span data-ttu-id="02650-164">Typ formátu .NET</span><span class="sxs-lookup"><span data-stu-id="02650-164">.NET Type</span></span> | <span data-ttu-id="02650-165">Typ VARIANT</span><span class="sxs-lookup"><span data-stu-id="02650-165">VARIANT Type</span></span> |
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
