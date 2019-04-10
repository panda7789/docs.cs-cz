---
title: Zpracování chyb v aktivitě FlowChart pomocí TryCatch
ms.date: 03/30/2017
ms.assetid: 50922964-bfe0-4ba8-9422-0e7220d514fd
ms.openlocfilehash: 81bfeb911658a6f363a9f0f95ecc7db68a02dbe2
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59331257"
---
# <a name="fault-handling-in-a-flowchart-activity-using-trycatch"></a><span data-ttu-id="cc619-102">Zpracování chyb v aktivitě FlowChart pomocí TryCatch</span><span class="sxs-lookup"><span data-stu-id="cc619-102">Fault Handling in a Flowchart Activity Using TryCatch</span></span>
<span data-ttu-id="cc619-103">Tato ukázka předvádí, jak <xref:System.Activities.Statements.TryCatch> aktivita se dá použít v rámci aktivity toku řízení komplexní.</span><span class="sxs-lookup"><span data-stu-id="cc619-103">This sample shows how the <xref:System.Activities.Statements.TryCatch> activity can be used within a complex control flow activity.</span></span>

 <span data-ttu-id="cc619-104">V této ukázce propagační kód, který a počet podřízených jsou předány jako proměnné <xref:System.Activities.Statements.Flowchart> aktivitu, která vypočítá a uplatnit tak slevu podle vzorce, které odpovídají propagační kód.</span><span class="sxs-lookup"><span data-stu-id="cc619-104">In this sample, a promotion code and number of children are passed as variables to a <xref:System.Activities.Statements.Flowchart> activity that calculates a discount based on formulae that correspond to the promotion code.</span></span> <span data-ttu-id="cc619-105">Ukázka zahrnuje imperativního kódu pracovního postupu návrháře verze a ukázky.</span><span class="sxs-lookup"><span data-stu-id="cc619-105">The sample includes imperative code and workflow designer versions of the sample.</span></span>

 <span data-ttu-id="cc619-106">Následující tabulka obsahuje podrobnosti o proměnné pro `CreateFlowchartWithFaults` aktivity.</span><span class="sxs-lookup"><span data-stu-id="cc619-106">The following table details the variables for the `CreateFlowchartWithFaults` activity.</span></span>

|<span data-ttu-id="cc619-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="cc619-107">Parameters</span></span>|<span data-ttu-id="cc619-108">Popis</span><span class="sxs-lookup"><span data-stu-id="cc619-108">Description</span></span>|
|----------------|-----------------|
|<span data-ttu-id="cc619-109">promoCode</span><span class="sxs-lookup"><span data-stu-id="cc619-109">promoCode</span></span>|<span data-ttu-id="cc619-110">Propagační kód.</span><span class="sxs-lookup"><span data-stu-id="cc619-110">The promotion code.</span></span> <span data-ttu-id="cc619-111">Zadejte: String</span><span class="sxs-lookup"><span data-stu-id="cc619-111">Type: String</span></span><br /><br /> <span data-ttu-id="cc619-112">Možné hodnoty s popisem v závorkách:</span><span class="sxs-lookup"><span data-stu-id="cc619-112">The possible values with description in parentheses:</span></span><br /><br /> <span data-ttu-id="cc619-113">-Jednou (jednoduchý)</span><span class="sxs-lookup"><span data-stu-id="cc619-113">-   Single (Single)</span></span><br /><span data-ttu-id="cc619-114">-MNK (vdaná s žádné děti.)</span><span class="sxs-lookup"><span data-stu-id="cc619-114">-   MNK (Married with no kids.)</span></span><br /><span data-ttu-id="cc619-115">-MWK (vdaná s děti.)</span><span class="sxs-lookup"><span data-stu-id="cc619-115">-   MWK (Married with kids.)</span></span>|
|<span data-ttu-id="cc619-116">numKids</span><span class="sxs-lookup"><span data-stu-id="cc619-116">numKids</span></span>|<span data-ttu-id="cc619-117">Počet podřízených.</span><span class="sxs-lookup"><span data-stu-id="cc619-117">The number of children.</span></span> <span data-ttu-id="cc619-118">Typ: int</span><span class="sxs-lookup"><span data-stu-id="cc619-118">Type: int</span></span>|

 <span data-ttu-id="cc619-119">`CreateFlowchartWithFaults` Používá aktivitu <xref:System.Activities.Statements.FlowSwitch%601> aktivitu, která se přepne na `promoCode` argument a vypočítá slevu pomocí tohoto vzorce.</span><span class="sxs-lookup"><span data-stu-id="cc619-119">The `CreateFlowchartWithFaults` activity uses a <xref:System.Activities.Statements.FlowSwitch%601> activity that switches on the `promoCode` argument and calculates the discount using the following formula.</span></span>

