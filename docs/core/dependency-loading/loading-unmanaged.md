---
title: Algoritmus načítání nespravované knihovny - .NET Core
description: Popis podrobností o algoritmu načítání nespravovaného sestavení v rozhraní .NET Core
ms.date: 10/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: c651aa6e0f37a968e6f8b26d1909def6fa488ccd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "72250038"
---
# <a name="unmanaged-native-library-loading-algorithm"></a><span data-ttu-id="858fc-103">Algoritmus načítání nespravované (nativní) knihovny</span><span class="sxs-lookup"><span data-stu-id="858fc-103">Unmanaged (native) library loading algorithm</span></span>

<span data-ttu-id="858fc-104">Nespravované knihovny jsou umístěny a načteny s algoritmem zahrnujícím různé fáze.</span><span class="sxs-lookup"><span data-stu-id="858fc-104">Unmanaged libraries are located and loaded with an algorithm involving various stages.</span></span>

<span data-ttu-id="858fc-105">Následující algoritmus popisuje, jak jsou `PInvoke`nativní knihovny načteny prostřednictvím aplikace .</span><span class="sxs-lookup"><span data-stu-id="858fc-105">The following algorithm describes how native libraries are loaded through `PInvoke`.</span></span>

## <a name="pinvoke-load-library-algorithm"></a><span data-ttu-id="858fc-106">`PInvoke`algoritmus knihovny zatížení</span><span class="sxs-lookup"><span data-stu-id="858fc-106">`PInvoke` load library algorithm</span></span>

<span data-ttu-id="858fc-107">`PInvoke`Při pokusu o načtení nespravovaného sestavení používá následující algoritmus:</span><span class="sxs-lookup"><span data-stu-id="858fc-107">`PInvoke` uses the following algorithm when attempting to load an unmanaged assembly:</span></span>

1. <span data-ttu-id="858fc-108">Určete `active` <xref:System.Runtime.Loader.AssemblyLoadContext>.</span><span class="sxs-lookup"><span data-stu-id="858fc-108">Determine the `active` <xref:System.Runtime.Loader.AssemblyLoadContext>.</span></span> <span data-ttu-id="858fc-109">Pro nespravovanou knihovnu `active` zatížení assemblyloadcontext je ten s `PInvoke`sestavením, které definuje .</span><span class="sxs-lookup"><span data-stu-id="858fc-109">For an unmanaged load library, the `active` AssemblyLoadContext is the one with the assembly that defines the `PInvoke`.</span></span>

2. <span data-ttu-id="858fc-110">V `active` <xref:System.Runtime.Loader.AssemblyLoadContext>oblasti se pokuste najít sestavení v pořadí podle priority:</span><span class="sxs-lookup"><span data-stu-id="858fc-110">For the `active` <xref:System.Runtime.Loader.AssemblyLoadContext>, try to find the assembly in priority order by:</span></span>
    * <span data-ttu-id="858fc-111">Kontroluji jeho mezipaměť.</span><span class="sxs-lookup"><span data-stu-id="858fc-111">Checking its cache.</span></span>

    * <span data-ttu-id="858fc-112">Volání aktuálního <xref:System.Runtime.InteropServices.DllImportResolver?displayProperty=nameWithType> delegáta <xref:System.Runtime.InteropServices.NativeLibrary.SetDllImportResolver(System.Reflection.Assembly,System.Runtime.InteropServices.DllImportResolver)?displayProperty=nameWithType> nastaveného funkcí.</span><span class="sxs-lookup"><span data-stu-id="858fc-112">Calling the current <xref:System.Runtime.InteropServices.DllImportResolver?displayProperty=nameWithType> delegate set by the <xref:System.Runtime.InteropServices.NativeLibrary.SetDllImportResolver(System.Reflection.Assembly,System.Runtime.InteropServices.DllImportResolver)?displayProperty=nameWithType> function.</span></span>

    * <span data-ttu-id="858fc-113">Volání <xref:System.Runtime.Loader.AssemblyLoadContext.LoadUnmanagedDll%2A?displayProperty=nameWithType> funkce na `active` AssemblyLoadContext.</span><span class="sxs-lookup"><span data-stu-id="858fc-113">Calling the <xref:System.Runtime.Loader.AssemblyLoadContext.LoadUnmanagedDll%2A?displayProperty=nameWithType> function on the `active` AssemblyLoadContext.</span></span>

    * <span data-ttu-id="858fc-114">Kontrola mezipaměti <xref:System.AppDomain> instance a spuštění logiky zjišťování [nespravované (nativní) knihovny.](default-probing.md#unmanaged-native-library-probing)</span><span class="sxs-lookup"><span data-stu-id="858fc-114">Checking the <xref:System.AppDomain> instance's cache and running the [Unmanaged (native) library probing](default-probing.md#unmanaged-native-library-probing) logic.</span></span>

    * <span data-ttu-id="858fc-115">Vyvolání <xref:System.Runtime.Loader.AssemblyLoadContext.ResolvingUnmanagedDll?displayProperty=nameWithType> události `active` pro AssemblyLoadContext.</span><span class="sxs-lookup"><span data-stu-id="858fc-115">Raising the <xref:System.Runtime.Loader.AssemblyLoadContext.ResolvingUnmanagedDll?displayProperty=nameWithType> event for the `active` AssemblyLoadContext.</span></span>
