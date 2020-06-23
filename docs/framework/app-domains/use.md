---
title: Používání domén aplikací
description: Použijte aplikační domény, které poskytují jednotku izolace pro modul CLR (Common Language Runtime). Domény aplikace se vytvářejí a spouštějí v rámci procesu.
ms.date: 03/30/2017
helpviewer_keywords:
- application domains, about
- common language runtime, application domains
- runtime, application domains
ms.assetid: c6d99815-e022-4d2c-9420-1d7ab5b9d504
ms.openlocfilehash: df2a63716904ebfc6ee163121a1f07e53aa07514
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2020
ms.locfileid: "85105187"
---
# <a name="using-application-domains"></a><span data-ttu-id="00b85-104">Používání domén aplikací</span><span class="sxs-lookup"><span data-stu-id="00b85-104">Using Application Domains</span></span>

<span data-ttu-id="00b85-105">Aplikační domény poskytují jednotkovou izolaci pro modul CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="00b85-105">Application domains provide a unit of isolation for the common language runtime.</span></span> <span data-ttu-id="00b85-106">Jsou vytvořeny a spuštěny uvnitř procesu.</span><span class="sxs-lookup"><span data-stu-id="00b85-106">They are created and run inside a process.</span></span> <span data-ttu-id="00b85-107">Domény aplikace jsou obvykle vytvořeny hostitelem modulu runtime, což je aplikace zodpovědná za načtení modulu runtime do procesu a provádění kódu uživatele v doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="00b85-107">Application domains are usually created by a runtime host, which is an application responsible for loading the runtime into a process and executing user code within an application domain.</span></span> <span data-ttu-id="00b85-108">Hostitel modulu runtime vytvoří proces a výchozí doménu aplikace a spustí spravovaný kód uvnitř něj.</span><span class="sxs-lookup"><span data-stu-id="00b85-108">The runtime host creates a process and a default application domain, and runs managed code inside it.</span></span> <span data-ttu-id="00b85-109">Mezi hostitele modulu runtime patří ASP.NET, Microsoft Internet Explorer a prostředí systému Windows.</span><span class="sxs-lookup"><span data-stu-id="00b85-109">Runtime hosts include ASP.NET, Microsoft Internet Explorer, and the Windows shell.</span></span>  
  
<span data-ttu-id="00b85-110">Pro většinu aplikací nemusíte vytvářet vlastní doménu aplikace. hostitelský modul runtime vytvoří pro vás všechny potřebné aplikační domény.</span><span class="sxs-lookup"><span data-stu-id="00b85-110">For most applications, you do not need to create your own application domain; the runtime host creates any necessary application domains for you.</span></span> <span data-ttu-id="00b85-111">Můžete ale vytvořit a nakonfigurovat další aplikační domény, pokud vaše aplikace potřebuje izolovat kód nebo použít a uvolnit knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="00b85-111">However, you can create and configure additional application domains if your application needs to isolate code or to use and unload DLLs.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="00b85-112">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="00b85-112">In This Section</span></span>  

[<span data-ttu-id="00b85-113">Postupy: Vytvoření domény aplikace</span><span class="sxs-lookup"><span data-stu-id="00b85-113">How to: Create an Application Domain</span></span>](how-to-create-an-application-domain.md)  
<span data-ttu-id="00b85-114">Popisuje, jak programově vytvořit doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="00b85-114">Describes how to programmatically create an application domain.</span></span>  
  
[<span data-ttu-id="00b85-115">Postupy: Uvolnění domény aplikace</span><span class="sxs-lookup"><span data-stu-id="00b85-115">How to: Unload an Application Domain</span></span>](how-to-unload-an-application-domain.md)  
<span data-ttu-id="00b85-116">Popisuje způsob, jak programově uvolnit doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="00b85-116">Describes how to programmatically unload an application domain.</span></span>  
  
[<span data-ttu-id="00b85-117">Postupy: Konfigurace domény aplikace</span><span class="sxs-lookup"><span data-stu-id="00b85-117">How to: Configure an Application Domain</span></span>](how-to-configure-an-application-domain.md)  
<span data-ttu-id="00b85-118">Poskytuje Úvod ke konfiguraci domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="00b85-118">Provides an introduction to configuring an application domain.</span></span>  
  
[<span data-ttu-id="00b85-119">Načítání informací nastavení z domény aplikace</span><span class="sxs-lookup"><span data-stu-id="00b85-119">Retrieving Setup Information from an Application Domain</span></span>](retrieve-setup-information.md)  
<span data-ttu-id="00b85-120">Popisuje, jak načíst informace o instalaci z domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="00b85-120">Describes how to retrieve setup information from an application domain.</span></span>  
  
[<span data-ttu-id="00b85-121">Postupy: Načtení sestavení do domény aplikace</span><span class="sxs-lookup"><span data-stu-id="00b85-121">How to: Load Assemblies into an Application Domain</span></span>](how-to-load-assemblies-into-an-application-domain.md)  
<span data-ttu-id="00b85-122">Popisuje načtení sestavení do domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="00b85-122">Describes how to load an assembly into an application domain.</span></span>  
  
