---
title: '&lt;clientCredentials&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1e6eef0d-a34e-4d74-b0f7-f65d2181858d
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: eaf46953d7b2c3f89e1f5b107dc9ddf5d1597875
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltclientcredentialsgt"></a>&lt;clientCredentials&gt;
Určuje pověření, která používá k ověření klienta ke službě.  
  
 \<systém. ServiceModel >  
\<chování >  
\<endpointBehaviors >  
\<chování >  
\<clientCredentials >  
  
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
|`supportInteractive`|Logická hodnota, která určuje, zda může být při výběru pověření klienta v době běhu zapojeno interaktivního uživatele. Výchozí hodnota je `true`.|  
|`type`|Řetězec, který určuje typ tohoto elementu konfigurace.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<clientCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md)|Určuje certifikát používaný k ověření klienta ke službě. Tento element je typu <xref:System.ServiceModel.Configuration.X509InitiatorCertificateClientElement>.|  
|[\<httpDigest >](../../../../../docs/framework/configure-apps/file-schema/wcf/httpdigest-element.md)|Určuje hodnotou hash používá k ověření klienta ke službě. Tento element je typu <xref:System.ServiceModel.Configuration.HttpDigestClientElement>.|  
|[\<issuedToken >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md)|Určuje vlastní typ tokenu, který používá k ověření klienta k zabezpečení tokenu služby (STS). Tento element je typu <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>.|  
|[\<sdílené >](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-clientcredentials-element.md)|Určuje aktuální přihlašovací údaje partnera. Tento element je typu <xref:System.ServiceModel.Configuration.PeerCredentialElement>.|  
|[\<serviceCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md)|Určuje certifikát používaný k ověřování klienta a poskytuje strukturu pro nastavení možností certifikátu. Tento certifikát musí být zadaný out-of-band ze služby do klienta. Tento element je typu <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>.|  
|[\<Windows >](../../../../../docs/framework/configure-apps/file-schema/wcf/windows-of-clientcredentials-element.md)|Určuje pověření systému Windows. Výchozí hodnota je přihlašovací údaje aktuálního vlákna. Tento element je typu <xref:System.ServiceModel.Configuration.WindowsClientElement>.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<chování >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Určuje chování koncového bodu.|  
  
## <a name="remarks"></a>Poznámky  
 Pověření klienta slouží k ověření klienta ke službám v případech, kdy je potřeba vzájemné ověřování. Tento oddíl konfigurace mohou sloužit také k určení certifikáty služby pro scénáře, kde klient musíte zabezpečit zprávy služby pomocí certifikátu služby.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 [Chování zabezpečení](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [Zabezpečení klientů](../../../../../docs/framework/wcf/securing-clients.md)
