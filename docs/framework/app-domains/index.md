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
ms.openlocfilehash: 7124b6b234601e3afc27109ac318f47e3fe40c35
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61675348"
---
# <a name="programming-with-application-domains-and-assemblies"></a><span data-ttu-id="99d2e-102">Programování s doménami aplikací a sestaveními</span><span class="sxs-lookup"><span data-stu-id="99d2e-102">Programming with Application Domains and Assemblies</span></span>
<span data-ttu-id="99d2e-103">Vytvoření hostitele, jako je Microsoft Internet Explorer, ASP.NET a načtení Windows prostředí common language runtime do procesu, [aplikační domény](../../../docs/framework/app-domains/application-domains.md) v dané zpracování a pak načíst a spustit uživatelský kód v této doméně aplikace Při spuštění aplikace rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="99d2e-103">Hosts such as Microsoft Internet Explorer, ASP.NET, and the Windows shell load the common language runtime into a process, create an [application domain](../../../docs/framework/app-domains/application-domains.md) in that process, and then load and execute user code in that application domain when running a .NET Framework application.</span></span> <span data-ttu-id="99d2e-104">Ve většině případů není nutné se starat o vytváření domény aplikace a načítání sestavení do nich, protože hostitelský modul runtime provádí tyto úlohy.</span><span class="sxs-lookup"><span data-stu-id="99d2e-104">In most cases, you do not have to worry about creating application domains and loading assemblies into them because the runtime host performs those tasks.</span></span>  
  
 <span data-ttu-id="99d2e-105">Nicméně pokud vytváříte aplikaci, která bude hostovat modul common language runtime, vytvořit nástroje nebo kódu, které chcete uvolnit prostřednictvím kódu programu, nebo vytvořit modulární komponenty, které mohou být a projekt znovu nenačtete v reálném čase, budete vytvářet vlastní aplikační domény.</span><span class="sxs-lookup"><span data-stu-id="99d2e-105">However, if you are creating an application that will host the common language runtime, creating tools or code you want to unload programmatically, or creating pluggable components that can be unloaded and reloaded on the fly, you will be creating your own application domains.</span></span> <span data-ttu-id="99d2e-106">I když nejsou vytvořit hostitelský modul runtime, tato část obsahuje důležité informace o tom, jak pracovat s doménami aplikací a sestavení načtená v těchto doménách aplikace.</span><span class="sxs-lookup"><span data-stu-id="99d2e-106">Even if you are not creating a runtime host, this section provides important information on how to work with application domains and assemblies loaded in these application domains.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="99d2e-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="99d2e-107">In This Section</span></span>  
 [<span data-ttu-id="99d2e-108">Témata s návody k doménám a sestavením aplikací</span><span class="sxs-lookup"><span data-stu-id="99d2e-108">Application Domains and Assemblies How-to Topics</span></span>](../../../docs/framework/app-domains/application-domains-and-assemblies-how-to-topics.md)  
 <span data-ttu-id="99d2e-109">Obsahuje odkazy na všechny postupy v rámcové dokumentaci k programování s doménami aplikací a sestaveními.</span><span class="sxs-lookup"><span data-stu-id="99d2e-109">Provides links to all How-to topics found in the conceptual documentation for programming with application domains and assemblies.</span></span>  
  
 [<span data-ttu-id="99d2e-110">Používání domén aplikací</span><span class="sxs-lookup"><span data-stu-id="99d2e-110">Using Application Domains</span></span>](../../../docs/framework/app-domains/use.md)  
 <span data-ttu-id="99d2e-111">Obsahuje příklady vytváření, konfiguraci a používání domén aplikací.</span><span class="sxs-lookup"><span data-stu-id="99d2e-111">Provides examples of creating, configuring, and using application domains.</span></span>  
  
 [<span data-ttu-id="99d2e-112">Programování se sestaveními</span><span class="sxs-lookup"><span data-stu-id="99d2e-112">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 <span data-ttu-id="99d2e-113">Popisuje způsob vytváření, podepisování a nastavení atributů v rámci sestavení.</span><span class="sxs-lookup"><span data-stu-id="99d2e-113">Describes how to create, sign, and set attributes on assemblies.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="99d2e-114">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="99d2e-114">Related Sections</span></span>  
 [<span data-ttu-id="99d2e-115">Generování dynamických metod a sestavení</span><span class="sxs-lookup"><span data-stu-id="99d2e-115">Emitting Dynamic Methods and Assemblies</span></span>](../../../docs/framework/reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)  
 <span data-ttu-id="99d2e-116">Popisuje způsob vytváření dynamických sestavení.</span><span class="sxs-lookup"><span data-stu-id="99d2e-116">Describes how to create dynamic assemblies.</span></span>  
  
 [<span data-ttu-id="99d2e-117">Sestavení v modulu CLR (Common Language Runtime)</span><span class="sxs-lookup"><span data-stu-id="99d2e-117">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 <span data-ttu-id="99d2e-118">Poskytuje koncepční přehled sestavení.</span><span class="sxs-lookup"><span data-stu-id="99d2e-118">Provides a conceptual overview of assemblies.</span></span>  
  
 [<span data-ttu-id="99d2e-119">Aplikační domény</span><span class="sxs-lookup"><span data-stu-id="99d2e-119">Application Domains</span></span>](../../../docs/framework/app-domains/application-domains.md)  
 <span data-ttu-id="99d2e-120">Poskytuje koncepční přehled domén aplikací.</span><span class="sxs-lookup"><span data-stu-id="99d2e-120">Provides a conceptual overview of application domains.</span></span>  
  
 [<span data-ttu-id="99d2e-121">Přehled reflexe</span><span class="sxs-lookup"><span data-stu-id="99d2e-121">Reflection Overview</span></span>](../../../docs/framework/reflection-and-codedom/reflection.md)  
 <span data-ttu-id="99d2e-122">Popisuje způsob použití **reflexe** třídy k získání informací o sestavení.</span><span class="sxs-lookup"><span data-stu-id="99d2e-122">Describes how to use the **Reflection** class to obtain information about an assembly.</span></span>
