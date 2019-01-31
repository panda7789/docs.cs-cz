---
title: <backupList>
ms.date: 03/30/2017
ms.assetid: a3d9d1f9-4a53-45e9-a880-86c8bee0b833
ms.openlocfilehash: 1e2b3eacbc845ad40030f3a48be2ef93c4ddbd8c
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55262423"
---
# <a name="backuplist"></a>\<backupList>
Představuje konfigurační oddíl pro definování zálohování seznamu, který uvádí sady koncových bodů, které byste chtěli směrovací služba použít v případě, že nelze dosáhnout primárního koncového bodu. Pokud je první koncový bod v seznamu dolů, směrovací služba se automaticky převzetí služby při selhání k dalším objektem v seznamu.  To umožňuje rychlé přidání spolehlivosti do aplikace bez nutnosti představuje klientskou aplikaci, jak zpracovávat složité vzory nebo všechny služby, ve které jsou nasazené.  
  
 \<system.serviceModel>  
\<směrování >  
\<backupLists>  
\<backupList>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|name|Řetězec určující název používaný k identifikaci tohoto seznamu koncových bodů.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Filtr >](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md)||  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<směrování >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|Seznamu zálohy koncových bodů.|  
  
## <a name="remarks"></a>Poznámky  
 Tato část obsahuje řazená kolekce koncových bodů, které zprávy budou předány v případě výjimky komunikace při odesílání na primární koncový bod.  
  
 Pokud uvedený na seznamu odeslat na primární koncový bod `endpointName` atribut [ \<Přidat >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-entries.md) selže s výjimkou komunikace, směrovací služba se pokusí o odeslání zprávy na první koncový bod v tomto konfigurační oddíl. Pokud to je také neúspěšná, s výjimkou komunikace, směrovací služba se pokusí odeslat zprávu na další zprávu obsažené v této části, až do pokusu o odeslání úspěšná, vrátí selhání než výjimky komunikace nebo všechny koncové body v kolekce mají vrátila chybu.  
  
 V následujícím příkladu Pokud odeslat na primární koncový bod s názvem "Cíl" vrátí výjimky komunikace, služba se pokusí odeslání zprávy do "alternateServiceQueue". Pokud tento pokus také vrátí hodnotu výjimky komunikace, směrovací služba se pokusí odeslat zprávu do další koncový bod v kolekci.  
  
```xml  
<filterTables>
  <filterTable name="filterTable1">
    <add filterName="MatchAllFilter1"
         endpointName="Destination"
         backupList="backupEndpointList" />
  </filterTable>
</filterTables>
<backupLists>
  <backupList name="backupEndpointList">
    <add endpointName="backupServiceQueue" />
    <add endpointName="alternateServiceQueue" />
  </backupList>
</backupLists>
```  
  
## <a name="see-also"></a>Viz také:
- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection?displayProperty=nameWithType>
