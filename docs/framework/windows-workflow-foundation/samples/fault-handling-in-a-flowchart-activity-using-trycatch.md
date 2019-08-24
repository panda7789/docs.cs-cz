---
title: Zpracování chyb v aktivitě FlowChart pomocí TryCatch
ms.date: 03/30/2017
ms.assetid: 50922964-bfe0-4ba8-9422-0e7220d514fd
ms.openlocfilehash: 42eb660aff01c7e29227c28a6ad0d47d4370eb91
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/24/2019
ms.locfileid: "70016020"
---
# <a name="fault-handling-in-a-flowchart-activity-using-trycatch"></a><span data-ttu-id="f6e07-102">Zpracování chyb v aktivitě FlowChart pomocí TryCatch</span><span class="sxs-lookup"><span data-stu-id="f6e07-102">Fault Handling in a Flowchart Activity Using TryCatch</span></span>

<span data-ttu-id="f6e07-103">Tento příklad ukazuje, <xref:System.Activities.Statements.TryCatch> jak lze aktivitu použít v rámci složité aktivity toku řízení.</span><span class="sxs-lookup"><span data-stu-id="f6e07-103">This sample shows how the <xref:System.Activities.Statements.TryCatch> activity can be used within a complex control flow activity.</span></span>

<span data-ttu-id="f6e07-104">V této ukázce se propagační kód a počet podřízených položek předávají jako proměnné do <xref:System.Activities.Statements.Flowchart> aktivity, která vypočítá slevu na základě vzorců, které odpovídají kódu pro povýšení.</span><span class="sxs-lookup"><span data-stu-id="f6e07-104">In this sample, a promotion code and number of children are passed as variables to a <xref:System.Activities.Statements.Flowchart> activity that calculates a discount based on formulae that correspond to the promotion code.</span></span> <span data-ttu-id="f6e07-105">Ukázka zahrnuje imperativní verze kódu a návrháře pracovních postupů v ukázce.</span><span class="sxs-lookup"><span data-stu-id="f6e07-105">The sample includes imperative code and workflow designer versions of the sample.</span></span>

<span data-ttu-id="f6e07-106">Následující tabulka popisuje proměnné pro `CreateFlowchartWithFaults` aktivitu.</span><span class="sxs-lookup"><span data-stu-id="f6e07-106">The following table details the variables for the `CreateFlowchartWithFaults` activity.</span></span>

|<span data-ttu-id="f6e07-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="f6e07-107">Parameters</span></span>|<span data-ttu-id="f6e07-108">Popis</span><span class="sxs-lookup"><span data-stu-id="f6e07-108">Description</span></span>|
|----------------|-----------------|
|<span data-ttu-id="f6e07-109">promoCode</span><span class="sxs-lookup"><span data-stu-id="f6e07-109">promoCode</span></span>|<span data-ttu-id="f6e07-110">Propagační kód.</span><span class="sxs-lookup"><span data-stu-id="f6e07-110">The promotion code.</span></span> <span data-ttu-id="f6e07-111">Zadejte: String</span><span class="sxs-lookup"><span data-stu-id="f6e07-111">Type: String</span></span><br /><br /> <span data-ttu-id="f6e07-112">Možné hodnoty s popisem v závorkách:</span><span class="sxs-lookup"><span data-stu-id="f6e07-112">The possible values with description in parentheses:</span></span><br /><br /> <span data-ttu-id="f6e07-113">-Single (jedna)</span><span class="sxs-lookup"><span data-stu-id="f6e07-113">-   Single (Single)</span></span><br /><span data-ttu-id="f6e07-114">-MNK (svatba bez dětí.)</span><span class="sxs-lookup"><span data-stu-id="f6e07-114">-   MNK (Married with no kids.)</span></span><br /><span data-ttu-id="f6e07-115">-MWK (svatba s dětskými děti)</span><span class="sxs-lookup"><span data-stu-id="f6e07-115">-   MWK (Married with kids.)</span></span>|
|<span data-ttu-id="f6e07-116">numKids</span><span class="sxs-lookup"><span data-stu-id="f6e07-116">numKids</span></span>|<span data-ttu-id="f6e07-117">Počet podřízených objektů.</span><span class="sxs-lookup"><span data-stu-id="f6e07-117">The number of children.</span></span> <span data-ttu-id="f6e07-118">Typ: int</span><span class="sxs-lookup"><span data-stu-id="f6e07-118">Type: int</span></span>|

