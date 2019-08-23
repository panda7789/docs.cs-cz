---
title: <add> z <participants>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 3c730850-6f8e-4102-acb8-8effb4e09463
ms.openlocfilehash: a6dc07b6f419fcb98e3f182269a99cb281139ba9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69946187"
---
# <a name="add-of-participants"></a>\<Přidat > \<účastníků >
Nakonfigurujte účastníkem sledování, která naslouchá na sledování záznamy probíhá emitovány přímo z modulu runtime a jejich zpracování libovolné způsobem, který byl nakonfigurován. Jedná se o zápis do konkrétní výstupu (např. soubor, konzoly, ETW), zpracování/agregaci záznamů nebo libovolnou kombinaci, který může být vyžadováno.  
  
 Další informace o sledování pracovních postupů a sledování účastníků najdete v tématu [sledování pracovních postupů a trasování](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) a [Sledování účastníků](../../../windows-workflow-foundation/tracking-participants.md).  
  
\<system.serviceModel>  
\<sledování >  
\<Účastníci >  
\<add>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml
<tracking>
  <participants>
    <add name="String" profileName="String" type="String" />
  </participants>
</tracking>   
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|name|Řetězec, který určuje název člena sledování.|  
|Název_profilu|Řetězec, který určuje název profilu sledování, která definuje sledování záznamů účastník sledování přihlásí k odběru.|  
|– typ|Řetězec, který určuje typ sledování člena.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Účastníci >](participants.md)|Seznam sledování účastníků|  
  
## <a name="remarks"></a>Poznámky  
 Sledování účastníci se používají pro získání data sledování vyzařovaného z pracovního postupu a uložit je do různá média. Stejně tak jakýkoli příspěvek zpracování na sledování, které záznamy lze provést také v rámci tohoto sledování.  
  
 Více sledování účastníci můžou událostí sledování současně. Každý účastník sledování může být přidružen k profilu různých sledování.  
  
 Účastník standardní sledování je poskytován, který zapíše záznamy sledování k relaci ETW. Účastník není konfigurována služba pracovního postupu přidáním specifické pro sledování chování v konfiguračním souboru. Povolení ETW umožňuje sledování účastník sledování záznamů, které mají být zobrazeny v události prohlížeč. Je-li který nesplňuje vaše požadavky, můžete také napsat vlastní sledování účastník.  
  
## <a name="example"></a>Příklad  
 Následující příklad konfigurace ukazuje standardní účastník sledování ETW konfigurován v souboru Web.config.  
  
 ID zprostředkovatele, které používá účastník sledování ETW k zápisu záznamů sledování do ETW, je definováno v  **\<části > diagnostiky** . Účastník sledování má vlastní profil přidružen k určení záznamy sledování, které se přihlásí k odběru. Tato definice je definována atributem  **\<** proformátu elementu add >. Po definování je účastník sledování přidán do  **\<chování služby etwTracking >** Service. Vybrané sledování účastníci bude přidán do instance pracovního postupu rozšíření, tak, aby začnou záznamy sledování.  
  
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection>
- <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>
- <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehaviorElement>
- [Sledování a trasování pracovních postupů](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [Účastníci sledování](../../../windows-workflow-foundation/tracking-participants.md)
