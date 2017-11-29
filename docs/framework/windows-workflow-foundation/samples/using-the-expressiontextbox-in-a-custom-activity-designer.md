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
# <a name="using-the-expressiontextbox-in-a-custom-activity-designer"></a>Pomocí ExpressionTextBox v Návrháři vlastní aktivity
Tento příklad ukazuje způsob použití <xref:System.Activities.Presentation.View.ExpressionTextBox> v Návrháři vlastní aktivity. Vlastní aktivity, `MultiAssign`, přiřadí dvou řetězcových hodnot dvě proměnné řetězce. Některé <xref:System.Activities.Presentation.View.ExpressionTextBox> k vytvoření vazby ovládacích prvků <xref:System.Activities.InArgument>s a některé vytvořit vazbu k <xref:System.Activities.OutArgument>s.  
  
## <a name="sample-details"></a>Ukázka podrobnosti  
 `ArgumentToExpressionConverter` Je převaděč typů použít při vytváření vazby výrazů pro argumenty. `ConverterParameter` Musí být nastavena na `In` nebo `Out` podle potřeby. `InOut`není podporována.  
  
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
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\ExpressionTextBox`  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Activities.Presentation.View.ExpressionTextBox>  
 [Vývoj aplikací pomocí návrháře pracovních postupů](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
