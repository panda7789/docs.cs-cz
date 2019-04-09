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
ms.openlocfilehash: af3e5c4c33936e809438019f1a8af823ffc3e52b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59114026"
---
# <a name="federation"></a><span data-ttu-id="e5879-102">Federace</span><span class="sxs-lookup"><span data-stu-id="e5879-102">Federation</span></span>
<span data-ttu-id="e5879-103">Toto téma nabízí stručný přehled konceptů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="e5879-103">This topic provides a brief overview of the concept of federated security.</span></span> <span data-ttu-id="e5879-104">Popisuje také podporu Windows Communication Foundation (WCF) pro nasazení architektury zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="e5879-104">It also describes Windows Communication Foundation (WCF) support for deploying federated security architectures.</span></span> <span data-ttu-id="e5879-105">Ukázková aplikace, které ukazuje, federace, naleznete v tématu [ukázka federace](../../../../docs/framework/wcf/samples/federation-sample.md).</span><span class="sxs-lookup"><span data-stu-id="e5879-105">For a sample application that demonstrates federation, see [Federation Sample](../../../../docs/framework/wcf/samples/federation-sample.md).</span></span>  
  
## <a name="definition-of-federated-security"></a><span data-ttu-id="e5879-106">Definice zabezpečení</span><span class="sxs-lookup"><span data-stu-id="e5879-106">Definition of Federated Security</span></span>  
 <span data-ttu-id="e5879-107">Zabezpečení umožňuje čisté oddělení mezi službu, kterou klient přistupuje a přidružené procedury ověřování a autorizace.</span><span class="sxs-lookup"><span data-stu-id="e5879-107">Federated security allows for clean separation between the service a client is accessing and the associated authentication and authorization procedures.</span></span> <span data-ttu-id="e5879-108">Zabezpečení také umožňuje spolupráci mezi více systémy, sítě a organizací ve sférách různých důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="e5879-108">Federated security also enables collaboration across multiple systems, networks, and organizations in different trust realms.</span></span>  
  
 <span data-ttu-id="e5879-109">WCF poskytuje podporu pro sestavování a nasazování distribuovaných systémů, které využívají zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="e5879-109">WCF provides support for building and deploying distributed systems that employ federated security.</span></span>  
  
### <a name="elements-of-a-federated-security-architecture"></a><span data-ttu-id="e5879-110">Prvky architektury zabezpečení</span><span class="sxs-lookup"><span data-stu-id="e5879-110">Elements of a Federated Security Architecture</span></span>  
 <span data-ttu-id="e5879-111">Architektura zabezpečení má tři klíčové prvky, jak je popsáno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="e5879-111">The federated security architecture has three key elements, as described in the following table.</span></span>  
  
|<span data-ttu-id="e5879-112">Prvek</span><span class="sxs-lookup"><span data-stu-id="e5879-112">Element</span></span>|<span data-ttu-id="e5879-113">Popis</span><span class="sxs-lookup"><span data-stu-id="e5879-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e5879-114">Domain/realm</span><span class="sxs-lookup"><span data-stu-id="e5879-114">Domain/realm</span></span>|<span data-ttu-id="e5879-115">Jedna jednotka správy zabezpečení nebo vztah důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="e5879-115">A single unit of security administration or trust.</span></span> <span data-ttu-id="e5879-116">Typické domény může obsahovat jednu organizaci.</span><span class="sxs-lookup"><span data-stu-id="e5879-116">A typical domain might include a single organization.</span></span>|  
|<span data-ttu-id="e5879-117">Federace</span><span class="sxs-lookup"><span data-stu-id="e5879-117">Federation</span></span>|<span data-ttu-id="e5879-118">Sada domény, které mají vztah důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="e5879-118">A collection of domains that have established trust.</span></span> <span data-ttu-id="e5879-119">Úroveň důvěryhodnosti mohou lišit, ale obvykle zahrnuje ověřování a téměř vždy obsahuje autorizaci.</span><span class="sxs-lookup"><span data-stu-id="e5879-119">The level of trust may vary, but typically includes authentication and almost always includes authorization.</span></span> <span data-ttu-id="e5879-120">Typické federace může obsahovat několik organizací, které mají vztah důvěryhodnosti pro sdílený přístup k sadu prostředků.</span><span class="sxs-lookup"><span data-stu-id="e5879-120">A typical federation might include a number of organizations that have established trust for shared access to a set of resources.</span></span>|  
|<span data-ttu-id="e5879-121">Služba tokenů zabezpečení (STS)</span><span class="sxs-lookup"><span data-stu-id="e5879-121">Security Token Service (STS)</span></span>|<span data-ttu-id="e5879-122">Webová služba, která vydává tokeny zabezpečení; To znamená je založen na důkaz, že důvěřuje na všechny uživatele, kteří důvěřuje kontrolní výrazy.</span><span class="sxs-lookup"><span data-stu-id="e5879-122">A Web service that issues security tokens; that is, it makes assertions based on evidence that it trusts, to whomever trusts it.</span></span> <span data-ttu-id="e5879-123">Tento balíček je základem zprostředkování vztahu důvěryhodnosti mezi doménami.</span><span class="sxs-lookup"><span data-stu-id="e5879-123">This forms the basis of trust brokering between domains.</span></span>|  
  
