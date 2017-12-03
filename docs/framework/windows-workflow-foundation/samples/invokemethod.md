---
title: InvokeMethod
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 04988eb3-65f8-456d-b1bd-509f5d05a57c
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c275943d37a3602335ecd898aed3feb6c9059edf
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="invokemethod"></a>InvokeMethod
Tento příklad ukazuje různé způsoby použití <xref:System.Activities.Statements.InvokeMethod> aktivity k vyvolání metody třídy.  
  
 Metoda patří do třídy, představuje sadu operací obsažené. <xref:System.Activities.Statements.InvokeMethod> Aktivity vám dává možnost volání metod s objekty nebo typů, předat parametry a získat návratovou hodnotu. Metody mohou být vyvolány synchronně nebo asynchronně.  
  
## <a name="sample-details"></a>Ukázka podrobnosti  
 V tomto příkladu <xref:System.Activities.Statements.InvokeMethod> aktivita k provedení následujících scénářů:  
  
1.  Vyvolání metody instance bez parametrů.  
  
2.  Vyvolání metody instance s dva parametry (<xref:System.String> a <xref:System.Int32>).  
  
3.  Vyvolání metody instance s dva parametry (<xref:System.String> a <xref:System.Int32>) a parametr pole typu <xref:System.String>[].  
  
4.  Vyvolání metody instance s dva parametry typu <xref:System.Int32> a výsledek typu <xref:System.Int32>. V tomto scénáři je výsledkem hodnota vázaná na proměnnou a použít v jiné aktivitě. Zobrazí se v konzole pomocí <xref:System.Activities.Statements.WriteLine> aktivity.  
  
5.  Vyvolání statickou metodu s dva parametry typu <xref:System.String> a <xref:System.Int32>.  
  
6.  Vyvolání metody instance s jeden obecný parametr typu <xref:System.String>.  
  
7.  Vyvolání statickou metodu s dvě obecné parametry typu <xref:System.String> a <xref:System.Int32>.  
  
8.  Vyvolání metody instance, který má jeden parametr předaná odkaz na typ <xref:System.String>. V tomto scénáři vazbu parametru odkazu na proměnnou (`outParam`) a použít v jiné aktivitě. Zobrazí se v konzole pomocí <xref:System.Activities.Statements.WriteLine> aktivity.  
  
9. Vyvolání metody asynchronní instance.  
  
10. Vyvolání dvě různé metody na stejnou instanci objekt, který používá dva <xref:System.Activities.Statements.InvokeMethod> aktivity.  
  
11. Hodnotu uložte instanci objektu.  
  
12. Načtení hodnoty z instance objektu.  
  
## <a name="to-use-this-sample"></a>Pro fungování této ukázky  
 Tato ukázka je součástí dvě verze. První verzi této ukázce ukazuje použití <xref:System.Activities.Statements.InvokeMethod> prostřednictvím jazyka C# kódu, pomocí [!INCLUDE[wf](../../../../includes/wf-md.md)] programovací model a nachází se ve složce CodedWorkflow\CS. Druhá verze ukazuje použití <xref:System.Activities.Statements.InvokeMethod> pomocí XAML a nachází se ve složce DesignerWorkflow\CS.  
  
#### <a name="to-run-the-coded-workflow-sample"></a>Ke spuštění ukázky programové pracovního postupu  
  
1.  Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení InvokeMethodUsage.sln ve složce CodedWorkflow\CS.  
  
2.  Sestavte řešení, stiskněte CTRL + SHIFT + B.  
  
3.  Chcete-li spustit řešení, stiskněte CTRL + F5.  
  
#### <a name="to-run-the-designer-workflow-sample"></a>Ke spuštění ukázky Návrháře pracovního postupu  
  
1.  Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení InvokeMethodUsage.sln ve složce DesignerWorkflow\CS.  
  
2.  Sestavte řešení, stiskněte CTRL + SHIFT + B.  
  
3.  Chcete-li spustit řešení, stiskněte CTRL + F5.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\InvokeMethod`