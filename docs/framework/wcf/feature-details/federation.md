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
# <a name="federation"></a><span data-ttu-id="bc82e-102">metadata</span><span class="sxs-lookup"><span data-stu-id="bc82e-102">Federation</span></span>
<span data-ttu-id="bc82e-103">Toto téma obsahuje stručný přehled konceptu federovaného zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="bc82e-103">This topic provides a brief overview of the concept of federated security.</span></span> <span data-ttu-id="bc82e-104">Popisuje také podporu Windows Communication Foundation (WCF) pro nasazení federovaných architektur zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="bc82e-104">It also describes Windows Communication Foundation (WCF) support for deploying federated security architectures.</span></span> <span data-ttu-id="bc82e-105">Ukázková aplikace, která demonstruje federaci, naleznete [v tématu Federation Sample](../../../../docs/framework/wcf/samples/federation-sample.md).</span><span class="sxs-lookup"><span data-stu-id="bc82e-105">For a sample application that demonstrates federation, see [Federation Sample](../../../../docs/framework/wcf/samples/federation-sample.md).</span></span>  
  
## <a name="definition-of-federated-security"></a><span data-ttu-id="bc82e-106">Definice federovaného zabezpečení</span><span class="sxs-lookup"><span data-stu-id="bc82e-106">Definition of Federated Security</span></span>  
 <span data-ttu-id="bc82e-107">Federované zabezpečení umožňuje čisté oddělení mezi službou, ke které klient přistupuje, a souvisejícími ověřovacími a autorizačními postupy.</span><span class="sxs-lookup"><span data-stu-id="bc82e-107">Federated security allows for clean separation between the service a client is accessing and the associated authentication and authorization procedures.</span></span> <span data-ttu-id="bc82e-108">Federované zabezpečení také umožňuje spolupráci napříč různými systémy, sítěmi a organizacemi v různých sférách důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="bc82e-108">Federated security also enables collaboration across multiple systems, networks, and organizations in different trust realms.</span></span>  
  
 <span data-ttu-id="bc82e-109">WCF poskytuje podporu pro vytváření a nasazování distribuovaných systémů, které používají federované zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="bc82e-109">WCF provides support for building and deploying distributed systems that employ federated security.</span></span>  
  
### <a name="elements-of-a-federated-security-architecture"></a><span data-ttu-id="bc82e-110">Prvky architektury federovaného zabezpečení</span><span class="sxs-lookup"><span data-stu-id="bc82e-110">Elements of a Federated Security Architecture</span></span>  
 <span data-ttu-id="bc82e-111">Federovaná architektura zabezpečení má tři klíčové prvky, jak je popsáno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="bc82e-111">The federated security architecture has three key elements, as described in the following table.</span></span>  
  
|<span data-ttu-id="bc82e-112">Prvek</span><span class="sxs-lookup"><span data-stu-id="bc82e-112">Element</span></span>|<span data-ttu-id="bc82e-113">Popis</span><span class="sxs-lookup"><span data-stu-id="bc82e-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bc82e-114">Doména/sféra</span><span class="sxs-lookup"><span data-stu-id="bc82e-114">Domain/realm</span></span>|<span data-ttu-id="bc82e-115">Jedna jednotka správy nebo důvěry v zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="bc82e-115">A single unit of security administration or trust.</span></span> <span data-ttu-id="bc82e-116">Typická doména může zahrnovat jednu organizaci.</span><span class="sxs-lookup"><span data-stu-id="bc82e-116">A typical domain might include a single organization.</span></span>|  
|<span data-ttu-id="bc82e-117">metadata</span><span class="sxs-lookup"><span data-stu-id="bc82e-117">Federation</span></span>|<span data-ttu-id="bc82e-118">Kolekce domén, které vytvořily vztah důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="bc82e-118">A collection of domains that have established trust.</span></span> <span data-ttu-id="bc82e-119">Úroveň důvěryhodnosti se může lišit, ale obvykle zahrnuje ověřování a téměř vždy zahrnuje autorizaci.</span><span class="sxs-lookup"><span data-stu-id="bc82e-119">The level of trust may vary, but typically includes authentication and almost always includes authorization.</span></span> <span data-ttu-id="bc82e-120">Typická federace může zahrnovat několik organizací, které vytvořily vztah důvěryhodnosti pro sdílený přístup k sadě prostředků.</span><span class="sxs-lookup"><span data-stu-id="bc82e-120">A typical federation might include a number of organizations that have established trust for shared access to a set of resources.</span></span>|  
|<span data-ttu-id="bc82e-121">Služba tokenů zabezpečení (STS)</span><span class="sxs-lookup"><span data-stu-id="bc82e-121">Security Token Service (STS)</span></span>|<span data-ttu-id="bc82e-122">Webová služba, která vydává tokeny zabezpečení. to znamená, že činí tvrzení založená na důkazech, kterým důvěřuje, tomu, komu důvěřuje.</span><span class="sxs-lookup"><span data-stu-id="bc82e-122">A Web service that issues security tokens; that is, it makes assertions based on evidence that it trusts, to whomever trusts it.</span></span> <span data-ttu-id="bc82e-123">To tvoří základ zprostředkovatele důvěryhodnosti mezi doménami.</span><span class="sxs-lookup"><span data-stu-id="bc82e-123">This forms the basis of trust brokering between domains.</span></span>|  
  
