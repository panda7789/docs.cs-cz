---
title: Chování zabezpečení ve WCF
ms.date: 03/30/2017
ms.assetid: 513232c0-39fd-4409-bda6-5ebd5e0ea7b0
ms.openlocfilehash: 3040f2af2f9db030d8434e977167810ac83f09dd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54592806"
---
# <a name="security-behaviors-in-wcf"></a>Chování zabezpečení ve WCF
Ve Windows Communication Foundation (WCF), chování změnit chování za běhu na úrovni služby, nebo na úrovni koncového bodu. (Další informace o chování obecné naleznete v tématu [určení chování za běhu služby](../../../../docs/framework/wcf/specifying-service-run-time-behavior.md).) *Chování zabezpečení* povolit kontrolu nad přihlašovacími údaji, ověřování, autorizace a auditování protokoly. Můžete použít chování programování nebo prostřednictvím konfigurace. Toto téma se zaměřuje na konfiguraci následujících chování související s funkcemi zabezpečení:  
  
-   [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).  
  
-   [\<třídu clientCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md).  
  
-   [\<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md).  
  
-   [\<serviceSecurityAudit>](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md).  
  
-   [\<serviceMetadata >](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md), který také umožňuje určit zabezpečení koncového bodu, který klienti mají přístup k pro metadata.  
  
## <a name="setting-credentials-with-behaviors"></a>Nastavení přihlašovacích údajů s chováním  
 Použití [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) a [ \<clientCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) k nastavení hodnot přihlašovacích údajů pro službu nebo klienta. Základní vazby konfigurace určuje, zda pověření musí být nastavena. Například, pokud je režim zabezpečení nastavený na `None`, klientů a služeb nejsou navzájem ověří a vyžadují žádné přihlašovací údaje libovolného typu.  
  
 Vazby služby na druhé straně může vyžadovat typu pověření klienta. V takovém případě budete muset nastavit hodnotu přihlašovacích údajů pomocí chování. (Další informace o možných typů přihlašovacích údajů najdete v tématu [výběr typu pověření](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md).) V některých případech, například když se používají přihlašovací údaje Windows k ověření prostředí automaticky vytvoří hodnotu skutečné přihlašovací údaje a není potřeba explicitně nastavit hodnoty přihlašovacích údajů (Pokud chcete zadat jinou sadu přihlašovacích údajů).  
  
 Všechny přihlašovací údaje služby jsou dostupné jako podřízené prvky [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md). Následující příklad ukazuje certifikát, který slouží jako pověření služby.  
  
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
 [ \<ServiceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) obsahuje čtyři podřízené prvky. V následujících částech jsou uvedeny prvky a jejich použití.  
  
### <a name="servicecertificate-element"></a>\<serviceCertificate > – Element  
 Tento element slouží k určení certifikát X.509, který se používá k ověření služby klientů, kteří používají režim zabezpečených zpráv. Pokud používáte certifikát, který je pravidelně obnovovat, pak změny jeho kryptografický otisk. V takovém případě použijte název subjektu, jako `X509FindType` vzhledem k tomu, že certifikát můžete opakováno se stejným názvem subjektu.  
  
 Další informace o používání elementu najdete v tématu [jak: Zadání hodnot přihlašovacích údajů klienta](../../../../docs/framework/wcf/how-to-specify-client-credential-values.md).  
  
### <a name="certificate-of-clientcertificate-element"></a>\<certifikát > z \<clientCertificate > – Element  
 Použití [ \<certifikátu >](../../../../docs/framework/configure-apps/file-schema/wcf/certificate-of-clientcertificate-element.md) prvku, když služba musí mít certifikát klienta předem k bezpečné komunikaci s klientem. Vyvolá se při použití vzoru duplexní komunikaci. Ve vzoru obvyklejší požadavek odpověď klient zahrne svůj certifikát v požadavku, který službu používá k zabezpečení odpověď zpět klientovi. Vzor duplexní komunikaci, ale nemá žádné požadavky a odpovědi. Službu nelze odvodit certifikát klienta z komunikace a proto služba vyžaduje, aby klientský certifikát předem pro zabezpečené zprávy do klienta. Musíte získat certifikát klienta způsobem out-of-band a vyberte certifikát pro použití tohoto prvku. Další informace o duplexní služby najdete v tématu [jak: Vytvoření duplexního kontraktu](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).  
  
