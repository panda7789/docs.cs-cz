---
title: "Trvalost osvědčené postupy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6974c5a4-1af8-4732-ab53-7d694608a3a0
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 20eb61ef05150b005fb7a3ab25fa21b4e6cd8a8f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="persistence-best-practices"></a>Trvalost osvědčené postupy
Tento dokument popisuje osvědčené postupy pro pracovní postup návrhu a konfigurace související s trvalost pracovního postupu.  
  
## <a name="design-and-implementation-of-durable-workflows"></a>Návrh a implementaci trvanlivý pracovních postupů  
 Obecně platí pracovní postupy práci v krátkém období, která je prokládaný s doby, během kterých je pracovní postup nečinnosti, protože se čeká na událost. Tato událost může být například zpráva nebo jejichž platnost brzy vyprší časovače. Abyste mohli uvolnit k instanci pracovního postupu, když se stane nečinnosti, musí hostitel služby uložit instanci pracovního postupu. To je možné pouze v případě, že se k instanci pracovního postupu není v zóně no-persist (například čeká na dokončení transakce nebo čekání na asynchronní zpětné volání). Povolit instance pracovního postupu nečinnosti se uvolnit, by měl Autor pracovního postupu použijte obory transakce a asynchronní aktivity pro pouze krátkodobou akce. Konkrétně Autor měli mít zpoždění aktivity v rámci těchto zón bez trvalosti co nejkratší.  
  
 Pracovní postup lze zachovat, pouze pokud jsou všechny datové typy používané v tomto pracovním postupu serializable. Kromě toho musí být serializovatelný s vlastní typy používané v pracovních postupech trvalou <xref:System.Runtime.Serialization.NetDataContractSerializer> Chcete-li nastavit jako trvalý, podle <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>.  
  
 Instance pracovního postupu nelze obnovit v případě selhání hostitele nebo počítače, pokud není trvalý. Obecně doporučujeme uchování instanci pracovního postupu již v rané fázi v cyklu pracovního postupu.  
  
 Pokud pracovní postup je zaneprázdněn po dlouhou dobu, doporučujeme vám, že můžete uložit instanci pracovního postupu pravidelně po celou dobu její zaneprázdněný. To provedete tak, že přidáte <xref:System.Activities.Statements.Persist> aktivity v rámci pořadí aktivit, které udržují zaneprázdněn k instanci pracovního postupu. Tímto způsobem, aplikační domény recyklace, nezpůsobí selhání hostitele nebo selhání počítače systému se vrátit zpět na začátek zaneprázdněn období. Uvědomte si, že přidání <xref:System.Activities.Statements.Persist> aktivity do pracovního postupu, mohla způsobit snížení výkonu.  
  
 Windows Server App Fabric výrazně zjednodušuje konfiguraci a použití trvalost. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Systému Windows Server App Fabric trvalost](http://go.microsoft.com/fwlink/?LinkID=201200&clcid=0x409)  
  
## <a name="configuration-of-scalability-parameters"></a>Konfigurace parametrů škálovatelnost  
 Požadavky na škálovatelnost a výkon určují nastavení následujících parametrů:  
  
-   <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A>  
  
-   <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A>  
  
-   <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior.InstanceLockedExceptionAction%2A>  
  
 Tyto parametry musí být nastaven následujícím způsobem podle aktuální scénář.  
  
### <a name="scenario-a-small-number-of-workflow-instances-that-require-optimal-response-time"></a>Scénář: Malý počet instancí pracovních postupů, které vyžadují optimální odezvu  
 V tomto scénáři by měla zůstat všechny instance pracovního postupu načíst, kdy se stanou nečinné. Nastavit <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> velké hodnoty. Použití tohoto nastavení nemohou instanci pracovního postupu přesouvat mezi počítači. Toto nastavení použijte jenom v případě, že platí jedna nebo více následujících akcí:  
  
-   Instance pracovního postupu obdrží do jedné zprávy v průběhu své životnosti.  
  
-   Všechny instance pracovního postupu spustit v jednom počítači  
  
-   Stejný počítač přijímá všechny zprávy, které přijímá instanci pracovního postupu.  
  
 Použití <xref:System.Activities.Statements.Persist> aktivity nebo sady <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A> na hodnotu 0, pokud chcete povolit obnovení vaší instance pracovního postupu po selhání hostitele nebo počítače služby.  
  
### <a name="scenario-workflow-instances-are-idle-for-long-periods-of-time"></a>Scénář: Instancí pracovních postupů jsou pro dlouhou dobu nečinnosti.  
 V tomto scénáři nastavit <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> na 0, budou co nejdříve uvolnění prostředků.  
  
### <a name="scenario-workflow-instances-receive-multiple-messages-in-a-short-period-of-time"></a>Scénář: Instance pracovního postupu přijímat více zpráv v krátké době  
 V tomto scénáři nastavit <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> na 60 sekund, pokud se tyto zprávy jsou přijímány do stejného počítače. Zabrání se tak rychlé posloupnost uvolnění a načítání instance pracovního postupu. To také není ponechat instance v paměti příliš dlouho.  
  
 Nastavit <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> 0 a sadu <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior.InstanceLockedExceptionAction%2A> BasicRetry nebo AggressiveRetry, pokud se tyto zprávy můžou přijímat pomocí různých počítačů. To umožňuje k instanci pracovního postupu, který se má načíst jiným počítačem.  
  
### <a name="scenario-workflow-uses-delay-activities-with-short-durations"></a>Scénář: Pracovní postup používá prodlevy aktivity s krátké doby trvání  
 V tomto scénáři <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> pravidelně dotazuje databázi trvalosti pro instance, která by měla být načíst z důvodu vypršenou platností <xref:System.Activities.Statements.Delay> aktivity. Pokud <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> najde časovač vypršení platnosti v dalším intervalu dotazování úložiště Instance pracovního postupu SQL zkracuje interval dotazování. Další dotazování dojde poté bezprostředně potom, co časovač vypršela platnost. Tento způsob ukládání Instance pracovního postupu SQL dosahuje vysokou přesnost časovače, které se spouštět déle než interval dotazování, které se nastavuje pomocí <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A>. Pokud chcete povolit včas zpracování kratší zpoždění, musí zůstat k instanci pracovního postupu v paměti pro alespoň jeden interval dotazování.  
  
 Nastavit <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A> na 0, budou zapisovat do databáze trvalost čas vypršení platnosti.  
  
 Nastavit <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> na delší než nebo rovna hodnotě <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A> pro instance v paměti pro alespoň jeden interval dotazování.  
  
 Nedoporučujeme snižuje <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A> vzhledem k tomu, že to vede k zvýšená zátěž na databázi trvalost. Každý hostitel služby, který používá <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> dotazuje databázi jednou za období detekce. Nastavení <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A> příliš malá na čas interval může způsobit snížení Pokud velký počet hostitelů služby výkonnosti vašeho systému.  
  
## <a name="configuring-the-sql-workflow-instance-store"></a>Konfigurace úložiště Instance pracovního postupu SQL  
 Ukládání Instance pracovního postupu SQL má následující konfigurační parametry:  
  
 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.InstanceEncodingOption%2A>  
 Tento parametr nastaví <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> komprimovat stav instance pracovního postupu. Komprese snižuje množství dat, který je uložen v databázi trvalosti a snižuje se zatížení sítě v případě, že vyhrazený databázový server je umístěná databáze trvalost. Pokud se používá komprese, vyžaduje výpočetní prostředky pro komprimování a extrahování stav instance. Ve většině případů komprese poskytuje vyšší výkon.  
  
 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.InstanceCompletionAction%2A>  
 Tento parametr nastaví <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> zachovat nebo odstranit dokončené instance. Zachování dokončit instancí zvyšuje požadavky na úložiště databáze trvalosti a za následek větší tabulky, což zvyšuje úroveň časy vyhledávací tabulky. Pokud dokončené instance jsou vyžadovány pro ladění nebo auditování, je nejvhodnější dáte pokyn, aby <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> k odstranění dokončit instancí. Odstraněné instance by měly být udržovány pouze v případě, že uživatel vytvoří proces pro nakonec je odstranit. Všimněte si, že korelace klíče nelze znovu použít také k instanci pracovního postupu dokončené nachází v úložišti instance.  
  
 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A>  
 Tento parametr definuje maximální interval, pomocí kterého <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> dotazuje databázi trvalosti pro instance, které by měly být načteny při zpracování <xref:System.Activities.Statements.Delay> aktivity vyprší. Pokud <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> vyhledá časovač, který vyprší za další interval dotazování, zkrátí interval dotazování, tak, aby další dotazování dojde bezprostředně potom, co časovač vypršela platnost. Tento způsob ukládání Instance pracovního postupu SQL dosahuje vysokou přesnost časovače, které se spouštět déle než <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A>.  
  
 Nedoporučujeme snižuje <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A>, protože to vede k zvýšená zátěž na databázi trvalost. Každý hostitel služby, který používá <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> dotazuje databázi jednou za období detekce. Nastavení <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A> na příliš malá intervalu může způsobit snížení Pokud velký počet hostitelů služby výkonnosti vašeho systému.  
  
 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.HostLockRenewalPeriod%2A>  
 Tento parametr určuje interval, pomocí kterého hostitele obnovuje jeho zámku v databázi trvalost. Tento interval zkrátit vám umožní rychlejší obnovení instance pracovního postupu v případě selhání hostitele nebo počítače. Interval obnovování krátké zámku na druhé straně zvyšuje zatížení databáze trvalost. Každý hostitel služby, který používá <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> zaktualizuje jeho zámky v databázi jednou doby obnovení. Pokud počítač používá mnoho hostitelů služby, ujistěte se, že zatížení způsobeno obnovení zámku poklesu výkonu systému. Pokud ho, zvažte zvýšení <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.HostLockRenewalPeriod%2A>.  
  
 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.InstanceLockedExceptionAction%2A>  
 Pokud je povoleno, <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> opakování načíst uzamčeném instance pro další 30 sekund. Nastavit <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.InstanceLockedExceptionAction%2A> BasicRetry nebo AggressiveRetry Pokud pracovní postup přijímá více zpráv v krátkém čase, a tyto zprávy jsou přijímány různých počítačích.  
  
 Protože mechanismus opakování zatížení nezavádí žádné výkonu režie, dokud nejsou se pokusili zatížení opakování, <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.InstanceLockedExceptionAction%2A> by měla být vždy povolená.
