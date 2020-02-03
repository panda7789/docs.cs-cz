---
title: Chování zabezpečení ve WCF
ms.date: 03/30/2017
ms.assetid: 513232c0-39fd-4409-bda6-5ebd5e0ea7b0
ms.openlocfilehash: 12ae9bb90752fe3ee76404948693c501fc42efe6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76730953"
---
# <a name="security-behaviors-in-wcf"></a>Chování zabezpečení ve WCF
V Windows Communication Foundation (WCF) chování upraví chování za běhu na úrovni služby nebo na úrovni koncového bodu. (Další informace o chování obecně najdete v tématu [Určení chování služby za běhu](../../../../docs/framework/wcf/specifying-service-run-time-behavior.md).) *Chování zabezpečení* umožňuje řídit protokoly přihlašovacích údajů, ověřování, autorizace a auditování. Chování můžete použít buď programováním, nebo prostřednictvím konfigurace. Toto téma se zaměřuje na konfiguraci následujících chování souvisejících s funkcemi zabezpečení:  
  
- [\<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).  
  
- [>\<ClientCredentials](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md).  
  
- [\<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md).  
  
- [\<serviceSecurityAudit >](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md).  
  
- [\<oddílu servicemetadata >](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md), což také umožňuje zadat zabezpečený koncový bod, ke kterému mají klienti přístup pro metadata.  
  
## <a name="setting-credentials-with-behaviors"></a>Nastavení přihlašovacích údajů s chováním  
 Pomocí [\<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) a [\<ClientCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) nastavte hodnoty přihlašovacích údajů pro službu nebo klienta. Základní konfigurace vazby Určuje, jestli musí být nastavené přihlašovací údaje. Pokud je například režim zabezpečení nastaven na `None`, klienti a služby se vzájemně neověřují a nevyžadují žádné přihlašovací údaje žádného typu.  
  
 Na druhé straně vazba služby může vyžadovat typ přihlašovacích údajů klienta. V takovém případě může být nutné nastavit hodnotu přihlašovacích údajů pomocí chování. (Další informace o možných typech přihlašovacích údajů najdete v tématu [Výběr typu přihlašovacích údajů](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md).) V některých případech, například když se k ověřování použijí přihlašovací údaje Windows, prostředí automaticky vytvoří skutečnou hodnotu přihlašovacích údajů a nemusíte explicitně nastavit hodnotu přihlašovacích údajů (Pokud nechcete zadat jinou sadu přihlašovacích údajů).  
  
 Všechny přihlašovací údaje služby se našly jako podřízené elementy [>\<serviceBehaviors](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md). Následující příklad ukazuje certifikát použitý jako pověření služby.  
  
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
  
## <a name="service-credentials"></a>Přihlašovací údaje služby  
 [\<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) obsahuje čtyři podřízené prvky. Prvky a jejich použití jsou popsány v následujících částech.  
  
### <a name="servicecertificate-element"></a>\<element > serviceCertificate  
 Pomocí tohoto prvku můžete zadat certifikát X. 509, který se používá k ověření služby klientům pomocí režimu zabezpečení zpráv. Pokud používáte certifikát, který se pravidelně obnovuje, pak se jeho kryptografický otisk změní. V takovém případě použijte název subjektu jako `X509FindType`, protože certifikát je možné vystavit znovu se stejným názvem subjektu.  
  
 Další informace o použití prvku naleznete v tématu [How to: zadat hodnoty přihlašovacích údajů klienta](../../../../docs/framework/wcf/how-to-specify-client-credential-values.md).  
  
### <a name="certificate-of-clientcertificate-element"></a>\<> certifikátu > elementu \<clientCertificate  
 > Element [\<certifikátu](../../../../docs/framework/configure-apps/file-schema/wcf/certificate-of-clientcertificate-element.md) použijte v případě, že služba musí mít certifikát klienta předem, aby mohl bezpečně komunikovat s klientem. K tomu dochází při použití duplexního způsobu komunikace. V typickém vzoru požadavek-odpověď klient zahrne svůj certifikát do žádosti, kterou služba používá k zabezpečení své odezvy zpátky klientovi. Duplexní způsob komunikace ale nemá žádné požadavky a odpovědi. Služba nemůže odvodit certifikát klienta od komunikace, a proto služba vyžaduje předem certifikát klienta, aby bylo možné zprávy zabezpečit klientovi. Certifikát klienta je nutné získat v rámci vzdáleného počítače a zadat certifikát pomocí tohoto prvku. Další informace o duplexních službách najdete v tématu [Postupy: Vytvoření duplexního kontraktu](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).  
  
