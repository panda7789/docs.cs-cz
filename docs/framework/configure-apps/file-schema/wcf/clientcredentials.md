---
title: <clientCredentials>
ms.date: 03/30/2017
ms.assetid: 1e6eef0d-a34e-4d74-b0f7-f65d2181858d
ms.openlocfilehash: 7ee49d6960864826dc74fbff629f502fcc70b4bf
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55254805"
---
# <a name="clientcredentials"></a>\<clientCredentials>
Určuje pověření pro ověření klienta ke službě.  
  
 \<system.ServiceModel>  
\<chování >  
\<endpointBehaviors>  
\<chování >  
\<clientCredentials>  
  
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
|`supportInteractive`|Logická hodnota, která určuje, zda může být interaktivní uživatelské součástí výběru pověření klienta za běhu. Výchozí hodnota je `true`.|  
|`type`|Řetězec, který určuje typ tohoto konfiguračního prvku.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<clientCertificate>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md)|Určuje certifikát používaný k ověření klienta ke službě. Tento prvek je typu <xref:System.ServiceModel.Configuration.X509InitiatorCertificateClientElement>.|  
|[\<httpDigest>](../../../../../docs/framework/configure-apps/file-schema/wcf/httpdigest-element.md)|Určuje algoritmu digest pro ověření klienta ke službě. Tento prvek je typu <xref:System.ServiceModel.Configuration.HttpDigestClientElement>.|  
|[\<issuedToken>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md)|Určuje vlastní typ tokenu pro ověření klienta k zabezpečení tokenu služby (STS). Tento prvek je typu <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>.|  
|[\<peer>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-clientcredentials-element.md)|Určuje aktuální peer pověření. Tento prvek je typu <xref:System.ServiceModel.Configuration.PeerCredentialElement>.|  
|[\<serviceCertificate>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md)|Určuje certifikát používaný k ověřování klienta a poskytuje strukturu pro nastavení možnosti certifikátu. Tento certifikát musí být zadaný out-of-band ze služby ke klientovi. Tento prvek je typu <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>.|  
|[\<windows>](../../../../../docs/framework/configure-apps/file-schema/wcf/windows-of-clientcredentials-element.md)|Určuje přihlašovací údaje Windows. Výchozí hodnota je přihlašovacích údajů aktuálního vlákna. Tento prvek je typu <xref:System.ServiceModel.Configuration.WindowsClientElement>.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<behavior>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Určuje chování koncového bodu.|  
  
## <a name="remarks"></a>Poznámky  
 Přihlašovací údaje pro klienta se používají k ověření klienta ke službám v případech, kdy je vyžaduje vzájemné ověřování. Tento oddíl konfigurace lze také určení certifikátů služby pro scénáře, ve kterém musí klient zabezpečené zprávy do služby pomocí certifikátu služby.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- [Chování zabezpečení](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [Zabezpečení klientů](../../../../../docs/framework/wcf/securing-clients.md)
