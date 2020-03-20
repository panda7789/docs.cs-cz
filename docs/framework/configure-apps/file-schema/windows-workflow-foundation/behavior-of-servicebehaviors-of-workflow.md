---
title: <behavior>pracovního <serviceBehaviors> postupu
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 6a4b718a-1b40-4957-935a-f6122819ab3c
ms.openlocfilehash: 071cff8e9f6ec3fa0546a07d19160869d8b43f60
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152317"
---
# <a name="behavior-of-servicebehaviors-of-workflow"></a>\<chování> \<serviceBehaviors> pracovního postupu
Prvek **chování** obsahuje kolekci nastavení pro chování služby. Každé chování je indexováno **podle**názvu . Služby mohou propojit každé chování prostřednictvím tohoto názvu pomocí atributu **behaviorConfiguration** [ \<koncového bodu>](../wcf/endpoint-element.md) elementu. To umožňuje koncové body sdílení obvyklé chování konfigurace bez předefinování nastavení.  
  
[**\<>konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[**\<Systému.>ServiceModel**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<chování>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<chování>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.ServiceModel>  
  <behaviors>  
    <serviceBehaviors>  
      <behavior name="String">
        <bufferReceive maxPendingMessagesPerChannel="Integer" />
        <etwTracking profileName="String" />
        <sendMessageChannelCache allowUnsafeCaching="Boolean">
          <channelSettings idleTimeout="TimeSpan"
                           leaseTimeout="TimeSpan"
                           maxItemsInCache="Integer" />
          <factorySettings idleTimeout="TimeSpan"
                           leaseTimeout="TimeSpan"
                           maxItemsInCache="Integer" />
        </sendMessageChannelCache>
        <sqlWorkflowInstanceStore connectionStringName="String"
                                  hostLockRenewalPeriod="TimeSpan"
                                  instanceCompletionAction="DeleteNothing/DeleteAll"
                                  instanceEncodingAction="None/GZip"
                                  instanceLockedExceptionAction="NoRetry/BasicRetry/AggressiveRetry"
                                  runnableInstancesDetectionPeriod="TimeSpan" />
        <workflowIdle timeToPersist="TimeSpan"
                      timeToUnload="TimeSpan" />
        <workflowUnhandledException action="Abandon/AbandonAndSuspend/Cancel/Terminate" />
      </behavior>
    </serviceBehaviors>  
  </behaviors>  
</system.ServiceModel>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|jméno|Jedinečný řetězec, který obsahuje název konfigurace chování. Tato hodnota je uživatelem definovaný řetězec, který musí být jedinečný, protože funguje jako identifikační řetězec pro element.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[\<bufferReceive>](bufferreceive.md)|Zpracování, která umožňuje služba pracovního postupu ke zpracování zpráv mimo pořadí příjmu chování služby, který povoluje službu, chcete-li použít do vyrovnávací paměti.|  
|[\<směrování>](../wcf/routing-of-servicebehavior.md)|Chování služby, které umožňuje službě využívat sledování <xref:System.Activities.Tracking.EtwTrackingParticipant>ETW pomocí .|  
|[\<sendMessageChannelCache>](sendmessagechannelcache.md)|Chování služby, které umožňuje přizpůsobení úrovní sdílení mezipaměti, nastavení mezipaměti kanálu ve výrobě a nastavení mezipaměti kanálu pro pracovní postupy, které odesílají zprávy koncovým bodům služby pomocí aktivit odesílání zpráv.|  
|[\<sqlWorkflowInstanceStore>](sqlworkflowinstancestore.md)|Chování služby, které umožňuje <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> konfigurovat funkci, která podporuje uchování informací o stavu pro instance služby pracovního postupu do databáze SERVERU SQL Server 2005 nebo SQL Server 2008.|  
|[\<workflowIdle>](workflowidle.md)|Chování služby, která určuje, kdy jsou instance nečinných pracovních postupů odpojeno a zachována.|  
|[\<workflowInstanceManagement>](workflowinstancemanagement.md)|Chování služby, která vám umožní zadat nastavení, které určují, jak jsou spuštěny instance pracovních postupů, včetně stálost, neošetřené výjimky chování a nečinnosti chování.|  
|[\<workflowUnhandledException>](workflowunhandledexception.md)|Chování služby, který umožňuje určit akci, která má provést při dojde k neošetřené výjimce v rámci pracovního postupu služby.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[\<serviceBehaviors>](servicebehaviors-of-workflow.md)|Kolekce elementů chování služby.|
