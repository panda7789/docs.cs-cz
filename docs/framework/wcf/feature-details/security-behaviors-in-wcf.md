---
title: Chování zabezpečení ve WCF
ms.date: 03/30/2017
ms.assetid: 513232c0-39fd-4409-bda6-5ebd5e0ea7b0
ms.openlocfilehash: f56bbd66aa61b8db9d6e720fb3a67ddbbf5e267e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184538"
---
# <a name="security-behaviors-in-wcf"></a>Chování zabezpečení ve WCF
V systému Windows Communication Foundation (WCF) chování změnit chování za běhu na úrovni služby nebo na úrovni koncového bodu. (Další informace o chování obecně naleznete v [tématu Určení chování za běhu služby](../../../../docs/framework/wcf/specifying-service-run-time-behavior.md).) *Chování zabezpečení* umožňuje kontrolu nad pověřeními, ověřováním, autorizací a protokoly auditování. Chování můžete použít buď programováním, nebo prostřednictvím konfigurace. Toto téma se zaměřuje na konfiguraci následujících chování souvisejících s funkcemi zabezpečení:  
  
- serviceCredentials>. [ \< ](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)  
  
- klientPověření>. [ \< ](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)  
  
- serviceAuthorization>. [ \< ](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md)  
  
- serviceSecurityAudit>. [ \< ](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md)  
  
- serviceMetadata>, který také umožňuje zadat zabezpečený koncový bod, ke kterému mají klienti přístup pro metadata. [ \< ](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md)  
  
## <a name="setting-credentials-with-behaviors"></a>Nastavení přihlašovacích údajů pomocí chování  
 Pomocí [ \<>serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) a [ \<clientCredentials](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) nastavte hodnoty pověření pro službu nebo klienta. Základní konfigurace vazby určuje, zda má být nastaveno pověření. Pokud je například režim zabezpečení `None`nastaven na , klienti i služby se navzájem neověřují a nevyžadují žádná pověření žádného typu.  
  
 Na druhé straně vazby služby může vyžadovat typ pověření klienta. V takovém případě bude pravděpodobně muset nastavit hodnotu pověření pomocí chování. (Další informace o možných typech pověření naleznete v [tématu Výběr typu pověření](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md).) V některých případech, například při ověřování pověření systému Windows, prostředí automaticky vytvoří skutečnou hodnotu pověření a není nutné explicitně nastavit hodnotu pověření (pokud nechcete zadat jinou sadu pověření).  
  
 Všechna pověření služby jsou nalezeny jako podřízené prvky [ \<serviceBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md). Následující příklad ukazuje certifikát používaný jako pověření služby.  
  
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
 [ \<ServiceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) obsahuje čtyři podřízené prvky. Prvky a jejich použití jsou popsány v následujících částech.  
  
### <a name="servicecertificate-element"></a>\<serviceCertificate> Element  
 Tento prvek slouží k určení certifikátu X.509, který se používá k ověření služby klientům pomocí režimu zabezpečení zprávy. Pokud používáte certifikát, který je pravidelně obnovován, změní se jeho kryptografický otisk. V takovém případě použijte název `X509FindType` subjektu jako, protože certifikát může být znovu vydán se stejným názvem subjektu.  
  
 Další informace o použití prvku naleznete v [tématu Postup: Zadání hodnot pověření klienta](../../../../docs/framework/wcf/how-to-specify-client-credential-values.md).  
  
### <a name="certificate-of-clientcertificate-element"></a>\<certifikát> \<klientského certifikátu> Element  
 Prvek [ \<certifikátu>,](../../../../docs/framework/configure-apps/file-schema/wcf/certificate-of-clientcertificate-element.md) pokud služba musí mít certifikát klienta předem, aby mohla bezpečně komunikovat s klientem. K tomu dochází při použití duplexní komunikace vzor. V typičtější request-reply vzor klienta zahrnuje svůj certifikát v požadavku, který služba používá k zabezpečení jeho odpověď zpět klientovi. Duplexní komunikace vzor, ale nemá žádné požadavky a odpovědi. Služba nemůže odvodit certifikát klienta z komunikace, a proto služba vyžaduje certifikát klienta předem k zabezpečení zpráv klientovi. Certifikát klienta je nutné získat nedostupným způsobem a zadat certifikát pomocí tohoto prvku. Další informace o duplexních službách najdete v [tématu Postup: Vytvoření duplexní smlouvy](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).  
  