### <a name="authentication-of-clientcertificate-element"></a>\<ověřování > elementu \<clientCertificate >  
 [> Prvek\<ověřování](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) umožňuje přizpůsobit způsob ověřování klientů. Atribut `CertificateValidationMode` můžete nastavit na `None`, `ChainTrust`, `PeerOrChainTrust`, `PeerTrust`nebo `Custom`. Ve výchozím nastavení je úroveň nastavená na `ChainTrust`, která určuje, že se každý certifikát musí najít v hierarchii certifikátů, které končí *kořenovou autoritou* v horní části řetězce. Toto je nejbezpečnější režim. Můžete také nastavit hodnotu na `PeerOrChainTrust`, která určuje, že se přijímají certifikáty, které jsou držitelem licence, a také certifikáty, které jsou v důvěryhodném řetězci. Tato hodnota se používá při vývoji a ladění klientů a služeb vzhledem k tomu, že certifikáty vystavené svým držitelem nemusejí být zakoupeny důvěryhodnou autoritou. Při nasazování klienta použijte místo toho `ChainTrust`ovou hodnotu. Můžete také nastavit hodnotu na `Custom`. Pokud je nastavená hodnota `Custom`, musíte také nastavit atribut `CustomCertificateValidatorType` na sestavení a typ, který se používá k ověření certifikátu. Chcete-li vytvořit vlastní validátor, je nutné dědit z abstraktní <xref:System.IdentityModel.Selectors.X509CertificateValidator> třídy.  
  
### <a name="issuedtokenauthentication-element"></a>\<element > issuedTokenAuthentication  
 Scénář vydaného tokenu má tři fáze. V první fázi se klientovi, který se pokouší o přístup ke službě, říká *služba tokenů zabezpečení* (STS). Služba STS potom ověří klienta a následně vydá token klienta, obvykle token SAML (Security Assert Markup Language). Klient se pak vrátí ke službě s tokenem. Služba prověřuje token pro data, která umožňují službě ověřit token, a tedy klienta. K ověření tokenu musí služba znát certifikát, který používá služba Secure token Service. [\<prvek > IssuedTokenAuthentication](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) je úložiště pro jakékoli takové certifikáty služby Secure token Service. K přidání certifikátů použijte [\<knownCertificates >](../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md). Vložte [\<přidejte >](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md) pro každý certifikát, jak je znázorněno v následujícím příkladu.  
  
```xml  
<issuedTokenAuthentication>  
   <knownCertificates>  
      <add findValue="www.contoso.com"   
           storeLocation="LocalMachine" storeName="My"   
           X509FindType="FindBySubjectName" />  
    </knownCertificates>  
</issuedTokenAuthentication>  
```  
  
 Ve výchozím nastavení se certifikáty musí získat ze služby zabezpečeného tokenu. Tyto "známé" certifikáty zajistí, že ke službě budou mít přístup jenom legitimní klienti.  
  
 V federované aplikaci byste měli použít kolekci [\<allowedAudienceUris >](../../../../docs/framework/configure-apps/file-schema/wcf/allowedaudienceuris.md) , která využívá *službu Secure token Service* (STS), která vydává `SamlSecurityToken` tokeny zabezpečení. Pokud služba STS vydá token zabezpečení, může zadat identifikátor URI webových služeb, pro které je token zabezpečení určen přidáním `SamlAudienceRestrictionCondition` do tokenu zabezpečení. To umožňuje `SamlSecurityTokenAuthenticator` pro webovou službu příjemce ověřit, jestli je vydaný token zabezpečení určený pro tuto webovou službu tím, že určíte, že se tato kontrola provede následujícím způsobem:  
  
- Nastavte atribut `audienceUriMode` [\<issuedTokenAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) na `Always` nebo `BearerKeyOnly`.  
  
- Zadejte sadu platných identifikátorů URI přidáním identifikátorů URI do této kolekce. Pokud to chcete provést, vložte [\<přidat >](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-allowedaudienceuris.md) pro každý identifikátor URI.  
  
 Další informace naleznete v tématu <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.  
  
 Další informace o použití tohoto konfiguračního prvku naleznete v tématu [How to: Configure a Credentials on a služba FS (Federation Service)](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).  
  
