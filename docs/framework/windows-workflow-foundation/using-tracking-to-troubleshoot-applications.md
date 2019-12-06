---
title: Řešení problémů s aplikací pomocí sledování
ms.date: 03/30/2017
ms.assetid: 8851adde-c3c2-4391-9523-d8eb831490af
ms.openlocfilehash: b07e850810734082568ddca9776a72575c986094
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837555"
---
# <a name="using-tracking-to-troubleshoot-applications"></a>Řešení problémů s aplikací pomocí sledování
Programovací model Windows Workflow Foundation (WF) umožňuje sledovat informace související s pracovním postupem a poskytnout tak podrobné informace o spuštění programovací model Windows Workflow Foundation aplikace nebo služby. Programovací model Windows Workflow Foundation hostitelé můžou zachytit události pracovního postupu během provádění instance pracovního postupu. Pokud váš pracovní postup generuje chyby nebo výjimky, můžete použít informace o sledování programovací model Windows Workflow Foundation k řešení potíží se zpracováním.  
  
## <a name="troubleshooting-a-wf-using-wf-tracking"></a>Řešení potíží s WF pomocí sledování WF  
 Chcete-li zjistit chyby v rámci zpracování aktivity programovací model Windows Workflow Foundation, můžete povolit sledování pomocí sledovacího profilu, který se dotazuje na <xref:System.Activities.Tracking.ActivityStateRecord> se stavem Chyba. Odpovídající dotaz je uveden v následujícím kódu.  
  
```xml  
<activityStateQueries>  
              <activityStateQuery activityName="*">  
                <states>  
                  <state name="Faulted" />  
                </states>  
              </activityStateQuery>  
 </activityStateQueries>  
```  
  
 Pokud je chyba šířena a zpracována v obslužné rutině selhání (například aktivita <xref:System.Activities.Statements.TryCatch>), lze ji zjistit pomocí <xref:System.Activities.Tracking.FaultPropagationRecord>. <xref:System.Activities.Tracking.FaultPropagationRecord> označuje zdrojovou aktivitu chyby a název obslužné rutiny chyb. <xref:System.Activities.Tracking.FaultPropagationRecord> obsahuje podrobnosti o chybě ve formě zásobníku výjimek pro chybu. V následujícím příkladu se zobrazí dotaz pro přihlášení k odběru <xref:System.Activities.Tracking.FaultPropagationRecord>.  
  
```xml  
<faultPropagationQueries>  
              <faultPropagationQuery faultSourceActivityName ="*" faultHandlerActivityName="*"/>  
 </faultPropagationQueries>  
```  
  
 Pokud chyba není zpracována v pracovním postupu, výsledkem je Neošetřená výjimka instance pracovního postupu a instance pracovního postupu byla přerušena. Pro pochopení podrobností o neošetřené výjimce musí profil sledování zadat dotaz na záznam instance pracovního postupu s `state name="UnhandledException"`, jak je uvedeno v následujícím příkladu.  
  
```xml  
<workflowInstanceQueries>  
              <workflowInstanceQuery>  
                <states>  
                  <state name="UnhandledException" />  
                </states>  
              </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
 Když instance pracovního postupu narazí na neošetřenou výjimku, vygeneruje se <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord> objekt, pokud je povolené sledování programovací model Windows Workflow Foundation.  
  
 Tento záznam sledování obsahuje podrobnosti o chybě ve formě zásobníku výjimek. Obsahuje podrobnosti o zdroji chyby (například aktivity), která byla způsobena chybou a vznikla v neošetřené výjimce. Chcete-li se přihlásit k odběru událostí selhání z programovací model Windows Workflow Foundation, povolte sledování přidáním účastníka sledování. Nakonfigurujte tohoto účastníka se sledovacím profilem, který se dotazuje na `ActivityStateQuery (state="Faulted")`, <xref:System.Activities.Tracking.FaultPropagationRecord>a `WorkflowInstanceQuery (state="UnhandledException")`.  
  
 Pokud je povoleno sledování pomocí účastníka sledování ETW, události selhání se generují do relace ETW. Události lze zobrazit pomocí Prohlížeč událostí prohlížeč událostí. Tuto možnost najdete pod uzlem **Prohlížeč událostí > protokoly aplikací a služeb – > Microsoft-> Windows-> aplikační server – aplikace** v analytickém kanálu.  
  
## <a name="see-also"></a>Viz také:

- [Monitorování Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677251(v=azure.10))
- [Monitorování aplikací pomocí prostředků infrastruktury aplikace](https://docs.microsoft.com/previous-versions/appfabric/ee677276(v=azure.10))
