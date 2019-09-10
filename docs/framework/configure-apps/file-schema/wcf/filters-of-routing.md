---
title: <filters> z <routing>
ms.date: 03/30/2017
ms.assetid: 7993cf90-9afd-4c3c-9608-184d5da1105c
ms.openlocfilehash: c9bc3a2c379e14d8cf687676a3ec40702d150e1e
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855246"
---
# <a name="filters-of-routing"></a>\<filtruje > \<> směrování.

Představuje konfigurační oddíl pro definování sady směrovacích filtrů, které určují typ Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> , který se použije při vyhodnocování příchozích zpráv.

[ **\<system.serviceModel>** ](system-servicemodel.md)\
&nbsp;&nbsp;[ **\<> směrování**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<> filtrů**  
  
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
| [ **\<Filtrovat >** ](filter.md) | Obsahuje filtr směrování, který určuje typ Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> , který se použije při vyhodnocování příchozích zpráv. |

### <a name="parent-elements"></a>Nadřazené prvky

|     | Popis |
| --- | ----------- |
| [ **\<> směrování**](routing.md) | Představuje konfigurační oddíl pro definování sady směrovacích filtrů, které určují typ Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> , který se má použít při vyhodnocování příchozích zpráv, jakož i směrovací tabulky, které definují cílové koncové body. Odeslat zprávy, když odpovídá filtr. |

## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>
