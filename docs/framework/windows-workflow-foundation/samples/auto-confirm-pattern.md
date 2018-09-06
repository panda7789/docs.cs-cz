---
title: Vzor automatického potvrzení
ms.date: 03/30/2017
ms.assetid: 668aec65-78d3-4636-9c7b-deed643a18f9
ms.openlocfilehash: a032c05743b64fe58b0b187328b5216080ba6e19
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43864052"
---
# <a name="auto-confirm-pattern"></a>Vzor automatického potvrzení
Tato ukázka se skládá ze tří scénářů, na kterých běží ilustrující vlastní `AutoConfirmScope` aktivity. První příklad ukazuje úspěšné provedení posloupnost čtyři kompenzovatelné aktivity, kde druhého a třetího jsou vnořené v `AutoConfirmScope`. Druhý příklad ukazuje stejnou sekvenci, s výjimkou po zpracování čtvrtým <xref:System.Activities.Statements.CompensableActivity>. Třetí scénář popisuje stejnou sekvenci, s výjimkou ke kterým dochází v `AutoConfirmScope` po druhé <xref:System.Activities.Statements.CompensableActivity> dokončí.  
  
 Ukázce auto-confirm vzor, ve kterém byly potvrzeny všechny podřízené kompenzovatelné aktivity po úspěšném dokončení oboru. Tento model definuje životnost všechny podřízené kompenzovatelné aktivity, jak můžete již měly být kompenzovat nebo potvrdit.  
  
 Se skládá z oboru <xref:System.Activities.Statements.TryCatch> kde <xref:System.Activities.Statements.TryCatch.Try%2A> je interní <xref:System.Activities.Statements.CompensableActivity>. Uživatel zadal text `AutoConfirmScope` tělo vnitřní <xref:System.Activities.Statements.CompensableActivity>. Při tomto interní <xref:System.Activities.Statements.CompensableActivity> dokončí, vytváří <xref:System.Activities.Statements.CompensationToken> jako výstupní argument. `AutoConfirmScope` Používá <xref:System.Activities.Statements.TryCatch.Finally%2A> ke kontrole, jestli byl získán token a pokud platnost vypršela, potvrzuje se tím vnitřní <xref:System.Activities.Statements.CompensableActivity>. Vnitřní <xref:System.Activities.Statements.CompensableActivity> vyvolá výchozí náhradu za žádné kompenzovatelné aktivity, které mohou existovat v těle.  
  
 První scénář zobrazuje úspěšné provedení pracovního postupu a ukazuje, druhý a třetí kompenzovatelné aktivity již potvrzen při dokončení pracovního postupu a první a čtvrtý potvrzují. To vytváří potvrzení objednávky tři, dva, čtyři a jedna.  
  
 Druhý scénář popisuje výjimku, po dokončení čtyři kompenzovatelné aktivity. Vzhledem k tomu, že již byly potvrzeny kompenzovatelné aktivity dva a tři, nejsou ovlivněny ale jedno a čtyři dostávají. Toto vytvoří tři potvrďte, dvě potvrzení, kompenzaci čtyři a kompenzovat jeden.  
  
 Poslední scénář ukazuje úspěšné provedení `AutoConfirmScope`. V tomto scénáři, dojde k výjimce po dokončení druhého <xref:System.Activities.Statements.CompensableActivity>. Protože nebyly provedeny třetí a čtvrtý kompenzovatelné aktivity, jsou poškozena. Protože oboru neproběhla úspěšně, druhý <xref:System.Activities.Statements.CompensableActivity> získat není potvrzena. Toto vytvoří a pořadí kompenzaci dvou pak jeden.  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení AutoConfirmSample.sln.  
  
2.  Abyste mohli sestavit řešení, stiskněte kombinaci kláves CTRL + SHIFT + B.  
  
3.  Abyste mohli spustit řešení, stiskněte CTRL + F5.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Compensation\AutoConfirm`