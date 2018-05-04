---
title: '&lt;secureConversationBootstrap&gt;'
ms.date: 03/30/2017
ms.assetid: 66b46f95-fa2d-4b5b-b6ce-0572ab0cdd50
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: f7eab333899f5fc379db8fb5683ea3d29d04943c
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltsecureconversationbootstrapgt"></a>&lt;secureConversationBootstrap&gt;
Určuje výchozí hodnoty používané pro inicializaci služby Zabezpečené konverzaci.  
  
 \<system.serviceModel>  
\<vazby >  
\<customBinding >  
\<Vazba >  
\<zabezpečení >  
\<secureConversationBootstrap >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<secureConversationBootstrap  
   allowSerializedSigningTokenOnReply="Boolean"  
   authenticationMode="AuthenticationMode"  
   defaultAlgorithmSuite="SecurityAlgorithmSuite"  
   includeTimestamp="Boolean"  
   requireDerivedKeys="Boolean"  
   keyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"   
messageProtectionOrder="SignBeforeEncrypt/SignBeforeEncryptAndEncryptSignature/EncryptBeforeSign"  
   messageSecurityVersion="WSSecurityJan2004/WSSecurityXXX2005"  
   requireDerivedKeys="Boolean"  
   requireSecurityContextCancellation="Boolean"  
   requireSignatureConfirmation="Boolean" >  
   securityHeaderLayout="Strict/Lax/LaxTimestampFirst/LaxTimestampLast"  
   includeTimestamp="Boolean" />  