### <a name="example-scenario"></a><span data-ttu-id="e5879-124">Příklad scénáře</span><span class="sxs-lookup"><span data-stu-id="e5879-124">Example Scenario</span></span>  
 <span data-ttu-id="e5879-125">Následující obrázek znázorňuje příklad federovaného zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="e5879-125">The following illustration shows an example of federated security.</span></span>  
  
 <span data-ttu-id="e5879-126">![Federation](../../../../docs/framework/wcf/feature-details/media/typicalfederatedsecurityscenario.gif "TypicalFederatedSecurityScenario")</span><span class="sxs-lookup"><span data-stu-id="e5879-126">![Federation](../../../../docs/framework/wcf/feature-details/media/typicalfederatedsecurityscenario.gif "TypicalFederatedSecurityScenario")</span></span>  
  
 <span data-ttu-id="e5879-127">Tento scénář obsahuje dvě organizace: A a B B. organizace má webový prostředek (webová služba), někteří uživatelé v organizaci A najít užitečné.</span><span class="sxs-lookup"><span data-stu-id="e5879-127">This scenario includes two organizations: A and B. Organization B has a Web resource (a Web service) that some users in organization A find valuable.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e5879-128">Tato část používá podmínky *prostředků*, *služby*, a *webovou službu* Zaměnitelně.</span><span class="sxs-lookup"><span data-stu-id="e5879-128">This section uses the terms *resource*, *service*, and *Web service* interchangeably.</span></span>  
  
 <span data-ttu-id="e5879-129">Organizace B obvykle vyžaduje, že uživatel z organizace A zadat nějakou platnou formu ověřování před přístupu ke službě.</span><span class="sxs-lookup"><span data-stu-id="e5879-129">Typically, organization B requires that a user from organization A provide some valid form of authentication before accessing the service.</span></span> <span data-ttu-id="e5879-130">Kromě toho organizace může také vyžadovat, že uživatel oprávnění k přístupu na příslušném konkrétního prostředku.</span><span class="sxs-lookup"><span data-stu-id="e5879-130">In addition, the organization may also require that the user be authorized to access the specific resource in question.</span></span> <span data-ttu-id="e5879-131">Jedním ze způsobů řešení tohoto problému a umožňují uživatelům v organizaci A pro přístup k prostředku v organizaci B je následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="e5879-131">One way to address this problem and enable users in organization A to access the resource in organization B is as follows:</span></span>  
  
-   <span data-ttu-id="e5879-132">Uživatelé v organizaci A zaregistrovat své přihlašovací údaje (uživatelské jméno a heslo) s organizací B.</span><span class="sxs-lookup"><span data-stu-id="e5879-132">Users from organization A register their credentials (a user name and password) with organization B.</span></span>  
  
-   <span data-ttu-id="e5879-133">Během přístupu k prostředkům uživatelů z organizace A poskytl svá pověření pro organizaci B a ověření před přístupem k prostředku.</span><span class="sxs-lookup"><span data-stu-id="e5879-133">During the resource access, users from organization A present their credentials to organization B and are authenticated before accessing the resource.</span></span>  
  
 <span data-ttu-id="e5879-134">Tento přístup má tři významné nevýhody:</span><span class="sxs-lookup"><span data-stu-id="e5879-134">This approach has three significant drawbacks:</span></span>  
  