### <a name="authentication-of-clientcertificate-element"></a>\<ověřování > z \<clientCertificate > – Element  
 [ \<Ověřování >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) element umožňuje přizpůsobit, jak se budou ověřovat klienti. Můžete nastavit `CertificateValidationMode` atribut `None`, `ChainTrust`, `PeerOrChainTrust`, `PeerTrust`, nebo `Custom`. Ve výchozím nastavení, úroveň je nastavena `ChainTrust`, která určuje, že každý certifikát musí být nalezena v hierarchii certifikátů končí na *kořenová autorita* na začátku řetězce. Toto je nejbezpečnější režim. Můžete také nastavit hodnotu `PeerOrChainTrust`, která určuje, že jsou přijímány samostatně vydané certifikáty (peer vztahu důvěryhodnosti) a také certifikáty, které jsou v důvěryhodným řetězem. Tato hodnota se používá při vývoji a ladění klientů a služeb, protože samostatně vydané certifikáty nemusí být zakoupenému od důvěryhodné autority. Při nasazování klienta, použijte `ChainTrust` místo hodnoty. Můžete také nastavit hodnotu `Custom`. Pokud je nastavena na `Custom` hodnotu, je nutné nastavit také `CustomCertificateValidatorType` atribut na sestavení a typ použitý k ověření certifikátu. Pokud chcete vytvořit vlastní vlastní validátor, musí dědit z abstraktní <xref:System.IdentityModel.Selectors.X509CertificateValidator> třídy.  
  
### <a name="issuedtokenauthentication-element"></a>\<issuedTokenAuthentication> Element  
 Vydaný token scénář má tři fáze. V první fázi se klient pokouší o přístup ke službě označuje *služby tokenů zabezpečení* (STS). Služba tokenů zabezpečení pak ověří klienta a následně vydá klienta token, obvykle token zabezpečení kontrolní výrazy SAML (Markup Language). Klient pak vrátí ke službě s tokenem. Služba zkontroluje token pro data, která umožňuje službě ověření tokenu a proto klienta. Pokud chcete ověřit token, musí být známo certifikát, který používá služba tokenů zabezpečení ve službě. [ \<IssuedTokenAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) element je úložiště pro tyto certifikáty služba tokenů zabezpečení. Chcete-li přidat certifikáty použít [ \<knownCertificates >](../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md). Vložit [ \<Přidat >](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md) pro každý certifikát, jak je znázorněno v následujícím příkladu.  
  
```xml  
<issuedTokenAuthentication>  
   <knownCertificates>  
      <add findValue="www.contoso.com"   
           storeLocation="LocalMachine" storeName="My"   
           X509FindType="FindBySubjectName" />  
    </knownCertificates>  
</issuedTokenAuthentication>  
```  
  
 Ve výchozím nastavení certifikáty musí pocházet od Služba tokenů zabezpečení. Tyto certifikáty, ujistěte se, že, který klientům pouze bezpečných "známé" můžete přístup ke službě.  
  
 Byste měli použít [ \<allowedAudienceUris >](../../../../docs/framework/configure-apps/file-schema/wcf/allowedaudienceuris.md) kolekce ve federovaných aplikací, které využívá *služby tokenů zabezpečení* (STS), který vystavuje `SamlSecurityToken` tokeny zabezpečení. Když služba tokenů zabezpečení vydá token zabezpečení, můžete určit identifikátor URI webové služby, pro které je určen token zabezpečení tak, že přidáte `SamlAudienceRestrictionCondition` do tokenu zabezpečení. Umožňuje `SamlSecurityTokenAuthenticator` pro příjemce webovou službu, chcete-li ověřit, že token vydaný zabezpečení je určený pro tuto webovou službu tak, že určíte, že tato kontrola se stane při následujícím způsobem:  
  
-   Nastavte `audienceUriMode` atribut [ \<issuedTokenAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) k `Always` nebo `BearerKeyOnly`.  
  
-   Zadejte sadu platné identifikátory URI, tak, že přidáte identifikátory URI do této kolekce. Chcete-li to provést, vložte [ \<Přidat >](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-allowedaudienceuris.md) pro každého identifikátoru URI  
  
 Další informace naleznete v tématu <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.  
  
 Další informace o používání tento prvek konfigurace, najdete v části [jak: Konfigurace pověření ve službě Federation Service](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).  
  
