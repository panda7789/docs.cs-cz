---
title: <issuerMetadata> z <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: 1a85ca37-496d-4fa3-8d44-d6c9383d735c
ms.openlocfilehash: fcdd66ecd162dff5be86a1d4ab1b196f50dbd445
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400343"
---
# <a name="issuermetadata-of-issuedtokenparameters"></a>\<issuerMetadata> z \<issuedTokenParameters>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenParameters>**](issuedtokenparameters.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuerMetadata>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<issuerMetaData address="String" />
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|adresa|Povinná hodnota. Řetězec, který určuje adresu koncového bodu. Adresa musí být absolutním identifikátorem URI. Výchozí hodnota je prázdný řetězec.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<headers>](headers-element.md)|Kolekce hlaviček adres.|  
|[\<identity>](identity.md)|Identita, která umožňuje ověřování koncového bodu jinými koncovými body vyměňující zprávy.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<issuedTokenParameters>](issuedtokenparameters.md)|Určuje parametry tokenu zabezpečení vydaného ve federovaném scénáři zabezpečení.|  
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Identita a ověřování služby](../../../wcf/feature-details/service-identity-and-authentication.md)
- [Federace a vystavené tokeny](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [Možnosti zabezpečení u vlastních vazeb](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [Federace a vystavené tokeny](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [Vazby](../../../wcf/bindings.md)
- [Rozšíření vazeb](../../../wcf/extending/extending-bindings.md)
- [Vlastní vazby](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [Postupy: Vytvoření vlastní vazby pomocí SecurityBindingElement](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [Zabezpečení vlastních vazeb](../../../wcf/samples/custom-binding-security.md)
