---
title: Element &lt;messageSenderAuthentication&gt;
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8d979dfc-a6f9-42ec-96d5-7fbc13a48118
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5a280f9fe59ca5294276b98ec3632d6bc1a7ecba
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltmessagesenderauthenticationgt-element"></a>Element &lt;messageSenderAuthentication&gt;
Určuje možnosti ověřování pro odesílatelé zpráv peer-to-peer.  
  
 Další informace o programování peer-to-peer, najdete v části [Peer-to-Peer sítě](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).  
  
 \<systém. ServiceModel >  
\<chování >  
\<endpointBehaviors >  
\<chování >  
\<clientCredentials >  
\<sdílené >  
\<messageSenderAuthentication >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<messageSenderAuthentication  
customCertificateValidatorType= "namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"  
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
|customCertificateValidatorType|Typ a sestavení, které slouží k ověření vlastního typu. Tento atribut musí být nastaven při `certificateValidationMode` je nastaven na `Custom`.|  
|certifcateValidationMode|Určuje jeden ze tří režimů slouží k ověření přihlašovacích údajů. Pokud nastavena na `Custom`, pak `customCertificateValidator` musí být uveden také.|  
|revocationMode|Jeden z režimů používá k ověření pro seznamy odvolaných certifikátů (CRL).|  
|trustedStoreLocation|Jedno z umístění úložiště dvě systému: `LocalMachine` nebo `CurrentUser`. Tato hodnota se používá, když je klientovi vyjednal certifikát služby. Ověření se provádí před **důvěryhodné osoby** uložit do umístění zadaného úložiště.|  
  
## <a name="customcertificatevalidatortype-attribute"></a>customCertificateValidatorType atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|String|Volitelné. Určuje název typu a sestavení a další data použít k vyhledání typu. Název oboru názvů a typ se minimálně, vyžadují. Volitelné informace zahrnují: název sestavení, číslo verze, jazykové verze a tokenu veřejného klíče.|  
  
## <a name="certificatevalidationmode-attribute"></a>certificateValidationMode atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|Výčet|Volitelné. Jeden z následujících hodnot: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`. Výchozí hodnota je `ChainTrust`. Výchozí hodnota je `ChainTrust`.<br /><br /> Další informace najdete v tématu [práce s certifikáty](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).|  
  
## <a name="revocationmode-attribute"></a>revocationMode atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|Výčet|Jeden z následujících hodnot: `NoCheck`, `Online`, `Offline`. Výchozí hodnota je `Online`.<br /><br /> Další informace najdete v tématu [práce s certifikáty](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).|  
  
## <a name="trustedstorelocation-attribute"></a>trustedStoreLocation atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|Výčet|Jeden z následujících hodnot: `LocalMachine` nebo `CurrentUser`. Výchozí hodnota je `CurrentUser`. Pokud klientská aplikace běží pod účtem systému pak certifikát je obvykle v části `LocalMachine`. Pokud klientská aplikace běží pod účtem uživatele, pak tento certifikát je obvykle v `CurrentUser`. Výchozí hodnota je `CurrentUser`.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<sdílené >](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-clientcredentials-element.md)|Určí pověření používaná pro ověřování klienta do sdílené služby.|  
  
## <a name="remarks"></a>Poznámky  
 Tento element musí být nakonfigurován, pokud je zvoleno ověřování zpráv. Pro výstup kanály, je každá zpráva podepsaná pomocí certifikátu poskytované [ \<certifikátu >](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md). Všechny zprávy před doručí aplikaci, je zkontrolován pověřením zpráv pomocí validátor určeného `customCertificateValidatorType` atribut tohoto elementu. Validátor můžete buď přijmout nebo odmítnout přihlašovací údaje.  
  
## <a name="example"></a>Příklad  
 Následující kód nastaví režim ověření odesílatele zprávy `PeerOrChainTrust`.  
  
```xml  
<behaviors>  
 <endpointBehaviors>  
  <behavior name="MyEndpointBehavior">  
   <clientCredentials>  
    <peer>  
      <certificate findValue="www.contoso.com"   
                   storeLocation="LocalMachine"  
                   x509FindType="FindByIssuerName" />  
        <messageSenderAuthentication   
          certificateValidationMode="PeerOrChainTrust" />  
       <messageSenderAuthentication certificateValidationMode="None" />  
    </peer>  
   </clientCredentials>  
  </behavior>  
 </endpointBehaviors>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>  
 <xref:System.ServiceModel.Security.PeerCredential.MessageSenderAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement.MessageSenderAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>  
 [Práce s certifikáty](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [Sítě peer-to-Peer](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [Ověřování zpráv rovnocenného kanálu](http://msdn.microsoft.com/en-us/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [Vlastní ověřování rovnocenného kanálu](http://msdn.microsoft.com/en-us/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [Zabezpečení aplikací rovnocenného kanálu](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