### <a name="example-scenario"></a><span data-ttu-id="bc82e-124">Ukázkový scénář</span><span class="sxs-lookup"><span data-stu-id="bc82e-124">Example Scenario</span></span>  
 <span data-ttu-id="bc82e-125">Následující obrázek znázorňuje příklad federovaného zabezpečení:</span><span class="sxs-lookup"><span data-stu-id="bc82e-125">The following illustration shows an example of federated security:</span></span>  
  
 ![Diagram znázorňující typický federovaný scénář zabezpečení.](./media/federation/typical-federated-security-scenario.gif)  
  
 <span data-ttu-id="bc82e-127">Tento scénář zahrnuje dvě organizace: A a B. Organizace B má webový prostředek (webovou službu), který někteří uživatelé v organizaci A považují za cenné.</span><span class="sxs-lookup"><span data-stu-id="bc82e-127">This scenario includes two organizations: A and B. Organization B has a Web resource (a Web service) that some users in organization A find valuable.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bc82e-128">Tato část používá termíny *zdroj*, *služba*a *webová služba* zaměnitelně.</span><span class="sxs-lookup"><span data-stu-id="bc82e-128">This section uses the terms *resource*, *service*, and *Web service* interchangeably.</span></span>  
  
 <span data-ttu-id="bc82e-129">Organizace B obvykle vyžaduje, aby uživatel z organizace A před přístupem ke službě poskytl nějakou platnou formu ověřování.</span><span class="sxs-lookup"><span data-stu-id="bc82e-129">Typically, organization B requires that a user from organization A provide some valid form of authentication before accessing the service.</span></span> <span data-ttu-id="bc82e-130">Kromě toho organizace může také vyžadovat, aby uživatel byl oprávněn k přístupu k určitému prostředku.</span><span class="sxs-lookup"><span data-stu-id="bc82e-130">In addition, the organization may also require that the user be authorized to access the specific resource in question.</span></span> <span data-ttu-id="bc82e-131">Jedním ze způsobů, jak tento problém vyřešit a umožnit uživatelům v organizaci A přístup k prostředku v organizaci B, je následující:</span><span class="sxs-lookup"><span data-stu-id="bc82e-131">One way to address this problem and enable users in organization A to access the resource in organization B is as follows:</span></span>  
  
- <span data-ttu-id="bc82e-132">Uživatelé z organizace A zaregistrují svá pověření (uživatelské jméno a heslo) u organizace B.</span><span class="sxs-lookup"><span data-stu-id="bc82e-132">Users from organization A register their credentials (a user name and password) with organization B.</span></span>  
  
