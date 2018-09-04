---
title: Jednoduché zásady
ms.date: 03/30/2017
ms.assetid: 6a94c834-2e32-4bed-9f47-ae5845eef6ff
ms.openlocfilehash: 7f189e4d1811cb0b7dd9138b944bfd0552481690
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43561261"
---
# <a name="simple-policy"></a>Jednoduché zásady
Tento příklad ukazuje způsob použití <xref:System.Workflow.Activities.PolicyActivity> aktivity v pracovním postupu.  
  
 Sekvenční pracovní postup v této ukázce se vytvoří pomocí <xref:System.Workflow.Activities.PolicyActivity> aktivity. Pracovní postup definuje `orderValue`, `customerType`, a `discount` pole, která se používají k definování produktu slevy pracovního postupu. Z pravidel definovaných v souboru pravidel nastavení, která je založena na hodnoty slevy `orderValue` a `customerType`. `orderValue` a `customerType` jsou nastaveny `SimplePolicyWorkflow` definici třídy a změnit chování lze změnit. Výsledný slevy je zapsán v konzole <xref:System.Workflow.Runtime.WorkflowRuntime.WorkflowCompleted> obslužná rutina události, která je definována v `SimplePolicyWorkflow` třídy.  
  
### <a name="to-build-the-sample"></a>K vytvoření vzorku  
  
1.  Otevřete řešení v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Sestavte řešení stisknutím kombinace kláves CTRL + SHIFT + B.  
  
3.  Spuštění řešení bez ladění stisknutím kombinace kláves CTRL + F5.  
  
### <a name="to-run-the-sample"></a>Chcete-li spustit ukázku  
  
-   V okně příkazového řádku sady SDK spusťte soubor .exe ve složce SimplePolicy\bin\debug (nebo ve složce SimplePolicy\bin pro verzi ukázky, která se týká jazyka Visual Basic), který se nachází pod hlavní složku pro vzorku.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno ve vašem počítači. Před pokračováním zkontrolujte následující adresář (výchozí):  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři:  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\Policy\SimplePolicy`  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Workflow.Activities.Rules.RuleSet>  
 <xref:System.Workflow.Activities.PolicyActivity>  
 [Pokročilé zásady](../../../../docs/framework/windows-workflow-foundation/samples/advanced-policy.md)
