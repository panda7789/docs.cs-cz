---
title: "Jednoduché zásady"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6a94c834-2e32-4bed-9f47-ae5845eef6ff
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0c704a9f3f27d63fb1a28db61f03cdc9b8de4370
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="simple-policy"></a>Jednoduché zásady
Tento příklad ukazuje způsob použití <xref:System.Workflow.Activities.PolicyActivity> aktivity v pracovním postupu.  
  
 Sekvenční pracovní postup v této ukázce je vytvořená pomocí <xref:System.Workflow.Activities.PolicyActivity> aktivity. Pracovní postup definuje `orderValue`, `customerType`, a `discount` pole, která slouží k určení produktu slevách pracovního postupu. Pravidla definovaná v souboru pravidel nastavit slevu hodnotu, která je založena na `orderValue` a `customerType`. `orderValue` a `customerType` jsou nastavené `SimplePolicyWorkflow` definici třídy a ke změně chování lze změnit. Výsledný slevu je zapsán do konzoly v <xref:System.Workflow.Runtime.WorkflowRuntime.WorkflowCompleted> obslužné rutiny události, která je definována v `SimplePolicyWorkflow` třídy.  
  
### <a name="to-build-the-sample"></a>Chcete-li sestavit ukázku  
  
1.  Otevřete řešení v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Sestavte řešení stisknutím kombinace kláves CTRL + SHIFT + B.  
  
3.  Spustíte řešení bez ladění stisknutím kombinace kláves CTRL + F5.  
  
### <a name="to-run-the-sample"></a>Chcete-li spustit ukázku  
  
-   V okně Příkazový řádek SDK spusťte soubor .exe ve složce SimplePolicy\bin\debug (nebo ve složce SimplePolicy\bin pro verzi ukázky jazyka Visual Basic), který se nachází pod hlavní složku pro ukázku.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalován ve vašem počítači. Před pokračováním zkontrolovat na následující adresář (výchozí):  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři:  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\Policy\SimplePolicy`  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Workflow.Activities.Rules.RuleSet>  
 <xref:System.Workflow.Activities.PolicyActivity>  
 [Rozšířené zásady](../../../../docs/framework/windows-workflow-foundation/samples/advanced-policy.md)
