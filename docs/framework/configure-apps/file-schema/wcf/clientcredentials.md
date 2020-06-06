---
title: <clientCredentials>
ms.date: 03/30/2017
ms.assetid: 1e6eef0d-a34e-4d74-b0f7-f65d2181858d
ms.openlocfilehash: f295fe48e194611c80b78c0c23ab3e66ea1c0b64
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400500"
---
# \<clientCredentials>
Určuje přihlašovací údaje, které se používají k ověření klienta ke službě.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clientCredentials>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<clientCredentials type="String"
                   supportInteractive="Boolean" >
  <clientCertificate>
  </clientCertificate>
  <digest>
  </digest>
  <isuedToken>
  </isuedToken>
  <peer>
  </peer>
  <serviceCertificate>
  </serviceCertificate>
  <windowsAuthentication>
  </windowsAuthentication>
</clientCredentials>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`supportInteractive`|Logická hodnota určující, zda může být interaktivní uživatel zapojen do výběru přihlašovacích údajů klienta za běhu. Výchozí hodnota je `true`.|  
|`type`|Řetězec, který určuje typ tohoto konfiguračního prvku.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<clientCertificate>](clientcertificate-of-clientcredentials-element.md)|Určuje certifikát, který se používá k ověření klienta ke službě. Tento prvek je typu <xref:System.ServiceModel.Configuration.X509InitiatorCertificateClientElement> .|  
|[\<httpDigest>](httpdigest-element.md)|Určuje výtah, který se používá k ověření klienta ke službě. Tento prvek je typu <xref:System.ServiceModel.Configuration.HttpDigestClientElement> .|  
|[\<issuedToken>](issuedtoken.md)|Určuje vlastní typ tokenu, který se používá k ověření klienta ke službě tokenů zabezpečení (STS). Tento prvek je typu <xref:System.ServiceModel.Configuration.IssuedTokenClientElement> .|  
|[\<peer>](peer-of-clientcredentials-element.md)|Určuje aktuální přihlašovací údaje partnerského vztahu. Tento prvek je typu <xref:System.ServiceModel.Configuration.PeerCredentialElement> .|  
|[\<serviceCertificate>](servicecertificate-of-clientcredentials-element.md)|Určuje certifikát použitý k ověření služby klientovi a poskytuje strukturu pro nastavení možností certifikátu. Tento certifikát musí být dodán od služby ke klientovi. Tento prvek je typu <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement> .|  
|[\<windows>](windows-of-clientcredentials-element.md)|Určuje pověření systému Windows. Výchozí hodnota je přihlašovací údaje aktuálního vlákna. Tento prvek je typu <xref:System.ServiceModel.Configuration.WindowsClientElement> .|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|Určuje chování koncového bodu.|  
  
## <a name="remarks"></a>Poznámky  
 Pověření klienta slouží k ověřování klienta se službami v případech, kdy je nutné vzájemné ověřování. Tento oddíl konfigurace lze také použít k určení certifikátů služby pro scénáře, ve kterých musí klient zabezpečit zprávy do služby pomocí certifikátu služby.  
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- [Chování zabezpečení](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [Zabezpečení klientů](../../../wcf/securing-clients.md)
