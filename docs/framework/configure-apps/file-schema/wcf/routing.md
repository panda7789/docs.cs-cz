---
title: "&lt;směrování&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a210c209-3940-4288-9a8e-39b1e62606bc
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7cbe682ef9f7bca25ab4f5089a295ada9a00a8bc
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltroutinggt"></a>&lt;směrování&gt;

Představuje konfigurační oddíl pro definování sady směrování filtrů, které určují typ [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> použije při vyhodnocení příchozí zprávy, jakož i směrování tabulky definující cílové koncové body k odesílání zpráv do kdy odpovídá filtru.

[**\<system.serviceModel >**](system-servicemodel.md)   
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
| [**\<Filtry >**](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md) | Obsahuje sadu směrování filtry, které určují typ [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] MessageFilter se použije při vyhodnocení příchozí zprávy. |
| [**\<filterTables >**](../../../../../docs/framework/configure-apps/file-schema/wcf/filtertables.md) | Obsahuje mapování mezi směrování filtry a cílové koncové body k určení kterému koncovému bodu pro použití při odpovídá filtru. |

### <a name="parent-elements"></a>Nadřazené prvky

|     | Popis |
| --- | ----------- |
| **\<systém. ServiceModel >** | Kořenový element všechny konfigurační prvky WCF. |

## <a name="see-also"></a>Viz také

<xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
