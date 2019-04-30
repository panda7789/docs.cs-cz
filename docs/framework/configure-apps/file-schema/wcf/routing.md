---
title: <routing>
ms.date: 03/30/2017
ms.assetid: a210c209-3940-4288-9a8e-39b1e62606bc
ms.openlocfilehash: cc7c1a64f9481a7ab41cf35241ade04bd690dae0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61786383"
---
# <a name="routing"></a>\<směrování >

Představuje konfigurační oddíl pro definování sady směrovacích filtrů, které určují typ služby Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> má být použit při vyhodnocování příchozích zpráv, jakož i směrovací tabulky, které definujjí koncové body do odesílání zpráv do při shodě s filtrem.

[**\<system.serviceModel>**](system-servicemodel.md)   
&nbsp;&nbsp;**\<směrování >**
  
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

|     | Popis |
| --- | ----------- |
| [**\<Filtry >**](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md) | Obsahuje sady směrovacích filtrů, které určují, že typ MessageFilter Windows Communication Foundation (WCF) se použije při vyhodnocování příchozích zpráv. |
| [**\<filterTables >**](../../../../../docs/framework/configure-apps/file-schema/wcf/filtertables.md) | Obsahuje mapování mezi směrovacími filtry a cílovými koncovými body k určení, který koncový bod používat, pokud bod odpovídá filtru. |

### <a name="parent-elements"></a>Nadřazené prvky

|     | Popis |
| --- | ----------- |
| **\<system.ServiceModel>** | Kořenový element všechny elementy konfigurace WCF. |

## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
