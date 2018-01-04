---
title: "Trvalost účastníky"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f84d2d5d-1c1b-4f19-be45-65b552d3e9e3
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5b85acf2e3c4d885988e92948481182b7cf8c32c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="persistence-participants"></a>Trvalost účastníky
Trvalost účastník účastnit aktivovány hostitele aplikace operaci trvalost (Uložit nebo zatížení). [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] Se dodává s dvěma abstraktní třídy **PersistenceParticipant** a **PersistenceIOParticipant**, který můžete použít k vytvoření účastník trvalost. Trvalost účastník je odvozena z jedné z těchto tříd, implementuje metody, které vás zajímají a potom přidá instanci třídy, která má <xref:System.ServiceModel.Activities.WorkflowServiceHost.WorkflowExtensions%2A> kolekce na <xref:System.ServiceModel.Activities.WorkflowServiceHost> . Hostitele aplikací může vyhledávat taková rozšíření pracovního postupu při zachování instanci pracovního postupu a volat metody odpovídající na účastníků trvalost v příslušnou dobu.  
  
 Následující seznam popisuje úlohy prováděné subsystémem trvalost v různých fázích operace zachovat (Uložit). Trvalost účastníků se používají ve třetí a čtvrté fáze. Pokud účastník účastníka vstupně-výstupní operace (trvalost účastník, který je také součástí operací v/v), se také používá účastník ve fázi šesté.  
  
1.  Shromažďuje předdefinované hodnoty, včetně stavu pracovního postupu, záložky, namapované proměnné a časové razítko.  
  
2.  Shromažďuje všechny účastníky trvalost, které byly přidány do rozšíření kolekce přidružené k instanci pracovního postupu.  
  
3.  Vyvolá <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A> metoda implementované všechny účastníky trvalost.  
  
4.  Vyvolá <xref:System.Activities.Persistence.PersistenceParticipant.MapValues%2A> metoda implementované všechny účastníky trvalost.  
  
5.  Zachovat nebo uložit do úložiště trvalosti pracovního postupu.  
  
6.  Vyvolá <xref:System.Activities.Persistence.PersistenceIOParticipant.BeginOnSave%2A> metodu všichni účastníci trvalost vstupně-výstupní operace. Pokud účastník není účastníka vstupně-výstupní operace, je tato úloha přeskočena. Pokud díl trvalost transakcí, transakce je součástí Transaction.Current vlastnost.  
  
7.  Čeká se na všechny účastníky trvalosti pro dokončení. Pokud všichni účastníci úspěšné v zachování data instance, potvrdí transakce.  
  
 Trvalost účastník, který je odvozen od **PersistenceParticipant** třídy a může implementovat **CollectValues** a **MapValues** metody. Vstupně-výstupní operace účastník trvalost je odvozena z **PersistenceIOParticipant** třídy a může implementovat **BeginOnSave** metoda kromě implementace **CollectValues**a **MapValues** metody.  
  
 Každá fáze byla dokončena, než začne další fáze. Například hodnoty se shromažďují z **všechny** trvalost účastníky v první fázi. Potom všechny hodnoty shromažďované v první fázi jsou k dispozici pro všechny účastníky trvalost ve druhé fázi pro mapování. Potom všechny hodnoty shromážděných a namapovat v prvním a druhém fázích poskytované poskytovateli trvalost třetí fází a tak dále.  
  
 Následující seznam popisuje úlohy prováděné subsystémem trvalost v různých fázích operace načtení. Trvalost účastníků se používají v čtvrté fáze. Trvalost účastníků vstupně-výstupní operace (trvalost účastníci, které jsou také součástí vstupně-výstupní operace) se také používají v třetí fází.  
  
1.  Shromažďuje všechny účastníky trvalost, které byly přidány do rozšíření kolekce přidružené k instanci pracovního postupu.  
  
2.  Načte pracovního postupu z obchodu trvalost.  
  
3.  Vyvolá <xref:System.Activities.Persistence.PersistenceIOParticipant.BeginOnLoad%2A> na všech trvalost vstupně-výstupní operace účastníci a čeká pro všechny účastníky trvalosti pro dokončení. Pokud je transakční díl trvalost, transakce je součástí Transaction.Current.  
  
4.  Načte instanci pracovního postupu v paměti na základě dat načíst z úložiště trvalosti.  
  
5.  Vyvolá <xref:System.Activities.Persistence.PersistenceParticipant.PublishValues%2A> na každý účastník trvalost.  
  
 Trvalost účastník, který je odvozen od **PersistenceParticipant** třídy a může implementovat **PublishValues** metoda. Vstupně-výstupní operace účastník trvalost je odvozena z **PersistenceIOParticipant** třídy a může implementovat **BeginOnLoad** metoda kromě implementace **PublishValues**metoda.  
  
 Při načítání instance pracovního postupu vytvoří poskytovatel trvalost zámek na tuto instanci. To zabrání instance načtení ve více než jednomu hostiteli ve scénáři s více uzly. Pokud pokus o načtení instance pracovního postupu, který byl uzamčen uvidíte výjimku takto: výjimka "System.ServiceModel.Persistence.InstanceLockException: Požadovaná operace nebyla dokončena, protože zámek pro instanci. 00000000-0000-0000-0000-000000000000 se nepodařilo získat ". K této chybě dojde, pokud dojde k jedné z následujících akcí:  
  
-   V případě několika uzly k instanci načítá jiného hostitele.  Existuje několik různých způsobů řešení konfliktů tyto typy: předávání zpracování na uzlu, který vlastní zámek a zkuste to znovu, nebo vynuťte zatížení, které způsobí, že nebude možné všechnu práci uložit hostitele.  
  
-   V případě jedním uzlem a hostiteli došlo k chybě.  Po spuštění hostitele znovu (recyklace procesu nebo vytvořit nový objekt factory zprostředkovatele trvalost) na nového hostitele pokusí načíst instanci, která je stále uzamčen staré hostitelem, protože zámek ještě nevypršela.  
  
-   V případě jedním uzlem a instance dotyčném bylo přerušeno v určitém okamžiku a je vytvořena nová instance zprostředkovatele trvalost, jehož ID jiné hostitele.  
  
 Hodnota časového limitu zámku má výchozí hodnotu 5 minut, můžete zadat hodnotu jiný časový limit při volání metody <xref:System.ServiceModel.Persistence.PersistenceProvider.Load%2A>.  
  
## <a name="in-this-section"></a>V tomto oddílu  
  
-   [Postupy: Vytvoření vlastního účastníka trvalosti](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-persistence-participant.md)  
  
## <a name="see-also"></a>Viz také  
 [Rozšiřitelnost úložiště](../../../docs/framework/windows-workflow-foundation/store-extensibility.md)