```  
  
## <a name="type"></a>Typ  
 `Type`  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`allowSerializedSigningTokenOnReply`|Volitelné. Logická hodnota, která určuje, pokud serializovaný token lze použít v odpovědi. Výchozí hodnota je `false`. Při použití duální vazby, nastavení výchozí hodnotu `true` všechna nastavení provedené budou ignorovány.|  
|`authenticationMode`|Určuje režim ověřování protokolu SOAP používá mezi iniciátoru a odpovídající počítač.<br /><br /> Výchozí hodnota je sspiNegotiated.<br /><br /> Tento atribut je typu <xref:System.ServiceModel.Configuration.AuthenticationMode>.|  
|`defaultAlgorithmSuite`|Sada algoritmů zabezpečení definuje z různých algoritmů, například kanonizace, ověřování algoritmem Digest, KeyWrap, podpisu, šifrování a algoritmy KeyDerivation. Všechny sady algoritmus zabezpečení definuje hodnoty pro tyto různé parametry. Zabezpečení na základě zpráv se opírá tyto algoritmy.<br /><br /> Tento atribut se používá při práci s jinou platformu, která požádá sady algoritmů, které jsou jiné než výchozí. Byste měli být vědomi silné a slabé stránky relevantní algoritmů při provádění změn tohoto nastavení. Tento atribut je typu <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>. Výchozí hodnota je `Basic256`.|  
|`includeTimestamp`|Logická hodnota, která určuje, zda časová razítka jsou zahrnuta v každé zprávě. Výchozí hodnota je `true`.|  
|`keyEntropyMode`|Určuje způsob, že se vypočítávají klíče pro zabezpečení zpráv. Klíče může být založen na klienta materiál klíče pouze na služby materiál klíče pouze nebo jejich kombinaci. Platné hodnoty jsou:<br /><br /> -ClientEntropy: Klíč relace je založena na zadaný materiál klíče klienta.<br />-ServerEntropy: Klíč relace je založena na službu poskytovanou materiál klíče.<br />-CombinedEntropy: Klíč relace je založena na klienta a služby poskytuje klíčový materiál.<br /><br /> Výchozí hodnota je CombinedEntropy.<br /><br /> Tento atribut je typu <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.|  
|`messageProtectionOrder`|Nastaví pořadí, ve zpráv, které jsou použity algoritmy úrovně zabezpečení ke zprávě. Platné hodnoty patří:<br /><br /> -SignBeforeEncrypt: Nejdřív přihlásit a šifrování.<br />-SignBeforeEncryptAndEncryptSignature: Podepisování, šifrování a šifrování podpis.<br />-EncryptBeforeSign: Šifrování nejprve a pak přihlásit.<br /><br /> SignBeforeEncryptAndEncryptSignature je výchozí hodnota při vzájemnými certifikáty pomocí protokolu WS-zabezpečení 1.1.  SignBeforeEncrypt je výchozí hodnota se WS-Security 1.0.<br /><br /> Tento atribut je typu <xref:System.ServiceModel.Security.MessageProtectionOrder>.|  
|`messageSecurityVersion`|Nastaví verzi protokolu WS-zabezpečení, který se používá. Platné hodnoty patří:<br /><br /> -WSSecurityJan2004<br />-WSSecurityXXX2005<br /><br /> Výchozí hodnota je WSSecurityXXX2005. Tento atribut je typu <xref:System.ServiceModel.MessageSecurityVersion>.|  
|`requireDerivedKeys`|Logická hodnota, která určuje, zda klíčů může být odvozen od původního doklad klíče. Výchozí hodnota je `true`.|  
|`requireSecurityContextCancellation`|Logická hodnota, která určuje, jestli kontext zabezpečení by měl být zrušena a byla ukončena, pokud se už nevyžaduje. Výchozí hodnota je `true`.|  
|`requireSignatureConfirmation`|Logická hodnota, která určuje, zda je povoleno potvrzení podpisu WS-zabezpečení. Pokud nastavíte hodnotu `true`, podpisy zpráv potvrdí odpovídající partner. Výchozí hodnota je `false`.<br /><br /> Potvrzení podpisu se používá pro potvrzení, zda služba reaguje v úplné povědomí o požadavek.|  
|`securityHeaderLayout`|Určuje pořadí prvků v záhlaví zabezpečení. Platné hodnoty jsou:<br /><br /> -Strict. Položky budou přidány do záhlaví zabezpečení podle obecné zásady "deklarovat před použitím".<br />-Hodnotě lax. Položky budou přidány do záhlaví zabezpečení v libovolném pořadí, který potvrdí k WSS: zabezpečení protokolu SOAP zprávy.<br />-LaxWithTimestampFirst. Položky budou přidány do záhlaví zabezpečení v libovolném pořadí, který potvrdí k WSS: zabezpečení zpráv protokolu SOAP s tím rozdílem, že prvním elementem v záhlaví zabezpečení musí být wsse:Timestamp element.<br />-LaxWithTimestampLast. Položky budou přidány do záhlaví zabezpečení v libovolném pořadí, který potvrdí k WSS: zabezpečení zpráv protokolu SOAP s tím rozdílem, že posledním prvkem v záhlaví zabezpečení musí být wsse:Timestamp element.<br /><br /> Výchozí hodnota je Strict.<br /><br /> Tento element je typu <xref:System.ServiceModel.Channels.SecurityHeaderLayout>.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<– issuedTokenParameters >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md)|Určuje aktuální vystavený token. Tento element je typu <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>.|  
|[\<localClientSettings >](../../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md)|Určuje nastavení zabezpečení místního klienta pro tuto vazbu. Tento element je typu <xref:System.ServiceModel.Configuration.LocalClientSecuritySettingsElement>.|  
|[\<localServiceSettings >](../../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md)|Určuje nastavení zabezpečení na místní služby pro tuto vazbu. Tento element je typu <xref:System.ServiceModel.Configuration.LocalServiceSecuritySettingsElement>.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<zabezpečení >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)|Určuje možnosti zabezpečení u vlastních vazeb.|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.LocalServiceSecuritySettingsElement>  
 <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A>  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [Vazby](../../../../../docs/framework/wcf/bindings.md)  
 [Rozšíření vazeb](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Vlastní vazby](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [Postupy: Vytvoření vlastní vazby pomocí SecurityBindingElement](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [Zabezpečení vlastních vazeb](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
