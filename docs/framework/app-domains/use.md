---
title: Používání domén aplikací
ms.date: 03/30/2017
helpviewer_keywords:
- application domains, about
- common language runtime, application domains
- runtime, application domains
ms.assetid: c6d99815-e022-4d2c-9420-1d7ab5b9d504
ms.openlocfilehash: 6ee02a3f27a645f19fd6a327052939586fac4aa9
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645426"
---
# <a name="using-application-domains"></a><span data-ttu-id="27514-102">Používání domén aplikací</span><span class="sxs-lookup"><span data-stu-id="27514-102">Using Application Domains</span></span>

<span data-ttu-id="27514-103">Aplikační domény poskytují jednotkovou izolaci pro modul CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="27514-103">Application domains provide a unit of isolation for the common language runtime.</span></span> <span data-ttu-id="27514-104">Jsou vytvořeny a spuštěny uvnitř procesu.</span><span class="sxs-lookup"><span data-stu-id="27514-104">They are created and run inside a process.</span></span> <span data-ttu-id="27514-105">Domény aplikace jsou obvykle vytvořeny hostitelem modulu runtime, což je aplikace zodpovědná za načtení modulu runtime do procesu a provádění kódu uživatele v doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="27514-105">Application domains are usually created by a runtime host, which is an application responsible for loading the runtime into a process and executing user code within an application domain.</span></span> <span data-ttu-id="27514-106">Hostitel modulu runtime vytvoří proces a výchozí doménu aplikace a spustí spravovaný kód uvnitř něj.</span><span class="sxs-lookup"><span data-stu-id="27514-106">The runtime host creates a process and a default application domain, and runs managed code inside it.</span></span> <span data-ttu-id="27514-107">Mezi hostitele modulu runtime patří ASP.NET, Microsoft Internet Explorer a prostředí systému Windows.</span><span class="sxs-lookup"><span data-stu-id="27514-107">Runtime hosts include ASP.NET, Microsoft Internet Explorer, and the Windows shell.</span></span>  
  
<span data-ttu-id="27514-108">Pro většinu aplikací nemusíte vytvářet vlastní doménu aplikace. hostitelský modul runtime vytvoří pro vás všechny potřebné aplikační domény.</span><span class="sxs-lookup"><span data-stu-id="27514-108">For most applications, you do not need to create your own application domain; the runtime host creates any necessary application domains for you.</span></span> <span data-ttu-id="27514-109">Můžete ale vytvořit a nakonfigurovat další aplikační domény, pokud vaše aplikace potřebuje izolovat kód nebo použít a uvolnit knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="27514-109">However, you can create and configure additional application domains if your application needs to isolate code or to use and unload DLLs.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="27514-110">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="27514-110">In This Section</span></span>  

[<span data-ttu-id="27514-111">Postupy: Vytvoření domény aplikace</span><span class="sxs-lookup"><span data-stu-id="27514-111">How to: Create an Application Domain</span></span>](how-to-create-an-application-domain.md)  
<span data-ttu-id="27514-112">Popisuje, jak programově vytvořit doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="27514-112">Describes how to programmatically create an application domain.</span></span>  
  
[<span data-ttu-id="27514-113">Postupy: Uvolnění domény aplikace</span><span class="sxs-lookup"><span data-stu-id="27514-113">How to: Unload an Application Domain</span></span>](how-to-unload-an-application-domain.md)  
<span data-ttu-id="27514-114">Popisuje způsob, jak programově uvolnit doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="27514-114">Describes how to programmatically unload an application domain.</span></span>  
  
[<span data-ttu-id="27514-115">Postupy: Konfigurace domény aplikace</span><span class="sxs-lookup"><span data-stu-id="27514-115">How to: Configure an Application Domain</span></span>](how-to-configure-an-application-domain.md)  
<span data-ttu-id="27514-116">Poskytuje Úvod ke konfiguraci domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="27514-116">Provides an introduction to configuring an application domain.</span></span>  
  
[<span data-ttu-id="27514-117">Načítání informací nastavení z domény aplikace</span><span class="sxs-lookup"><span data-stu-id="27514-117">Retrieving Setup Information from an Application Domain</span></span>](retrieve-setup-information.md)  
<span data-ttu-id="27514-118">Popisuje, jak načíst informace o instalaci z domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="27514-118">Describes how to retrieve setup information from an application domain.</span></span>  
  
[<span data-ttu-id="27514-119">Postupy: Načtení sestavení do domény aplikace</span><span class="sxs-lookup"><span data-stu-id="27514-119">How to: Load Assemblies into an Application Domain</span></span>](how-to-load-assemblies-into-an-application-domain.md)  
<span data-ttu-id="27514-120">Popisuje načtení sestavení do domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="27514-120">Describes how to load an assembly into an application domain.</span></span>  
  
