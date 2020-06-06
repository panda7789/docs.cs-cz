---
title: <messageSenderAuthentication> – element
ms.date: 03/30/2017
ms.assetid: 8d979dfc-a6f9-42ec-96d5-7fbc13a48118
ms.openlocfilehash: bab0e50d7feba3ea55d505be07cfa41427a5cbbc
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70397779"
---
# <a name="messagesenderauthentication-element"></a>\<messageSenderAuthentication> – element
Určuje možnosti ověřování pro odesílatele zpráv peer-to-peer.  
  
 Další informace o programování peer-to-peer najdete v tématu [sítě peer-to-peer](../../../wcf/feature-details/peer-to-peer-networking.md).  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peer>**](peer-of-clientcredentials-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<messageSenderAuthentication>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<messageSenderAuthentication customCertificateValidatorType= "namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                             certificateValidationMode = "ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                             revocationMode="NoCheck/Online/Offline"
                             trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`customCertificateValidatorType`|Typ a sestavení, které slouží k ověření vlastního typu. Tento atribut musí být nastaven `certificateValidationMode` , je-li nastavena na hodnotu `Custom` .|  
|`certificateValidationMode`|Určuje jeden ze tří režimů, který se používá k ověření přihlašovacích údajů. Je-li nastaveno na hodnotu `Custom` , `customCertificateValidator` musí být zadána také.|  
|`revocationMode`|Jeden z režimů, který slouží ke kontrole seznamů odvolaných certifikátů (CRL).|  
|`trustedStoreLocation`|Jedno ze dvou umístění úložiště systému: `LocalMachine` nebo `CurrentUser` . Tato hodnota se používá, když je certifikát služby vyjednán klientovi. Ověřování se provádí pro úložiště **důvěryhodných osob** v zadaném umístění úložiště.|  
  
## <a name="customcertificatevalidatortype-attribute"></a>customCertificateValidatorType – atribut  
  
|Hodnota|Description|  
|-----------|-----------------|  
|Řetězec|Nepovinný parametr. Určuje název typu a sestavení a další data, která se používají k vyhledání typu. Je vyžadován minimální obor názvů a název typu. Volitelné informace zahrnují: název sestavení, číslo verze, jazykovou verzi a token veřejného klíče.|  
  
## <a name="certificatevalidationmode-attribute"></a>certificateValidationMode – atribut  
  
|Hodnota|Description|  
|-----------|-----------------|  
|Výčet|Nepovinný parametr. Jedna z následujících hodnot: `None` , `PeerTrust` , `ChainTrust` , `PeerOrChainTrust` , `Custom` . Výchozí formát je `ChainTrust`. Výchozí formát je `ChainTrust`.<br /><br /> Další informace najdete v tématu [práce s certifikáty](../../../wcf/feature-details/working-with-certificates.md).|  
  
## <a name="revocationmode-attribute"></a>revocationMode – atribut  
  
|Hodnota|Description|  
|-----------|-----------------|  
|Výčet|Jedna z následujících hodnot: `NoCheck` , `Online` , `Offline` . Výchozí formát je `Online`.<br /><br /> Další informace najdete v tématu [práce s certifikáty](../../../wcf/feature-details/working-with-certificates.md).|  
  
## <a name="trustedstorelocation-attribute"></a>trustedStoreLocation – atribut  
  
|Hodnota|Description|  
|-----------|-----------------|  
|Výčet|Jedna z následujících hodnot: `LocalMachine` nebo `CurrentUser` . Výchozí formát je `CurrentUser`. Pokud klientská aplikace běží pod účtem systému, certifikát se obvykle nachází v části `LocalMachine` . Pokud klientská aplikace běží pod uživatelským účtem, bude certifikát typicky v `CurrentUser` . Výchozí formát je `CurrentUser`.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<peer>](peer-of-clientcredentials-element.md)|Určuje přihlašovací údaje, které se používají k ověřování klienta pro partnerských služeb.|  
  
## <a name="remarks"></a>Poznámky  
 Tento prvek musí být nakonfigurován, pokud je zvoleno ověřování zpráv. U výstupních kanálů se každá zpráva podepisuje pomocí certifikátu, který poskytuje [\<certificate>](certificate-element.md) . Všechny zprávy před doručením do aplikace jsou zkontrolovány proti pověření zprávy pomocí validátoru určeného `customCertificateValidatorType` atributem tohoto prvku. Validátor může buď přijmout nebo odmítnout přihlašovací údaje.  
  
## <a name="example"></a>Příklad  
 Následující kód nastaví režim ověřování odesílatele zprávy na `PeerOrChainTrust` .  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="MyEndpointBehavior">
      <clientCredentials>
        <peer>
          <certificate findValue="www.contoso.com"
                       storeLocation="LocalMachine"
                       x509FindType="FindByIssuerName" />
          <messageSenderAuthentication certificateValidationMode="PeerOrChainTrust" />
          <messageSenderAuthentication certificateValidationMode="None" />
        </peer>
      </clientCredentials>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.MessageSenderAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.MessageSenderAuthentication%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- [Práce s certifikáty](../../../wcf/feature-details/working-with-certificates.md)
- [Síť rovnocenných počítačů](../../../wcf/feature-details/peer-to-peer-networking.md)
- [Ověřování zpráv rovnocenného kanálu](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))
- [Vlastní ověřování rovnocenných kanálů](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))
- [Zabezpečení aplikací rovnocenného kanálu](../../../wcf/feature-details/securing-peer-channel-applications.md)
