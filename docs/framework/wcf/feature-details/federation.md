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
ms.openlocfilehash: c31c2612b595e627b0c4c2d7fbb3a359b19ee704
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595489"
---
# <a name="federation"></a>metadata
Toto téma poskytuje stručný přehled konceptu federovaného zabezpečení. Popisuje také podporu Windows Communication Foundation (WCF) pro nasazení federovaných architektur zabezpečení. Ukázkovou aplikaci, která demonstruje federaci, najdete v tématu [federace – ukázka](../samples/federation-sample.md).  
  
## <a name="definition-of-federated-security"></a>Definice federovaného zabezpečení  
 Federované zabezpečení umožňuje čisté oddělení mezi službou, ke které klient přistupuje, a přidruženými postupy ověřování a autorizace. Federované zabezpečení také umožňuje spolupráci napříč různými systémy, sítěmi a organizacemi v různých sférách vztahů důvěryhodnosti.  
  
 WCF poskytuje podporu pro sestavování a nasazování distribuovaných systémů, které využívají federované zabezpečení.  
  
### <a name="elements-of-a-federated-security-architecture"></a>Prvky federované architektury zabezpečení  
 Architektura federovaného zabezpečení má tři klíčové prvky, jak je popsáno v následující tabulce.  
  
|Prvek|Popis|  
|-------------|-----------------|  
|Doména nebo sféra|Jediná jednotka správy zabezpečení nebo vztahu důvěryhodnosti. Typická doména může zahrnovat jednu organizaci.|  
|metadata|Kolekce domén, které mají zavedený vztah důvěryhodnosti. Úroveň důvěryhodnosti se může lišit, ale obvykle zahrnuje ověřování a téměř vždy zahrnuje autorizaci. Typická federace může zahrnovat řadu organizací, které navázaly důvěryhodnost pro sdílený přístup k sadě prostředků.|  
|Služba tokenů zabezpečení (STS)|Webová služba, která vydává tokeny zabezpečení. To znamená, že provádí kontrolní výrazy na základě legitimace, kterou důvěřuje, aby ji whomever důvěřuje. Tato forma je základem vztahu důvěryhodnosti mezi doménami.|  
  
### <a name="example-scenario"></a>Ukázkový scénář  
 Následující ilustrace znázorňuje příklad federovaného zabezpečení:  
  
 ![Diagram znázorňující Typický scénář federovaného zabezpečení](./media/federation/typical-federated-security-scenario.gif)  
  
 Tento scénář zahrnuje dvě organizace: a a B. organizace B má webový prostředek (webovou službu), který někteří uživatelé v organizaci vyhledali jako cenné.  
  
> [!NOTE]
> V této části se používají *prostředky*, *služby*a *webové služby* , které jsou zaměnitelné.  
  
 Organizace B obvykle vyžaduje, aby uživatel z organizace A před přístupem ke službě poskytoval určitou platnou formu ověřování. Kromě toho může organizace také vyžadovat, aby uživatel byl autorizovaný pro přístup k příslušnému prostředku. Jedním ze způsobů, jak tento problém vyřešit, a umožnit uživatelům v organizaci A přístup k prostředkům v organizaci B je následující:  
  
- Uživatelé z organizace registrují svá pověření (uživatelské jméno a heslo) s organizací B.  
  
- Během přístupu k prostředkům uživatelé z organizace A předloží své přihlašovací údaje organizaci B a ověřují se před přístupem k prostředku.  
  
 Tento přístup má tři významné nevýhody:  
  
- Organizace B musí spravovat přihlašovací údaje pro uživatele z organizace A navíc ke správě přihlašovacích údajů místních uživatelů.  
  
- Uživatelé v organizaci potřebují zachovat další sadu přihlašovacích údajů (to znamená, že si zapamatuje dodatečné uživatelské jméno a heslo) Kromě přihlašovacích údajů, které běžně používají k získání přístupu k prostředkům v organizaci A. To obvykle podporuje postup použití stejného uživatelského jména a hesla v několika lokalitách služby, což je slabé bezpečnostní opatření.  
  
