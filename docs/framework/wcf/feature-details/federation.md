---
title: metadata
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation [WCF]
ms.assetid: 2f1e646f-8361-48d4-9d5d-1b961f31ede4
ms.openlocfilehash: 9616a5afb88e46bb5d69f1cd253c854cc1684d9f
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81464188"
---
# <a name="federation"></a>metadata
Toto téma obsahuje stručný přehled konceptu federovaného zabezpečení. Popisuje také podporu Windows Communication Foundation (WCF) pro nasazení federovaných architektur zabezpečení. Ukázková aplikace, která demonstruje federaci, naleznete [v tématu Federation Sample](../../../../docs/framework/wcf/samples/federation-sample.md).  
  
## <a name="definition-of-federated-security"></a>Definice federovaného zabezpečení  
 Federované zabezpečení umožňuje čisté oddělení mezi službou, ke které klient přistupuje, a souvisejícími ověřovacími a autorizačními postupy. Federované zabezpečení také umožňuje spolupráci napříč různými systémy, sítěmi a organizacemi v různých sférách důvěryhodnosti.  
  
 WCF poskytuje podporu pro vytváření a nasazování distribuovaných systémů, které používají federované zabezpečení.  
  
### <a name="elements-of-a-federated-security-architecture"></a>Prvky architektury federovaného zabezpečení  
 Federovaná architektura zabezpečení má tři klíčové prvky, jak je popsáno v následující tabulce.  
  
|Prvek|Popis|  
|-------------|-----------------|  
|Doména/sféra|Jedna jednotka správy nebo důvěry v zabezpečení. Typická doména může zahrnovat jednu organizaci.|  
|metadata|Kolekce domén, které vytvořily vztah důvěryhodnosti. Úroveň důvěryhodnosti se může lišit, ale obvykle zahrnuje ověřování a téměř vždy zahrnuje autorizaci. Typická federace může zahrnovat několik organizací, které vytvořily vztah důvěryhodnosti pro sdílený přístup k sadě prostředků.|  
|Služba tokenů zabezpečení (STS)|Webová služba, která vydává tokeny zabezpečení. to znamená, že činí tvrzení založená na důkazech, kterým důvěřuje, tomu, komu důvěřuje. To tvoří základ zprostředkovatele důvěryhodnosti mezi doménami.|  
  
### <a name="example-scenario"></a>Ukázkový scénář  
 Následující obrázek znázorňuje příklad federovaného zabezpečení:  
  
 ![Diagram znázorňující typický federovaný scénář zabezpečení.](./media/federation/typical-federated-security-scenario.gif)  
  
 Tento scénář zahrnuje dvě organizace: A a B. Organizace B má webový prostředek (webovou službu), který někteří uživatelé v organizaci A považují za cenné.  
  
> [!NOTE]
> Tato část používá termíny *zdroj*, *služba*a *webová služba* zaměnitelně.  
  
 Organizace B obvykle vyžaduje, aby uživatel z organizace A před přístupem ke službě poskytl nějakou platnou formu ověřování. Kromě toho organizace může také vyžadovat, aby uživatel byl oprávněn k přístupu k určitému prostředku. Jedním ze způsobů, jak tento problém vyřešit a umožnit uživatelům v organizaci A přístup k prostředku v organizaci B, je následující:  
  
- Uživatelé z organizace A zaregistrují svá pověření (uživatelské jméno a heslo) u organizace B.  
  
- Během přístupu k prostředkům uživatelé z organizace A prezentují svá pověření organizaci B a jsou ověřeni před přístupem k prostředku.  
  
 Tento přístup má tři významné nevýhody:  
  
- Organizace B musí spravovat pověření pro uživatele z organizace A kromě správy pověření místních uživatelů.  
  
- Uživatelé v organizaci: Kromě pověření, která obvykle používají k získání přístupu k prostředkům v rámci organizace A, je třeba udržovat další sadu pověření (tj. zapamatovat další uživatelské jméno a heslo). To obvykle podporuje praxi používání stejného uživatelského jména a hesla na více místech služeb, což je slabé bezpečnostní opatření.  
  
