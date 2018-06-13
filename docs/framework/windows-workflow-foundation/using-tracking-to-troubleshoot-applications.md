---
title: Řešení potíží s aplikací pomocí sledování
ms.date: 03/30/2017
ms.assetid: 8851adde-c3c2-4391-9523-d8eb831490af
ms.openlocfilehash: ee9aaaae80f213f026a222ac1754ae8b4fdf2d37
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33517040"
---
# <a name="using-tracking-to-troubleshoot-applications"></a>Řešení potíží s aplikací pomocí sledování
Windows Workflow Foundation (WF) umožňuje sledovat informace týkající se pracovní postup uvést podrobnosti do spuštění aplikace Windows Workflow Foundation nebo služby. K zachycení událostí pracovního postupu během zpracování instance pracovního postupu dokážou hostitele Windows Workflow Foundation. Pokud pracovní postup generuje chyby nebo výjimky, můžete použít sledování podrobnosti o řešení problémů s jeho zpracování modelu Windows Workflow Foundation.  
  
## <a name="troubleshooting-a-wf-using-wf-tracking"></a>Řešení potíží WF pomocí sledování WF  
 Ke zjištění chyb v rámci zpracování aktivity modelu Windows Workflow Foundation, můžete povolit sledování s sledování profil, který se dotazuje na <xref:System.Activities.Tracking.ActivityStateRecord> v chybném stavu. Odpovídající dotaz je zadána v následujícím kódu.  
  
```xml  
<activityStateQueries>  
              <activityStateQuery activityName="*">  
                <states>  
                  <state name="Faulted" />  
                </states>  
              </activityStateQuery>  
 </activityStateQueries>  
```  
  
 Pokud je chybu rozšířen a zpracovávaných v rámci obslužná rutina chyb (například <xref:System.Activities.Statements.TryCatch> aktivity) to lze zjistit pomocí <xref:System.Activities.Tracking.FaultPropagationRecord>. <xref:System.Activities.Tracking.FaultPropagationRecord> Označuje zdrojové aktivity poruchy a název obslužné rutiny selhání. <xref:System.Activities.Tracking.FaultPropagationRecord> Obsahuje podrobné informace o chybě v podobě zásobník výjimek poruchy. Dotaz pro přihlášení k odběru pro <xref:System.Activities.Tracking.FaultPropagationRecord> je znázorněno v následujícím příkladu.  
  
```xml  
<faultPropagationQueries>  
              <faultPropagationQuery faultSourceActivityName ="*" faultHandlerActivityName="*"/>  
 </faultPropagationQueries>  
```  
  
 Pokud není chybu zpracovávaných v rámci pracovního postupu, který je výsledkem k neošetřené výjimce v instanci pracovního postupu a instance pracovního postupu byla přerušena. Profil sledování musí zjistit podrobnosti o neošetřené výjimce dotaz na záznam instance pracovního postupu s `state name="UnhandledException"` jak je uvedeno v následujícím příkladu.  
  
```xml  
<workflowInstanceQueries>  
              <workflowInstanceQuery>  
                <states>  
                  <state name="UnhandledException" />  
                </states>  
              </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
 Když dojde k neošetřené výjimce instanci pracovního postupu <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord> objektu je vygenerované, pokud bylo povoleno sledování modelu Windows Workflow Foundation.  
  
 Tento záznam sledování obsahuje v podrobnostech o chybě ve formě zásobník výjimek. Obsahuje podrobnosti o zdroj selhání (například aktivita), který došlo k chybě a výsledkem neošetřených výjimek. K odběru události chyby z Windows Workflow Foundation, povolte sledování přidáním účastník sledování. Tento účastník nakonfigurovat sledování profil, který se dotazuje na `ActivityStateQuery (state="Faulted")`, <xref:System.Activities.Tracking.FaultPropagationRecord>, a `WorkflowInstanceQuery (state="UnhandledException")`.  
  
 Pokud je povoleno sledování pomocí účastník sledování trasování událostí pro Windows, jsou události chyby vygenerované relaci trasování událostí pro Windows. Události lze zobrazit pomocí prohlížeče událostí Prohlížeč událostí. To lze nalézt v uzlu **Prohlížeč událostí -> aplikace a protokoly služby -> Microsoft -> Windows -> serveru aplikace – aplikace** v analytické kanál.  
  
## <a name="see-also"></a>Viz také  
 [Windows Server App Fabric monitorování](http://go.microsoft.com/fwlink/?LinkId=201273)  
 [Monitorování aplikací pomocí App Fabric](http://go.microsoft.com/fwlink/?LinkId=201275)
