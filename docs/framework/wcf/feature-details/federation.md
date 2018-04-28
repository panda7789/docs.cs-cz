---
title: Federace
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation [WCF]
ms.assetid: 2f1e646f-8361-48d4-9d5d-1b961f31ede4
caps.latest.revision: 26
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0e7aef1f53675089ee311aa79a54abf60441b728
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="federation"></a>Federace
Toto téma obsahuje stručný přehled koncept federované zabezpečení. Také popisuje [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] podporu pro nasazení architektury federované zabezpečení. Ukázkovou aplikaci, která demonstruje federace, najdete v části [ukázka federace](../../../../docs/framework/wcf/samples/federation-sample.md).  
  
## <a name="definition-of-federated-security"></a>Definice federované zabezpečení  
 Federované zabezpečení umožňuje čistou oddělení mezi službu, kterou klient přistupuje a přidružené postupů ověřování a autorizace. Federované zabezpečení taky umožňuje spolupráci mezi více systémy, sítě a organizace v různých důvěryhodnosti sfér.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] poskytuje podporu pro vytváření a nasazování distribuovaných systémů, které využívají federované zabezpečení.  
  
### <a name="elements-of-a-federated-security-architecture"></a>Prvky architektury federované zabezpečení  
 Architektura federované zabezpečení má tři klíčové prvky, jak je popsáno v následující tabulce.  
  
|Prvek|Popis|  
|-------------|-----------------|  
|Domény nebo sféry|Na jednu jednotku správu zabezpečení nebo vztah důvěryhodnosti. Typické domény mohou zahrnovat jedné organizace.|  
|Federace|Kolekce domén, které mají vztah důvěryhodnosti. Úroveň důvěryhodnosti může lišit, ale obvykle zahrnuje ověřování a téměř vždy obsahuje autorizace. Typické federace může obsahovat několik organizací, které mají vztah důvěryhodnosti pro sdílený přístup k sadu prostředků.|  
|Služba tokenů zabezpečení (STS)|Webová služba, která vydává tokeny zabezpečení; To znamená provede kontrolních výrazů založené na důkaz, která důvěřuje na všechny uživatele, kteří důvěřuje. Tento balíček je základem zprostředkování vztahu důvěryhodnosti mezi doménami.|  
  
### <a name="example-scenario"></a>Příklad scénáře  
 Následující obrázek znázorňuje příklad federované zabezpečení.  
  
 ![Federační](../../../../docs/framework/wcf/feature-details/media/typicalfederatedsecurityscenario.gif "TypicalFederatedSecurityScenario")  
  
 Tento scénář zahrnuje dvě organizace: A a B. organizace B má někteří uživatelé v organizaci A najít cenné webové prostředky (webová služba).  
  
> [!NOTE]
>  Tato část používá podmínky *prostředků*, *služby*, a *webovou službu* zcela zaměnitelným významem.  
  
 Organizace B, obvykle vyžaduje, aby uživatel z organizace A zadali některé platné formu ověřování před přístupem ke službě. Kromě toho organizace může také vyžadovat, uživatel povolen přístup k určitému konkrétní prostředku. Jeden způsob, jak vyřešit tento problém a povolit uživatelům v organizaci A pro přístup k prostředku v organizaci B je následující:  
  
-   Uživatelé z organizace A zaregistrovat svoje přihlašovací údaje (uživatelské jméno a heslo) s organizace B.  
  
-   Během přístupu k prostředkům uživatelům v organizaci A k dispozici přihlašovacích údajů pro organizaci B a ověření před přístupem k prostředku.  
  
 Tento přístup má tři významné nevýhody:  
  
-   Organizace B má ke správě pověření pro uživatele z organizace A kromě správy pověření své místní uživatelé.  
  
-   Třeba uživatelům v organizaci A spravovat další sadu pověření (to znamená, nezapomeňte další uživatelské jméno a heslo) kromě přihlašovací údaje, obvykle používají pro přístup k prostředkům v rámci organizace A. To obvykle doporučuje postup pomocí stejné uživatelské jméno a heslo ve více lokalitách služby, což je slabé bezpečnostní opatření.  
  