#### <a name="allowing-anonymous-cardspace-users"></a>Povolení uživatelů anonymních CardSpace  
 Nastavením atributu `AllowUntrustedRsaIssuers` prvku `<IssuedTokenAuthentication>` na `true` explicitně umožníte každému klientovi zobrazit token, který je podepsaný libovolným párem klíčů RSA. Vystavitel není *důvěryhodný* , protože k tomuto klíči nejsou přidružená žádná data vystavitele. Uživatel karty CardSpace může vytvořit samoobslužnou kartu, která obsahuje deklarace identity, které jsou samoobslužné. Tuto možnost používejte opatrně. Chcete-li použít tuto funkci, zamyslete se s veřejným klíčem RSA jako s bezpečnějším heslem, které by mělo být uloženo v databázi společně s uživatelským jménem. Předtím, než povolíte klientskému přístupu ke službě, ověřte, že klient předložil veřejný klíč RSA pomocí porovnání s uloženým veřejným klíčem pro prezentované uživatelské jméno. To předpokládá, že jste zavedli proces registrace, kdy si uživatelé můžou zaregistrovat svá uživatelská jména a přidružit je k veřejným klíčům RSA vystaveným svým držitelem.  
  
## <a name="client-credentials"></a>Pověření klienta  
 Pověření klienta slouží k ověřování klienta se službami v případech, kdy je nutné vzájemné ověřování. V části můžete zadat certifikáty služeb pro scénáře, ve kterých musí klient zabezpečit zprávy do služby s certifikátem služby.  
  
 Klienta můžete také nakonfigurovat jako součást scénáře federace pro použití vydaných tokenů ze služby tokenu zabezpečení nebo místního vystavitele tokenů. Další informace o federovaných scénářích najdete v tématu [federace a vystavené tokeny](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md). Všechna pověření klienta se nacházejí v [>\<endpointBehaviors](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md), jak je znázorněno v následujícím kódu.  
  
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
  
#### <a name="clientcertificate-element"></a>\<> elementu clientCertificate  
 Nastavte certifikát použitý k ověření klienta s tímto elementem. Další informace najdete v tématu [Postupy: určení hodnot přihlašovacích údajů klienta](../../../../docs/framework/wcf/how-to-specify-client-credential-values.md).  
  
#### <a name="httpdigest"></a>\<httpDigest >  
 Tato funkce musí být povolená se službou Active Directory ve Windows a Internetová informační služba (IIS). Další informace najdete v tématu [ověřování algoritmem Digest ve službě IIS 6,0](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc782661(v=ws.10)).  
  
#### <a name="issuedtoken-element"></a>\<element > třídy IssuedToken  
 [>\<třídy IssuedToken](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md) obsahuje prvky, které slouží ke konfiguraci místního vystavitele tokenů nebo chování používaného se službou tokenu zabezpečení. Pokyny ke konfiguraci klienta pro použití místního vystavitele najdete v tématu [Postupy: Konfigurace místního vystavitele](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).  
  
#### <a name="localissueraddress"></a>\<localIssuerAddress >  
 Určuje výchozí adresu služby tokenu zabezpečení. Tato část se používá, když <xref:System.ServiceModel.WSFederationHttpBinding> neposkytuje adresu URL pro službu tokenu zabezpečení nebo pokud je adresa vydavatele federované vazby `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` nebo `null`. V takových případech musí být <xref:System.ServiceModel.Description.ClientCredentials> nakonfigurovaný s adresou místního vystavitele a vazbou, která se má použít ke komunikaci s tímto vystavitelem.  
  
#### <a name="issuerchannelbehaviors"></a>\<issuerChannelBehaviors >  
 [>\<issuerChannelBehaviors](../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md) můžete použít k přidání chování klienta WCF používaného při komunikaci se službou tokenu zabezpečení. V části [\<endpointBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md) definujte chování klienta. Chcete-li použít definované chování, přidejte <`add`> elementu do prvku `<issuerChannelBehaviors>` se dvěma atributy. Nastavte `issuerAddress` na adresu URL služby tokenu zabezpečení a nastavte atribut `behaviorConfiguration` na název definovaného chování koncového bodu, jak je znázorněno v následujícím příkladu.  
  
```xml  
<clientCredentials>  
   <issuedToken>  
      <issuerChannelBehaviors>  
         <add issuerAddress="http://www.contoso.com"  
               behaviorConfiguration="clientBehavior1" />     
```  
  
