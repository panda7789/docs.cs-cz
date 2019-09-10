---
title: <namespaceTable>
ms.date: 03/30/2017
ms.assetid: 64801766-01b7-4c65-9ce6-70ad5af67689
ms.openlocfilehash: aefe7beec7335d80341e670961800907c2bd0200
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855092"
---
# <a name="namespacetable"></a>\<namespaceTable>

Představuje konfigurační oddíl pro definování sady prvků, které obsahují obor názvů k mapování předpon, které lze následně použít ve filtrech XPath pro směrování.

[ **\<> Konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> směrování**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> oboru názvů**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.serviceModel>
  <routing>
    <namespaceTable>
      <add namespace="String"
           prefix="String" />
    </namespaceTable>
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
| [ **\<Filtrovat >** ](filter.md) | Definuje mapování předpony oboru názvů používané pro výrazy XPath. |

### <a name="parent-elements"></a>Nadřazené prvky

|     | Popis |
| --- | ----------- |
| [ **\<> směrování**](routing.md) | Představuje konfigurační oddíl pro definování sady směrovacích filtrů, které určují typ Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> , který se má použít při vyhodnocování příchozích zpráv, jakož i směrovací tabulky, které definují cílové koncové body. Odeslat zprávy, když odpovídá filtr. |

## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Routing.Configuration.NamespaceElementCollection?displayProperty=nameWithType>
