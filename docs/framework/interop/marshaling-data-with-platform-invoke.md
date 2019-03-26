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
ms.openlocfilehash: 3cb310dc6d786c3c7711f4c194c6623324c777dd
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2019
ms.locfileid: "58412393"
---
# <a name="marshaling-data-with-platform-invoke"></a><span data-ttu-id="5a75e-102">Zařazování dat s voláním platformy</span><span class="sxs-lookup"><span data-stu-id="5a75e-102">Marshaling Data with Platform Invoke</span></span>

<span data-ttu-id="5a75e-103">Volání funkcí exportovaných z nespravovaná knihovna, vyžaduje aplikaci rozhraní .NET Framework prototypu funkce ve spravovaném kódu, který představuje nespravované funkci.</span><span class="sxs-lookup"><span data-stu-id="5a75e-103">To call functions exported from an unmanaged library, a .NET Framework application requires a function prototype in managed code that represents the unmanaged function.</span></span> <span data-ttu-id="5a75e-104">K vytvoření prototypu, který umožňuje platformu vyvolání zařazování dat správně, musíte provést následující:</span><span class="sxs-lookup"><span data-stu-id="5a75e-104">To create a prototype that enables platform invoke to marshal data correctly, you must do the following:</span></span>

- <span data-ttu-id="5a75e-105">Použít <xref:System.Runtime.InteropServices.DllImportAttribute> atribut statické funkce nebo metody ve spravovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="5a75e-105">Apply the <xref:System.Runtime.InteropServices.DllImportAttribute> attribute to the static function or method in managed code.</span></span>

- <span data-ttu-id="5a75e-106">Nahraďte spravované datové typy pro nespravované datové typy.</span><span class="sxs-lookup"><span data-stu-id="5a75e-106">Substitute managed data types for unmanaged data types.</span></span>

<span data-ttu-id="5a75e-107">Podle dokumentace dodané s nespravovanou funkci můžete použít k vytvoření odpovídající spravovaný prototyp použitím atribut s jeho volitelná pole a nahrazování spravované datové typy pro nespravované typy.</span><span class="sxs-lookup"><span data-stu-id="5a75e-107">You can use the documentation supplied with an unmanaged function to construct an equivalent managed prototype by applying the attribute with its optional fields and substituting managed data types for unmanaged types.</span></span> <span data-ttu-id="5a75e-108">Pokyny o tom, jak aplikovat <xref:System.Runtime.InteropServices.DllImportAttribute>, naleznete v tématu [používání nespravovaných funkcí DLL](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md).</span><span class="sxs-lookup"><span data-stu-id="5a75e-108">For instructions about how to apply the <xref:System.Runtime.InteropServices.DllImportAttribute>, see [Consuming Unmanaged DLL Functions](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md).</span></span>

<span data-ttu-id="5a75e-109">Tato část obsahuje ukázky, které ukazují, jak vytvářet prototypy spravované funkce pro předávání argumentů do a z funkcí exportovaných knihovnou nespravovaných knihoven příjem návratové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="5a75e-109">This section provides samples that demonstrate how to create managed function prototypes for passing arguments to and receiving return values from functions exported by unmanaged libraries.</span></span> <span data-ttu-id="5a75e-110">Ukázky také ukazují, kdy se má použít <xref:System.Runtime.InteropServices.MarshalAsAttribute> atribut a <xref:System.Runtime.InteropServices.Marshal> třídy explicitně zařazování dat.</span><span class="sxs-lookup"><span data-stu-id="5a75e-110">The samples also demonstrate when to use the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute and the <xref:System.Runtime.InteropServices.Marshal> class to explicitly marshal data.</span></span>

## <a name="platform-invoke-data-types"></a><span data-ttu-id="5a75e-111">Datové typy vyvolání platformy</span><span class="sxs-lookup"><span data-stu-id="5a75e-111">Platform invoke data types</span></span>

<span data-ttu-id="5a75e-112">V následující tabulce jsou uvedeny datové typy používané v rozhraní Windows API a funkce C-style.</span><span class="sxs-lookup"><span data-stu-id="5a75e-112">The following table lists data types used in the Windows APIs and C-style functions.</span></span> <span data-ttu-id="5a75e-113">Mnoho nespravovaných knihoven obsahují funkce, které jako parametry předat těchto datových typů a návratových hodnot.</span><span class="sxs-lookup"><span data-stu-id="5a75e-113">Many unmanaged libraries contain functions that pass these data types as parameters and return values.</span></span> <span data-ttu-id="5a75e-114">Třetí sloupec uvádí odpovídající rozhraní .NET Framework předdefinovaného hodnotového typu nebo třídy, která používáte ve spravovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="5a75e-114">The third column lists the corresponding .NET Framework built-in value type or class that you use in managed code.</span></span> <span data-ttu-id="5a75e-115">V některých případech můžete nahradit typ stejné velikosti typu uvedené v tabulce.</span><span class="sxs-lookup"><span data-stu-id="5a75e-115">In some cases, you can substitute a type of the same size for the type listed in the table.</span></span>