### <a name="authentication-of-clientcertificate-element"></a>\<ověřovací> \<prvku clientCertificate> Element  
 Prvek [ \<>ověřování](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) umožňuje přizpůsobit způsob ověřování klientů. Atribut můžete `CertificateValidationMode` nastavit `None`na `ChainTrust` `PeerOrChainTrust`, `PeerTrust`, `Custom`, nebo . Ve výchozím nastavení je `ChainTrust`úroveň nastavena na , která určuje, že každý certifikát musí být nalezen v hierarchii certifikátů *končících kořenovou autoritou* v horní části řetězce. Toto je nejbezpečnější režim. Můžete také nastavit hodnotu na `PeerOrChainTrust`, která určuje, že jsou přijímány certifikáty vydané samostatně (rovnocenný vztah důvěryhodnosti) a také certifikáty, které jsou v důvěryhodném řetězci. Tato hodnota se používá při vývoji a ladění klientů a služeb, protože certifikáty vydané samostatně nemusí být zakoupeny od důvěryhodné autority. Při nasazování klienta `ChainTrust` použijte místo toho hodnotu. Můžete také nastavit hodnotu na `Custom`. Pokud je `Custom` nastavena na hodnotu, musíte také nastavit `CustomCertificateValidatorType` atribut sestavení a typ použitý k ověření certifikátu. Chcete-li vytvořit vlastní validátor, musíte dědit z abstraktní <xref:System.IdentityModel.Selectors.X509CertificateValidator> třídy.  
  
### <a name="issuedtokenauthentication-element"></a>\<issuedTokenAuthentication> Element  
 Scénář vydaného tokenu má tři fáze. V první fázi klient a pokus o přístup ke službě je odkazoval se na *službu zabezpečenétoken* (STS). SLUŽBA STS pak ověří klienta a následně vydá klientovi token, obvykle token jazyka Služka zabezpečení (SAML). Klient se pak vrátí do služby s tokenem. Služba zkontroluje token pro data, která umožňuje službě k ověření tokenu a proto klienta. K ověření tokenu musí být certifikát, který používá služba zabezpečeného tokenu, znám službě. Element [ \<issuedTokenAuthentication>](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) je úložištěm pro všechny takové certifikáty služby zabezpečené ho tokenu. Chcete-li přidat certifikáty, použijte [ \<známé certifikáty>](../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md). Pro každý certifikát vložte [ \<>pro přidání,](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md) jak je znázorněno v následujícím příkladu.  
  
```xml  
<issuedTokenAuthentication>  
   <knownCertificates>  
      <add findValue="www.contoso.com"
           storeLocation="LocalMachine" storeName="My"
           X509FindType="FindBySubjectName" />  
    </knownCertificates>  
</issuedTokenAuthentication>  
```  
  
 Ve výchozím nastavení musí být certifikáty získány ze zabezpečené služby tokenů. Tyto "známé" certifikáty zajišťují, že ke službě mají přístup pouze legitimní klienti.  
  
 Měli byste použít [ \<allowedAudienceUris kolekce>](../../../../docs/framework/configure-apps/file-schema/wcf/allowedaudienceuris.md) ve federované aplikaci, která využívá *službu zabezpečenétoken* (STS), která vydává `SamlSecurityToken` tokeny zabezpečení. Když služba STS vydá token zabezpečení, může určit identifikátor URI webových služeb, `SamlAudienceRestrictionCondition` pro které je token zabezpečení určen přidáním tokenu zabezpečení. To umožňuje `SamlSecurityTokenAuthenticator` webové službě příjemce ověřit, zda je vydaný token zabezpečení určen pro tuto webovou službu, zadáním, že k této kontrole by mělo dojít následujícím způsobem:  
  
- Nastavte `audienceUriMode` atribut [ \<issuedTokenAuthentication](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)>`Always` `BearerKeyOnly`nebo .  
  
- Zadejte sadu platných identifikátorů URI přidáním identifikátorů URI do této kolekce. Chcete-li to [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-allowedaudienceuris.md) provést, vložte pro každý identifikátor URI>pro přidání.  
  
 Další informace naleznete v tématu <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.  
  
 Další informace o použití tohoto konfiguračního prvku naleznete v [tématu Postup: Konfigurace pověření ve službě Federation Service](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).  
  
