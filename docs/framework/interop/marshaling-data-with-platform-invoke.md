---
title: Zařazování dat s voláním platformy
ms.date: 03/20/2019
dev_langs:
- cpp
helpviewer_keywords:
- platform invoke, marshaling data
- data marshaling, platform invoke
- marshaling, platform invoke
ms.assetid: dc5c76cf-7b12-406f-b79c-d1a023ec245d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d3167abd0c263a0a27573778d6f243bc824306a9
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71051691"
---
# <a name="marshaling-data-with-platform-invoke"></a><span data-ttu-id="55ae5-102">Zařazování dat s voláním platformy</span><span class="sxs-lookup"><span data-stu-id="55ae5-102">Marshaling Data with Platform Invoke</span></span>

<span data-ttu-id="55ae5-103">Chcete-li volat funkce exportované z nespravované knihovny, aplikace .NET Framework vyžaduje prototyp funkce ve spravovaném kódu, který představuje nespravovanou funkci.</span><span class="sxs-lookup"><span data-stu-id="55ae5-103">To call functions exported from an unmanaged library, a .NET Framework application requires a function prototype in managed code that represents the unmanaged function.</span></span> <span data-ttu-id="55ae5-104">Chcete-li vytvořit prototyp, který umožňuje vyvolání platformy pro správné zařazování dat, je nutné provést následující:</span><span class="sxs-lookup"><span data-stu-id="55ae5-104">To create a prototype that enables platform invoke to marshal data correctly, you must do the following:</span></span>

- <span data-ttu-id="55ae5-105"><xref:System.Runtime.InteropServices.DllImportAttribute> Použijte atribut pro statickou funkci nebo metodu ve spravovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="55ae5-105">Apply the <xref:System.Runtime.InteropServices.DllImportAttribute> attribute to the static function or method in managed code.</span></span>

- <span data-ttu-id="55ae5-106">Nahraďte spravované datové typy pro nespravované datové typy.</span><span class="sxs-lookup"><span data-stu-id="55ae5-106">Substitute managed data types for unmanaged data types.</span></span>

<span data-ttu-id="55ae5-107">Dokumentaci dodanou s nespravovanou funkcí můžete použít k vytvoření ekvivalentního spravovaného prototypu použitím atributu s jeho nepovinnými poli a nahrazením spravovaných datových typů pro nespravované typy.</span><span class="sxs-lookup"><span data-stu-id="55ae5-107">You can use the documentation supplied with an unmanaged function to construct an equivalent managed prototype by applying the attribute with its optional fields and substituting managed data types for unmanaged types.</span></span> <span data-ttu-id="55ae5-108">Pokyny k použití <xref:System.Runtime.InteropServices.DllImportAttribute>naleznete v tématu [spotřebovávání nespravovaných funkcí DLL](consuming-unmanaged-dll-functions.md).</span><span class="sxs-lookup"><span data-stu-id="55ae5-108">For instructions about how to apply the <xref:System.Runtime.InteropServices.DllImportAttribute>, see [Consuming Unmanaged DLL Functions](consuming-unmanaged-dll-functions.md).</span></span>

<span data-ttu-id="55ae5-109">V této části jsou uvedeny ukázky, které ukazují, jak vytvořit prototypy spravované funkce pro předávání argumentů a přijímání návratových hodnot z funkcí exportovaných nespravovanými knihovnami.</span><span class="sxs-lookup"><span data-stu-id="55ae5-109">This section provides samples that demonstrate how to create managed function prototypes for passing arguments to and receiving return values from functions exported by unmanaged libraries.</span></span> <span data-ttu-id="55ae5-110">Ukázky také ukazují, kdy použít <xref:System.Runtime.InteropServices.MarshalAsAttribute> atribut <xref:System.Runtime.InteropServices.Marshal> a třídu k explicitnímu zařazování dat.</span><span class="sxs-lookup"><span data-stu-id="55ae5-110">The samples also demonstrate when to use the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute and the <xref:System.Runtime.InteropServices.Marshal> class to explicitly marshal data.</span></span>

## <a name="platform-invoke-data-types"></a><span data-ttu-id="55ae5-111">Datové typy vyvolání platformy</span><span class="sxs-lookup"><span data-stu-id="55ae5-111">Platform invoke data types</span></span>

<span data-ttu-id="55ae5-112">V následující tabulce jsou uvedeny datové typy používané ve funkcích rozhraní API systému Windows a ve stylu jazyka C.</span><span class="sxs-lookup"><span data-stu-id="55ae5-112">The following table lists data types used in the Windows APIs and C-style functions.</span></span> <span data-ttu-id="55ae5-113">Mnoho nespravovaných knihoven obsahuje funkce, které tyto datové typy předají jako parametry a návratové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="55ae5-113">Many unmanaged libraries contain functions that pass these data types as parameters and return values.</span></span> <span data-ttu-id="55ae5-114">Třetí sloupec uvádí odpovídající .NET Framework typ hodnoty nebo třídu, která se používá ve spravovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="55ae5-114">The third column lists the corresponding .NET Framework built-in value type or class that you use in managed code.</span></span> <span data-ttu-id="55ae5-115">V některých případech můžete nahradit typ stejné velikosti pro typ uvedený v tabulce.</span><span class="sxs-lookup"><span data-stu-id="55ae5-115">In some cases, you can substitute a type of the same size for the type listed in the table.</span></span>

