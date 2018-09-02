---
title: Aktivita CommentOut
ms.date: 03/30/2017
ms.assetid: 340204c3-f827-45fb-870e-55e2ac457ca5
ms.openlocfilehash: 3e9f6945755bd60c551674ea8a3471a9f612da52
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43404747"
---
# <a name="commentout-activity"></a><span data-ttu-id="1603e-102">Aktivita CommentOut</span><span class="sxs-lookup"><span data-stu-id="1603e-102">CommentOut Activity</span></span>
<span data-ttu-id="1603e-103">Tato ukázka předvádí, jak psát vlastní aktivitu, která odebere z cesty spuštění efektivně komentářů je jiné aktivity.</span><span class="sxs-lookup"><span data-stu-id="1603e-103">This sample demonstrates how to write a custom activity that removes other activities from the path of execution, effectively commenting them out.</span></span>  
  
## <a name="the-commentout-activity"></a><span data-ttu-id="1603e-104">Aktivita CommentOut</span><span class="sxs-lookup"><span data-stu-id="1603e-104">The CommentOut Activity</span></span>  
 <span data-ttu-id="1603e-105">K dosažení jejího cíle – aktivita CommentOut je odvozen od <xref:System.Activities.CodeActivity> základní třídy a implementuje prázdná <xref:System.Activities.CodeActivity.Execute%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="1603e-105">To achieve its goal, the CommentOut activity derives from the <xref:System.Activities.CodeActivity> base class and implements an empty <xref:System.Activities.CodeActivity.Execute%2A> method.</span></span>  
  
```  
protected override void Execute(CodeActivityContext context)  
{  
}  
```  
  
 <span data-ttu-id="1603e-106">Třída je deklarována, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="1603e-106">The class is declared as shown in the following example.</span></span>  
  
```  
[Designer(typeof(CommentOutDesigner))]  
[ContentProperty("Body")]  
public sealed class CommentOut : CodeActivity  
```  
  
 <span data-ttu-id="1603e-107">`Designer` Atribut určuje třídu, která implementuje rozhraní visual aktivity v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="1603e-107">The `Designer` attribute specifies the class that implements the visual interface of the activity at design time.</span></span> <span data-ttu-id="1603e-108">`ContentProperty` Atributu deklaruje, že `"Body"` vlastnosti mohou být přeskočeny v XAML reprezentaci instance této aktivity.</span><span class="sxs-lookup"><span data-stu-id="1603e-108">The `ContentProperty` attribute declares that the `"Body"` property can be skipped in the XAML representation of an instance of this activity.</span></span>  
  
```  
<Border x:Uid="Border_1" BorderThickness ="1">  
    <sad:WorkflowItemPresenter   
    x:Uid="sad:WorkflowItemPresenter_1" AutomationProperties.AutomationId="Body" Item="{Binding Path=ModelItem.Body, Mode=TwoWay}"  
    AllowedItemType="{x:Type sa:Activity}"  
    HintText="Drop activity here"   
    Margin="5,5,5,5" />  
</Border>  
```  
  
 <span data-ttu-id="1603e-109">Ve třídě návrháře XAML slouží k vytvoření vlastní vizuální znázornění aktivity.</span><span class="sxs-lookup"><span data-stu-id="1603e-109">In the designer class, XAML is used to create a custom visual representation of the activity.</span></span> <span data-ttu-id="1603e-110"><xref:System.Activities.Presentation.WorkflowItemPresenter> je třída, která poskytuje vizuální editor.</span><span class="sxs-lookup"><span data-stu-id="1603e-110"><xref:System.Activities.Presentation.WorkflowItemPresenter> is a class that provides the visual editor.</span></span>  
  
 <span data-ttu-id="1603e-111">Jediné aktivity může být přetaženy `CommentOut` aktivity povrchu.</span><span class="sxs-lookup"><span data-stu-id="1603e-111">A single activity can be dropped onto the `CommentOut` activity surface.</span></span> <span data-ttu-id="1603e-112">Pokud chcete přidat více aktivit do tuto plochu, sekvenční aktivity Sem přetáhněte nejdřív.</span><span class="sxs-lookup"><span data-stu-id="1603e-112">If you want to add multiple activities to this surface, drag a sequence activity here first.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="1603e-113">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="1603e-113">To use this sample</span></span>  
  
1.  <span data-ttu-id="1603e-114">Otevřete CommentOut.sln v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1603e-114">Open CommentOut.sln in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="1603e-115">Zkompilujte řešení stisknutím kombinace kláves CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="1603e-115">Compile the solution by pressing CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="1603e-116">Ukázku spusťte bez ladění stisknutím kombinace kláves CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="1603e-116">Start the sample without debugging by pressing CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1603e-117">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="1603e-117">The samples may already be installed on your machine.</span></span> <span data-ttu-id="1603e-118">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="1603e-118">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="1603e-119">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="1603e-119">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1603e-120">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="1603e-120">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\CommentOut`