-   Architektura se nedá použít jako další organizace vnímat prostředků v organizaci B, že některé hodnoty.  
  
 Alternativní způsob, který řeší výše uvedených nevýhody, je použít federované zabezpečení. V tomto přístupu organizace A a B navázání vztahu důvěryhodnosti a využít zabezpečení tokenu služby (STS) Chcete-li povolit zprostředkování zavedených vztahu důvěryhodnosti.  
  
 V architektuře federované zabezpečení uživatele organizaci A vědět, že pokud chtějí přístup k webové službě v organizaci B, který se musí představovat platný zabezpečení token zabezpečení ze služby tokenů zabezpečení v organizaci B, který provádí ověřování a autorizaci svůj přístup k konkrétní službu.  
  
 Na kontaktování služby tokenů zabezpečení B, uživatelé přijímat jinou úroveň dereference z zásady přidružené Služba tokenů zabezpečení. Se musí představovat platný zabezpečení od služby tokenů zabezpečení A (tedy sféry klienta vztahu důvěryhodnosti) token před B služby tokenů zabezpečení můžete vydat, je token zabezpečení. Toto je důsledkem této vztah důvěryhodnosti mezi dvěma organizacemi a znamená, že organizace B nemá spravovat identity pro uživatele z organizace A. V praxi, STS B, obvykle má hodnotu null `issuerAddress` a `issuerMetadataAddress`. Další informace najdete v tématu [postupy: Konfigurace místního vystavitele](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md). V takovém případě klienta zajímají místní zásady najít službu tokenů zabezpečení A. Tato konfigurace se nazývá *domácí sféry federace* a škáluje líp, protože není nutné udržovat informace o STS A. B služby tokenů zabezpečení  
  
 Uživatelé pak, obraťte se na službu tokenů zabezpečení v organizaci A a získat token zabezpečení prezentací ověřování přihlašovacích údajů, které standardně používáte k získání přístupu k jakémukoli prostředku, v rámci organizace A. To také řeší problém uživatelů bude potřeba udržovat několik sad přihlašovacích údajů, nebo pomocí stejné sady přihlašovacích údajů ve více lokalitách služby.  
  
 Jakmile se uživatelé získat token zabezpečení od služby tokenů zabezpečení A, se nachází token, který má služba tokenů zabezpečení B. organizace B pokračuje k autorizaci požadavků uživatelů a vydá token zabezpečení pro uživatele z vlastní sadu tokenů zabezpečení. Uživatele můžete prezentovat token k prostředku v organizaci B a přístup ke službě.  
  
## <a name="support-for-federated-security-in-wcf"></a>Podpora pro federované zabezpečení ve WCF  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] To podporuje pro nasazení architektury federované zabezpečení prostřednictvím [ \<– wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).  
  
 [ \<– WsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) element poskytuje bezpečné, spolehlivé a umožňuje vzájemnou spolupráci vazby, která se používá jako podkladový přenosový mechanismus pro komunikaci styl požadavku a odpovědi HTTP nasazení jako přenosový formát pro kódování textu a XML.  
  
 Použití [ \<– wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) v federované zabezpečení scénáři může být odděleno do dvou fází logicky nezávislý, jak je popsáno v následujících částech.  
  
