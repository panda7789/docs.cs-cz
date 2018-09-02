---
title: Skupina podmíněných aktivit
ms.date: 03/30/2017
ms.assetid: f76ef924-34ce-48ae-8c8d-48faf9697754
ms.openlocfilehash: 144a6c76ea6314c553e201fe4e2364890d869f34
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43418166"
---
# <a name="conditioned-activity-group"></a>Skupina podmíněných aktivit
Ukázka demonstruje aplikaci rezervace cesty. <xref:System.Workflow.Activities.ConditionedActivityGroup> (CAG) má dvě aktivity kódu: aktivita Car a aktivita letecká společnost. V `SimpleCAGWorkflow` konstruktor objekt ArrayList "travelNeedType" se vyplní typy cestovní rezervací, které jsou požadovány. Tak jedno nebo obě `travelNeeds.Add` příkazy, odpovídajícím způsobem upravit chování CAG. Auto i letecká společnost aktivity mají jejich <xref:System.Workflow.Activities.ConditionedActivityGroup.WhenConditionProperty> vyplní podmínku <xref:System.Workflow.Activities.CodeCondition>. Car aktivita spustí jenom v případě, `travelNeeds` kolekce má `TravelNeeds.Car` položky a aktivity spustí jenom v případě letecká společnost `travelNeeds` kolekce má `TravelNeeds.Airline` položka.  
  
 Provedení každé aktivity odebere odpovídající položku z kolekce. Výchozí hodnota <xref:System.Workflow.Activities.ConditionedActivityGroup.UntilCondition%2A> Podmínka určuje to, že CAG by měla ukončit při žádné podřízené položky jsou provádění nebo jsou připravené ke spuštění (na základě jejich <xref:System.Workflow.Activities.ConditionedActivityGroup.WhenConditionProperty> podmínky). V této ukázce, to znamená, že CAG ukončí, když `travelNeeds` kolekce je prázdná.  
  
### <a name="to-build-the-sample"></a>K vytvoření vzorku  
  
1.  Otevřete řešení v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Sestavte řešení stisknutím kombinace kláves CTRL + SHIFT + B.  
  
3.  Spuštění řešení bez ladění stisknutím kombinace kláves CTRL + F5.  
  
### <a name="to-run-the-sample"></a>Chcete-li spustit ukázku  
  
-   V okně příkazového řádku sady SDK spusťte soubor .exe ve složce SimpleCAG\bin\debug (nebo ve složce SimpleCAG\bin pro verzi ukázky, která se týká jazyka Visual Basic), který se nachází pod hlavní složku pro vzorku.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno ve vašem počítači. Před pokračováním zkontrolujte následující adresář (výchozí):  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři:  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\SimpleCAG`  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Workflow.Activities.ConditionedActivityGroup>  
 <xref:System.Workflow.Activities.ConditionedActivityGroup.WhenConditionProperty>  
 <xref:System.Workflow.Activities.CodeCondition>  
 <xref:System.Workflow.Activities.ConditionedActivityGroup.UntilCondition%2A>
