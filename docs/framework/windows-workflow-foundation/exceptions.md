---
title: Výjimky
ms.date: 03/30/2017
ms.assetid: 065205cc-52dd-4f30-9578-b17d8d113136
ms.openlocfilehash: 64a8338133c265ee1b4c7acbd9b4d168318b66a5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59145987"
---
# <a name="exceptions"></a>Výjimky
Pracovní postupy můžete použít <xref:System.Activities.Statements.TryCatch> aktivity pro zpracování výjimek, které jsou aktivovány v průběhu provádění pracovního postupu. Tyto výjimky mohou být zpracovány nebo se může být znovu vyvolány při použití <xref:System.Activities.Statements.Rethrow> aktivity. Aktivity ve službě <xref:System.Activities.Statements.TryCatch.Finally%2A> oddílu jsou spuštěna při buď <xref:System.Activities.Statements.TryCatch.Try%2A> části nebo <xref:System.Activities.Statements.TryCatch.Catches%2A> části dokončí. Hostitelem pracovních postupů <xref:System.Activities.WorkflowApplication> instance můžete použít také <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> obslužnou rutinu události pro zpracování výjimek, které nejsou zpracovány <xref:System.Activities.Statements.TryCatch> aktivity.  
  
## <a name="causes-of-exceptions"></a>Příčinami výjimek  
 V pracovním postupu mohou být generovány výjimky následujícími způsoby:  
  
-   Časový limit transakcí v <xref:System.Activities.Statements.TransactionScope>.  
  
-   Explicitní výjimka vyvolaná pomocí pracovního postupu <xref:System.Activities.Statements.Throw> aktivity.  
  
-   A [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] z aktivity došlo k výjimce.  
  
-   Výjimka vyvolaná z externího kódu, jako jsou knihovny, komponenty nebo služby, které se používají v pracovním postupu.  
  
## <a name="handling-exceptions"></a>Zpracování výjimek  
 Pokud je vyvolána aktivitou a neošetřená výjimka, je výchozí chování k ukončení instance pracovního postupu. Pokud vlastní <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> obslužná rutina je k dispozici, jej můžete přepsat toto výchozí chování. Tato obslužná rutina poskytuje možnost poskytnout příslušné zpracování, jako jsou vlastní protokolování, přerušení pracovního postupu, zrušení pracovního postupu nebo ukončení pracovního postupu Autor hostitele pracovního postupu.  Pokud pracovní postup vyvolá výjimku, která není zpracována, <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> je vyvolána obslužná rutina. Existují tři možné akce vrácená <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> který určení konečný výsledek pracovního postupu.  
  
-   **Zrušit** – instance pracovního postupu bylo zrušeno je bezproblémové ukončit provádění větve. Zrušení chování lze modelovat (například pomocí aktivity CancellationScope). Po dokončení procesu zrušení, je vyvolána obslužná rutina dokončeno. Zrušené pracovní postup je ve stavu zrušeno.  
  
-   **Ukončit** – instance ukončení pracovního postupu se nedá obnovit nebo restartovat.  Tím se aktivuje událost dokončení, ve kterém můžete zadat výjimku jako z důvodů, proč byl ukončen. Po dokončení procesu ukončení, je vyvolána obslužná rutina ukončeno. Ukončené pracovní postup je v chybovém stavu.  
  
-   **Přerušit** – instance pracovního postupu byl přerušen lze obnovit pouze v případě, že je nakonfigurovaný jako trvalé.  Bez trvalost nelze obnovit pracovního postupu.  V okamžiku, pracovní postup byl přerušen, veškeré akce provedené (v paměti) od posledního trvalého bodu budou ztraceny. Přerušené pracovní postup je vyvolána obslužná rutina přerušeno, pomocí výjimku jako z důvodu po dokončení procesu přerušení. Na rozdíl od zrušeno a ukončeno, ale není vyvolána obslužná rutina dokončeno. Přerušené pracovní postup je ve stavu přerušeno.  
  
 Následující příklad vyvolá pracovní postup, který vyvolá výjimku. Není výjimka ošetřena tímto pracovním postupem a <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> je vyvolána obslužná rutina. <xref:System.Activities.WorkflowApplicationUnhandledExceptionEventArgs> Jsou kontrolovány k poskytnutí informací o výjimce, a pracovní postup se ukončí.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#1](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#1)]  
  
