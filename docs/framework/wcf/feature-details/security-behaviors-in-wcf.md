---
title: Chování zabezpečení ve WCF
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 513232c0-39fd-4409-bda6-5ebd5e0ea7b0
caps.latest.revision: 23
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: 98323b4d29b68d57d3c01e9a007b5f0f9fc08377
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="security-behaviors-in-wcf"></a>Chování zabezpečení ve WCF
V [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], chování změny chování při spuštění na úrovni služby, nebo na úrovni koncového bodu. ([!INCLUDE[crabout](../../../../includes/crabout-md.md)] chování obecně naleznete v tématu [určení chování služby Run-Time](../../../../docs/framework/wcf/specifying-service-run-time-behavior.md).) *Chování zabezpečení* kontrolu nad přihlašovací údaje, ověřování, autorizaci a auditování protokoly. Chování můžete použít buď programování, nebo prostřednictvím konfigurace. Toto téma se zaměřuje na konfiguraci následujících chování související s funkcí zabezpečení:  
  
-   [\<– serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).  
  
-   [\<clientCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md).  
  
-   [\<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md).  
  
-   [\<serviceSecurityAudit >](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md).  
  
-   [\<serviceMetadata >](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md), který také umožňuje určit zabezpečený koncový bod, který mohou klienti získat přístup pro metadata.  
  
## <a name="setting-credentials-with-behaviors"></a>Nastavení přihlašovacích údajů s chováním  
 Použití [ \<– serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) a [ \<clientCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) nastavit hodnoty přihlašovacích údajů pro službu nebo klienta. Základní konfigurace vazeb Určuje, zda pověření musí být nastavena. Například, pokud má nastaven režim zabezpečení `None`, služby a klienti není vzájemné ověření a vyžadovat žádné přihlašovací údaje libovolného typu.  
  
 Vazby služby na druhé straně může vyžadovat typu pověření klienta. V takovém případě budete muset nastavit na hodnotu přihlašovacích údajů pomocí chování. ([!INCLUDE[crabout](../../../../includes/crabout-md.md)] možné typy přihlašovací údaje, najdete v části [výběr typu pověření](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md).) V některých případech, například při použití pověření systému Windows k ověření prostředí automaticky vytváří hodnotu skutečné přihlašovacích údajů a není potřeba explicitně nastavit hodnotu přihlašovacích údajů (Pokud chcete určit jinou sadu přihlašovacích údajů).  
  
 Všechny přihlašovací údaje služby se najdou podřízených elementů [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md). Následující příklad ukazuje certifikátu jako přihlašovací údaje služby.  
  
```xml  
<configuration>  
 <system.serviceModel>  
  <behaviors>  
   <serviceBehaviors>  
    <behavior name="ServiceBehavior1">  
     <serviceCredentials>  
      <serviceCertificate findValue="000000000000000000000000000"   
                          storeLocation="CurrentUser"  
      storeName="Root" x509FindType="FindByThumbprint" />  
     </serviceCredentials>  
    </behavior>  
   </serviceBehaviors>  
  </behaviors>  
 </system.serviceModel>  
</configuration>  
```  
  
## <a name="service-credentials"></a>Pověření služby  
 [ \<– ServiceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) obsahuje čtyři podřízené elementy. V následujících částech jsou uvedeny elementy a jejich použití.  
  
### <a name="servicecertificate-element"></a>\<serviceCertificate > elementu  
 Tento prvek slouží k určení certifikát X.509, který slouží k ověřování klientů pomocí režim zabezpečení zprávy. Pokud používáte certifikát, který je pravidelně obnovovat, pak změny jeho kryptografický otisk. V takovém případě použijte název subjektu, jako `X509FindType` vzhledem k tomu, že certifikát můžete ho znova vydat se stejným názvem subjektu.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] pomocí elementu, najdete v tématu [postupy: určení hodnot přihlašovacích údajů klienta](../../../../docs/framework/wcf/how-to-specify-client-credential-values.md).  
  
