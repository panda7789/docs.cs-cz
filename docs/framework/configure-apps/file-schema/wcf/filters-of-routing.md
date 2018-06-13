---
title: '&lt;filters&gt; – &lt;routing&gt;'
ms.date: 03/30/2017
ms.assetid: 7993cf90-9afd-4c3c-9608-184d5da1105c
ms.openlocfilehash: 9f0fa9bf51d264346738172f57a8efca7950fdb7
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32753112"
---
# <a name="ltfiltersgt-of-ltroutinggt"></a>&lt;filters&gt; – &lt;routing&gt;

Představuje konfigurační oddíl pro definování sady směrování filtrů, které určují typ služby Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> použije při vyhodnocení příchozí zprávy.

[**\<system.serviceModel >**](system-servicemodel.md)   
&nbsp;&nbsp;[**\<směrování >**](routing.md)   
&nbsp;&nbsp;&nbsp;&nbsp;**\<Filtry >**

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
| [**\<Filtr >**](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md) | Obsahuje směrování filtr, který určuje typ služby Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> se použije při vyhodnocení příchozí zprávy. |

### <a name="parent-elements"></a>Nadřazené prvky

|     | Popis |
| --- | ----------- |
| [**\<směrování >**](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md) | Představuje konfigurační oddíl pro definování sady směrování filtrů, které určují typ služby Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> použije při vyhodnocení příchozí zprávy, jakož i směrování tabulky definující cílové koncové body k Pokud filtr odpovídá odesílat zprávy. |

## <a name="see-also"></a>Viz také

<xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>
