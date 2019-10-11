---
title: Algoritmus nespravované knihovny pro načítání – .NET Core
description: Popis podrobností algoritmu načítání nespravovaného sestavení v .NET Core
ms.date: 10/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: c651aa6e0f37a968e6f8b26d1909def6fa488ccd
ms.sourcegitcommit: d7c298f6c2e3aab0c7498bfafc0a0a94ea1fe23e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/10/2019
ms.locfileid: "72250038"
---
# <a name="unmanaged-native-library-loading-algorithm"></a><span data-ttu-id="ac5bf-103">Algoritmus načítání nespravované (nativní) knihovny</span><span class="sxs-lookup"><span data-stu-id="ac5bf-103">Unmanaged (native) library loading algorithm</span></span>

<span data-ttu-id="ac5bf-104">Nespravované knihovny se nacházejí a načítají pomocí algoritmu zahrnujícího různé fáze.</span><span class="sxs-lookup"><span data-stu-id="ac5bf-104">Unmanaged libraries are located and loaded with an algorithm involving various stages.</span></span>

<span data-ttu-id="ac5bf-105">Následující algoritmus popisuje, jak jsou načteny nativní knihovny pomocí `PInvoke`.</span><span class="sxs-lookup"><span data-stu-id="ac5bf-105">The following algorithm describes how native libraries are loaded through `PInvoke`.</span></span>

## <a name="pinvoke-load-library-algorithm"></a><span data-ttu-id="ac5bf-106">algoritmus knihovny Load `PInvoke`</span><span class="sxs-lookup"><span data-stu-id="ac5bf-106">`PInvoke` load library algorithm</span></span>

<span data-ttu-id="ac5bf-107">`PInvoke` používá při pokusu o načtení nespravovaného sestavení následující algoritmus:</span><span class="sxs-lookup"><span data-stu-id="ac5bf-107">`PInvoke` uses the following algorithm when attempting to load an unmanaged assembly:</span></span>

1. <span data-ttu-id="ac5bf-108">Určete `active` <xref:System.Runtime.Loader.AssemblyLoadContext>.</span><span class="sxs-lookup"><span data-stu-id="ac5bf-108">Determine the `active` <xref:System.Runtime.Loader.AssemblyLoadContext>.</span></span> <span data-ttu-id="ac5bf-109">Pro nespravované knihovny zatížení je `active` AssemblyLoadContext se sestavením, které definuje `PInvoke`.</span><span class="sxs-lookup"><span data-stu-id="ac5bf-109">For an unmanaged load library, the `active` AssemblyLoadContext is the one with the assembly that defines the `PInvoke`.</span></span>

2. <span data-ttu-id="ac5bf-110">U `active` <xref:System.Runtime.Loader.AssemblyLoadContext> zkuste najít sestavení v pořadí podle priority podle:</span><span class="sxs-lookup"><span data-stu-id="ac5bf-110">For the `active` <xref:System.Runtime.Loader.AssemblyLoadContext>, try to find the assembly in priority order by:</span></span>
    * <span data-ttu-id="ac5bf-111">Kontroluje se její mezipaměť.</span><span class="sxs-lookup"><span data-stu-id="ac5bf-111">Checking its cache.</span></span>

    * <span data-ttu-id="ac5bf-112">Volání aktuálního delegáta <xref:System.Runtime.InteropServices.DllImportResolver?displayProperty=nameWithType> nastaveného funkcí <xref:System.Runtime.InteropServices.NativeLibrary.SetDllImportResolver(System.Reflection.Assembly,System.Runtime.InteropServices.DllImportResolver)?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ac5bf-112">Calling the current <xref:System.Runtime.InteropServices.DllImportResolver?displayProperty=nameWithType> delegate set by the <xref:System.Runtime.InteropServices.NativeLibrary.SetDllImportResolver(System.Reflection.Assembly,System.Runtime.InteropServices.DllImportResolver)?displayProperty=nameWithType> function.</span></span>

    * <span data-ttu-id="ac5bf-113">Volání funkce <xref:System.Runtime.Loader.AssemblyLoadContext.LoadUnmanagedDll%2A?displayProperty=nameWithType> na `active` AssemblyLoadContext.</span><span class="sxs-lookup"><span data-stu-id="ac5bf-113">Calling the <xref:System.Runtime.Loader.AssemblyLoadContext.LoadUnmanagedDll%2A?displayProperty=nameWithType> function on the `active` AssemblyLoadContext.</span></span>

    * <span data-ttu-id="ac5bf-114">Probíhá kontrola mezipaměti instance <xref:System.AppDomain> a spuštění [nespravované (nativní) knihovny zjišťování knihovny](default-probing.md#unmanaged-native-library-probing) .</span><span class="sxs-lookup"><span data-stu-id="ac5bf-114">Checking the <xref:System.AppDomain> instance's cache and running the [Unmanaged (native) library probing](default-probing.md#unmanaged-native-library-probing) logic.</span></span>

    * <span data-ttu-id="ac5bf-115">Vyvolává se událost <xref:System.Runtime.Loader.AssemblyLoadContext.ResolvingUnmanagedDll?displayProperty=nameWithType> pro `active` AssemblyLoadContext.</span><span class="sxs-lookup"><span data-stu-id="ac5bf-115">Raising the <xref:System.Runtime.Loader.AssemblyLoadContext.ResolvingUnmanagedDll?displayProperty=nameWithType> event for the `active` AssemblyLoadContext.</span></span>