### <a name="certificate-of-clientcertificate-element"></a>\<certifikát > z \<clientCertificate > elementu  
 Použití [ \<certifikátu >](../../../../docs/framework/configure-apps/file-schema/wcf/certificate-of-clientcertificate-element.md) elementu, pokud služba musí mít certifikát klienta předem pro bezpečnou komunikaci s klientem. K tomu dochází, když pomocí vzoru duplexní komunikace. Ve vzoru typičtější požadavku a odpovědi klient zahrne svůj certifikát v žádosti, které služba používá k zabezpečení odpověď zpět klientovi. Duplexní komunikace vzor, ale nemá žádné požadavky a odpovědi. Službu nelze odvodit certifikát klienta z komunikace a proto služba vyžaduje, aby certifikát klienta předem k zabezpečení zprávy, které mají klienta. Musíte získat certifikát klienta způsobem out-of-band a zadat certifikát pomocí tohoto elementu. [!INCLUDE[crabout](../../../../includes/crabout-md.md)] duplexní služby, najdete v části [postupy: vytvoření duplexního kontraktu](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).  
  
### <a name="authentication-of-clientcertificate-element"></a>\<ověřování > z \<clientCertificate > elementu  
 [ \<Ověřování >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) element umožňuje přizpůsobit, jak klienti se ověřují. Můžete nastavit `CertificateValidationMode` atribut `None`, `ChainTrust`, `PeerOrChainTrust`, `PeerTrust`, nebo `Custom`. Ve výchozím nastavení je úroveň nastavena na `ChainTrust`, která určuje, že každý certifikát, je nutné nalézt v hierarchii certifikátů končí na *kořenová autorita* v horní části řetězu. Toto je nejbezpečnější režim. Můžete také nastavit hodnotu `PeerOrChainTrust`, která určuje, že samoobslužné vydaných certifikátů (peer vztahu důvěryhodnosti) jsou přijaty a také certifikáty, které jsou v důvěryhodné řetězu. Tato hodnota se používá při vývoji a ladění klientů a služeb, protože samoobslužné vydaných certifikátů nemusí zakoupenému od důvěryhodné autority. Při nasazování klienta, použijte `ChainTrust` místo hodnoty. Můžete také nastavit hodnotu `Custom`. Pokud nastavíte `Custom` hodnotu, je nutné také nastavit `CustomCertificateValidatorType` atribut sestavení a typ použitý k ověření certifikátu. Pokud chcete vytvořit vlastní vlastní validátor, musí dědit z abstraktní <xref:System.IdentityModel.Selectors.X509CertificateValidator> třídy.  
  
### <a name="issuedtokenauthentication-element"></a>\<issuedTokenAuthentication > – Element  
 Vystavený token scénář má tři fáze. V první fázi se klient pokouší o přístup ke službě označuje *služby tokenů zabezpečení* (STS). Služba tokenů zabezpečení pak ověřuje klienta a následně vydá klienta token, obvykle token zabezpečení kontrolní výrazy Markup Language (SAML). Klient pak vrátí ke službě pomocí tokenu. Služba prověří token pro data, která umožňuje službě ověření tokenu a proto klienta. K ověření tokenu, musí být známo certifikát, který používá službu tokenů zabezpečení ve službě. [ \<IssuedTokenAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) element slouží jako úložiště pro všechny zabezpečené služby tokenů certifikáty. Chcete-li přidat certifikáty, použijte [ \<knownCertificates >](../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md). Vložit [ \<Přidat >](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md) pro každý certifikát, jak je znázorněno v následujícím příkladu.  
  
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
  
 Měli byste použít [ \<allowedAudienceUris >](../../../../docs/framework/configure-apps/file-schema/wcf/allowedaudienceuris.md) kolekce ve federované aplikaci, která využívá *služby tokenů zabezpečení* (STS), který vystavuje `SamlSecurityToken` tokeny zabezpečení. Když služba tokenů zabezpečení vydá token zabezpečení, může však určovat identifikátor URI webové služby, pro které je určen přidáním token zabezpečení `SamlAudienceRestrictionCondition` do tokenu zabezpečení. Umožňuje `SamlSecurityTokenAuthenticator` pro příjemce webovou službu k ověření, že token zabezpečení vydané slouží k této webové služby tak, že zadáte, aby tato kontrola má proběhnout provedením následujících akcí:  
  
