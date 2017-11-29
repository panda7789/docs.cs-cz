---
title: "Automatické potvrďte vzor"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 668aec65-78d3-4636-9c7b-deed643a18f9
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 30aa268fbfa8a6f59491de30dbde6508ccdd7a68
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="auto-confirm-pattern"></a>Automatické potvrďte vzor
Tato ukázka se skládá ze tří scénářů, které spustit ilustrující vlastní `AutoConfirmScope` aktivity. První příklad ukazuje úspěšné provedení posloupnost čtyři compensable aktivit, kde vnořených druhý a třetí v `AutoConfirmScope`. Druhý příklad ukazuje stejné pořadí s výjimkou po provedení čtvrtý <xref:System.Activities.Statements.CompensableActivity>. Třetí scénář ukazuje stejné pořadí s výjimku, ke kterým dochází v `AutoConfirmScope` po druhá <xref:System.Activities.Statements.CompensableActivity> dokončení.  
  
 Ukázka ukazuje auto-confirm vzor, kde jsou všechny podřízené compensable aktivity potvrzen po úspěšném oboru. Tento vzor definuje životnost všechny podřízené compensable aktivity, jako se dá už kompenzované nebo potvrzen.  
  
 Obor se skládá z <xref:System.Activities.Statements.TryCatch> kde <xref:System.Activities.Statements.TryCatch.Try%2A> je interní <xref:System.Activities.Statements.CompensableActivity>. Tělo zadán uživatel `AutoConfirmScope` tělo vnitřního <xref:System.Activities.Statements.CompensableActivity>. Při tomto interní <xref:System.Activities.Statements.CompensableActivity> dokončí, vyvolá <xref:System.Activities.Statements.CompensationToken> jako argumentem na více systémů. `AutoConfirmScope` Používá <xref:System.Activities.Statements.TryCatch.Finally%2A> ke kontrole, jestli se vytvořily token a pokud platnost vypršela, potvrzuje se tím vnitřní <xref:System.Activities.Statements.CompensableActivity>. Vnitřní <xref:System.Activities.Statements.CompensableActivity> vyvolá výchozí náhradu za žádné compensable aktivity, které mohou existovat v jeho obsahu.  
  
 První scénář ukazuje úspěšné provedení pracovního postupu a ukazuje, druhý a třetí compensable aktivity jsou při dokončení pracovního postupu a první a čtvrtý potvrzují již potvrzen. To vytváří potvrzení pořadí tři, dva, čtyři a jeden.  
  
 Druhý scénář ukazuje výjimku po dokončení čtyři compensable aktivity. Protože jsou již potvrzen compensable aktivity dva a tři jsou poškozena, ale jedna a čtyřmi jsou kompenzované. Tato vytváří potvrďte tři, potvrďte dva, odpovídajícím způsobem čtyři a odpovídajícím způsobem jeden.  
  
 Poslední scénář popisuje úspěšné provedení `AutoConfirmScope`. V tomto scénáři, dojde k výjimce po dokončení druhý <xref:System.Activities.Statements.CompensableActivity>. Vzhledem k tomu, že nebyly provést třetí a čtvrtý compensable aktivity, jsou poškozena. Protože oboru nebyla dokončena úspěšně, druhý <xref:System.Activities.Statements.CompensableActivity> získat nebyl potvrzen. Tento vytváří a kompenzace pořadí dvě pak jeden.  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení AutoConfirmSample.sln.  
  
2.  Sestavte řešení, stiskněte CTRL + SHIFT + B.  
  
3.  Chcete-li spustit řešení, stiskněte CTRL + F5.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Compensation\AutoConfirm`  
  
## <a name="see-also"></a>Viz také
