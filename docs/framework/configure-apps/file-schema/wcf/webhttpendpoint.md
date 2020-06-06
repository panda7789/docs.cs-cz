---
title: <webHttpEndpoint>
ms.date: 03/30/2017
ms.assetid: ecaaeb6f-ebd0-411d-8b53-92477cd45347
ms.openlocfilehash: 8d4f55fd5b51ea77839b7fdbb930e937f5700417
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70854795"
---
# \<webHttpEndpoint>
Tento prvek konfigurace definuje standardní koncový bod s pevnou [\<webHttpBinding>](webhttpbinding.md) vazbou, která automaticky přidá [\<webHttp>](webhttp.md) chování. Tento koncový bod použijte při psaní služby REST.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webHttpEndpoint>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <webHttpEndpoint>
      <standardEndpoint automaticFormatSelectionEnabled="String"
                        defaultOutgoingResponseFormat="Xml/Json"
                        helpEnabled="Boolean"
                        webEndpointType="String" />
    </webHttpEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|automaticFormatSelectionEnabled|Logická hodnota, která určuje, zda je povolen automatický výběr formátu.<br /><br /> Pokud je povolen automatický formát výběru, infrastruktura analyzuje `Accept` hlavičku zprávy požadavku a určí nejvhodnější formát odpovědi. Pokud `Accept` Hlavička neurčuje vhodný formát odpovědi, používá infrastruktura `Content-Type` zprávu požadavku nebo výchozí formát odpovědi této operace.|  
|defaultOutgoingResponseFormat|Atribut, který určuje výchozí formát odchozí odpovědi. Tento atribut je <xref:System.ServiceModel.Web.WebMessageFormat> typu|  
|helpEnabled|Logická hodnota, která označuje, zda je pro koncový bod povolena stránka Help HTTP.|  
|webEndpointType|Řetězec, který určuje typ koncového bodu.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|Kolekce standardních koncových bodů, které jsou předem definovanými koncovými body s jednou nebo více vlastnostmi (adresa, vazba, smlouva) opraveny.|  
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.Description.WebHttpEndpoint>
- <xref:System.ServiceModel.Configuration.WebHttpEndpointElement>
