---
title: Zpracování chyb v aktivitě FlowChart pomocí TryCatch
ms.date: 03/30/2017
ms.assetid: 50922964-bfe0-4ba8-9422-0e7220d514fd
ms.openlocfilehash: 8e3ca59bc9743300a230877a6fbcbed5468a1589
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74710827"
---
# <a name="fault-handling-in-a-flowchart-activity-using-trycatch"></a><span data-ttu-id="67612-102">Zpracování chyb v aktivitě FlowChart pomocí TryCatch</span><span class="sxs-lookup"><span data-stu-id="67612-102">Fault Handling in a Flowchart Activity Using TryCatch</span></span>

<span data-ttu-id="67612-103">Tento příklad ukazuje, jak lze použít aktivitu <xref:System.Activities.Statements.TryCatch> v rámci složité aktivity toku řízení.</span><span class="sxs-lookup"><span data-stu-id="67612-103">This sample shows how the <xref:System.Activities.Statements.TryCatch> activity can be used within a complex control flow activity.</span></span>

<span data-ttu-id="67612-104">V této ukázce se propagační kód a počet podřízených položek předávají jako proměnné do aktivity <xref:System.Activities.Statements.Flowchart>, která vypočítá slevu na základě vzorců, které odpovídají kódu pro povýšení.</span><span class="sxs-lookup"><span data-stu-id="67612-104">In this sample, a promotion code and number of children are passed as variables to a <xref:System.Activities.Statements.Flowchart> activity that calculates a discount based on formulae that correspond to the promotion code.</span></span> <span data-ttu-id="67612-105">Ukázka zahrnuje imperativní verze kódu a návrháře pracovních postupů v ukázce.</span><span class="sxs-lookup"><span data-stu-id="67612-105">The sample includes imperative code and workflow designer versions of the sample.</span></span>

<span data-ttu-id="67612-106">Následující tabulka popisuje proměnné pro aktivitu `CreateFlowchartWithFaults`.</span><span class="sxs-lookup"><span data-stu-id="67612-106">The following table details the variables for the `CreateFlowchartWithFaults` activity.</span></span>

|<span data-ttu-id="67612-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="67612-107">Parameters</span></span>|<span data-ttu-id="67612-108">Popis</span><span class="sxs-lookup"><span data-stu-id="67612-108">Description</span></span>|
|----------------|-----------------|
|<span data-ttu-id="67612-109">promoCode</span><span class="sxs-lookup"><span data-stu-id="67612-109">promoCode</span></span>|<span data-ttu-id="67612-110">Propagační kód.</span><span class="sxs-lookup"><span data-stu-id="67612-110">The promotion code.</span></span> <span data-ttu-id="67612-111">Typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="67612-111">Type: String</span></span><br /><br /> <span data-ttu-id="67612-112">Možné hodnoty s popisem v závorkách:</span><span class="sxs-lookup"><span data-stu-id="67612-112">The possible values with description in parentheses:</span></span><br /><br /> <span data-ttu-id="67612-113">-Single (jedna)</span><span class="sxs-lookup"><span data-stu-id="67612-113">-   Single (Single)</span></span><br /><span data-ttu-id="67612-114">-MNK (svatba bez dětí.)</span><span class="sxs-lookup"><span data-stu-id="67612-114">-   MNK (Married with no kids.)</span></span><br /><span data-ttu-id="67612-115">-MWK (svatba s dětskými děti)</span><span class="sxs-lookup"><span data-stu-id="67612-115">-   MWK (Married with kids.)</span></span>|
|<span data-ttu-id="67612-116">numKids</span><span class="sxs-lookup"><span data-stu-id="67612-116">numKids</span></span>|<span data-ttu-id="67612-117">Počet podřízených objektů.</span><span class="sxs-lookup"><span data-stu-id="67612-117">The number of children.</span></span> <span data-ttu-id="67612-118">Typ: int</span><span class="sxs-lookup"><span data-stu-id="67612-118">Type: int</span></span>|

