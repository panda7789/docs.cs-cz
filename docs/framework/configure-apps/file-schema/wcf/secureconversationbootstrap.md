---
title: <secureConversationBootstrap>
ms.date: 03/30/2017
ms.assetid: 66b46f95-fa2d-4b5b-b6ce-0572ab0cdd50
ms.openlocfilehash: b3187cb51b6fd32797c9ad401c704d5f16c6f7e8
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399911"
---
# <a name="secureconversationbootstrap"></a>\<secureConversationBootstrap>
Určuje výchozí hodnoty, které se použijí při inicializaci služby zabezpečené konverzace.  
  
[ **\<> Konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> vazeb**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> vazby**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zabezpečení**](security-of-custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<secureConversationBootstrap >**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<secureConversationBootstrap allowSerializedSigningTokenOnReply="Boolean"
                             authenticationMode="AuthenticationMode"
                             defaultAlgorithmSuite="SecurityAlgorithmSuite"
                             includeTimestamp="Boolean"
                             requireDerivedKeys="Boolean"
                             keyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"
                             messageProtectionOrder="SignBeforeEncrypt/SignBeforeEncryptAndEncryptSignature/EncryptBeforeSign"
                             messageSecurityVersion="WSSecurityJan2004/WSSecurityXXX2005"
                             requireDerivedKeys="Boolean"
                             requireSecurityContextCancellation="Boolean"
                             requireSignatureConfirmation="Boolean"
                             securityHeaderLayout="Strict/Lax/LaxTimestampFirst/LaxTimestampLast"
                             includeTimestamp="Boolean" />
```  
  
## <a name="type"></a>type  
 `Type`  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`allowSerializedSigningTokenOnReply`|Volitelný parametr. Logická hodnota, která určuje, zda lze pro odpověď použít serializovaný token. Výchozí hodnota je `false`. Při použití duální vazby se nastavení nastaví jako výchozí pro `true` všechna nastavení, která se budou ignorovat.|  
|`authenticationMode`|Určuje režim ověřování SOAP, který se používá mezi iniciátorem a respondérem.<br /><br /> Výchozí hodnota je sspiNegotiated.<br /><br /> Tento atribut je typu <xref:System.ServiceModel.Configuration.AuthenticationMode>.|  
|`defaultAlgorithmSuite`|Sada algoritmů zabezpečení definuje celou řadu algoritmů, jako je například kanonikalizace, Digest, zabalení, podpis, šifrování a algoritmy odvození. Jednotlivé sady algoritmů zabezpečení definují hodnoty pro tyto různé parametry. Zabezpečení založené na zprávách se dosahuje pomocí těchto algoritmů.<br /><br /> Tento atribut se používá při práci s jinou platformou, která se výslovný pro sadu algoritmů, která se liší od výchozí hodnoty. Při provádění úprav tohoto nastavení byste měli být vědomi síly a slabých stránek relevantních algoritmů. Tento atribut je typu <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>. Výchozí hodnota je `Basic256`.|  
|`includeTimestamp`|Logická hodnota, která určuje, zda jsou časová razítka obsažena v každé zprávě. Výchozí hodnota je `true`.|  
|`keyEntropyMode`|Určuje způsob výpočtu klíčů pro zabezpečení zpráv. Klíče můžou být založené jenom na materiálech klientského klíče, jenom v materiálech klíče služby nebo v kombinaci obou. Platné hodnoty jsou:<br /><br /> - ClientEntropy: Klíč relace je založen na klíčovém materiálu poskytnutém klientem.<br />- ServerEntropy: Klíč relace je založen na službě, která poskytuje klíčový materiál.<br />- CombinedEntropy: Klíč relace je založen na obsahu klíče, který poskytuje klient a služba.<br /><br /> Výchozí hodnota je CombinedEntropy.<br /><br /> Tento atribut je typu <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.|  
|`messageProtectionOrder`|Nastaví pořadí, ve kterém jsou pro zprávu aplikovány algoritmy zabezpečení na úrovni zprávy. Platné hodnoty jsou následující:<br /><br /> - SignBeforeEncrypt: Nejdřív se podepište a pak zašifrujte.<br />- SignBeforeEncryptAndEncryptSignature: Podepsání, šifrování a šifrování podpisu.<br />- EncryptBeforeSign: Nejprve Zašifrujte a pak podepište.<br /><br /> SignBeforeEncryptAndEncryptSignature je výchozí hodnota při použití vzájemného certifikátu s WS-Security 1,1.  SignBeforeEncrypt je výchozí hodnota s WS-Security 1,0.<br /><br /> Tento atribut je typu <xref:System.ServiceModel.Security.MessageProtectionOrder>.|  
|`messageSecurityVersion`|Nastaví verzi WS-Security, která se používá. Platné hodnoty jsou následující:<br /><br /> – WSSecurityJan2004<br />- WSSecurityXXX2005<br /><br /> Výchozí hodnota je WSSecurityXXX2005. Tento atribut je typu <xref:System.ServiceModel.MessageSecurityVersion>.|  
|`requireDerivedKeys`|Logická hodnota, která určuje, zda mohou být klíče odvozeny z původních ověřovacích klíčů. Výchozí hodnota je `true`.|  
|`requireSecurityContextCancellation`|Logická hodnota určující, zda má být kontext zabezpečení zrušen a ukončen, pokud již není požadován. Výchozí hodnota je `true`.|  
|`requireSignatureConfirmation`|Logická hodnota, která určuje, zda je povoleno potvrzení podpisu WS-Security. Když je nastavené na `true`, příjemce potvrdí podpisy zpráv. Výchozí hodnota je `false`.<br /><br /> Potvrzení podpisu se používá k potvrzení, že služba reaguje v plné povědomí o žádosti.|  
|`securityHeaderLayout`|Určuje pořadí prvků v záhlaví zabezpečení. Platné hodnoty jsou:<br /><br /> Zásadní. Položky jsou přidány do záhlaví zabezpečení podle obecné zásady deklarace před použitím.<br />LAX. Položky se přidají do záhlaví zabezpečení v libovolném pořadí, které potvrdí na WSS: Zabezpečení zprávy SOAP.<br />- LaxWithTimestampFirst. Položky se přidají do záhlaví zabezpečení v libovolném pořadí, které potvrdí na WSS: Zabezpečení zprávy SOAP s výjimkou toho, že první prvek v záhlaví zabezpečení musí být element wsse: Timestamp.<br />- LaxWithTimestampLast. Položky se přidají do záhlaví zabezpečení v libovolném pořadí, které potvrdí na WSS: Zabezpečení zprávy SOAP s výjimkou toho, že poslední prvek v záhlaví zabezpečení musí být element wsse: Timestamp.<br /><br /> Výchozí hodnota je Strict.<br /><br /> Tento prvek je typu <xref:System.ServiceModel.Channels.SecurityHeaderLayout>.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<issuedTokenParameters>](issuedtokenparameters.md)|Určuje aktuální vydaný token. Tento prvek je typu <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>.|  
|[\<localClientSettings>](localclientsettings-element.md)|Určuje nastavení zabezpečení místního klienta pro tuto vazbu. Tento prvek je typu <xref:System.ServiceModel.Configuration.LocalClientSecuritySettingsElement>.|  
|[\<localServiceSettings>](localservicesettings-element.md)|Určuje nastavení zabezpečení místní služby pro tuto vazbu. Tento prvek je typu <xref:System.ServiceModel.Configuration.LocalServiceSecuritySettingsElement>.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<> zabezpečení](security-of-custombinding.md)|Určuje možnosti zabezpečení pro vlastní vazbu.|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.LocalServiceSecuritySettingsElement>
- <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A>
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Vazby](../../../wcf/bindings.md)
- [Rozšíření vazeb](../../../wcf/extending/extending-bindings.md)
- [Vlastní vazby](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [Postupy: Vytvoření vlastní vazby pomocí SecurityBindingElement](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [Zabezpečení vlastních vazeb](../../../wcf/samples/custom-binding-security.md)
