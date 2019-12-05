---
title: Osvědčené postupy pro trvalost
ms.date: 03/30/2017
ms.assetid: 6974c5a4-1af8-4732-ab53-7d694608a3a0
ms.openlocfilehash: 8ffbb3ebfa8f85e2b0052a9df9ada30766accd8e
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802515"
---
# <a name="persistence-best-practices"></a>Osvědčené postupy pro trvalost
Tento dokument popisuje osvědčené postupy pro návrh a konfiguraci pracovního postupu související s trvalým pracovním postupem.  
  
## <a name="design-and-implementation-of-durable-workflows"></a>Návrh a implementace trvalých pracovních postupů  
 Obecně platí, že pracovní postupy provádějí práci v krátkých obdobích, která jsou provedená v době, kdy je pracovní postup nečinný, protože čeká na událost. Tato událost může být taková jako zpráva nebo časovač vypršení platnosti. Aby bylo možné uvolnit instanci pracovního postupu, pokud se nejedná o nečinné, hostitel služby musí zachovat instanci pracovního postupu. To je možné pouze v případě, že instance pracovního postupu není v zóně bez trvalého uchování (například čekání na dokončení transakce nebo čekání na asynchronní zpětné volání). Aby bylo možné uvolnit nečinné instance pracovního postupu, měl by Autor pracovního postupu používat obory transakcí a asynchronní aktivity pouze pro krátkodobé akce. Konkrétně by měl autor v těchto zónách bez trvalého zachovávání aktivity co nejkratší.  
  
 Pracovní postup může být trvalý pouze v případě, že všechny datové typy používané pracovním postupem jsou serializovatelný. Kromě toho musí být vlastní typy používané v trvalých pracovních postupech serializovatelné s <xref:System.Runtime.Serialization.NetDataContractSerializer>, aby je bylo možné trvale <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>.  
  
 Instance pracovního postupu nejde obnovit v případě selhání hostitele nebo počítače, pokud není trvalá. Obecně doporučujeme, abyste zachovali instanci pracovního postupu na začátku v životním cyklu pracovního postupu.  
  
 Pokud je váš pracovní postup zaneprázdněný dlouhou dobu, doporučujeme, abyste instanci pracovního postupu pravidelně zachovali v průběhu svého zaneprázdněného období. Můžete to udělat tak, že přidáte <xref:System.Activities.Statements.Persist> aktivity v průběhu posloupnosti aktivit, které udržují instanci pracovního postupu zaneprázdněnou. Tímto způsobem může recyklace domény aplikace, selhání hostitelů nebo selhání počítače způsobit vrácení systému zpět na začátek zaneprázdněného období. Mějte na paměti, že přidání <xref:System.Activities.Statements.Persist> aktivit do pracovního postupu by mohlo vést k snížení výkonu.  
  
 Windows Server App Fabric značně zjednodušuje konfiguraci a používání trvalosti. Další informace najdete v tématu [trvalost Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677272(v=azure.10)) .  
  
## <a name="configuration-of-scalability-parameters"></a>Konfigurace parametrů škálovatelnosti  
 Požadavky na škálovatelnost a výkon určují nastavení následujících parametrů:  
  
- <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A>  
  
- <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A>  
  
- <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior.InstanceLockedExceptionAction%2A>  
  
 Tyto parametry by měly být nastaveny podle aktuálního scénáře jako následující.  
  
### <a name="scenario-a-small-number-of-workflow-instances-that-require-optimal-response-time"></a>Scénář: malý počet instancí pracovních postupů, které vyžadují optimální dobu odezvy.  
 V tomto scénáři by všechny instance pracovního postupu měly zůstat načteny, když se stanou nečinné. Nastavte <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> na velkou hodnotu. Použití tohoto nastavení zabrání přesunutí instance pracovního postupu mezi počítači. Toto nastavení použijte pouze v případě, že platí některá z následujících podmínek:  
  
- Instance pracovního postupu obdrží v průběhu své životnosti jednu zprávu.  
  
- Všechny instance pracovního postupu jsou spouštěny v jednom počítači.  
  
- Všechny zprávy, které jsou přijímány instancí pracovního postupu, jsou přijímány stejným počítačem.  
  
 Pomocí <xref:System.Activities.Statements.Persist> aktivity nebo nastavte <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A> na hodnotu 0, abyste mohli po selhání hostitele služby nebo počítače povolit obnovení instance pracovního postupu.  
  
### <a name="scenario-workflow-instances-are-idle-for-long-periods-of-time"></a>Scénář: instance pracovního postupu jsou nečinné po dlouhou dobu.  
 V tomto scénáři nastavte <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> na 0, aby se uvolnily prostředky co nejrychleji.  
  
### <a name="scenario-workflow-instances-receive-multiple-messages-in-a-short-period-of-time"></a>Scénář: instance pracovních postupů přijímají více zpráv v krátké době  
 V tomto scénáři nastavte <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> na 60 sekund, pokud jsou tyto zprávy přijímány stejným počítačem. Tím zabráníte rychlému sekvencování a načtení instance pracovního postupu. Tím se také nezachová instance v paměti, která je příliš dlouhá.  
  
 Nastavte <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> na 0 a nastavte <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior.InstanceLockedExceptionAction%2A> na BasicRetry nebo AggressiveRetry, pokud tyto zprávy mohou být přijímány různými počítači. To umožňuje, aby instance pracovního postupu byla načtena jiným počítačem.  
  