-   Nastavte `audienceUriMode` atribut [ \<issuedTokenAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) k `Always` nebo `BearerKeyOnly`.  
  
-   Zadejte sadu platné identifikátory URI přidáním identifikátory URI k této kolekci. Chcete-li to provést, vložte [ \<Přidat >](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-allowedaudienceuris.md) pro každý identifikátor URI  
  
 Další informace naleznete v tématu <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] Pomocí tohoto elementu konfigurace najdete v tématu [postupy: Konfigurace pověření ve službě Federation](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).  
  
#### <a name="allowing-anonymous-cardspace-users"></a>Povolení CardSpace anonymní uživatelé  
 Nastavení `AllowUntrustedRsaIssuers` atribut `<IssuedTokenAuthentication>` element `true` explicitně umožňuje libovolného klienta k dispozici vystavený token podepsané libovolný pár klíče RSA. Vystavitel je *nedůvěryhodné* vzhledem k tomu, že klíč neobsahuje žádná data vystavitele s ním spojená. A [!INCLUDE[infocard](../../../../includes/infocard-md.md)] uživatel může vytvářet samostatně vydané karty, která zahrnuje samoobslužné zadané deklarace identity. Používejte tuto funkci opatrně. Pokud chcete tuto funkci použít, považuje za bezpečnější heslo, které by měly být uložené v databázi společně s uživatelské jméno veřejného klíče RSA. Před povolením klientský přístup ke službě, ověření klienta uvedené veřejným klíčem RSA porovnáním se souborem uložené veřejný klíč pro vidění uživatelské jméno. Toto předpokládá, že jste vytvořili procesu registrace, které uživatelé mohou registrovat svá uživatelská jména a přidružit vystavený veřejné klíče RSA.  
  
## <a name="client-credentials"></a>Pověření klienta  
 Pověření klienta slouží k ověření klienta ke službám v případech, kdy je potřeba vzájemné ověřování. V části můžete použít k určení certifikáty služby pro scénáře, kde klient musíte zabezpečit zprávy služby pomocí certifikátu služby.  
  
 Klienta můžete také nakonfigurovat jako součást scénář federace použití vystavené tokeny z zabezpečené tokenu služby nebo místního vystavitele tokenů. [!INCLUDE[crabout](../../../../includes/crabout-md.md)] federovaných scénářích najdete v části [federace a vystavené tokeny](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md). Všechny přihlašovací údaje klienta se nacházejí v části [ \<endpointBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md), jak je znázorněno v následujícím kódu.  
  
```xml  
<behaviors>  
 <endpointBehaviors>  
  <behavior name="EndpointBehavior1">  
   <clientCredentials>  
    <clientCertificate findValue="cn=www.contoso.com"     
        storeLocation="LocalMachine"  
        storeName="AuthRoot" x509FindType="FindBySubjectName" />  
    <serviceCertificate>  
     <defaultCertificate findValue="www.cohowinery.com"   
                    storeLocation="LocalMachine"  
                    storeName="Root" x509FindType="FindByIssuerName" />  
    <authentication revocationMode="Online"  
                    trustedStoreLocation="LocalMachine" />  
    </serviceCertificate>  
   </clientCredentials>  
  </behavior>  
 </endpointBehaviors>  
```  
  
#### <a name="clientcertifictate-element"></a>\<clientCertifictate > elementu  
 Nastavte certifikát používaný k ověření klienta s tímto elementem. Další informace najdete v tématu [postupy: určení hodnot přihlašovacích údajů klienta](../../../../docs/framework/wcf/how-to-specify-client-credential-values.md).  
  