- Architektura není škálovat jako více organizací vnímají prostředek v organizaci B jako nějakou hodnotu.  
  
 Alternativním přístupem, který řeší výše uvedené nevýhody, je využití federovaného zabezpečení. V tomto přístupu organizace A a B vytvořit vztah důvěryhodnosti a zaměstnávat službu tokenů zabezpečení (STS) povolit zprostředkování zavedeného vztahu důvěryhodnosti.  
  
 Ve federované architektuře zabezpečení uživatelé z organizace A vědí, že pokud chtějí získat přístup k webové službě v organizaci B, musí předložit platný token zabezpečení z STS v organizaci B, který ověřuje a autorizuje jejich přístup ke konkrétní službě.  
  
 Při kontaktování STS B, uživatelé obdrží jinou úroveň dereference ze zásady spojené s STS. Musí předložit platný token zabezpečení z STS A (to znamená, že správa důvěryhodnosti klienta) před STS B může vydat token zabezpečení. Toto je důsledek vztahu důvěryhodnosti vytvořeného mezi oběma organizacemi a znamená, že organizace B nemusí spravovat identity pro uživatele z organizace A. V praxi MÁ STS B `issuerAddress` obvykle `issuerMetadataAddress`null a . Další informace naleznete v [tématu How to: Configure a Local Issuer](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md). V takovém případě klient konzultuje místní zásady k vyhledání STS A. Tato konfigurace se nazývá *federace domácí sféry* a lépe se škáluje, protože STS B nemusí udržovat informace o STS A.  
  
 Uživatelé pak kontaktovat STS v organizaci A a získat token zabezpečení tím, že předloží ověřovací pověření, které obvykle používají k získání přístupu k jinému prostředku v rámci organizace A. To také zmírňuje problém uživatelů, kteří musí udržovat více sad pověření nebo používat stejnou sadu pověření na více serverech služeb.  
  
 Jakmile uživatelé získají token zabezpečení z STS A, předloží token sts B. Organizace B pokračuje k autorizaci požadavků uživatelů a vydává token zabezpečení uživatelům z vlastní sady tokenů zabezpečení. Uživatelé pak mohou prezentovat svůj token prostředku v organizaci B a získat přístup ke službě.  
  
## <a name="support-for-federated-security-in-wcf"></a>Podpora federovaného zabezpečení v WCF  
 WCF poskytuje podporu na klíč pro nasazení federovaných architektur zabezpečení prostřednictvím [ \<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).  
  
 [ \<WsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) prvek poskytuje zabezpečené, spolehlivé, interoperabilní vazby, která zahrnuje použití protokolu HTTP jako základní mechanismus přenosu pro styl komunikace požadavek odpověď, použití textu a XML jako formát drátu pro kódování.  
  
 Použití [ \<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) ve federovaném scénáři zabezpečení lze oddělit do dvou logicky nezávislých fází, jak je popsáno v následujících částech.  
  