#### <a name="servicecertificate-element"></a>\<element > serviceCertificate  
 Tento prvek použijte k řízení ověřování certifikátů služby.  
  
 Element [\<defaultCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md) může ukládat jeden certifikát, který se používá, když služba neurčuje žádný certifikát.  
  
 Pomocí [\<scopedCertificates >](../../../../docs/framework/configure-apps/file-schema/wcf/scopedcertificates-element.md) a [\<přidejte >](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-scopedcertificates-element.md) pro nastavení certifikátů služby, které jsou přidruženy k určitým službám. Element `<add>` obsahuje atribut `targetUri`, který se používá k přidružení certifikátu ke službě.  
  
 Prvek [\<authentication >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) určuje úroveň důvěryhodnosti použitou k ověřování certifikátů. Ve výchozím nastavení je úroveň nastavena na "ChainTrust", která určuje, že každý certifikát musí být nalezen v hierarchii certifikátů, které končí důvěryhodnou certifikační autoritou v horní části řetězce. Toto je nejbezpečnější režim. Tuto hodnotu můžete také nastavit na "PeerOrChainTrust", která určuje, že se přijímají certifikáty s certifikátem (Trust peer) a také certifikáty, které jsou v důvěryhodném řetězci. Tato hodnota se používá při vývoji a ladění klientů a služeb vzhledem k tomu, že certifikáty vystavené svým držitelem nemusejí být zakoupeny důvěryhodnou autoritou. Při nasazování klienta použijte místo toho hodnotu "ChainTrust". Můžete také nastavit hodnotu "vlastní" nebo "none". Chcete-li použít hodnotu Custom (vlastní), musíte také nastavit atribut `CustomCertificateValidatorType` na sestavení a typ použitý k ověření certifikátu. Chcete-li vytvořit vlastní validátor, je nutné dědit z abstraktní <xref:System.IdentityModel.Selectors.X509CertificateValidator> třídy. Další informace najdete v tématu [Postup: vytvoření služby, která využívá vlastní validátor certifikátů](../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).  
  
 Element [\<authentication >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) obsahuje atribut `RevocationMode`, který určuje, jak se kontrolují certifikáty pro odvolání. Výchozí hodnota je "online", což znamená, že se certifikáty automaticky kontrolují pro odvolání. Další informace najdete v tématu [práce s certifikáty](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
## <a name="serviceauthorization"></a>ServiceAuthorization  
 Element [\<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) obsahuje prvky, které mají vliv na autorizaci, vlastní poskytovatele rolí a zosobnění.  
  
 Třída <xref:System.Security.Permissions.PrincipalPermissionAttribute> se aplikuje na metodu služby. Atribut určuje skupiny uživatelů, které se mají použít při autorizaci použití chráněné metody. Výchozí hodnota je "UseWindowsGroups" a určí, že se skupiny systému Windows, například "Administrators" nebo "uživatelé", prohledávají identity, která se pokouší o přístup k prostředku. Můžete také zadat "UseAspNetRoles", chcete-li použít vlastního poskytovatele rolí, který je nakonfigurován pod <`system.web` > prvek, jak je znázorněno v následujícím kódu.  
  
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
  
 Následující kód ukazuje `roleProviderName` použit s atributem `principalPermissionMode`.  
  
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
 Pomocí [\<serviceSecurityAudit >](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md) určete protokol, na který se zapisuje zápis, a typy událostí, které se mají protokolovat. Další informace najdete v tématu [auditování](../../../../docs/framework/wcf/feature-details/auditing-security-events.md).  
  
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
 Export metadat do klientů je pohodlný pro vývojáře služeb a klientů, protože umožňuje stažení konfigurace a kódu klienta. Aby se snížila pravděpodobnost, že se služba vystavuje uživatelům se zlými úmysly, je možné zabezpečit přenos pomocí mechanismu SSL přes protokol HTTP (HTTPS). K tomu je nutné nejdřív navazovat vhodný certifikát X. 509 na konkrétní port v počítači, který je hostitelem služby. (Další informace najdete v tématu [práce s certifikáty](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).) Potom do konfigurace služby přidejte [\<oddílu servicemetadata >](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md) a nastavte atribut `HttpsGetEnabled` na `true`. Nakonec nastavte atribut `HttpsGetUrl` na adresu URL koncového bodu metadat služby, jak je znázorněno v následujícím příkladu.  
  
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
- [Model zabezpečení pro Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))