### <a name="scenario-workflow-uses-delay-activities-with-short-durations"></a>Scénář: pracovní postup používá aktivity zpoždění s krátkými dobami trvání  
 V tomto scénáři se <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> pravidelně dotazuje databáze trvalosti na instance, které by se měly načíst z důvodu <xref:System.Activities.Statements.Delay> aktivity s prošlou platností. Pokud <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> najde časovač, jehož platnost vyprší v dalším intervalu dotazování, zkrátí se v úložišti instance pracovního postupu SQL interval dotazování. Další dotaz pak bude následovat hned po vypršení platnosti časovače. Tímto způsobem úložiště instancí pracovních postupů SQL dosáhne vysoké přesnosti časovačů, které běží déle než interval dotazování, který je nastavený <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A>. Aby bylo možné včas zpracovat kratší prodlevy, musí instance pracovního postupu zůstat v paměti alespoň v jednom intervalu cyklického dotazování.  
  
 Nastavte <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A> na 0, chcete-li zapsat čas vypršení platnosti do databáze trvalosti.  
  
 Nastavte <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> na větší nebo rovnou <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A> aby se instance v paměti zachovala aspoň u jednoho intervalu cyklického dotazování.  
  
 Nedoporučujeme snižovat <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A>, protože to vede k zvýšenému zatížení databáze trvalosti. Každý hostitel služby, který používá <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> dotazuje databázi jednou za dobu detekce. Nastavení <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A> do příliš malého časového intervalu může způsobit snížení výkonu systému, pokud je počet hostitelů služby velký.  
  
## <a name="configuring-the-sql-workflow-instance-store"></a>Konfigurace úložiště instance pracovního postupu SQL  
 Úložiště instance pracovního postupu SQL má následující konfigurační parametry:  
  
 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.InstanceEncodingOption%2A>  
 Tento parametr instruuje <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> pro komprimaci stavu instance pracovního postupu. Komprese snižuje množství dat uložených v databázi trvalosti a snižuje síťový provoz pro případ, že se databáze trvaly nachází na vyhrazeném databázovém serveru. Pokud se používá komprese, vyžaduje výpočetní prostředky pro komprimaci a extrakci stavu instance. Ve většině případů komprese poskytuje zvýšený výkon.  
  
 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.InstanceCompletionAction%2A>  
 Tento parametr dá <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>, aby bylo možné zachovat nebo odstranit dokončené instance. Udržování dokončených instancí zvyšuje požadavky na úložiště databáze Persistence a vede k větším tabulkám, což zvyšuje dobu vyhledávání tabulek. Pokud nejsou dokončené instance požadovány pro ladění nebo auditování, je nejlepší dát <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> k odstranění dokončených instancí. Odstraněné instance by se měly uchovávat pouze v případě, že uživatel vytvoří proces pro jejich nakonec odebrání. Všimněte si, že korelační klíče nelze použít, dokud je instance dokončeného pracovního postupu uložena v úložišti instancí.  
  
 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A>  
 Tento parametr definuje maximální interval, pomocí kterého se <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> dotazuje databáze trvalosti pro instance, které by měly být načteny po vypršení platnosti <xref:System.Activities.Statements.Delay> aktivity. Pokud <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> najde časovač, jehož platnost vyprší v dalším intervalu dotazování, zkrátí interval dotazování tak, aby k dalšímu cyklickému dotazování docházelo ihned po vypršení platnosti časovače. Tímto způsobem úložiště instancí pracovních postupů SQL dosáhne vysoké přesnosti časovačů, které běží déle než <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A>.  
  
 Nedoporučujeme snižovat <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A>, protože to vede k zvýšenému zatížení databáze trvalosti. Každý hostitel služby, který používá <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> dotazuje databázi jednou za dobu detekce. Nastavení <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A> do příliš malého intervalu může způsobit snížení výkonu vašeho systému, pokud je počet hostitelů služby velký.  
  
 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.HostLockRenewalPeriod%2A>  
 Tento parametr definuje interval, s nímž hostitel obnoví zámek v databázi trvalosti. Zkrácením tohoto intervalu umožníte rychlejší obnovení instancí pracovního postupu v případě, že hostitel nebo počítač selže. Na druhé straně, krátké období obnovení zámků zvyšuje zatížení databáze trvalosti. Každý hostitel služby, který používá <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>, aktualizuje své zámky v databázi jednou za dobu obnovení. Pokud počítač používá mnoho hostitelů služby, zajistěte, aby zatížení způsobené obnovením zámku nesnížilo výkon systému. V takovém případě zvažte zvýšení <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.HostLockRenewalPeriod%2A>.  
  
 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.InstanceLockedExceptionAction%2A>  
 Pokud je povoleno, <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> se pokusí načíst uzamčenou instanci po dobu následujících 30 sekund. Nastavte <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.InstanceLockedExceptionAction%2A> na BasicRetry nebo AggressiveRetry, pokud pracovní postup obdrží více zpráv krátkou dobu a tyto zprávy jsou přijímány různými počítači.  
  
 Vzhledem k tomu, že mechanismus pro opakování zátěže nezavádí žádné nároky na výkon, dokud nedojde k pokusu o zatížení, <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.InstanceLockedExceptionAction%2A> by měla být vždy povolena.