### <a name="phase-1-design-phase"></a>Fáze 1: Fáze návrhu  
 Během fáze návrhu, klient použije [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ke čtení zásad zpřístupní koncový bod služby a shromažďovat služby ověřování a autorizaci požadavků. Odpovídající proxy sestavení tak, aby vytvořit následující vzor federované zabezpečení komunikace na straně klienta:  
  
-   Získejte token zabezpečení od služby tokenů zabezpečení ve sféře, důvěryhodnosti klienta.  
  
-   Token k dispozici na službu STS ve sféře, vztah důvěryhodnosti služby.  
  
-   Získejte token zabezpečení od služby tokenů zabezpečení ve sféře, vztah důvěryhodnosti služby.  
  
-   K dispozici token, který má služba pro přístup ke službě.  
  
### <a name="phase-2-run-time-phase"></a>Fáze 2: Run-Time fáze  
 Během fáze spuštění klienta vytvoří objekt [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] třída klienta a umožňuje volání pomocí [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta. Základní architektura [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zpracovává výše uvedených kroků ve vzoru federované zabezpečení komunikace a umožňuje klientovi bez problémů používat službu.  
  
## <a name="sample-implementation-using-wcf"></a>Ukázka implementace pomocí WCF  
 Následující obrázek znázorňuje implementaci ukázka pro federované zabezpečení architektury pomocí nativní podporu z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 ![Federační zabezpečení ve WCF](../../../../docs/framework/wcf/feature-details/media/federatedsecurityinwcf.gif "FederatedSecurityInWCF")  
  
### <a name="example-myservice"></a>Příklad Moje_služba  
 Služba `MyService` vystavuje jeden koncový bod prostřednictvím `MyServiceEndpoint`. Následující obrázek znázorňuje adresy, vazby a kontraktu přiřazené ke koncovému bodu.  
  
 ![Federační](../../../../docs/framework/wcf/feature-details/media/myservice.gif "Moje_služba")  
  
 Koncový bod služby `MyServiceEndpoint` používá [ \<– wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) a vyžaduje platný token zabezpečení kontrolní výrazy Markup Language (SAML) s `accessAuthorized` deklarace identity vystavený B. služby tokenů zabezpečení Toto nastavení je deklarativně zadané v konfiguraci služby.  
  
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
>  O deklaracích identity vyžaduje potřeba poznamenat bod jemně `MyService`. Druhý obrázek znamená, že `MyService` vyžaduje tokenu SAML s `accessAuthorized` deklarací identity. Jako přesnější, určuje typ deklarace identity, aby `MyService` vyžaduje. Plně kvalifikovaný název tohoto typu deklarace identity je http://tempuri.org:accessAuthorized (spolu s přidružené oboru názvů), který se používá v konfiguračním souboru služby. Hodnota této deklarace indikuje přítomnost této deklarace identity a se předpokládá, že bude nastaven na `true` pomocí služby tokenů zabezpečení B.  
  
 Za běhu, je tato zásada vynucené `MyServiceOperationRequirement` třídu, která je implementovaná jako součást `MyService`.  
  
 [!code-csharp[C_Federation#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#0)]
 [!code-vb[C_Federation#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#0)]  
[!code-csharp[C_Federation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#1)]
[!code-vb[C_Federation#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#1)]  
  
#### <a name="sts-b"></a>SLUŽBA TOKENŮ ZABEZPEČENÍ B  
 Následující obrázek znázorňuje B. služby tokenů zabezpečení Jak jsme uvedli dříve, služby tokenů zabezpečení (STS) je také webová služba a může mít jeho přidružené koncových bodů, zásad a tak dále.  
  
 ![Federační](../../../../docs/framework/wcf/feature-details/media/msservicestsb.gif "MsServiceSTSB")  
  
 Služby tokenů zabezpečení B vystavuje jeden koncový bod, který volá `STSEndpoint` který lze použít k žádosti o tokeny zabezpečení. Konkrétně STS B vydává tokeny SAML s `accessAuthorized` deklarace identity, které lze zobrazit v `MyService` služeb – web pro přístup k službě. Však B služby tokenů zabezpečení vyžaduje uživatelům k dispozici platný token SAML vydaný A služby tokenů zabezpečení, který obsahuje `userAuthenticated` deklarací identity. To je deklarativně zadaný v konfiguraci služby tokenů zabezpečení.  
  
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
>  Znovu `userAuthenticated` deklarace identity je typ deklarace identity, který vyžaduje službu tokenů zabezpečení B. Plně kvalifikovaný název tohoto typu deklarace identity je http://tempuri.org:userAuthenticated (spolu s přidružené oboru názvů), který se používá v konfiguračním souboru služby tokenů zabezpečení. Hodnota této deklarace indikuje přítomnost této deklarace identity a se předpokládá, že bude nastaven na `true` služby tokenů zabezpečení a.  
  
 V době běhu `STS_B_OperationRequirement` třída vynucuje tato zásada, která je implementovaná jako součást služby tokenů zabezpečení B.  
  
 [!code-csharp[C_Federation#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#2)]
 [!code-vb[C_Federation#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#2)]  
  
 Pokud kontrola přístupu není zaškrtnuto, služba tokenů zabezpečení B vydá token SAML s `accessAuthorized` deklarací identity.  
  
 [!code-csharp[C_Federation#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#3)]
 [!code-vb[C_Federation#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#3)]  
  
#### <a name="sts-a"></a>SLUŽBA TOKENŮ ZABEZPEČENÍ A  
 Následující obrázek znázorňuje A. služby tokenů zabezpečení  
  
 ![Federační](../../../../docs/framework/wcf/feature-details/media/sts-b.gif "STS_B")  
  
 Podobně jako u služby tokenů zabezpečení B, A služby tokenů zabezpečení je taky webová služba, která vydává tokeny zabezpečení a zveřejňuje jeden koncový bod pro tento účel. Ale používá jinou vazbou (`wsHttpBinding`) a vyžaduje, aby uživatelé k dispozici platný [!INCLUDE[infocard](../../../../includes/infocard-md.md)] s `emailAddress` deklarací identity. V odpovědi, vydává tokeny SAML s `userAuthenticated` deklarací identity. Toto nastavení je deklarativně zadané v konfiguraci služby.  
  
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
  
 V době běhu `STS_A_OperationRequirement` třída vynucuje tato zásada, která je implementovaná jako součást služby tokenů zabezpečení A.  
  
 [!code-csharp[C_Federation#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#4)]
 [!code-vb[C_Federation#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#4)]  
  
 Pokud je přístup `true`, služby tokenů zabezpečení A vydá token SAML s `userAuthenticated` deklarací identity.  
  
 [!code-csharp[C_Federation#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#5)]
 [!code-vb[C_Federation#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#5)]  
  
### <a name="client-at-organization-a"></a>Klient v organizaci A  
 Následující obrázek znázorňuje klienta v organizaci A, společně s kroky při vytváření `MyService` služby volání. Ostatní funkční součásti jsou také zahrnuté pro úplnost.  
  
 ![Federační](../../../../docs/framework/wcf/feature-details/media/federationclienta.gif "FederationClientA")  
  
## <a name="summary"></a>Souhrn  
 Federované zabezpečení poskytuje čistou dělení zodpovědnosti a pomáhá k vytvoření zabezpečeného a škálovatelného služby architektury. Jako platforma pro vytváření a nasazování distribuované aplikace [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] poskytuje nativní podporu pro implementaci federované zabezpečení.  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečení](../../../../docs/framework/wcf/feature-details/security.md)
