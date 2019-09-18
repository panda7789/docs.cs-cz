---
title: Programování s doménami aplikací a sestaveními
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], programming
- programming assemblies
- application domains, programming
- programming application domains
ms.assetid: 96d3b8e3-bef8-4da0-9a81-9841e23a94e9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 84d674f7ae8e80d7a5e6a40539e3330fcfa9b563
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053118"
---
# <a name="programming-with-application-domains-and-assemblies"></a><span data-ttu-id="0efd6-102">Programování s doménami aplikací a sestaveními</span><span class="sxs-lookup"><span data-stu-id="0efd6-102">Programming with Application Domains and Assemblies</span></span>

<span data-ttu-id="0efd6-103">Hostitelé, jako je Microsoft Internet Explorer, ASP.NET a prostředí Windows, načítají modul CLR (Common Language Runtime) do procesu, vytvoří [doménu aplikace](application-domains.md) v tomto procesu a pak načtou a spustí uživatelský kód v této doméně aplikace při spuštění rozhraní .NET. Aplikace architektury.</span><span class="sxs-lookup"><span data-stu-id="0efd6-103">Hosts such as Microsoft Internet Explorer, ASP.NET, and the Windows shell load the common language runtime into a process, create an [application domain](application-domains.md) in that process, and then load and execute user code in that application domain when running a .NET Framework application.</span></span> <span data-ttu-id="0efd6-104">Ve většině případů se nemusíte starat o vytváření domén aplikací a načítání sestavení do nich, protože hostitel modulu runtime provádí tyto úlohy.</span><span class="sxs-lookup"><span data-stu-id="0efd6-104">In most cases, you do not have to worry about creating application domains and loading assemblies into them because the runtime host performs those tasks.</span></span>  
  
<span data-ttu-id="0efd6-105">Pokud však vytváříte aplikaci, která bude hostovat modul CLR (Common Language Runtime), vytváříte nástroje nebo kód, který chcete uvolnit programově, nebo vytváříte připojené součásti, které se dají uvolnit a znovu načíst, budete vytvářet vlastní. aplikační domény.</span><span class="sxs-lookup"><span data-stu-id="0efd6-105">However, if you are creating an application that will host the common language runtime, creating tools or code you want to unload programmatically, or creating pluggable components that can be unloaded and reloaded on the fly, you will be creating your own application domains.</span></span> <span data-ttu-id="0efd6-106">I v případě, že nevytváříte hostitele modulu runtime, Tato část poskytuje důležité informace o tom, jak pracovat s doménami aplikací a sestaveními načtenými v těchto doménách aplikace.</span><span class="sxs-lookup"><span data-stu-id="0efd6-106">Even if you are not creating a runtime host, this section provides important information on how to work with application domains and assemblies loaded in these application domains.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0efd6-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="0efd6-107">In This Section</span></span>  

[<span data-ttu-id="0efd6-108">Témata s návody k doménám a sestavením aplikací</span><span class="sxs-lookup"><span data-stu-id="0efd6-108">Application Domains and Assemblies How-to Topics</span></span>](application-domains-and-assemblies-how-to-topics.md)  
<span data-ttu-id="0efd6-109">Obsahuje odkazy na všechna témata s postupy, která najdete v Koncepční dokumentaci pro programování s doménami aplikací a sestaveními.</span><span class="sxs-lookup"><span data-stu-id="0efd6-109">Provides links to all How-to topics found in the conceptual documentation for programming with application domains and assemblies.</span></span>  
  
[<span data-ttu-id="0efd6-110">Používání domén aplikací</span><span class="sxs-lookup"><span data-stu-id="0efd6-110">Using Application Domains</span></span>](use.md)  
<span data-ttu-id="0efd6-111">V této části najdete příklady vytváření, konfigurace a používání domén aplikací.</span><span class="sxs-lookup"><span data-stu-id="0efd6-111">Provides examples of creating, configuring, and using application domains.</span></span>  
  
[<span data-ttu-id="0efd6-112">Programování se sestaveními</span><span class="sxs-lookup"><span data-stu-id="0efd6-112">Programming with Assemblies</span></span>](../../standard/assembly/program.md)  
<span data-ttu-id="0efd6-113">Popisuje způsob vytváření, podepisování a nastavení atributů v rámci sestavení.</span><span class="sxs-lookup"><span data-stu-id="0efd6-113">Describes how to create, sign, and set attributes on assemblies.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="0efd6-114">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="0efd6-114">Related Sections</span></span>  

[<span data-ttu-id="0efd6-115">Generování dynamických metod a sestavení</span><span class="sxs-lookup"><span data-stu-id="0efd6-115">Emitting Dynamic Methods and Assemblies</span></span>](../reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)  
<span data-ttu-id="0efd6-116">Popisuje způsob vytváření dynamických sestavení.</span><span class="sxs-lookup"><span data-stu-id="0efd6-116">Describes how to create dynamic assemblies.</span></span>  
  
[<span data-ttu-id="0efd6-117">Sestavení v .NET</span><span class="sxs-lookup"><span data-stu-id="0efd6-117">Assemblies in .NET</span></span>](../../standard/assembly/index.md)  
<span data-ttu-id="0efd6-118">Poskytuje koncepční přehled sestavení.</span><span class="sxs-lookup"><span data-stu-id="0efd6-118">Provides a conceptual overview of assemblies.</span></span>  
  
[<span data-ttu-id="0efd6-119">Aplikační domény</span><span class="sxs-lookup"><span data-stu-id="0efd6-119">Application Domains</span></span>](application-domains.md)  
<span data-ttu-id="0efd6-120">Poskytuje koncepční přehled domén aplikací.</span><span class="sxs-lookup"><span data-stu-id="0efd6-120">Provides a conceptual overview of application domains.</span></span>  
  
[<span data-ttu-id="0efd6-121">Přehled reflexe</span><span class="sxs-lookup"><span data-stu-id="0efd6-121">Reflection Overview</span></span>](../reflection-and-codedom/reflection.md)  
<span data-ttu-id="0efd6-122">Popisuje způsob použití třídy **reflexe** k získání informací o sestavení.</span><span class="sxs-lookup"><span data-stu-id="0efd6-122">Describes how to use the **Reflection** class to obtain information about an assembly.</span></span>
