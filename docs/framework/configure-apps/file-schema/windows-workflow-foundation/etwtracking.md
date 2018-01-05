---
title: '&lt;etwTracking&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: cb45c82e-6ea1-4c4d-924c-118a25ae1f35
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b989cd4a757b3da9371fdeb3a7e42ca00d7d28f3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltetwtrackinggt"></a>&lt;etwTracking&gt;
Chování služby, která umožňuje službám využít trasování událostí pro Windows Sledování pomocí <xref:System.Activities.Tracking.EtwTrackingParticipant>.  
  
\<systém. ServiceModel >  
\<chování >  
\<serviceBehaviors >  
\<chování >  
\<etwTracking >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <etwTracking profileName="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|Název_profilu|Řetězec, který určuje název profilu sledování přidružené k tomuto chování.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<chování > z \<serviceBehaviors >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|Určuje chování element.|  
  
## <a name="remarks"></a>Poznámky  
 Po přidání do služby konfiguraci chování, tento element konfigurace konfigurovat účastníkem sledování na službě pracovního postupu.  
  
 Sledování účastníci se používají pro získání data sledování vyzařovaného z pracovního postupu a uložit je do různá média. Stejně tak jakýkoli příspěvek zpracování na sledování, které záznamy lze provést také v rámci tohoto sledování.  
  
## <a name="example"></a>Příklad  
 Následující příklad konfigurace ukazuje standardní účastník sledování ETW konfigurován v souboru Web.config.  
  
 Id zprostředkovatele, které účastník sledování trasování událostí pro Windows používá k zápisu sledování záznamů do trasování událostí pro Windows je definována v  **\<diagnostics >** části. Účastník sledování má vlastní profil přidružen k určení záznamy sledování, které se přihlásí k odběru. To je definováno **profileName** atribut  **\<Přidat >** element. Jakmile jsou definované, účastník sledování je přidána do  **\<etwTracking >** služby chování. Vybrané sledování účastníci bude přidán do instance pracovního postupu rozšíření, tak, aby začnou záznamy sledování.  
  
```xml  
<configuration>   
  <system.web>   
    <compilation targetFrameworkMoniker=".NETFramework,Version=v4.0"/>   
  </system.web>   
  <system.serviceModel>   
    <diagnostics etwProviderId="52A3165D-4AD9-405C-B1E8-7D9A257EAC9F" />                
    <tracking>   
      <participants>   
        <add name="EtwTrackingParticipant"   
             type="System.Activities.Tracking.EtwTrackingParticipant, System.Activities, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"   
             profileName="HealthMonitoring_Tracking_Profile"/>   
      </participants>   
    </tracking>   
    <behaviors>   
      <serviceBehaviors>   
        <behavior>   
          <etwTracking profileName="Sample Tracking Profile"/>  
        </behavior>   
      </serviceBehaviors>   
    </behaviors>   
  </system.serviceModel>   
</configuration>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>  
 <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehaviorElement>  
 [Sledování a trasování pracovních postupů](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [Účastníci sledování](../../../../../docs/framework/windows-workflow-foundation/tracking-participants.md)