### <a name="handling-exceptions-with-the-trycatch-activity"></a>Zpracování výjimek s aktivitou TryCatch  
 Zpracování výjimek v pracovním postupu pomocí provádí <xref:System.Activities.Statements.TryCatch> aktivity. <xref:System.Activities.Statements.TryCatch> Má aktivita <xref:System.Activities.Statements.TryCatch.Catches%2A> kolekce <xref:System.Activities.Statements.Catch> aktivity, které jsou spojené s konkrétním <xref:System.Exception> typu. Pokud výjimky vyvolané aktivitou, která je součástí <xref:System.Activities.Statements.TryCatch.Try%2A> část <xref:System.Activities.Statements.TryCatch> aktivity shoduje s výjimkou <xref:System.Activities.Statements.Catch%601> aktivity v <xref:System.Activities.Statements.TryCatch.Catches%2A> kolekce a pak výjimka je zpracována. Pokud je explicitně znovu vyvolána výjimka nebo vyvolána nová výjimka pak tato výjimka předá Nadřazená aktivita. Následující příklad kódu ukazuje <xref:System.Activities.Statements.TryCatch> aktivitu, která zpracovává <xref:System.ApplicationException> , která je vyvolána <xref:System.Activities.Statements.TryCatch.Try%2A> části podle <xref:System.Activities.Statements.Throw> aktivity. Zpráva výjimky je zapsána do konzole <xref:System.Activities.Statements.Catch%601> aktivitu a pak napište zprávu, je zapsán v konzole <xref:System.Activities.Statements.TryCatch.Finally%2A> oddílu.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#33](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#33)]  
  
 Aktivity v <xref:System.Activities.Statements.TryCatch.Finally%2A> oddílu jsou spuštěna při buď <xref:System.Activities.Statements.TryCatch.Try%2A> části nebo <xref:System.Activities.Statements.TryCatch.Catches%2A> části úspěšně dokončí. <xref:System.Activities.Statements.TryCatch.Try%2A> Části úspěšně dokončí, pokud nejsou vyvolány žádné výjimky z něj a <xref:System.Activities.Statements.TryCatch.Catches%2A> části úspěšně dokončí, pokud žádné výjimky jsou vyvolány nebo znovu vyvolány z něj. Pokud dojde k výjimce <xref:System.Activities.Statements.TryCatch.Try%2A> část <xref:System.Activities.Statements.TryCatch> a není buď zpracována <xref:System.Activities.Statements.Catch%601> v <xref:System.Activities.Statements.TryCatch.Catches%2A> části nebo je znovu vyvolána z <xref:System.Activities.Statements.TryCatch.Catches%2A>, aktivity v <xref:System.Activities.Statements.TryCatch.Finally%2A> nebude provedena, pokud dojde k jedné z následujících akcí.  
  
-   Výjimka je zachycena ve vyšší úrovni <xref:System.Activities.Statements.TryCatch> aktivity v pracovním postupu, bez ohledu na to, zda se je znovu vyvolána z tuto vyšší úroveň <xref:System.Activities.Statements.TryCatch>.  
  
-   Tato výjimka není ošetřena ve vyšší úrovni <xref:System.Activities.Statements.TryCatch>, řídící kořenového pracovního postupu a pracovní postup nastaven na zrušení namísto ukončit nebo přerušení. Pracovní postupy, které jsou hostované pomocí <xref:System.Activities.WorkflowApplication> to můžete nakonfigurovat pomocí manipulace <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> a vrácení <xref:System.Activities.UnhandledExceptionAction.Cancel>. Příklad zpracování <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> je uvedené dříve v tomto tématu. To služby pracovního postupu můžete nakonfigurovat pomocí <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> uvedete <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction.Cancel>. Příklad konfigurace <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>, naleznete v tématu [rozšíření hostitele služby pracovního postupu](../wcf/feature-details/workflow-service-host-extensibility.md).  
  
## <a name="exception-handling-versus-compensation"></a>Výjimka manipulace a kompenzace  
 Rozdíl mezi zpracování výjimek a kompenzace je, že zpracování výjimek dochází při provádění aktivity. Kompenzace vyvolá se po úspěšném dokončení aktivity. Zpracování výjimek představuje příležitost k vyčištění po aktivita vyvolá výjimku, zatímco poskytuje mechanismus, pomocí kterého lze vrátit zpět úspěšně dokončená práce dříve dokončené aktivity kompenzace. Další informace najdete v tématu [kompenzace](compensation.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Activities.Statements.TryCatch>
- <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>
- <xref:System.Activities.Statements.CompensableActivity>
