---
title: "&lt;– issuedTokenParameters&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 120b3f37-7331-4816-b712-d6aab39655a4
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4fdb110302de05fd7dac3c318b8cd4bf83c0155b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltissuedtokenparametersgt"></a>&lt;– issuedTokenParameters&gt;
Určuje parametry pro token zabezpečení vydané ve scénáři federovaný zabezpečení.  
  
 \<system.serviceModel >  
\<vazby >  
\<customBinding >  
\<Vazba >  
\<zabezpečení >  
\<– issuedTokenParameters >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<issuedTokenParameters   
      DefaultMessageSecurityVersion="System.ServiceModel.MessageSecurityVersion"  
      inclusionMode="AlwaysToInitiator/AlwaysToRecipient/Never/Once"  
      keySize="Integer"  
   keyType="AsymmetricKey/BearerKey/SymmetricKey"  
      tokenType="String" >  
   <additionalRequestParameters />  
      <claimTypeRequirements>  
            <add claimType="URI"  
           isOptional="Boolean" />  
      </claimTypeRequirements>  
      <issuer address="String"   
                      binding=" " />  
      <issuerMetadata address="String" />   
</issuedTokenParameters>  
```  
  
## <a name="type"></a>Typ  
 `Type`  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|defaultMessageSecurityVersion|Určuje bezpečnostní specifikací verze (WS-zabezpečení, WS-Trust, WS-zabezpečené konverzace a zásady zabezpečení WS), musí být podporována vazba. Tato hodnota je typu <xref:System.ServiceModel.MessageSecurityVersion>.|  
|inclusionMode|Určuje požadavky na zařazení tokenu. Tento atribut je typu <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode>.|  
|Velikost klíče|Celé číslo, které určuje velikost klíče tokenu. Výchozí hodnota je 256.|  
|Typ_klíče.|Platná hodnota <xref:System.IdentityModel.Tokens.SecurityKeyType> určující typ klíče. Výchozí hodnota je `SymmetricKey`.|  
|tokenType|Řetězec, který určuje typ tokenu. Výchozí hodnota je "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAML".|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<additionalRequestParameters >](../../../../../docs/framework/configure-apps/file-schema/wcf/additionalrequestparameters-element.md)|Kolekce konfigurační prvky, které zadejte parametry další požadavek.|  
|[\<claimTypeRequirements >](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-element.md)|Určuje kolekci typů požadované deklarace identity.<br /><br /> V případě federovaných stavu služby požadavky na příchozí přihlašovací údaje. Například příchozí pověření musí mít sadu typy deklarací identity. Každý prvek v této kolekci Určuje typy deklarací identity požadované a volitelné očekávání měla objevit ve federované přihlašovací údaje.|  
|[\<Issuer >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuer-of-issuedtokenparameters.md)|Konfigurace element, který určuje koncového bodu, který vydá aktuální token.|  
|[\<issuerMetadata >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata-of-issuedtokenparameters.md)|Konfigurace element, který určuje adresa koncového bodu metadat vydavatel tokenu.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<secureConversationBootstrap >](../../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md)|Určuje výchozí hodnoty používané pro inicializaci služby Zabezpečené konverzaci.|  
|[\<zabezpečení >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)|Určuje možnosti zabezpečení u vlastních vazeb.|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>  
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>  
 <xref:System.ServiceModel.Configuration.SecurityElementBase.IssuedTokenParameters%2A>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [Vazby](../../../../../docs/framework/wcf/bindings.md)  
 [Rozšiřování vazeb](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Vlastní vazby](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [Postupy: vytvoření vlastní vazby pomocí elementu SecurityBindingElement](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [Zabezpečení vlastních vazeb](../../../../../docs/framework/wcf/samples/custom-binding-security.md)  
 [Identita a ověřování služby](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [Federace a vystavené tokeny](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [Možnosti zabezpečení u vlastních vazeb](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [Federace a vystavené tokeny](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
