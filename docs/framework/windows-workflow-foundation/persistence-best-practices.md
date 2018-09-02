---
title: Osvědčené postupy pro trvalost
ms.date: 03/30/2017
ms.assetid: 6974c5a4-1af8-4732-ab53-7d694608a3a0
ms.openlocfilehash: fdbf61e559efbd978df1c5a46fcbbbbc528ec98a
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43404687"
---
# <a name="persistence-best-practices"></a>Osvědčené postupy pro trvalost
Tento dokument popisuje osvědčené postupy pro návrh pracovního postupu a konfigurace související s trvalost pracovního postupu.  
  
## <a name="design-and-implementation-of-durable-workflows"></a>Návrh a implementace odolné pracovní postupy  
 Obecně platí pracovní postupy provedení práce v krátkém období, která je prokládaný s časem, během kterých je nečinný pracovního postupu, protože se čeká na událost. Tato událost může být například zpráva nebo zpráva u nichž vyprší platnost časovače. Aby bylo možné uvolnit instance pracovního postupu, když se změní na nečinnosti, musí hostitel služby zachovat instance pracovního postupu. Toto je možný jenom v případě, že instance pracovního postupu není v zóně no-persist (například čekání na dokončení transakce nebo čeká na asynchronní zpětné volání). Pokud chcete povolit instance nečinných pracovních postupů pro uvolnění, by měl Autor pracovního postupu použijte obory transakce a asynchronních aktivitách krátkodobou pouze pro akce. Konkrétně se Autor zachovával zpoždění aktivity v rámci těchto no zachovat zóny co nejkratší.  
  
 Pracovní postup mohl být trvalý, pouze pokud jsou všechny datové typy používané tímto pracovním postupem serializovatelný. Kromě toho musí být serializovatelný s vlastní typy používané v pracovních postupech trvalý <xref:System.Runtime.Serialization.NetDataContractSerializer> aby bylo možné nastavit jako trvalý, podle <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>.  
  
 Instance pracovního postupu nelze obnovit v případě selhání hostitele nebo počítače, pokud ještě nebyla trvale uložena. Obecně doporučujeme zachovat instance pracovního postupu v rané fázi životního cyklu pro pracovní postupy.  
  
 Pokud váš pracovní postup je zaneprázdněn po dlouhou dobu, doporučujeme, zachovat instance pracovního postupu pravidelně v průběhu doby zaneprázdněn. Můžete to provést tak, že přidáte <xref:System.Activities.Statements.Persist> aktivity v rámci posloupnost aktivit, které udržují zaneprázdněný instance pracovního postupu. Tímto způsobem, aplikační domény recyklaci, nezpůsobí selhání hostitele nebo selhání počítače systému se vrátit zpět na začátek zaneprázdněný období. Mějte na paměti, že přidání <xref:System.Activities.Statements.Persist> aktivity do pracovního postupu by mohla vést ke snížení výkonu.  
  
 Windows Server App Fabric výrazně zjednodušuje konfiguraci a použití trvalosti. Další informace najdete v tématu [systému Windows Server App Fabric trvalosti](https://go.microsoft.com/fwlink/?LinkID=201200&clcid=0x409)  
  
## <a name="configuration-of-scalability-parameters"></a>Konfigurace parametrů škálovatelnost  
 Požadavky na škálovatelnost a výkon určení nastavení z následujících parametrů:  
  
-   <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A>  
  
-   <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A>  
  
-   <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior.InstanceLockedExceptionAction%2A>  
  
 Tyto parametry, je třeba nastavit následujícím způsobem podle aktuální situaci.  
  
### <a name="scenario-a-small-number-of-workflow-instances-that-require-optimal-response-time"></a>Scénář: Malý počet instancí pracovních postupů, které vyžadují optimální odezvu  
 V tomto scénáři by měla zůstat všechny instance pracovních postupů načtených, když jsou nečinné. Nastavte <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> velké hodnoty. Použití tohoto nastavení zabraňuje přesunu mezi počítači instance pracovního postupu. Toto nastavení použijte jenom v případě, že platí jedna nebo více z následujících akcí:  
  
-   Instance pracovního postupu obdrží do jedné zprávy v průběhu svého životního cyklu.  
  
-   Všechny instance pracovního postupu spuštěné v jednom počítači  
  
-   Všechny zprávy, které jsou přijímány instance pracovního postupu jsou přijímány do stejného počítače.  
  
 Použití <xref:System.Activities.Statements.Persist> aktivity nebo sadu <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A> na 0 pro povolení obnovení instance pracovního postupu po selhání služby hostitele nebo počítače.  
  
### <a name="scenario-workflow-instances-are-idle-for-long-periods-of-time"></a>Scénář: Instancí pracovních postupů jsou pro dlouhou dobu nečinné.  
 V tomto scénáři, nastavte <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> na hodnotu 0 a co nejdříve uvolnit prostředky.  
  
### <a name="scenario-workflow-instances-receive-multiple-messages-in-a-short-period-of-time"></a>Scénář: Instance pracovního postupu přijmout více zpráv v krátké době  
 V tomto scénáři, nastavte <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> na 60 sekund, pokud se tyto zprávy jsou přijímány do stejného počítače. To zabraňuje rychlém sledu uvolnění a načítání instance pracovního postupu. To také neudržuje instance v paměti příliš dlouho.  
  
 Nastavte <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> 0 a sada <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior.InstanceLockedExceptionAction%2A> BasicRetry nebo AggressiveRetry, pokud se tyto zprávy můžou přijímat pomocí různých počítačů. To umožňuje instance pracovního postupu, které mají být načteny jiného počítače.  
  
### <a name="scenario-workflow-uses-delay-activities-with-short-durations"></a>Scénář: Pracovní postup používá zpoždění aktivity s krátkou dobou trvání  
 V tomto scénáři <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> pravidelně se dotazuje databáze trvalosti pro instancí, které by měl být načteny z důvodu vypršela <xref:System.Activities.Statements.Delay> aktivity. Pokud <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> najde časovač, který vyprší za na další interval dotazování, Store Instance pracovního postupu SQL zkrátí interval dotazování. Další dotazování dojde poté bezprostředně potom, co má vypršela. Tímto způsobem Store Instance pracovního postupu SQL dosahuje přesnější časovače, které trvají déle než interval dotazování, které nastavuje <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A>. Povolit včas zpracování kratší zpoždění, musí zůstat instance pracovního postupu v paměti pro alespoň jeden interval dotazování.  
  
 Nastavte <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A> na hodnotu 0 pro zápis do databáze trvalosti čas vypršení platnosti.  
  
 Nastavte <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> delší než nebo rovna hodnotě <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A> pro instance v paměti pro alespoň jeden interval dotazování.  
  
 Nedoporučujeme snížení <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A> protože důsledkem je zvýšená zátěž databáze trvalosti. Každý hostitel služby, který používá <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> dotazuje databázi jednou za období zjišťování. Nastavení <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A> příliš malý na čas interval může způsobit, že výkon vašeho systému, snížit, pokud je velký počet hostitelů služby.  
  
## <a name="configuring-the-sql-workflow-instance-store"></a>Konfigurace Store Instance pracovních postupů SQL  
 Store Instance pracovního postupu SQL má následující parametry konfigurace:  
  
 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.InstanceEncodingOption%2A>  
 Tento parametr nastaví <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> komprese stavu instance pracovního postupu. Komprese snižuje množství dat, která je uložena v databázi trvalosti a snižuje síťový provoz v případě, že databáze stálost nachází na vyhrazený databázový server. Pokud se používá komprese, vyžaduje výpočetní prostředky ke komprimaci a extrakci stav instance. Komprese ve většině případů poskytuje vyšší výkon.  
  
 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.InstanceCompletionAction%2A>  
 Tento parametr nastaví <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> zachovat nebo odstranit dokončené instance. Uchování dokončit instance zvyšuje požadavky na úložiště databáze trvalosti a vede k větší tabulky, který zlepšuje dobu vyhledávací tabulky. Pokud dokončené instance jsou požadovány pro ladění nebo auditování, je nejvhodnější dáte pokyn, aby <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> k instancím odstraňování se dokončilo. Odstraněné instancí se uchovávají pouze v případě, že uživatel vytvoří proces pro nakonec je odstranit. Všimněte si, že srovnávací klíče nesmí znovu použít jako dokončený pracovní postup instance se nachází v úložišti instancí.  
  
 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A>  
 Tento parametr definuje maximální časový interval, pomocí kterého <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> se dotazuje databáze trvalosti pro instance, které by měly být načteny při <xref:System.Activities.Statements.Delay> aktivity vyprší platnost. Pokud <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> najde časovač, který vyprší za na další interval dotazování, zkrátí interval dotazování, takže hned po vypršení časovač bude docházet k další dotazování. Tímto způsobem Store Instance pracovního postupu SQL dosahuje vysoké přesnost časovače, které trvají déle než <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A>.  
  
 Nedoporučujeme snížení <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A>, protože to vede k větší zatížení databáze trvalosti. Každý hostitel služby, který používá <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> dotazuje databázi jednou za období zjišťování. Nastavení <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A> příliš malý interval může způsobit výkon vašeho systému, snížit, pokud je velký počet hostitelů služby.  
  
 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.HostLockRenewalPeriod%2A>  
 Tento parametr definuje interval, pomocí kterého hostitele se tato možnost obnoví platnost zámku v databázi trvalosti. Zkrácení tohoto intervalu vám umožní rychlejší obnovení instancí pracovních postupů v případě selhání hostitele nebo počítače. Interval obnovování krátký zámku na druhé straně zvyšuje zatížení databáze trvalosti. Každý hostitel služby, který používá <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> se aktualizuje jednou za období obnovení jeho zámky v databázi. Pokud počítač používá mnoho hostitelů služby, ujistěte se, že zatížení způsobeno obnovení zámku ne snížit výkon systému. Pokud ano, zvažte zvýšení <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.HostLockRenewalPeriod%2A>.  
  
 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.InstanceLockedExceptionAction%2A>  
 Pokud je povoleno, <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> opakovanými pokusy o načtení zamknuté instance pro další 30 sekund. Nastavte <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.InstanceLockedExceptionAction%2A> BasicRetry nebo AggressiveRetry Pokud pracovní postup přijímá více zpráv v krátkém čase, a tyto zprávy jsou přijímány různých počítačích.  
  
 Protože mechanismus opakování zatížení nezavádí jakékoli výkonu režie tak dlouho, dokud zkoušet zatížení opakování, <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.InstanceLockedExceptionAction%2A> měla být vždy povolena.
