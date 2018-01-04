---
title: "Výjimky"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 065205cc-52dd-4f30-9578-b17d8d113136
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bf2c6e12dac2130a26aa01efc21b8f58f509294a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="exceptions"></a>Výjimky
Pracovní postupy můžete použít <xref:System.Activities.Statements.TryCatch> aktivity zpracování výjimek, které jsou vyvolány během spouštění pracovního postupu. Tyto odchylky mohou být zpracovány nebo se může být znovu vyvolána, pomocí <xref:System.Activities.Statements.Rethrow> aktivity. Aktivity v <xref:System.Activities.Statements.TryCatch.Finally%2A> části jsou spuštěna při buď <xref:System.Activities.Statements.TryCatch.Try%2A> části nebo <xref:System.Activities.Statements.TryCatch.Catches%2A> části dokončení. Pracovní postupy hostované <xref:System.Activities.WorkflowApplication> instance můžete také použít <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> obslužné rutiny události pro zpracování výjimek, které nejsou zpracovávány <xref:System.Activities.Statements.TryCatch> aktivity.  
  
## <a name="causes-of-exceptions"></a>Příčinami výjimek  
 V pracovním postupu mohou být výjimky generovány následujícími způsoby:  
  
-   Časový limit transakcí v <xref:System.Activities.Statements.TransactionScope>.  
  
-   Explicitní výjimka vyvolaná pomocí pracovního postupu <xref:System.Activities.Statements.Throw> aktivity.  
  
-   A [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] došlo k výjimce z aktivity.  
  
-   Výjimka vyvolaná z externí kódu, například knihovny, komponenty nebo služby, které se používají v pracovním postupu.  
  
## <a name="handling-exceptions"></a>Zpracování výjimek  
 Pokud je vyvolána aktivitou a neošetřené výjimka, použije se výchozí chování je ukončení instance pracovního postupu. Pokud vlastní <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> obslužná rutina přítomen, ho můžete přepsat toto výchozí chování. Tato obslužná rutina dává možnost poskytnout příslušné zpracování, například vlastní protokolování, přerušení pracovního postupu, pracovní postup zrušení nebo ukončení pracovního postupu vytvořit hostitele pracovního postupu.  Pokud pracovní postup vyvolá výjimku, která nejsou zpracovávány <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> je volána obslužná rutina. Existují tři možných akcí, kterou vrátil <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> který určit konečný výsledek pracovního postupu.  
  
-   **Zrušit** -instanci zrušené pracovního postupu je řádně ukončení provádění firemní pobočky. Zrušení chování můžete model (například pomocí aktivity CancellationScope). Obslužná rutina dokončeno je vyvolána po dokončení procesu zrušení. Zrušené pracovní postup je ve stavu zrušeno.  
  
-   **Ukončit** -instanci ukončenou pracovního postupu se nedá obnovit nebo restartovat.  Tím se spustí dokončeno událostí, ve kterém můžete zadat výjimku jako důvod, proč byl ukončen. Obslužná rutina ukončeno je vyvolána po dokončení procesu ukončení. Ukončenou pracovní postup je v chybném stavu.  
  
-   **Abort –** -instancí přerušené pracovního postupu můžete obnovit pouze v případě, že byl nakonfigurován jako trvalé.  Bez trvalost nelze pokračovat. pracovní postup.  V bodě pracovní postup byl přerušen, všechny objem práce (v paměti), od vytvoření posledního bodu trvalost budou ztraceny. Pro přerušené pracovní postup je vyvolána obslužná rutina bylo přerušeno. pomocí výjimka jako z důvodu, po dokončení procesu přerušení. Na rozdíl od zrušeno a ukončeno, ale není vyvolána obslužná rutina dokončeno. Přerušené pracovního postupu je ve stavu bylo přerušeno.  
  
 Následující příklad popisuje vyvolání pracovní postup, který vyvolá výjimku. V tomto pracovním postupu je neošetřené výjimky a <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> je volána obslužná rutina. <xref:System.Activities.WorkflowApplicationUnhandledExceptionEventArgs> Jsou prozkoumá a poskytují informace o výjimce, a pracovní postup bude ukončen.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#1](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#1)]  
  
