---
title: <behavior><serviceBehaviors>pracovního postupu
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 6a4b718a-1b40-4957-935a-f6122819ab3c
ms.openlocfilehash: 071cff8e9f6ec3fa0546a07d19160869d8b43f60
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152317"
---
# <a name="behavior-of-servicebehaviors-of-workflow"></a><span data-ttu-id="130d9-102">\<behavior>\<serviceBehaviors>pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="130d9-102">\<behavior> of \<serviceBehaviors> of workflow</span></span>
<span data-ttu-id="130d9-103">Prvek **chování** obsahuje soubor nastavení chování služby.</span><span class="sxs-lookup"><span data-stu-id="130d9-103">The **behavior** element contains a collection of settings for the behavior of a service.</span></span> <span data-ttu-id="130d9-104">Každé chování je indexováno podle **názvu**.</span><span class="sxs-lookup"><span data-stu-id="130d9-104">Each behavior is indexed by its **name**.</span></span> <span data-ttu-id="130d9-105">Služby lze propojit s každým chováním prostřednictvím tohoto názvu pomocí atributu **behaviorConfiguration** [\<endpoint>](../wcf/endpoint-element.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="130d9-105">Services can link to each behavior through this name using the **behaviorConfiguration** attribute of the [\<endpoint>](../wcf/endpoint-element.md) element.</span></span> <span data-ttu-id="130d9-106">To umožňuje koncové body sdílení obvyklé chování konfigurace bez předefinování nastavení.</span><span class="sxs-lookup"><span data-stu-id="130d9-106">This allows endpoints to share common behavior configurations without redefining the settings.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<behavior>**  
  
## <a name="syntax"></a><span data-ttu-id="130d9-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="130d9-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="130d9-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="130d9-108">Attributes and Elements</span></span>  
 <span data-ttu-id="130d9-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="130d9-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="130d9-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="130d9-110">Attributes</span></span>  
  
|<span data-ttu-id="130d9-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="130d9-111">Attribute</span></span>|<span data-ttu-id="130d9-112">Popis</span><span class="sxs-lookup"><span data-stu-id="130d9-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="130d9-113">name</span><span class="sxs-lookup"><span data-stu-id="130d9-113">name</span></span>|<span data-ttu-id="130d9-114">Jedinečný řetězec, který obsahuje název konfigurace chování.</span><span class="sxs-lookup"><span data-stu-id="130d9-114">A unique string that contains the configuration name of the behavior.</span></span> <span data-ttu-id="130d9-115">Tato hodnota je uživatelem definovaný řetězec, který musí být jedinečný, protože funguje jako identifikační řetězec pro element.</span><span class="sxs-lookup"><span data-stu-id="130d9-115">This value is a user-defined string that must be unique, since it acts as the identification string for the element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="130d9-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="130d9-116">Child Elements</span></span>  
  
|<span data-ttu-id="130d9-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="130d9-117">Element</span></span>|<span data-ttu-id="130d9-118">Description</span><span class="sxs-lookup"><span data-stu-id="130d9-118">Description</span></span>|  
|-------------|-----------------|  
|[\<bufferReceive>](bufferreceive.md)|<span data-ttu-id="130d9-119">Zpracování, která umožňuje služba pracovního postupu ke zpracování zpráv mimo pořadí příjmu chování služby, který povoluje službu, chcete-li použít do vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="130d9-119">A service behavior that enables a service to use buffered receive processing, which enables a workflow service to process out-of-order messages.</span></span>|  
|[\<routing>](../wcf/routing-of-servicebehavior.md)|<span data-ttu-id="130d9-120">Chování služby, které umožňuje službě využívat sledování ETW pomocí <xref:System.Activities.Tracking.EtwTrackingParticipant> .</span><span class="sxs-lookup"><span data-stu-id="130d9-120">A service behavior that allows a service to utilize ETW tracking using an <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span></span>|  
|[\<sendMessageChannelCache>](sendmessagechannelcache.md)|<span data-ttu-id="130d9-121">Chování služby, které umožňuje přizpůsobení úrovní sdílení mezipaměti, nastavení mezipaměti objektu pro vytváření kanálu a nastavení mezipaměti kanálu pro pracovní postupy, které odesílají zprávy do koncových bodů služby pomocí aktivit odesílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="130d9-121">A service behavior that enables the customization of the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using Send messaging activities.</span></span>|  
|[\<sqlWorkflowInstanceStore>](sqlworkflowinstancestore.md)|<span data-ttu-id="130d9-122">Chování služby, které umožňuje nakonfigurovat <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> funkci, která podporuje informace o stavu pro instance služby pracovního postupu do databáze SQL Server 2005 nebo SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="130d9-122">A service behavior that allows you to configure the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> feature, which supports persisting state information for workflow service instances into an SQL Server 2005 or SQL Server 2008 database.</span></span>|  
|[\<workflowIdle>](workflowidle.md)|<span data-ttu-id="130d9-123">Chování služby, která určuje, kdy jsou instance nečinných pracovních postupů odpojeno a zachována.</span><span class="sxs-lookup"><span data-stu-id="130d9-123">A service behavior that controls when idle workflow instances are unloaded and persisted.</span></span>|  
|[\<workflowInstanceManagement>](workflowinstancemanagement.md)|<span data-ttu-id="130d9-124">Chování služby, která vám umožní zadat nastavení, které určují, jak jsou spuštěny instance pracovních postupů, včetně stálost, neošetřené výjimky chování a nečinnosti chování.</span><span class="sxs-lookup"><span data-stu-id="130d9-124">A service behavior that enables you to specify settings that control how workflow instances are run, including persistence, unhandled Exception behavior and idle behavior.</span></span>|  
|[\<workflowUnhandledException>](workflowunhandledexception.md)|<span data-ttu-id="130d9-125">Chování služby, který umožňuje určit akci, která má provést při dojde k neošetřené výjimce v rámci pracovního postupu služby.</span><span class="sxs-lookup"><span data-stu-id="130d9-125">A service behavior that enables you to specify the action to take when an unhandled exception occurs within a workflow service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="130d9-126">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="130d9-126">Parent Elements</span></span>  
  
|<span data-ttu-id="130d9-127">Prvek</span><span class="sxs-lookup"><span data-stu-id="130d9-127">Element</span></span>|<span data-ttu-id="130d9-128">Description</span><span class="sxs-lookup"><span data-stu-id="130d9-128">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceBehaviors>](servicebehaviors-of-workflow.md)|<span data-ttu-id="130d9-129">Kolekce elementů chování služby.</span><span class="sxs-lookup"><span data-stu-id="130d9-129">A collection of service behavior elements.</span></span>|
