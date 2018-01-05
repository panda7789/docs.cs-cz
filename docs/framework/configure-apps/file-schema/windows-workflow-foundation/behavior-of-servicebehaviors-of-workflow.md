---
title: "&lt;chování&gt; z &lt;serviceBehaviors&gt; pracovního postupu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 6a4b718a-1b40-4957-935a-f6122819ab3c
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7ce452b97b31f1d552eda481d2f514857372e2d5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltbehaviorgt-of-ltservicebehaviorsgt-of-workflow"></a>&lt;chování&gt; z &lt;serviceBehaviors&gt; pracovního postupu
**Chování** element obsahuje kolekce nastavení pro chování služby. Každý chování je indexované podle jeho **název**. Služby můžete propojit každý chování pomocí této konfigurace pomocí názvu **behaviorConfiguration**atribut [ \<endpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) element. To umožňuje koncové body sdílení obvyklé chování konfigurace bez předefinování nastavení.  
  
\<systém. ServiceModel >  
\<chování >  
\<serviceBehaviors >  
\<chování >  
  
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
                                  honstLockRenewalPeriod="TimeSpan" 
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
|name|Jedinečný řetězec, který obsahuje název konfigurace chování. Tato hodnota je uživatelem definovaný řetězec, který musí být jedinečný, protože funguje jako identifikační řetězec pro element.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<bufferReceive >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bufferreceive.md)|Zpracování, která umožňuje služba pracovního postupu ke zpracování zpráv mimo pořadí příjmu chování služby, který povoluje službu, chcete-li použít do vyrovnávací paměti.|  
|[\<směrování >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md)|Chování služby, která umožňuje službám využít trasování událostí pro Windows Sledování pomocí <xref:System.Activities.Tracking.EtwTrackingParticipant>.|  
|[\<sendMessageChannelCache >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/sendmessagechannelcache.md)|Chování služby, která umožňuje přizpůsobení mezipaměti sdílení úrovní, nastavení objektu pro vytváření mezipaměti kanál a nastavení mezipaměti kanál pro pracovní postupy, které odesílají zprávy do koncových bodů služby pomocí odesílání aktivity zasílání zpráv.|  
|[\<sqlWorkflowInstanceStore >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/sqlworkflowinstancestore.md)|Chování služby, který umožňuje nakonfigurovat <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> funkci, která podporuje zachování informací o stavu pro instance služby pracovního postupu do databáze systému SQL Server 2005 nebo SQL Server 2008.|  
|[\<workflowIdle >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowidle.md)|Chování služby, která určuje, kdy jsou instance nečinných pracovních postupů odpojeno a zachována.|  
|[\<workflowInstanceManagement >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancemanagement.md)|Chování služby, která vám umožní zadat nastavení, které určují, jak jsou spuštěny instance pracovních postupů, včetně stálost, neošetřené výjimky chování a nečinnosti chování.|  
|[\<workflowUnhandledException >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowunhandledexception.md)|Chování služby, který umožňuje určit akci, která má provést při dojde k neošetřené výjimce v rámci pracovního postupu služby.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<serviceBehaviors >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/servicebehaviors-of-workflow.md)|Kolekce elementů chování služby.|