|<span data-ttu-id="5a75e-116">Nespravovaný typ v rozhraní Windows API</span><span class="sxs-lookup"><span data-stu-id="5a75e-116">Unmanaged type in Windows APIs</span></span>|<span data-ttu-id="5a75e-117">Nespravovaný typ jazyka C</span><span class="sxs-lookup"><span data-stu-id="5a75e-117">Unmanaged C language type</span></span>|<span data-ttu-id="5a75e-118">Spravovaného typu</span><span class="sxs-lookup"><span data-stu-id="5a75e-118">Managed type</span></span>|<span data-ttu-id="5a75e-119">Popis</span><span class="sxs-lookup"><span data-stu-id="5a75e-119">Description</span></span>|
|--------------------------------|-------------------------------|------------------------|-----------------|
|`VOID`|`void`|<xref:System.Void?displayProperty=nameWithType>|<span data-ttu-id="5a75e-120">Použít pro funkci, která nevrací hodnotu.</span><span class="sxs-lookup"><span data-stu-id="5a75e-120">Applied to a function that does not return a value.</span></span>|
|`HANDLE`|`void *`|<span data-ttu-id="5a75e-121"><xref:System.IntPtr?displayProperty=nameWithType> Nebo <xref:System.UIntPtr?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="5a75e-121"><xref:System.IntPtr?displayProperty=nameWithType> or <xref:System.UIntPtr?displayProperty=nameWithType></span></span>|<span data-ttu-id="5a75e-122">32 bitů na 32bitové operační systémy Windows, 64 bitů v operačních systémech Windows 64-bit.</span><span class="sxs-lookup"><span data-stu-id="5a75e-122">32 bits on 32-bit Windows operating systems, 64 bits on 64-bit Windows operating systems.</span></span>|
|`BYTE`|`unsigned char`|<xref:System.Byte?displayProperty=nameWithType>|<span data-ttu-id="5a75e-123">8 bitů</span><span class="sxs-lookup"><span data-stu-id="5a75e-123">8 bits</span></span>|
|`SHORT`|`short`|<xref:System.Int16?displayProperty=nameWithType>|<span data-ttu-id="5a75e-124">16 bitů</span><span class="sxs-lookup"><span data-stu-id="5a75e-124">16 bits</span></span>|
|`WORD`|`unsigned short`|<xref:System.UInt16?displayProperty=nameWithType>|<span data-ttu-id="5a75e-125">16 bitů</span><span class="sxs-lookup"><span data-stu-id="5a75e-125">16 bits</span></span>|
|`INT`|`int`|<xref:System.Int32?displayProperty=nameWithType>|<span data-ttu-id="5a75e-126">32 bitů</span><span class="sxs-lookup"><span data-stu-id="5a75e-126">32 bits</span></span>|
|`UINT`|`unsigned int`|<xref:System.UInt32?displayProperty=nameWithType>|<span data-ttu-id="5a75e-127">32 bitů</span><span class="sxs-lookup"><span data-stu-id="5a75e-127">32 bits</span></span>|
|`LONG`|`long`|<xref:System.Int32?displayProperty=nameWithType>|<span data-ttu-id="5a75e-128">32 bitů</span><span class="sxs-lookup"><span data-stu-id="5a75e-128">32 bits</span></span>|
|`BOOL`|`long`|<span data-ttu-id="5a75e-129"><xref:System.Boolean?displayProperty=nameWithType> Nebo <xref:System.Int32?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="5a75e-129"><xref:System.Boolean?displayProperty=nameWithType> or <xref:System.Int32?displayProperty=nameWithType></span></span>|<span data-ttu-id="5a75e-130">32 bitů</span><span class="sxs-lookup"><span data-stu-id="5a75e-130">32 bits</span></span>|
|`DWORD`|`unsigned long`|<xref:System.UInt32?displayProperty=nameWithType>|<span data-ttu-id="5a75e-131">32 bitů</span><span class="sxs-lookup"><span data-stu-id="5a75e-131">32 bits</span></span>|
|`ULONG`|`unsigned long`|<xref:System.UInt32?displayProperty=nameWithType>|<span data-ttu-id="5a75e-132">32 bitů</span><span class="sxs-lookup"><span data-stu-id="5a75e-132">32 bits</span></span>|
|`CHAR`|`char`|<xref:System.Char?displayProperty=nameWithType>|<span data-ttu-id="5a75e-133">Uspořádání s ANSI.</span><span class="sxs-lookup"><span data-stu-id="5a75e-133">Decorate with ANSI.</span></span>|
|`WCHAR`|`wchar_t`|<xref:System.Char?displayProperty=nameWithType>|<span data-ttu-id="5a75e-134">Vyplnění pomocí kódování Unicode.</span><span class="sxs-lookup"><span data-stu-id="5a75e-134">Decorate with Unicode.</span></span>|
|`LPSTR`|`char *`|<span data-ttu-id="5a75e-135"><xref:System.String?displayProperty=nameWithType> Nebo <xref:System.Text.StringBuilder?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="5a75e-135"><xref:System.String?displayProperty=nameWithType> or <xref:System.Text.StringBuilder?displayProperty=nameWithType></span></span>|<span data-ttu-id="5a75e-136">Uspořádání s ANSI.</span><span class="sxs-lookup"><span data-stu-id="5a75e-136">Decorate with ANSI.</span></span>|
|`LPCSTR`|`const char *`|<span data-ttu-id="5a75e-137"><xref:System.String?displayProperty=nameWithType> Nebo <xref:System.Text.StringBuilder?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="5a75e-137"><xref:System.String?displayProperty=nameWithType> or <xref:System.Text.StringBuilder?displayProperty=nameWithType></span></span>|<span data-ttu-id="5a75e-138">Uspořádání s ANSI.</span><span class="sxs-lookup"><span data-stu-id="5a75e-138">Decorate with ANSI.</span></span>|
|`LPWSTR`|`wchar_t *`|<span data-ttu-id="5a75e-139"><xref:System.String?displayProperty=nameWithType> Nebo <xref:System.Text.StringBuilder?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="5a75e-139"><xref:System.String?displayProperty=nameWithType> or <xref:System.Text.StringBuilder?displayProperty=nameWithType></span></span>|<span data-ttu-id="5a75e-140">Vyplnění pomocí kódování Unicode.</span><span class="sxs-lookup"><span data-stu-id="5a75e-140">Decorate with Unicode.</span></span>|
|`LPCWSTR`|`const wchar_t *`|<span data-ttu-id="5a75e-141"><xref:System.String?displayProperty=nameWithType> Nebo <xref:System.Text.StringBuilder?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="5a75e-141"><xref:System.String?displayProperty=nameWithType> or <xref:System.Text.StringBuilder?displayProperty=nameWithType></span></span>|<span data-ttu-id="5a75e-142">Vyplnění pomocí kódování Unicode.</span><span class="sxs-lookup"><span data-stu-id="5a75e-142">Decorate with Unicode.</span></span>|
|`FLOAT`|`float`|<xref:System.Single?displayProperty=nameWithType>|<span data-ttu-id="5a75e-143">32 bitů</span><span class="sxs-lookup"><span data-stu-id="5a75e-143">32 bits</span></span>|
|`DOUBLE`|`double`|<xref:System.Double?displayProperty=nameWithType>|<span data-ttu-id="5a75e-144">64 bitů</span><span class="sxs-lookup"><span data-stu-id="5a75e-144">64 bits</span></span>|

