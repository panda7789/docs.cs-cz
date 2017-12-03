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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e66d1383c42310c2f61b0b3059cb8b347ad55a15
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="commentout-activity"></a>CommentOut aktivity
Tento příklad znázorňuje, jak psát vlastní aktivity, která odebere z cesty k provádění, efektivně komentářů je ostatní aktivity.  
  
## <a name="the-commentout-activity"></a>CommentOut aktivity  
 Zajistit jeho cílem CommentOut aktivity je odvozena z <xref:System.Activities.CodeActivity> základní třídy a implementuje prázdnou <xref:System.Activities.CodeActivity.Execute%2A> metoda.  
  
```  
protected override void Execute(CodeActivityContext context)  
{  
}  
```  
  
 Třída je deklarovaná, jak je znázorněno v následujícím příkladu.  
  
```  
[Designer(typeof(CommentOutDesigner))]  
[ContentProperty("Body")]  
public sealed class CommentOut : CodeActivity  
```  
  
 `Designer` Atribut určuje třídu, která implementuje rozhraní visual aktivity v době návrhu. `ContentProperty` Atribut uvádí, že `"Body"` vlastnosti mohou být přeskočeny v XAML reprezentace instance této aktivity.  
  
```  
<Border x:Uid="Border_1" BorderThickness ="1">  
    <sad:WorkflowItemPresenter   
    x:Uid="sad:WorkflowItemPresenter_1" AutomationProperties.AutomationId="Body" Item="{Binding Path=ModelItem.Body, Mode=TwoWay}"  
    AllowedItemType="{x:Type sa:Activity}"  
    HintText="Drop activity here"   
    Margin="5,5,5,5" />  
</Border>  
```  
  
 Ve třídě návrháře XAML slouží k vytvoření vlastní vizuální reprezentace aktivity. <xref:System.Activities.Presentation.WorkflowItemPresenter>je třída, která poskytuje vizuální editor.  
  
 Jediné aktivity může být přetažen na `CommentOut` prostor pro aktivity. Pokud chcete přidat více aktivit do tento prostor, přetáhněte aktivitu pořadí sem nejdřív.  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Otevřete CommentOut.sln v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Zkompilujte řešení stisknutím kombinace kláves CTRL + SHIFT + B.  
  
3.  Spusťte ukázku bez ladění stisknutím kombinace kláves CTRL + F5.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\CommentOut`
