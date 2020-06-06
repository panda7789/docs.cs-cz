---
title: Element <peerAuthentication>
ms.date: 03/30/2017
ms.assetid: 09a8a9ff-e395-42f6-8ceb-9d44bdc1cbe1
ms.openlocfilehash: 4c29c84a2cc56a890c8273e410ba31b5f3900732
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400082"
---
# <a name="peerauthentication-element"></a>Element \<peerAuthentication>
Určuje možnosti ověřování pro klienty peer-to-peer.  
  
 Další informace o programování peer-to-peer najdete v tématu [sítě peer-to-peer](../../../wcf/feature-details/peer-to-peer-networking.md).  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peer>**](peer-of-clientcredentials-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<peerAuthentication>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<peerAuthentication customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                    certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                    revocationMode="NoCheck/Online/Offline"
                    trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`customCertificateValidatorType`|Volitelný řetězec. Typ a sestavení, které slouží k ověření vlastního typu. Tento atribut musí být nastaven `certificateValidationMode` , je-li nastavena na hodnotu `Custom` .|  
|`certificateValidationMode`|Volitelný výčet. Určuje jeden ze tří režimů, který se používá k ověření přihlašovacích údajů. Je-li nastaveno na hodnotu `Custom` , `customCertificateValidator` musí být zadána také. Výchozí formát je `ChainTrust`.|  
|`revocationMode`|Volitelný výčet. Jeden z režimů, který slouží ke kontrole seznamů odvolaných certifikátů (CRL). Výchozí formát je `Online`.|  
|`trustedStoreLocation`|Volitelný výčet. Jedno ze dvou umístění úložiště systému: `LocalMachine` nebo `CurrentUser` . Tato hodnota se používá, když je certifikát služby vyjednán klientovi. Ověřování se provádí pro úložiště **důvěryhodných osob** v zadaném umístění úložiště. Výchozí formát je `CurrentUser`.|  
  
## <a name="customcertificatevalidatortype-attribute"></a>customCertificateValidatorType – atribut  
  
|Hodnota|Description|  
|-----------|-----------------|  
|Řetězec|Určuje název typu a sestavení a další data, která se používají k vyhledání typu. Je vyžadován minimální obor názvů a název typu. Volitelné informace zahrnují: název sestavení, číslo verze, jazykovou verzi a token veřejného klíče.|  
  
## <a name="certificatevalidationmode-attribute"></a>certificateValidationMode – atribut  
  
|Hodnota|Description|  
|-----------|-----------------|  
|Výčet|Jedna z následujících hodnot: `None` , `PeerTrust` , `ChainTrust` , `PeerOrChainTrust` , `Custom` . Výchozí formát je `ChainTrust`.<br /><br /> Další informace najdete v tématu [práce s certifikáty](../../../wcf/feature-details/working-with-certificates.md).|  
  
## <a name="revocationmode-attribute"></a>revocationMode – atribut  
  
|Hodnota|Description|  
|-----------|-----------------|  
|Výčet|Jedna z následujících hodnot: `NoCheck` , `Online` , `Offline` . Výchozí formát je `Online`.<br /><br /> Další informace najdete v tématu [práce s certifikáty](../../../wcf/feature-details/working-with-certificates.md).|  
  
## <a name="trustedstorelocation-attribute"></a>trustedStoreLocation – atribut  
  
|Hodnota|Description|  
|-----------|-----------------|  
|Výčet|Jedna z následujících hodnot: `LocalMachine` nebo `CurrentUser` . Výchozí formát je `CurrentUser`. Pokud klientská aplikace běží pod účtem systému, certifikát se obvykle nachází v části `LocalMachine` . Pokud klientská aplikace běží pod uživatelským účtem, bude certifikát typicky v `CurrentUser` .|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<peer>](peer-of-clientcredentials-element.md)|Určuje přihlašovací údaje, které se používají k ověřování klienta pro partnerských služeb.|  
  
## <a name="remarks"></a>Poznámky  
 `<authentication>`Prvek odpovídá <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> třídě. Tento prvek určuje validátor, který je vyvolán při ověřování typu Neighbor-to-Neighbor v síti. Když se nový partner pokusí vytvořit sousední připojení, předá partnerskému partnerovi své vlastní přihlašovací údaje. K ověření přihlašovacích údajů vzdálené strany se vyvolá validátor daného respondéru. Pokaždé, když je v síti navázáno připojení typu peer, oba partneři se vzájemně ověřují, což znamená, že jsou vyvolány validátory na obou koncích.  
  
## <a name="example"></a>Příklad  
 Následující kód nastaví režim ověřování certifikátu na `PeerOrChainTrust` .  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="MyEndpointBehavior">
      <clientCredentials>
        <peer>
          <certificate findValue="www.contoso.com"
                       storeLocation="LocalMachine"
                       x509FindType="FindByIssuerName" />
          <peerAuthentication certificateValidationMode="PeerOrChainTrust" />
          <messageSenderAuthentication certificateValidationMode="None" />
        </peer>
      </clientCredentials>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.PeerAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.PeerAuthentication%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- [Práce s certifikáty](../../../wcf/feature-details/working-with-certificates.md)
- [Síť rovnocenných počítačů](../../../wcf/feature-details/peer-to-peer-networking.md)
- [Ověřování zpráv rovnocenného kanálu](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))
- [Vlastní ověřování rovnocenných kanálů](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))
- [Zabezpečení aplikací rovnocenného kanálu](../../../wcf/feature-details/securing-peer-channel-applications.md)
