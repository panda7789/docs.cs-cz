---
title: "&lt;issuedTokenAuthentication&gt; – &lt;serviceCredentials&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5c2e288f-f603-4d13-839a-0fd6d1981bec
caps.latest.revision: "14"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2d8e3c7df0108c6f8656827c6c0795dcb9fe3a9e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltissuedtokenauthenticationgt-of-ltservicecredentialsgt"></a>&lt;issuedTokenAuthentication&gt; – &lt;serviceCredentials&gt;
Určuje vlastní tokenem vydaným jako přihlašovací údaje služby.  
  
 \<systém. ServiceModel >  
\<chování >  
\<serviceBehaviors >  
\<chování >  
\<– serviceCredentials >  
\<issuedTokenAuthentication >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<issuedTokenAuthentication   
   allowUntrustedRsaIssuers="Boolean"  
   audienceUriMode="Always/BearerKeyOnly/Never"  
      customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"  
certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"  
   revocationMode="NoCheck/Online/Offline"  
   samlSerializer="String"  
    trustedStoreLocation="CurrentUser/LocalMachine">  
      <allowedAudienceUris>  
      <add allowedAudienceUri="String"/>  
      </allowedAudienceUris>  
      <knownCertificates>   
         <add findValue="String"  
                 storeLocation="CurrentUser/LocalMachine"  
                storeName=" CurrentUser/LocalMachine"  
                x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"/>  
      </knownCertificates>  
</issuedTokenAuthentication>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují nadřazené elementy, atributy a podřízené elementy  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`allowedAudienceUris`|Získá sadu cíle identifikátory URI pro kterou <xref:System.IdentityModel.Tokens.SamlSecurityToken> token zabezpečení je možné cílit pro Chcete-li být považován za platný podle <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance. Další informace o použití tohoto atributu naleznete v části <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>.|  
|`allowUntrustedRsaIssuers`|Logická hodnota, která určuje, jestli jsou povolená nedůvěryhodné vystavitelů certifikátů RSA.<br /><br /> Certifikáty jsou podepsané certifikační autority (CA) k ověření pravosti. Nedůvěryhodné vystavitele je certifikační Autorita, která není zadán důvěru k podepisování certifikátů.|  
|`audienceUriMode`|Získá hodnotu, která určuje, zda <xref:System.IdentityModel.Tokens.SamlSecurityToken> token zabezpečení <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> má být ověřen. Tato hodnota je typu <xref:System.IdentityModel.Selectors.AudienceUriMode>. Další informace o použití tohoto atributu naleznete v části <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>.|  
|`certificateValidationMode`|Nastaví režim ověření certifikátu. Mezi platné hodnoty <xref:System.ServiceModel.Security.X509CertificateValidationMode>. Pokud nastavena na `Custom`, pak `customCertificateValidator` musí být uveden také. Výchozí hodnota je `ChainTrust`.|  
|`customCertificateValidatorType`|Volitelný řetězec. Typ a sestavení, které slouží k ověření vlastního typu. Tento atribut musí být nastaven při `certificateValidationMode` je nastaven na `Custom`.|  
|`revocationMode`|Nastaví režim odvolaných certifikátů, který určuje, zda dojde k kontrolu odvolaných certifikátů, a pokud probíhá online nebo offline. Tento atribut je typu <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.|  
|`samlSerializer`|Atribut volitelný řetězec, který určuje typ SamlSerializer, který se používá pro přihlašovací údaje služby. Výchozí hodnota je prázdný řetězec.|  
|`trustedStoreLocation`|Volitelné výčtu. Jedno z umístění úložiště dvě systému: `LocalMachine` nebo `CurrentUser`.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`knownCertificates`|Určuje kolekci <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement> prvky, které určuje důvěryhodných vystavitelů pro přihlašovací údaje služby.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<– serviceCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|Určuje pověření, která se použije v ověřování služby a nastavení související s ověření pověření klienta.|  
  
## <a name="remarks"></a>Poznámky  
 Vystavený token scénář má tři fáze. V první fázi se klient pokouší o přístup ke službě označuje *služby tokenů zabezpečení*. Službu tokenů zabezpečení pak ověřuje klienta a následně vydá klienta token, obvykle token zabezpečení kontrolní výrazy Markup Language (SAML). Klient pak vrátí ke službě pomocí tokenu. Služba prověří token pro data, která umožňuje službě ověření tokenu a proto klienta. K ověření tokenu, certifikátu používá zabezpečené tokenu služby musí být známo ke službě.  
  
 Tento element má úložiště pro všechny zabezpečené služby tokenů certifikáty. Chcete-li přidat certifikáty, použijte [ \<knownCertificates >](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md). Vložit [ \<Přidat >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md) pro každý certifikát, jak je znázorněno v následujícím příkladu.  
  
```xml  
<issuedTokenAuthorization>  
   <knownCertificates>  
      <add findValue="www.contoso.com"   
           storeLocation="LocalMachine" storeName="My"   
           X509FindType="FindBySubjectName" />  
    </knownCertificates>  
</issuedTokenAuthentication>  
```  
  
 Ve výchozím nastavení musí získat certifikáty ze služby tokenu zabezpečení. Tyto "známé" certifikáty, ujistěte se, že který pouze oprávněné klientů můžete přístup ke službě.  
  
 Další informace o použití tohoto elementu konfigurace najdete v tématu [postupy: Konfigurace pověření ve službě Federation](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.IssuedTokenAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>  
 <xref:System.ServiceModel.Description.ServiceCredentials.IssuedTokenAuthentication%2A>  
 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential>  
 [Zabezpečení služeb a klientů](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Postupy: Konfigurace pověření ve službě Federation](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
