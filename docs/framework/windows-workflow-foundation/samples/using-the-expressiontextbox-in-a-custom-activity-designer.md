---
title: Použití ExpressionTextBox v návrháři vlastní aktivity
ms.date: 03/30/2017
ms.assetid: f82e73e7-a256-4a4d-82b7-c0d62f4ab5e7
ms.openlocfilehash: 6d3df9e18c7239f0e4695509d80edfd02e9a9d6f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182771"
---
# <a name="using-the-expressiontextbox-in-a-custom-activity-designer"></a><span data-ttu-id="2c8b6-102">Použití ExpressionTextBox v návrháři vlastní aktivity</span><span class="sxs-lookup"><span data-stu-id="2c8b6-102">Using the ExpressionTextBox in a Custom Activity Designer</span></span>
<span data-ttu-id="2c8b6-103">Tato ukázka ukazuje, <xref:System.Activities.Presentation.View.ExpressionTextBox> jak používat v návrháři vlastní aktivity.</span><span class="sxs-lookup"><span data-stu-id="2c8b6-103">This sample shows how to use the <xref:System.Activities.Presentation.View.ExpressionTextBox> in a custom activity designer.</span></span> <span data-ttu-id="2c8b6-104">Vlastní aktivita `MultiAssign`, přiřadí dvě řetězcové hodnoty dvěma řetězcovým proměnným.</span><span class="sxs-lookup"><span data-stu-id="2c8b6-104">The custom activity, `MultiAssign`, assigns two string values to two string variables.</span></span> <span data-ttu-id="2c8b6-105">Některé <xref:System.Activities.Presentation.View.ExpressionTextBox> ovládací <xref:System.Activities.InArgument>prvky se <xref:System.Activities.OutArgument>vážou na s a některé se vážou na s.</span><span class="sxs-lookup"><span data-stu-id="2c8b6-105">Some <xref:System.Activities.Presentation.View.ExpressionTextBox> controls bind to <xref:System.Activities.InArgument>s and some bind to <xref:System.Activities.OutArgument>s.</span></span>

## <a name="sample-details"></a><span data-ttu-id="2c8b6-106">Podrobnosti ukázky</span><span class="sxs-lookup"><span data-stu-id="2c8b6-106">Sample details</span></span>
 <span data-ttu-id="2c8b6-107">Převaděč `ArgumentToExpressionConverter` typu se používá při vazby výrazy argumenty.</span><span class="sxs-lookup"><span data-stu-id="2c8b6-107">The `ArgumentToExpressionConverter` is the type converter used when binding expressions to arguments.</span></span> <span data-ttu-id="2c8b6-108">Musí `ConverterParameter` být nastavena na `In` nebo `Out` podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="2c8b6-108">The `ConverterParameter` must be set to `In` or `Out` as appropriate.</span></span> <span data-ttu-id="2c8b6-109">`InOut`není podporována.</span><span class="sxs-lookup"><span data-stu-id="2c8b6-109">`InOut` is not supported.</span></span>

 <span data-ttu-id="2c8b6-110">Atribut `UseLocationExpression` se používá `OutArgument`na s určit, že výraz by měl být l-hodnota ("levá hodnota" nebo "hodnota umístění") výraz.</span><span class="sxs-lookup"><span data-stu-id="2c8b6-110">The `UseLocationExpression` attribute is used on `OutArgument`s to specify that the expression should be an L-value ("left value" or "location value") expression.</span></span> <span data-ttu-id="2c8b6-111">Ve většině případů je výraz hodnoty L platným identifikátorem jazyka `OutArgument` Visual Basic, který slouží k označení, že vrácená možnost je název proměnné nebo argumentu.</span><span class="sxs-lookup"><span data-stu-id="2c8b6-111">In most cases, an L-value expression is a valid Visual Basic identifier used to indicate that the `OutArgument` being returned is a variable or argument name.</span></span>

 <span data-ttu-id="2c8b6-112">Atribut `MaxLines` je nastaven na jeden `MinLines` v tomto příkladu a není nastaven.</span><span class="sxs-lookup"><span data-stu-id="2c8b6-112">The `MaxLines` attribute is set to one in this example and `MinLines` is not set.</span></span> <span data-ttu-id="2c8b6-113">To znamená, <xref:System.Activities.Presentation.View.ExpressionTextBox> že je pevná velikost jednoho řádku bez ohledu na množství textu zadali uživatel.</span><span class="sxs-lookup"><span data-stu-id="2c8b6-113">This indicates that the <xref:System.Activities.Presentation.View.ExpressionTextBox> is a fixed size of one line regardless of the amount of text typed by the user.</span></span> <span data-ttu-id="2c8b6-114">Chcete-li <xref:System.Activities.Presentation.View.ExpressionTextBox> povolit růst, aby `MaxLines` se `MinLines`vešly vstup uživatele, nastavte větší než .</span><span class="sxs-lookup"><span data-stu-id="2c8b6-114">To allow the <xref:System.Activities.Presentation.View.ExpressionTextBox> to grow to fit user input, set `MaxLines` greater than `MinLines`.</span></span>

 <span data-ttu-id="2c8b6-115">ExpressionTextBox může být vázán pouze na argumenty a nemůže být vázán na vlastnosti CLR.</span><span class="sxs-lookup"><span data-stu-id="2c8b6-115">An ExpressionTextBox can only be bound to arguments, and cannot be bound to CLR properties.</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="2c8b6-116">Chcete-li použít tento vzorek</span><span class="sxs-lookup"><span data-stu-id="2c8b6-116">To use this sample</span></span>

