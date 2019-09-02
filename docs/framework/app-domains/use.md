---
title: Používání domén aplikací
ms.date: 03/30/2017
helpviewer_keywords:
- application domains, about
- common language runtime, application domains
- runtime, application domains
ms.assetid: c6d99815-e022-4d2c-9420-1d7ab5b9d504
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5ebd1de46eb2757098a369b58dd9a6c0009e5b95
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2019
ms.locfileid: "61674884"
---
# <a name="using-application-domains"></a><span data-ttu-id="75de5-102">Používání domén aplikací</span><span class="sxs-lookup"><span data-stu-id="75de5-102">Using Application Domains</span></span>
<span data-ttu-id="75de5-103">Aplikační domény poskytují jednotkovou izolaci pro modul CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="75de5-103">Application domains provide a unit of isolation for the common language runtime.</span></span> <span data-ttu-id="75de5-104">Jsou vytvořeny a spuštěny uvnitř procesu.</span><span class="sxs-lookup"><span data-stu-id="75de5-104">They are created and run inside a process.</span></span> <span data-ttu-id="75de5-105">Domény aplikace jsou obvykle vytvořeny hostitelem modulu runtime, což je aplikace zodpovědná za načtení modulu runtime do procesu a provádění kódu uživatele v doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="75de5-105">Application domains are usually created by a runtime host, which is an application responsible for loading the runtime into a process and executing user code within an application domain.</span></span> <span data-ttu-id="75de5-106">Hostitel modulu runtime vytvoří proces a výchozí doménu aplikace a spustí spravovaný kód uvnitř něj.</span><span class="sxs-lookup"><span data-stu-id="75de5-106">The runtime host creates a process and a default application domain, and runs managed code inside it.</span></span> <span data-ttu-id="75de5-107">Mezi hostitele modulu runtime patří ASP.NET, Microsoft Internet Explorer a prostředí systému Windows.</span><span class="sxs-lookup"><span data-stu-id="75de5-107">Runtime hosts include ASP.NET, Microsoft Internet Explorer, and the Windows shell.</span></span>  
  
 <span data-ttu-id="75de5-108">Pro většinu aplikací nemusíte vytvářet vlastní doménu aplikace. hostitelský modul runtime vytvoří pro vás všechny potřebné aplikační domény.</span><span class="sxs-lookup"><span data-stu-id="75de5-108">For most applications, you do not need to create your own application domain; the runtime host creates any necessary application domains for you.</span></span> <span data-ttu-id="75de5-109">Můžete ale vytvořit a nakonfigurovat další aplikační domény, pokud vaše aplikace potřebuje izolovat kód nebo použít a uvolnit knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="75de5-109">However, you can create and configure additional application domains if your application needs to isolate code or to use and unload DLLs.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="75de5-110">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="75de5-110">In This Section</span></span>  
 [<span data-ttu-id="75de5-111">Postupy: Vytvoření domény aplikace</span><span class="sxs-lookup"><span data-stu-id="75de5-111">How to: Create an Application Domain</span></span>](../../../docs/framework/app-domains/how-to-create-an-application-domain.md)  
 <span data-ttu-id="75de5-112">Popisuje, jak programově vytvořit doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="75de5-112">Describes how to programmatically create an application domain.</span></span>  
  
 [<span data-ttu-id="75de5-113">Postupy: Uvolnění domény aplikace</span><span class="sxs-lookup"><span data-stu-id="75de5-113">How to: Unload an Application Domain</span></span>](../../../docs/framework/app-domains/how-to-unload-an-application-domain.md)  
 <span data-ttu-id="75de5-114">Popisuje způsob, jak programově uvolnit doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="75de5-114">Describes how to programmatically unload an application domain.</span></span>  
  
 [<span data-ttu-id="75de5-115">Postupy: Konfigurace domény aplikace</span><span class="sxs-lookup"><span data-stu-id="75de5-115">How to: Configure an Application Domain</span></span>](../../../docs/framework/app-domains/how-to-configure-an-application-domain.md)  
 <span data-ttu-id="75de5-116">Poskytuje Úvod ke konfiguraci domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="75de5-116">Provides an introduction to configuring an application domain.</span></span>  
  
 [<span data-ttu-id="75de5-117">Načítání informací nastavení z domény aplikace</span><span class="sxs-lookup"><span data-stu-id="75de5-117">Retrieving Setup Information from an Application Domain</span></span>](../../../docs/framework/app-domains/retrieve-setup-information.md)  
 <span data-ttu-id="75de5-118">Popisuje, jak načíst informace o instalaci z domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="75de5-118">Describes how to retrieve setup information from an application domain.</span></span>  
  
 [<span data-ttu-id="75de5-119">Postupy: Načtení sestavení do domény aplikace</span><span class="sxs-lookup"><span data-stu-id="75de5-119">How to: Load Assemblies into an Application Domain</span></span>](../../../docs/framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)  
 <span data-ttu-id="75de5-120">Popisuje načtení sestavení do domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="75de5-120">Describes how to load an assembly into an application domain.</span></span>  
  
 [<span data-ttu-id="75de5-121">Postupy: Získání informací o typu a členu ze sestavení</span><span class="sxs-lookup"><span data-stu-id="75de5-121">How to: Obtain Type and Member Information from an Assembly</span></span>](../../../docs/framework/app-domains/how-to-obtain-type-and-member-information-from-an-assembly.md)  
 <span data-ttu-id="75de5-122">Popisuje, jak načíst informace o sestavení.</span><span class="sxs-lookup"><span data-stu-id="75de5-122">Describes how to retrieve information about an assembly.</span></span>  
  
 [<span data-ttu-id="75de5-123">Stínové kopírování sestavení</span><span class="sxs-lookup"><span data-stu-id="75de5-123">Shadow Copying Assemblies</span></span>](../../../docs/framework/app-domains/shadow-copy-assemblies.md)  
 <span data-ttu-id="75de5-124">Popisuje, jak stínové kopírování umožňuje aktualizace sestavení, když jsou používány, a jak nakonfigurovat stínové kopírování.</span><span class="sxs-lookup"><span data-stu-id="75de5-124">Describes how shadow copying allows updates to assemblies while they are in use, and how to configure shadow copying.</span></span>  
  
 [<span data-ttu-id="75de5-125">Postupy: Přijetí oznámení o první pravděpodobné výjimce</span><span class="sxs-lookup"><span data-stu-id="75de5-125">How to: Receive First-Chance Exception Notifications</span></span>](../../../docs/framework/app-domains/how-to-receive-first-chance-exception-notifications.md)  
 <span data-ttu-id="75de5-126">Vysvětluje, jak můžete obdržet oznámení o vyvolání výjimky před tím, než modul CLR (Common Language Runtime) začne hledat obslužné rutiny výjimek.</span><span class="sxs-lookup"><span data-stu-id="75de5-126">Explains how you can receive a notification that an exception has been thrown, before the common language runtime has begun searching for exception handlers.</span></span>  
  
 [<span data-ttu-id="75de5-127">Řešení načítání sestavení</span><span class="sxs-lookup"><span data-stu-id="75de5-127">Resolving Assembly Loads</span></span>](../../../docs/framework/app-domains/resolve-assembly-loads.md)  
 <span data-ttu-id="75de5-128">Poskytuje pokyny k použití <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> události pro řešení selhání načtení sestavení.</span><span class="sxs-lookup"><span data-stu-id="75de5-128">Provides guidance on using the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event to resolve assembly load failures.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="75de5-129">Reference</span><span class="sxs-lookup"><span data-stu-id="75de5-129">Reference</span></span>  
 <xref:System.AppDomain>  
 <span data-ttu-id="75de5-130">Představuje doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="75de5-130">Represents an application domain.</span></span> <span data-ttu-id="75de5-131">Poskytuje metody pro vytváření a řízení domén aplikací.</span><span class="sxs-lookup"><span data-stu-id="75de5-131">Provides methods for creating and controlling application domains.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="75de5-132">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="75de5-132">Related Sections</span></span>  
 [<span data-ttu-id="75de5-133">Sestavení v modulu CLR (Common Language Runtime)</span><span class="sxs-lookup"><span data-stu-id="75de5-133">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 <span data-ttu-id="75de5-134">Poskytuje přehled o funkcích, které provádí sestavení.</span><span class="sxs-lookup"><span data-stu-id="75de5-134">Provides an overview of the functions performed by assemblies.</span></span>  
  
 [<span data-ttu-id="75de5-135">Programování se sestaveními</span><span class="sxs-lookup"><span data-stu-id="75de5-135">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 <span data-ttu-id="75de5-136">Popisuje způsob vytváření, podepisování a nastavení atributů v rámci sestavení.</span><span class="sxs-lookup"><span data-stu-id="75de5-136">Describes how to create, sign, and set attributes on assemblies.</span></span>  
  
 [<span data-ttu-id="75de5-137">Generování dynamických metod a sestavení</span><span class="sxs-lookup"><span data-stu-id="75de5-137">Emitting Dynamic Methods and Assemblies</span></span>](../../../docs/framework/reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)  
 <span data-ttu-id="75de5-138">Popisuje způsob vytváření dynamických sestavení.</span><span class="sxs-lookup"><span data-stu-id="75de5-138">Describes how to create dynamic assemblies.</span></span>  
  
 [<span data-ttu-id="75de5-139">Aplikační domény</span><span class="sxs-lookup"><span data-stu-id="75de5-139">Application Domains</span></span>](../../../docs/framework/app-domains/application-domains.md)  
 <span data-ttu-id="75de5-140">Poskytuje koncepční přehled domén aplikací.</span><span class="sxs-lookup"><span data-stu-id="75de5-140">Provides a conceptual overview of application domains.</span></span>  
  
 [<span data-ttu-id="75de5-141">Přehled reflexe</span><span class="sxs-lookup"><span data-stu-id="75de5-141">Reflection Overview</span></span>](../../../docs/framework/reflection-and-codedom/reflection.md)  
 <span data-ttu-id="75de5-142">Popisuje způsob použití třídy reflexe k získání informací o sestavení.</span><span class="sxs-lookup"><span data-stu-id="75de5-142">Describes how to use the **Reflection** class to obtain information about an assembly.</span></span>
