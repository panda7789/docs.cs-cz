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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61674884"
---
# <a name="using-application-domains"></a><span data-ttu-id="23fc0-102">Používání domén aplikací</span><span class="sxs-lookup"><span data-stu-id="23fc0-102">Using Application Domains</span></span>
<span data-ttu-id="23fc0-103">Aplikační domény poskytují jednotka izolace pro modul common language runtime.</span><span class="sxs-lookup"><span data-stu-id="23fc0-103">Application domains provide a unit of isolation for the common language runtime.</span></span> <span data-ttu-id="23fc0-104">Jsou vytvořeny a spuštění uvnitř procesu.</span><span class="sxs-lookup"><span data-stu-id="23fc0-104">They are created and run inside a process.</span></span> <span data-ttu-id="23fc0-105">Aplikační domény jsou obvykle vytvořeny od hostitele runtime, který je zodpovědný za načítání modulu runtime do procesu a provádění uživatelského kódu v rámci domény aplikace aplikace.</span><span class="sxs-lookup"><span data-stu-id="23fc0-105">Application domains are usually created by a runtime host, which is an application responsible for loading the runtime into a process and executing user code within an application domain.</span></span> <span data-ttu-id="23fc0-106">Hostitelský modul runtime vytvoří proces a výchozí domény aplikace a spouští spravovaný kód uvnitř.</span><span class="sxs-lookup"><span data-stu-id="23fc0-106">The runtime host creates a process and a default application domain, and runs managed code inside it.</span></span> <span data-ttu-id="23fc0-107">Hostitelská prostředí modulu runtime zahrnují technologie ASP.NET, Microsoft Internet Explorer a prostředí Windows.</span><span class="sxs-lookup"><span data-stu-id="23fc0-107">Runtime hosts include ASP.NET, Microsoft Internet Explorer, and the Windows shell.</span></span>  
  
 <span data-ttu-id="23fc0-108">Pro většinu aplikací nepotřebujete k vytvoření vlastní domény aplikace. hostitelský modul runtime vytvoří všechny nezbytné domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="23fc0-108">For most applications, you do not need to create your own application domain; the runtime host creates any necessary application domains for you.</span></span> <span data-ttu-id="23fc0-109">Můžete však vytvořit a nakonfigurovat další domény aplikace, pokud vaše aplikace potřebuje k izolaci kódu nebo použití a uvolnění knihoven DLL.</span><span class="sxs-lookup"><span data-stu-id="23fc0-109">However, you can create and configure additional application domains if your application needs to isolate code or to use and unload DLLs.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="23fc0-110">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="23fc0-110">In This Section</span></span>  
 [<span data-ttu-id="23fc0-111">Postupy: Vytvoření domény aplikace</span><span class="sxs-lookup"><span data-stu-id="23fc0-111">How to: Create an Application Domain</span></span>](../../../docs/framework/app-domains/how-to-create-an-application-domain.md)  
 <span data-ttu-id="23fc0-112">Popisuje, jak prostřednictvím kódu programu vytvořit doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="23fc0-112">Describes how to programmatically create an application domain.</span></span>  
  
 [<span data-ttu-id="23fc0-113">Postupy: Uvolnění domény aplikace</span><span class="sxs-lookup"><span data-stu-id="23fc0-113">How to: Unload an Application Domain</span></span>](../../../docs/framework/app-domains/how-to-unload-an-application-domain.md)  
 <span data-ttu-id="23fc0-114">Popisuje, jak prostřednictvím kódu programu uvolnění domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="23fc0-114">Describes how to programmatically unload an application domain.</span></span>  
  
 [<span data-ttu-id="23fc0-115">Postupy: Konfigurace domény aplikace</span><span class="sxs-lookup"><span data-stu-id="23fc0-115">How to: Configure an Application Domain</span></span>](../../../docs/framework/app-domains/how-to-configure-an-application-domain.md)  
 <span data-ttu-id="23fc0-116">Poskytuje úvod do konfigurace domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="23fc0-116">Provides an introduction to configuring an application domain.</span></span>  
  
 [<span data-ttu-id="23fc0-117">Načítání informací nastavení z domény aplikace</span><span class="sxs-lookup"><span data-stu-id="23fc0-117">Retrieving Setup Information from an Application Domain</span></span>](../../../docs/framework/app-domains/retrieve-setup-information.md)  
 <span data-ttu-id="23fc0-118">Popisuje, jak načíst informace o nastavení z domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="23fc0-118">Describes how to retrieve setup information from an application domain.</span></span>  
  
 [<span data-ttu-id="23fc0-119">Postupy: Načtení sestavení do domény aplikace</span><span class="sxs-lookup"><span data-stu-id="23fc0-119">How to: Load Assemblies into an Application Domain</span></span>](../../../docs/framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)  
 <span data-ttu-id="23fc0-120">Popisuje, jak načíst sestavení do domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="23fc0-120">Describes how to load an assembly into an application domain.</span></span>  
  
 [<span data-ttu-id="23fc0-121">Postupy: Získávání informací o člen typu a ze sestavení</span><span class="sxs-lookup"><span data-stu-id="23fc0-121">How to: Obtain Type and Member Information from an Assembly</span></span>](../../../docs/framework/app-domains/how-to-obtain-type-and-member-information-from-an-assembly.md)  
 <span data-ttu-id="23fc0-122">Popisuje, jak načíst informace o sestavení.</span><span class="sxs-lookup"><span data-stu-id="23fc0-122">Describes how to retrieve information about an assembly.</span></span>  
  
 [<span data-ttu-id="23fc0-123">Stínové kopírování sestavení</span><span class="sxs-lookup"><span data-stu-id="23fc0-123">Shadow Copying Assemblies</span></span>](../../../docs/framework/app-domains/shadow-copy-assemblies.md)  
 <span data-ttu-id="23fc0-124">Popisuje, jak stínové kopírování sestavení umožňuje instalaci aktualizací do sestavení za použití a jak konfigurovat stínové kopírování sestavení.</span><span class="sxs-lookup"><span data-stu-id="23fc0-124">Describes how shadow copying allows updates to assemblies while they are in use, and how to configure shadow copying.</span></span>  
  
 [<span data-ttu-id="23fc0-125">Postupy: Přijímání oznámení o první odpovídající výjimce</span><span class="sxs-lookup"><span data-stu-id="23fc0-125">How to: Receive First-Chance Exception Notifications</span></span>](../../../docs/framework/app-domains/how-to-receive-first-chance-exception-notifications.md)  
 <span data-ttu-id="23fc0-126">Vysvětluje, jak můžete dostávat oznámení, že byla vyvolána výjimka, než začne hledat obslužné rutiny výjimek common language runtime.</span><span class="sxs-lookup"><span data-stu-id="23fc0-126">Explains how you can receive a notification that an exception has been thrown, before the common language runtime has begun searching for exception handlers.</span></span>  
  
 [<span data-ttu-id="23fc0-127">Řešení načítání sestavení</span><span class="sxs-lookup"><span data-stu-id="23fc0-127">Resolving Assembly Loads</span></span>](../../../docs/framework/app-domains/resolve-assembly-loads.md)  
 <span data-ttu-id="23fc0-128">Obsahuje informace o použití <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> událostí k vyřešení selhání při načítání sestavení.</span><span class="sxs-lookup"><span data-stu-id="23fc0-128">Provides guidance on using the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event to resolve assembly load failures.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="23fc0-129">Odkaz</span><span class="sxs-lookup"><span data-stu-id="23fc0-129">Reference</span></span>  
 <xref:System.AppDomain>  
 <span data-ttu-id="23fc0-130">Představuje doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="23fc0-130">Represents an application domain.</span></span> <span data-ttu-id="23fc0-131">Poskytuje metody pro vytváření a řízení aplikačních doménách.</span><span class="sxs-lookup"><span data-stu-id="23fc0-131">Provides methods for creating and controlling application domains.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="23fc0-132">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="23fc0-132">Related Sections</span></span>  
 [<span data-ttu-id="23fc0-133">Sestavení v modulu CLR (Common Language Runtime)</span><span class="sxs-lookup"><span data-stu-id="23fc0-133">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 <span data-ttu-id="23fc0-134">Obsahuje přehled funkce prováděné sestavení.</span><span class="sxs-lookup"><span data-stu-id="23fc0-134">Provides an overview of the functions performed by assemblies.</span></span>  
  
 [<span data-ttu-id="23fc0-135">Programování se sestaveními</span><span class="sxs-lookup"><span data-stu-id="23fc0-135">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 <span data-ttu-id="23fc0-136">Popisuje způsob vytváření, podepisování a nastavení atributů v rámci sestavení.</span><span class="sxs-lookup"><span data-stu-id="23fc0-136">Describes how to create, sign, and set attributes on assemblies.</span></span>  
  
 [<span data-ttu-id="23fc0-137">Generování dynamických metod a sestavení</span><span class="sxs-lookup"><span data-stu-id="23fc0-137">Emitting Dynamic Methods and Assemblies</span></span>](../../../docs/framework/reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)  
 <span data-ttu-id="23fc0-138">Popisuje způsob vytváření dynamických sestavení.</span><span class="sxs-lookup"><span data-stu-id="23fc0-138">Describes how to create dynamic assemblies.</span></span>  
  
 [<span data-ttu-id="23fc0-139">Aplikační domény</span><span class="sxs-lookup"><span data-stu-id="23fc0-139">Application Domains</span></span>](../../../docs/framework/app-domains/application-domains.md)  
 <span data-ttu-id="23fc0-140">Poskytuje koncepční přehled domén aplikací.</span><span class="sxs-lookup"><span data-stu-id="23fc0-140">Provides a conceptual overview of application domains.</span></span>  
  
 [<span data-ttu-id="23fc0-141">Přehled reflexe</span><span class="sxs-lookup"><span data-stu-id="23fc0-141">Reflection Overview</span></span>](../../../docs/framework/reflection-and-codedom/reflection.md)  
 <span data-ttu-id="23fc0-142">Popisuje způsob použití **reflexe** třídy k získání informací o sestavení.</span><span class="sxs-lookup"><span data-stu-id="23fc0-142">Describes how to use the **Reflection** class to obtain information about an assembly.</span></span>