<span data-ttu-id="5a75e-145">Pro odpovídající typy v jazyce Visual Basic C#a C++, naleznete v tématu [Úvod do knihovny tříd rozhraní .NET Framework](../../standard/class-library-overview.md#system-namespace).</span><span class="sxs-lookup"><span data-stu-id="5a75e-145">For corresponding types in Visual Basic, C#, and C++, see the [Introduction to the .NET Framework Class Library](../../standard/class-library-overview.md#system-namespace).</span></span>

## <a name="pinvokelibdll"></a><span data-ttu-id="5a75e-146">PinvokeLib.dll</span><span class="sxs-lookup"><span data-stu-id="5a75e-146">PinvokeLib.dll</span></span>

<span data-ttu-id="5a75e-147">Následující kód definuje funkce knihovny poskytované Pinvoke.dll.</span><span class="sxs-lookup"><span data-stu-id="5a75e-147">The following code defines the library functions provided by Pinvoke.dll.</span></span> <span data-ttu-id="5a75e-148">Mnoho vzorků popsané v této části volání této knihovny.</span><span class="sxs-lookup"><span data-stu-id="5a75e-148">Many samples described in this section call this library.</span></span>

### <a name="example"></a><span data-ttu-id="5a75e-149">Příklad</span><span class="sxs-lookup"><span data-stu-id="5a75e-149">Example</span></span>

[!code-cpp[PInvokeLib#1](../../../samples/snippets/cpp/VS_Snippets_CLR/pinvokelib/cpp/pinvokelib.cpp#1)]

[!code-cpp[PInvokeLib#2](../../../samples/snippets/cpp/VS_Snippets_CLR/pinvokelib/cpp/pinvokelib.h#2)]
