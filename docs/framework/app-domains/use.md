---
title: "Používání domén aplikací"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application domains, about
- common language runtime, application domains
- runtime, application domains
ms.assetid: c6d99815-e022-4d2c-9420-1d7ab5b9d504
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 53180d5d3d9314c3f078ddca8f5c155b01981f4e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="using-application-domains"></a><span data-ttu-id="c31cf-102">Používání domén aplikací</span><span class="sxs-lookup"><span data-stu-id="c31cf-102">Using Application Domains</span></span>
<span data-ttu-id="c31cf-103">Aplikační domény zadejte jednotku pro izolaci pro modul common language runtime.</span><span class="sxs-lookup"><span data-stu-id="c31cf-103">Application domains provide a unit of isolation for the common language runtime.</span></span> <span data-ttu-id="c31cf-104">Jsou vytvořeny a spustit uvnitř proces.</span><span class="sxs-lookup"><span data-stu-id="c31cf-104">They are created and run inside a process.</span></span> <span data-ttu-id="c31cf-105">Aplikační domény jsou obvykle vytvořené pomocí modulu runtime hostitele, který je zodpovědný za načítání modulu runtime do procesu a spuštění uživatelského kódu v rámci domény aplikace aplikace.</span><span class="sxs-lookup"><span data-stu-id="c31cf-105">Application domains are usually created by a runtime host, which is an application responsible for loading the runtime into a process and executing user code within an application domain.</span></span> <span data-ttu-id="c31cf-106">Hostitel modulu runtime vytvoří proces a výchozí doménu aplikace a spustí spravovaný kód je uvnitř.</span><span class="sxs-lookup"><span data-stu-id="c31cf-106">The runtime host creates a process and a default application domain, and runs managed code inside it.</span></span> <span data-ttu-id="c31cf-107">Modulu runtime zahrnout ASP.NET, aplikace Microsoft Internet Explorer a prostředí systému Windows.</span><span class="sxs-lookup"><span data-stu-id="c31cf-107">Runtime hosts include ASP.NET, Microsoft Internet Explorer, and the Windows shell.</span></span>  
  
 <span data-ttu-id="c31cf-108">Pro většinu aplikací není nutné k vytvoření vlastní domény aplikace. hostitel modulu runtime pro vás vytvoří všechny nezbytné domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="c31cf-108">For most applications, you do not need to create your own application domain; the runtime host creates any necessary application domains for you.</span></span> <span data-ttu-id="c31cf-109">Můžete však vytvořit a nakonfigurovat další domény aplikace, pokud aplikace potřebuje izolovat kódu nebo použití a uvolnění knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="c31cf-109">However, you can create and configure additional application domains if your application needs to isolate code or to use and unload DLLs.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c31cf-110">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="c31cf-110">In This Section</span></span>  
 [<span data-ttu-id="c31cf-111">Postupy: vytvoření domény aplikace</span><span class="sxs-lookup"><span data-stu-id="c31cf-111">How to: Create an Application Domain</span></span>](../../../docs/framework/app-domains/how-to-create-an-application-domain.md)  
 <span data-ttu-id="c31cf-112">Popisuje postup vytváření domény aplikace prostřednictvím kódu programu.</span><span class="sxs-lookup"><span data-stu-id="c31cf-112">Describes how to programmatically create an application domain.</span></span>  
  
 [<span data-ttu-id="c31cf-113">Postupy: uvolnění domény aplikace</span><span class="sxs-lookup"><span data-stu-id="c31cf-113">How to: Unload an Application Domain</span></span>](../../../docs/framework/app-domains/how-to-unload-an-application-domain.md)  
 <span data-ttu-id="c31cf-114">Popisuje, jak programově uvolnění domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="c31cf-114">Describes how to programmatically unload an application domain.</span></span>  
  
 [<span data-ttu-id="c31cf-115">Postupy: Konfigurace domény aplikace</span><span class="sxs-lookup"><span data-stu-id="c31cf-115">How to: Configure an Application Domain</span></span>](../../../docs/framework/app-domains/how-to-configure-an-application-domain.md)  
 <span data-ttu-id="c31cf-116">Poskytuje úvod do konfigurace domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="c31cf-116">Provides an introduction to configuring an application domain.</span></span>  
  
 [<span data-ttu-id="c31cf-117">Načítání informací nastavení z domény aplikace</span><span class="sxs-lookup"><span data-stu-id="c31cf-117">Retrieving Setup Information from an Application Domain</span></span>](../../../docs/framework/app-domains/retrieve-setup-information.md)  
 <span data-ttu-id="c31cf-118">Popisuje, jak načíst informace o instalaci z domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="c31cf-118">Describes how to retrieve setup information from an application domain.</span></span>  
  
 [<span data-ttu-id="c31cf-119">Postupy: načtení sestavení do domény aplikace</span><span class="sxs-lookup"><span data-stu-id="c31cf-119">How to: Load Assemblies into an Application Domain</span></span>](../../../docs/framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)  
 <span data-ttu-id="c31cf-120">Popisuje, jak načíst sestavení do domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="c31cf-120">Describes how to load an assembly into an application domain.</span></span>  
  
 [<span data-ttu-id="c31cf-121">Postupy: získání typ a informace o členech ze sestavení</span><span class="sxs-lookup"><span data-stu-id="c31cf-121">How to: Obtain Type and Member Information from an Assembly</span></span>](../../../docs/framework/app-domains/how-to-obtain-type-and-member-information-from-an-assembly.md)  
 <span data-ttu-id="c31cf-122">Popisuje, jak načíst informace o sestavení.</span><span class="sxs-lookup"><span data-stu-id="c31cf-122">Describes how to retrieve information about an assembly.</span></span>  
  
 [<span data-ttu-id="c31cf-123">Stínové kopírování sestavení</span><span class="sxs-lookup"><span data-stu-id="c31cf-123">Shadow Copying Assemblies</span></span>](../../../docs/framework/app-domains/shadow-copy-assemblies.md)  
 <span data-ttu-id="c31cf-124">Popisuje, jak stínové kopírování umožňuje aktualizace sestavení při se používají a postup konfigurace stínové kopírování sestavení.</span><span class="sxs-lookup"><span data-stu-id="c31cf-124">Describes how shadow copying allows updates to assemblies while they are in use, and how to configure shadow copying.</span></span>  
  
 [<span data-ttu-id="c31cf-125">Postupy: přijímání oznámení o první odpovídající výjimce</span><span class="sxs-lookup"><span data-stu-id="c31cf-125">How to: Receive First-Chance Exception Notifications</span></span>](../../../docs/framework/app-domains/how-to-receive-first-chance-exception-notifications.md)  
 <span data-ttu-id="c31cf-126">Vysvětluje, jak může přijímat oznámení, že byla vyvolána výjimka, než začne modul common language runtime hledat obslužné rutiny výjimek.</span><span class="sxs-lookup"><span data-stu-id="c31cf-126">Explains how you can receive a notification that an exception has been thrown, before the common language runtime has begun searching for exception handlers.</span></span>  
  
 [<span data-ttu-id="c31cf-127">Řešení načítání sestavení</span><span class="sxs-lookup"><span data-stu-id="c31cf-127">Resolving Assembly Loads</span></span>](../../../docs/framework/app-domains/resolve-assembly-loads.md)  
 <span data-ttu-id="c31cf-128">Obsahuje informace o použití <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> událostí k vyřešení selhání načtení sestavení.</span><span class="sxs-lookup"><span data-stu-id="c31cf-128">Provides guidance on using the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event to resolve assembly load failures.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="c31cf-129">Odkaz</span><span class="sxs-lookup"><span data-stu-id="c31cf-129">Reference</span></span>  
 <xref:System.AppDomain>  
 <span data-ttu-id="c31cf-130">Představuje domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="c31cf-130">Represents an application domain.</span></span> <span data-ttu-id="c31cf-131">Poskytuje metody pro vytváření a řízení aplikační domény.</span><span class="sxs-lookup"><span data-stu-id="c31cf-131">Provides methods for creating and controlling application domains.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c31cf-132">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="c31cf-132">Related Sections</span></span>  
 [<span data-ttu-id="c31cf-133">Sestavení v modulu Common Language Runtime</span><span class="sxs-lookup"><span data-stu-id="c31cf-133">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 <span data-ttu-id="c31cf-134">Obsahuje přehled funkce provádí sestavení.</span><span class="sxs-lookup"><span data-stu-id="c31cf-134">Provides an overview of the functions performed by assemblies.</span></span>  
  
 [<span data-ttu-id="c31cf-135">Programování se sestaveními</span><span class="sxs-lookup"><span data-stu-id="c31cf-135">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 <span data-ttu-id="c31cf-136">Popisuje způsob vytváření, podepisování a nastavení atributů v rámci sestavení.</span><span class="sxs-lookup"><span data-stu-id="c31cf-136">Describes how to create, sign, and set attributes on assemblies.</span></span>  
  
 [<span data-ttu-id="c31cf-137">Emitování dynamických metod a sestavení</span><span class="sxs-lookup"><span data-stu-id="c31cf-137">Emitting Dynamic Methods and Assemblies</span></span>](../../../docs/framework/reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)  
 <span data-ttu-id="c31cf-138">Popisuje způsob vytváření dynamických sestavení.</span><span class="sxs-lookup"><span data-stu-id="c31cf-138">Describes how to create dynamic assemblies.</span></span>  
  
 [<span data-ttu-id="c31cf-139">Aplikační domény</span><span class="sxs-lookup"><span data-stu-id="c31cf-139">Application Domains</span></span>](../../../docs/framework/app-domains/application-domains.md)  
 <span data-ttu-id="c31cf-140">Poskytuje koncepční přehled domén aplikací.</span><span class="sxs-lookup"><span data-stu-id="c31cf-140">Provides a conceptual overview of application domains.</span></span>  
  
 [<span data-ttu-id="c31cf-141">Přehled reflexe</span><span class="sxs-lookup"><span data-stu-id="c31cf-141">Reflection Overview</span></span>](../../../docs/framework/reflection-and-codedom/reflection.md)  
 <span data-ttu-id="c31cf-142">Popisuje postup použití **reflexe** třída získat informace o sestavení.</span><span class="sxs-lookup"><span data-stu-id="c31cf-142">Describes how to use the **Reflection** class to obtain information about an assembly.</span></span>
