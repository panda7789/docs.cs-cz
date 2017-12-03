---
title: "Vystavení a vyvolání ActivityActions"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 97ce4797-426e-463d-9cc4-1261afad6df4
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 27b5ea6c4a4afea1bc3cb9f5a79d22850d2a4143
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="exposing-and-invoking-activityactions"></a><span data-ttu-id="0ea0f-102">Vystavení a vyvolání ActivityActions</span><span class="sxs-lookup"><span data-stu-id="0ea0f-102">Exposing and Invoking ActivityActions</span></span>
<span data-ttu-id="0ea0f-103">Tento příklad ukazuje, jak vyvíjet vlastní aktivity, který má <xref:System.Activities.ActivityAction>.</span><span class="sxs-lookup"><span data-stu-id="0ea0f-103">This sample demonstrates how to develop a custom activity that has an <xref:System.Activities.ActivityAction>.</span></span> <span data-ttu-id="0ea0f-104">Také ukazuje, jak tuto aktivitu použijte, tím, že poskytuje implementaci pro <xref:System.Activities.ActivityAction>.</span><span class="sxs-lookup"><span data-stu-id="0ea0f-104">It also demonstrates how to use this activity by providing an implementation of the <xref:System.Activities.ActivityAction>.</span></span>  
  
 <span data-ttu-id="0ea0f-105"><xref:System.Activities.ActivityAction> Umožňuje autorovi aktivity vystavit "mezery" s konkrétní podpisy kde aktivity uživatele můžete zařadit vlastní chování.</span><span class="sxs-lookup"><span data-stu-id="0ea0f-105">An <xref:System.Activities.ActivityAction> allows an activity author to expose "holes" with specific signatures where the activity user can plug in a custom behavior.</span></span> <span data-ttu-id="0ea0f-106">Například <!--zz <xref:System.Activities.Statements.ForEach>--> `System.Activities.Statements.ForEach` aktivitu (který funguje v rámci kolekce položek), má <xref:System.Activities.ActivityAction> umožňuje uživateli aktivity zařaďte chování, které funguje na aktuální iteraci položky.</span><span class="sxs-lookup"><span data-stu-id="0ea0f-106">For example, the <!--zz <xref:System.Activities.Statements.ForEach>--> `System.Activities.Statements.ForEach` activity, (which operates over a collection of items), has an <xref:System.Activities.ActivityAction> that allows the activity user to plug in behavior that operates on the current iteration item.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="0ea0f-107">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="0ea0f-107">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="0ea0f-108">Otevřete **ActivityAction.sln** ukázkové řešení v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0ea0f-108">Open the **ActivityAction.sln** sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="0ea0f-109">Sestavení a spuštění řešení.</span><span class="sxs-lookup"><span data-stu-id="0ea0f-109">Build and run the solution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="0ea0f-110">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="0ea0f-110">The samples may already be installed on your machine.</span></span> <span data-ttu-id="0ea0f-111">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="0ea0f-111">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="0ea0f-112">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="0ea0f-112">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0ea0f-113">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="0ea0f-113">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\ActivityAction`