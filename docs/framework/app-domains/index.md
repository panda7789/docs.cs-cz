---
title: Programování s doménami aplikací a sestaveními
description: Získejte informace o programování s aplikačními doménami a sestaveními v .NET. V tématu odkazy na témata s postupy & příklady vytváření aplikačních domén & sestaveních.
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], programming
- programming assemblies
- application domains, programming
- programming application domains
ms.assetid: 96d3b8e3-bef8-4da0-9a81-9841e23a94e9
ms.openlocfilehash: 1c28fe0abeb279a1dbbc6dcf043c1780c72d79df
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/17/2020
ms.locfileid: "84903435"
---
# <a name="programming-with-application-domains-and-assemblies"></a><span data-ttu-id="bb974-104">Programování s doménami aplikací a sestaveními</span><span class="sxs-lookup"><span data-stu-id="bb974-104">Programming with Application Domains and Assemblies</span></span>

<span data-ttu-id="bb974-105">Hostitelé, jako je Microsoft Internet Explorer, ASP.NET a prostředí Windows, načtou modul CLR (Common Language Runtime) do procesu, vytvoří v tomto procesu [doménu aplikace](application-domains.md) a při spuštění aplikace .NET Framework načte a spustí uživatelský kód v této doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="bb974-105">Hosts such as Microsoft Internet Explorer, ASP.NET, and the Windows shell load the common language runtime into a process, create an [application domain](application-domains.md) in that process, and then load and execute user code in that application domain when running a .NET Framework application.</span></span> <span data-ttu-id="bb974-106">Ve většině případů se nemusíte starat o vytváření domén aplikací a načítání sestavení do nich, protože hostitel modulu runtime provádí tyto úlohy.</span><span class="sxs-lookup"><span data-stu-id="bb974-106">In most cases, you do not have to worry about creating application domains and loading assemblies into them because the runtime host performs those tasks.</span></span>  
  
<span data-ttu-id="bb974-107">Pokud však vytváříte aplikaci, která bude hostovat modul CLR (Common Language Runtime), vytváříte nástroje nebo kód, který chcete uvolnit programově, nebo vytváříte zapojitelné součásti, které se dají uvolnit a znovu načíst, budete vytvářet vlastní aplikační domény.</span><span class="sxs-lookup"><span data-stu-id="bb974-107">However, if you are creating an application that will host the common language runtime, creating tools or code you want to unload programmatically, or creating pluggable components that can be unloaded and reloaded on the fly, you will be creating your own application domains.</span></span> <span data-ttu-id="bb974-108">I v případě, že nevytváříte hostitele modulu runtime, Tato část poskytuje důležité informace o tom, jak pracovat s doménami aplikací a sestaveními načtenými v těchto doménách aplikace.</span><span class="sxs-lookup"><span data-stu-id="bb974-108">Even if you are not creating a runtime host, this section provides important information on how to work with application domains and assemblies loaded in these application domains.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bb974-109">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="bb974-109">In This Section</span></span>  

[<span data-ttu-id="bb974-110">Témata s návody k doménám a sestavením aplikací</span><span class="sxs-lookup"><span data-stu-id="bb974-110">Application Domains and Assemblies How-to Topics</span></span>](application-domains-and-assemblies-how-to-topics.md)  
<span data-ttu-id="bb974-111">Obsahuje odkazy na všechna témata s postupy, která najdete v Koncepční dokumentaci pro programování s doménami aplikací a sestaveními.</span><span class="sxs-lookup"><span data-stu-id="bb974-111">Provides links to all How-to topics found in the conceptual documentation for programming with application domains and assemblies.</span></span>  
  
[<span data-ttu-id="bb974-112">Používání domén aplikací</span><span class="sxs-lookup"><span data-stu-id="bb974-112">Using Application Domains</span></span>](use.md)  
<span data-ttu-id="bb974-113">V této části najdete příklady vytváření, konfigurace a používání domén aplikací.</span><span class="sxs-lookup"><span data-stu-id="bb974-113">Provides examples of creating, configuring, and using application domains.</span></span>  
  
[<span data-ttu-id="bb974-114">Programování se sestaveními</span><span class="sxs-lookup"><span data-stu-id="bb974-114">Programming with Assemblies</span></span>](../../standard/assembly/index.md)  
<span data-ttu-id="bb974-115">Popisuje způsob vytváření, podepisování a nastavení atributů v rámci sestavení.</span><span class="sxs-lookup"><span data-stu-id="bb974-115">Describes how to create, sign, and set attributes on assemblies.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="bb974-116">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="bb974-116">Related Sections</span></span>  

[<span data-ttu-id="bb974-117">Generování dynamických metod a sestavení</span><span class="sxs-lookup"><span data-stu-id="bb974-117">Emitting Dynamic Methods and Assemblies</span></span>](../reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)  
<span data-ttu-id="bb974-118">Popisuje způsob vytváření dynamických sestavení.</span><span class="sxs-lookup"><span data-stu-id="bb974-118">Describes how to create dynamic assemblies.</span></span>  
  
[<span data-ttu-id="bb974-119">Sestavení v .NET</span><span class="sxs-lookup"><span data-stu-id="bb974-119">Assemblies in .NET</span></span>](../../standard/assembly/index.md)  
<span data-ttu-id="bb974-120">Poskytuje koncepční přehled sestavení.</span><span class="sxs-lookup"><span data-stu-id="bb974-120">Provides a conceptual overview of assemblies.</span></span>  
  
[<span data-ttu-id="bb974-121">Aplikační domény</span><span class="sxs-lookup"><span data-stu-id="bb974-121">Application Domains</span></span>](application-domains.md)  
<span data-ttu-id="bb974-122">Poskytuje koncepční přehled domén aplikací.</span><span class="sxs-lookup"><span data-stu-id="bb974-122">Provides a conceptual overview of application domains.</span></span>  
  
[<span data-ttu-id="bb974-123">Přehled reflexe</span><span class="sxs-lookup"><span data-stu-id="bb974-123">Reflection Overview</span></span>](../reflection-and-codedom/reflection.md)  
<span data-ttu-id="bb974-124">Popisuje způsob použití třídy **reflexe** k získání informací o sestavení.</span><span class="sxs-lookup"><span data-stu-id="bb974-124">Describes how to use the **Reflection** class to obtain information about an assembly.</span></span>
