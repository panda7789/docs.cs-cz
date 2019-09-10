---
title: <webHttpEndpoint>
ms.date: 03/30/2017
ms.assetid: ecaaeb6f-ebd0-411d-8b53-92477cd45347
ms.openlocfilehash: 8d4f55fd5b51ea77839b7fdbb930e937f5700417
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854795"
---
# <a name="webhttpendpoint"></a>\<webHttpEndpoint>
Tento prvek konfigurace definuje standardní koncový bod s pevnou [ \<vazbou WebHttpBinding >](webhttpbinding.md) [ \<](webhttp.md) , která automaticky přidá chování > protokolu WebHttp. Tento koncový bod použijte při psaní služby REST.  
  
[ **\<> Konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Oddílu StandardEndpoints >** ](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<webHttpEndpoint >**  
  
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
|automaticFormatSelectionEnabled|Logická hodnota, která určuje, zda je povolen automatický výběr formátu.<br /><br /> Pokud je povolen automatický formát výběru, infrastruktura analyzuje `Accept` hlavičku zprávy požadavku a určí nejvhodnější formát odpovědi. Pokud hlavička neurčuje vhodný formát odpovědi, `Content-Type` používá infrastruktura zprávu požadavku nebo výchozí formát odpovědi této operace. `Accept`|  
|defaultOutgoingResponseFormat|Atribut, který určuje výchozí formát odchozí odpovědi. Tento atribut je <xref:System.ServiceModel.Web.WebMessageFormat> typu|  
|helpEnabled|Logická hodnota, která označuje, zda je pro koncový bod povolena stránka Help HTTP.|  
|webEndpointType|Řetězec, který určuje typ koncového bodu.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|Kolekce standardních koncových bodů, které jsou předem definovanými koncovými body s jednou nebo více vlastnostmi (adresa, vazba, smlouva) opraveny.|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Description.WebHttpEndpoint>
- <xref:System.ServiceModel.Configuration.WebHttpEndpointElement>
