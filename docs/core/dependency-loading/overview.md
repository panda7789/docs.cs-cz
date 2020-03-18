---
title: Načítání závislostí - jádro .NET Core
description: Přehled načítání spravovaných a nespravovaných závislostí v jádru rozhraní .NET
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.topic: overview
ms.openlocfilehash: f6b5fc1f92171b61dcab162b782ca7212c602d76
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "73416669"
---
# <a name="dependency-loading-in-net-core"></a><span data-ttu-id="e1c32-103">Načítání závislostí v jádru rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="e1c32-103">Dependency loading in .NET Core</span></span>

<span data-ttu-id="e1c32-104">Každá aplikace .NET Core má závislosti.</span><span class="sxs-lookup"><span data-stu-id="e1c32-104">Every .NET Core application has dependencies.</span></span> <span data-ttu-id="e1c32-105">I jednoduchá `hello world` aplikace má závislosti na částech knihoven tříd .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e1c32-105">Even the simple `hello world` app has dependencies on portions of the .NET Core class libraries.</span></span>

<span data-ttu-id="e1c32-106">Principy logiky načítání výchozího sestavení jádra .NET mohou pomoci pochopit a ladit typické problémy s nasazením.</span><span class="sxs-lookup"><span data-stu-id="e1c32-106">Understanding .NET Core default assembly loading logic can help understanding and debugging typical deployment issues.</span></span>

<span data-ttu-id="e1c32-107">V některých aplikacích jsou závislosti dynamicky určeny za běhu.</span><span class="sxs-lookup"><span data-stu-id="e1c32-107">In some applications, dependencies are dynamically determined at runtime.</span></span> <span data-ttu-id="e1c32-108">V těchto situacích je důležité pochopit, jak jsou načtena spravovaná sestavení a nespravované závislosti.</span><span class="sxs-lookup"><span data-stu-id="e1c32-108">In these situations, it's critical to understand how managed assemblies and unmanaged dependencies are loaded.</span></span>

## <a name="understanding-assemblyloadcontext"></a><span data-ttu-id="e1c32-109">Vysvětlení používání třídy AssemblyLoadContext</span><span class="sxs-lookup"><span data-stu-id="e1c32-109">Understanding AssemblyLoadContext</span></span>

<span data-ttu-id="e1c32-110">Rozhraní <xref:System.Runtime.Loader.AssemblyLoadContext> API je centrální pro návrh načítání jádra .NET.</span><span class="sxs-lookup"><span data-stu-id="e1c32-110">The <xref:System.Runtime.Loader.AssemblyLoadContext> API is central to the .NET Core loading design.</span></span> <span data-ttu-id="e1c32-111">[Principy AssemblyLoadContext](understanding-assemblyloadcontext.md) článek poskytuje koncepční přehled návrhu.</span><span class="sxs-lookup"><span data-stu-id="e1c32-111">The [Understanding AssemblyLoadContext](understanding-assemblyloadcontext.md) article provides a conceptual overview to the design.</span></span>

## <a name="loading-details"></a><span data-ttu-id="e1c32-112">Podrobné informace o načítání</span><span class="sxs-lookup"><span data-stu-id="e1c32-112">Loading details</span></span>

<span data-ttu-id="e1c32-113">Podrobnosti algoritmu načítání jsou stručně popsány v několika článcích:</span><span class="sxs-lookup"><span data-stu-id="e1c32-113">The loading algorithm details are covered briefly in several articles:</span></span>

- [<span data-ttu-id="e1c32-114">Algoritmus načítání spravovaného sestavení</span><span class="sxs-lookup"><span data-stu-id="e1c32-114">Managed assembly loading algorithm</span></span>](loading-managed.md)
- [<span data-ttu-id="e1c32-115">Algoritmus satelitního nakládacího systému</span><span class="sxs-lookup"><span data-stu-id="e1c32-115">Satellite assembly loading algorithm</span></span>](loading-resources.md)
- [<span data-ttu-id="e1c32-116">Algoritmus načítání nespravované (nativní) knihovny</span><span class="sxs-lookup"><span data-stu-id="e1c32-116">Unmanaged (native) library loading algorithm</span></span>](loading-unmanaged.md)
- [<span data-ttu-id="e1c32-117">Výchozí zjišťování</span><span class="sxs-lookup"><span data-stu-id="e1c32-117">Default probing</span></span>](default-probing.md)

## <a name="create-a-net-core-application-with-plugins"></a><span data-ttu-id="e1c32-118">Vytvoření aplikace .NET Core pomocí modulů plug-in</span><span class="sxs-lookup"><span data-stu-id="e1c32-118">Create a .NET Core application with plugins</span></span>

<span data-ttu-id="e1c32-119">Kurz [Vytvoření aplikace .NET Core s pluginy](../tutorials/creating-app-with-plugin-support.md) popisuje, jak vytvořit vlastní AssemblyLoadContext.</span><span class="sxs-lookup"><span data-stu-id="e1c32-119">The tutorial [Create a .NET Core application with plugins](../tutorials/creating-app-with-plugin-support.md) describes how to create a custom AssemblyLoadContext.</span></span> <span data-ttu-id="e1c32-120">Používá k <xref:System.Runtime.Loader.AssemblyDependencyResolver> vyřešení závislosti pluginu.</span><span class="sxs-lookup"><span data-stu-id="e1c32-120">It uses an <xref:System.Runtime.Loader.AssemblyDependencyResolver> to resolve the dependencies of the plugin.</span></span> <span data-ttu-id="e1c32-121">Výukový program správně izoluje závislosti pluginu z hostitelské aplikace.</span><span class="sxs-lookup"><span data-stu-id="e1c32-121">The tutorial correctly isolates the plugin's dependencies from the hosting application.</span></span>

## <a name="how-to-use-and-debug-assembly-unloadability-in-net-core"></a><span data-ttu-id="e1c32-122">Jak se používá a ladí funkce zrušení načtení sestavení v .NET Core</span><span class="sxs-lookup"><span data-stu-id="e1c32-122">How to use and debug assembly unloadability in .NET Core</span></span>

<span data-ttu-id="e1c32-123">[Použití a ladění sestavení uvolnitelnost v](../../standard/assembly/unloadability.md) článku .NET Core je podrobný kurz.</span><span class="sxs-lookup"><span data-stu-id="e1c32-123">The [How to use and debug assembly unloadability in .NET Core](../../standard/assembly/unloadability.md) article is a step-by-step tutorial.</span></span> <span data-ttu-id="e1c32-124">Ukazuje, jak načíst aplikaci .NET Core, spustit a potom ji uvolnit.</span><span class="sxs-lookup"><span data-stu-id="e1c32-124">It shows how to load a .NET Core application, execute, and then unload it.</span></span> <span data-ttu-id="e1c32-125">Článek také obsahuje tipy pro ladění.</span><span class="sxs-lookup"><span data-stu-id="e1c32-125">The article also provides debugging tips.</span></span>
