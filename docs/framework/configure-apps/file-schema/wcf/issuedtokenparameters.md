---
title: <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: 120b3f37-7331-4816-b712-d6aab39655a4
ms.openlocfilehash: 07fc2c4c52c29de1cfc9f498a6dc6b6da887b502
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925345"
---
# <a name="issuedtokenparameters"></a>\<issuedTokenParameters >
Určuje parametry tokenu zabezpečení vydaného ve federovaném scénáři zabezpečení.  
  
 \<system.serviceModel>  
\<> vazeb  
\<customBinding >  
\<> vazby  
\<> zabezpečení  
\<issuedTokenParameters >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<issuedTokenParameters defaultMessageSecurityVersion="System.ServiceModel.MessageSecurityVersion"
                       inclusionMode="AlwaysToInitiator/AlwaysToRecipient/Never/Once"
                       keySize="Integer"
                       keyType="AsymmetricKey/BearerKey/SymmetricKey"
                       tokenType="String">
  <additionalRequestParameters />
  <claimTypeRequirements>
    <add claimType="URI"
         isOptional="Boolean" />
  </claimTypeRequirements>
  <issuer address="String"
          binding="" />
  <issuerMetadata address="String" />
</issuedTokenParameters>
```  
  
## <a name="type"></a>type  
 `Type`  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|defaultMessageSecurityVersion|Určuje verze specifikací zabezpečení (WS-Security, WS-Trust, WS-Secure konverzace a WS-Security Policy), které musí vazba podporovat. Tato hodnota je typu <xref:System.ServiceModel.MessageSecurityVersion>.|  
|inclusionMode|Určuje požadavky na zařazení tokenu. Tento atribut je typu <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode>.|  
|keySize|Celé číslo, které určuje velikost klíče tokenu. Výchozí hodnota je 256.|  
|keyType|Platná hodnota <xref:System.IdentityModel.Tokens.SecurityKeyType> , která určuje typ klíče. Výchozí hodnota je `SymmetricKey`.|  
|tokenType|Řetězec, který určuje typ tokenu. Ve výchozím nastavení je "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAML".|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<additionalRequestParameters>](additionalrequestparameters-element.md)|Kolekce elementů konfigurace, které určují další parametry požadavku.|  
|[\<claimTypeRequirements>](claimtyperequirements-element.md)|Určuje kolekci požadovaných typů deklarací.<br /><br /> Ve federovaném scénáři služby stavují požadavky na příchozí přihlašovací údaje. Například příchozí přihlašovací údaje musí mít určitou sadu typů deklarací. Každý prvek v této kolekci určuje typy požadovaných a volitelných deklarací, které mají být zobrazeny ve federovaném pověření.|  
|[\<issuer>](issuer-of-issuedtokenparameters.md)|Prvek konfigurace, který určuje koncový bod, který vydává aktuální token.|  
|[\<issuerMetadata>](issuermetadata-of-issuedtokenparameters.md)|Prvek konfigurace, který určuje adresu koncového bodu metadat vystavitele tokenu.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<secureConversationBootstrap>](secureconversationbootstrap.md)|Určuje výchozí hodnoty, které se použijí při inicializaci služby zabezpečené konverzace.|  
|[\<> zabezpečení](security-of-custombinding.md)|Určuje možnosti zabezpečení pro vlastní vazbu.|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>
- <xref:System.ServiceModel.Configuration.SecurityElementBase.IssuedTokenParameters%2A>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Vazby](../../../wcf/bindings.md)
- [Rozšíření vazeb](../../../wcf/extending/extending-bindings.md)
- [Vlastní vazby](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [Postupy: Vytvoření vlastní vazby pomocí SecurityBindingElement](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [Zabezpečení vlastních vazeb](../../../wcf/samples/custom-binding-security.md)
- [Identita a ověřování služby](../../../wcf/feature-details/service-identity-and-authentication.md)
- [Federace a vystavené tokeny](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [Možnosti zabezpečení u vlastních vazeb](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [Federace a vystavené tokeny](../../../wcf/feature-details/federation-and-issued-tokens.md)