- Architektura se neškáluje jako více organizací, které by vnímaty prostředek v organizaci B, pokud se jedná o nějakou hodnotu.  
  
 Alternativním přístupem, který řeší výše zmíněné nevýhody, je využívání federovaného zabezpečení. V tomto přístupu organizace a a B navážou vztah důvěryhodnosti a využívají službu tokenů zabezpečení (STS), aby umožnila zprostředkovateli zavedeného vztahu důvěryhodnosti.  
  
 V rámci federované architektury zabezpečení uživatelé z organizace ví, že pokud chtějí získat přístup k webové službě v organizaci B, že musí předložit platný token zabezpečení ze služby STS v organizaci B, která ověřuje a autorizuje přístup ke konkrétní službě.  
  
 Při kontaktování služby tokenů zabezpečení (STS B) získají uživatelé další úroveň nepřímých odkazů ze zásad přidružených ke službě STS. Před tím, než služba STS B může vydávat token zabezpečení, musí mít platný token zabezpečení ze služby STS A (tj. sféra vztahu důvěryhodnosti klienta). Jedná se o Corollary vztah důvěryhodnosti mezi dvěma organizacemi a naznačuje, že organizace B nemusí spravovat identity pro uživatele z organizace A. V praxi má STS B obvykle hodnotu null `issuerAddress` a `issuerMetadataAddress` . Další informace najdete v tématu [Postupy: Konfigurace místního vystavitele](how-to-configure-a-local-issuer.md). V takovém případě klient prohledává službu STS A pomocí místních zásad. Tato konfigurace se nazývá *federace domovské sféry* a je lepší škálovat, protože služba STS B nemusí spravovat informace o STS A.  
  
 Uživatelé pak budou kontaktovat službu STS v organizaci a a získat token zabezpečení tím, že prezentují ověřovací přihlašovací údaje, které běžně používají k získání přístupu k jakémukoli jinému prostředku v organizaci A. Tím se také řeší problém uživatelů, kteří si mají zachovat více sad přihlašovacích údajů nebo používají stejnou sadu přihlašovacích údajů na více lokalitách služby.  
  
 Jakmile uživatelé získají token zabezpečení ze služby STS A, prezentují token službě STS B. organizace B pokračuje v provádění autorizace požadavků uživatelů a vydá token zabezpečení uživatelům z vlastní sady tokenů zabezpečení. Uživatelé pak mohou svůj token prezentovat k prostředkům v organizaci B a přistupovat ke službě.  
  
## <a name="support-for-federated-security-in-wcf"></a>Podpora federovaného zabezpečení ve službě WCF  
 WCF poskytuje podporu klíč pro nasazení federovaných architektur zabezpečení prostřednictvím [\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md) .  
  
 [\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md)Element poskytuje zabezpečenou, spolehlivou a interoperabilní vazbu, která zahrnuje použití http jako základního přenosového mechanismu pro styl komunikace požadavek-odpověď, který pro kódování používá text a XML jako formát pro přenos.  
  
 Použití [\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md) ve federovaném scénáři zabezpečení lze oddělit do dvou logicky nezávislých fází, jak je popsáno v následujících částech.  
  
