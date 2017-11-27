---
title: "Řešení potíží s aplikací pomocí sledování"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8851adde-c3c2-4391-9523-d8eb831490af
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 02c6d346c6ebea27148c11f5f033f74dfb556e44
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="using-tracking-to-troubleshoot-applications"></a>Řešení potíží s aplikací pomocí sledování
[!INCLUDE[wf](../../../includes/wf-md.md)]umožňuje sledovat informace týkající se pracovní postup uvést podrobnosti do provádění [!INCLUDE[wf2](../../../includes/wf2-md.md)] aplikaci nebo službě. [!INCLUDE[wf2](../../../includes/wf2-md.md)]hostitelé dokážou zachytit pracovního postupu události během zpracování instance pracovního postupu. Pokud pracovní postup generuje chyby nebo výjimky, můžete použít [!INCLUDE[wf2](../../../includes/wf2-md.md)] sledování podrobnosti o řešení problémů s jeho zpracování.  
  
## <a name="troubleshooting-a-wf-using-wf-tracking"></a>Řešení potíží WF pomocí sledování WF  
 Ke zjištění chyb v rámci zpracování [!INCLUDE[wf2](../../../includes/wf2-md.md)] aktivita, můžete povolit sledování s sledování profil, který se dotazuje na <xref:System.Activities.Tracking.ActivityStateRecord> v chybném stavu. Odpovídající dotaz je zadána v následujícím kódu.  
  
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
  
 Když dojde k neošetřené výjimce instanci pracovního postupu <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord> objektu je vygenerované Pokud [!INCLUDE[wf2](../../../includes/wf2-md.md)] bylo povoleno sledování.  
  
 Tento záznam sledování obsahuje v podrobnostech o chybě ve formě zásobník výjimek. Obsahuje podrobnosti o zdroj selhání (například aktivita), který došlo k chybě a výsledkem neošetřených výjimek. Přihlásit k odběru událostí selhání z [!INCLUDE[wf2](../../../includes/wf2-md.md)], povolit sledování přidáním účastník sledování. Tento účastník nakonfigurovat sledování profil, který se dotazuje na `ActivityStateQuery (state="Faulted")`, <xref:System.Activities.Tracking.FaultPropagationRecord>, a `WorkflowInstanceQuery (state="UnhandledException")`.  
  
 Pokud je povoleno sledování pomocí účastník sledování trasování událostí pro Windows, jsou události chyby vygenerované relaci trasování událostí pro Windows. Události lze zobrazit pomocí prohlížeče událostí Prohlížeč událostí. To lze nalézt v uzlu **Prohlížeč událostí -> aplikace a protokoly služby -> Microsoft -> Windows -> serveru aplikace – aplikace** v analytické kanál.  
  
## <a name="see-also"></a>Viz také  
 [Windows Server App Fabric monitorování](http://go.microsoft.com/fwlink/?LinkId=201273)  
 [Monitorování aplikací pomocí App Fabric](http://go.microsoft.com/fwlink/?LinkId=201275)