#### <a name="allowing-anonymous-cardspace-users"></a>Povolení anonymních uživatelů cardspace  
 Nastavení `AllowUntrustedRsaIssuers` atributu `<IssuedTokenAuthentication>` prvku `true` explicitně umožňuje každému klientovi prezentovat vlastní vydaný token podepsaný libovolným párem klíčů RSA. Vystavitel je *nedůvěryhodný,* protože klíč nemá k němu přidružená žádná data vystavitela. Uživatel služby CardSpace může vytvořit kartu, která se sama vydává a která obsahuje vlastní deklarace identity. Tuto funkci používejte opatrně. Chcete-li tuto funkci použít, představte si veřejný klíč RSA jako bezpečnější heslo, které by mělo být uloženo v databázi spolu s uživatelským jménem. Před povolením přístupu klienta ke službě ověřte veřejný klíč RSA prezentovaný klientem porovnáním s uloženým veřejným klíčem pro prezentované uživatelské jméno. To předpokládá, že jste vytvořili proces registrace, kdy uživatelé mohou zaregistrovat svá uživatelská jména a přidružit je k vlastním veřejným klíčům RSA.  
  
## <a name="client-credentials"></a>Pověření klienta  
 Pověření klienta se používají k ověření klienta ke službám v případech, kdy je vyžadováno vzájemné ověřování. Část můžete použít k určení certifikátů služeb pro scénáře, kde klient musí zabezpečit zprávy do služby s certifikátem služby.  
  
 Můžete také nakonfigurovat klienta jako součást scénáře federace pro použití vydaných tokenů ze zabezpečené služby tokenů nebo místního vystavitele tokenů. Další informace o federovaných scénářích naleznete v [tématu Federation and Issueed Tokens](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md). Všechna pověření klienta jsou nalezeny pod [ \<koncovým bodemBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md), jak je znázorněno v následujícím kódu.  
  
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
  
#### <a name="clientcertificate-element"></a>\<klientCertificate> Element  
 Nastavte certifikát použitý k ověření klienta pomocí tohoto prvku. Další informace naleznete v [tématu How to: Specify Client Credential Values](../../../../docs/framework/wcf/how-to-specify-client-credential-values.md).  
  
#### <a name="httpdigest"></a>\<httpDigest>  
 Tato funkce musí být povolena pomocí služby Active Directory v systému Windows a internetové informační služby (IIS). Další informace naleznete [v tématu Digest Authentication in IIS 6.0](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc782661(v=ws.10)).  
  
#### <a name="issuedtoken-element"></a>\<issuedToken> Element  
 [ \<IssuedToken>](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md) obsahuje prvky používané ke konfiguraci místního vystavitela tokenů nebo chování používaného se službou tokenů zabezpečení. Pokyny k konfiguraci klienta pro použití místního vystavitele naleznete v [tématu Postup: Konfigurace místního vystavitele](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).  
  
#### <a name="localissueraddress"></a>\<> localIssuerAddress  
 Určuje výchozí adresu služby tokenů zabezpečení. Používá se v <xref:System.ServiceModel.WSFederationHttpBinding> případě, že neposkytuje adresu URL služby tokenů zabezpečení nebo pokud `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` `null`je adresa vystavittele federované vazby nebo . V takových případech <xref:System.ServiceModel.Description.ClientCredentials> musí být nakonfigurován s adresou místního vystavittele a vazbou pro komunikaci s tímto vydavatelem.  
  
#### <a name="issuerchannelbehaviors"></a>\<issuerChannelBehaviors>  
 Pomocí [ \<>issuerChannelBehaviors](../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md) přidejte chování klienta WCF používané při komunikaci se službou tokenů zabezpečení. Definujte chování klienta v části [ \<>koncového boduChování.](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md) Chcete-li použít definované chování, přidejte <`add`> element u elementu `<issuerChannelBehaviors>` se dvěma atributy. Nastavte `issuerAddress` adresu URL služby tokenů zabezpečení `behaviorConfiguration` a nastavte atribut na název definovaného chování koncového bodu, jak je znázorněno v následujícím příkladu.  
  
```xml  
<clientCredentials>  
   <issuedToken>  
      <issuerChannelBehaviors>  
         <add issuerAddress="http://www.contoso.com"  
               behaviorConfiguration="clientBehavior1" />
```  
  
