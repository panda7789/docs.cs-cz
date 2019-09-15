---
title: Řešení problémů s aplikací pomocí sledování
ms.date: 03/30/2017
ms.assetid: 8851adde-c3c2-4391-9523-d8eb831490af
ms.openlocfilehash: b64b92de9cb36807a2bf1eb7ff57f9f6e1a07156
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70988937"
---
# <a name="using-tracking-to-troubleshoot-applications"></a>Řešení problémů s aplikací pomocí sledování
Programovací model Windows Workflow Foundation (WF) umožňuje sledovat informace související s pracovním postupem a poskytnout tak podrobné informace o spuštění programovací model Windows Workflow Foundation aplikace nebo služby. Programovací model Windows Workflow Foundation hostitelé můžou zachytit události pracovního postupu během provádění instance pracovního postupu. Pokud váš pracovní postup generuje chyby nebo výjimky, můžete použít informace o sledování programovací model Windows Workflow Foundation k řešení potíží se zpracováním.  
  
## <a name="troubleshooting-a-wf-using-wf-tracking"></a>Řešení potíží s WF pomocí sledování WF  
 Chcete-li zjistit chyby v rámci zpracování aktivity programovací model Windows Workflow Foundation, můžete povolit sledování pomocí sledovacího profilu, který <xref:System.Activities.Tracking.ActivityStateRecord> se dotazuje pro stav s chybou. Odpovídající dotaz je uveden v následujícím kódu.  
  
```xml  
<activityStateQueries>  
              <activityStateQuery activityName="*">  
                <states>  
                  <state name="Faulted" />  
                </states>  
              </activityStateQuery>  
 </activityStateQueries>  
```  
  
 Pokud je chyba šířena a zpracována v obslužné rutině chyby (například <xref:System.Activities.Statements.TryCatch> aktivita), lze ji zjistit <xref:System.Activities.Tracking.FaultPropagationRecord>pomocí. <xref:System.Activities.Tracking.FaultPropagationRecord> Určuje zdrojovou aktivitu chyby a název obslužné rutiny chyby. <xref:System.Activities.Tracking.FaultPropagationRecord> Obsahuje podrobnosti o chybě ve formě zásobníku výjimek pro chybu. V následujícím příkladu se zobrazí dotaz <xref:System.Activities.Tracking.FaultPropagationRecord> pro přihlášení k odběru.  
  
```xml  
<faultPropagationQueries>  
              <faultPropagationQuery faultSourceActivityName ="*" faultHandlerActivityName="*"/>  
 </faultPropagationQueries>  
```  
  
 Pokud chyba není zpracována v pracovním postupu, výsledkem je Neošetřená výjimka instance pracovního postupu a instance pracovního postupu byla přerušena. Pro pochopení podrobností o neošetřené výjimce musí profil sledování zadat dotaz na záznam `state name="UnhandledException"` instance pracovního postupu, jak je uvedeno v následujícím příkladu.  
  
```xml  
<workflowInstanceQueries>  
              <workflowInstanceQuery>  
                <states>  
                  <state name="UnhandledException" />  
                </states>  
              </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
 Když instance pracovního postupu nalezne neošetřenou výjimku, <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord> objekt se vygeneruje, pokud je povolené sledování programovací model Windows Workflow Foundation.  
  
 Tento záznam sledování obsahuje podrobnosti o chybě ve formě zásobníku výjimek. Obsahuje podrobnosti o zdroji chyby (například aktivity), která byla způsobena chybou a vznikla v neošetřené výjimce. Chcete-li se přihlásit k odběru událostí selhání z programovací model Windows Workflow Foundation, povolte sledování přidáním účastníka sledování. Nakonfigurujte tohoto účastníka se sledovacím profilem, `ActivityStateQuery (state="Faulted")`který <xref:System.Activities.Tracking.FaultPropagationRecord>se dotazuje na, a `WorkflowInstanceQuery (state="UnhandledException")`.  
  
 Pokud je povoleno sledování pomocí účastníka sledování ETW, události selhání se generují do relace ETW. Události lze zobrazit pomocí Prohlížeč událostí prohlížeč událostí. Tuto možnost najdete pod uzlem **Prohlížeč událostí > protokoly aplikací a služeb – > Microsoft-> Windows-> aplikační server – aplikace** v analytickém kanálu.  
  
## <a name="see-also"></a>Viz také:

- [Monitorování Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkId=201273)
- [Monitorování aplikací pomocí prostředků infrastruktury aplikace](https://go.microsoft.com/fwlink/?LinkId=201275)
