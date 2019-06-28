---
title: Federace
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation [WCF]
ms.assetid: 2f1e646f-8361-48d4-9d5d-1b961f31ede4
ms.openlocfilehash: 376448502b7b9c7002213be5c3437849a3868166
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/28/2019
ms.locfileid: "67425038"
---
# <a name="federation"></a>Federace
Toto téma nabízí stručný přehled konceptů zabezpečení. Popisuje také podporu Windows Communication Foundation (WCF) pro nasazení architektury zabezpečení. Ukázková aplikace, které ukazuje, federace, naleznete v tématu [ukázka federace](../../../../docs/framework/wcf/samples/federation-sample.md).  
  
## <a name="definition-of-federated-security"></a>Definice zabezpečení  
 Zabezpečení umožňuje čisté oddělení mezi službu, kterou klient přistupuje a přidružené procedury ověřování a autorizace. Zabezpečení také umožňuje spolupráci mezi více systémy, sítě a organizací ve sférách různých důvěryhodnosti.  
  
 WCF poskytuje podporu pro sestavování a nasazování distribuovaných systémů, které využívají zabezpečení.  
  
### <a name="elements-of-a-federated-security-architecture"></a>Prvky architektury zabezpečení  
 Architektura zabezpečení má tři klíčové prvky, jak je popsáno v následující tabulce.  
  
|Prvek|Popis|  
|-------------|-----------------|  
|Domain/realm|Jedna jednotka správy zabezpečení nebo vztah důvěryhodnosti. Typické domény může obsahovat jednu organizaci.|  
|Federace|Sada domény, které mají vztah důvěryhodnosti. Úroveň důvěryhodnosti mohou lišit, ale obvykle zahrnuje ověřování a téměř vždy obsahuje autorizaci. Typické federace může obsahovat několik organizací, které mají vztah důvěryhodnosti pro sdílený přístup k sadu prostředků.|  
|Služba tokenů zabezpečení (STS)|Webová služba, která vydává tokeny zabezpečení; To znamená je založen na důkaz, že důvěřuje na všechny uživatele, kteří důvěřuje kontrolní výrazy. Tento balíček je základem zprostředkování vztahu důvěryhodnosti mezi doménami.|  
  
### <a name="example-scenario"></a>Příklad scénáře  
 Následující obrázek znázorňuje příklad zabezpečení:  
  
 ![Diagram znázorňující scénář typické federovaného zabezpečení.](./media/federation/typical-federated-security-scenario.gif)  
  
 Tento scénář obsahuje dvě organizace: A a B B. organizace má webový prostředek (webová služba), někteří uživatelé v organizaci A najít užitečné.  
  
> [!NOTE]
>  Tato část používá podmínky *prostředků*, *služby*, a *webovou službu* Zaměnitelně.  
  
 Organizace B obvykle vyžaduje, že uživatel z organizace A zadat nějakou platnou formu ověřování před přístupu ke službě. Kromě toho organizace může také vyžadovat, že uživatel oprávnění k přístupu na příslušném konkrétního prostředku. Jedním ze způsobů řešení tohoto problému a umožňují uživatelům v organizaci A pro přístup k prostředku v organizaci B je následujícím způsobem:  
  
- Uživatelé v organizaci A zaregistrovat své přihlašovací údaje (uživatelské jméno a heslo) s organizací B.  
  
- Během přístupu k prostředkům uživatelů z organizace A poskytl svá pověření pro organizaci B a ověření před přístupem k prostředku.  
  
 Tento přístup má tři významné nevýhody:  
  
- Organizace B má ke správě přihlašovacích údajů pro uživatele z organizace A kromě správy pověření své místní uživatelé.  
  
- Uživatelé v organizaci A nemusíte Udržovat další sadu pověření (to znamená, nezapomeňte další uživatelské jméno a heslo) kromě přihlašovací údaje, obvykle používají pro získání přístupu k prostředkům v rámci organizace A. To obvykle doporučuje praxe používání stejné uživatelské jméno a heslo ve víc lokalitách služby, který je slabé bezpečnostní opatření.  
  
