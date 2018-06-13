---
title: Selhání zpracování v aktivitě sady vývojový diagram pomocí TryCatch
ms.date: 03/30/2017
ms.assetid: 50922964-bfe0-4ba8-9422-0e7220d514fd
ms.openlocfilehash: cc7630be868a5bdc1a07e8d935e5dd3269b4ae22
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33518060"
---
# <a name="fault-handling-in-a-flowchart-activity-using-trycatch"></a><span data-ttu-id="74aa0-102">Selhání zpracování v aktivitě sady vývojový diagram pomocí TryCatch</span><span class="sxs-lookup"><span data-stu-id="74aa0-102">Fault Handling in a Flowchart Activity Using TryCatch</span></span>
<span data-ttu-id="74aa0-103">Tento příklad ukazuje, jak <xref:System.Activities.Statements.TryCatch> aktivitu je možné v rámci aktivitu toku řízení komplexní.</span><span class="sxs-lookup"><span data-stu-id="74aa0-103">This sample shows how the <xref:System.Activities.Statements.TryCatch> activity can be used within a complex control flow activity.</span></span>  
  
 <span data-ttu-id="74aa0-104">V této ukázce kódu povýšení a počet podřízených jsou předány jako proměnné, které chcete <xref:System.Activities.Statements.Flowchart> aktivity, která vypočítá slevu podle vzorce, které odpovídají propagační kód.</span><span class="sxs-lookup"><span data-stu-id="74aa0-104">In this sample, a promotion code and number of children are passed as variables to a <xref:System.Activities.Statements.Flowchart> activity that calculates a discount based on formulae that correspond to the promotion code.</span></span> <span data-ttu-id="74aa0-105">Ukázka zahrnuje imperativní kódu a pracovní postup návrháře verze vzorku.</span><span class="sxs-lookup"><span data-stu-id="74aa0-105">The sample includes imperative code and workflow designer versions of the sample.</span></span>  
  
 <span data-ttu-id="74aa0-106">V následující tabulce jsou proměnné pro `CreateFlowchartWithFaults` aktivity.</span><span class="sxs-lookup"><span data-stu-id="74aa0-106">The following table details the variables for the `CreateFlowchartWithFaults` activity.</span></span>  
  
|<span data-ttu-id="74aa0-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="74aa0-107">Parameters</span></span>|<span data-ttu-id="74aa0-108">Popis</span><span class="sxs-lookup"><span data-stu-id="74aa0-108">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="74aa0-109">promoCode</span><span class="sxs-lookup"><span data-stu-id="74aa0-109">promoCode</span></span>|<span data-ttu-id="74aa0-110">Propagační kód.</span><span class="sxs-lookup"><span data-stu-id="74aa0-110">The promotion code.</span></span> <span data-ttu-id="74aa0-111">Typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="74aa0-111">Type: String</span></span><br /><br /> <span data-ttu-id="74aa0-112">Možné hodnoty s Popis v závorkách:</span><span class="sxs-lookup"><span data-stu-id="74aa0-112">The possible values with description in parentheses:</span></span><br /><br /> <span data-ttu-id="74aa0-113">-Jedním (jednoduchý)</span><span class="sxs-lookup"><span data-stu-id="74aa0-113">-   Single (Single)</span></span><br /><span data-ttu-id="74aa0-114">-MNK (Ženatý s žádné dětí.)</span><span class="sxs-lookup"><span data-stu-id="74aa0-114">-   MNK (Married with no kids.)</span></span><br /><span data-ttu-id="74aa0-115">-MWK (Ženatý s dětí.)</span><span class="sxs-lookup"><span data-stu-id="74aa0-115">-   MWK (Married with kids.)</span></span>|  
|<span data-ttu-id="74aa0-116">numKids</span><span class="sxs-lookup"><span data-stu-id="74aa0-116">numKids</span></span>|<span data-ttu-id="74aa0-117">Počet podřízených prvků.</span><span class="sxs-lookup"><span data-stu-id="74aa0-117">The number of children.</span></span> <span data-ttu-id="74aa0-118">Typ: int</span><span class="sxs-lookup"><span data-stu-id="74aa0-118">Type: int</span></span>|  
  
 <span data-ttu-id="74aa0-119">`CreateFlowchartWithFaults` Používá aktivitu <xref:System.Activities.Statements.FlowSwitch%601> aktivity, která přepne na `promoCode` argument a vypočítá slevu pomocí následujícího vzorce.</span><span class="sxs-lookup"><span data-stu-id="74aa0-119">The `CreateFlowchartWithFaults` activity uses a <xref:System.Activities.Statements.FlowSwitch%601> activity that switches on the `promoCode` argument and calculates the discount using the following formula.</span></span>  
  