### <a name="phase-1-design-phase"></a>Fáze 1: fáze návrhu  
 Ve fázi návrhu používá klient Nástroj pro dokládání [metadat (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) k přečtení zásad, které zpřístupňuje koncový bod služby, a ke shromažďování požadavků na ověřování a autorizaci služby. Příslušné proxy servery jsou vytvořeny tak, aby na klientovi vytvořily následující vzor federovaného zabezpečení:  
  
- Získejte token zabezpečení ze služby STS ve sféře vztahu důvěryhodnosti klienta.  
  
- Prezentovat token ke službě STS ve sféře vztahu důvěryhodnosti služby.  
  
- Získejte token zabezpečení ze služby STS ve sféře vztahu důvěryhodnosti služby.  
  
- Prezentovat token službě pro přístup ke službě.  
  
### <a name="phase-2-run-time-phase"></a>Fáze 2: fáze run-time  
 Během fáze běhu klient vytvoří instanci objektu třídy klienta WCF a provede volání pomocí klienta WCF. Základní architektura služby WCF zpracovává dříve zmíněné kroky v rámci modelu federované zabezpečení komunikace a umožňuje klientovi bezproblémové využívání služby.  
  
## <a name="sample-implementation-using-wcf"></a>Ukázková implementace pomocí WCF  
 Následující ilustrace znázorňuje ukázkovou implementaci pro federované architektury zabezpečení pomocí nativní podpory služby WCF.  
  
 ![Diagram znázorňující ukázkovou implementaci zabezpečení federace](./media/federation/federated-security-implementation.gif)  
  
### <a name="example-myservice"></a>Příklad Mojesluzba  
 Služba `MyService` zpřístupňuje jeden koncový bod prostřednictvím `MyServiceEndpoint` . Na následujícím obrázku je znázorněna adresa, vazba a kontrakt spojený s koncovým bodem.  
  
 ![Diagram znázorňující MyServiceEndpoint podrobnosti.](./media/federation/myserviceendpoint-details.gif)  
  
 Koncový bod služby `MyServiceEndpoint` používá [\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md) a vyžaduje platný token SAML (Security Assert Markup Language) s `accessAuthorized` deklarací, kterou vystavila služba STS B. Tato deklarace je deklarativně specifikovaná v konfiguraci služby.  
  
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
> Je třeba si poznamenat jemný bod o deklaracích vyžadovaných nástrojem `MyService` . Druhý obrázek ukazuje, že `MyService` vyžaduje token SAML s `accessAuthorized` deklarací identity. Aby bylo přesnější, určuje typ deklarace identity, který `MyService` vyžaduje. Plně kvalifikovaný název tohoto typu deklarace identity je `http://tempuri.org:accessAuthorized` (spolu s přidruženým oborem názvů), který se používá v konfiguračním souboru služby. Hodnota této deklarace identity označuje přítomnost této deklarace identity a předpokládá se, že je nastavena na službu `true` STS B.  
  
 Za běhu se tato zásada vynutila `MyServiceOperationRequirement` třídou, která je implementovaná jako součást `MyService` .  
  
 [!code-csharp[C_Federation#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#0)]
 [!code-vb[C_Federation#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#0)]  
[!code-csharp[C_Federation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#1)]
[!code-vb[C_Federation#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#1)]  
  
#### <a name="sts-b"></a>STS B  
 Na následujícím obrázku je znázorněná služba tokenů zabezpečení (STS) B. Jak je uvedeno výše, služba tokenů zabezpečení (STS) je také webová služba a může mít přidružené koncové body, zásady a tak dále.  
  
 ![Diagram znázorňující službu tokenu zabezpečení B.](./media/federation/myservice-security-token-service-b.gif)  
  
 Služba STS B zpřístupňuje jeden koncový bod, `STSEndpoint` který je možné použít k vyžádání tokenů zabezpečení. Konkrétně služba tokenů zabezpečení (STS B) vystavuje tokeny SAML s `accessAuthorized` deklarací identity, které mohou být uvedeny na `MyService` webu služby pro přístup k této službě. Služba STS B ale vyžaduje, aby uživatelé prezentují platný token SAML vydaný službou STS A, který obsahuje `userAuthenticated` deklaraci identity. Tato deklarace je deklarativně specifikovaná v konfiguraci služby STS.  
  
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
> `userAuthenticated`Deklarace identity je znovu typu deklarace identity, který vyžaduje služba tokenů zabezpečení (STS) B. Plně kvalifikovaný název tohoto typu deklarace identity je `http://tempuri.org:userAuthenticated` (spolu s přidruženým oborem názvů), který se používá v konfiguračním souboru STS. Hodnota této deklarace identity označuje přítomnost této deklarace identity a předpokládá se, že ji nastaví `true` Služba STS a.  
  
 V době běhu `STS_B_OperationRequirement` Třída vynutila tuto zásadu, která je implementována jako součást služby tokenů zabezpečení (STS) B.  
  
 [!code-csharp[C_Federation#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#2)]
 [!code-vb[C_Federation#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#2)]  
  
 Pokud je kontroler přístupu jasný, služba tokenů zabezpečení (STS B) vydá token SAML s `accessAuthorized` deklarací identity.  
  
 [!code-csharp[C_Federation#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#3)]
 [!code-vb[C_Federation#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#3)]  
  
#### <a name="sts-a"></a>SLUŽBA STS A  
 Na následujícím obrázku je znázorněna služba STS A.  
  
 ![metadata](media/sts-b.gif "STS_B")  
  
 Podobně jako služba STS B, STS A je také webová služba, která vydává tokeny zabezpečení a zpřístupňuje jeden koncový bod pro tento účel. Používá ale jinou vazbu ( `wsHttpBinding` ) a vyžaduje, aby uživatelé mohli prezentovat platnou službu CardSpace s `emailAddress` deklarací identity. V reakci vydá tokeny SAML s `userAuthenticated` deklarací identity. Tato deklarace je deklarativně specifikovaná v konfiguraci služby.  
  
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
  
 V době běhu `STS_A_OperationRequirement` Třída vynutila tuto zásadu, která je implementována jako součást služby STS a.  
  
 [!code-csharp[C_Federation#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#4)]
 [!code-vb[C_Federation#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#4)]  
  
 Pokud je přístup `true` , STS a vydá token SAML s `userAuthenticated` deklarací identity.  
  
 [!code-csharp[C_Federation#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#5)]
 [!code-vb[C_Federation#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#5)]  
  
### <a name="client-at-organization-a"></a>Klient v organizaci A  
 Následující ilustrace znázorňuje klienta v organizaci A spolu s postupem, který je součástí provádění `MyService` volání služby. Další funkční komponenty jsou také zahrnuty pro úplnost.  
  
 ![Diagram znázorňující kroky ve volání služby Mojesluzba](./media/federation/federation-myservice-service-call-process.gif)  
  
## <a name="summary"></a>Souhrn  
 Federované zabezpečení poskytuje čistou divizi zodpovědnosti a pomáhá sestavovat zabezpečené a škálovatelné architektury služeb. Jako platforma pro sestavování a nasazování distribuovaných aplikací poskytuje WCF nativní podporu pro implementaci federovaného zabezpečení.  
  
## <a name="see-also"></a>Viz také

- [Zabezpečení](security.md)
