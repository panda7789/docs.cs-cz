---
title: Element &lt;peerAuthentication&gt;
ms.date: 03/30/2017
ms.assetid: 09a8a9ff-e395-42f6-8ceb-9d44bdc1cbe1
ms.openlocfilehash: 4fb8cc4989313afa3ef16c90b54e0feae1ccb71d
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44180238"
---
# <a name="ltpeerauthenticationgt-element"></a>Element &lt;peerAuthentication&gt;
Určuje možnosti ověřování klientů peer-to-peer.  
  
 Další informace o programování peer-to-peer, naleznete v tématu [sítě Peer-to-Peer](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).  
  
 \<system.ServiceModel>  
\<chování >  
\<názvy endpointBehaviors >  
\<chování >  
\<třídu clientCredentials >  
\<sdílená >  
\<peerAuthentication >  
  
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
 Následující části popisují atributy, podřízené prvky a nadřazené elementy  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`customCertificateValidatorType`|Volitelný řetězec. Typ a sestavení používané pro ověření vlastního typu. Tento atribut musí být nastaven při `certificateValidationMode` je nastavena na `Custom`.|  
|`certifcateValidationMode`|Volitelný výčet. Určuje jeden ze tří režimů používaných pro ověření pověření. Pokud hodnotu `Custom`, o `customCertificateValidator` musí být rovněž dodán. Výchozí hodnota je `ChainTrust`.|  
|`revocationMode`|Volitelný výčet. Jeden z režimů pro kontrolu seznamu odvolaných certifikátů (CRL). Výchozí hodnota je `Online`.|  
|`trustedStoreLocation`|Volitelný výčet. Jeden z umístění dvou systémových úložišť: `LocalMachine` nebo `CurrentUser`. Tato hodnota se používá při certifikát služby se vyjedná do klienta. Ověření se provádí proti **důvěryhodné osoby** uložit do umístění určeného úložiště. Výchozí hodnota je `CurrentUser`.|  
  
## <a name="customcertificatevalidatortype-attribute"></a>customCertificateValidatorType atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|String|Určuje název typu a sestavení a další data použít k vyhledání typu. Minimálně název oboru názvů a typ jsou požadovány. Volitelné informace zahrnují: název sestavení, číslo verze, jazykovou verzi a token veřejného klíče.|  
  
## <a name="certificatevalidationmode-attribute"></a>certificateValidationMode atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|Výčet|Jeden z následujících hodnot: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`. Výchozí hodnota je `ChainTrust`.<br /><br /> Další informace najdete v tématu [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).|  
  
## <a name="revocationmode-attribute"></a>revocationMode atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|Výčet|Jeden z následujících hodnot: `NoCheck`, `Online`, `Offline`. Výchozí hodnota je `Online`.<br /><br /> Další informace najdete v tématu [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).|  
  
## <a name="trustedstorelocation-attribute"></a>trustedStoreLocation atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|Výčet|Jeden z následujících hodnot: `LocalMachine` nebo `CurrentUser`. Výchozí hodnota je `CurrentUser`. Pokud klientská aplikace běží pod účtem systému, certifikátu je obvykle pod `LocalMachine`. Pokud klientská aplikace běží pod účtem uživatele, že certifikát je obvykle v `CurrentUser`.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<peer>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-clientcredentials-element.md)|Určuje pověření pro ověření klienta ke službě partnera.|  
  
## <a name="remarks"></a>Poznámky  
 `<authentication>` Odpovídá elementu <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> třídy. Tento prvek určuje ověřování, které se vyvolá při ověřování sousední souseda v mřížce. Nový partnerský uzel pokusí navázat připojení k sousedovi, předá odpovídá peer své vlastní přihlašovací údaje. Validátor odpovídajícího objektu je vyvolán k ověření přihlašovacích údajů vzdálené strany. Při každém navázání připojení partnera v mřížce, jak partnerské uzly jsou vzájemně se ověřují, jsou vyvolány význam validátory na obou koncích.  
  
## <a name="example"></a>Příklad  
 Následující kód nastaví režim ověřování certifikátu `PeerOrChainTrust`.  
  
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
 [Ověřování zpráv protokolu peer Channel](https://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [Vlastní ověřování protokolu peer Channel](https://msdn.microsoft.com/library/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [Zabezpečení aplikací protokolu Peer Channel](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