- <span data-ttu-id="bc82e-133">Během přístupu k prostředkům uživatelé z organizace A prezentují svá pověření organizaci B a jsou ověřeni před přístupem k prostředku.</span><span class="sxs-lookup"><span data-stu-id="bc82e-133">During the resource access, users from organization A present their credentials to organization B and are authenticated before accessing the resource.</span></span>  
  
 <span data-ttu-id="bc82e-134">Tento přístup má tři významné nevýhody:</span><span class="sxs-lookup"><span data-stu-id="bc82e-134">This approach has three significant drawbacks:</span></span>  
  
- <span data-ttu-id="bc82e-135">Organizace B musí spravovat pověření pro uživatele z organizace A kromě správy pověření místních uživatelů.</span><span class="sxs-lookup"><span data-stu-id="bc82e-135">Organization B has to manage the credentials for users from organization A in addition to managing the credentials of its local users.</span></span>  
  
- <span data-ttu-id="bc82e-136">Uživatelé v organizaci: Kromě pověření, která obvykle používají k získání přístupu k prostředkům v rámci organizace A, je třeba udržovat další sadu pověření (tj. zapamatovat další uživatelské jméno a heslo). To obvykle podporuje praxi používání stejného uživatelského jména a hesla na více místech služeb, což je slabé bezpečnostní opatření.</span><span class="sxs-lookup"><span data-stu-id="bc82e-136">Users in organization A need to maintain an additional set of credentials (that is, remember an additional user name and password) apart from the credentials they normally use to gain access to resources within organization A. This usually encourages the practice of using the same user name and password at multiple service sites, which is a weak security measure.</span></span>  
  