#### <a name="allowing-anonymous-cardspace-users"></a>Povolení služby CardSpace anonymní uživatelé  
 Nastavení `AllowUntrustedRsaIssuers` atribut `<IssuedTokenAuthentication>` elementu `true` explicitně povoluje libovolného klienta předložit vystavený token podepsán pomocí libovolného pár klíče RSA. Vystavitel je *nedůvěryhodné* vzhledem k tomu, že klíč nemá žádná data vystavitele s ním spojená. A [!INCLUDE[infocard](../../../../includes/infocard-md.md)] uživatel může vytvořit samostatně vydané karty, která zahrnuje svým zadaná deklarací identity. Tuto možnost používejte s opatrností. Pokud chcete používat tuto funkci, přemýšlejte veřejný klíč RSA zabezpečenějším heslem, které by měla být uložena v databázi spolu s uživatelským jménem. Před povolením přístupu klientů ke službě, ověření klienta zobrazí veřejný klíč RSA porovnáním se souborem veřejného klíče uložené pro zobrazené uživatelské jméno. Předpokládá se, že jste zavedli proces registrace, kterým uživatelé mohou zaregistrovat svá uživatelská jména a přidružit samostatně vydané veřejné klíče RSA.  
  
## <a name="client-credentials"></a>Přihlašovací údaje klienta  
 Přihlašovací údaje pro klienta se používají k ověření klienta ke službám v případech, kdy je vyžaduje vzájemné ověřování. V části můžete použít k určení certifikáty služby pro scénáře, kde klient musí zabezpečené zprávy do služby pomocí certifikátu služby.  
  
 Klienta můžete také nakonfigurovat jako součást Federační scénář použití vydané tokeny z Služba tokenů zabezpečení nebo místního vystavitele tokenů. Další informace o federovaných scénářích najdete v tématu [federace a vydané tokeny](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md). Všechny přihlašovací údaje pro klienta se nacházejí v rámci [ \<endpointBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md), jak je znázorněno v následujícím kódu.  
  
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
  
#### <a name="clientcertifictate-element"></a>\<clientCertifictate > – Element  
 Nastavte certifikát používaný k ověření klienta s tímto elementem. Další informace najdete v tématu [jak: Zadání hodnot přihlašovacích údajů klienta](../../../../docs/framework/wcf/how-to-specify-client-credential-values.md).  
  