#### <a name="httpdigest"></a>\<httpDigest >  
 Musí být povolena tato funkce se službou Active Directory ve Windows a Internetové informační služby (IIS). Další informace najdete v tématu [ověřování algoritmem Digest ve službě IIS 6.0](http://go.microsoft.com/fwlink/?LinkId=88443).  
  
#### <a name="issuedtoken-element"></a>\<issuedToken > elementu  
 [ \<IssuedToken >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md) obsahuje prvky, které konfigurace místního vystavitele tokeny nebo chování použít s služby tokenů zabezpečení. Pokyny týkající se konfigurace klienta pomocí místního vystavitele najdete v tématu [postupy: Konfigurace místního vystavitele](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).  
  
#### <a name="localissueraddress"></a>\<localIssuerAddress >  
 Určuje výchozí adresu služby tokenů zabezpečení. Používá se při <xref:System.ServiceModel.WSFederationHttpBinding> neposkytuje adresu URL služby tokenů zabezpečení, nebo pokud je adresa vystavitele federované vazby http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous nebo `null`. V takových případech <xref:System.ServiceModel.Description.ClientCredentials> musí být nakonfigurované na adresu místního vystavitele a vazby, které používají ke komunikaci s této vystavitele.  
  
#### <a name="issuerchannelbehaviors"></a>\<issuerChannelBehaviors >  
 Použití [ \<issuerChannelBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md) přidat [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] chování klienta použít při komunikaci s služby tokenů zabezpečení. Určení chování klienta v [ \<endpointBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md) části. Chcete-li použít definované chování, přidejte <`add`> elementu, který chcete `<issuerChannelBehaviors>` element s dva atributy. Nastavte `issuerAddress` na adresu URL služby tokenů zabezpečení a sadu `behaviorConfiguration` atribut název chování definované koncového bodu, jak je znázorněno v následujícím příkladu.  
  
```xml  
<clientCredentials>  
   <issuedToken>  
      <issuerChannelBehaviors>  
         <add issuerAddress="http://www.contoso.com"  
               behaviorConfiguration="clientBehavior1" />     
```  
  
#### <a name="servicecertificate-element"></a>\<serviceCertificate > elementu  
 Pomocí tohoto elementu k řízení ověřování certifikáty služeb.  
  
 [ \<DefaultCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md) element může ukládat jeden certifikát použít, když služba určuje žádný certifikát.  
  
 Použití [ \<scopedCertificates >](../../../../docs/framework/configure-apps/file-schema/wcf/scopedcertificates-element.md) a [ \<Přidat >](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-scopedcertificates-element.md) nastavit certifikáty služby, které jsou spojeny s určitým službám. `<add>` Obsahuje element `targetUri` atribut, který se používá k přidružení certifikátu služby.  
  
 [ \<Ověřování >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) element určuje úroveň důvěryhodnosti používá k ověření certifikátů. Ve výchozím nastavení je úroveň nastavena na "ChainTrust", která určuje, že každý certifikát, je nutné nalézt v hierarchii certifikátů končí na důvěryhodné certifikační autority v horní části řetězu. Toto je nejbezpečnější režim. Můžete také nastavit hodnotu "PeerOrChainTrust", která určuje, že jsou přijaty samoobslužné vydaných certifikátů (peer vztahu důvěryhodnosti), a také certifikáty, které jsou v důvěryhodné řetězu. Tato hodnota se používá při vývoji a ladění klientů a služeb, protože samoobslužné vydaných certifikátů nemusí zakoupenému od důvěryhodné autority. Při nasazování klienta, použijte místo toho hodnotu "ChainTrust". Můžete také nastavit hodnotu "Vlastní" nebo "None." Pokud chcete použít hodnotu "Vlastní", musíte taky nastavit `CustomCertificateValidatorType` atribut sestavení a typ použitý k ověření certifikátu. Pokud chcete vytvořit vlastní vlastní validátor, musí dědit z abstraktní <xref:System.IdentityModel.Selectors.X509CertificateValidator> třídy. Další informace najdete v tématu [postupy: vytvoření služby, který využívá validátor certifikátu vlastní](../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).  
  
 [ \<Ověřování >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) obsahuje element `RevocationMode` atribut, který určuje, jak certifikáty jsou zaškrtnutá políčka pro odvolání. Výchozí hodnota je "online", což naznačuje, že certifikáty jsou automaticky zkontrolovány pro odvolání. Další informace najdete v tématu [práce s certifikáty](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
## <a name="serviceauthorization"></a>ServiceAuthorization  
 [ \<ServiceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) prvek obsahuje prvky, které ovlivňují autorizace, vlastní roli zprostředkovatele a zosobnění.  
  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute> Třídy je použít metody služby. Atribut určuje skupiny uživatelů pro použití při použití chráněná metoda autorizace. Výchozí hodnota je "UseWindowsGroups" a určuje skupiny systému Windows, jako je například "Administrators" nebo "Uživatelé," se vyhledávají identity pokusu o přístup k prostředku. Můžete také zadat "UseAspNetRoles" používat vlastní roli zprostředkovatele, který je nakonfigurovaný pod <`system.web` > elementu, jak je znázorněno v následujícím kódu.  
  
```xml  
<system.web>  
  <membership defaultProvider="SqlProvider"   
   userIsOnlineTimeWindow="15">  
     <providers>  
       <clear />  
       <add   
          name="SqlProvider"   
          type="System.Web.Security.SqlMembershipProvider"   
          connectionStringName="SqlConn"  
          applicationName="MembershipProvider"  
          enablePasswordRetrieval="false"  
          enablePasswordReset="false"  
          requiresQuestionAndAnswer="false"  
          requiresUniqueEmail="true"  
          passwordFormat="Hashed" />  
     </providers>  
   </membership>  
  <!-- Other configuration code not shown.-->  
</system.web>  
```  
  
 Následující kód ukazuje `roleProviderName` použít s `principalPermissionMode` atribut.  
  
```xml  
<behaviors>  
 <behavior name="ServiceBehaviour">          
  <serviceAuthorization principalPermissionMode ="UseAspNetRoles"   
                        roleProviderName ="SqlProvider" />  
</behavior>   
   <!-- Other configuration code not shown. -->  
</behaviors>  
```  
  
## <a name="configuring-security-audits"></a>Konfigurace auditování zabezpečení  
 Použití [ \<serviceSecurityAudit >](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md) k určení zapisovat do protokolu a jaké typy událostí do protokolu. Další informace najdete v tématu [auditování](../../../../docs/framework/wcf/feature-details/auditing-security-events.md).  
  
```xml  
<system.serviceModel>  
<serviceBehaviors>  
  <behavior name="NewBehavior">  
    <serviceSecurityAudit auditLogLocation="Application"   
             suppressAuditFailure="true"  
             serviceAuthorizationAuditLevel="Success"   
             messageAuthenticationAuditLevel="Success" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="secure-metadata-exchange"></a>Zabezpečená výměna metadat  
 Export metadat klientům je vhodné pro vývojáře klienta a služby, protože umožňuje stahování kódu konfigurace a klienta. Aby se snížila zranitelnost služby uživatelům se zlými úmysly, je možné zabezpečit přenos pomocí protokolu SSL přes protokol HTTP (HTTPS) mechanismus. To pokud chcete udělat, je třeba nejprve svázat vhodný certifikát X.509 konkrétní port, na počítači, který je hostitelem služby. (Další informace najdete v tématu [práce s certifikáty](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).) Druhý, přidejte [ \<serviceMetadata >](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md) do konfigurace služby a nastavte `HttpsGetEnabled` atribut `true`. Nakonec nastavte `HttpsGetUrl` atribut na adresu URL metadat koncového bodu služby, jak je znázorněno v následujícím příkladu.  
  
```xml  
<behaviors>  
 <serviceBehaviors>  
  <behavior name="NewBehavior">  
    <serviceMetadata httpsGetEnabled="true"   
     httpsGetUrl="https://myComputerName/myEndpoint" />  
  </behavior>  
 </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="see-also"></a>Viz také  
 [Auditování](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)  
 [Model zabezpečení pro Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