### <a name="phase-1-design-phase"></a>Fáze 1: Fáze návrhu  
 Během fáze návrhu klient používá [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ke čtení zásad koncový bod služby zveřejňuje a shromažďovat požadavky na ověřování a autorizaci služby. Příslušné proxy servery jsou konstruovány tak, aby vytvořily následující federovaný vzor komunikace zabezpečení v klientovi:  
  
- Získejte token zabezpečení ze služby STS ve sféře důvěryhodnosti klienta.  
  
- Prezentujte token sts ve sféře vztahu důvěryhodnosti služby.  
  
- Získejte token zabezpečení ze služby STS ve sféře důvěryhodnosti služby.  
  
- Prezentujte token službě pro přístup ke službě.  
  
### <a name="phase-2-run-time-phase"></a>Fáze 2: Fáze běhu  
 Během fáze běhu klient vytvoří instance objektu třídy wcf klienta a provede volání pomocí klienta WCF. Základní rámec WCF zpracovává výše uvedené kroky ve federované matné komunikace zabezpečení vzor a umožňuje klientovi bezproblémově využívat službu.  
  
## <a name="sample-implementation-using-wcf"></a>Ukázková implementace pomocí WCF  
 Následující obrázek znázorňuje ukázkovou implementaci pro federovovnou architekturu zabezpečení pomocí nativní podpory z WCF.  
  
 ![Diagram znázorňující ukázkovou implementaci zabezpečení Federace.](./media/federation/federated-security-implementation.gif)  
  
### <a name="example-myservice"></a>Příklad MyService  
 Služba `MyService` zpřístupňuje jeden koncový `MyServiceEndpoint`bod prostřednictvím . Následující obrázek znázorňuje adresu, vazbu a smlouvu přidruženou ke koncovému bodu.  
  
 ![Diagram znázorňující podrobnosti myserviceendpoint.](./media/federation/myserviceendpoint-details.gif)  
  
 Koncový bod `MyServiceEndpoint` služby používá>[ \<wsFederationHttpBinding](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) a vyžaduje platný token jazyka svýrazná výrazy zabezpečení (SAML) s `accessAuthorized` deklarací vydanou službou STS B. To je deklarativně zadáno v konfiguraci služby.  
  
```xml  
<system.serviceModel>  
  <services>  
    <service type="FederationSample.MyService"
        behaviorConfiguration='MyServiceBehavior'>  
        <endpoint address=""  
            binding=" wsFederationHttpBinding"  
            bindingConfiguration='MyServiceBinding'  
            contract="Federation.IMyService" />  
   </service>  
  </services>  
  
  <bindings>  
    <wsFederationHttpBinding>  
    <!-- This is the binding used by MyService. It redirects   
    clients to STS-B. -->  
      <binding name='MyServiceBinding'>  
        <security mode="Message">  
           <message issuedTokenType=  
"http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1">  
           <issuer address="http://localhost/FederationSample/STS-B/STS.svc" />  
            <issuerMetadata
           address=  
"http://localhost/FederationSample/STS-B/STS.svc/mex" />  
         <requiredClaimTypes>  
            <add claimType="http://tempuri.org:accessAuthorized" />  
         </requiredClaimTypes>  
        </message>  
      </security>  
      </binding>  
    </wsFederationHttpBinding>  
  </bindings>  
  
  <behaviors>  
    <behavior name='MyServiceBehavior'>  
      <serviceAuthorization
operationRequirementType="FederationSample.MyServiceOperationRequirement, MyService" />  
       <serviceCredentials>  
         <serviceCertificate findValue="CN=FederationSample.com"  
         x509FindType="FindBySubjectDistinguishedName"  
         storeLocation='LocalMachine'  
         storeName='My' />  
      </serviceCredentials>  
    </behavior>  
  </behaviors>  
</system.serviceModel>  
```  
  
> [!NOTE]
> Je třeba uvést jemný bod o `MyService`tvrzeních požadovaných . Druhý obrázek `MyService` označuje, že vyžaduje `accessAuthorized` token SAML s deklarací. Chcete-li být přesnější, určuje typ `MyService` deklarace, která vyžaduje. Plně kvalifikovaný název tohoto typu `http://tempuri.org:accessAuthorized` deklarace je (spolu s přidruženým oborem názvů), který se používá v konfiguračním souboru služby. Hodnota této deklarace označuje přítomnost této deklarace a `true` předpokládá se, že je nastavena na STS B.  
  
 Za běhu je tato zásada `MyServiceOperationRequirement` vynucena třídou, která `MyService`je implementována jako součást .  
  
 [!code-csharp[C_Federation#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#0)]
 [!code-vb[C_Federation#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#0)]  
[!code-csharp[C_Federation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#1)]
[!code-vb[C_Federation#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#1)]  
  
#### <a name="sts-b"></a>STS B  
 Následující obrázek znázorňuje STS B. Jak již bylo uvedeno dříve, služba tokenů zabezpečení (STS) je také webová služba a může mít přidružené koncové body, zásady a tak dále.  
  
 ![Diagram znázorňující službu tokenů zabezpečení B.](./media/federation/myservice-security-token-service-b.gif)  
  
 STS B zpřístupňuje jeden `STSEndpoint` koncový bod, volána, které lze použít k vyžádání tokeny zabezpečení. Konkrétně STS B problémy SAML `accessAuthorized` tokeny s deklarací, které mohou být prezentovány na webu `MyService` služby pro přístup ke službě. Sts B však vyžaduje, aby uživatelé předložili platný token `userAuthenticated` SAML vydaný společností STS A, který obsahuje deklaraci. To je deklarativně zadáno v konfiguraci STS.  
  
```xml  
<system.serviceModel>  
  <services>  
    <service type="FederationSample.STS_B" behaviorConfiguration=  
     "STS-B_Behavior">  
    <endpoint address=""  
              binding="wsFederationHttpBinding"  
              bindingConfiguration='STS-B_Binding'  
      contract="FederationSample.ISts" />  
    </service>  
  </services>  
  <bindings>  
    <wsFederationHttpBinding>  
    <!-- This is the binding used by STS-B. It redirects clients to   
         STS-A. -->  
      <binding name='STS-B_Binding'>  
        <security mode='Message'>  
          <message issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1">  
          <issuer address='http://localhost/FederationSample/STS-A/STS.svc' />  
          <issuerMetadata address='http://localhost/FederationSample/STS-A/STS.svc/mex'/>  
          <requiredClaimTypes>  
            <add claimType='http://tempuri.org:userAuthenticated'/>  
          </requiredClaimTypes>  
          </message>  
        </security>  
    </binding>  
   </wsFederationHttpBinding>  
  </bindings>  
  <behaviors>  
  <behavior name='STS-B_Behavior'>  
    <serviceAuthorization   operationRequirementType='FederationSample.STS_B_OperationRequirement, STS_B' />  
    <serviceCredentials>  
      <serviceCertificate findValue='CN=FederationSample.com'  
      x509FindType='FindBySubjectDistinguishedName'  
       storeLocation='LocalMachine'  
       storeName='My' />  
     </serviceCredentials>  
   </behavior>  
  </behaviors>  
</system.serviceModel>  
```  
  
> [!NOTE]
> Opět platí, že deklarace `userAuthenticated` je typ deklarace, který je vyžadován STS B. Plně kvalifikovaný název tohoto typu `http://tempuri.org:userAuthenticated` deklarace je (spolu s přidruženým oborem názvů), který se používá v konfiguračním souboru STS. Hodnota této deklarace označuje přítomnost této deklarace a `true` předpokládá se, že je nastavena na STS A.  
  
 Za běhu `STS_B_OperationRequirement` třída vynucuje tuto zásadu, která je implementována jako součást STS B.  
  
 [!code-csharp[C_Federation#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#2)]
 [!code-vb[C_Federation#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#2)]  
  
 Pokud kontrola přístupu je jasné, STS B `accessAuthorized` vydá token SAML s deklarací.  
  
 [!code-csharp[C_Federation#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#3)]
 [!code-vb[C_Federation#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#3)]  
  
#### <a name="sts-a"></a>STS A  
 Následující obrázek znázorňuje STS A.  
  
 ![metadata](../../../../docs/framework/wcf/feature-details/media/sts-b.gif "STS_B")  
  
 Podobně jako STS B, STS A je také webová služba, která vydává tokeny zabezpečení a zpřístupňuje jeden koncový bod pro tento účel. Používá však jinou`wsHttpBinding`vazbu ( ) a vyžaduje, `emailAddress` aby uživatelé předložili platný cardspace s deklarací. V reakci na to vydává tokeny SAML s deklarací. `userAuthenticated` To je deklarativně zadáno v konfiguraci služby.  
  
```xml  
<system.serviceModel>  
  <services>  
    <service type="FederationSample.STS_A" behaviorConfiguration="STS-A_Behavior">  
      <endpoint address=""  
                binding="wsHttpBinding"  
                bindingConfiguration="STS-A_Binding"  
                contract="FederationSample.ISts">  
       <identity>  
       <certificateReference findValue="CN=FederationSample.com"
                       x509FindType="FindBySubjectDistinguishedName"  
                       storeLocation="LocalMachine"
                       storeName="My" />  
       </identity>  
    </endpoint>  
  </service>  
</services>  
  
<bindings>  
  <wsHttpBinding>  
  <!-- This is the binding used by STS-A. It requires users to present  
   a CardSpace. -->  
    <binding name='STS-A_Binding'>  
      <security mode='Message'>  
        <message clientCredentialType="CardSpace" />  
      </security>  
    </binding>  
  </wsHttpBinding>  
</bindings>  
  
<behaviors>  
  <behavior name='STS-A_Behavior'>  
    <serviceAuthorization operationRequirementType=  
     "FederationSample.STS_A_OperationRequirement, STS_A" />  
      <serviceCredentials>  
  <serviceCertificate findValue="CN=FederationSample.com"  
                     x509FindType='FindBySubjectDistinguishedName'  
                     storeLocation='LocalMachine'  
                     storeName='My' />  
      </serviceCredentials>  
    </behavior>  
  </behaviors>  
</system.serviceModel>  
```  
  
 Za běhu `STS_A_OperationRequirement` třída vynucuje tuto zásadu, která je implementována jako součást STS A.  
  
 [!code-csharp[C_Federation#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#4)]
 [!code-vb[C_Federation#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#4)]  
  
 Pokud je `true`přístup , STS A vydá `userAuthenticated` token SAML s deklarací.  
  
 [!code-csharp[C_Federation#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#5)]
 [!code-vb[C_Federation#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#5)]  
  
### <a name="client-at-organization-a"></a>Client ve společnosti Organization A  
 Následující obrázek znázorňuje klienta v organizaci A `MyService` spolu s kroky, které se podílejí na volání služby. Ostatní funkční komponenty jsou také zahrnuty pro úplnost.  
  
 ![Diagram znázorňující kroky ve službě MyService volání.](./media/federation/federation-myservice-service-call-process.gif)  
  
## <a name="summary"></a>Souhrn  
 Federované zabezpečení poskytuje čisté rozdělení odpovědnosti a pomáhá vytvářet zabezpečené a škálovatelné architektury služeb. Jako platforma pro vytváření a nasazování distribuovaných aplikací poskytuje WCF nativní podporu pro implementaci federovaného zabezpečení.  
  
## <a name="see-also"></a>Viz také

- [Zabezpečení](../../../../docs/framework/wcf/feature-details/security.md)
