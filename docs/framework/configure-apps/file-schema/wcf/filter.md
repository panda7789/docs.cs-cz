---
title: '&lt;Filtr&gt;'
ms.date: 03/30/2017
ms.assetid: 3266700b-904b-44e4-93a7-e06a1a445100
ms.openlocfilehash: f7224eab9f3c21bce9839298b50c52e9da08b6f7
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54146404"
---
# <a name="ltfiltergt"></a>&lt;Filtr&gt;

Definuje směrovací filtr, který určuje typ služby Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> má být použit při vyhodnocování příchozích zpráv, jako a libovolných podpůrných dat nebo parametrů vyžadovaných filtrem.

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
| Customtype – | Řetězec obsahující název plně kvalifikovaný typ vlastního typu, který má být použit jako filtr. Pokud `filterType` je nastavena na `custom`, tento atribut obsahuje název plně kvalifikovaný typ třídy k vytvoření.  `filterData` může také obsahovat hodnoty, které se použijí při vyhodnocení filtru vlastního typu. |
| fulltextových dat filtru | Řetězec obsahující data filtru. Další informace o tom, jak tento atribut zadán, naleznete v tématu <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>. |
| filterType | Řetězec obsahující typ filtru. Tento atribut je <xref:System.ServiceModel.Routing.Configuration.FilterType> typu.  Další informace o tom, jak to funguje s `filterData` atributu naleznete v tématu <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>. |
| name       | Řetězec obsahující jedinečný název tohoto prvku filtru. |

### <a name="child-elements"></a>Podřízené prvky

Žádné

### <a name="parent-elements"></a>Nadřazené prvky

| Prvek | Popis |
| ------- | ----------- |
| [\<směrování >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md) | Konfigurační oddíl pro definování sady směrovacích filtrů, které určují typ služby Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> má být použit při vyhodnocování příchozích zpráv. |

## <a name="see-also"></a>Viz také:

<xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>    
<xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A?displayProperty=nameWithType>   
<xref:System.ServiceModel.Routing.Configuration.FilterType?displayProperty=nameWithType>   
