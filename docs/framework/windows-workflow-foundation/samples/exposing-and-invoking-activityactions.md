---
title: Zveřejnění a vyvolání akcí aktivit
ms.date: 03/30/2017
ms.assetid: 97ce4797-426e-463d-9cc4-1261afad6df4
ms.openlocfilehash: 99207c33d82ec9028da2355cc792c366dc5e0cc6
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/27/2018
ms.locfileid: "47398560"
---
# <a name="exposing-and-invoking-activityactions"></a><span data-ttu-id="384b6-102">Zveřejnění a vyvolání akcí aktivit</span><span class="sxs-lookup"><span data-stu-id="384b6-102">Exposing and Invoking ActivityActions</span></span>
<span data-ttu-id="384b6-103">Tato ukázka předvádí, jak vyvinout vlastní aktivity, která má <xref:System.Activities.ActivityAction>.</span><span class="sxs-lookup"><span data-stu-id="384b6-103">This sample demonstrates how to develop a custom activity that has an <xref:System.Activities.ActivityAction>.</span></span> <span data-ttu-id="384b6-104">Také ukazuje, jak tuto aktivitu použijte, tím, že poskytuje implementace <xref:System.Activities.ActivityAction>.</span><span class="sxs-lookup"><span data-stu-id="384b6-104">It also demonstrates how to use this activity by providing an implementation of the <xref:System.Activities.ActivityAction>.</span></span>  
  
 <span data-ttu-id="384b6-105"><xref:System.Activities.ActivityAction> Umožňuje autorovi aktivity vystavit "otvorů" konkrétní podpisy kde aktivity uživatele můžete zařadit vlastní chování.</span><span class="sxs-lookup"><span data-stu-id="384b6-105">An <xref:System.Activities.ActivityAction> allows an activity author to expose "holes" with specific signatures where the activity user can plug in a custom behavior.</span></span> <span data-ttu-id="384b6-106">Například <xref:System.Activities.Statements.ForEach%601> aktivity (která funguje v kolekci položek), má <xref:System.Activities.ActivityAction> , který umožňuje uživateli aktivity k chování, které působí na aktuální položku iterace.</span><span class="sxs-lookup"><span data-stu-id="384b6-106">For example, the <xref:System.Activities.Statements.ForEach%601> activity, (which operates over a collection of items), has an <xref:System.Activities.ActivityAction> that allows the activity user to plug in behavior that operates on the current iteration item.</span></span>  
  
## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="384b6-107">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="384b6-107">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="384b6-108">Otevřít **ActivityAction.sln** ukázkové řešení v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="384b6-108">Open the **ActivityAction.sln** sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="384b6-109">Sestavte a spusťte řešení.</span><span class="sxs-lookup"><span data-stu-id="384b6-109">Build and run the solution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="384b6-110">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="384b6-110">The samples may already be installed on your machine.</span></span> <span data-ttu-id="384b6-111">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="384b6-111">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="384b6-112">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="384b6-112">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="384b6-113">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="384b6-113">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\ActivityAction`