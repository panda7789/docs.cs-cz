---
title: <routing>
ms.date: 03/30/2017
ms.assetid: a210c209-3940-4288-9a8e-39b1e62606bc
ms.openlocfilehash: fcf2d4eec93fd7127c6f800e1c739ad1fac49203
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399965"
---
# \<routing>

Představuje konfigurační oddíl pro definování sady směrovacích filtrů, které určují typ Windows Communication Foundation (WCF), který se <xref:System.ServiceModel.Dispatcher.MessageFilter> má použít při vyhodnocování příchozích zpráv, jakož i směrovací tabulky definující cílové koncové body, na které se odesílají zprávy, když se filtr shoduje.

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<routing>**
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.serviceModel>
  <routing>
    <filters>
      <filter customType="String"
              filterData="String"
              filterType="Action/Address/AddressPrefix/And/Custom/Endpoint/MatchAll/XPath"
              name="String" />
    </filters>
    <routingTables>
      <table name="String">
        <entries>
          <add endpoint="String"
               filterName="String"
               priority="Integer" />
        </entries>
      </table>
    </routingTables>
  </routing>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy

Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

Žádné

### <a name="child-elements"></a>Podřízené prvky

|     | Description |
| --- | ----------- |
| [**\<filters>**](filters-of-routing.md) | Obsahuje sadu směrovacích filtrů, které určují typ Windows Communication Foundation (WCF) MessageFilter bude použit při vyhodnocování příchozích zpráv. |
| [**\<filterTables>**](filtertables.md) | Obsahuje mapování mezi směrovacími filtry a cílovými koncovými body k určení koncového bodu, který se má použít, když filtr odpovídá. |

### <a name="parent-elements"></a>Nadřazené prvky

|     | Description |
| --- | ----------- |
| **\<system.ServiceModel>** | Kořenový element všech elementů konfigurace služby WCF. |

## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
