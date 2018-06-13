---
title: Klimatizovaném skupiny aktivit
ms.date: 03/30/2017
ms.assetid: f76ef924-34ce-48ae-8c8d-48faf9697754
ms.openlocfilehash: 3560542b912f9697ec2e77c8d5c82e148a41d485
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33514062"
---
# <a name="conditioned-activity-group"></a>Klimatizovaném skupiny aktivit
Ukázka ukazuje na aplikaci rezervace cesta. <xref:System.Workflow.Activities.ConditionedActivityGroup> (CAG) má dvě aktivity kód: aktivitu Car a aktivitu letecká společnost. V `SimpleCAGWorkflow` konstruktoru, objekt ArrayList "travelNeedType" naplněný typy cesta rezervace, které jsou požadovány. Pomocí komentářů na jeden nebo oba `travelNeeds.Add` příkazy, můžete změnit chování CAG odpovídajícím způsobem. Auto i letecká společnost aktivity mají jejich <xref:System.Workflow.Activities.ConditionedActivityGroup.WhenConditionProperty> naplněný podmínku <xref:System.Workflow.Activities.CodeCondition>. Aktivity Car provádí pouze v případě, `travelNeeds` kolekce má `TravelNeeds.Car` položku a letecká společnost aktivita se spustí pouze v případě `travelNeeds` kolekce má `TravelNeeds.Airline` položku.  
  
 Spuštění každé aktivity odebere odpovídající položku z kolekce. Výchozí hodnota <xref:System.Workflow.Activities.ConditionedActivityGroup.UntilCondition%2A> podmínka Určuje, že CAG musí ukončit, i když žádné podřízené objekty jsou prováděny nebo jsou připravené ke spuštění (na základě jejich <xref:System.Workflow.Activities.ConditionedActivityGroup.WhenConditionProperty> podmínky). V této ukázce, to znamená, že CAG ukončí při `travelNeeds` kolekce je prázdná.  
  
### <a name="to-build-the-sample"></a>Chcete-li sestavit ukázku  
  
1.  Otevřete řešení v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Sestavte řešení stisknutím kombinace kláves CTRL + SHIFT + B.  
  
3.  Spustíte řešení bez ladění stisknutím kombinace kláves CTRL + F5.  
  
### <a name="to-run-the-sample"></a>Chcete-li spustit ukázku  
  
-   V okně Příkazový řádek SDK spusťte soubor .exe ve složce SimpleCAG\bin\debug (nebo ve složce SimpleCAG\bin pro verzi ukázky jazyka Visual Basic), který se nachází pod hlavní složku pro ukázku.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalován ve vašem počítači. Před pokračováním zkontrolovat na následující adresář (výchozí):  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři:  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\SimpleCAG`  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Workflow.Activities.ConditionedActivityGroup>  
 <xref:System.Workflow.Activities.ConditionedActivityGroup.WhenConditionProperty>  
 <xref:System.Workflow.Activities.CodeCondition>  
 <xref:System.Workflow.Activities.ConditionedActivityGroup.UntilCondition%2A>