|<span data-ttu-id="55ae5-116">Nespravovaný typ v rozhraních API systému Windows</span><span class="sxs-lookup"><span data-stu-id="55ae5-116">Unmanaged type in Windows APIs</span></span>|<span data-ttu-id="55ae5-117">Nespravovaný typ jazyka C</span><span class="sxs-lookup"><span data-stu-id="55ae5-117">Unmanaged C language type</span></span>|<span data-ttu-id="55ae5-118">Spravovaný typ</span><span class="sxs-lookup"><span data-stu-id="55ae5-118">Managed type</span></span>|<span data-ttu-id="55ae5-119">Popis</span><span class="sxs-lookup"><span data-stu-id="55ae5-119">Description</span></span>|
|--------------------------------|-------------------------------|------------------------|-----------------|
|`VOID`|`void`|<xref:System.Void?displayProperty=nameWithType>|<span data-ttu-id="55ae5-120">Používá se pro funkci, která nevrací hodnotu.</span><span class="sxs-lookup"><span data-stu-id="55ae5-120">Applied to a function that does not return a value.</span></span>|
|`HANDLE`|`void *`|<span data-ttu-id="55ae5-121"><xref:System.IntPtr?displayProperty=nameWithType> Nebo <xref:System.UIntPtr?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="55ae5-121"><xref:System.IntPtr?displayProperty=nameWithType> or <xref:System.UIntPtr?displayProperty=nameWithType></span></span>|<span data-ttu-id="55ae5-122">32 bitů v systémech Windows 32, 64 bitů v systémech Windows 64 v 16bitovém operačním systému Windows.</span><span class="sxs-lookup"><span data-stu-id="55ae5-122">32 bits on 32-bit Windows operating systems, 64 bits on 64-bit Windows operating systems.</span></span>|
|`BYTE`|`unsigned char`|<xref:System.Byte?displayProperty=nameWithType>|<span data-ttu-id="55ae5-123">8 bitů</span><span class="sxs-lookup"><span data-stu-id="55ae5-123">8 bits</span></span>|
|`SHORT`|`short`|<xref:System.Int16?displayProperty=nameWithType>|<span data-ttu-id="55ae5-124">16 bitů</span><span class="sxs-lookup"><span data-stu-id="55ae5-124">16 bits</span></span>|
|`WORD`|`unsigned short`|<xref:System.UInt16?displayProperty=nameWithType>|<span data-ttu-id="55ae5-125">16 bitů</span><span class="sxs-lookup"><span data-stu-id="55ae5-125">16 bits</span></span>|
|`INT`|`int`|<xref:System.Int32?displayProperty=nameWithType>|<span data-ttu-id="55ae5-126">32 bitů</span><span class="sxs-lookup"><span data-stu-id="55ae5-126">32 bits</span></span>|
|`UINT`|`unsigned int`|<xref:System.UInt32?displayProperty=nameWithType>|<span data-ttu-id="55ae5-127">32 bitů</span><span class="sxs-lookup"><span data-stu-id="55ae5-127">32 bits</span></span>|
|`LONG`|`long`|<xref:System.Int32?displayProperty=nameWithType>|<span data-ttu-id="55ae5-128">32 bitů</span><span class="sxs-lookup"><span data-stu-id="55ae5-128">32 bits</span></span>|
|`BOOL`|`long`|<span data-ttu-id="55ae5-129"><xref:System.Boolean?displayProperty=nameWithType> Nebo <xref:System.Int32?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="55ae5-129"><xref:System.Boolean?displayProperty=nameWithType> or <xref:System.Int32?displayProperty=nameWithType></span></span>|<span data-ttu-id="55ae5-130">32 bitů</span><span class="sxs-lookup"><span data-stu-id="55ae5-130">32 bits</span></span>|
|`DWORD`|`unsigned long`|<xref:System.UInt32?displayProperty=nameWithType>|<span data-ttu-id="55ae5-131">32 bitů</span><span class="sxs-lookup"><span data-stu-id="55ae5-131">32 bits</span></span>|
|`ULONG`|`unsigned long`|<xref:System.UInt32?displayProperty=nameWithType>|<span data-ttu-id="55ae5-132">32 bitů</span><span class="sxs-lookup"><span data-stu-id="55ae5-132">32 bits</span></span>|
|`CHAR`|`char`|<xref:System.Char?displayProperty=nameWithType>|<span data-ttu-id="55ae5-133">Upravte pomocí ANSI.</span><span class="sxs-lookup"><span data-stu-id="55ae5-133">Decorate with ANSI.</span></span>|
|`WCHAR`|`wchar_t`|<xref:System.Char?displayProperty=nameWithType>|<span data-ttu-id="55ae5-134">Upravte pomocí kódování Unicode.</span><span class="sxs-lookup"><span data-stu-id="55ae5-134">Decorate with Unicode.</span></span>|
|`LPSTR`|`char *`|<span data-ttu-id="55ae5-135"><xref:System.String?displayProperty=nameWithType> Nebo <xref:System.Text.StringBuilder?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="55ae5-135"><xref:System.String?displayProperty=nameWithType> or <xref:System.Text.StringBuilder?displayProperty=nameWithType></span></span>|<span data-ttu-id="55ae5-136">Upravte pomocí ANSI.</span><span class="sxs-lookup"><span data-stu-id="55ae5-136">Decorate with ANSI.</span></span>|
|`LPCSTR`|`const char *`|<span data-ttu-id="55ae5-137"><xref:System.String?displayProperty=nameWithType> Nebo <xref:System.Text.StringBuilder?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="55ae5-137"><xref:System.String?displayProperty=nameWithType> or <xref:System.Text.StringBuilder?displayProperty=nameWithType></span></span>|<span data-ttu-id="55ae5-138">Upravte pomocí ANSI.</span><span class="sxs-lookup"><span data-stu-id="55ae5-138">Decorate with ANSI.</span></span>|
|`LPWSTR`|`wchar_t *`|<span data-ttu-id="55ae5-139"><xref:System.String?displayProperty=nameWithType> Nebo <xref:System.Text.StringBuilder?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="55ae5-139"><xref:System.String?displayProperty=nameWithType> or <xref:System.Text.StringBuilder?displayProperty=nameWithType></span></span>|<span data-ttu-id="55ae5-140">Upravte pomocí kódování Unicode.</span><span class="sxs-lookup"><span data-stu-id="55ae5-140">Decorate with Unicode.</span></span>|
|`LPCWSTR`|`const wchar_t *`|<span data-ttu-id="55ae5-141"><xref:System.String?displayProperty=nameWithType> Nebo <xref:System.Text.StringBuilder?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="55ae5-141"><xref:System.String?displayProperty=nameWithType> or <xref:System.Text.StringBuilder?displayProperty=nameWithType></span></span>|<span data-ttu-id="55ae5-142">Upravte pomocí kódování Unicode.</span><span class="sxs-lookup"><span data-stu-id="55ae5-142">Decorate with Unicode.</span></span>|
|`FLOAT`|`float`|<xref:System.Single?displayProperty=nameWithType>|<span data-ttu-id="55ae5-143">32 bitů</span><span class="sxs-lookup"><span data-stu-id="55ae5-143">32 bits</span></span>|
|`DOUBLE`|`double`|<xref:System.Double?displayProperty=nameWithType>|<span data-ttu-id="55ae5-144">64 bitů</span><span class="sxs-lookup"><span data-stu-id="55ae5-144">64 bits</span></span>|

