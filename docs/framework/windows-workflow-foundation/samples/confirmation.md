---
title: Potvrzení
ms.date: 03/30/2017
ms.assetid: 8637aeaf-ac9e-49b8-93f4-da15dee45277
ms.openlocfilehash: 334ac362333565626dd2bb8dcaede27fbab16f33
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33518842"
---
# <a name="confirmation"></a>Potvrzení
Tento příklad ukazuje čtyři běžné scénáře, které obaluje použití <xref:System.Activities.Statements.CompensableActivity> a potvrzení hesla. Ukázka spustí čtyři pracovní postupy pro zobrazení potvrzení. Tato ukázka je dostupná v deklarativní a imperativní verze.  
  
## <a name="confirm-a-compensable-activity"></a>Potvrďte Compensable aktivity  
 První pracovní postup ukazuje, jak potvrďte compensable aktivity a skládá se z pořadí dva <xref:System.Activities.Statements.CompensableActivity> instance. Po dokončení druhý <xref:System.Activities.Statements.CompensableActivity> aktivitu potvrdit potvrdí první aktivitu. Když pracovní postup úspěšně dokončí, všechny <xref:System.Activities.Statements.CompensableActivity> instancí, které nebyly potvrzeny ani kompenzované automaticky potvrzena pomocí výchozí pořadí. Bez potvrzení druhý <xref:System.Activities.Statements.CompensableActivity> by byly potvrzeny nejdřív.  
  
## <a name="explicit-compensation"></a>Explicitní kompenzace  
 Druhý scénář ukazuje vlivu na výchozí potvrzení při <xref:System.Activities.Statements.CompensableActivity> je explicitně kompenzované. Pracovní postup se skládá z pořadí dva <xref:System.Activities.Statements.CompensableActivity> aktivit, po dokončení první druhý je explicitně kompenzované. V důsledku při dokončení pracovního postupu, pouze druhý <xref:System.Activities.Statements.CompensableActivity> je potvrzen.  
  
## <a name="controlling-the-order-of-confirmation-for-nested-compensableactivity-activities"></a>Řízení pořadí potvrzení pro vnořené CompensableActivity aktivity  
 Třetí scénář ukazuje, jak řídit pořadí potvrzení pro vnořené <xref:System.Activities.Statements.CompensableActivity>. Tento scénář se skládá z <xref:System.Activities.Statements.CompensableActivity> jako kořen pracovního postupu. Tělo kořenu <xref:System.Activities.Statements.CompensableActivity> je posloupnost tři <xref:System.Activities.Statements.CompensableActivity>. <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> Pro kořenovou <xref:System.Activities.Statements.CompensableActivity> je řada, která určuje potvrďte první a druhý vnořené <xref:System.Activities.Statements.CompensableActivity>. Po dokončení pracovního postupu kořenové potvrzuje <xref:System.Activities.Statements.CompensableActivity>, který pak potvrdí první, druhý a třetí vnořené <xref:System.Activities.Statements.CompensableActivity>, v tomto pořadí. V důsledku toho je v podstatě výchozí pořadí potvrzení obrácený. Protože třetí <xref:System.Activities.Statements.CompensableActivity> nebyl potvrzen explicitně jako část kořenové <xref:System.Activities.Statements.CompensableActivity> podle <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>, je potvrzen podle výchozí pořadí. Ale protože je to jediné nepotvrzeného <xref:System.Activities.Statements.CompensableActivity> to znamená právě je potvrzen.  
  
## <a name="scoping-of-variables"></a>Obor proměnné  
 Čtvrtý scénář popisuje, jak životnost proměnné definované pro <xref:System.Activities.Statements.CompensableActivity> nebo některý ze svých nadřazených složek jsou pořád ještě v oboru, kdy <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>, <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> nebo <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> obslužné rutiny jsou spouštěny i v případě, že dokončení aktivity nebo má pracovní postup byla dokončena. Pracovní postup se skládá z pořadí dva <xref:System.Activities.Statements.CompensableActivity>. V těle první, proměnná `mySum` je nastaven na součet 5 a 10 a výsledek vytisknout. V těle druhý <xref:System.Activities.Statements.CompensableActivity>, součet je nastaven na součet existující součet a 7 a výsledek vytisknout. Obslužná rutina vlastní potvrzení je definována pro první <xref:System.Activities.Statements.CompensableActivity>, který vytiskne součet, odečte 7 a vytiskne součet znovu. Je zřejmé, zkontrolováním na tištěných součty, které je proměnné v oboru, ne jenom pro těla i <xref:System.Activities.Statements.CompensableActivity> ale <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> také.  
  
#### <a name="to-run-the-sample"></a>Chcete-li spustit ukázku  
  
1.  Spouštění řešení v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Spusťte aplikaci ConfirmationSample.exe.  
  
3.  Sledujte následující výstup:  
  
 **Explicitní potvrzení: spuštění workflowCompensableActivity1: BodyCompensableActivity2: BodyCompensableActivity1: potvrzení HandlerEnd z workflowCompensableActivity2: potvrzení HandlerExplicit kompenzace: začátek workflowCompensableActivity1: BodyCompensableActivity2: BodyCompensableActivity1: kompenzace HandlerEnd z workflowCompensableActivity2: potvrzení HandlerCustom potvrzení obslužná rutina: začátek workflowCompensableActivity1: BodyCompensableActivity2: BodyCompensableActivity3: BodyEnd workflowCompensableActivity1: HandlerCompensableActivity2 potvrzení: potvrzení HandlerCompensableActivity3: HandlerVariable potvrzení přístupu v obslužnou rutinu potvrzení: Začátek workflowCompensableActivity1: BodyCompensableActivity1: je součet: 15CompensableActivity2: BodyCompensableActivity2: Přidání 7 sumCompensableActivity2: součet je nyní: 22End workflowCompensableActivity2: potvrzení HandlerCompensableActivity1: Potvrzení HandlerCompensableActivity2: je součet: 22CompensableActivity2: po odečtení 12 součet je nyní: 10Press ENTER ukončíte.**  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Compensation\Confirmation`