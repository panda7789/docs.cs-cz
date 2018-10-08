---
title: Použití ExpressionTextBox v Návrháři vlastní aktivity
ms.date: 03/30/2017
ms.assetid: f82e73e7-a256-4a4d-82b7-c0d62f4ab5e7
ms.openlocfilehash: ee9da26625d772eda6100fc4d0db0469941bdb0d
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/08/2018
ms.locfileid: "48849812"
---
# <a name="using-the-expressiontextbox-in-a-custom-activity-designer"></a><span data-ttu-id="6b64d-102">Použití ExpressionTextBox v Návrháři vlastní aktivity</span><span class="sxs-lookup"><span data-stu-id="6b64d-102">Using the ExpressionTextBox in a Custom Activity Designer</span></span>
<span data-ttu-id="6b64d-103">Tento příklad ukazuje způsob použití <xref:System.Activities.Presentation.View.ExpressionTextBox> v Návrháři vlastní aktivity.</span><span class="sxs-lookup"><span data-stu-id="6b64d-103">This sample shows how to use the <xref:System.Activities.Presentation.View.ExpressionTextBox> in a custom activity designer.</span></span> <span data-ttu-id="6b64d-104">Vlastní aktivita `MultiAssign`, přiřadí dva řetězcové hodnoty dvou proměnných řetězce.</span><span class="sxs-lookup"><span data-stu-id="6b64d-104">The custom activity, `MultiAssign`, assigns two string values to two string variables.</span></span> <span data-ttu-id="6b64d-105">Některé <xref:System.Activities.Presentation.View.ExpressionTextBox> svázat ovládací prvky <xref:System.Activities.InArgument>svázat s a některé <xref:System.Activities.OutArgument>s.</span><span class="sxs-lookup"><span data-stu-id="6b64d-105">Some <xref:System.Activities.Presentation.View.ExpressionTextBox> controls bind to <xref:System.Activities.InArgument>s and some bind to <xref:System.Activities.OutArgument>s.</span></span>

## <a name="sample-details"></a><span data-ttu-id="6b64d-106">Ukázka podrobnosti</span><span class="sxs-lookup"><span data-stu-id="6b64d-106">Sample details</span></span>
 <span data-ttu-id="6b64d-107">`ArgumentToExpressionConverter` Se používá při vytváření vazby výrazy na argumenty konvertor typu.</span><span class="sxs-lookup"><span data-stu-id="6b64d-107">The `ArgumentToExpressionConverter` is the type converter used when binding expressions to arguments.</span></span> <span data-ttu-id="6b64d-108">`ConverterParameter` Musí být nastaveno na `In` nebo `Out` podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="6b64d-108">The `ConverterParameter` must be set to `In` or `Out` as appropriate.</span></span> <span data-ttu-id="6b64d-109">`InOut` není podporováno.</span><span class="sxs-lookup"><span data-stu-id="6b64d-109">`InOut` is not supported.</span></span>

 <span data-ttu-id="6b64d-110">`UseLocationExpression` Atribut se používá na `OutArgument`s určit, že výraz musí být výraz L-value ("vlevo hodnota" nebo "umístění value").</span><span class="sxs-lookup"><span data-stu-id="6b64d-110">The `UseLocationExpression` attribute is used on `OutArgument`s to specify that the expression should be an L-value ("left value" or "location value") expression.</span></span> <span data-ttu-id="6b64d-111">Ve většině případů výraz L-hodnota je platným identifikátorem jazyka Visual Basic používá k označení, že `OutArgument` vracených je název proměnné nebo argumentu.</span><span class="sxs-lookup"><span data-stu-id="6b64d-111">In most cases, an L-value expression is a valid Visual Basic identifier used to indicate that the `OutArgument` being returned is a variable or argument name.</span></span>

 <span data-ttu-id="6b64d-112">`MaxLines` Atribut je nastaven na jednu v tomto příkladu a `MinLines` není nastaven.</span><span class="sxs-lookup"><span data-stu-id="6b64d-112">The `MaxLines` attribute is set to one in this example and `MinLines` is not set.</span></span> <span data-ttu-id="6b64d-113">Znamená to, že <xref:System.Activities.Presentation.View.ExpressionTextBox> pevnou velikost jednoho řádku bez ohledu na to, jaká část textu zadaného uživatelem.</span><span class="sxs-lookup"><span data-stu-id="6b64d-113">This indicates that the <xref:System.Activities.Presentation.View.ExpressionTextBox> is a fixed size of one line regardless of the amount of text typed by the user.</span></span> <span data-ttu-id="6b64d-114">Chcete-li povolit <xref:System.Activities.Presentation.View.ExpressionTextBox> růst podle uživatelského vstupu, nastavte `MaxLines` větší než `MinLines`.</span><span class="sxs-lookup"><span data-stu-id="6b64d-114">To allow the <xref:System.Activities.Presentation.View.ExpressionTextBox> to grow to fit user input, set `MaxLines` greater than `MinLines`.</span></span>

 <span data-ttu-id="6b64d-115">ExpressionTextBox může být vázaný jedině na argumenty a nemůže být vázaný na vlastnosti CLR.</span><span class="sxs-lookup"><span data-stu-id="6b64d-115">An ExpressionTextBox can only be bound to arguments, and cannot be bound to CLR properties.</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="6b64d-116">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="6b64d-116">To use this sample</span></span>

1.  <span data-ttu-id="6b64d-117">Pomocí sady Visual Studio 2010, otevřete soubor ExpressionTextBoxSample.sln.</span><span class="sxs-lookup"><span data-stu-id="6b64d-117">Using Visual Studio 2010, open the ExpressionTextBoxSample.sln file.</span></span>

2.  <span data-ttu-id="6b64d-118">Abyste mohli sestavit řešení, stiskněte kombinaci kláves CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="6b64d-118">To build the solution, press CTRL+SHIFT+B.</span></span>

#### <a name="to-run-this-sample"></a><span data-ttu-id="6b64d-119">Tuto ukázku spustit</span><span class="sxs-lookup"><span data-stu-id="6b64d-119">To run this sample</span></span>

1.  <span data-ttu-id="6b64d-120">Přidáte novou konzolovou aplikaci pracovního postupu do řešení.</span><span class="sxs-lookup"><span data-stu-id="6b64d-120">Add a new Workflow Console Application to the solution.</span></span>

2.  <span data-ttu-id="6b64d-121">Přidejte odkaz na **ExpressionTextBoxSample** projekt z nový projekt konzolové aplikace pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="6b64d-121">Add a reference to the **ExpressionTextBoxSample** project from the new Workflow Console Application project.</span></span>

3.  <span data-ttu-id="6b64d-122">Sestavte řešení.</span><span class="sxs-lookup"><span data-stu-id="6b64d-122">Build the solution.</span></span>

4.  <span data-ttu-id="6b64d-123">Přetáhněte **MultiAssign** aktivity ze sady nástrojů a umístěte ho do pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="6b64d-123">Drag the **MultiAssign** activity from the toolbox and drop it into the workflow.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="6b64d-124">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="6b64d-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="6b64d-125">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="6b64d-125">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="6b64d-126">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="6b64d-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6b64d-127">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="6b64d-127">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\ExpressionTextBox`  
  
## <a name="see-also"></a><span data-ttu-id="6b64d-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="6b64d-128">See Also</span></span>  
 <xref:System.Activities.Presentation.View.ExpressionTextBox>  
 [<span data-ttu-id="6b64d-129">Vývoj aplikací pomocí návrháře postupu provádění</span><span class="sxs-lookup"><span data-stu-id="6b64d-129">Developing Applications with the Workflow Designer</span></span>](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
