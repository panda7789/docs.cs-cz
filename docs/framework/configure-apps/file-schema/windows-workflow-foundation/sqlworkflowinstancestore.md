---
title: <sqlWorkflowInstanceStore>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 8a4e4214-fc51-4f4d-b968-0427c37a9520
ms.openlocfilehash: 8601f1c7f4e1dbf911020c328652c371bf039124
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61794430"
---
# <a name="sqlworkflowinstancestore"></a>\<sqlWorkflowInstanceStore>
Chování služby, která můžete nakonfigurovat <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> funkci, která podporuje zachovává informace o stavu pro instance služby pracovního postupu do databáze serveru SQL Server 2005 nebo SQL Server 2008. Další informace o této funkci najdete v tématu [Store Instance pracovního postupu SQL](../../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md).  
  
\<system.ServiceModel>  
\<chování >  
\<serviceBehaviors>  
\<chování >  
\<sqlWorkflowInstanceStore>  
  
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
|připojovací řetězec|Řetězec, který obsahuje připojovací řetězec použitý pro připojení k databázi aplikace základní stálost.|  
|PřipojovacíŘetězecNázev|Řetězec, který obsahuje název připojovacího řetězce k databázovému serveru. Příkladem pojmenovaného připojovacího řetězce je "DefaultConnectionString".|  
|honstLockRenewalPeriod|Časový interval hodnotu, která určuje časové období, ve kterém musí obnovit hostitele zámku v instanci. Pokud hostitel nebyly v určeném časovém intervalu uzamčení prodlužují instance odemknut a může být vyzvednutí jiného hostitele.<br /><br /> Uvolňování pracovního postupu znamená, že je také zachována. Pokud tento atribut je nastaven na hodnotu nula instance pracovního postupu je trvalá a odpojeno ihned po pracovního postupu změní nečinnosti. Nastavení tohoto atributu na hodnotu TimeSpan.MaxValue efektivně zakáže operace uvolnění. Instance nečinných pracovních postupů jsou nikdy uvolněna.|  
|instanceCompletionAction|Hodnota, která určuje, zda data instance pracovního postupu uchovány v úložišti stálost po dokončení instance pracovního postupu nebo pokud je v tomto okamžiku odstraněny. Tato hodnota je typu <xref:System.Activities.DurableInstancing.InstanceCompletionAction>.<br /><br /> Výčet akce se skládají ze odstranění instance data z úložiště stálosti nebo není odstranění instance data z úložiště stálost instance po dokončení jeho operace.<br /><br /> Udržování instancí po dokončení způsobí, že databáze stálost k rozvoji rychle a tato akce ovlivní výkon databáze. Měli byste nakonfigurovat zásadu vymazání databáze, která má odstranit tyto záznamy pravidelně tak, aby byl výkon databáze na úrovni, které odpovídají vašim požadavkům výkonu.|  
|instanceEncodingOption|Volitelné hodnotu, která určuje, zda informace o stavu instance je komprimován pomocí algoritmu GZip před informace jsou uloženy v úložišti stálost... Tato hodnota je typu <xref:System.Activities.DurableInstancing.InstanceEncodingOption>. Možné hodnoty této vlastnosti jsou <xref:System.Activities.DurableInstancing.InstanceEncodingOption.None>, který určuje bez komprese a <xref:System.Activities.DurableInstancing.InstanceEncodingOption.GZip>, která určuje, že instance data je komprimován a používá algoritmus gzip.|  
|instanceLockedExceptionAction|Hodnota, která určuje akci, k níž dojde v reakci na výjimku, která je vyvolána, pokud hostitel se pokusí Uzamknout instanci, protože instance je aktuálně uzamčen jiného hostitele. Tato hodnota je typu <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction>.<br /><br /> Možnosti povoleny pro toto pole jsou: NONE, Basic opakujte a účinnou opakovat. Výchozí hodnota je žádné. V následujícím seznamu vám poskytuje popisy těchto tří možností:<br /><br /> -Žádný. Hostitele služby nepokouší uzamknout instance a předá <xref:System.Runtime.DurableInstancing.InstanceLockedException> do volajícího.<br />-Základní opakovat. Hostitele služby reattempts k uzamčení instanci s lineární intervalu a předá výjimku volajícího na konci sekvence.<br />-Účinnou opakovat. Hostitele služby reattempts k uzamčení instanci s geometrickou řadou rostoucí zpoždění a předá <xref:System.Runtime.DurableInstancing.InstanceLockedException> do volajícího na konci sekvence.|  
|runnableInstancesDetectionPeriod||  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<chování > z \<serviceBehaviors >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|Určuje chování element.|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>
- <xref:System.ServiceModel.Activities.Configuration.SqlWorkflowInstanceStoreElement>
- <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>
- [Úložiště instancí pracovních postupů SQL](../../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md)