### <a name="handling-exceptions-with-the-trycatch-activity"></a>Zpracování výjimek s TryCatch aktivity  
 Zpracování výjimek v pracovním postupu se provádí pomocí <xref:System.Activities.Statements.TryCatch> aktivity. <xref:System.Activities.Statements.TryCatch> Aktivita má <xref:System.Activities.Statements.TryCatch.Catches%2A> kolekce <xref:System.Activities.Statements.Catch> aktivity, které jsou všechny související s konkrétní <xref:System.Exception> typu. Pokud výjimky vyvolané aktivitu, která je součástí <xref:System.Activities.Statements.TryCatch.Try%2A> části <xref:System.Activities.Statements.TryCatch> aktivity odpovídá výjimku <xref:System.Activities.Statements.Catch%601> aktivity v <xref:System.Activities.Statements.TryCatch.Catches%2A> zpracovává kolekce a potom výjimka. Pokud je explicitně znovu vyvolána výjimka nebo novou výjimku pak tato výjimka předá do nadřazené aktivity. Následující příklad kódu ukazuje <xref:System.Activities.Statements.TryCatch> aktivity, která zpracovává <xref:System.ApplicationException> , je vyvolána <xref:System.Activities.Statements.TryCatch.Try%2A> části podle <xref:System.Activities.Statements.Throw> aktivity. Zpráva výjimky je zapsán do konzoly pomocí <xref:System.Activities.Statements.Catch%601> aktivitu a potom zprávu je zapsán do konzoly v <xref:System.Activities.Statements.TryCatch.Finally%2A> části.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#33](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#33)]  
  
 Aktivity v <xref:System.Activities.Statements.TryCatch.Finally%2A> části jsou spuštěna při buď <xref:System.Activities.Statements.TryCatch.Try%2A> části nebo <xref:System.Activities.Statements.TryCatch.Catches%2A> části úspěšně dokončí. <xref:System.Activities.Statements.TryCatch.Try%2A> Části úspěšně dokončí, pokud žádné výjimky jsou vyvolány z a <xref:System.Activities.Statements.TryCatch.Catches%2A> části úspěšně dokončí, pokud žádné výjimky jsou vyvolány nebo znovu vyvolány z něj. Pokud je vyvolána výjimka <xref:System.Activities.Statements.TryCatch.Try%2A> části <xref:System.Activities.Statements.TryCatch> a není buď zpracovává <xref:System.Activities.Statements.Catch%601> v <xref:System.Activities.Statements.TryCatch.Catches%2A> části nebo je znovu vyvolány z <xref:System.Activities.Statements.TryCatch.Catches%2A>, aktivity v <xref:System.Activities.Statements.TryCatch.Finally%2A> nebude možné provést, dokud nenastane některá z následujících akcí.  
  
-   Výjimka je zachytila na vyšší úrovni <xref:System.Activities.Statements.TryCatch> aktivity v pracovním postupu, bez ohledu na to, jestli je vyvolány z této vyšší úrovni <xref:System.Activities.Statements.TryCatch>.  
  
-   Výjimka není zpracováván na vyšší úrovni <xref:System.Activities.Statements.TryCatch>, řídicí sekvence kořenu pracovního postupu a pracovní postup je nakonfigurovaný zrušit místo provedení příkazu ukončit nebo přerušení. Pracovní postupy, které jsou hostované pomocí <xref:System.Activities.WorkflowApplication> to můžete nakonfigurovat zpracování <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> a vrátí <xref:System.Activities.UnhandledExceptionAction.Cancel>. Příkladem zpracování <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> je uvedené dříve v tomto tématu. Služby pracovních postupů to můžete nakonfigurovat pomocí <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> a zadání <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction.Cancel>. Příklad konfigurace <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>, najdete v části [rozšíření hostitele služby pracovního postupu](../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md).  
  
## <a name="exception-handling-versus-compensation"></a>Porovnání kompenzace zpracování výjimek  
 Rozdíl mezi výjimek a kompenzace je, že při provádění aktivity k výjimek. Kompenzace nastane po úspěšném dokončení aktivity. Zpracovávání výjimek v jazyce poskytuje možnost Vyčištění po aktivity vyvolá výjimku, zatímco kompenzace poskytuje mechanismus, pomocí kterého lze úspěšně dokončila práci při dříve dokončené aktivity vrátit zpět. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Kompenzace](../../../docs/framework/windows-workflow-foundation/compensation.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Activities.Statements.TryCatch>  
 <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>  
 <xref:System.Activities.Statements.CompensableActivity>