#### <a name="servicecertificate-element"></a>\<serviceCertificate> Element  
 Tento prvek slouží k řízení ověřování certifikátů služby.  
  
 Element [ \<defaultCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md) může uložit jeden certifikát používaný v případě, že služba neurčuje žádný certifikát.  
  
 Pomocí [ \<>scopedCertificates](../../../../docs/framework/configure-apps/file-schema/wcf/scopedcertificates-element.md) a [ \<přidejte>](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-scopedcertificates-element.md) k nastavení certifikátů služeb, které jsou přidruženy k určitým službám. Prvek `<add>` obsahuje `targetUri` atribut, který se používá k přidružení certifikátu ke službě.  
  
 Prvek [ \<>ověřování](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) určuje úroveň důvěryhodnosti používanou k ověřování certifikátů. Ve výchozím nastavení je úroveň nastavena na "ChainTrust", která určuje, že každý certifikát musí být nalezen v hierarchii certifikátů končících důvěryhodným certifikačním úřadem v horní části řetězce. Toto je nejbezpečnější režim. Můžete také nastavit hodnotu "PeerOrChainTrust", která určuje, že jsou přijímány certifikáty vydané samostatně (rovnocenný vztah důvěryhodnosti) a také certifikáty, které jsou v důvěryhodném řetězci. Tato hodnota se používá při vývoji a ladění klientů a služeb, protože certifikáty vydané samostatně nemusí být zakoupeny od důvěryhodné autority. Při nasazování klienta použijte místo toho hodnotu ChainTrust. Můžete také nastavit hodnotu na "Vlastní" nebo "Žádné". Chcete-li použít hodnotu "Vlastní", `CustomCertificateValidatorType` musíte také nastavit atribut na sestavení a typ použitý k ověření certifikátu. Chcete-li vytvořit vlastní validátor, musíte dědit z abstraktní <xref:System.IdentityModel.Selectors.X509CertificateValidator> třídy. Další informace naleznete v [tématu How to: Create a Service that Employs a Custom Certificate Validator](../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).  
  
 Prvek [ \<>ověřování](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) `RevocationMode` obsahuje atribut, který určuje způsob kontroly certifikátů pro odvolání. Výchozí hodnota je "online", což znamená, že certifikáty jsou automaticky kontrolovány pro odvolání. Další informace naleznete v [tématu Práce s certifikáty](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
## <a name="serviceauthorization"></a>Autorizace služby  
 Element [ \<serviceAuthorization>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) obsahuje prvky, které ovlivňují autorizaci, vlastní zprostředkovatele rolí a zosobnění.  
  
 Třída <xref:System.Security.Permissions.PrincipalPermissionAttribute> je použita pro metodu služby. Atribut určuje skupiny uživatelů, které mají být používány při autorizaci použití chráněné metody. Výchozí hodnota je "UseWindowsGroups" a určuje, že skupiny systému Windows, například "Správci" nebo "Uživatelé", jsou vyhledávány identity při pokusu o přístup k prostředku. Můžete také zadat "UseAspNetRoles" pro použití vlastního zprostředkovatele `system.web` rolí, který je nakonfigurován pod elementem <>, jak je znázorněno v následujícím kódu.  
  
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
  
 Následující kód ukazuje `roleProviderName` použité `principalPermissionMode` s atributem.  
  
```xml  
<behaviors>  
 <behavior name="ServiceBehaviour">
  <serviceAuthorization principalPermissionMode ="UseAspNetRoles"
                        roleProviderName ="SqlProvider" />  
</behavior>
   <!-- Other configuration code not shown. -->  
</behaviors>  
```  
  
## <a name="configuring-security-audits"></a>Konfigurace auditů zabezpečení  
 Pomocí [ \<>serviceSecurityAudit](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md) určete protokol zapsaný do protokolu a jaké typy událostí se mají protokolovat. Další informace naleznete v [tématu Auditování](../../../../docs/framework/wcf/feature-details/auditing-security-events.md).  
  
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
 Export metadat do klientů je vhodný pro servisní a klientské vývojáře, protože umožňuje stahování konfigurace a klientského kódu. Chcete-li snížit expozici služby uživatelům se zlými úmysly, je možné zabezpečit přenos pomocí mechanismu SSL přes HTTP (HTTPS). Chcete-li tak učinit, musíte nejprve svázat vhodný certifikát X.509 s konkrétním portem v počítači, který je hostitelem služby. (Další informace naleznete v [tématu Práce s certifikáty](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).) Za druhé přidejte `HttpsGetEnabled` `true` [ \<do](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md) konfigurace služby>metadata služby a nastavte atribut na . Nakonec nastavte `HttpsGetUrl` atribut na adresu URL koncového bodu metadat služby, jak je znázorněno v následujícím příkladu.  
  
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

- [Auditování](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)
- [Model zabezpečení pro infrastrukturu aplikací pro Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))