1. <span data-ttu-id="2c8b6-117">Pomocí sady Visual Studio 2010 otevřete soubor ExpressionTextBoxSample.sln.</span><span class="sxs-lookup"><span data-stu-id="2c8b6-117">Using Visual Studio 2010, open the ExpressionTextBoxSample.sln file.</span></span>

2. <span data-ttu-id="2c8b6-118">Chcete-li vytvořit řešení, stiskněte kombinaci kláves CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="2c8b6-118">To build the solution, press CTRL+SHIFT+B.</span></span>

#### <a name="to-run-this-sample"></a><span data-ttu-id="2c8b6-119">Spuštění této ukázky</span><span class="sxs-lookup"><span data-stu-id="2c8b6-119">To run this sample</span></span>

1. <span data-ttu-id="2c8b6-120">Přidejte do řešení novou konzolovou aplikaci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="2c8b6-120">Add a new Workflow Console Application to the solution.</span></span>

2. <span data-ttu-id="2c8b6-121">Přidejte odkaz na projekt **ExpressionTextBoxSample** z nového projektu konzoly pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="2c8b6-121">Add a reference to the **ExpressionTextBoxSample** project from the new Workflow Console Application project.</span></span>

3. <span data-ttu-id="2c8b6-122">Sestavte řešení.</span><span class="sxs-lookup"><span data-stu-id="2c8b6-122">Build the solution.</span></span>

4. <span data-ttu-id="2c8b6-123">Přetáhněte aktivitu **MultiAssign** z panelu nástrojů a přetáhněte ji do pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="2c8b6-123">Drag the **MultiAssign** activity from the toolbox and drop it into the workflow.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2c8b6-124">Ukázky mohou být již nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="2c8b6-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="2c8b6-125">Před pokračováním zkontrolujte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="2c8b6-125">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="2c8b6-126">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="2c8b6-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2c8b6-127">Tato ukázka je umístěna v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="2c8b6-127">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\ExpressionTextBox`  
  
## <a name="see-also"></a><span data-ttu-id="2c8b6-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="2c8b6-128">See also</span></span>

- <xref:System.Activities.Presentation.View.ExpressionTextBox>
- [<span data-ttu-id="2c8b6-129">Vývoj aplikací pomocí Návrháře postupu provádění</span><span class="sxs-lookup"><span data-stu-id="2c8b6-129">Developing Applications with the Workflow Designer</span></span>](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