<span data-ttu-id="67612-119">Aktivita `CreateFlowchartWithFaults` používá <xref:System.Activities.Statements.FlowSwitch%601> aktivity, která se přepíná na argument `promoCode` a vypočítá slevu pomocí následujícího vzorce.</span><span class="sxs-lookup"><span data-stu-id="67612-119">The `CreateFlowchartWithFaults` activity uses a <xref:System.Activities.Statements.FlowSwitch%601> activity that switches on the `promoCode` argument and calculates the discount using the following formula.</span></span>

|<span data-ttu-id="67612-120">Hodnota `promoCode`</span><span class="sxs-lookup"><span data-stu-id="67612-120">Value of `promoCode`</span></span>|<span data-ttu-id="67612-121">Sleva (%)</span><span class="sxs-lookup"><span data-stu-id="67612-121">Discount (%)</span></span>|
|--------------------------|--------------------|
|<span data-ttu-id="67612-122">Jednoduché</span><span class="sxs-lookup"><span data-stu-id="67612-122">Single</span></span>|<span data-ttu-id="67612-123">10</span><span class="sxs-lookup"><span data-stu-id="67612-123">10</span></span>|
|<span data-ttu-id="67612-124">MNK</span><span class="sxs-lookup"><span data-stu-id="67612-124">MNK</span></span>|<span data-ttu-id="67612-125">15</span><span class="sxs-lookup"><span data-stu-id="67612-125">15</span></span>|
|<span data-ttu-id="67612-126">MWK</span><span class="sxs-lookup"><span data-stu-id="67612-126">MWK</span></span>|<span data-ttu-id="67612-127">15 + (1 – 1/`numberOfKids`)\*10 **Poznámka:** potenciálně může tento výpočet vyvolat <xref:System.DivideByZeroException>.</span><span class="sxs-lookup"><span data-stu-id="67612-127">15 + (1 – 1/`numberOfKids`)\*10 **Note:**  Potentially, this calculation can throw a <xref:System.DivideByZeroException>.</span></span> <span data-ttu-id="67612-128">Proto je výpočet slevy zabalen do <xref:System.Activities.Statements.TryCatch> aktivity, která zachytává výjimku <xref:System.DivideByZeroException> a nastaví slevu na nulu.</span><span class="sxs-lookup"><span data-stu-id="67612-128">So, the discount calculation is wrapped in a <xref:System.Activities.Statements.TryCatch> activity that catches the <xref:System.DivideByZeroException> exception and sets the discount to zero.</span></span>|

#### <a name="to-use-this-sample"></a><span data-ttu-id="67612-129">Použití této ukázky</span><span class="sxs-lookup"><span data-stu-id="67612-129">To use this sample</span></span>

1. <span data-ttu-id="67612-130">Pomocí sady Visual Studio 2010 otevřete soubor řešení FlowchartWithFaultHandling. sln.</span><span class="sxs-lookup"><span data-stu-id="67612-130">Using Visual Studio 2010, open the FlowchartWithFaultHandling.sln solution file.</span></span>

2. <span data-ttu-id="67612-131">Pro sestavení řešení stiskněte kombinaci kláves CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="67612-131">To build the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="67612-132">Pokud chcete řešení spustit, stiskněte klávesu F5.</span><span class="sxs-lookup"><span data-stu-id="67612-132">To run the solution, press F5.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="67612-133">Ukázky již mohou být nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="67612-133">The samples may already be installed on your computer.</span></span> <span data-ttu-id="67612-134">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="67612-134">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="67612-135">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples.</span><span class="sxs-lookup"><span data-stu-id="67612-135">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="67612-136">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="67612-136">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\FlowChartWithFaultHandling`

## <a name="see-also"></a><span data-ttu-id="67612-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="67612-137">See also</span></span>

- [<span data-ttu-id="67612-138">Pracovní postupy vývojového diagramu</span><span class="sxs-lookup"><span data-stu-id="67612-138">Flowchart Workflows</span></span>](../flowchart-workflows.md)
- [<span data-ttu-id="67612-139">Výjimky</span><span class="sxs-lookup"><span data-stu-id="67612-139">Exceptions</span></span>](../exceptions.md)
