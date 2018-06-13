---
title: '&lt;IssuedToken&gt;'
ms.date: 03/30/2017
ms.assetid: b6eae4b7-a6cd-4e1a-b0f6-f407022550b0
ms.openlocfilehash: 9a8d701e0806aae0a17a1c5ff7284606dd080f85
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32750229"
---
# <a name="ltissuedtokengt"></a>&lt;IssuedToken&gt;
Určuje vlastní token používaný k ověření klienta ke službě.  
  
 \<system.ServiceModel>  
\<chování >  
část endpointBehaviors  
\<chování >  
\<clientCredentials >  
\<issuedToken >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<issuedToken   
   cacheIssuedTokens="Boolean"  
   defaultKeyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"  
   issuedTokenRenewalThresholdPercentage = "0 to 100"  
   issuerChannelBehaviors="String"  
      localIssuerChannelBehaviors="String"  
   maxIssuedTokenCachingTime="TimeSpan"  
</issuedToken>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`cacheIssuedTokens`|Volitelný logický atribut, který určuje, zda jsou do mezipaměti tokenů. Výchozí hodnota je `true`.|  
|`defaultKeyEntropyMode`|Volitelný řetězec atribut, který určuje, které náhodných hodnot (entropies) se používá pro operace metody handshake. Hodnoty zahrnují `ClientEntropy`, `ServerEntropy`, a `CombinedEntropy`, výchozí hodnota je `CombinedEntropy`. Tento atribut je typu <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.|  
|`issuedTokenRenewalThresholdPercentage`|Volitelné číslo atribut, který určuje procento platný časovém rámci (poskytl vydavatel tokenu), může uplynout, než token byl obnoven. Hodnoty jsou od 0 do 100. Výchozí hodnota je 60, který určuje 60 % doby přerušeno dříve, než dojde k pokusu o obnovení.|  
|`issuerChannelBehaviors`|Volitelný atribut, který určuje chování kanál používat při komunikaci s vystavitele.|  
|`localIssuerChannelBehaviors`|Volitelný atribut, který určuje chování kanál používat při komunikaci s místní vystavitele.|  
|`maxIssuedTokenCachingTime`|Volitelný atribut časový interval, který určuje dobu, která vydala tokeny jsou uložené v mezipaměti při vydavatel tokenu (služby tokenů zabezpečení) neurčuje čas. Výchozí hodnota je "10675199.02:48:05.4775807."|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<localIssuer >](../../../../../docs/framework/configure-apps/file-schema/wcf/localissuer.md)|Určuje adresu místního vystavitele tokenu a vazby používaný ke komunikaci s koncovým bodem.|  
|[\<issuerChannelBehaviors >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)|Určuje chování koncový bod při kontaktování místního vystavitele.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|Určuje pověření použitá k ověření klienta pro službu.|  
  
## <a name="remarks"></a>Poznámky  
 Vystavený token je typu vlastní pověření, použije, například při ověřování s zabezpečení tokenu služby (STS) v případě federovaných. Ve výchozím nastavení je token SAML token. Další informace najdete v tématu [federace a vystavené tokeny](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md). a [federace a vystavené tokeny](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).  
  
 Tato část obsahuje prvky, které konfigurace místního vystavitele tokeny nebo chování použít s služby tokenů zabezpečení. Pokyny týkající se konfigurace klienta pomocí místního vystavitele najdete v tématu [postupy: Konfigurace místního vystavitele](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).  
  
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
