---
title: Programování s doménami aplikací a sestaveními
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], programming
- programming assemblies
- application domains, programming
- programming application domains
ms.assetid: 96d3b8e3-bef8-4da0-9a81-9841e23a94e9
ms.openlocfilehash: 2c849d27c70971d17bf4359ee7ae1081ee976a5f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73119822"
---
# <a name="programming-with-application-domains-and-assemblies"></a><span data-ttu-id="18ded-102">Programování s doménami aplikací a sestaveními</span><span class="sxs-lookup"><span data-stu-id="18ded-102">Programming with Application Domains and Assemblies</span></span>

<span data-ttu-id="18ded-103">Hostitelé, jako je microsoft internet explorer, ASP.NET a prostředí systému Windows, načítají za běhu společného jazyka do procesu, vytvářejí v tomto procesu [doménu aplikace](application-domains.md) a při spuštění aplikace rozhraní .NET Framework načítají a spouštějí uživatelský kód v této doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="18ded-103">Hosts such as Microsoft Internet Explorer, ASP.NET, and the Windows shell load the common language runtime into a process, create an [application domain](application-domains.md) in that process, and then load and execute user code in that application domain when running a .NET Framework application.</span></span> <span data-ttu-id="18ded-104">Ve většině případů se nemusíte starat o vytváření aplikačních domén a načítání sestavení do nich, protože hostitel runtime provádí tyto úlohy.</span><span class="sxs-lookup"><span data-stu-id="18ded-104">In most cases, you do not have to worry about creating application domains and loading assemblies into them because the runtime host performs those tasks.</span></span>  
  
<span data-ttu-id="18ded-105">Pokud však vytváříte aplikaci, která bude hostitelem běžného jazykového běhu, vytváříte nástroje nebo kód, který chcete programově uvolnit, nebo vytváříte připojitelné součásti, které lze uvolnit a znovu načíst za běhu, budete vytvářet vlastní aplikačních domén.</span><span class="sxs-lookup"><span data-stu-id="18ded-105">However, if you are creating an application that will host the common language runtime, creating tools or code you want to unload programmatically, or creating pluggable components that can be unloaded and reloaded on the fly, you will be creating your own application domains.</span></span> <span data-ttu-id="18ded-106">I v případě, že nevytváříte hostitele runtime, tato část obsahuje důležité informace o tom, jak pracovat s aplikačními doménami a sestaveními načtenými v těchto aplikačních doménách.</span><span class="sxs-lookup"><span data-stu-id="18ded-106">Even if you are not creating a runtime host, this section provides important information on how to work with application domains and assemblies loaded in these application domains.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="18ded-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="18ded-107">In This Section</span></span>  

[<span data-ttu-id="18ded-108">Témata s návody k doménám a sestavením aplikací</span><span class="sxs-lookup"><span data-stu-id="18ded-108">Application Domains and Assemblies How-to Topics</span></span>](application-domains-and-assemblies-how-to-topics.md)  
<span data-ttu-id="18ded-109">Obsahuje odkazy na všechna témata s postupy, která naleznete v koncepční dokumentaci pro programování s aplikačními doménami a sestaveními.</span><span class="sxs-lookup"><span data-stu-id="18ded-109">Provides links to all How-to topics found in the conceptual documentation for programming with application domains and assemblies.</span></span>  
  
[<span data-ttu-id="18ded-110">Používání domén aplikací</span><span class="sxs-lookup"><span data-stu-id="18ded-110">Using Application Domains</span></span>](use.md)  
<span data-ttu-id="18ded-111">Obsahuje příklady vytváření, konfigurace a používání aplikačních domén.</span><span class="sxs-lookup"><span data-stu-id="18ded-111">Provides examples of creating, configuring, and using application domains.</span></span>  
  
[<span data-ttu-id="18ded-112">Programování se sestaveními</span><span class="sxs-lookup"><span data-stu-id="18ded-112">Programming with Assemblies</span></span>](../../standard/assembly/program.md)  
<span data-ttu-id="18ded-113">Popisuje způsob vytváření, podepisování a nastavení atributů v rámci sestavení.</span><span class="sxs-lookup"><span data-stu-id="18ded-113">Describes how to create, sign, and set attributes on assemblies.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="18ded-114">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="18ded-114">Related Sections</span></span>  

[<span data-ttu-id="18ded-115">Generování dynamických metod a sestavení</span><span class="sxs-lookup"><span data-stu-id="18ded-115">Emitting Dynamic Methods and Assemblies</span></span>](../reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)  
<span data-ttu-id="18ded-116">Popisuje způsob vytváření dynamických sestavení.</span><span class="sxs-lookup"><span data-stu-id="18ded-116">Describes how to create dynamic assemblies.</span></span>  
  
[<span data-ttu-id="18ded-117">Sestavení v .NET</span><span class="sxs-lookup"><span data-stu-id="18ded-117">Assemblies in .NET</span></span>](../../standard/assembly/index.md)  
<span data-ttu-id="18ded-118">Poskytuje koncepční přehled sestavení.</span><span class="sxs-lookup"><span data-stu-id="18ded-118">Provides a conceptual overview of assemblies.</span></span>  
  
[<span data-ttu-id="18ded-119">Aplikační domény</span><span class="sxs-lookup"><span data-stu-id="18ded-119">Application Domains</span></span>](application-domains.md)  
<span data-ttu-id="18ded-120">Poskytuje koncepční přehled domén aplikací.</span><span class="sxs-lookup"><span data-stu-id="18ded-120">Provides a conceptual overview of application domains.</span></span>  
  
[<span data-ttu-id="18ded-121">Přehled reflexe</span><span class="sxs-lookup"><span data-stu-id="18ded-121">Reflection Overview</span></span>](../reflection-and-codedom/reflection.md)  
<span data-ttu-id="18ded-122">Popisuje, jak použít **Reflection** třídy získat informace o sestavení.</span><span class="sxs-lookup"><span data-stu-id="18ded-122">Describes how to use the **Reflection** class to obtain information about an assembly.</span></span>