[<span data-ttu-id="00b85-123">Postupy: Získávání informací o typu a členu ze sestavení</span><span class="sxs-lookup"><span data-stu-id="00b85-123">How to: Obtain Type and Member Information from an Assembly</span></span>](../reflection-and-codedom/get-type-member-information.md)  
<span data-ttu-id="00b85-124">Popisuje, jak načíst informace o sestavení.</span><span class="sxs-lookup"><span data-stu-id="00b85-124">Describes how to retrieve information about an assembly.</span></span>  
  
[<span data-ttu-id="00b85-125">Stínové kopírování sestavení</span><span class="sxs-lookup"><span data-stu-id="00b85-125">Shadow Copying Assemblies</span></span>](shadow-copy-assemblies.md)  
<span data-ttu-id="00b85-126">Popisuje, jak stínové kopírování umožňuje aktualizace sestavení, když jsou používány, a jak nakonfigurovat stínové kopírování.</span><span class="sxs-lookup"><span data-stu-id="00b85-126">Describes how shadow copying allows updates to assemblies while they are in use, and how to configure shadow copying.</span></span>  
  
[<span data-ttu-id="00b85-127">Postupy: Přijímání oznámení o první odpovídající výjimce</span><span class="sxs-lookup"><span data-stu-id="00b85-127">How to: Receive First-Chance Exception Notifications</span></span>](how-to-receive-first-chance-exception-notifications.md)  
<span data-ttu-id="00b85-128">Vysvětluje, jak můžete obdržet oznámení o vyvolání výjimky před tím, než modul CLR (Common Language Runtime) začne hledat obslužné rutiny výjimek.</span><span class="sxs-lookup"><span data-stu-id="00b85-128">Explains how you can receive a notification that an exception has been thrown, before the common language runtime has begun searching for exception handlers.</span></span>  
  
[<span data-ttu-id="00b85-129">Řešení načítání sestavení</span><span class="sxs-lookup"><span data-stu-id="00b85-129">Resolving Assembly Loads</span></span>](../../standard/assembly/resolve-loads.md)  
<span data-ttu-id="00b85-130">Poskytuje pokyny <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> k použití události pro řešení selhání načtení sestavení.</span><span class="sxs-lookup"><span data-stu-id="00b85-130">Provides guidance on using the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event to resolve assembly load failures.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="00b85-131">Referenční informace</span><span class="sxs-lookup"><span data-stu-id="00b85-131">Reference</span></span>  

<xref:System.AppDomain>  
<span data-ttu-id="00b85-132">Představuje doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="00b85-132">Represents an application domain.</span></span> <span data-ttu-id="00b85-133">Poskytuje metody pro vytváření a řízení domén aplikací.</span><span class="sxs-lookup"><span data-stu-id="00b85-133">Provides methods for creating and controlling application domains.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="00b85-134">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="00b85-134">Related Sections</span></span>  
[<span data-ttu-id="00b85-135">Sestavení v .NET</span><span class="sxs-lookup"><span data-stu-id="00b85-135">Assemblies in .NET</span></span>](../../standard/assembly/index.md)  
<span data-ttu-id="00b85-136">Poskytuje přehled o funkcích, které provádí sestavení.</span><span class="sxs-lookup"><span data-stu-id="00b85-136">Provides an overview of the functions performed by assemblies.</span></span>  
  
[<span data-ttu-id="00b85-137">Programování se sestaveními</span><span class="sxs-lookup"><span data-stu-id="00b85-137">Programming with Assemblies</span></span>](../../standard/assembly/index.md)  
<span data-ttu-id="00b85-138">Popisuje způsob vytváření, podepisování a nastavení atributů v rámci sestavení.</span><span class="sxs-lookup"><span data-stu-id="00b85-138">Describes how to create, sign, and set attributes on assemblies.</span></span>  
  
[<span data-ttu-id="00b85-139">Generování dynamických metod a sestavení</span><span class="sxs-lookup"><span data-stu-id="00b85-139">Emitting Dynamic Methods and Assemblies</span></span>](../reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)  
<span data-ttu-id="00b85-140">Popisuje způsob vytváření dynamických sestavení.</span><span class="sxs-lookup"><span data-stu-id="00b85-140">Describes how to create dynamic assemblies.</span></span>  
  
[<span data-ttu-id="00b85-141">Aplikační domény</span><span class="sxs-lookup"><span data-stu-id="00b85-141">Application Domains</span></span>](application-domains.md)  
<span data-ttu-id="00b85-142">Poskytuje koncepční přehled domén aplikací.</span><span class="sxs-lookup"><span data-stu-id="00b85-142">Provides a conceptual overview of application domains.</span></span>  
  
[<span data-ttu-id="00b85-143">Přehled reflexe</span><span class="sxs-lookup"><span data-stu-id="00b85-143">Reflection Overview</span></span>](../reflection-and-codedom/reflection.md)  
<span data-ttu-id="00b85-144">Popisuje způsob použití třídy **reflexe** k získání informací o sestavení.</span><span class="sxs-lookup"><span data-stu-id="00b85-144">Describes how to use the **Reflection** class to obtain information about an assembly.</span></span>