<span data-ttu-id="55ae5-145">Odpovídající typy v Visual Basic, C#a C++naleznete v tématu [Úvod do knihovny tříd .NET Framework](../../standard/class-library-overview.md#system-namespace).</span><span class="sxs-lookup"><span data-stu-id="55ae5-145">For corresponding types in Visual Basic, C#, and C++, see the [Introduction to the .NET Framework Class Library](../../standard/class-library-overview.md#system-namespace).</span></span>

## <a name="pinvokelibdll"></a><span data-ttu-id="55ae5-146">PinvokeLib.dll</span><span class="sxs-lookup"><span data-stu-id="55ae5-146">PinvokeLib.dll</span></span>

<span data-ttu-id="55ae5-147">Následující kód definuje funkce knihovny, které poskytuje PInvoke. dll.</span><span class="sxs-lookup"><span data-stu-id="55ae5-147">The following code defines the library functions provided by Pinvoke.dll.</span></span> <span data-ttu-id="55ae5-148">Mnoho ukázek popsaných v této části volá tuto knihovnu.</span><span class="sxs-lookup"><span data-stu-id="55ae5-148">Many samples described in this section call this library.</span></span>

### <a name="example"></a><span data-ttu-id="55ae5-149">Příklad</span><span class="sxs-lookup"><span data-stu-id="55ae5-149">Example</span></span>

[!code-cpp[PInvokeLib#1](../../../samples/snippets/cpp/VS_Snippets_CLR/pinvokelib/cpp/pinvokelib.cpp#1)]

[!code-cpp[PInvokeLib#2](../../../samples/snippets/cpp/VS_Snippets_CLR/pinvokelib/cpp/pinvokelib.h#2)]
