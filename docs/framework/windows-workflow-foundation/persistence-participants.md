---
title: Účastníci trvalosti
ms.date: 03/30/2017
ms.assetid: f84d2d5d-1c1b-4f19-be45-65b552d3e9e3
ms.openlocfilehash: 18614962708eafa192d8163638fce2b8154d6106
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59316359"
---
# <a name="persistence-participants"></a>Účastníci trvalosti
Trvalého účastníka mohou účastnit aktivuje hostitele aplikace operace trvalosti (Uložit nebo načíst). [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] Se dodává se dvěma abstraktní třídy **PersistenceParticipant** a **PersistenceIOParticipant**, který můžete použít k vytvoření trvalého účastníka. Trvalého účastníka je odvozena z jedné z těchto tříd, implementuje metody, které vás zajímají a pak přidá instanci třídy, která se <xref:System.ServiceModel.Activities.WorkflowServiceHost.WorkflowExtensions%2A> kolekce na <xref:System.ServiceModel.Activities.WorkflowServiceHost> . Hostitel aplikace může vyhledat taková rozšíření pracovního postupu při trvalém ukládání instance pracovního postupu a volat metody odpovídající na účastníci trvalosti ve vhodných chvílích.  
  
 Následující seznam popisuje úlohy prováděné subsystému přetrvávání v různých fázích operace trvalého (Uložit). Účastníci trvalosti se používají ve třetím a čtvrtém fázích. Pokud účastník účastníkovi vstupně-výstupních operací (trvalého účastníka, který je také součástí vstupně-výstupní operace), účastníka se používá také ve fázi šesté.  
  
1. Shromažďuje předdefinované hodnoty, včetně stavu pracovního postupu, záložek, proměnné pro mapovanou a časové razítko.  
  
2. Shromažďuje všichni účastníci trvalosti, které byly přidány do kolekci rozšíření asociovanou s instancí pracovního postupu.  
  
3. Vyvolá <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A> metoda implementovaná všichni účastníci trvalosti.  
  
4. Vyvolá <xref:System.Activities.Persistence.PersistenceParticipant.MapValues%2A> metoda implementovaná všichni účastníci trvalosti.  
  
5. Zachovat nebo uložit pracovní postup do trvalého úložiště.  
  
6. Vyvolá <xref:System.Activities.Persistence.PersistenceIOParticipant.BeginOnSave%2A> metodu na všichni účastníci trvalosti vstupně-výstupních operací. Pokud účastník není účastníkovi vstupně-výstupních operací, tato úloha se přeskočí. Pokud je transakční epizodě trvalost, transakce je k dispozici ve vlastnosti Transaction.Current.  
  
7. Čeká, až všichni účastníci trvalosti pro dokončení. Pokud všichni účastníci trvalá data instance, potvrzení transakce.  
  
 Je odvozen od trvalého účastníka **PersistenceParticipant** třídy a může implementovat **CollectValues** a **MapValues** metody. Účastníka trvalosti vstupně-výstupních operací je odvozen od **PersistenceIOParticipant** třídy a může implementovat **BeginOnSave** metoda kromě provádění **CollectValues**a **MapValues** metody.  
  
 Každá fáze je dokončit, než začne další fáze. Například hodnoty jsou shromažďovány z **všechny** účastníci trvalosti v první fázi. Potom všechny hodnoty, které jsou shromážděné v první fázi jsou k dispozici všichni účastníci trvalosti ve druhé fázi pro mapování. Potom všechny hodnoty shromažďují a mapována v prvním a druhém fáze jsou k dispozici pro poskytovatele trvalého chování ve fázi třetí a tak dále.  
  
 Následující seznam popisuje úlohy prováděné subsystému přetrvávání v různých fázích operace načtení. Ve čtvrté fáze se používají účastníci trvalosti. Účastníci trvalosti vstupně-výstupních operací (účastníci trvalosti, které jsou také součástí vstupně-výstupních operací) se také používají ve třetí fázi.  
  
1. Shromažďuje všichni účastníci trvalosti, které byly přidány do kolekci rozšíření asociovanou s instancí pracovního postupu.  
  
2. Načte pracovní postup z trvalého úložiště.  
  
3. Vyvolá <xref:System.Activities.Persistence.PersistenceIOParticipant.BeginOnLoad%2A> na všech účastníci trvalosti vstupně-výstupní operace a čeká na všichni účastníci trvalosti pro dokončení. Pokud je transakční epizodě trvalost, transakce je k dispozici v Transaction.Current.  
  
4. Načte instanci pracovního postupu v paměti na základě dat načíst z trvalého úložiště.  
  
5. Vyvolá <xref:System.Activities.Persistence.PersistenceParticipant.PublishValues%2A> na každý trvalého účastníka.  
  
 Je odvozen od trvalého účastníka **PersistenceParticipant** třídy a může implementovat **PublishValues** metoda. Účastníka trvalosti vstupně-výstupních operací je odvozen od **PersistenceIOParticipant** třídy a může implementovat **BeginOnLoad** metoda kromě provádění **PublishValues**metody.  
  
 Při načítání instance pracovního postupu vytvoří poskytovatele trvalého chování zámku na tuto instanci. To zabrání tomu, aby instance načtení více než jeden hostitel ve scénáři více uzly. Při pokusu o načtení instance pracovního postupu, který je pevně spojené se zobrazí výjimku vypadat asi takto: Výjimka "System.ServiceModel.Persistence.InstanceLockException: Požadovaná operace nebyla dokončena, protože zámek pro instanci "00000000-0000-0000-0000-000000000000' nebylo možné získat". K této chybě dojde, pokud dojde k jedné z následujících akcí:  
  
-   V případě několika uzly v instanci načítá jiného hostitele.  Existuje několik různých způsobů, jak vyřešit tyto typy konfliktů: předávání zpracování na uzel, který vlastní zámek a zkuste to znovu, nebo vynuťte zatížení, což způsobí, že hostitel nebude možné práci uložit.  
  
-   V případě jedním uzlem a hostiteli došlo k chybě.  Při spuštění hostitele znovu (recyklace procesu nebo vytvořením nové továrny poskytovatele trvalosti) nového hostitele se pokusí načíst instanci, která je stále zamknuta staré hostitelem, protože nebyla dosud vypršela platnost zámku.  
  
-   V případě jedním uzlem a instanci dotyčný bylo přerušeno v určitém okamžiku a je vytvořena nová instance poskytovatele trvalosti, která má ID jiného hostitele.  
  
 Hodnota časového limitu zámku má výchozí hodnotu 5 minut, můžete zadat jiný časový limit při volání metody <xref:System.ServiceModel.Persistence.PersistenceProvider.Load%2A>.  
  
## <a name="in-this-section"></a>V tomto oddílu  
  
-   [Postupy: Vytvoření vlastního účastníka trvalosti](how-to-create-a-custom-persistence-participant.md)  
  
## <a name="see-also"></a>Viz také:

- [Rozšiřitelnost úložiště](store-extensibility.md)
