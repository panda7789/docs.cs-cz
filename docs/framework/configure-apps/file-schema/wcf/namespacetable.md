---
title: '&lt;namespaceTable&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 64801766-01b7-4c65-9ce6-70ad5af67689
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4a6646b94449a79c96a8720a798f48298ab32ee0
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltnamespacetablegt"></a>&lt;namespaceTable&gt;

Představuje konfigurační oddíl pro definování sady elementů, které obsahují obor názvů pro mapování předpony, které lze použít ve filtrech XPath pro směrování.

**\<system.serviceModel >**   
&nbsp;&nbsp;**\<směrování >**   
&nbsp;&nbsp;&nbsp;&nbsp;**\<namespaceTable >**

## <a name="syntax"></a>Syntaxe

```xml
<system.serviceModel>
  <routing>
    <namespaceTable>
      <add namespace="String" prefix="String" />
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
| [**\<Filtr >**](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md) | Definuje mapování předpony oboru názvů používá pro výrazech XPath. |

### <a name="parent-elements"></a>Nadřazené prvky

|     | Popis |
| --- | ----------- |
| [**\<směrování >**](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md) | Představuje konfigurační oddíl pro definování sady směrování filtrů, které určují typ [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> použije při vyhodnocení příchozí zprávy, jakož i směrování tabulky definující cílové koncové body k odesílání zpráv do kdy odpovídá filtru. |

## <a name="see-also"></a>Viz také

<xref:System.ServiceModel.Routing.Configuration.NamespaceElementCollection?displayProperty=nameWithType>
