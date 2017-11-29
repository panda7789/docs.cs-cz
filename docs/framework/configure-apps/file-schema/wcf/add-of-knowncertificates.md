---
title: "&lt;add&gt; – &lt;knownCertificates&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 128aaabe-3f1a-4c3b-b59f-898d0f02910f
caps.latest.revision: "14"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e19bb495f360352b7304595323265d28773660a4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltaddgt-of-ltknowncertificatesgt"></a>&lt;add&gt; – &lt;knownCertificates&gt;
Přidá do kolekce známých certifikátů certifikát X.509.  
  
 \<systém. ServiceModel >  
\<chování >  
\<serviceBehaviors >  
\<chování >  
\<– serviceCredentials >  
\<issuedTokenAuthentication >  
\<knownCertificates >  
\<Přidat >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<knownCertificates>   
   <add findValue="String"  
      storeLocation="CurrentUser/LocalMachine"  
      storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"  
      x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"/>  
</knownCertificates>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|findValue|Řetězec. Hodnota, kterou chcete vyhledat.|  
|storeLocation|Výčet. Jednu ze dvou ukládat prohledávaných umístění.|  
|storeName|Výčet. Jeden z úložiště systému pro vyhledávání.|  
|X509FindType|Výčet. Jeden z pole certifikátu pro vyhledávání.|  
  
## <a name="findvalue-attribute"></a>findValue atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|String|Hodnota závisí na poli (zadané v atributu X509FindType) být vyhledán. Například pokud hledání kryptografický otisk, hodnota musí být řetězec o délce hexadecimální číslice.|  
  
## <a name="x509findtype-attribute"></a>Atribut x509FindType  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|Výčet|Hodnoty patří: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.|  
  
## <a name="storelocation-attribute"></a>storeLocation atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|Výčet|CurrentUser nebo LocalMachine.|  
  
## <a name="storename-attribute"></a>storeName atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|Výčet|Hodnoty patří: CertificateAuthority adresáře, AuthRoot, zakázané, Moje, Root, TrustedPeople a TrustedPublisher.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<knownCertificates >](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md)|Představuje kolekci certifikáty X.509, které jsou k dispozici ve zabezpečení tokenu služby (STS) pro ověřování tokenů zabezpečení.|  
  
## <a name="remarks"></a>Poznámky  
 Vystavený token scénář má tři fáze. V první fázi se klient pokouší o přístup ke službě označuje *služby tokenů zabezpečení*. Službu tokenů zabezpečení pak ověřuje klienta a následně vydá klienta token, obvykle token zabezpečení kontrolní výrazy Markup Language (SAML). Klient pak vrátí ke službě pomocí tokenu. Služba prověří token pro data, která umožňuje službě ověření tokenu a proto klienta. K ověření tokenu, certifikátu používá zabezpečené tokenu služby musí být známo ke službě.  
  
 [ \<IssuedTokenAuthentication >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) element slouží jako úložiště pro všechny zabezpečené služby tokenů certifikáty. Chcete-li přidat certifikáty, použijte [ \<knownCertificates >](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md). Vložit [ \<Přidat > element \<knownCertificates > Element](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md) pro každý certifikát, jak je znázorněno v následujícím příkladu.  
  
```xml  
<issuedTokenAuthentication>  
   <knownCertificates>  
      <add findValue="www.contoso.com"   
           storeLocation="LocalMachine" storeName="My"   
           X509FindType="FindBySubjectName" />  
    </knownCertificates>  
</issuedTokenAuthentication>  
```  
  
 Ve výchozím nastavení musí získat certifikáty ze služby tokenu zabezpečení. Tyto "známé" certifikáty, ujistěte se, že který pouze oprávněné klientů můžete přístup ke službě.  
  
 Podmínky pro klienta k ověření pomocí federované služby a také další informace o použití tohoto elementu konfigurace najdete v tématu [postupy: Konfigurace pověření ve službě Federation](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md). Další informace o federovaných scénářích najdete v tématu [federace a vystavené tokeny](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad přidá certifikát do úložiště pro všechny certifikáty, služby tokenů zabezpečení.  
  
```xml  
<serviceBehaviors>  
 <behavior name="myServiceBehavior">  
  <serviceCredentials>  
   <issuedTokenAuthentication>  
    <knownCertificates>  
     <add findValue="www.contoso.com" storeLocation="LocalMachine"   
           storeName="CertificateAuthority"  
           x509FindType="FindByIssuerName" />  
     </knownCertificates>  
    </issuedTokenAuthentication>  
   </serviceCredentials>  
  </behavior>  
 </serviceBehaviors>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.KnownCertificates%2A>  
 <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElementCollection>  
 <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement>  
 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A>  
 [\<knownCertificates >](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md)  
 [Práce s certifikáty](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [Federace a vystavené tokeny](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [Postupy: Konfigurace pověření ve službě Federation](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)  
 [Zabezpečení služeb a klientů](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
