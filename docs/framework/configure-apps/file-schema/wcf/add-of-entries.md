---
title: <add> z <entries>
ms.date: 03/30/2017
ms.assetid: 3af4805b-dc72-4f68-b168-da4fba8c6170
ms.openlocfilehash: 690fd07159e07b7e037f7330b31fdcba423e80f9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920132"
---
# <a name="add-of-entries"></a>\<Přidat > \<položek >
Představuje položku směrování, která mapuje filtr na koncový bod klienta, který byl dříve definován. Zprávy, které odpovídají tomuto filtru, budou odeslány do tohoto cíle.  
  
 \<system.serviceModel>  
\<> směrování  
\<filterTables >  
\<> filtru  
\<> položky  
\<add>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<routing>
  <filterTables>
    <filterTable name="String">
      <entries>
        <add backupList="String"
             endpointName="String"
             filterName="String"
             priority="Integer" />
      </entries>
    </filterTable>
  </filterTables>
</routing>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|backupList|Řetězec, který určuje odkaz na záložní seznam koncových bodů.|  
|endpoint|Řetězec, který určuje odkaz na koncový bod klienta, který obdrží zprávy, které odpovídají filtru zadanému `filterName` atributem.|  
|filterName|Řetězec, který určuje odkaz na element filtru.|  
|priority|Celé číslo, které určuje prioritu této položky.<br /><br /> Položky v tabulce směrování budou vyhodnocovány na základě priority, přičemž 0 je nejnižší priorita. Všechny položky pro konkrétní prioritu jsou vyhodnocovány současně, pokud se pro aktuální prioritu nenajde žádná vyhovující položka, bude vyhodnocena další úroveň priority.<br /><br /> Tato hodnota je volitelná.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<> směrování](routing.md)|Konfigurační oddíl, který obsahuje položky mapování směrování.|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType>
