---
title: "Pomocí ExpressionTextBox v Návrháři vlastní aktivity"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f82e73e7-a256-4a4d-82b7-c0d62f4ab5e7
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 41a5d5645f66f69fd267b75359d0c74952b7b4bd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="using-the-expressiontextbox-in-a-custom-activity-designer"></a><span data-ttu-id="a104e-102">Pomocí ExpressionTextBox v Návrháři vlastní aktivity</span><span class="sxs-lookup"><span data-stu-id="a104e-102">Using the ExpressionTextBox in a Custom Activity Designer</span></span>
<span data-ttu-id="a104e-103">Tento příklad ukazuje způsob použití <xref:System.Activities.Presentation.View.ExpressionTextBox> v Návrháři vlastní aktivity.</span><span class="sxs-lookup"><span data-stu-id="a104e-103">This sample shows how to use the <xref:System.Activities.Presentation.View.ExpressionTextBox> in a custom activity designer.</span></span> <span data-ttu-id="a104e-104">Vlastní aktivity, `MultiAssign`, přiřadí dvou řetězcových hodnot dvě proměnné řetězce.</span><span class="sxs-lookup"><span data-stu-id="a104e-104">The custom activity, `MultiAssign`, assigns two string values to two string variables.</span></span> <span data-ttu-id="a104e-105">Některé <xref:System.Activities.Presentation.View.ExpressionTextBox> k vytvoření vazby ovládacích prvků <xref:System.Activities.InArgument>s a některé vytvořit vazbu k <xref:System.Activities.OutArgument>s.</span><span class="sxs-lookup"><span data-stu-id="a104e-105">Some <xref:System.Activities.Presentation.View.ExpressionTextBox> controls bind to <xref:System.Activities.InArgument>s and some bind to <xref:System.Activities.OutArgument>s.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="a104e-106">Ukázka podrobnosti</span><span class="sxs-lookup"><span data-stu-id="a104e-106">Sample details</span></span>  
 <span data-ttu-id="a104e-107">`ArgumentToExpressionConverter` Je převaděč typů použít při vytváření vazby výrazů pro argumenty.</span><span class="sxs-lookup"><span data-stu-id="a104e-107">The `ArgumentToExpressionConverter` is the type converter used when binding expressions to arguments.</span></span> <span data-ttu-id="a104e-108">`ConverterParameter` Musí být nastavena na `In` nebo `Out` podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="a104e-108">The `ConverterParameter` must be set to `In` or `Out` as appropriate.</span></span> <span data-ttu-id="a104e-109">`InOut`není podporována.</span><span class="sxs-lookup"><span data-stu-id="a104e-109">`InOut` is not supported.</span></span>  
  
 <span data-ttu-id="a104e-110">`UseLocationExpression` Atribut se používá na `OutArgument`s k určení, zda výraz by měl být výraz L-value ("levém hodnota" nebo "umístění hodnota").</span><span class="sxs-lookup"><span data-stu-id="a104e-110">The `UseLocationExpression` attribute is used on `OutArgument`s to specify that the expression should be an L-value ("left value" or "location value") expression.</span></span> <span data-ttu-id="a104e-111">Ve většině případů je výraz L-value platný identifikátor jazyka Visual Basic slouží k určení, který `OutArgument` nevrátila je název proměnné nebo argumentu.</span><span class="sxs-lookup"><span data-stu-id="a104e-111">In most cases, an L-value expression is a valid Visual Basic identifier used to indicate that the `OutArgument` being returned is a variable or argument name.</span></span>  
  
 <span data-ttu-id="a104e-112">`MaxLines` Je atribut nastaven na jednu v tomto příkladu a `MinLines` není nastaven.</span><span class="sxs-lookup"><span data-stu-id="a104e-112">The `MaxLines` attribute is set to one in this example and `MinLines` is not set.</span></span> <span data-ttu-id="a104e-113">Znamená to, že <xref:System.Activities.Presentation.View.ExpressionTextBox> pevnou velikost jednoho řádku bez ohledu na množství text zadaný uživatelem.</span><span class="sxs-lookup"><span data-stu-id="a104e-113">This indicates that the <xref:System.Activities.Presentation.View.ExpressionTextBox> is a fixed size of one line regardless of the amount of text typed by the user.</span></span> <span data-ttu-id="a104e-114">Chcete-li povolit <xref:System.Activities.Presentation.View.ExpressionTextBox> roste s tím, aby vyhovovaly uživatelský vstup, nastavte `MaxLines` větší než `MinLines`.</span><span class="sxs-lookup"><span data-stu-id="a104e-114">To allow the <xref:System.Activities.Presentation.View.ExpressionTextBox> to grow to fit user input, set `MaxLines` greater than `MinLines`.</span></span>  
  
 <span data-ttu-id="a104e-115">ExpressionTextBox může být vázaný jenom na argumenty a nemůže být vázán k vlastnosti CLR.</span><span class="sxs-lookup"><span data-stu-id="a104e-115">An ExpressionTextBox can only be bound to arguments, and cannot be bound to CLR properties.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="a104e-116">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="a104e-116">To use this sample</span></span>  
  
1.  <span data-ttu-id="a104e-117">Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor ExpressionTextBoxSample.sln.</span><span class="sxs-lookup"><span data-stu-id="a104e-117">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the ExpressionTextBoxSample.sln file.</span></span>  
  
2.  <span data-ttu-id="a104e-118">Sestavte řešení, stiskněte CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="a104e-118">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
#### <a name="to-run-this-sample"></a><span data-ttu-id="a104e-119">Chcete tuto ukázku spustit</span><span class="sxs-lookup"><span data-stu-id="a104e-119">To run this sample</span></span>  
  
1.  <span data-ttu-id="a104e-120">Přidejte novou konzolovou aplikaci pracovní postup k řešení.</span><span class="sxs-lookup"><span data-stu-id="a104e-120">Add a new Workflow Console Application to the solution.</span></span>  
  
2.  <span data-ttu-id="a104e-121">Přidat odkaz na **ExpressionTextBoxSample** projekt z nový projekt konzolové aplikace pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="a104e-121">Add a reference to the **ExpressionTextBoxSample** project from the new Workflow Console Application project.</span></span>  
  
3.  <span data-ttu-id="a104e-122">Sestavte řešení.</span><span class="sxs-lookup"><span data-stu-id="a104e-122">Build the solution.</span></span>  
  
4.  <span data-ttu-id="a104e-123">Přetáhněte **MultiAssign** aktivity z panelu nástrojů a umístěte jej do pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="a104e-123">Drag the **MultiAssign** activity from the toolbox and drop it into the workflow.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a104e-124">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="a104e-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a104e-125">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="a104e-125">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="a104e-126">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="a104e-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a104e-127">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="a104e-127">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\ExpressionTextBox`  
  
## <a name="see-also"></a><span data-ttu-id="a104e-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="a104e-128">See Also</span></span>  
 <xref:System.Activities.Presentation.View.ExpressionTextBox>  
 [<span data-ttu-id="a104e-129">Vývoj aplikací pomocí návrháře pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="a104e-129">Developing Applications with the Workflow Designer</span></span>](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