[<span data-ttu-id="27514-121">Postupy: Získávání informací o typu a členu ze sestavení</span><span class="sxs-lookup"><span data-stu-id="27514-121">How to: Obtain Type and Member Information from an Assembly</span></span>](../reflection-and-codedom/get-type-member-information.md)  
<span data-ttu-id="27514-122">Popisuje, jak načíst informace o sestavení.</span><span class="sxs-lookup"><span data-stu-id="27514-122">Describes how to retrieve information about an assembly.</span></span>  
  
[<span data-ttu-id="27514-123">Stínové kopírování sestavení</span><span class="sxs-lookup"><span data-stu-id="27514-123">Shadow Copying Assemblies</span></span>](shadow-copy-assemblies.md)  
<span data-ttu-id="27514-124">Popisuje, jak stínové kopírování umožňuje aktualizace sestavení, když jsou používány, a jak nakonfigurovat stínové kopírování.</span><span class="sxs-lookup"><span data-stu-id="27514-124">Describes how shadow copying allows updates to assemblies while they are in use, and how to configure shadow copying.</span></span>  
  
[<span data-ttu-id="27514-125">Postupy: Přijímání oznámení o první odpovídající výjimce</span><span class="sxs-lookup"><span data-stu-id="27514-125">How to: Receive First-Chance Exception Notifications</span></span>](how-to-receive-first-chance-exception-notifications.md)  
<span data-ttu-id="27514-126">Vysvětluje, jak můžete obdržet oznámení o vyvolání výjimky před tím, než modul CLR (Common Language Runtime) začne hledat obslužné rutiny výjimek.</span><span class="sxs-lookup"><span data-stu-id="27514-126">Explains how you can receive a notification that an exception has been thrown, before the common language runtime has begun searching for exception handlers.</span></span>  
  
[<span data-ttu-id="27514-127">Řešení načítání sestavení</span><span class="sxs-lookup"><span data-stu-id="27514-127">Resolving Assembly Loads</span></span>](../../standard/assembly/resolve-loads.md)  
<span data-ttu-id="27514-128">Poskytuje pokyny k použití <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> události pro řešení selhání načtení sestavení.</span><span class="sxs-lookup"><span data-stu-id="27514-128">Provides guidance on using the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event to resolve assembly load failures.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="27514-129">Referenční informace</span><span class="sxs-lookup"><span data-stu-id="27514-129">Reference</span></span>  

<xref:System.AppDomain>  
<span data-ttu-id="27514-130">Představuje doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="27514-130">Represents an application domain.</span></span> <span data-ttu-id="27514-131">Poskytuje metody pro vytváření a řízení domén aplikací.</span><span class="sxs-lookup"><span data-stu-id="27514-131">Provides methods for creating and controlling application domains.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="27514-132">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="27514-132">Related Sections</span></span>  
[<span data-ttu-id="27514-133">Sestavení v .NET</span><span class="sxs-lookup"><span data-stu-id="27514-133">Assemblies in .NET</span></span>](../../standard/assembly/index.md)  
<span data-ttu-id="27514-134">Poskytuje přehled o funkcích, které provádí sestavení.</span><span class="sxs-lookup"><span data-stu-id="27514-134">Provides an overview of the functions performed by assemblies.</span></span>  
  
[<span data-ttu-id="27514-135">Programování se sestaveními</span><span class="sxs-lookup"><span data-stu-id="27514-135">Programming with Assemblies</span></span>](../../standard/assembly/index.md)  
<span data-ttu-id="27514-136">Popisuje způsob vytváření, podepisování a nastavení atributů v rámci sestavení.</span><span class="sxs-lookup"><span data-stu-id="27514-136">Describes how to create, sign, and set attributes on assemblies.</span></span>  
  
[<span data-ttu-id="27514-137">Generování dynamických metod a sestavení</span><span class="sxs-lookup"><span data-stu-id="27514-137">Emitting Dynamic Methods and Assemblies</span></span>](../reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)  
<span data-ttu-id="27514-138">Popisuje způsob vytváření dynamických sestavení.</span><span class="sxs-lookup"><span data-stu-id="27514-138">Describes how to create dynamic assemblies.</span></span>  
  
[<span data-ttu-id="27514-139">Aplikační domény</span><span class="sxs-lookup"><span data-stu-id="27514-139">Application Domains</span></span>](application-domains.md)  
<span data-ttu-id="27514-140">Poskytuje koncepční přehled domén aplikací.</span><span class="sxs-lookup"><span data-stu-id="27514-140">Provides a conceptual overview of application domains.</span></span>  
  
[<span data-ttu-id="27514-141">Přehled reflexe</span><span class="sxs-lookup"><span data-stu-id="27514-141">Reflection Overview</span></span>](../reflection-and-codedom/reflection.md)  
<span data-ttu-id="27514-142">Popisuje způsob použití třídy **reflexe** k získání informací o sestavení.</span><span class="sxs-lookup"><span data-stu-id="27514-142">Describes how to use the **Reflection** class to obtain information about an assembly.</span></span>
