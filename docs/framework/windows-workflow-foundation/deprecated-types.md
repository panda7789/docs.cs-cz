---
title: "Zastaralé typy v modelu Windows Workflow Foundation"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4aebe928-a964-4c1c-abf7-0dbbd3604b13
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 422e95a105978749cc56dfe6601fb4518cc11509
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="deprecated-types-in-windows-workflow-foundation"></a><span data-ttu-id="6caea-102">Zastaralé typy v modelu Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="6caea-102">Deprecated types in Windows Workflow Foundation</span></span>
<span data-ttu-id="6caea-103">V rozhraní .NET 4 týmem pracovního postupu vydané modul všechny nové pracovní postup v <xref:System.Activities> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="6caea-103">In .NET 4 the Workflow Team released an all new Workflow engine in the <xref:System.Activities> namespace.</span></span> <span data-ttu-id="6caea-104">Ve verzi beta verzi rozhraní .NET 4.5 jsme jsou označení většinu typů v "WF 3" <xref:System.Workflow.Activities>, <xref:System.Workflow.ComponentModel>, a <xref:System.Workflow.Runtime> obory názvů jako zastaralé.</span><span class="sxs-lookup"><span data-stu-id="6caea-104">With the release of .NET 4.5 Beta we are marking most of the types in the "WF 3" <xref:System.Workflow.Activities>, <xref:System.Workflow.ComponentModel>, and  <xref:System.Workflow.Runtime> namespaces as obsolete.</span></span>  
  
## <a name="obsolete-namespaces-and-tools"></a><span data-ttu-id="6caea-105">Zastaralé obory názvů a nástroje</span><span class="sxs-lookup"><span data-stu-id="6caea-105">Obsolete namespaces and tools</span></span>  
 <span data-ttu-id="6caea-106">Následující sestavení mít jeden nebo více veřejné typy, které přestanou:</span><span class="sxs-lookup"><span data-stu-id="6caea-106">The following assemblies have one or more public types that will be deprecated:</span></span>  
  
-   <span data-ttu-id="6caea-107">System.Workflow.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="6caea-107">System.Workflow.Activities.dll</span></span>  
  
-   <span data-ttu-id="6caea-108">System.Workflow.ComponentModel.dll</span><span class="sxs-lookup"><span data-stu-id="6caea-108">System.Workflow.ComponentModel.dll</span></span>  
  
-   <span data-ttu-id="6caea-109">System.Workflow.Runtime.dll</span><span class="sxs-lookup"><span data-stu-id="6caea-109">System.Workflow.Runtime.dll</span></span>  
  
-   <span data-ttu-id="6caea-110">System.WorkflowServices.dll</span><span class="sxs-lookup"><span data-stu-id="6caea-110">System.WorkflowServices.dll</span></span>  
  
-   <span data-ttu-id="6caea-111">Microsoft.Workflow.DebugController.dll</span><span class="sxs-lookup"><span data-stu-id="6caea-111">Microsoft.Workflow.DebugController.dll</span></span>  
  
-   <span data-ttu-id="6caea-112">Microsoft.Workflow.Compiler.exe</span><span class="sxs-lookup"><span data-stu-id="6caea-112">Microsoft.Workflow.Compiler.exe</span></span>  
  
-   <span data-ttu-id="6caea-113">Wfc.exe</span><span class="sxs-lookup"><span data-stu-id="6caea-113">Wfc.exe</span></span>  
  
 <span data-ttu-id="6caea-114">Zákazníci, kteří používají rozhraní API pro zastaralé 3 WF v důsledku toho se setkají sestavení upozornění s zpráva podobná následující:</span><span class="sxs-lookup"><span data-stu-id="6caea-114">As a result, customers who are using the deprecated WF 3 APIs will encounter build warnings with a message similar to the following:</span></span>  
  
 <span data-ttu-id="6caea-115">**Upozornění BC40000: X je zastaralý: WF 3 typy jsou zastaralé. Místo toho použijte WF 4.**</span><span class="sxs-lookup"><span data-stu-id="6caea-115">**Warning BC40000: X is obsolete: WF 3 types are deprecated. Please use WF 4 instead.**</span></span> <span data-ttu-id="6caea-116">Typy jsme se odebrat z rozhraní .NET Framework v budoucí verzi, ale zjistili jsme nebyly dosud tohoto časového období (ne ve 4.5).</span><span class="sxs-lookup"><span data-stu-id="6caea-116">We will remove the types from the .NET Framework in a future release, but we have not yet determined that timeframe (not in 4.5).</span></span> <span data-ttu-id="6caea-117">Tento krok aktuální umožňuje komunikaci naše směr zákazníkům a povolit dostatek času pro přesun do nového modelu WF4.</span><span class="sxs-lookup"><span data-stu-id="6caea-117">This current step allows us to communicate our direction to our customers and allow them plenty of time to move to the new WF4 model.</span></span> <span data-ttu-id="6caea-118">Budeme, samozřejmě nadále podporu těchto typů WF 3 v části [o zásadách životního cyklu podpory společnosti Microsoft](http://aka.ms/MicrosoftSupportLifecycle).</span><span class="sxs-lookup"><span data-stu-id="6caea-118">We will, of course, continue to support these WF 3 types under the [Microsoft Support Lifecycle Policy](http://aka.ms/MicrosoftSupportLifecycle).</span></span> <span data-ttu-id="6caea-119">Existující WF3 aplikací spustit bez problém v rozhraní .NET 4.5 a [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] budou podporovat nové a stávající na základě WF3 řešení.</span><span class="sxs-lookup"><span data-stu-id="6caea-119">Existing WF3 applications will run without issue on .NET 4.5, and [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] will support new and existing WF3-based solutions.</span></span>  
  
 <span data-ttu-id="6caea-120">Pravidla související typy v <xref:System.Workflow.Activities.Rules> obor názvů, které nemají náhradní v WF 4.5, nebyly zastaralá.</span><span class="sxs-lookup"><span data-stu-id="6caea-120">Rules related types in the <xref:System.Workflow.Activities.Rules> namespace, which do not have a replacement in WF 4.5, have not been deprecated.</span></span>  
  
 <span data-ttu-id="6caea-121">Zákazníci, kteří chtějí migrovat své aplikace na WF 4 najdete v nápovědě [pracovního postupu 4 migrace pokyny](migration-guidance.md).</span><span class="sxs-lookup"><span data-stu-id="6caea-121">Customers who want to migrate their applications to WF 4 will find help in the [Workflow 4 Migration Guidance](migration-guidance.md).</span></span>