- Architektura nejsou adekvátní jako víc organizací vnímat prostředek na organizace B tak, jak se některé hodnoty.  
  
 Alternativním přístupem, což reaguje na výše uvedené nevýhody, má odlišnou úroveň zabezpečení. V takovém případě organizací A a B navázání vztahu důvěryhodnosti a využívat službu tokenů zabezpečení (STS) umožňující ručním vytvořen vztah důvěryhodnosti.  
  
 V architektuře zabezpečení uživatelům v organizaci A vědět, že pokud chtějí přístup k webové službě v organizaci B, který se musí poskytnout token platný zabezpečení ze služby STS na organizaci B, která ověřuje a autorizuje jeho přístup k konkrétní službu.  
  
 O kontaktování služby tokenů zabezpečení B, uživatelé dostanou jinou úroveň dereference ze zásady přidružené k Služba tokenů zabezpečení. Platný zabezpečení se musí poskytnout token od služby STS A (to znamená, sféry klienta vztahu důvěryhodnosti) před B služby tokenů zabezpečení můžete jim nabídnete token zabezpečení. Toto je důsledkem této vztah důvěryhodnosti mezi dvěma organizacemi a znamená, že organizace B nemá ke správě identit uživatelů z organizace A. V praxi, služba tokenů zabezpečení B obvykle má hodnotu null `issuerAddress` a `issuerMetadataAddress`. Další informace najdete v tématu [jak: Konfigurace místního vystavitele](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md). V takovém případě klienta consults místních zásad vyhledejte STS A. Tato konfigurace se nazývá *domovskou sféru federace* a škáluje líp, protože není nutné udržovat informace o STS A. B služby tokenů zabezpečení  
  
 Uživatelé pak obraťte se na službu tokenů zabezpečení v organizaci A a získat token zabezpečení tím, že předloží přihlašovacími údaji, které běžně používáte pro přístup k žádnému jinému prostředku v rámci organizace A. To také řeší problém uživatelé museli udržovat několik sad přihlašovacích údajů nebo ve víc lokalitách služby pomocí jednou sadou přihlašovacích údajů.  
  
 Jakmile uživatelé získat token zabezpečení ze služby STS A jsou k dispozici token, který má služba tokenů zabezpečení B. organizace B pokračuje k autorizaci požadavků uživatelů a vydá token zabezpečení pro uživatele ze své vlastní sada tokenů zabezpečení. Uživatele můžete předložit jejich token prostředku v organizaci B a přístup ke službě.  
  
## <a name="support-for-federated-security-in-wcf"></a>Podpora pro zabezpečení ve WCF  
 WCF poskytuje kompletní podpory pro nasazení architektury zabezpečení prostřednictvím [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).  
  
 [ \<WsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) element poskytuje pro zabezpečené, spolehlivé a interoperabilní vazbu, která zahrnuje použití protokolu HTTP jako podkladový přenosový mechanismus pro komunikaci styl požadavek odpověď, Když text a XML jako přenosový formát pro kódování.  
  
 Použití [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) federovaného zabezpečení scénář mohou být oddělené do dvou logicky nezávislý fází, jak je popsáno v následujících částech.  
  
### <a name="phase-1-design-phase"></a>Fáze 1: Fáze návrhu  
 Během fáze návrhu, klient použije [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) zásadách zpřístupňuje koncový bod služby a shromažďování požadavky služby ověřování a autorizaci. Příslušný proxy servery jsou sestavené tak, aby vytvořit následující vzor komunikace zabezpečení u klienta:  
  
- Získáte token zabezpečení ze služby STS ve vztahu důvěryhodnosti sféry klienta.  
  
- K dispozici token na službu STS ve sféře vztah důvěryhodnosti služby.  
  
- Získáte token zabezpečení ze služby STS ve sféře vztah důvěryhodnosti služby.  
  
- K dispozici token, který má služba pro přístup ke službě.  
  
### <a name="phase-2-run-time-phase"></a>Fáze 2: Fáze za běhu  
 Během fáze za běhu klient vytvoří instanci objektu třídy klienta WCF a provede volání pomocí klienta WCF. Základní architektury WCF zpracovává výše uvedené kroky v modelu zabezpečení komunikace a umožňuje klientovi bez problémů využívat služby.  
  
## <a name="sample-implementation-using-wcf"></a>Ukázková implementace pomocí technologie WCF  
 Následující obrázek znázorňuje ukázku implementace pro architekturu zabezpečení s využitím nativní podpory z WCF.  
  
 ![Diagram znázorňující ukázku implementace zabezpečení federace.](./media/federation/federated-security-implementation.gif)  
  