|<span data-ttu-id="74aa0-120">Hodnota `promoCode`</span><span class="sxs-lookup"><span data-stu-id="74aa0-120">Value of `promoCode`</span></span>|<span data-ttu-id="74aa0-121">Diskontní (%)</span><span class="sxs-lookup"><span data-stu-id="74aa0-121">Discount (%)</span></span>|  
|--------------------------|--------------------|  
|<span data-ttu-id="74aa0-122">Single</span><span class="sxs-lookup"><span data-stu-id="74aa0-122">Single</span></span>|<span data-ttu-id="74aa0-123">10</span><span class="sxs-lookup"><span data-stu-id="74aa0-123">10</span></span>|  
|<span data-ttu-id="74aa0-124">MNK</span><span class="sxs-lookup"><span data-stu-id="74aa0-124">MNK</span></span>|<span data-ttu-id="74aa0-125">15</span><span class="sxs-lookup"><span data-stu-id="74aa0-125">15</span></span>|  
|<span data-ttu-id="74aa0-126">MWK</span><span class="sxs-lookup"><span data-stu-id="74aa0-126">MWK</span></span>|<span data-ttu-id="74aa0-127">15 + (1 – 1 /`numberOfKids`)\*10 **Poznámka:** potenciálně, může tento výpočet throw <xref:System.DivideByZeroException>.</span><span class="sxs-lookup"><span data-stu-id="74aa0-127">15 + (1 – 1/`numberOfKids`)\*10 **Note:**  Potentially, this calculation can throw a <xref:System.DivideByZeroException>.</span></span> <span data-ttu-id="74aa0-128">Ano, je výpočet slevy uzavřen do <xref:System.Activities.Statements.TryCatch> aktivity, který zachytí <xref:System.DivideByZeroException> výjimky a nastaví sleva na nula.</span><span class="sxs-lookup"><span data-stu-id="74aa0-128">So, the discount calculation is wrapped in a <xref:System.Activities.Statements.TryCatch> activity that catches the <xref:System.DivideByZeroException> exception and sets the discount to zero.</span></span>|  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="74aa0-129">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="74aa0-129">To use this sample</span></span>  
  
1.  <span data-ttu-id="74aa0-130">Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení FlowchartWithFaultHandling.sln.</span><span class="sxs-lookup"><span data-stu-id="74aa0-130">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the FlowchartWithFaultHandling.sln solution file.</span></span>  
  
2.  <span data-ttu-id="74aa0-131">Sestavte řešení, stiskněte CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="74aa0-131">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="74aa0-132">Pokud chcete spustit řešení, stisknutím klávesy F5.</span><span class="sxs-lookup"><span data-stu-id="74aa0-132">To run the solution, press F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="74aa0-133">Ukázky může být již nainstalován ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="74aa0-133">The samples may already be installed on your computer.</span></span> <span data-ttu-id="74aa0-134">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="74aa0-134">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="74aa0-135">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="74aa0-135">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="74aa0-136">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="74aa0-136">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\FlowChartWithFaultHandling`  
  
## <a name="see-also"></a><span data-ttu-id="74aa0-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="74aa0-137">See Also</span></span>  
 [<span data-ttu-id="74aa0-138">Pracovní postupy vývojového diagramu</span><span class="sxs-lookup"><span data-stu-id="74aa0-138">Flowchart Workflows</span></span>](../../../../docs/framework/windows-workflow-foundation/flowchart-workflows.md)  
 [<span data-ttu-id="74aa0-139">Výjimky</span><span class="sxs-lookup"><span data-stu-id="74aa0-139">Exceptions</span></span>](../../../../docs/framework/windows-workflow-foundation/exceptions.md)
