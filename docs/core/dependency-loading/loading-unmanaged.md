---
title: Algoritmus nespravované knihovny pro načítání – .NET Core
description: Popis podrobností algoritmu načítání nespravovaného sestavení v .NET Core
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: 8240cb730180637393e2545f8013d3f1439be719
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/24/2019
ms.locfileid: "70017329"
---
# <a name="unmanaged-native-library-loading-algorithm"></a><span data-ttu-id="03c6e-103">Algoritmus načítání nespravované (nativní) knihovny</span><span class="sxs-lookup"><span data-stu-id="03c6e-103">Unmanaged (native) library loading algorithm</span></span>

<span data-ttu-id="03c6e-104">Nespravované knihovny se nacházejí a načítají pomocí algoritmu zahrnujícího různé fáze.</span><span class="sxs-lookup"><span data-stu-id="03c6e-104">Unmanaged libraries are located and loaded with an algorithm involving various stages.</span></span>

<span data-ttu-id="03c6e-105">Následující algoritmus popisuje, jak jsou načítány nativní knihovny `PInvoke`pomocí.</span><span class="sxs-lookup"><span data-stu-id="03c6e-105">The following algorithm describes how native libraries are loaded through `PInvoke`.</span></span>

## <a name="pinvoke-load-library-algorithm"></a><span data-ttu-id="03c6e-106">`PInvoke`načíst algoritmus knihovny</span><span class="sxs-lookup"><span data-stu-id="03c6e-106">`PInvoke` load library algorithm</span></span>

<span data-ttu-id="03c6e-107">`PInvoke`Při pokusu o načtení nespravovaného sestavení používá následující algoritmus:</span><span class="sxs-lookup"><span data-stu-id="03c6e-107">`PInvoke` uses the following algorithm when attempting to load an unmanaged assembly:</span></span>

1. <span data-ttu-id="03c6e-108">`active` Určete .<xref:System.Runtime.Loader.AssemblyLoadContext></span><span class="sxs-lookup"><span data-stu-id="03c6e-108">Determine the `active` <xref:System.Runtime.Loader.AssemblyLoadContext>.</span></span> <span data-ttu-id="03c6e-109">Pro nespravované knihovny `active` zatížení je AssemblyLoadContext volajícím `PInvoke`.</span><span class="sxs-lookup"><span data-stu-id="03c6e-109">For an unmanaged load library, the `active` AssemblyLoadContext is the caller of the `PInvoke`.</span></span>

2. <span data-ttu-id="03c6e-110">`active` Vpřípaděsepokustenajítsestavenív<xref:System.Runtime.Loader.AssemblyLoadContext>pořadí podle priority podle:</span><span class="sxs-lookup"><span data-stu-id="03c6e-110">For the `active` <xref:System.Runtime.Loader.AssemblyLoadContext>, try to find the assembly in priority order by:</span></span>
    * <span data-ttu-id="03c6e-111">Kontroluje se její mezipaměť.</span><span class="sxs-lookup"><span data-stu-id="03c6e-111">Checking its cache.</span></span>

    * <span data-ttu-id="03c6e-112">Volání aktuálního <xref:System.Runtime.InteropServices.DllImportResolver?displayProperty=nameWithType> delegáta nastaveného <xref:System.Runtime.InteropServices.NativeLibrary.SetDllImportResolver(System.Reflection.Assembly,System.Runtime.InteropServices.DllImportResolver)?displayProperty=nameWithType> funkcí.</span><span class="sxs-lookup"><span data-stu-id="03c6e-112">Calling the current <xref:System.Runtime.InteropServices.DllImportResolver?displayProperty=nameWithType> delegate set by the <xref:System.Runtime.InteropServices.NativeLibrary.SetDllImportResolver(System.Reflection.Assembly,System.Runtime.InteropServices.DllImportResolver)?displayProperty=nameWithType> function.</span></span>

    * <span data-ttu-id="03c6e-113"><xref:System.Runtime.Loader.AssemblyLoadContext.LoadUnmanagedDll%2A?displayProperty=nameWithType> Volání funkce.</span><span class="sxs-lookup"><span data-stu-id="03c6e-113">Calling the <xref:System.Runtime.Loader.AssemblyLoadContext.LoadUnmanagedDll%2A?displayProperty=nameWithType> function.</span></span>

    * <span data-ttu-id="03c6e-114">Kontroluje se <xref:System.AppDomain> mezipaměť instance a spouští nespravovanou [(nativní) logiku zjišťování knihovny](default-probing.md#unmanaged-native-library-probing) .</span><span class="sxs-lookup"><span data-stu-id="03c6e-114">Checking the <xref:System.AppDomain> instance's cache and running the [Unmanaged (native) library probing](default-probing.md#unmanaged-native-library-probing) logic.</span></span>

    * <span data-ttu-id="03c6e-115">Vyvolává se `active` událost pro AssemblyLoadContext. <xref:System.Runtime.Loader.AssemblyLoadContext.ResolvingUnmanagedDll?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="03c6e-115">Raising the <xref:System.Runtime.Loader.AssemblyLoadContext.ResolvingUnmanagedDll?displayProperty=nameWithType> event for the `active` AssemblyLoadContext.</span></span>

3. <span data-ttu-id="03c6e-116">Pokud je nespravovaná knihovna nově načtena <xref:System.AppDomain.AssemblyLoad?displayProperty=nameWithType> , událost je vyvolána.</span><span class="sxs-lookup"><span data-stu-id="03c6e-116">If the unmanaged library is newly loaded, the <xref:System.AppDomain.AssemblyLoad?displayProperty=nameWithType> event is raised.</span></span>
