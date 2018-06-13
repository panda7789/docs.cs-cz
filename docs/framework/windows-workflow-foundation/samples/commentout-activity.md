---
title: CommentOut aktivity
ms.date: 03/30/2017
ms.assetid: 340204c3-f827-45fb-870e-55e2ac457ca5
ms.openlocfilehash: 7847f4e1d77c2927a27be6b83f4016a22e4e3b32
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33515193"
---
# <a name="commentout-activity"></a><span data-ttu-id="79382-102">CommentOut aktivity</span><span class="sxs-lookup"><span data-stu-id="79382-102">CommentOut Activity</span></span>
<span data-ttu-id="79382-103">Tento příklad znázorňuje, jak psát vlastní aktivity, která odebere z cesty k provádění, efektivně komentářů je ostatní aktivity.</span><span class="sxs-lookup"><span data-stu-id="79382-103">This sample demonstrates how to write a custom activity that removes other activities from the path of execution, effectively commenting them out.</span></span>  
  
## <a name="the-commentout-activity"></a><span data-ttu-id="79382-104">CommentOut aktivity</span><span class="sxs-lookup"><span data-stu-id="79382-104">The CommentOut Activity</span></span>  
 <span data-ttu-id="79382-105">Zajistit jeho cílem CommentOut aktivity je odvozena z <xref:System.Activities.CodeActivity> základní třídy a implementuje prázdnou <xref:System.Activities.CodeActivity.Execute%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="79382-105">To achieve its goal, the CommentOut activity derives from the <xref:System.Activities.CodeActivity> base class and implements an empty <xref:System.Activities.CodeActivity.Execute%2A> method.</span></span>  
  
```  
protected override void Execute(CodeActivityContext context)  
{  
}  
```  
  
 <span data-ttu-id="79382-106">Třída je deklarovaná, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="79382-106">The class is declared as shown in the following example.</span></span>  
  
```  
[Designer(typeof(CommentOutDesigner))]  
[ContentProperty("Body")]  
public sealed class CommentOut : CodeActivity  
```  
  
 <span data-ttu-id="79382-107">`Designer` Atribut určuje třídu, která implementuje rozhraní visual aktivity v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="79382-107">The `Designer` attribute specifies the class that implements the visual interface of the activity at design time.</span></span> <span data-ttu-id="79382-108">`ContentProperty` Atribut uvádí, že `"Body"` vlastnosti mohou být přeskočeny v XAML reprezentace instance této aktivity.</span><span class="sxs-lookup"><span data-stu-id="79382-108">The `ContentProperty` attribute declares that the `"Body"` property can be skipped in the XAML representation of an instance of this activity.</span></span>  
  
```  
<Border x:Uid="Border_1" BorderThickness ="1">  
    <sad:WorkflowItemPresenter   
    x:Uid="sad:WorkflowItemPresenter_1" AutomationProperties.AutomationId="Body" Item="{Binding Path=ModelItem.Body, Mode=TwoWay}"  
    AllowedItemType="{x:Type sa:Activity}"  
    HintText="Drop activity here"   
    Margin="5,5,5,5" />  
</Border>  
```  
  
 <span data-ttu-id="79382-109">Ve třídě návrháře XAML slouží k vytvoření vlastní vizuální reprezentace aktivity.</span><span class="sxs-lookup"><span data-stu-id="79382-109">In the designer class, XAML is used to create a custom visual representation of the activity.</span></span> <span data-ttu-id="79382-110"><xref:System.Activities.Presentation.WorkflowItemPresenter> je třída, která poskytuje vizuální editor.</span><span class="sxs-lookup"><span data-stu-id="79382-110"><xref:System.Activities.Presentation.WorkflowItemPresenter> is a class that provides the visual editor.</span></span>  
  
 <span data-ttu-id="79382-111">Jediné aktivity může být přetažen na `CommentOut` prostor pro aktivity.</span><span class="sxs-lookup"><span data-stu-id="79382-111">A single activity can be dropped onto the `CommentOut` activity surface.</span></span> <span data-ttu-id="79382-112">Pokud chcete přidat více aktivit do tento prostor, přetáhněte aktivitu pořadí sem nejdřív.</span><span class="sxs-lookup"><span data-stu-id="79382-112">If you want to add multiple activities to this surface, drag a sequence activity here first.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="79382-113">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="79382-113">To use this sample</span></span>  
  
1.  <span data-ttu-id="79382-114">Otevřete CommentOut.sln v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="79382-114">Open CommentOut.sln in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="79382-115">Zkompilujte řešení stisknutím kombinace kláves CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="79382-115">Compile the solution by pressing CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="79382-116">Spusťte ukázku bez ladění stisknutím kombinace kláves CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="79382-116">Start the sample without debugging by pressing CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="79382-117">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="79382-117">The samples may already be installed on your machine.</span></span> <span data-ttu-id="79382-118">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="79382-118">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="79382-119">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="79382-119">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="79382-120">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="79382-120">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\CommentOut`