#### <a name="httpdigest"></a>\<httpDigest>  
 Musí být povolena tato funkce se službou Active Directory na Windows a Internetové informační služby (IIS). Další informace najdete v tématu [ověřování algoritmem Digest ve službě IIS 6.0](https://go.microsoft.com/fwlink/?LinkId=88443).  
  
#### <a name="issuedtoken-element"></a>\<třídy issuedToken > – Element  
 [ \<Třídy issuedToken >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md) obsahuje prvků, které slouží ke konfiguraci místního vystavitele tokeny nebo chování používaná službou tokenu zabezpečení. Pokyny ke konfiguraci klienta pro použití místního vystavitele, naleznete v tématu [jak: Konfigurace místního vystavitele](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).  
  
#### <a name="localissueraddress"></a>\<localIssuerAddress>  
 Určuje výchozí adresu služby tokenů zabezpečení. Používá se při <xref:System.ServiceModel.WSFederationHttpBinding> neposkytuje adresu URL pro službu tokenů zabezpečení, nebo když je adresa vystavitele federované vazby `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` nebo `null`. V takovém případě <xref:System.ServiceModel.Description.ClientCredentials> musí mít nakonfigurovanou adresu místního vystavitele a vazbu používají ke komunikaci s tohoto vydavatele.  
  
#### <a name="issuerchannelbehaviors"></a>\<issuerChannelBehaviors>  
 Použití [ \<issuerChannelBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md) přidat chování klienta WCF pro komunikaci se službou tokenu zabezpečení. Definování chování klienta v [ \<endpointBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md) oddílu. Chcete-li použít chování definované, přidejte <`add`> element `<issuerChannelBehaviors>` element s dva atributy. Nastavte `issuerAddress` na adresu URL služby tokenů zabezpečení a nastavte `behaviorConfiguration` atribut název chování definované koncového bodu, jak je znázorněno v následujícím příkladu.  
  
```xml  
<clientCredentials>  
   <issuedToken>  
      <issuerChannelBehaviors>  
         <add issuerAddress="http://www.contoso.com"  
               behaviorConfiguration="clientBehavior1" />     
```  
  
#### <a name="servicecertificate-element"></a>\<serviceCertificate > – Element  
 Pomocí tohoto elementu k řízení ověřování certifikáty služeb.  
  
 [ \<DefaultCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md) element můžete ukládat jeden certifikát použít při služba určuje žádný certifikát.  
  
 Použití [ \<scopedCertificates >](../../../../docs/framework/configure-apps/file-schema/wcf/scopedcertificates-element.md) a [ \<Přidat >](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-scopedcertificates-element.md) nastavit certifikáty služby, které jsou spojeny s konkrétní služby. `<add>` Obsahuje element `targetUri` atribut, který slouží k přidružení certifikátu služby.  
  
 [ \<Ověřování >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) prvek určuje úroveň vztahu důvěryhodnosti používá k ověřování certifikátů. Ve výchozím nastavení je úroveň nastavena na "ChainTrust", která určuje, že každý certifikát musí být nalezena v hierarchii certifikátů důvěryhodné certifikační autority v horní části řetězce s koncovkou. Toto je nejbezpečnější režim. Můžete také nastavit hodnotu "PeerOrChainTrust", která určuje, že jsou přijímány samostatně vydané certifikáty (peer vztahu důvěryhodnosti), stejně jako certifikáty, které jsou v důvěryhodným řetězem. Tato hodnota se používá při vývoji a ladění klientů a služeb, protože samostatně vydané certifikáty nemusí být zakoupenému od důvěryhodné autority. Při nasazování klienta, použijte hodnotu "ChainTrust". Můžete také nastavit hodnotu "Vlastní" nebo "None". Pokud chcete použít hodnotu "Vlastní", musíte taky nastavit `CustomCertificateValidatorType` atribut na sestavení a typ použitý k ověření certifikátu. Pokud chcete vytvořit vlastní vlastní validátor, musí dědit z abstraktní <xref:System.IdentityModel.Selectors.X509CertificateValidator> třídy. Další informace najdete v tématu [jak: Vytvoření služby, která používá vlastní validátor certifikátů](../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).  
  
 [ \<Ověřování >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) obsahuje element `RevocationMode` atribut, který určuje, jak kontroluje odvolání certifikátů. Výchozí hodnota je "online", což znamená, že certifikáty automaticky kontroluje odvolání. Další informace najdete v tématu [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
## <a name="serviceauthorization"></a>ServiceAuthorization  
 [ \<ServiceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) prvek obsahuje prvky, které mají vliv na ověřování, vlastní roli zprostředkovatele a zosobnění.  
  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute> Třídy je použít pro metodu služby. Atribut určuje skupiny uživatelů, kteří mají používat při autorizaci použití chráněné metody. Výchozí hodnota je "UseWindowsGroups" a určuje, že skupin Windows, jako je například "Administrators" nebo "Uživatelé," se vyhledávají identitu při pokusu o přístup k prostředku. Můžete také zadat "UseAspNetRoles" používat vlastní role poskytovatele, který je nakonfigurovaný pod <`system.web` > element, jak je znázorněno v následujícím kódu.  
  
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
 Použití [ \<serviceSecurityAudit >](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md) k určení zapisují do protokolu a jaké typy událostí do protokolu. Další informace najdete v tématu [auditování](../../../../docs/framework/wcf/feature-details/auditing-security-events.md).  
  
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
  
## <a name="secure-metadata-exchange"></a>Zabezpečené výměny metadat  
 Export metadat klientů je vhodné pro klienta a služby vývojářů, protože umožňuje soubory ke stažení kódu, konfigurace a klienta. Aby se snížila zranitelnost služby k uživateli se zlými úmysly, je možné na vyžádání bezpečného přenosu pomocí protokolu SSL přes HTTP (HTTPS) mechanismus. Uděláte to tak, musíte nejprve vytvořit vazbu vhodný certifikát X.509, na konkrétní port na počítači, který je hostitelem služby. (Další informace najdete v tématu [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).) Za druhé, přidejte [ \<serviceMetadata >](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md) do konfigurace služby a nastavte `HttpsGetEnabled` atribut `true`. Nastavte `HttpsGetUrl` atribut na adresu URL koncového bodu metadat služby, jak je znázorněno v následujícím příkladu.  
  
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
  
## <a name="see-also"></a>Viz také:
- [Auditování](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)
- [Model zabezpečení pro Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
