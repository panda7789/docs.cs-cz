---
title: Pomocí ExpressionTextBox v Návrháři vlastní aktivity
ms.date: 03/30/2017
ms.assetid: f82e73e7-a256-4a4d-82b7-c0d62f4ab5e7
ms.openlocfilehash: ad0c29e2661c82e663fd6b68fdcd74f542ef28b1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="using-the-expressiontextbox-in-a-custom-activity-designer"></a>Pomocí ExpressionTextBox v Návrháři vlastní aktivity
Tento příklad ukazuje způsob použití <xref:System.Activities.Presentation.View.ExpressionTextBox> v Návrháři vlastní aktivity. Vlastní aktivity, `MultiAssign`, přiřadí dvou řetězcových hodnot dvě proměnné řetězce. Některé <xref:System.Activities.Presentation.View.ExpressionTextBox> k vytvoření vazby ovládacích prvků <xref:System.Activities.InArgument>s a některé vytvořit vazbu k <xref:System.Activities.OutArgument>s.  
  
## <a name="sample-details"></a>Ukázka podrobnosti  
 `ArgumentToExpressionConverter` Je převaděč typů použít při vytváření vazby výrazů pro argumenty. `ConverterParameter` Musí být nastavena na `In` nebo `Out` podle potřeby. `InOut` není podporována.  
  
 `UseLocationExpression` Atribut se používá na `OutArgument`s k určení, zda výraz by měl být výraz L-value ("levém hodnota" nebo "umístění hodnota"). Ve většině případů je výraz L-value platný identifikátor jazyka Visual Basic slouží k určení, který `OutArgument` nevrátila je název proměnné nebo argumentu.  
  
 `MaxLines` Je atribut nastaven na jednu v tomto příkladu a `MinLines` není nastaven. Znamená to, že <xref:System.Activities.Presentation.View.ExpressionTextBox> pevnou velikost jednoho řádku bez ohledu na množství text zadaný uživatelem. Chcete-li povolit <xref:System.Activities.Presentation.View.ExpressionTextBox> roste s tím, aby vyhovovaly uživatelský vstup, nastavte `MaxLines` větší než `MinLines`.  
  
 ExpressionTextBox může být vázaný jenom na argumenty a nemůže být vázán k vlastnosti CLR.  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor ExpressionTextBoxSample.sln.  
  
2.  Sestavte řešení, stiskněte CTRL + SHIFT + B.  
  
#### <a name="to-run-this-sample"></a>Chcete tuto ukázku spustit  
  
1.  Přidejte novou konzolovou aplikaci pracovní postup k řešení.  
  
2.  Přidat odkaz na **ExpressionTextBoxSample** projekt z nový projekt konzolové aplikace pracovního postupu.  
  
3.  Sestavte řešení.  
  
4.  Přetáhněte **MultiAssign** aktivity z panelu nástrojů a umístěte jej do pracovního postupu.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\ExpressionTextBox`  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Activities.Presentation.View.ExpressionTextBox>  
 [Vývoj aplikací pomocí návrháře postupu provádění](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
