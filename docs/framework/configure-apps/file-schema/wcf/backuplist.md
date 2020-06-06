---
title: <backupList>
ms.date: 03/30/2017
ms.assetid: a3d9d1f9-4a53-45e9-a880-86c8bee0b833
ms.openlocfilehash: 478211755b9131c03b72777ee95ff7223b9092c9
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850271"
---
# \<backupList>
Představuje konfigurační oddíl pro definování seznamu zálohování, který vytvoří výčet sady koncových bodů, které chcete, aby služba Směrování použila v případě, že není dostupný primární koncový bod. Pokud je první koncový bod v seznamu mimo provoz, směrovací služba se v seznamu automaticky převezme na další.  Díky tomu můžete rychle přidat do své aplikace spolehlivost, aniž byste museli poučit klientské aplikace o tom, jak zpracovávat složité vzory nebo kde jsou nasazené všechny služby.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<backupLists>**](backuplists.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<backupList>**  
  
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
|name|Řetězec, který určuje název, který slouží k identifikaci tohoto seznamu koncových bodů.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<filter>](filter.md)||  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<routing>](routing.md)|Seznam koncových bodů zálohy.|  
  
## <a name="remarks"></a>Poznámky  
 Tato část obsahuje uspořádanou kolekci koncových bodů, na které se v případě výjimky komunikace při odesílání do primárního koncového bodu přenáší zpráva.  
  
 Pokud odeslání do primárního koncového bodu uvedeného v `endpointName` atributu [\<add>](add-of-entries.md) selže s výjimkou komunikace, služba Směrování se pokusí odeslat zprávu do prvního koncového bodu v této části konfigurace. Pokud se tím také nezdaří s výjimkou komunikace, směrovací služba se pokusí odeslat zprávu na další zprávu obsaženou v této části, dokud pokus o odeslání nebude úspěšný, vrátí chybu jinou než výjimka komunikace nebo všechny koncové body v kolekci vrátily chybu.  
  
 V následujícím příkladu, pokud odeslání do primárního koncového bodu s názvem "cíl" vrátí výjimku komunikace, služba se pokusí odeslat zprávu do "alternateServiceQueue". Pokud se tento pokus vrátí taky výjimku komunikace, pokusí se služba Směrování odeslat zprávu na další koncový bod v kolekci.  
  
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
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection?displayProperty=nameWithType>
