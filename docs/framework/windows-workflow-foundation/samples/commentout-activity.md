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
# <a name="commentout-activity"></a>Aktivita CommentOut
Tato ukázka předvádí, jak psát vlastní aktivitu, která odebere z cesty spuštění efektivně komentářů je jiné aktivity.  
  
## <a name="the-commentout-activity"></a>Aktivita CommentOut  
 K dosažení jejího cíle – aktivita CommentOut je odvozen od <xref:System.Activities.CodeActivity> základní třídy a implementuje prázdná <xref:System.Activities.CodeActivity.Execute%2A> metody.  
  
```  
protected override void Execute(CodeActivityContext context)  
{  
}  
```  
  
 Třída je deklarována, jak je znázorněno v následujícím příkladu.  
  
```  
[Designer(typeof(CommentOutDesigner))]  
[ContentProperty("Body")]  
public sealed class CommentOut : CodeActivity  
```  
  
 `Designer` Atribut určuje třídu, která implementuje rozhraní visual aktivity v době návrhu. `ContentProperty` Atributu deklaruje, že `"Body"` vlastnosti mohou být přeskočeny v XAML reprezentaci instance této aktivity.  
  
```  
<Border x:Uid="Border_1" BorderThickness ="1">  
    <sad:WorkflowItemPresenter   
    x:Uid="sad:WorkflowItemPresenter_1" AutomationProperties.AutomationId="Body" Item="{Binding Path=ModelItem.Body, Mode=TwoWay}"  
    AllowedItemType="{x:Type sa:Activity}"  
    HintText="Drop activity here"   
    Margin="5,5,5,5" />  
</Border>  
```  
  
 Ve třídě návrháře XAML slouží k vytvoření vlastní vizuální znázornění aktivity. <xref:System.Activities.Presentation.WorkflowItemPresenter> je třída, která poskytuje vizuální editor.  
  
 Jediné aktivity může být přetaženy `CommentOut` aktivity povrchu. Pokud chcete přidat více aktivit do tuto plochu, sekvenční aktivity Sem přetáhněte nejdřív.  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Otevřete CommentOut.sln v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Zkompilujte řešení stisknutím kombinace kláves CTRL + SHIFT + B.  
  
3.  Ukázku spusťte bez ladění stisknutím kombinace kláves CTRL + F5.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\CommentOut`