- <span data-ttu-id="bc82e-137">Architektura není škálovat jako více organizací vnímají prostředek v organizaci B jako nějakou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="bc82e-137">The architecture does not scale as more organizations perceive the resource at organization B as being of some value.</span></span>  
  
 <span data-ttu-id="bc82e-138">Alternativním přístupem, který řeší výše uvedené nevýhody, je využití federovaného zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="bc82e-138">An alternative approach, which addresses the previously mentioned drawbacks, is to employ federated security.</span></span> <span data-ttu-id="bc82e-139">V tomto přístupu organizace A a B vytvořit vztah důvěryhodnosti a zaměstnávat službu tokenů zabezpečení (STS) povolit zprostředkování zavedeného vztahu důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="bc82e-139">In this approach, organizations A and B establish a trust relationship and employ Security Token Service (STS) to enable brokering of the established trust.</span></span>  
  
 <span data-ttu-id="bc82e-140">Ve federované architektuře zabezpečení uživatelé z organizace A vědí, že pokud chtějí získat přístup k webové službě v organizaci B, musí předložit platný token zabezpečení z STS v organizaci B, který ověřuje a autorizuje jejich přístup ke konkrétní službě.</span><span class="sxs-lookup"><span data-stu-id="bc82e-140">In a federated security architecture, users from organization A know that if they want to access the Web service in organization B that they must present a valid security token from the STS at organization B, which authenticates and authorizes their access to the specific service.</span></span>  
  
 <span data-ttu-id="bc82e-141">Při kontaktování STS B, uživatelé obdrží jinou úroveň dereference ze zásady spojené s STS.</span><span class="sxs-lookup"><span data-stu-id="bc82e-141">On contacting the STS B, the users receive another level of indirection from the policy associated with the STS.</span></span> <span data-ttu-id="bc82e-142">Musí předložit platný token zabezpečení z STS A (to znamená, že správa důvěryhodnosti klienta) před STS B může vydat token zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="bc82e-142">They must present a valid security token from the STS A (that is, the client trust realm) before the STS B can issue them a security token.</span></span> <span data-ttu-id="bc82e-143">Toto je důsledek vztahu důvěryhodnosti vytvořeného mezi oběma organizacemi a znamená, že organizace B nemusí spravovat identity pro uživatele z organizace A. V praxi MÁ STS B `issuerAddress` obvykle `issuerMetadataAddress`null a .</span><span class="sxs-lookup"><span data-stu-id="bc82e-143">This is a corollary of the trust relationship established between the two organizations and implies that organization B does not have to manage identities for users from organization A. In practice, STS B typically has a null `issuerAddress` and `issuerMetadataAddress`.</span></span> <span data-ttu-id="bc82e-144">Další informace naleznete v [tématu How to: Configure a Local Issuer](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).</span><span class="sxs-lookup"><span data-stu-id="bc82e-144">For more information, see [How to: Configure a Local Issuer](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span> <span data-ttu-id="bc82e-145">V takovém případě klient konzultuje místní zásady k vyhledání STS A. Tato konfigurace se nazývá *federace domácí sféry* a lépe se škáluje, protože STS B nemusí udržovat informace o STS A.</span><span class="sxs-lookup"><span data-stu-id="bc82e-145">In that case, the client consults a local policy to locate STS A. This configuration is called *home realm federation* and it scales better because STS B does not have to maintain information about STS A.</span></span>  
  
 <span data-ttu-id="bc82e-146">Uživatelé pak kontaktovat STS v organizaci A a získat token zabezpečení tím, že předloží ověřovací pověření, které obvykle používají k získání přístupu k jinému prostředku v rámci organizace A. To také zmírňuje problém uživatelů, kteří musí udržovat více sad pověření nebo používat stejnou sadu pověření na více serverech služeb.</span><span class="sxs-lookup"><span data-stu-id="bc82e-146">The users then contact the STS at organization A and obtain a security token by presenting authentication credentials that they normally use to gain access to any other resource within organization A. This also alleviates the problem of users having to maintain multiple sets of credentials or using the same set of credentials at multiple service sites.</span></span>  
  
 <span data-ttu-id="bc82e-147">Jakmile uživatelé získají token zabezpečení z STS A, předloží token sts B. Organizace B pokračuje k autorizaci požadavků uživatelů a vydává token zabezpečení uživatelům z vlastní sady tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="bc82e-147">Once the users obtain a security token from the STS A, they present the token to the STS B. Organization B proceeds to perform authorization of the users' requests and issues a security token to the users from its own set of security tokens.</span></span> <span data-ttu-id="bc82e-148">Uživatelé pak mohou prezentovat svůj token prostředku v organizaci B a získat přístup ke službě.</span><span class="sxs-lookup"><span data-stu-id="bc82e-148">The users can then present their token to the resource at organization B and access the service.</span></span>  
  
## <a name="support-for-federated-security-in-wcf"></a><span data-ttu-id="bc82e-149">Podpora federovaného zabezpečení v WCF</span><span class="sxs-lookup"><span data-stu-id="bc82e-149">Support for Federated Security in WCF</span></span>  
 <span data-ttu-id="bc82e-150">WCF poskytuje podporu na klíč pro nasazení federovaných architektur zabezpečení prostřednictvím [ \<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="bc82e-150">WCF provides turnkey support for deploying federated security architectures through the [\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span></span>  
  
 <span data-ttu-id="bc82e-151">[ \<WsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) prvek poskytuje zabezpečené, spolehlivé, interoperabilní vazby, která zahrnuje použití protokolu HTTP jako základní mechanismus přenosu pro styl komunikace požadavek odpověď, použití textu a XML jako formát drátu pro kódování.</span><span class="sxs-lookup"><span data-stu-id="bc82e-151">The [\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) element provides for a secure, reliable, interoperable binding that entails the use of HTTP as the underlying transport mechanism for request-reply communication style, employing text and XML as the wire format for encoding.</span></span>  
  
 <span data-ttu-id="bc82e-152">Použití [ \<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) ve federovaném scénáři zabezpečení lze oddělit do dvou logicky nezávislých fází, jak je popsáno v následujících částech.</span><span class="sxs-lookup"><span data-stu-id="bc82e-152">The use of [\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) in a federated security scenario can be decoupled into two logically independent phases, as described in the following sections.</span></span>  
  
### <a name="phase-1-design-phase"></a><span data-ttu-id="bc82e-153">Fáze 1: Fáze návrhu</span><span class="sxs-lookup"><span data-stu-id="bc82e-153">Phase 1: Design Phase</span></span>  
 <span data-ttu-id="bc82e-154">Během fáze návrhu klient používá [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ke čtení zásad koncový bod služby zveřejňuje a shromažďovat požadavky na ověřování a autorizaci služby.</span><span class="sxs-lookup"><span data-stu-id="bc82e-154">During the design phase, the client uses the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to read the policy the service endpoint exposes and to collect the service's authentication and authorization requirements.</span></span> <span data-ttu-id="bc82e-155">Příslušné proxy servery jsou konstruovány tak, aby vytvořily následující federovaný vzor komunikace zabezpečení v klientovi:</span><span class="sxs-lookup"><span data-stu-id="bc82e-155">The appropriate proxies are constructed to create the following federated security communication pattern at the client:</span></span>  
  
- <span data-ttu-id="bc82e-156">Získejte token zabezpečení ze služby STS ve sféře důvěryhodnosti klienta.</span><span class="sxs-lookup"><span data-stu-id="bc82e-156">Obtain a security token from the STS in the client trust realm.</span></span>  
  
- <span data-ttu-id="bc82e-157">Prezentujte token sts ve sféře vztahu důvěryhodnosti služby.</span><span class="sxs-lookup"><span data-stu-id="bc82e-157">Present the token to the STS in the service trust realm.</span></span>  
  
- <span data-ttu-id="bc82e-158">Získejte token zabezpečení ze služby STS ve sféře důvěryhodnosti služby.</span><span class="sxs-lookup"><span data-stu-id="bc82e-158">Obtain a security token from the STS in the service trust realm.</span></span>  
  
- <span data-ttu-id="bc82e-159">Prezentujte token službě pro přístup ke službě.</span><span class="sxs-lookup"><span data-stu-id="bc82e-159">Present the token to the service to access the service.</span></span>  
  
### <a name="phase-2-run-time-phase"></a><span data-ttu-id="bc82e-160">Fáze 2: Fáze běhu</span><span class="sxs-lookup"><span data-stu-id="bc82e-160">Phase 2: Run-Time Phase</span></span>  
 <span data-ttu-id="bc82e-161">Během fáze běhu klient vytvoří instance objektu třídy wcf klienta a provede volání pomocí klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="bc82e-161">During the run-time phase, the client instantiates an object of the WCF client class and makes a call using the WCF client.</span></span> <span data-ttu-id="bc82e-162">Základní rámec WCF zpracovává výše uvedené kroky ve federované matné komunikace zabezpečení vzor a umožňuje klientovi bezproblémově využívat službu.</span><span class="sxs-lookup"><span data-stu-id="bc82e-162">The underlying framework of WCF handles the previously mentioned steps in the federated security communication pattern and enables the client to seamlessly consume the service.</span></span>  
  
## <a name="sample-implementation-using-wcf"></a><span data-ttu-id="bc82e-163">Ukázková implementace pomocí WCF</span><span class="sxs-lookup"><span data-stu-id="bc82e-163">Sample Implementation Using WCF</span></span>  
 <span data-ttu-id="bc82e-164">Následující obrázek znázorňuje ukázkovou implementaci pro federovovnou architekturu zabezpečení pomocí nativní podpory z WCF.</span><span class="sxs-lookup"><span data-stu-id="bc82e-164">The following illustration shows a sample implementation for a federated security architecture using native support from WCF.</span></span>  
  
 ![Diagram znázorňující ukázkovou implementaci zabezpečení Federace.](./media/federation/federated-security-implementation.gif)  
  
### <a name="example-myservice"></a><span data-ttu-id="bc82e-166">Příklad MyService</span><span class="sxs-lookup"><span data-stu-id="bc82e-166">Example MyService</span></span>  
 <span data-ttu-id="bc82e-167">Služba `MyService` zpřístupňuje jeden koncový `MyServiceEndpoint`bod prostřednictvím .</span><span class="sxs-lookup"><span data-stu-id="bc82e-167">The service `MyService` exposes a single endpoint through `MyServiceEndpoint`.</span></span> <span data-ttu-id="bc82e-168">Následující obrázek znázorňuje adresu, vazbu a smlouvu přidruženou ke koncovému bodu.</span><span class="sxs-lookup"><span data-stu-id="bc82e-168">The following illustration shows the address, binding, and contract associated with the endpoint.</span></span>  
  
 ![Diagram znázorňující podrobnosti myserviceendpoint.](./media/federation/myserviceendpoint-details.gif)  
  
 <span data-ttu-id="bc82e-170">Koncový bod `MyServiceEndpoint` služby používá>[ \<wsFederationHttpBinding](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) a vyžaduje platný token jazyka svýrazná výrazy zabezpečení (SAML) s `accessAuthorized` deklarací vydanou službou STS B. To je deklarativně zadáno v konfiguraci služby.</span><span class="sxs-lookup"><span data-stu-id="bc82e-170">The service endpoint `MyServiceEndpoint` uses the [\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) and requires a valid Security Assertions Markup Language (SAML) token with an `accessAuthorized` claim issued by STS B. This is declaratively specified in the service configuration.</span></span>  
  
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
> <span data-ttu-id="bc82e-171">Je třeba uvést jemný bod o `MyService`tvrzeních požadovaných .</span><span class="sxs-lookup"><span data-stu-id="bc82e-171">A subtle point should be noted about the claims required by `MyService`.</span></span> <span data-ttu-id="bc82e-172">Druhý obrázek `MyService` označuje, že vyžaduje `accessAuthorized` token SAML s deklarací.</span><span class="sxs-lookup"><span data-stu-id="bc82e-172">The second figure indicates that `MyService` requires a SAML token with the `accessAuthorized` claim.</span></span> <span data-ttu-id="bc82e-173">Chcete-li být přesnější, určuje typ `MyService` deklarace, která vyžaduje.</span><span class="sxs-lookup"><span data-stu-id="bc82e-173">To be more precise, this specifies the claim type that `MyService` requires.</span></span> <span data-ttu-id="bc82e-174">Plně kvalifikovaný název tohoto typu `http://tempuri.org:accessAuthorized` deklarace je (spolu s přidruženým oborem názvů), který se používá v konfiguračním souboru služby.</span><span class="sxs-lookup"><span data-stu-id="bc82e-174">The fully-qualified name of this claim type is `http://tempuri.org:accessAuthorized` (along with the associated namespace), which is used in the service configuration file.</span></span> <span data-ttu-id="bc82e-175">Hodnota této deklarace označuje přítomnost této deklarace a `true` předpokládá se, že je nastavena na STS B.</span><span class="sxs-lookup"><span data-stu-id="bc82e-175">The value of this claim indicates the presence of this claim and is assumed to be set to `true` by STS B.</span></span>  
  
 <span data-ttu-id="bc82e-176">Za běhu je tato zásada `MyServiceOperationRequirement` vynucena třídou, která `MyService`je implementována jako součást .</span><span class="sxs-lookup"><span data-stu-id="bc82e-176">At runtime, this policy is enforced by the `MyServiceOperationRequirement` class that is implemented as part of the `MyService`.</span></span>  
  
 [!code-csharp[C_Federation#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#0)]
 [!code-vb[C_Federation#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#0)]  
[!code-csharp[C_Federation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#1)]
[!code-vb[C_Federation#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#1)]  
  
#### <a name="sts-b"></a><span data-ttu-id="bc82e-177">STS B</span><span class="sxs-lookup"><span data-stu-id="bc82e-177">STS B</span></span>  
 <span data-ttu-id="bc82e-178">Následující obrázek znázorňuje STS B. Jak již bylo uvedeno dříve, služba tokenů zabezpečení (STS) je také webová služba a může mít přidružené koncové body, zásady a tak dále.</span><span class="sxs-lookup"><span data-stu-id="bc82e-178">The following illustration shows the STS B. As stated earlier, a security token service (STS) is also a Web service and can have its associated endpoints, policy, and so on.</span></span>  
  
 ![Diagram znázorňující službu tokenů zabezpečení B.](./media/federation/myservice-security-token-service-b.gif)  
  
 <span data-ttu-id="bc82e-180">STS B zpřístupňuje jeden `STSEndpoint` koncový bod, volána, které lze použít k vyžádání tokeny zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="bc82e-180">STS B exposes a single endpoint, called `STSEndpoint` that can be use to request security tokens.</span></span> <span data-ttu-id="bc82e-181">Konkrétně STS B problémy SAML `accessAuthorized` tokeny s deklarací, které mohou být prezentovány na webu `MyService` služby pro přístup ke službě.</span><span class="sxs-lookup"><span data-stu-id="bc82e-181">Specifically, STS B issues SAML tokens with the `accessAuthorized` claim, which can be presented at the `MyService` service site for accessing the service.</span></span> <span data-ttu-id="bc82e-182">Sts B však vyžaduje, aby uživatelé předložili platný token `userAuthenticated` SAML vydaný společností STS A, který obsahuje deklaraci.</span><span class="sxs-lookup"><span data-stu-id="bc82e-182">However, STS B requires users to present a valid SAML token issued by STS A that contains the `userAuthenticated` claim.</span></span> <span data-ttu-id="bc82e-183">To je deklarativně zadáno v konfiguraci STS.</span><span class="sxs-lookup"><span data-stu-id="bc82e-183">This is declaratively specified in the STS configuration.</span></span>  
  
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
> <span data-ttu-id="bc82e-184">Opět platí, že deklarace `userAuthenticated` je typ deklarace, který je vyžadován STS B. Plně kvalifikovaný název tohoto typu `http://tempuri.org:userAuthenticated` deklarace je (spolu s přidruženým oborem názvů), který se používá v konfiguračním souboru STS.</span><span class="sxs-lookup"><span data-stu-id="bc82e-184">Again, the `userAuthenticated` claim is the claim type that is required by STS B. The fully-qualified name of this claim type is `http://tempuri.org:userAuthenticated` (along with the associated namespace), which is used in the STS configuration file.</span></span> <span data-ttu-id="bc82e-185">Hodnota této deklarace označuje přítomnost této deklarace a `true` předpokládá se, že je nastavena na STS A.</span><span class="sxs-lookup"><span data-stu-id="bc82e-185">The value of this claim indicates the presence of this claim and is assumed to be set to `true` by STS A.</span></span>  
  
 <span data-ttu-id="bc82e-186">Za běhu `STS_B_OperationRequirement` třída vynucuje tuto zásadu, která je implementována jako součást STS B.</span><span class="sxs-lookup"><span data-stu-id="bc82e-186">At runtime, the `STS_B_OperationRequirement` class enforces this policy, which is implemented as part of STS B.</span></span>  
  
 [!code-csharp[C_Federation#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#2)]
 [!code-vb[C_Federation#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#2)]  
  
 <span data-ttu-id="bc82e-187">Pokud kontrola přístupu je jasné, STS B `accessAuthorized` vydá token SAML s deklarací.</span><span class="sxs-lookup"><span data-stu-id="bc82e-187">If the access check is clear, STS B issues a SAML token with the `accessAuthorized` claim.</span></span>  
  
 [!code-csharp[C_Federation#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#3)]
 [!code-vb[C_Federation#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#3)]  
  
#### <a name="sts-a"></a><span data-ttu-id="bc82e-188">STS A</span><span class="sxs-lookup"><span data-stu-id="bc82e-188">STS A</span></span>  
 <span data-ttu-id="bc82e-189">Následující obrázek znázorňuje STS A.</span><span class="sxs-lookup"><span data-stu-id="bc82e-189">The following illustration shows the STS A.</span></span>  
  
 <span data-ttu-id="bc82e-190">![metadata](../../../../docs/framework/wcf/feature-details/media/sts-b.gif "STS_B")</span><span class="sxs-lookup"><span data-stu-id="bc82e-190">![Federation](../../../../docs/framework/wcf/feature-details/media/sts-b.gif "STS_B")</span></span>  
  
 <span data-ttu-id="bc82e-191">Podobně jako STS B, STS A je také webová služba, která vydává tokeny zabezpečení a zpřístupňuje jeden koncový bod pro tento účel.</span><span class="sxs-lookup"><span data-stu-id="bc82e-191">Similar to the STS B, the STS A is also a Web service that issues security tokens and exposes a single endpoint for this purpose.</span></span> <span data-ttu-id="bc82e-192">Používá však jinou`wsHttpBinding`vazbu ( ) a vyžaduje, `emailAddress` aby uživatelé předložili platný cardspace s deklarací.</span><span class="sxs-lookup"><span data-stu-id="bc82e-192">However, it uses a different binding (`wsHttpBinding`) and requires users to present a valid CardSpace with an `emailAddress` claim.</span></span> <span data-ttu-id="bc82e-193">V reakci na to vydává tokeny SAML s deklarací. `userAuthenticated`</span><span class="sxs-lookup"><span data-stu-id="bc82e-193">In response, it issues SAML tokens with the `userAuthenticated` claim.</span></span> <span data-ttu-id="bc82e-194">To je deklarativně zadáno v konfiguraci služby.</span><span class="sxs-lookup"><span data-stu-id="bc82e-194">This is declaratively specified in the service configuration.</span></span>  
  
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
  
 <span data-ttu-id="bc82e-195">Za běhu `STS_A_OperationRequirement` třída vynucuje tuto zásadu, která je implementována jako součást STS A.</span><span class="sxs-lookup"><span data-stu-id="bc82e-195">At runtime, the `STS_A_OperationRequirement` class enforces this policy, which is implemented as part of STS A.</span></span>  
  
 [!code-csharp[C_Federation#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#4)]
 [!code-vb[C_Federation#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#4)]  
  
 <span data-ttu-id="bc82e-196">Pokud je `true`přístup , STS A vydá `userAuthenticated` token SAML s deklarací.</span><span class="sxs-lookup"><span data-stu-id="bc82e-196">If the access is `true`, STS A issues a SAML token with `userAuthenticated` claim.</span></span>  
  
 [!code-csharp[C_Federation#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#5)]
 [!code-vb[C_Federation#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#5)]  
  
### <a name="client-at-organization-a"></a><span data-ttu-id="bc82e-197">Client ve společnosti Organization A</span><span class="sxs-lookup"><span data-stu-id="bc82e-197">Client at Organization A</span></span>  
 <span data-ttu-id="bc82e-198">Následující obrázek znázorňuje klienta v organizaci A `MyService` spolu s kroky, které se podílejí na volání služby.</span><span class="sxs-lookup"><span data-stu-id="bc82e-198">The following illustration shows the client at organization A, along with the steps involved in making a `MyService` service call.</span></span> <span data-ttu-id="bc82e-199">Ostatní funkční komponenty jsou také zahrnuty pro úplnost.</span><span class="sxs-lookup"><span data-stu-id="bc82e-199">The other functional components are also included for completeness.</span></span>  
  
 ![Diagram znázorňující kroky ve službě MyService volání.](./media/federation/federation-myservice-service-call-process.gif)  
  
## <a name="summary"></a><span data-ttu-id="bc82e-201">Souhrn</span><span class="sxs-lookup"><span data-stu-id="bc82e-201">Summary</span></span>  
 <span data-ttu-id="bc82e-202">Federované zabezpečení poskytuje čisté rozdělení odpovědnosti a pomáhá vytvářet zabezpečené a škálovatelné architektury služeb.</span><span class="sxs-lookup"><span data-stu-id="bc82e-202">Federated security provides a clean division of responsibility and helps to build secure, scalable service architectures.</span></span> <span data-ttu-id="bc82e-203">Jako platforma pro vytváření a nasazování distribuovaných aplikací poskytuje WCF nativní podporu pro implementaci federovaného zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="bc82e-203">As a platform for building and deploying distributed applications, WCF provides native support for implementing federated security.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc82e-204">Viz také</span><span class="sxs-lookup"><span data-stu-id="bc82e-204">See also</span></span>

- [<span data-ttu-id="bc82e-205">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="bc82e-205">Security</span></span>](../../../../docs/framework/wcf/feature-details/security.md)
