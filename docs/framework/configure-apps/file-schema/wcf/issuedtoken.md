---
title: <issuedToken>
ms.date: 03/30/2017
ms.assetid: b6eae4b7-a6cd-4e1a-b0f6-f407022550b0
ms.openlocfilehash: 56439748926ada642018f48a5787634a50d0f180
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "72846863"
---
# \<issuedToken>
Určuje vlastní token, který slouží k ověření klienta ke službě.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuedToken>**  
  
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
|`cacheIssuedTokens`|Volitelný logický atribut, který určuje, zda jsou tokeny uloženy v mezipaměti. Výchozí formát je `true`.|  
|`defaultKeyEntropyMode`|Volitelný řetězcový atribut určující, které náhodné hodnoty (jenž) se používají pro operace handshake. Mezi hodnoty patří `ClientEntropy` , `ServerEntropy` a `CombinedEntropy` . výchozí hodnota je `CombinedEntropy` . Tento atribut je typu <xref:System.ServiceModel.Security.SecurityKeyEntropyMode> .|  
|`issuedTokenRenewalThresholdPercentage`|Volitelný celočíselný atribut, který určuje procentuální hodnotu platného časového rámce (poskytnutý vystavitelem tokenu), který může uplynout před obnovením tokenu. Hodnoty jsou od 0 do 100. Výchozí hodnota je 60, která určuje 60% času průchodu před pokusem o obnovení.|  
|`issuerChannelBehaviors`|Volitelný atribut, který určuje chování kanálu, které se má použít při komunikaci s vystavitelem.|  
|`localIssuerChannelBehaviors`|Volitelný atribut, který určuje chování kanálu, které se má použít při komunikaci s místním vystavitelem.|  
|`maxIssuedTokenCachingTime`|Volitelný atribut TimeSpan, který určuje dobu, po kterou jsou vydané tokeny ukládány do mezipaměti v případě, že Vystavitel tokenů (STS) neurčuje čas. Výchozí hodnota je "10675199.02:48:05.4775807."|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<localIssuer>](localissuer.md)|Určuje adresu místního vystavitele tokenu a vazbu, která se používá ke komunikaci s koncovým bodem.|  
|[\<issuerChannelBehaviors>](issuerchannelbehaviors-element.md)|Určuje chování koncového bodu, které se má použít při kontaktování místního vystavitele.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<clientCredentials>](clientcredentials.md)|Určuje přihlašovací údaje, které se používají k ověření klienta ke službě.|  
  
## <a name="remarks"></a>Poznámky  
 Vydaný token je vlastní typ přihlašovacích údajů, který se používá například při ověřování pomocí služby tokenů zabezpečení (STS) ve federovaném scénáři. Ve výchozím nastavení je tokenem token SAML. Další informace najdete v tématech [federace a vystavené tokeny](../../../wcf/feature-details/federation-and-issued-tokens.md)a [federační a vystavené tokeny](../../../wcf/feature-details/federation-and-issued-tokens.md).  
  
 Tato část obsahuje prvky, které slouží ke konfiguraci místního vystavitele tokenů nebo chování používaného se službou tokenů zabezpečení. Pokyny ke konfiguraci klienta pro použití místního vystavitele najdete v tématu [Postupy: Konfigurace místního vystavitele](../../../wcf/feature-details/how-to-configure-a-local-issuer.md).  
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.IssuedToken%2A>
- <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential>
- [Chování zabezpečení](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [Zabezpečení služeb a klientů](../../../wcf/feature-details/securing-services-and-clients.md)
- [Federace a vystavené tokeny](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [Zabezpečení klientů](../../../wcf/securing-clients.md)
- [Postupy: Vytvoření federovaného klienta](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [Postupy: Konfigurace místního vystavitele](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [Federace a vystavené tokeny](../../../wcf/feature-details/federation-and-issued-tokens.md)
