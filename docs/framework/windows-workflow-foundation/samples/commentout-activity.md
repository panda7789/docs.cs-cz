---
title: CommentOut aktivity
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 340204c3-f827-45fb-870e-55e2ac457ca5
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: df5faa2aacf6b86d708dad4b157b27d2609a0a93
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="commentout-activity"></a><span data-ttu-id="deadb-102">CommentOut aktivity</span><span class="sxs-lookup"><span data-stu-id="deadb-102">CommentOut Activity</span></span>
<span data-ttu-id="deadb-103">Tento příklad znázorňuje, jak psát vlastní aktivity, která odebere z cesty k provádění, efektivně komentářů je ostatní aktivity.</span><span class="sxs-lookup"><span data-stu-id="deadb-103">This sample demonstrates how to write a custom activity that removes other activities from the path of execution, effectively commenting them out.</span></span>  
  
## <a name="the-commentout-activity"></a><span data-ttu-id="deadb-104">CommentOut aktivity</span><span class="sxs-lookup"><span data-stu-id="deadb-104">The CommentOut Activity</span></span>  
 <span data-ttu-id="deadb-105">Zajistit jeho cílem CommentOut aktivity je odvozena z <xref:System.Activities.CodeActivity> základní třídy a implementuje prázdnou <xref:System.Activities.CodeActivity.Execute%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="deadb-105">To achieve its goal, the CommentOut activity derives from the <xref:System.Activities.CodeActivity> base class and implements an empty <xref:System.Activities.CodeActivity.Execute%2A> method.</span></span>  
  
```  
protected override void Execute(CodeActivityContext context)  
{  
}  
```  
  
 <span data-ttu-id="deadb-106">Třída je deklarovaná, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="deadb-106">The class is declared as shown in the following example.</span></span>  
  
```  
[Designer(typeof(CommentOutDesigner))]  
[ContentProperty("Body")]  
public sealed class CommentOut : CodeActivity  
```  
  
 <span data-ttu-id="deadb-107">`Designer` Atribut určuje třídu, která implementuje rozhraní visual aktivity v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="deadb-107">The `Designer` attribute specifies the class that implements the visual interface of the activity at design time.</span></span> <span data-ttu-id="deadb-108">`ContentProperty` Atribut uvádí, že `"Body"` vlastnosti mohou být přeskočeny v XAML reprezentace instance této aktivity.</span><span class="sxs-lookup"><span data-stu-id="deadb-108">The `ContentProperty` attribute declares that the `"Body"` property can be skipped in the XAML representation of an instance of this activity.</span></span>  
  
```  
<Border x:Uid="Border_1" BorderThickness ="1">  
    <sad:WorkflowItemPresenter   
    x:Uid="sad:WorkflowItemPresenter_1" AutomationProperties.AutomationId="Body" Item="{Binding Path=ModelItem.Body, Mode=TwoWay}"  
    AllowedItemType="{x:Type sa:Activity}"  
    HintText="Drop activity here"   
    Margin="5,5,5,5" />  
</Border>  
```  
  
 <span data-ttu-id="deadb-109">Ve třídě návrháře XAML slouží k vytvoření vlastní vizuální reprezentace aktivity.</span><span class="sxs-lookup"><span data-stu-id="deadb-109">In the designer class, XAML is used to create a custom visual representation of the activity.</span></span> <span data-ttu-id="deadb-110"><xref:System.Activities.Presentation.WorkflowItemPresenter>je třída, která poskytuje vizuální editor.</span><span class="sxs-lookup"><span data-stu-id="deadb-110"><xref:System.Activities.Presentation.WorkflowItemPresenter> is a class that provides the visual editor.</span></span>  
  
 <span data-ttu-id="deadb-111">Jediné aktivity může být přetažen na `CommentOut` prostor pro aktivity.</span><span class="sxs-lookup"><span data-stu-id="deadb-111">A single activity can be dropped onto the `CommentOut` activity surface.</span></span> <span data-ttu-id="deadb-112">Pokud chcete přidat více aktivit do tento prostor, přetáhněte aktivitu pořadí sem nejdřív.</span><span class="sxs-lookup"><span data-stu-id="deadb-112">If you want to add multiple activities to this surface, drag a sequence activity here first.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="deadb-113">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="deadb-113">To use this sample</span></span>  
  
1.  <span data-ttu-id="deadb-114">Otevřete CommentOut.sln v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="deadb-114">Open CommentOut.sln in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="deadb-115">Zkompilujte řešení stisknutím kombinace kláves CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="deadb-115">Compile the solution by pressing CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="deadb-116">Spusťte ukázku bez ladění stisknutím kombinace kláves CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="deadb-116">Start the sample without debugging by pressing CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="deadb-117">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="deadb-117">The samples may already be installed on your machine.</span></span> <span data-ttu-id="deadb-118">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="deadb-118">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="deadb-119">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="deadb-119">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="deadb-120">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="deadb-120">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\CommentOut`
