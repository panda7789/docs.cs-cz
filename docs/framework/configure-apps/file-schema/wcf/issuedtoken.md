---
title: '&lt;Třídy IssuedToken&gt;'
ms.date: 03/30/2017
ms.assetid: b6eae4b7-a6cd-4e1a-b0f6-f407022550b0
ms.openlocfilehash: a06d59c5dfb14e5f3346ff2424339659568a369a
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54150185"
---
# <a name="ltissuedtokengt"></a>&lt;Třídy IssuedToken&gt;
Určuje vlastní token pro ověření klienta ke službě.  
  
 \<system.ServiceModel>  
\<chování >  
část endpointBehaviors  
\<chování >  
\<třídu clientCredentials >  
\<třídy issuedToken >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<issuedToken cacheIssuedTokens="Boolean"
             defaultKeyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"
             issuedTokenRenewalThresholdPercentage = "0 to 100"
             issuerChannelBehaviors="String"
             localIssuerChannelBehaviors="String"
             maxIssuedTokenCachingTime="TimeSpan">
</issuedToken>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`cacheIssuedTokens`|Volitelný logický atribut, který určuje, zda tokeny uchovávány v mezipaměti. Výchozí hodnota je `true`.|  
|`defaultKeyEntropyMode`|Volitelný atribut řetězce, který určuje náhodné hodnoty (entropies) se používají pro metodu handshake. Mezi hodnoty patří `ClientEntropy`, `ServerEntropy`, a `CombinedEntropy`, výchozí hodnota je `CombinedEntropy`. Tento atribut je typu <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.|  
|`issuedTokenRenewalThresholdPercentage`|Volitelný celočíselný atribut, který určuje procento platných období (poskytnutých vystavitelem tokenu), která mohou uplynout před obnovením tokenu. Hodnoty jsou od 0 do 100. Výchozí hodnota je 60, který určuje 60 % časových intervalech, než dojde k pokusu o obnovení.|  
|`issuerChannelBehaviors`|Volitelný atribut, který určuje chování kanálu při komunikaci s vystavitelem.|  
|`localIssuerChannelBehaviors`|Volitelný atribut, který určuje chování kanálu při komunikaci s místním vystavitelem.|  
|`maxIssuedTokenCachingTime`|Volitelný atribut Timespan, který určuje dobu, po kterou jsou vydané tokeny ukládány do mezipaměti, když vystavitel (STS) neurčuje čas. Výchozí hodnota je "10675199.02:48:05.4775807."|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<localIssuer >](../../../../../docs/framework/configure-apps/file-schema/wcf/localissuer.md)|Určuje adresu místního vystavitele tokenu a vazby používaný ke komunikaci s koncovým bodem.|  
|[\<issuerChannelBehaviors >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)|Určuje chování koncového bodu při kontaktování místního vystavitele.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<třídu clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|Určuje pověření pro ověření klienta ke službě.|  
  
## <a name="remarks"></a>Poznámky  
 Vydaný token má typ vlastní pověření, například používaný při ověřování s zabezpečení tokenu služby (STS) ve scénáři federované. Ve výchozím nastavení token je SAML token. Další informace najdete v tématu [federace a vydané tokeny](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md). a [federace a vystavené tokeny](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).  
  
 Tato část obsahuje prvků, které slouží ke konfiguraci místního vystavitele tokeny nebo chování používaná službou tokenu zabezpečení. Pokyny ke konfiguraci klienta pro použití místního vystavitele, naleznete v tématu [jak: Konfigurace místního vystavitele](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement.IssuedToken%2A>  
 <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A>  
 <xref:System.ServiceModel.Security.IssuedTokenClientCredential>  
 [Chování zabezpečení](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [Zabezpečení služeb a klientů](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Federace a vystavené tokeny](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [Zabezpečení klientů](../../../../../docs/framework/wcf/securing-clients.md)  
 [Postupy: Vytvoření federovaného klienta](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [Postupy: Konfigurace místního vystavitele](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)  
 [Federace a vystavené tokeny](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