### <a name="example-myservice"></a>Příklad Moje_služba  
 Služba `MyService` poskytuje jeden koncový bod prostřednictvím `MyServiceEndpoint`. Následující obrázek znázorňuje adresa, vazba a kontrakt přidružený k koncový bod.  
  
 ![Diagram znázorňující MyServiceEndpoint podrobnosti.](./media/federation/myserviceendpoint-details.gif)  
  
 Koncový bod služby `MyServiceEndpoint` používá [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) a vyžaduje platný token zabezpečení kontrolní výrazy SAML (Markup Language) pomocí `accessAuthorized` vydané služby serveru B. služby tokenů zabezpečení deklarace identity To je určeno deklarativně v konfiguraci služby.  
  
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
>  Bod drobným potřeba poznamenat týkající se deklarací vyžadované `MyService`. Druhý obrázek označuje, že `MyService` vyžaduje token SAML se `accessAuthorized` deklarací identity. Přesněji, určuje typ deklarace identity, aby `MyService` vyžaduje. Plně kvalifikovaný název tohoto typu deklarace identity je `http://tempuri.org:accessAuthorized` (spolu s přidružené oboru názvů), který se používá v konfiguračním souboru služby. Hodnota této deklarace indikuje přítomnost této deklarace identity a předpokládá, že je nastavena na `true` službou STS B.  
  
 V době běhu je vynucuje tuto zásadu `MyServiceOperationRequirement` třídu, která je implementovaná jako součást `MyService`.  
  
 [!code-csharp[C_Federation#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#0)]
 [!code-vb[C_Federation#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#0)]  
[!code-csharp[C_Federation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#1)]
[!code-vb[C_Federation#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#1)]  
  
#### <a name="sts-b"></a>STS B  
 Následující obrázek znázorňuje STS B. Jak bylo uvedeno dříve, služby tokenů zabezpečení (STS) je také webovou službu a může mít jeho přidruženými koncovými body, zásad a tak dále.  
  
 ![Diagram znázorňující služby tokenů zabezpečení B.](./media/federation/myservice-security-token-service-b.gif)  
  
 Služba tokenů zabezpečení B poskytuje jeden koncový bod, volá se `STSEndpoint` , který lze použít k žádosti o tokeny zabezpečení. Konkrétně STS B vystavuje tokeny SAML s `accessAuthorized` deklarace identity, které lze zobrazit na `MyService` služeb – web pro přístupu ke službě. Však vyžaduje, aby službu STS B uživatelé, předložit platný token SAML vydané A Služba tokenů zabezpečení, který obsahuje `userAuthenticated` deklarací identity. To je určeno deklarativně v konfiguraci služby tokenů zabezpečení.  
  
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
>  Znovu `userAuthenticated` deklarace identity je typ deklarace identity, který vyžaduje službu STS B. Plně kvalifikovaný název tohoto typu deklarace identity je `http://tempuri.org:userAuthenticated` (spolu s přidružené oboru názvů), který se používá v konfiguračním souboru služby tokenů zabezpečení. Hodnota této deklarace indikuje přítomnost této deklarace identity a předpokládá, že je nastavena na `true` službou STS A.  
  
 V době běhu `STS_B_OperationRequirement` třídě vynucuje tuto zásadu, která je implementovaná jako součást služby serveru B. služby tokenů zabezpečení  
  
 [!code-csharp[C_Federation#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#2)]
 [!code-vb[C_Federation#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#2)]  
  
 Pokud kontrola přístupu je jasné, služba tokenů zabezpečení B vydá token SAML s `accessAuthorized` deklarací identity.  
  
 [!code-csharp[C_Federation#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#3)]
 [!code-vb[C_Federation#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#3)]  
  
#### <a name="sts-a"></a>STS A  
 Následující obrázek znázorňuje STS A.  
  
 ![Federace](../../../../docs/framework/wcf/feature-details/media/sts-b.gif "STS_B")  
  
 Podobně jako služba tokenů zabezpečení B, A Služba tokenů zabezpečení je také webovou službu, která vydává tokeny zabezpečení a poskytuje jeden koncový bod pro tento účel. Ale používá jinou vazbou (`wsHttpBinding`) a vyžaduje, aby uživatelé k dispozici platný [!INCLUDE[infocard](../../../../includes/infocard-md.md)] s `emailAddress` deklarací identity. V odpovědi, vystavuje tokeny SAML s `userAuthenticated` deklarací identity. To je určeno deklarativně v konfiguraci služby.  
  
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
    <endpoint>  
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
  
 V době běhu `STS_A_OperationRequirement` třídy vynucuje tuto zásadu, která je implementovaná jako součást služby tokenů zabezpečení A.  
  
 [!code-csharp[C_Federation#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#4)]
 [!code-vb[C_Federation#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#4)]  
  
 Pokud je přístup `true`, služba tokenů zabezpečení A vydá token SAML s `userAuthenticated` deklarací identity.  
  
 [!code-csharp[C_Federation#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#5)]
 [!code-vb[C_Federation#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#5)]  
  
### <a name="client-at-organization-a"></a>Klient v organizaci A  
 Následující obrázek znázorňuje klienta v organizaci A spolu s jednotlivými kroky při vytváření `MyService` volání. Funkční součásti jsou také zahrnuté pro úplnost.  
  
 ![Diagram znázorňující kroky při volání služby Moje_služba.](./media/federation/federation-myservice-service-call-process.gif)  
  
## <a name="summary"></a>Souhrn  
 Zabezpečení nabízí čisté dělení zodpovědnosti a pomáhá vytvářet zabezpečené, škálovatelné služby architektury. Jako platformu pro sestavování a nasazování distribuovaných aplikací WCF poskytuje nativní podporu pro implementaci zabezpečení.  
  
## <a name="see-also"></a>Viz také:

- [Zabezpečení](../../../../docs/framework/wcf/feature-details/security.md)
