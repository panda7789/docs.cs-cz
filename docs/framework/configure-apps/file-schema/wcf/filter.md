---
title: '&lt;Filtr&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3266700b-904b-44e4-93a7-e06a1a445100
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 186c511cd8a69cef5e30e369641628a10a0972d7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltfiltergt"></a>&lt;Filtr&gt;

Definuje filtr, směrování, která určuje typ [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> použije při vyhodnocení příchozí zprávy, jako a všechny podpůrné data nebo parametrů požadovaných filtr.

\<system.serviceModel > \<směrování > \<filtry > \<filtru >

## <a name="syntax"></a>Syntaxe

```xml
<routing>
  <filters>
    <filter customType="String" 
            filterData="String" 
            filterType="Action/Address/AddressPrefix/And/Custom/Endpoint/MatchAll/XPath" 
            name="String" />
  </filters>
</routing>
```

## <a name="attributes-and-elements"></a>Atributy a elementy

Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

| Atribut  | Popis |
| ---------- | ----------- |
| customType | Řetězec obsahující typ plně kvalifikovaný název vlastního typu, který se má použít jako filtr. Pokud `filterType` je nastaven na `custom`, tento atribut obsahuje typ plně kvalifikovaný název třídy pro vytvoření.  `filterData`může také obsahovat hodnot použitých během vyhodnocení vlastního typu filtru. |
| fulltextových dat filtru | Řetězec obsahující data filtru. Další informace o tom, jak zadat Tento atribut najdete v tématu <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>. |
| filterType | Řetězec obsahující typ filtru. Tento atribut je <xref:System.ServiceModel.Routing.Configuration.FilterType> typu.  Další informace o tom, jak to funguje s `filterData` atributů najdete v tématu <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>. |
| name       | Řetězec obsahující jedinečný název tohoto elementu filtru. |

### <a name="child-elements"></a>Podřízené prvky

Žádné

### <a name="parent-elements"></a>Nadřazené prvky

| Prvek | Popis |
| ------- | ----------- |
| [\<směrování >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md) | Konfigurační oddíl pro definování sady směrování filtrů, které určují typ [!INCLUDE[ indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> použije při vyhodnocení příchozí zprávy. |

## <a name="see-also"></a>Viz také

<xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>    
<xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A?displayProperty=nameWithType>   
<xref:System.ServiceModel.Routing.Configuration.FilterType?displayProperty=nameWithType>   
