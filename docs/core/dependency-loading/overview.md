---
title: Načítání závislostí – .NET Core
description: Přehled spravovaného a nespravovaného načítání závislostí v .NET Core
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.topic: overview
ms.openlocfilehash: 69cca28606c64479d500e731ba95fe404bea38df
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/24/2019
ms.locfileid: "70017332"
---
# <a name="dependency-loading-in-net-core"></a><span data-ttu-id="06072-103">Načítání závislostí v .NET Core</span><span class="sxs-lookup"><span data-stu-id="06072-103">Dependency loading in .NET Core</span></span>

<span data-ttu-id="06072-104">Každá aplikace .NET Core má závislosti.</span><span class="sxs-lookup"><span data-stu-id="06072-104">Every .NET Core application has dependencies.</span></span> <span data-ttu-id="06072-105">I jednoduchá `hello world` aplikace má závislosti na částech knihoven tříd .NET Core.</span><span class="sxs-lookup"><span data-stu-id="06072-105">Even the simple `hello world` app has dependencies on portions of the .NET Core class libraries.</span></span>

<span data-ttu-id="06072-106">Porozumění logice načítání výchozích sestavení .NET Core vám může pomáhat pochopit a ladit běžné problémy s nasazením.</span><span class="sxs-lookup"><span data-stu-id="06072-106">Understanding .NET Core default assembly loading logic can help understanding and debugging typical deployment issues.</span></span>

<span data-ttu-id="06072-107">V některých aplikacích se závislosti dynamicky určují za běhu.</span><span class="sxs-lookup"><span data-stu-id="06072-107">In some applications, dependencies are dynamically determined at runtime.</span></span> <span data-ttu-id="06072-108">V těchto situacích je důležité pochopit, jak jsou načtena spravovaná sestavení a nespravované závislosti.</span><span class="sxs-lookup"><span data-stu-id="06072-108">In these situations, it's critical to understand how managed assemblies and unmanaged dependencies are loaded.</span></span>

## <a name="understanding-assemblyloadcontext"></a><span data-ttu-id="06072-109">Principy AssemblyLoadContext</span><span class="sxs-lookup"><span data-stu-id="06072-109">Understanding AssemblyLoadContext</span></span>

<span data-ttu-id="06072-110"><xref:System.Runtime.Loader.AssemblyLoadContext> Rozhraní API je centrální pro návrh načítání .NET Core.</span><span class="sxs-lookup"><span data-stu-id="06072-110">The <xref:System.Runtime.Loader.AssemblyLoadContext> API is central to the .NET Core loading design.</span></span> <span data-ttu-id="06072-111">Článek [Princip porozumění AssemblyLoadContext](understanding-assemblyloadcontext.md) poskytuje koncepční přehled návrhu.</span><span class="sxs-lookup"><span data-stu-id="06072-111">The [Understanding AssemblyLoadContext](understanding-assemblyloadcontext.md) article provides a conceptual overview to the design.</span></span>

## <a name="loading-details"></a><span data-ttu-id="06072-112">Načítají se podrobnosti.</span><span class="sxs-lookup"><span data-stu-id="06072-112">Loading details</span></span>

<span data-ttu-id="06072-113">Podrobnosti o zkušebním algoritmu jsou stručně uvedeny v několika článcích:</span><span class="sxs-lookup"><span data-stu-id="06072-113">The loading algorithm details are covered briefly in several articles:</span></span>
- [<span data-ttu-id="06072-114">Algoritmus načítání spravovaného sestavení</span><span class="sxs-lookup"><span data-stu-id="06072-114">Managed assembly loading algorithm</span></span>](loading-managed.md)
- [<span data-ttu-id="06072-115">Algoritmus načítání satelitních sestavení</span><span class="sxs-lookup"><span data-stu-id="06072-115">Satellite assembly loading algorithm</span></span>](loading-resources.md)
- [<span data-ttu-id="06072-116">Algoritmus načítání nespravované (nativní) knihovny</span><span class="sxs-lookup"><span data-stu-id="06072-116">Unmanaged (native) library loading algorithm</span></span>](loading-unmanaged.md)
- [<span data-ttu-id="06072-117">Výchozí zjišťování</span><span class="sxs-lookup"><span data-stu-id="06072-117">Default probing</span></span>](default-probing.md)

## <a name="create-a-net-core-application-with-plugins"></a><span data-ttu-id="06072-118">Vytvoření aplikace .NET Core pomocí modulů plug-in</span><span class="sxs-lookup"><span data-stu-id="06072-118">Create a .NET Core application with plugins</span></span>

<span data-ttu-id="06072-119">Kurz [Vytvoření aplikace .NET Core s moduly plug-in](../tutorials/creating-app-with-plugin-support.md) popisuje, jak vytvořit vlastní AssemblyLoadContext.</span><span class="sxs-lookup"><span data-stu-id="06072-119">The tutorial [Create a .NET Core application with plugins](../tutorials/creating-app-with-plugin-support.md) describes how to create a custom AssemblyLoadContext.</span></span> <span data-ttu-id="06072-120">Používá <xref:System.Runtime.Loader.AssemblyDependencyResolver> k vyřešení závislostí modulu plug-in.</span><span class="sxs-lookup"><span data-stu-id="06072-120">It uses an <xref:System.Runtime.Loader.AssemblyDependencyResolver> to resolve the dependencies of the plugin.</span></span> <span data-ttu-id="06072-121">Kurz správně izoluje závislosti modulu plug-in z hostující aplikace.</span><span class="sxs-lookup"><span data-stu-id="06072-121">The tutorial correctly isolates the plugin's dependencies from the hosting application.</span></span>

## <a name="how-to-use-and-debug-assembly-unloadability-in-net-core"></a><span data-ttu-id="06072-122">Jak se používá a ladí funkce zrušení načtení sestavení v .NET Core</span><span class="sxs-lookup"><span data-stu-id="06072-122">How to use and debug assembly unloadability in .NET Core</span></span>

<span data-ttu-id="06072-123">Podrobný kurz, [Jak používat a ladit nevytížení sestavení v článku .NET Core](../../standard/assembly/unloadability-howto.md) , je podrobný postup.</span><span class="sxs-lookup"><span data-stu-id="06072-123">The [How to use and debug assembly unloadability in .NET Core](../../standard/assembly/unloadability-howto.md) article is a step-by-step tutorial.</span></span> <span data-ttu-id="06072-124">Ukazuje, jak načíst aplikaci .NET Core, provést a poté ji uvolnit.</span><span class="sxs-lookup"><span data-stu-id="06072-124">It shows how to load a .NET Core application, execute, and then unload it.</span></span> <span data-ttu-id="06072-125">Článek také poskytuje tipy pro ladění.</span><span class="sxs-lookup"><span data-stu-id="06072-125">The article also provides debugging tips.</span></span>
