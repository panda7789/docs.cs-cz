---
title: <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 96db336c-4f7a-4193-81a5-910b8ffd804f
ms.openlocfilehash: 90a34a4a52b4c7a2e67d733fecba132818cac4fc
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399658"
---
# \<serviceCredentials>
Určuje přihlašovací údaje, které se mají použít při ověřování služby a nastavení vztahující se k ověření přihlašovacích údajů klienta.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceCredentials>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<serviceCredentials type="String">
  <clientCertificate>
  </clientCertificate>
  <issuedTokenAuthentication>
  </issuedTokenAuthentication>
  <peer>
  </peer>
  <secureConversationAuthentication>
  </secureConversationAuthentication>
  <serviceCertificate>
  </serviceCertificate>
  <userNameAuthentication>
  </userNameAuthentication>
  <windowsAuthentication>
  </windowsAuthentication>
</serviceCredentials>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`type`|Řetězec, který určuje typ tohoto konfiguračního prvku.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<clientCertificate>](clientcertificate-of-servicecredentials.md)|Určuje certifikát, který má být použit v případě, že je klientský certifikát k dispozici mimo IP síť. Tento prvek také určuje nastavení ověřování klientského certifikátu. Tento prvek je typu <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement> .|  
|[\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md)|Určuje aktuální vydaný token pro tuto službu. Tento prvek je typu <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement> .|  
|[\<peer>](peer-of-servicecredentials.md)|Určuje aktuální pověření pro partnerský uzel. Tento prvek je typu <xref:System.ServiceModel.Configuration.PeerCredentialElement> .|  
|[\<secureConversationAuthentication>](secureconversationauthentication-of-servicecredential.md)|Určuje aktuální pověření pro zabezpečenou konverzaci. Tento prvek je typu <xref:System.ServiceModel.Configuration.SecureConversationServiceElement> .|  
|[\<serviceCertificate>](servicecertificate-of-servicecredentials.md)|Určuje certifikát používaný službou k identifikaci sebe sama. Tento prvek je typu <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement> .|  
|[\<userNameAuthentication>](usernameauthentication.md)|Určuje nastavení pro ověřování hesla uživatelského jména. Tento prvek je typu <xref:System.ServiceModel.Configuration.UserNameServiceElement> .|  
|[\<windowsAuthentication>](windowsauthentication-of-servicecredentials.md)|Určuje nastavení pro ověření přihlašovacích údajů systému Windows. Tento prvek je typu <xref:System.ServiceModel.Configuration.WindowsServiceElement> .|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|Určuje chování element.|  
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement>
- <xref:System.ServiceModel.Description.ServiceCredentials>
- [Chování zabezpečení](../../../wcf/feature-details/security-behaviors-in-wcf.md)
