---
title: Řešení problémů s aplikací pomocí sledování
ms.date: 03/30/2017
ms.assetid: 8851adde-c3c2-4391-9523-d8eb831490af
ms.openlocfilehash: 62c46ca36c89c023bfc775eb76ba454c9a4162c0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59142061"
---
# <a name="using-tracking-to-troubleshoot-applications"></a>Řešení problémů s aplikací pomocí sledování
Windows Workflow Foundation (WF) umožňuje sledovat související pracovní postup informace, které poskytují podrobnosti do spuštění Windows Workflow Foundation aplikace nebo služby. Hostitele Windows Workflow Foundation je možné ji zachytit události pracovního postupu za běhu instance pracovního postupu. Pokud váš pracovní postup generuje chyby nebo výjimky, můžete použít sledování podrobnosti pro řešení potíží s jeho zpracování modelu Windows Workflow Foundation.  
  
## <a name="troubleshooting-a-wf-using-wf-tracking"></a>Řešení potíží s WF pomocí sledování WF  
 Ke zjištění chyb v rámci zpracování aktivit Windows Workflow Foundation, můžete povolit sledování pomocí sledování profil, který se dotazuje <xref:System.Activities.Tracking.ActivityStateRecord> v chybovém stavu. V následujícím kódu je zadán odpovídající dotaz.  
  
```xml  
<activityStateQueries>  
              <activityStateQuery activityName="*">  
                <states>  
                  <state name="Faulted" />  
                </states>  
              </activityStateQuery>  
 </activityStateQueries>  
```  
  
 Pokud chybu se rozšíří a zpracovávají v rámci obslužné rutiny chyb (například <xref:System.Activities.Statements.TryCatch> aktivity) to lze zjistit pomocí <xref:System.Activities.Tracking.FaultPropagationRecord>. <xref:System.Activities.Tracking.FaultPropagationRecord> Označuje zdrojová aktivita chyby a název obslužné rutiny chyb. <xref:System.Activities.Tracking.FaultPropagationRecord> Obsahuje podrobné informace o chybě v podobě zásobník výjimek pro chybu. Dotaz přihlásit k odběru <xref:System.Activities.Tracking.FaultPropagationRecord> je znázorněno v následujícím příkladu.  
  
```xml  
<faultPropagationQueries>  
              <faultPropagationQuery faultSourceActivityName ="*" faultHandlerActivityName="*"/>  
 </faultPropagationQueries>  
```  
  
 Pokud nezpracovává chybu v rámci pracovního postupu, který je výsledkem neošetřená výjimka v instanci pracovního postupu a instance pracovního postupu byla zrušena. Informace o tom podrobnosti neošetřené výjimky, musí profilu sledování dotáže na záznam instance pracovního postupu s `state name="UnhandledException"` jak je uvedeno v následujícím příkladu.  
  
```xml  
<workflowInstanceQueries>  
              <workflowInstanceQuery>  
                <states>  
                  <state name="UnhandledException" />  
                </states>  
              </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
 Když instance pracovního postupu dojde neošetřené výjimce <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord> objektu je vygenerován, pokud bylo povoleno sledování Windows Workflow Foundation.  
  
 Tento záznam sledování obsahuje podrobné informace o chybě v podobě zásobník výjimek. Obsahuje podrobnosti o zdroj chyby (například aktivita), který s chybou a výsledkem neošetřených výjimek. Přihlásit k odběru selhání události z Windows Workflow Foundation, povolte tak, že přidáte sledování účastník sledování. Nakonfigurovat tímto účastníkem sledování profil, který se dotazuje na `ActivityStateQuery (state="Faulted")`, <xref:System.Activities.Tracking.FaultPropagationRecord>, a `WorkflowInstanceQuery (state="UnhandledException")`.  
  
 Pokud je povolené sledování účastník sledování ETW pomocí selhání události se vysílají do relace trasování událostí pro Windows. Události lze zobrazit pomocí prohlížeče událostí v prohlížeči událostí. To lze nalézt v uzlu **Prohlížeč událostí -> aplikace a služby protokoly -> Microsoft -> Windows -> aplikace Server-** analytického kanálu.  
  
## <a name="see-also"></a>Viz také:

- [Windows Server App Fabric monitorování](https://go.microsoft.com/fwlink/?LinkId=201273)
- [Monitorování aplikací pomocí App Fabric](https://go.microsoft.com/fwlink/?LinkId=201275)