-   <span data-ttu-id="e5879-135">Organizace B má ke správě přihlašovacích údajů pro uživatele z organizace A kromě správy pověření své místní uživatelé.</span><span class="sxs-lookup"><span data-stu-id="e5879-135">Organization B has to manage the credentials for users from organization A in addition to managing the credentials of its local users.</span></span>  
  
-   <span data-ttu-id="e5879-136">Uživatelé v organizaci A nemusíte Udržovat další sadu pověření (to znamená, nezapomeňte další uživatelské jméno a heslo) kromě přihlašovací údaje, obvykle používají pro získání přístupu k prostředkům v rámci organizace A. To obvykle doporučuje praxe používání stejné uživatelské jméno a heslo ve víc lokalitách služby, který je slabé bezpečnostní opatření.</span><span class="sxs-lookup"><span data-stu-id="e5879-136">Users in organization A need to maintain an additional set of credentials (that is, remember an additional user name and password) apart from the credentials they normally use to gain access to resources within organization A. This usually encourages the practice of using the same user name and password at multiple service sites, which is a weak security measure.</span></span>  
  
-   <span data-ttu-id="e5879-137">Architektura nejsou adekvátní jako víc organizací vnímat prostředek na organizace B tak, jak se některé hodnoty.</span><span class="sxs-lookup"><span data-stu-id="e5879-137">The architecture does not scale as more organizations perceive the resource at organization B as being of some value.</span></span>  
  
 <span data-ttu-id="e5879-138">Alternativním přístupem, což reaguje na výše uvedené nevýhody, má odlišnou úroveň zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="e5879-138">An alternative approach, which addresses the previously mentioned drawbacks, is to employ federated security.</span></span> <span data-ttu-id="e5879-139">V takovém případě organizací A a B navázání vztahu důvěryhodnosti a využívat službu tokenů zabezpečení (STS) umožňující ručním vytvořen vztah důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="e5879-139">In this approach, organizations A and B establish a trust relationship and employ Security Token Service (STS) to enable brokering of the established trust.</span></span>  
  
 <span data-ttu-id="e5879-140">V architektuře zabezpečení uživatelům v organizaci A vědět, že pokud chtějí přístup k webové službě v organizaci B, který se musí poskytnout token platný zabezpečení ze služby STS na organizaci B, která ověřuje a autorizuje jeho přístup k konkrétní službu.</span><span class="sxs-lookup"><span data-stu-id="e5879-140">In a federated security architecture, users from organization A know that if they want to access the Web service in organization B that they must present a valid security token from the STS at organization B, which authenticates and authorizes their access to the specific service.</span></span>  
  
 <span data-ttu-id="e5879-141">O kontaktování služby tokenů zabezpečení B, uživatelé dostanou jinou úroveň dereference ze zásady přidružené k Služba tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="e5879-141">On contacting the STS B, the users receive another level of indirection from the policy associated with the STS.</span></span> <span data-ttu-id="e5879-142">Platný zabezpečení se musí poskytnout token od služby STS A (to znamená, sféry klienta vztahu důvěryhodnosti) před B služby tokenů zabezpečení můžete jim nabídnete token zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="e5879-142">They must present a valid security token from the STS A (that is, the client trust realm) before the STS B can issue them a security token.</span></span> <span data-ttu-id="e5879-143">Toto je důsledkem této vztah důvěryhodnosti mezi dvěma organizacemi a znamená, že organizace B nemá ke správě identit uživatelů z organizace A. V praxi, služba tokenů zabezpečení B obvykle má hodnotu null `issuerAddress` a `issuerMetadataAddress`.</span><span class="sxs-lookup"><span data-stu-id="e5879-143">This is a corollary of the trust relationship established between the two organizations and implies that organization B does not have to manage identities for users from organization A. In practice, STS B typically has a null `issuerAddress` and `issuerMetadataAddress`.</span></span> <span data-ttu-id="e5879-144">Další informace najdete v tématu [jak: Konfigurace místního vystavitele](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).</span><span class="sxs-lookup"><span data-stu-id="e5879-144">For more information, see [How to: Configure a Local Issuer](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span> <span data-ttu-id="e5879-145">V takovém případě klienta consults místních zásad vyhledejte STS A. Tato konfigurace se nazývá *domovskou sféru federace* a škáluje líp, protože není nutné udržovat informace o STS A. B služby tokenů zabezpečení</span><span class="sxs-lookup"><span data-stu-id="e5879-145">In that case, the client consults a local policy to locate STS A. This configuration is called *home realm federation* and it scales better because STS B does not have to maintain information about STS A.</span></span>  
  
 <span data-ttu-id="e5879-146">Uživatelé pak obraťte se na službu tokenů zabezpečení v organizaci A a získat token zabezpečení tím, že předloží přihlašovacími údaji, které běžně používáte pro přístup k žádnému jinému prostředku v rámci organizace A. To také řeší problém uživatelé museli udržovat několik sad přihlašovacích údajů nebo ve víc lokalitách služby pomocí jednou sadou přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="e5879-146">The users then contact the STS at organization A and obtain a security token by presenting authentication credentials that they normally use to gain access to any other resource within organization A. This also alleviates the problem of users having to maintain multiple sets of credentials or using the same set of credentials at multiple service sites.</span></span>  
  
 <span data-ttu-id="e5879-147">Jakmile uživatelé získat token zabezpečení ze služby STS A jsou k dispozici token, který má služba tokenů zabezpečení B. organizace B pokračuje k autorizaci požadavků uživatelů a vydá token zabezpečení pro uživatele ze své vlastní sada tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="e5879-147">Once the users obtain a security token from the STS A, they present the token to the STS B. Organization B proceeds to perform authorization of the users' requests and issues a security token to the users from its own set of security tokens.</span></span> <span data-ttu-id="e5879-148">Uživatele můžete předložit jejich token prostředku v organizaci B a přístup ke službě.</span><span class="sxs-lookup"><span data-stu-id="e5879-148">The users can then present their token to the resource at organization B and access the service.</span></span>  
  
## <a name="support-for-federated-security-in-wcf"></a><span data-ttu-id="e5879-149">Podpora pro zabezpečení ve WCF</span><span class="sxs-lookup"><span data-stu-id="e5879-149">Support for Federated Security in WCF</span></span>  
 <span data-ttu-id="e5879-150">WCF poskytuje kompletní podpory pro nasazení architektury zabezpečení prostřednictvím [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="e5879-150">WCF provides turnkey support for deploying federated security architectures through the [\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span></span>  
  
 <span data-ttu-id="e5879-151">[ \<WsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) element poskytuje pro zabezpečené, spolehlivé a interoperabilní vazbu, která zahrnuje použití protokolu HTTP jako podkladový přenosový mechanismus pro komunikaci styl požadavek odpověď, Když text a XML jako přenosový formát pro kódování.</span><span class="sxs-lookup"><span data-stu-id="e5879-151">The [\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) element provides for a secure, reliable, interoperable binding that entails the use of HTTP as the underlying transport mechanism for request-reply communication style, employing text and XML as the wire format for encoding.</span></span>  
  
 <span data-ttu-id="e5879-152">Použití [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) federovaného zabezpečení scénář mohou být oddělené do dvou logicky nezávislý fází, jak je popsáno v následujících částech.</span><span class="sxs-lookup"><span data-stu-id="e5879-152">The use of [\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) in a federated security scenario can be decoupled into two logically independent phases, as described in the following sections.</span></span>  
  
### <a name="phase-1-design-phase"></a><span data-ttu-id="e5879-153">Fáze 1: Fáze návrhu</span><span class="sxs-lookup"><span data-stu-id="e5879-153">Phase 1: Design Phase</span></span>  
 <span data-ttu-id="e5879-154">Během fáze návrhu, klient použije [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) zásadách zpřístupňuje koncový bod služby a shromažďování požadavky služby ověřování a autorizaci.</span><span class="sxs-lookup"><span data-stu-id="e5879-154">During the design phase, the client uses the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to read the policy the service endpoint exposes and to collect the service's authentication and authorization requirements.</span></span> <span data-ttu-id="e5879-155">Příslušný proxy servery jsou sestavené tak, aby vytvořit následující vzor komunikace zabezpečení u klienta:</span><span class="sxs-lookup"><span data-stu-id="e5879-155">The appropriate proxies are constructed to create the following federated security communication pattern at the client:</span></span>  
  
-   <span data-ttu-id="e5879-156">Získáte token zabezpečení ze služby STS ve vztahu důvěryhodnosti sféry klienta.</span><span class="sxs-lookup"><span data-stu-id="e5879-156">Obtain a security token from the STS in the client trust realm.</span></span>  
  
-   <span data-ttu-id="e5879-157">K dispozici token na službu STS ve sféře vztah důvěryhodnosti služby.</span><span class="sxs-lookup"><span data-stu-id="e5879-157">Present the token to the STS in the service trust realm.</span></span>  
  
-   <span data-ttu-id="e5879-158">Získáte token zabezpečení ze služby STS ve sféře vztah důvěryhodnosti služby.</span><span class="sxs-lookup"><span data-stu-id="e5879-158">Obtain a security token from the STS in the service trust realm.</span></span>  
  
-   <span data-ttu-id="e5879-159">K dispozici token, který má služba pro přístup ke službě.</span><span class="sxs-lookup"><span data-stu-id="e5879-159">Present the token to the service to access the service.</span></span>  
  
### <a name="phase-2-run-time-phase"></a><span data-ttu-id="e5879-160">Fáze 2: Fáze za běhu</span><span class="sxs-lookup"><span data-stu-id="e5879-160">Phase 2: Run-Time Phase</span></span>  
 <span data-ttu-id="e5879-161">Během fáze za běhu klient vytvoří instanci objektu třídy klienta WCF a provede volání pomocí klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="e5879-161">During the run-time phase, the client instantiates an object of the WCF client class and makes a call using the WCF client.</span></span> <span data-ttu-id="e5879-162">Základní architektury WCF zpracovává výše uvedené kroky v modelu zabezpečení komunikace a umožňuje klientovi bez problémů využívat služby.</span><span class="sxs-lookup"><span data-stu-id="e5879-162">The underlying framework of WCF handles the previously mentioned steps in the federated security communication pattern and enables the client to seamlessly consume the service.</span></span>  
  
## <a name="sample-implementation-using-wcf"></a><span data-ttu-id="e5879-163">Ukázková implementace pomocí technologie WCF</span><span class="sxs-lookup"><span data-stu-id="e5879-163">Sample Implementation Using WCF</span></span>  
 <span data-ttu-id="e5879-164">Následující obrázek znázorňuje ukázku implementace pro architekturu zabezpečení s využitím nativní podpory z WCF.</span><span class="sxs-lookup"><span data-stu-id="e5879-164">The following illustration shows a sample implementation for a federated security architecture using native support from WCF.</span></span>  
  
 <span data-ttu-id="e5879-165">![Federace zabezpečení ve službě WCF](../../../../docs/framework/wcf/feature-details/media/federatedsecurityinwcf.gif "FederatedSecurityInWCF")</span><span class="sxs-lookup"><span data-stu-id="e5879-165">![Federation security in WCF](../../../../docs/framework/wcf/feature-details/media/federatedsecurityinwcf.gif "FederatedSecurityInWCF")</span></span>  
  
### <a name="example-myservice"></a><span data-ttu-id="e5879-166">Příklad Moje_služba</span><span class="sxs-lookup"><span data-stu-id="e5879-166">Example MyService</span></span>  
 <span data-ttu-id="e5879-167">Služba `MyService` poskytuje jeden koncový bod prostřednictvím `MyServiceEndpoint`.</span><span class="sxs-lookup"><span data-stu-id="e5879-167">The service `MyService` exposes a single endpoint through `MyServiceEndpoint`.</span></span> <span data-ttu-id="e5879-168">Následující obrázek znázorňuje adresa, vazba a kontrakt přidružený k koncový bod.</span><span class="sxs-lookup"><span data-stu-id="e5879-168">The following illustration shows the address, binding, and contract associated with the endpoint.</span></span>  
  
 <span data-ttu-id="e5879-169">![Federation](../../../../docs/framework/wcf/feature-details/media/myservice.gif "MyService")</span><span class="sxs-lookup"><span data-stu-id="e5879-169">![Federation](../../../../docs/framework/wcf/feature-details/media/myservice.gif "MyService")</span></span>  
  
 <span data-ttu-id="e5879-170">Koncový bod služby `MyServiceEndpoint` používá [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) a vyžaduje platný token zabezpečení kontrolní výrazy SAML (Markup Language) pomocí `accessAuthorized` vydané služby serveru B. služby tokenů zabezpečení deklarace identity To je určeno deklarativně v konfiguraci služby.</span><span class="sxs-lookup"><span data-stu-id="e5879-170">The service endpoint `MyServiceEndpoint` uses the [\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) and requires a valid Security Assertions Markup Language (SAML) token with an `accessAuthorized` claim issued by STS B. This is declaratively specified in the service configuration.</span></span>  
  
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
>  <span data-ttu-id="e5879-171">Bod drobným potřeba poznamenat týkající se deklarací vyžadované `MyService`.</span><span class="sxs-lookup"><span data-stu-id="e5879-171">A subtle point should be noted about the claims required by `MyService`.</span></span> <span data-ttu-id="e5879-172">Druhý obrázek označuje, že `MyService` vyžaduje token SAML se `accessAuthorized` deklarací identity.</span><span class="sxs-lookup"><span data-stu-id="e5879-172">The second figure indicates that `MyService` requires a SAML token with the `accessAuthorized` claim.</span></span> <span data-ttu-id="e5879-173">Přesněji, určuje typ deklarace identity, aby `MyService` vyžaduje.</span><span class="sxs-lookup"><span data-stu-id="e5879-173">To be more precise, this specifies the claim type that `MyService` requires.</span></span> <span data-ttu-id="e5879-174">Plně kvalifikovaný název tohoto typu deklarace identity je `http://tempuri.org:accessAuthorized` (spolu s přidružené oboru názvů), který se používá v konfiguračním souboru služby.</span><span class="sxs-lookup"><span data-stu-id="e5879-174">The fully-qualified name of this claim type is `http://tempuri.org:accessAuthorized` (along with the associated namespace), which is used in the service configuration file.</span></span> <span data-ttu-id="e5879-175">Hodnota této deklarace indikuje přítomnost této deklarace identity a předpokládá, že je nastavena na `true` službou STS B.</span><span class="sxs-lookup"><span data-stu-id="e5879-175">The value of this claim indicates the presence of this claim and is assumed to be set to `true` by STS B.</span></span>  
  
 <span data-ttu-id="e5879-176">V době běhu je vynucuje tuto zásadu `MyServiceOperationRequirement` třídu, která je implementovaná jako součást `MyService`.</span><span class="sxs-lookup"><span data-stu-id="e5879-176">At runtime, this policy is enforced by the `MyServiceOperationRequirement` class that is implemented as part of the `MyService`.</span></span>  
  
 [!code-csharp[C_Federation#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#0)]
 [!code-vb[C_Federation#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#0)]  
[!code-csharp[C_Federation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#1)]
[!code-vb[C_Federation#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#1)]  
  
#### <a name="sts-b"></a><span data-ttu-id="e5879-177">STS B</span><span class="sxs-lookup"><span data-stu-id="e5879-177">STS B</span></span>  
 <span data-ttu-id="e5879-178">Následující obrázek znázorňuje STS B. Jak bylo uvedeno dříve, služby tokenů zabezpečení (STS) je také webovou službu a může mít jeho přidruženými koncovými body, zásad a tak dále.</span><span class="sxs-lookup"><span data-stu-id="e5879-178">The following illustration shows the STS B. As stated earlier, a security token service (STS) is also a Web service and can have its associated endpoints, policy, and so on.</span></span>  
  
 <span data-ttu-id="e5879-179">![Federation](../../../../docs/framework/wcf/feature-details/media/msservicestsb.gif "MsServiceSTSB")</span><span class="sxs-lookup"><span data-stu-id="e5879-179">![Federation](../../../../docs/framework/wcf/feature-details/media/msservicestsb.gif "MsServiceSTSB")</span></span>  
  
 <span data-ttu-id="e5879-180">Služba tokenů zabezpečení B poskytuje jeden koncový bod, volá se `STSEndpoint` , který lze použít k žádosti o tokeny zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="e5879-180">STS B exposes a single endpoint, called `STSEndpoint` that can be use to request security tokens.</span></span> <span data-ttu-id="e5879-181">Konkrétně STS B vystavuje tokeny SAML s `accessAuthorized` deklarace identity, které lze zobrazit na `MyService` služeb – web pro přístupu ke službě.</span><span class="sxs-lookup"><span data-stu-id="e5879-181">Specifically, STS B issues SAML tokens with the `accessAuthorized` claim, which can be presented at the `MyService` service site for accessing the service.</span></span> <span data-ttu-id="e5879-182">Však vyžaduje, aby službu STS B uživatelé, předložit platný token SAML vydané A Služba tokenů zabezpečení, který obsahuje `userAuthenticated` deklarací identity.</span><span class="sxs-lookup"><span data-stu-id="e5879-182">However, STS B requires users to present a valid SAML token issued by STS A that contains the `userAuthenticated` claim.</span></span> <span data-ttu-id="e5879-183">To je určeno deklarativně v konfiguraci služby tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="e5879-183">This is declaratively specified in the STS configuration.</span></span>  
  
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
>  <span data-ttu-id="e5879-184">Znovu `userAuthenticated` deklarace identity je typ deklarace identity, který vyžaduje službu STS B. Plně kvalifikovaný název tohoto typu deklarace identity je `http://tempuri.org:userAuthenticated` (spolu s přidružené oboru názvů), který se používá v konfiguračním souboru služby tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="e5879-184">Again, the `userAuthenticated` claim is the claim type that is required by STS B. The fully-qualified name of this claim type is `http://tempuri.org:userAuthenticated` (along with the associated namespace), which is used in the STS configuration file.</span></span> <span data-ttu-id="e5879-185">Hodnota této deklarace indikuje přítomnost této deklarace identity a předpokládá, že je nastavena na `true` službou STS A.</span><span class="sxs-lookup"><span data-stu-id="e5879-185">The value of this claim indicates the presence of this claim and is assumed to be set to `true` by STS A.</span></span>  
  
 <span data-ttu-id="e5879-186">V době běhu `STS_B_OperationRequirement` třídě vynucuje tuto zásadu, která je implementovaná jako součást služby serveru B. služby tokenů zabezpečení</span><span class="sxs-lookup"><span data-stu-id="e5879-186">At runtime, the `STS_B_OperationRequirement` class enforces this policy, which is implemented as part of STS B.</span></span>  
  
 [!code-csharp[C_Federation#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#2)]
 [!code-vb[C_Federation#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#2)]  
  
 <span data-ttu-id="e5879-187">Pokud kontrola přístupu je jasné, služba tokenů zabezpečení B vydá token SAML s `accessAuthorized` deklarací identity.</span><span class="sxs-lookup"><span data-stu-id="e5879-187">If the access check is clear, STS B issues a SAML token with the `accessAuthorized` claim.</span></span>  
  
 [!code-csharp[C_Federation#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#3)]
 [!code-vb[C_Federation#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#3)]  
  
#### <a name="sts-a"></a><span data-ttu-id="e5879-188">STS A</span><span class="sxs-lookup"><span data-stu-id="e5879-188">STS A</span></span>  
 <span data-ttu-id="e5879-189">Následující obrázek znázorňuje STS A.</span><span class="sxs-lookup"><span data-stu-id="e5879-189">The following illustration shows the STS A.</span></span>  
  
 <span data-ttu-id="e5879-190">![Federace](../../../../docs/framework/wcf/feature-details/media/sts-b.gif "STS_B")</span><span class="sxs-lookup"><span data-stu-id="e5879-190">![Federation](../../../../docs/framework/wcf/feature-details/media/sts-b.gif "STS_B")</span></span>  
  
 <span data-ttu-id="e5879-191">Podobně jako služba tokenů zabezpečení B, A Služba tokenů zabezpečení je také webovou službu, která vydává tokeny zabezpečení a poskytuje jeden koncový bod pro tento účel.</span><span class="sxs-lookup"><span data-stu-id="e5879-191">Similar to the STS B, the STS A is also a Web service that issues security tokens and exposes a single endpoint for this purpose.</span></span> <span data-ttu-id="e5879-192">Ale používá jinou vazbou (`wsHttpBinding`) a vyžaduje, aby uživatelé k dispozici platný [!INCLUDE[infocard](../../../../includes/infocard-md.md)] s `emailAddress` deklarací identity.</span><span class="sxs-lookup"><span data-stu-id="e5879-192">However, it uses a different binding (`wsHttpBinding`) and requires users to present a valid [!INCLUDE[infocard](../../../../includes/infocard-md.md)] with an `emailAddress` claim.</span></span> <span data-ttu-id="e5879-193">V odpovědi, vystavuje tokeny SAML s `userAuthenticated` deklarací identity.</span><span class="sxs-lookup"><span data-stu-id="e5879-193">In response, it issues SAML tokens with the `userAuthenticated` claim.</span></span> <span data-ttu-id="e5879-194">To je určeno deklarativně v konfiguraci služby.</span><span class="sxs-lookup"><span data-stu-id="e5879-194">This is declaratively specified in the service configuration.</span></span>  
  
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
  
 <span data-ttu-id="e5879-195">V době běhu `STS_A_OperationRequirement` třídy vynucuje tuto zásadu, která je implementovaná jako součást služby tokenů zabezpečení A.</span><span class="sxs-lookup"><span data-stu-id="e5879-195">At runtime, the `STS_A_OperationRequirement` class enforces this policy, which is implemented as part of STS A.</span></span>  
  
 [!code-csharp[C_Federation#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#4)]
 [!code-vb[C_Federation#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#4)]  
  
 <span data-ttu-id="e5879-196">Pokud je přístup `true`, služba tokenů zabezpečení A vydá token SAML s `userAuthenticated` deklarací identity.</span><span class="sxs-lookup"><span data-stu-id="e5879-196">If the access is `true`, STS A issues a SAML token with `userAuthenticated` claim.</span></span>  
  
 [!code-csharp[C_Federation#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#5)]
 [!code-vb[C_Federation#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#5)]  
  
### <a name="client-at-organization-a"></a><span data-ttu-id="e5879-197">Klient v organizaci A</span><span class="sxs-lookup"><span data-stu-id="e5879-197">Client at Organization A</span></span>  
 <span data-ttu-id="e5879-198">Následující obrázek znázorňuje klienta v organizaci A spolu s jednotlivými kroky při vytváření `MyService` volání.</span><span class="sxs-lookup"><span data-stu-id="e5879-198">The following illustration shows the client at organization A, along with the steps involved in making a `MyService` service call.</span></span> <span data-ttu-id="e5879-199">Funkční součásti jsou také zahrnuté pro úplnost.</span><span class="sxs-lookup"><span data-stu-id="e5879-199">The other functional components are also included for completeness.</span></span>  
  
 <span data-ttu-id="e5879-200">![Federation](../../../../docs/framework/wcf/feature-details/media/federationclienta.gif "FederationClientA")</span><span class="sxs-lookup"><span data-stu-id="e5879-200">![Federation](../../../../docs/framework/wcf/feature-details/media/federationclienta.gif "FederationClientA")</span></span>  
  
## <a name="summary"></a><span data-ttu-id="e5879-201">Souhrn</span><span class="sxs-lookup"><span data-stu-id="e5879-201">Summary</span></span>  
 <span data-ttu-id="e5879-202">Zabezpečení nabízí čisté dělení zodpovědnosti a pomáhá vytvářet zabezpečené, škálovatelné služby architektury.</span><span class="sxs-lookup"><span data-stu-id="e5879-202">Federated security provides a clean division of responsibility and helps to build secure, scalable service architectures.</span></span> <span data-ttu-id="e5879-203">Jako platformu pro sestavování a nasazování distribuovaných aplikací WCF poskytuje nativní podporu pro implementaci zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="e5879-203">As a platform for building and deploying distributed applications, WCF provides native support for implementing federated security.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5879-204">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e5879-204">See also</span></span>

- [<span data-ttu-id="e5879-205">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="e5879-205">Security</span></span>](../../../../docs/framework/wcf/feature-details/security.md)
