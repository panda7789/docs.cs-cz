---
title: Zastaralé typy ve Windows Workflow Foundation
ms.date: 03/30/2017
ms.assetid: 4aebe928-a964-4c1c-abf7-0dbbd3604b13
ms.openlocfilehash: c8325e60d708b53e1701a980355d5d2bf20e8a4b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64644958"
---
# <a name="deprecated-types-in-windows-workflow-foundation"></a><span data-ttu-id="aad5b-102">Zastaralé typy ve Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="aad5b-102">Deprecated types in Windows Workflow Foundation</span></span>
<span data-ttu-id="aad5b-103">V rozhraní .NET 4 pracovního postupu týmu vydali modul pro všechny nové pracovní postup v <xref:System.Activities> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="aad5b-103">In .NET 4 the Workflow Team released an all new Workflow engine in the <xref:System.Activities> namespace.</span></span> <span data-ttu-id="aad5b-104">Ve verzi beta verze rozhraní .NET 4.5 jsme se označení většina typů v "WF 3" <xref:System.Workflow.Activities>, <xref:System.Workflow.ComponentModel>, a <xref:System.Workflow.Runtime> obory názvů jako zastaralé.</span><span class="sxs-lookup"><span data-stu-id="aad5b-104">With the release of .NET 4.5 Beta we are marking most of the types in the "WF 3" <xref:System.Workflow.Activities>, <xref:System.Workflow.ComponentModel>, and  <xref:System.Workflow.Runtime> namespaces as obsolete.</span></span>  
  
## <a name="obsolete-namespaces-and-tools"></a><span data-ttu-id="aad5b-105">Zastaralé obory názvů a nástroje</span><span class="sxs-lookup"><span data-stu-id="aad5b-105">Obsolete namespaces and tools</span></span>  
 <span data-ttu-id="aad5b-106">Následující sestavení mají jednu nebo více veřejných typů, které se přestanou používat:</span><span class="sxs-lookup"><span data-stu-id="aad5b-106">The following assemblies have one or more public types that will be deprecated:</span></span>  
  
- <span data-ttu-id="aad5b-107">System.Workflow.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="aad5b-107">System.Workflow.Activities.dll</span></span>  
  
- <span data-ttu-id="aad5b-108">System.Workflow.ComponentModel.dll</span><span class="sxs-lookup"><span data-stu-id="aad5b-108">System.Workflow.ComponentModel.dll</span></span>  
  
- <span data-ttu-id="aad5b-109">System.Workflow.Runtime.dll</span><span class="sxs-lookup"><span data-stu-id="aad5b-109">System.Workflow.Runtime.dll</span></span>  
  
- <span data-ttu-id="aad5b-110">System.WorkflowServices.dll</span><span class="sxs-lookup"><span data-stu-id="aad5b-110">System.WorkflowServices.dll</span></span>  
  
- <span data-ttu-id="aad5b-111">Microsoft.Workflow.DebugController.dll</span><span class="sxs-lookup"><span data-stu-id="aad5b-111">Microsoft.Workflow.DebugController.dll</span></span>  
  
- <span data-ttu-id="aad5b-112">Microsoft.Workflow.Compiler.exe</span><span class="sxs-lookup"><span data-stu-id="aad5b-112">Microsoft.Workflow.Compiler.exe</span></span>  
  
- <span data-ttu-id="aad5b-113">Wfc.exe</span><span class="sxs-lookup"><span data-stu-id="aad5b-113">Wfc.exe</span></span>  
  
 <span data-ttu-id="aad5b-114">Zákazníci, kteří používají rozhraní API nepoužívané 3 WF v důsledku toho dojde upozornění a zobrazí se zpráva podobná této:</span><span class="sxs-lookup"><span data-stu-id="aad5b-114">As a result, customers who are using the deprecated WF 3 APIs will encounter build warnings with a message similar to the following:</span></span>  
  
 <span data-ttu-id="aad5b-115">**Upozornění BC40000: X je zastaralý: WF 3 typy se považují za zastaralé. Místo toho použijte WF 4.**</span><span class="sxs-lookup"><span data-stu-id="aad5b-115">**Warning BC40000: X is obsolete: WF 3 types are deprecated. Please use WF 4 instead.**</span></span> <span data-ttu-id="aad5b-116">Typy jsme se odebrat z rozhraní .NET Framework v budoucí verzi, ale jsme ještě nebyla určena tohoto časového rámce (ne v 4.5).</span><span class="sxs-lookup"><span data-stu-id="aad5b-116">We will remove the types from the .NET Framework in a future release, but we have not yet determined that timeframe (not in 4.5).</span></span> <span data-ttu-id="aad5b-117">Tento krok aktuální umožňuje komunikaci naše směr pro naše zákazníky a poskytnout dostatek čas na přechod na nový model WF4.</span><span class="sxs-lookup"><span data-stu-id="aad5b-117">This current step allows us to communicate our direction to our customers and allow them plenty of time to move to the new WF4 model.</span></span> <span data-ttu-id="aad5b-118">Budeme, samozřejmě, i nadále podporuje tyto typy WF 3 v části [životní cyklus podpory Microsoft](https://aka.ms/MicrosoftSupportLifecycle).</span><span class="sxs-lookup"><span data-stu-id="aad5b-118">We will, of course, continue to support these WF 3 types under the [Microsoft Support Lifecycle Policy](https://aka.ms/MicrosoftSupportLifecycle).</span></span> <span data-ttu-id="aad5b-119">Stávající aplikace WF3 poběží bez problému v rozhraní .NET 4.5 a Visual Studio 2012 budou podporovat nové i stávající řešení založená na WF3.</span><span class="sxs-lookup"><span data-stu-id="aad5b-119">Existing WF3 applications will run without issue on .NET 4.5, and Visual Studio 2012 will support new and existing WF3-based solutions.</span></span>  
  
 <span data-ttu-id="aad5b-120">Pravidla souvisejících typů v <xref:System.Workflow.Activities.Rules> obor názvů, které nemají můžou nahradit aktuální soubor v systému Windows 4.5, nejsou zastaralé.</span><span class="sxs-lookup"><span data-stu-id="aad5b-120">Rules related types in the <xref:System.Workflow.Activities.Rules> namespace, which do not have a replacement in WF 4.5, have not been deprecated.</span></span>  
  
 <span data-ttu-id="aad5b-121">Zákazníci, kteří chtějí migrovat své aplikace WF 4 najdete v nápovědě [pokyny k migraci 4 pracovního postupu](migration-guidance.md).</span><span class="sxs-lookup"><span data-stu-id="aad5b-121">Customers who want to migrate their applications to WF 4 will find help in the [Workflow 4 Migration Guidance](migration-guidance.md).</span></span>
