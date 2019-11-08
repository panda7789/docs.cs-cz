---
title: <oneWay>
ms.date: 03/30/2017
ms.assetid: 00e67e0e-77c0-4695-9138-c0997b0e5f3c
ms.openlocfilehash: a5c773ea91de882920775ac8dc0ecc1da68a6c9f
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738786"
---
# <a name="oneway"></a>\<oneWay >
Povoluje směrování paketů a používání jednosměrných metod pro vlastní vazbu.  
  
[ **\<configuration >** ](../configuration-element.md) \
&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) \
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<vazeb >** ](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<vazeb >** \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<oneWay >**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<oneWay packetRoutable="Boolean">
  <channelPoolSettings idleTimeout="TimeSpan"
                       leaseTimeout="TimeSpan"
                       maxOutboundConnectionsPerEndpoint="Integer" />
</oneWay>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`packetRoutable`|Logická hodnota, která určuje, zda je povoleno směrování paketů. Výchozí hodnota je `false`.|  
|`MaxAcceptedChannels`|Celé číslo, které určuje maximální počet kanálů, které mohou být přijaty.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<channelPoolSettings >](channelpoolsettings.md)|Objekt <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement>, který obsahuje vlastnosti fondu kanálu pro aktuální kanál.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[vazba \<](bindings.md)|Definuje všechny schopnosti vazby vlastní vazby.|  
  
## <a name="remarks"></a>Poznámky  
 Chcete-li povolit směrování paketů, je požadována jednosměrná konverzní vrstva, která tento prvek poskytuje. Uživatel může vytvořit vlastní vazbu, která tuto vazbu navrství prostřednictvím přenosu, který je v relaci nebo požadavek-odpověď, aby bylo možné směrovat paket. Tento prvek je také užitečný, pokud chcete zveřejnit jednosměrné metody v nativním režimu. Pro tuto vrstvu lze použít více transformací, jako je kompozitní duplexní a spolehlivé zasílání zpráv.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Channels.OneWayBindingElement>
- <xref:System.ServiceModel.Configuration.OneWayElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Vazby](../../../wcf/bindings.md)
- [Rozšíření vazeb](../../../wcf/extending/extending-bindings.md)
- [Vlastní vazby](../../../wcf/extending/custom-bindings.md)
- [\<customBinding >](custombinding.md)
