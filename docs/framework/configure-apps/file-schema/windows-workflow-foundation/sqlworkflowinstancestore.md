---
title: '&lt;sqlWorkflowInstanceStore&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 8a4e4214-fc51-4f4d-b968-0427c37a9520
ms.openlocfilehash: 223108502395311f0db19753addc2a3f2345beac
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32757876"
---
# <a name="ltsqlworkflowinstancestoregt"></a>&lt;sqlWorkflowInstanceStore&gt;
Chování služby, který umožňuje nakonfigurovat <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> funkci, která podporuje zachování informací o stavu pro instance služby pracovního postupu do databáze systému SQL Server 2005 nebo SQL Server 2008. Další informace o této funkci najdete v tématu [úložiště Instance pracovního postupu SQL](../../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md).  
  
\<system.ServiceModel>  
\<chování >  
\<serviceBehaviors >  
\<chování >  
\<sqlWorkflowInstanceStore >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <sqlWorkflowInstanceStore connectionStringName="String" 
                                honstLockRenewalPeriod="TimeSpan" 
                                instanceCompletionAction="DeleteNothing/DeleteAll" 
                                instanceEncodingAction="None/GZip" 
                                instanceLockedExceptionAction="NoRetry/BasicRetry/AggressiveRetry" 
                                runnableInstancesDetectionPeriod="TimeSpan" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|připojovací řetězec|Řetězec, který obsahuje připojovací řetězec používaný pro připojení k databázi základní trvalost.|  
|PřipojovacíŘetězecNázev|Řetězec, který obsahuje řetězec pojmenovaného připojení k databázovému serveru. Příkladem pojmenovaného připojovacího řetězce je "DefaultConnectionString".|  
|honstLockRenewalPeriod|Časový interval hodnotu, která určuje časové období, ve kterém musí obnovit hostitele zámku v instanci. Pokud hostitel nebyly v určeném časovém intervalu uzamčení prodlužují instance odemknut a může být vyzvednutí jiného hostitele.<br /><br /> Uvolňování pracovního postupu znamená, že je také zachována. Pokud tento atribut je nastaven na hodnotu nula k instanci pracovního postupu je trvalá a uvolněna ihned po stane nečinnosti pracovního postupu. Nastavení tohoto atributu na hodnotu TimeSpan.MaxValue efektivně zakáže operace uvolnění. Instance nečinných pracovních postupů jsou nikdy uvolněna.|  
|instanceCompletionAction|Hodnota, která určuje, zda data instance pracovního postupu uchovány v úložišti stálost po dokončení instance pracovního postupu nebo pokud je v tomto okamžiku odstraněny. Tato hodnota je typu <xref:System.Activities.DurableInstancing.InstanceCompletionAction>.<br /><br /> Výčet akce se skládají ze odstranění instance data z úložiště stálosti nebo není odstranění instance data z úložiště stálost instance po dokončení jeho operace.<br /><br /> Udržování instancí po dokončení způsobí, že databáze stálost k rozvoji rychle a tato akce ovlivní výkon databáze. Měli byste nakonfigurovat zásadu vymazání databáze, která má odstranit tyto záznamy pravidelně tak, aby byl výkon databáze na úrovni, které odpovídají vašim požadavkům výkonu.|  
|instanceEncodingOption|Volitelné hodnotu, která určuje, zda informace o stavu instance je komprimován pomocí algoritmu GZip před informace jsou uloženy v úložišti stálost... Tato hodnota je typu `System.Activities.DurableInstancing.InstanceEncodingAction`. Možné hodnoty pro tuto vlastnost jsou "Žádný", který určuje bez komprese a "GZip", který určuje, že instance dat se komprimují a využívá algoritmus gzip.|  
|instanceLockedExceptionAction|Hodnota, která určuje akci, k níž dojde v reakci na výjimku, která je vyvolána, pokud hostitel se pokusí Uzamknout instanci, protože instance je aktuálně uzamčen jiného hostitele. Tato hodnota je typu <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction>.<br /><br /> Možnosti povoleny pro toto pole jsou: None, Basic opakujte a účinnou opakujte. Výchozí hodnota je žádné. V následujícím seznamu vám poskytuje popisy těchto tří možností:<br /><br /> -None. Hostitele služby nepokouší uzamknout instance a předá <xref:System.Runtime.DurableInstancing.InstanceLockedException> do volajícího.<br />-Základní opakování. Hostitele služby reattempts k uzamčení instanci s lineární intervalu a předá výjimku volajícího na konci sekvence.<br />-Agresivní opakování. Hostitele služby reattempts k uzamčení instanci s geometrickou řadou rostoucí zpoždění a předá <xref:System.Runtime.DurableInstancing.InstanceLockedException> do volajícího na konci sekvence.|  
|runnableInstancesDetectionPeriod||  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<chování > z \<serviceBehaviors >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|Určuje chování element.|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>  
 <xref:System.ServiceModel.Activities.Configuration.SqlWorkflowInstanceStoreElement>  
 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>  
 [Úložiště instancí pracovních postupů SQL](../../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md)
