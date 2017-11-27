---
title: "Programování s doménami aplikací a sestaveními"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assemblies [.NET Framework], programming
- programming assemblies
- application domains, programming
- programming application domains
ms.assetid: 96d3b8e3-bef8-4da0-9a81-9841e23a94e9
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6dcf8e4c9bf2401309b1d80d2306bd619b96460d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="programming-with-application-domains-and-assemblies"></a><span data-ttu-id="7deda-102">Programování s doménami aplikací a sestaveními</span><span class="sxs-lookup"><span data-stu-id="7deda-102">Programming with Application Domains and Assemblies</span></span>
<span data-ttu-id="7deda-103">Vytvořte hostitele, jako je například aplikace Microsoft Internet Explorer, ASP.NET a načtení prostředí Windows modul common language runtime do procesu, [domény aplikace](../../../docs/framework/app-domains/application-domains.md) v tom, že zpracování a pak můžete načíst a spuštění uživatelského kódu v této doméně Při spuštění aplikace rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7deda-103">Hosts such as Microsoft Internet Explorer, ASP.NET, and the Windows shell load the common language runtime into a process, create an [application domain](../../../docs/framework/app-domains/application-domains.md) in that process, and then load and execute user code in that application domain when running a .NET Framework application.</span></span> <span data-ttu-id="7deda-104">Ve většině případů nemáte starosti vytvoření domény aplikace a načtení sestavení do nich, protože hostitel běhu provádí tyto úlohy.</span><span class="sxs-lookup"><span data-stu-id="7deda-104">In most cases, you do not have to worry about creating application domains and loading assemblies into them because the runtime host performs those tasks.</span></span>  
  
 <span data-ttu-id="7deda-105">Ale při vytváření aplikace, která bude hostitelem modul CLR, vytvořit nástroje nebo kód, který chcete uvolnit prostřednictvím kódu programu, nebo vytvořit modulární součásti, které mohou být uvolněny nebo za chodu, bude vytvářet vlastní aplikační domény.</span><span class="sxs-lookup"><span data-stu-id="7deda-105">However, if you are creating an application that will host the common language runtime, creating tools or code you want to unload programmatically, or creating pluggable components that can be unloaded and reloaded on the fly, you will be creating your own application domains.</span></span> <span data-ttu-id="7deda-106">I když nejsou vytvoření hostitele modulu runtime, tato část obsahuje důležité informace o tom, jak pracovat s doménami aplikací a sestaveními načíst v těchto doménách aplikace.</span><span class="sxs-lookup"><span data-stu-id="7deda-106">Even if you are not creating a runtime host, this section provides important information on how to work with application domains and assemblies loaded in these application domains.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7deda-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="7deda-107">In This Section</span></span>  
 [<span data-ttu-id="7deda-108">Postupy: témata doménám a sestavením aplikací</span><span class="sxs-lookup"><span data-stu-id="7deda-108">Application Domains and Assemblies How-to Topics</span></span>](../../../docs/framework/app-domains/application-domains-and-assemblies-how-to-topics.md)  
 <span data-ttu-id="7deda-109">Obsahuje odkazy na všechny postupy v rámcová dokumentace k programování s doménami aplikací a sestaveními.</span><span class="sxs-lookup"><span data-stu-id="7deda-109">Provides links to all How-to topics found in the conceptual documentation for programming with application domains and assemblies.</span></span>  
  
 [<span data-ttu-id="7deda-110">Používání domén aplikací</span><span class="sxs-lookup"><span data-stu-id="7deda-110">Using Application Domains</span></span>](../../../docs/framework/app-domains/use.md)  
 <span data-ttu-id="7deda-111">Obsahuje příklady vytvoření, konfiguraci a používání domén aplikací.</span><span class="sxs-lookup"><span data-stu-id="7deda-111">Provides examples of creating, configuring, and using application domains.</span></span>  
  
 [<span data-ttu-id="7deda-112">Programování se sestaveními</span><span class="sxs-lookup"><span data-stu-id="7deda-112">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 <span data-ttu-id="7deda-113">Popisuje způsob vytváření, podepisování a nastavení atributů v rámci sestavení.</span><span class="sxs-lookup"><span data-stu-id="7deda-113">Describes how to create, sign, and set attributes on assemblies.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="7deda-114">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="7deda-114">Related Sections</span></span>  
 [<span data-ttu-id="7deda-115">Emitování dynamických metod a sestavení</span><span class="sxs-lookup"><span data-stu-id="7deda-115">Emitting Dynamic Methods and Assemblies</span></span>](../../../docs/framework/reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)  
 <span data-ttu-id="7deda-116">Popisuje způsob vytváření dynamických sestavení.</span><span class="sxs-lookup"><span data-stu-id="7deda-116">Describes how to create dynamic assemblies.</span></span>  
  
 [<span data-ttu-id="7deda-117">Sestavení v modulu Common Language Runtime</span><span class="sxs-lookup"><span data-stu-id="7deda-117">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 <span data-ttu-id="7deda-118">Poskytuje koncepční přehled sestavení.</span><span class="sxs-lookup"><span data-stu-id="7deda-118">Provides a conceptual overview of assemblies.</span></span>  
  
 [<span data-ttu-id="7deda-119">Aplikační domény</span><span class="sxs-lookup"><span data-stu-id="7deda-119">Application Domains</span></span>](../../../docs/framework/app-domains/application-domains.md)  
 <span data-ttu-id="7deda-120">Poskytuje koncepční přehled domén aplikací.</span><span class="sxs-lookup"><span data-stu-id="7deda-120">Provides a conceptual overview of application domains.</span></span>  
  
 [<span data-ttu-id="7deda-121">Přehled reflexe</span><span class="sxs-lookup"><span data-stu-id="7deda-121">Reflection Overview</span></span>](../../../docs/framework/reflection-and-codedom/reflection.md)  
 <span data-ttu-id="7deda-122">Popisuje postup použití **reflexe** třída získat informace o sestavení.</span><span class="sxs-lookup"><span data-stu-id="7deda-122">Describes how to use the **Reflection** class to obtain information about an assembly.</span></span>