|<span data-ttu-id="cc619-120">Hodnota</span><span class="sxs-lookup"><span data-stu-id="cc619-120">Value of</span></span> `promoCode`|<span data-ttu-id="cc619-121">Slevy (%)</span><span class="sxs-lookup"><span data-stu-id="cc619-121">Discount (%)</span></span>|
|--------------------------|--------------------|
|<span data-ttu-id="cc619-122">Single</span><span class="sxs-lookup"><span data-stu-id="cc619-122">Single</span></span>|<span data-ttu-id="cc619-123">10</span><span class="sxs-lookup"><span data-stu-id="cc619-123">10</span></span>|
|<span data-ttu-id="cc619-124">MNK</span><span class="sxs-lookup"><span data-stu-id="cc619-124">MNK</span></span>|<span data-ttu-id="cc619-125">15</span><span class="sxs-lookup"><span data-stu-id="cc619-125">15</span></span>|
|<span data-ttu-id="cc619-126">MWK</span><span class="sxs-lookup"><span data-stu-id="cc619-126">MWK</span></span>|<span data-ttu-id="cc619-127">15 + (1 – 1 /`numberOfKids`)\*10 **Poznámka:**  Případně může vyvolat tento výpočet <xref:System.DivideByZeroException>.</span><span class="sxs-lookup"><span data-stu-id="cc619-127">15 + (1 – 1/`numberOfKids`)\*10 **Note:**  Potentially, this calculation can throw a <xref:System.DivideByZeroException>.</span></span> <span data-ttu-id="cc619-128">Ano, je výpočet slevy zabalené v <xref:System.Activities.Statements.TryCatch> aktivitu, která zachytává <xref:System.DivideByZeroException> výjimky a nastaví slevy na nulu.</span><span class="sxs-lookup"><span data-stu-id="cc619-128">So, the discount calculation is wrapped in a <xref:System.Activities.Statements.TryCatch> activity that catches the <xref:System.DivideByZeroException> exception and sets the discount to zero.</span></span>|

#### <a name="to-use-this-sample"></a><span data-ttu-id="cc619-129">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="cc619-129">To use this sample</span></span>

1. <span data-ttu-id="cc619-130">Pomocí sady Visual Studio 2010, otevřete soubor řešení FlowchartWithFaultHandling.sln.</span><span class="sxs-lookup"><span data-stu-id="cc619-130">Using Visual Studio 2010, open the FlowchartWithFaultHandling.sln solution file.</span></span>

2. <span data-ttu-id="cc619-131">Abyste mohli sestavit řešení, stiskněte kombinaci kláves CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="cc619-131">To build the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="cc619-132">Abyste mohli spustit řešení, stiskněte klávesu F5.</span><span class="sxs-lookup"><span data-stu-id="cc619-132">To run the solution, press F5.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="cc619-133">Vzorky mohou již být nainstalováno ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="cc619-133">The samples may already be installed on your computer.</span></span> <span data-ttu-id="cc619-134">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="cc619-134">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="cc619-135">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="cc619-135">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="cc619-136">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="cc619-136">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\FlowChartWithFaultHandling`  
  
## <a name="see-also"></a><span data-ttu-id="cc619-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cc619-137">See also</span></span>

- [<span data-ttu-id="cc619-138">Pracovní postupy vývojového diagramu</span><span class="sxs-lookup"><span data-stu-id="cc619-138">Flowchart Workflows</span></span>](../flowchart-workflows.md)
- [<span data-ttu-id="cc619-139">Výjimky</span><span class="sxs-lookup"><span data-stu-id="cc619-139">Exceptions</span></span>](../exceptions.md)
