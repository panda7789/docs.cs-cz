---
title: Jednoduché zásady
ms.date: 03/30/2017
ms.assetid: 6a94c834-2e32-4bed-9f47-ae5845eef6ff
ms.openlocfilehash: dff3979d75fdeb5a45be3940af3568c26f5e8f98
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33515893"
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
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři:  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\Policy\SimplePolicy`  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Workflow.Activities.Rules.RuleSet>  
 <xref:System.Workflow.Activities.PolicyActivity>  
 [Pokročilé zásady](../../../../docs/framework/windows-workflow-foundation/samples/advanced-policy.md)
