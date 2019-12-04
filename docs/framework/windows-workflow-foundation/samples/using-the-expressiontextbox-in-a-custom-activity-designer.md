---
title: Použití ExpressionTextBox v návrháři vlastní aktivity
ms.date: 03/30/2017
ms.assetid: f82e73e7-a256-4a4d-82b7-c0d62f4ab5e7
ms.openlocfilehash: 6b581b42c882c12425a17b9a518f8957ca10898a
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715539"
---
# <a name="using-the-expressiontextbox-in-a-custom-activity-designer"></a><span data-ttu-id="28102-102">Použití ExpressionTextBox v návrháři vlastní aktivity</span><span class="sxs-lookup"><span data-stu-id="28102-102">Using the ExpressionTextBox in a Custom Activity Designer</span></span>
<span data-ttu-id="28102-103">V této ukázce se dozvíte, jak používat <xref:System.Activities.Presentation.View.ExpressionTextBox> v Návrháři vlastní aktivity.</span><span class="sxs-lookup"><span data-stu-id="28102-103">This sample shows how to use the <xref:System.Activities.Presentation.View.ExpressionTextBox> in a custom activity designer.</span></span> <span data-ttu-id="28102-104">Vlastní aktivita `MultiAssign`přiřadí dvě řetězcové hodnoty dvěma řetězcovým proměnným.</span><span class="sxs-lookup"><span data-stu-id="28102-104">The custom activity, `MultiAssign`, assigns two string values to two string variables.</span></span> <span data-ttu-id="28102-105">Některé ovládací prvky <xref:System.Activities.Presentation.View.ExpressionTextBox> vážou <xref:System.Activities.InArgument>s a některá vazba na <xref:System.Activities.OutArgument>s.</span><span class="sxs-lookup"><span data-stu-id="28102-105">Some <xref:System.Activities.Presentation.View.ExpressionTextBox> controls bind to <xref:System.Activities.InArgument>s and some bind to <xref:System.Activities.OutArgument>s.</span></span>

## <a name="sample-details"></a><span data-ttu-id="28102-106">Podrobnosti ukázky</span><span class="sxs-lookup"><span data-stu-id="28102-106">Sample details</span></span>
 <span data-ttu-id="28102-107">`ArgumentToExpressionConverter` je konvertor typu, který se používá při vytváření výrazů vazby k argumentům.</span><span class="sxs-lookup"><span data-stu-id="28102-107">The `ArgumentToExpressionConverter` is the type converter used when binding expressions to arguments.</span></span> <span data-ttu-id="28102-108">`ConverterParameter` musí být nastavená na `In` nebo `Out` podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="28102-108">The `ConverterParameter` must be set to `In` or `Out` as appropriate.</span></span> <span data-ttu-id="28102-109">`InOut` se nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="28102-109">`InOut` is not supported.</span></span>

 <span data-ttu-id="28102-110">Atribut `UseLocationExpression` se používá v `OutArgument`s k určení, že výraz by měl být výraz L-hodnota ("levá hodnota" nebo "hodnota umístění").</span><span class="sxs-lookup"><span data-stu-id="28102-110">The `UseLocationExpression` attribute is used on `OutArgument`s to specify that the expression should be an L-value ("left value" or "location value") expression.</span></span> <span data-ttu-id="28102-111">Ve většině případů je výraz L-hodnoty platným Visual Basicm identifikátorem, který označuje, že `OutArgument` vracená je proměnná nebo název argumentu.</span><span class="sxs-lookup"><span data-stu-id="28102-111">In most cases, an L-value expression is a valid Visual Basic identifier used to indicate that the `OutArgument` being returned is a variable or argument name.</span></span>

 <span data-ttu-id="28102-112">Atribut `MaxLines` je v tomto příkladu nastaven na jeden a `MinLines` není nastaven.</span><span class="sxs-lookup"><span data-stu-id="28102-112">The `MaxLines` attribute is set to one in this example and `MinLines` is not set.</span></span> <span data-ttu-id="28102-113">To znamená, že <xref:System.Activities.Presentation.View.ExpressionTextBox> je pevná velikost jednoho řádku bez ohledu na množství textu zadaného uživatelem.</span><span class="sxs-lookup"><span data-stu-id="28102-113">This indicates that the <xref:System.Activities.Presentation.View.ExpressionTextBox> is a fixed size of one line regardless of the amount of text typed by the user.</span></span> <span data-ttu-id="28102-114">Aby bylo možné <xref:System.Activities.Presentation.View.ExpressionTextBox> zvětšit tak, aby odpovídaly vstupu uživatele, nastavte `MaxLines` větší než `MinLines`.</span><span class="sxs-lookup"><span data-stu-id="28102-114">To allow the <xref:System.Activities.Presentation.View.ExpressionTextBox> to grow to fit user input, set `MaxLines` greater than `MinLines`.</span></span>

 <span data-ttu-id="28102-115">ExpressionTextBox může být svázána pouze s argumenty a nelze jej svázat s vlastnostmi CLR.</span><span class="sxs-lookup"><span data-stu-id="28102-115">An ExpressionTextBox can only be bound to arguments, and cannot be bound to CLR properties.</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="28102-116">Použití této ukázky</span><span class="sxs-lookup"><span data-stu-id="28102-116">To use this sample</span></span>

1. <span data-ttu-id="28102-117">Pomocí sady Visual Studio 2010 otevřete soubor ExpressionTextBoxSample. sln.</span><span class="sxs-lookup"><span data-stu-id="28102-117">Using Visual Studio 2010, open the ExpressionTextBoxSample.sln file.</span></span>

2. <span data-ttu-id="28102-118">Pro sestavení řešení stiskněte kombinaci kláves CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="28102-118">To build the solution, press CTRL+SHIFT+B.</span></span>

#### <a name="to-run-this-sample"></a><span data-ttu-id="28102-119">Spuštění této ukázky</span><span class="sxs-lookup"><span data-stu-id="28102-119">To run this sample</span></span>

1. <span data-ttu-id="28102-120">Přidejte do řešení novou konzolovou aplikaci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="28102-120">Add a new Workflow Console Application to the solution.</span></span>

2. <span data-ttu-id="28102-121">Do projektu **ExpressionTextBoxSample** přidejte odkaz z projektu konzolové aplikace nového pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="28102-121">Add a reference to the **ExpressionTextBoxSample** project from the new Workflow Console Application project.</span></span>

3. <span data-ttu-id="28102-122">Sestavte řešení.</span><span class="sxs-lookup"><span data-stu-id="28102-122">Build the solution.</span></span>

4. <span data-ttu-id="28102-123">Přetáhněte aktivitu více **přiřazení** z panelu nástrojů a přetáhněte ji do pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="28102-123">Drag the **MultiAssign** activity from the toolbox and drop it into the workflow.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="28102-124">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="28102-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="28102-125">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="28102-125">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="28102-126">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples.</span><span class="sxs-lookup"><span data-stu-id="28102-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="28102-127">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="28102-127">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\ExpressionTextBox`  
  
## <a name="see-also"></a><span data-ttu-id="28102-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="28102-128">See also</span></span>

- <xref:System.Activities.Presentation.View.ExpressionTextBox>
- [<span data-ttu-id="28102-129">Vývoj aplikací pomocí návrháře postupu provádění</span><span class="sxs-lookup"><span data-stu-id="28102-129">Developing Applications with the Workflow Designer</span></span>](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
