---
title: Potvrzení
ms.date: 03/30/2017
ms.assetid: 8637aeaf-ac9e-49b8-93f4-da15dee45277
ms.openlocfilehash: caa712aa52da01ce44335a361fd6c9f5215316bf
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45964472"
---
# <a name="confirmation"></a>Potvrzení
Tento příklad ukazuje čtyři běžné scénáře použití okolní <xref:System.Activities.Statements.CompensableActivity> a potvrzení hesla. Ukázka spouští čtyři pracovní postupy pro zobrazení potvrzení. Tato ukázka je k dispozici ve verzích deklarativního a imperativního.  
  
## <a name="confirm-a-compensable-activity"></a>Potvrďte Kompenzovatelná aktivita  
 První pracovní postup ukazuje, jak se potvrzení kompenzovatelné aktivity a tvoří ho pořadí dvou <xref:System.Activities.Statements.CompensableActivity> instancí. Po dokončení druhého <xref:System.Activities.Statements.CompensableActivity> aktivitu potvrzení potvrdí první aktivitu. Po dokončení pracovního postupu úspěšně, všechny <xref:System.Activities.Statements.CompensableActivity> instancí, které nebyly byla potvrzena nebo kompenzována potvrzují automaticky pomocí výchozí pořadí. Bez potvrzení druhý <xref:System.Activities.Statements.CompensableActivity> by byly potvrzeny nejprve.  
  
## <a name="explicit-compensation"></a>Explicitní kompenzace  
 Druhý scénář popisuje vliv na výchozí potvrzení při <xref:System.Activities.Statements.CompensableActivity> explicitně kompenzována. Pracovní postup se skládá ze dvou posloupnost <xref:System.Activities.Statements.CompensableActivity> aktivity po dokončení první druhý je explicitně kompenzována. V důsledku po dokončení pracovního postupu, pouze sekundu <xref:System.Activities.Statements.CompensableActivity> je potvrzeno.  
  
## <a name="controlling-the-order-of-confirmation-for-nested-compensableactivity-activities"></a>Pořadí potvrzení pro aktivity CompensableActivity vnořené řízení  
 Třetí scénář popisuje, jak řídit pořadí potvrzení pro vnořené <xref:System.Activities.Statements.CompensableActivity>. Tento scénář se skládá z <xref:System.Activities.Statements.CompensableActivity> jako kořen pracovního postupu. Tělo kořenové <xref:System.Activities.Statements.CompensableActivity> je posloupnost tří <xref:System.Activities.Statements.CompensableActivity>. <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> Pro kořenovou <xref:System.Activities.Statements.CompensableActivity> je sekvence, která určuje potvrďte první a druhý vnořené <xref:System.Activities.Statements.CompensableActivity>. Po dokončení pracovního postupu potvrdí kořenové <xref:System.Activities.Statements.CompensableActivity>, která potvrdí první, druhý a třetí vnořené <xref:System.Activities.Statements.CompensableActivity>v tomto pořadí. V důsledku toho je v podstatě obrácený pořadí výchozí potvrzení. Protože třetí <xref:System.Activities.Statements.CompensableActivity> nebyl explicitně potvrzena jako část kořenové <xref:System.Activities.Statements.CompensableActivity> podle <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>, je potvrzen v pořadí, výchozí. Ale protože pouze nepotvrzené <xref:System.Activities.Statements.CompensableActivity> to pouze znamená, že je potvrzeno.  
  
## <a name="scoping-of-variables"></a>Nastavení rozsahu proměnné  
 Čtvrtý scénář popisuje, jak životnost proměnné definované pro <xref:System.Activities.Statements.CompensableActivity> nebo jeden z jejich nadřazených objektů jsou stále v oboru při <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>, <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> nebo <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> obslužné rutiny jsou provedeny i v případě, že byla aktivita dokončena nebo je pracovní postup Dokončit. Pracovní postup se skládá ze dvou posloupnost <xref:System.Activities.Statements.CompensableActivity>. V těle první proměnné `mySum` je nastavena na součet 5 a 10 a výsledek vytisknout. V těle druhého <xref:System.Activities.Statements.CompensableActivity>, součet je nastavena na součet existující sum a 7 a vytisknout výsledek. Obslužné rutiny vlastních potvrzení je definována pro první <xref:System.Activities.Statements.CompensableActivity>, který vytiskne součet, odečte 7 a vytiskne součet znovu. Je jasné zkontrolováním tištěné součty, které proměnná je v oboru není jenom pro instituce obě <xref:System.Activities.Statements.CompensableActivity> ale <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> také.  
  
#### <a name="to-run-the-sample"></a>Chcete-li spustit ukázku  
  
1.  Načtení řešení v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Spusťte aplikaci ConfirmationSample.exe.  
  
3.  Podívejte se následující výstup:  
  
 **Explicitní potvrzení: Start workflowCompensableActivity1: BodyCompensableActivity2: BodyCompensableActivity1: potvrzení HandlerEnd workflowCompensableActivity2: potvrzení HandlerExplicit kompenzace: začátek workflowCompensableActivity1: BodyCompensableActivity2: BodyCompensableActivity1: kompenzace HandlerEnd workflowCompensableActivity2: potvrzení HandlerCustom workflowCompensableActivity1 potvrzení. obslužná rutina: Spusťte: BodyCompensableActivity2: BodyCompensableActivity3: BodyEnd workflowCompensableActivity1: potvrzení HandlerCompensableActivity2: potvrzení HandlerCompensableActivity3: potvrzení HandlerVariable přístup v popisovači potvrzení: Začátek workflowCompensableActivity1: BodyCompensableActivity1: součet: 15CompensableActivity2: BodyCompensableActivity2: Přidání 7 sumCompensableActivity2: je součet: 22End workflowCompensableActivity2: potvrzení HandlerCompensableActivity1: Potvrzení HandlerCompensableActivity2: součet: 22CompensableActivity2: po odečtení 12 součet je nyní: 10Press ENTER ukončete.**  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Compensation\Confirmation`