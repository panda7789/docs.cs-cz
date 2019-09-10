---
title: <filter>
ms.date: 03/30/2017
ms.assetid: 3266700b-904b-44e4-93a7-e06a1a445100
ms.openlocfilehash: 6e78275aaeb202405e327302455d56fa431d7f27
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855260"
---
# <a name="filter"></a>\<Filtrovat >

Definuje filtr směrování, který určuje typ Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> , který se má použít při vyhodnocování příchozích zpráv, a také všechna podpůrná data nebo parametry, které filtr vyžaduje.

[ **\<system.serviceModel>** ](system-servicemodel.md)\
&nbsp;&nbsp;[ **\<> směrování**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> filtrů**](filters-of-routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Filtrovat >**  
  
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
| customType | Řetězec obsahující plně kvalifikovaný název typu vlastního typu, který má být použit jako filtr. Pokud `filterType` je nastaven na `custom`, tento atribut obsahuje plně kvalifikovaný název třídy, která se má vytvořit.  `filterData`může také obsahovat hodnoty, které mají být použity během hodnocení vlastního filtru typu. |
| filterData | Řetězec obsahující data filtru. Další informace o tom, jak zadat tento atribut, naleznete <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>v tématu. |
| filterType | Řetězec obsahující typ filtru. Tento atribut je <xref:System.ServiceModel.Routing.Configuration.FilterType> typu.  Další informace o tom, jak to funguje s `filterData` atributem, <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>naleznete v tématu. |
| name       | Řetězec obsahující jedinečný název tohoto prvku filtru. |

### <a name="child-elements"></a>Podřízené prvky

Žádné

### <a name="parent-elements"></a>Nadřazené prvky

| Prvek | Popis |
| ------- | ----------- |
| [\<> směrování](routing.md) | Konfigurační oddíl pro definování sady směrovacích filtrů, které určují typ Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> , který se má použít při vyhodnocování příchozích zpráv. |

## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterType?displayProperty=nameWithType>
