---
title: Element &lt;peerAuthentication&gt;
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 09a8a9ff-e395-42f6-8ceb-9d44bdc1cbe1
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: eed1bac41babb970e3d85a8ae1aa5132f44e3621
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltpeerauthenticationgt-element"></a>Element &lt;peerAuthentication&gt;
Určuje možnosti ověřování pro klienty peer-to-peer.  
  
 [!INCLUDE[crabout](../../../../../includes/crabout-md.md)]programování, viz peer-to-peer [Peer-to-Peer sítě](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).  
  
 \<systém. ServiceModel >  
\<chování >  
\<endpointBehaviors >  
\<chování >  
\<clientCredentials >  
\<sdílené >  
\<PeerAuthentication >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<peerAuthentication  
customCertificateValidatorType = "namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"  
certificateValidationMode = "ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"  
revocationMode="NoCheck/Online/Offline"  
trustedStoreLocation="CurrentUser/LocalMachine"   
/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují nadřazené elementy, atributy a podřízené elementy  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`customCertificateValidatorType`|Volitelný řetězec. Typ a sestavení, které slouží k ověření vlastního typu. Tento atribut musí být nastaven při `certificateValidationMode` je nastaven na `Custom`.|  
|`certifcateValidationMode`|Volitelné výčtu. Určuje jeden ze tří režimů slouží k ověření přihlašovacích údajů. Pokud nastavena na `Custom`, pak `customCertificateValidator` musí být uveden také. Výchozí hodnota je `ChainTrust`.|  
|`revocationMode`|Volitelné výčtu. Jeden z režimů používá k ověření pro seznamy odvolaných certifikátů (CRL). Výchozí hodnota je `Online`.|  
|`trustedStoreLocation`|Volitelné výčtu. Jedno z umístění úložiště dvě systému: `LocalMachine` nebo `CurrentUser`. Tato hodnota se používá, když je klientovi vyjednal certifikát služby. Ověření se provádí před **důvěryhodné osoby** uložit do umístění zadaného úložiště. Výchozí hodnota je `CurrentUser`.|  
  
## <a name="customcertificatevalidatortype-attribute"></a>customCertificateValidatorType atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|String|Určuje název typu a sestavení a další data použít k vyhledání typu. Název oboru názvů a typ se minimálně, vyžadují. Volitelné informace zahrnují: název sestavení, číslo verze, jazykové verze a tokenu veřejného klíče.|  
  
## <a name="certificatevalidationmode-attribute"></a>certificateValidationMode atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|Výčet|Jeden z následujících hodnot: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`. Výchozí hodnota je `ChainTrust`.<br /><br /> Další informace najdete v tématu [práce s certifikáty](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).|  
  
## <a name="revocationmode-attribute"></a>revocationMode atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|Výčet|Jeden z následujících hodnot: `NoCheck`, `Online`, `Offline`. Výchozí hodnota je `Online`.<br /><br /> Další informace najdete v tématu [práce s certifikáty](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).|  
  
## <a name="trustedstorelocation-attribute"></a>trustedStoreLocation atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|Výčet|Jeden z následujících hodnot: `LocalMachine` nebo `CurrentUser`. Výchozí hodnota je `CurrentUser`. Pokud klientská aplikace běží pod účtem systému pak certifikát je obvykle v části `LocalMachine`. Pokud klientská aplikace běží pod účtem uživatele, pak tento certifikát je obvykle v `CurrentUser`.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<sdílené >](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-clientcredentials-element.md)|Určí pověření používaná pro ověřování klienta do sdílené služby.|  
  
## <a name="remarks"></a>Poznámky  
 `<authentication>` Element odpovídá <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> třídy. Tento element určuje validátor, která se vyvolá při ověřování sousedním sousedním v mřížce. Když se nové sdílené pokusí navázat připojení sousedním, předá vlastní pověření na odpovídá partnera. Validátor odpovídající partner je vyvolána k ověření pověření vzdálené strany. Při každém navázání připojení sdílené v mřížce, oba partneři jsou vzájemně ověřeni, jsou vyvolány význam validátory na obou koncích.  
  
## <a name="example"></a>Příklad  
 Následující kód nastaví režim ověření certifikátu na `PeerOrChainTrust`.  
  
```xml  
<behaviors>  
 <endpointBehaviors>  
  <behavior name="MyEndpointBehavior">  
   <clientCredentials>  
    <peer>  
     <certificate findValue="www.contoso.com"   
                   storeLocation="LocalMachine"  
                   x509FindType="FindByIssuerName" />  
     <peerAuthentication   
          certificateValidationMode="PeerOrChainTrust" />  
     <messageSenderAuthentication certificateValidationMode="None" />  
    </peer>  
   </clientCredentials>  
  </behavior>  
</endpointBehaviors>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement>  
 <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>  
 <xref:System.ServiceModel.Security.PeerCredential.PeerAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement.PeerAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>  
 [Práce s certifikáty](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [Síť rovnocenných počítačů](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [Ověřování zpráv rovnocenného kanálu](http://msdn.microsoft.com/en-us/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [Vlastní ověřování rovnocenného kanálu](http://msdn.microsoft.com/en-us/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [Zabezpečení aplikací protokolu Peer Channel](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
