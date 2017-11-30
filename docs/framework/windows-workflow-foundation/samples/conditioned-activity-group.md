---
title: "Klimatizovaném skupiny aktivit"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f76ef924-34ce-48ae-8c8d-48faf9697754
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ab8f47601f84267d1ac357b313fa5d2215a586d8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="conditioned-activity-group"></a><span data-ttu-id="67401-102">Klimatizovaném skupiny aktivit</span><span class="sxs-lookup"><span data-stu-id="67401-102">Conditioned Activity Group</span></span>
<span data-ttu-id="67401-103">Ukázka ukazuje na aplikaci rezervace cesta.</span><span class="sxs-lookup"><span data-stu-id="67401-103">The sample demonstrates a travel booking application.</span></span> <span data-ttu-id="67401-104"><xref:System.Workflow.Activities.ConditionedActivityGroup> (CAG) má dvě aktivity kód: aktivitu Car a aktivitu letecká společnost.</span><span class="sxs-lookup"><span data-stu-id="67401-104">The <xref:System.Workflow.Activities.ConditionedActivityGroup> (CAG) has two code activities: a Car activity and an Airline activity.</span></span> <span data-ttu-id="67401-105">V `SimpleCAGWorkflow` konstruktoru, objekt ArrayList "travelNeedType" naplněný typy cesta rezervace, které jsou požadovány.</span><span class="sxs-lookup"><span data-stu-id="67401-105">In the `SimpleCAGWorkflow` constructor, a "travelNeedType" ArrayList object is populated with the types of travel bookings that are required.</span></span> <span data-ttu-id="67401-106">Pomocí komentářů na jeden nebo oba `travelNeeds.Add` příkazy, můžete změnit chování CAG odpovídajícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="67401-106">By commenting out one or both of the `travelNeeds.Add` statements, you modify the CAG behavior accordingly.</span></span> <span data-ttu-id="67401-107">Auto i letecká společnost aktivity mají jejich <xref:System.Workflow.Activities.ConditionedActivityGroup.WhenConditionProperty> naplněný podmínku <xref:System.Workflow.Activities.CodeCondition>.</span><span class="sxs-lookup"><span data-stu-id="67401-107">Both the Car and Airline activities have their <xref:System.Workflow.Activities.ConditionedActivityGroup.WhenConditionProperty> condition populated with a <xref:System.Workflow.Activities.CodeCondition>.</span></span> <span data-ttu-id="67401-108">Aktivity Car provádí pouze v případě, `travelNeeds` kolekce má `TravelNeeds.Car` položku a letecká společnost aktivita se spustí pouze v případě `travelNeeds` kolekce má `TravelNeeds.Airline` položku.</span><span class="sxs-lookup"><span data-stu-id="67401-108">The Car activity executes only if the `travelNeeds` collection has a `TravelNeeds.Car` entry, and the Airline activity executes only if the `travelNeeds` collection has a `TravelNeeds.Airline` entry.</span></span>  
  
 <span data-ttu-id="67401-109">Spuštění každé aktivity odebere odpovídající položku z kolekce.</span><span class="sxs-lookup"><span data-stu-id="67401-109">The execution of each activity removes the corresponding entry from the collection.</span></span> <span data-ttu-id="67401-110">Výchozí hodnota <xref:System.Workflow.Activities.ConditionedActivityGroup.UntilCondition%2A> podmínka Určuje, že CAG musí ukončit, i když žádné podřízené objekty jsou prováděny nebo jsou připravené ke spuštění (na základě jejich <xref:System.Workflow.Activities.ConditionedActivityGroup.WhenConditionProperty> podmínky).</span><span class="sxs-lookup"><span data-stu-id="67401-110">The default <xref:System.Workflow.Activities.ConditionedActivityGroup.UntilCondition%2A> condition specifies that the CAG should exit when no children are executing or are ready for execution (based on their <xref:System.Workflow.Activities.ConditionedActivityGroup.WhenConditionProperty> conditions).</span></span> <span data-ttu-id="67401-111">V této ukázce, to znamená, že CAG ukončí při `travelNeeds` kolekce je prázdná.</span><span class="sxs-lookup"><span data-stu-id="67401-111">In this sample, this means that the CAG exits when the `travelNeeds` collection is empty.</span></span>  
  
### <a name="to-build-the-sample"></a><span data-ttu-id="67401-112">Chcete-li sestavit ukázku</span><span class="sxs-lookup"><span data-stu-id="67401-112">To build the sample</span></span>  
  
1.  <span data-ttu-id="67401-113">Otevřete řešení v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="67401-113">Open the solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="67401-114">Sestavte řešení stisknutím kombinace kláves CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="67401-114">Build the solution by pressing CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="67401-115">Spustíte řešení bez ladění stisknutím kombinace kláves CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="67401-115">Run the solution without debugging by pressing CTRL+F5.</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="67401-116">Chcete-li spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="67401-116">To run the sample</span></span>  
  
-   <span data-ttu-id="67401-117">V okně Příkazový řádek SDK spusťte soubor .exe ve složce SimpleCAG\bin\debug (nebo ve složce SimpleCAG\bin pro verzi ukázky jazyka Visual Basic), který se nachází pod hlavní složku pro ukázku.</span><span class="sxs-lookup"><span data-stu-id="67401-117">In the SDK Command Prompt window, run the .exe file in the SimpleCAG\bin\debug folder (or the SimpleCAG\bin folder for the Visual Basic version of the sample), which is located below the main folder for the sample.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="67401-118">Ukázky může být již nainstalován ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="67401-118">The samples may already be installed on your computer.</span></span> <span data-ttu-id="67401-119">Před pokračováním zkontrolovat na následující adresář (výchozí):</span><span class="sxs-lookup"><span data-stu-id="67401-119">Check for the following (default) directory before continuing:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="67401-120">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="67401-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="67401-121">Tato ukázka se nachází v následujícím adresáři:</span><span class="sxs-lookup"><span data-stu-id="67401-121">This sample is located in the following directory:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\SimpleCAG`  
  
## <a name="see-also"></a><span data-ttu-id="67401-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="67401-122">See Also</span></span>  
 <xref:System.Workflow.Activities.ConditionedActivityGroup>  
 <xref:System.Workflow.Activities.ConditionedActivityGroup.WhenConditionProperty>  
 <xref:System.Workflow.Activities.CodeCondition>  
 <xref:System.Workflow.Activities.ConditionedActivityGroup.UntilCondition%2A>