<span data-ttu-id="f6e07-119">`CreateFlowchartWithFaults` Aktivita používá`promoCode` aktivitu, která se přepíná na argument a vypočítá slevu pomocí následujícího vzorce. <xref:System.Activities.Statements.FlowSwitch%601></span><span class="sxs-lookup"><span data-stu-id="f6e07-119">The `CreateFlowchartWithFaults` activity uses a <xref:System.Activities.Statements.FlowSwitch%601> activity that switches on the `promoCode` argument and calculates the discount using the following formula.</span></span>

|<span data-ttu-id="f6e07-120">Hodnota`promoCode`</span><span class="sxs-lookup"><span data-stu-id="f6e07-120">Value of `promoCode`</span></span>|<span data-ttu-id="f6e07-121">Sleva (%)</span><span class="sxs-lookup"><span data-stu-id="f6e07-121">Discount (%)</span></span>|
|--------------------------|--------------------|
|<span data-ttu-id="f6e07-122">Single</span><span class="sxs-lookup"><span data-stu-id="f6e07-122">Single</span></span>|<span data-ttu-id="f6e07-123">10</span><span class="sxs-lookup"><span data-stu-id="f6e07-123">10</span></span>|
|<span data-ttu-id="f6e07-124">MNK</span><span class="sxs-lookup"><span data-stu-id="f6e07-124">MNK</span></span>|<span data-ttu-id="f6e07-125">15</span><span class="sxs-lookup"><span data-stu-id="f6e07-125">15</span></span>|
|<span data-ttu-id="f6e07-126">MWK</span><span class="sxs-lookup"><span data-stu-id="f6e07-126">MWK</span></span>|<span data-ttu-id="f6e07-127">15 + (1 – 1/`numberOfKids`)\*10 **Poznámka:**  Tento výpočet může způsobit vyvolání <xref:System.DivideByZeroException>.</span><span class="sxs-lookup"><span data-stu-id="f6e07-127">15 + (1 – 1/`numberOfKids`)\*10 **Note:**  Potentially, this calculation can throw a <xref:System.DivideByZeroException>.</span></span> <span data-ttu-id="f6e07-128">Proto je výpočet slevy zabalen do <xref:System.Activities.Statements.TryCatch> aktivity, která <xref:System.DivideByZeroException> výjimku zachytí, a nastaví slevu na nulu.</span><span class="sxs-lookup"><span data-stu-id="f6e07-128">So, the discount calculation is wrapped in a <xref:System.Activities.Statements.TryCatch> activity that catches the <xref:System.DivideByZeroException> exception and sets the discount to zero.</span></span>|

#### <a name="to-use-this-sample"></a><span data-ttu-id="f6e07-129">Použití této ukázky</span><span class="sxs-lookup"><span data-stu-id="f6e07-129">To use this sample</span></span>

1. <span data-ttu-id="f6e07-130">Pomocí sady Visual Studio 2010 otevřete soubor řešení FlowchartWithFaultHandling. sln.</span><span class="sxs-lookup"><span data-stu-id="f6e07-130">Using Visual Studio 2010, open the FlowchartWithFaultHandling.sln solution file.</span></span>

2. <span data-ttu-id="f6e07-131">Pro sestavení řešení stiskněte kombinaci kláves CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="f6e07-131">To build the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="f6e07-132">Pokud chcete řešení spustit, stiskněte klávesu F5.</span><span class="sxs-lookup"><span data-stu-id="f6e07-132">To run the solution, press F5.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f6e07-133">Ukázky již mohou být nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="f6e07-133">The samples may already be installed on your computer.</span></span> <span data-ttu-id="f6e07-134">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="f6e07-134">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="f6e07-135">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="f6e07-135">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f6e07-136">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="f6e07-136">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\FlowChartWithFaultHandling`

## <a name="see-also"></a><span data-ttu-id="f6e07-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f6e07-137">See also</span></span>

- [<span data-ttu-id="f6e07-138">Pracovní postupy vývojového diagramu</span><span class="sxs-lookup"><span data-stu-id="f6e07-138">Flowchart Workflows</span></span>](../flowchart-workflows.md)
- [<span data-ttu-id="f6e07-139">Výjimky</span><span class="sxs-lookup"><span data-stu-id="f6e07-139">Exceptions</span></span>](../exceptions.md)
