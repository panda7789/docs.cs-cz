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
ms.openlocfilehash: 2331e484f22be7e3154a4cff981ee320a9b143a5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69948156"
---
# <a name="federation"></a><span data-ttu-id="55a4b-102">Federace</span><span class="sxs-lookup"><span data-stu-id="55a4b-102">Federation</span></span>
<span data-ttu-id="55a4b-103">Toto téma poskytuje stručný přehled konceptu federovaného zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="55a4b-103">This topic provides a brief overview of the concept of federated security.</span></span> <span data-ttu-id="55a4b-104">Popisuje také podporu Windows Communication Foundation (WCF) pro nasazení federovaných architektur zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="55a4b-104">It also describes Windows Communication Foundation (WCF) support for deploying federated security architectures.</span></span> <span data-ttu-id="55a4b-105">Ukázkovou aplikaci, která demonstruje federaci, najdete v tématu [federace – ukázka](../../../../docs/framework/wcf/samples/federation-sample.md).</span><span class="sxs-lookup"><span data-stu-id="55a4b-105">For a sample application that demonstrates federation, see [Federation Sample](../../../../docs/framework/wcf/samples/federation-sample.md).</span></span>  
  
## <a name="definition-of-federated-security"></a><span data-ttu-id="55a4b-106">Definice federovaného zabezpečení</span><span class="sxs-lookup"><span data-stu-id="55a4b-106">Definition of Federated Security</span></span>  
 <span data-ttu-id="55a4b-107">Federované zabezpečení umožňuje čisté oddělení mezi službou, ke které klient přistupuje, a přidruženými postupy ověřování a autorizace.</span><span class="sxs-lookup"><span data-stu-id="55a4b-107">Federated security allows for clean separation between the service a client is accessing and the associated authentication and authorization procedures.</span></span> <span data-ttu-id="55a4b-108">Federované zabezpečení také umožňuje spolupráci napříč různými systémy, sítěmi a organizacemi v různých sférách vztahů důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="55a4b-108">Federated security also enables collaboration across multiple systems, networks, and organizations in different trust realms.</span></span>  
  
 <span data-ttu-id="55a4b-109">WCF poskytuje podporu pro sestavování a nasazování distribuovaných systémů, které využívají federované zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="55a4b-109">WCF provides support for building and deploying distributed systems that employ federated security.</span></span>  
  
### <a name="elements-of-a-federated-security-architecture"></a><span data-ttu-id="55a4b-110">Prvky federované architektury zabezpečení</span><span class="sxs-lookup"><span data-stu-id="55a4b-110">Elements of a Federated Security Architecture</span></span>  
 <span data-ttu-id="55a4b-111">Architektura federovaného zabezpečení má tři klíčové prvky, jak je popsáno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="55a4b-111">The federated security architecture has three key elements, as described in the following table.</span></span>  
  
|<span data-ttu-id="55a4b-112">Prvek</span><span class="sxs-lookup"><span data-stu-id="55a4b-112">Element</span></span>|<span data-ttu-id="55a4b-113">Popis</span><span class="sxs-lookup"><span data-stu-id="55a4b-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="55a4b-114">Doména nebo sféra</span><span class="sxs-lookup"><span data-stu-id="55a4b-114">Domain/realm</span></span>|<span data-ttu-id="55a4b-115">Jediná jednotka správy zabezpečení nebo vztahu důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="55a4b-115">A single unit of security administration or trust.</span></span> <span data-ttu-id="55a4b-116">Typická doména může zahrnovat jednu organizaci.</span><span class="sxs-lookup"><span data-stu-id="55a4b-116">A typical domain might include a single organization.</span></span>|  
|<span data-ttu-id="55a4b-117">Federace</span><span class="sxs-lookup"><span data-stu-id="55a4b-117">Federation</span></span>|<span data-ttu-id="55a4b-118">Kolekce domén, které mají zavedený vztah důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="55a4b-118">A collection of domains that have established trust.</span></span> <span data-ttu-id="55a4b-119">Úroveň důvěryhodnosti mohou lišit, ale obvykle zahrnuje ověřování a téměř vždy obsahuje autorizaci.</span><span class="sxs-lookup"><span data-stu-id="55a4b-119">The level of trust may vary, but typically includes authentication and almost always includes authorization.</span></span> <span data-ttu-id="55a4b-120">Typické federace může obsahovat několik organizací, které mají vztah důvěryhodnosti pro sdílený přístup k sadu prostředků.</span><span class="sxs-lookup"><span data-stu-id="55a4b-120">A typical federation might include a number of organizations that have established trust for shared access to a set of resources.</span></span>|  
|<span data-ttu-id="55a4b-121">Služba tokenů zabezpečení (STS)</span><span class="sxs-lookup"><span data-stu-id="55a4b-121">Security Token Service (STS)</span></span>|<span data-ttu-id="55a4b-122">Webová služba, která vydává tokeny zabezpečení. To znamená, že provádí kontrolní výrazy na základě legitimace, kterou důvěřuje, aby ji whomever důvěřuje.</span><span class="sxs-lookup"><span data-stu-id="55a4b-122">A Web service that issues security tokens; that is, it makes assertions based on evidence that it trusts, to whomever trusts it.</span></span> <span data-ttu-id="55a4b-123">Tato forma je základem vztahu důvěryhodnosti mezi doménami.</span><span class="sxs-lookup"><span data-stu-id="55a4b-123">This forms the basis of trust brokering between domains.</span></span>|  
  
### <a name="example-scenario"></a><span data-ttu-id="55a4b-124">Ukázkový scénář</span><span class="sxs-lookup"><span data-stu-id="55a4b-124">Example Scenario</span></span>  
 <span data-ttu-id="55a4b-125">Následující ilustrace znázorňuje příklad federovaného zabezpečení:</span><span class="sxs-lookup"><span data-stu-id="55a4b-125">The following illustration shows an example of federated security:</span></span>  
  
 ![Diagram znázorňující Typický scénář federovaného zabezpečení](./media/federation/typical-federated-security-scenario.gif)  
  
 <span data-ttu-id="55a4b-127">Tento scénář zahrnuje dvě organizace: A a B. organizace B má webový prostředek (webovou službu), který někteří uživatelé v organizaci vyhledali jako cenné.</span><span class="sxs-lookup"><span data-stu-id="55a4b-127">This scenario includes two organizations: A and B. Organization B has a Web resource (a Web service) that some users in organization A find valuable.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="55a4b-128">V této části se používají *prostředky*, *služby*a *webové služby* , které jsou zaměnitelné.</span><span class="sxs-lookup"><span data-stu-id="55a4b-128">This section uses the terms *resource*, *service*, and *Web service* interchangeably.</span></span>  
  
 <span data-ttu-id="55a4b-129">Organizace B obvykle vyžaduje, aby uživatel z organizace A před přístupem ke službě poskytoval určitou platnou formu ověřování.</span><span class="sxs-lookup"><span data-stu-id="55a4b-129">Typically, organization B requires that a user from organization A provide some valid form of authentication before accessing the service.</span></span> <span data-ttu-id="55a4b-130">Kromě toho může organizace také vyžadovat, aby uživatel byl autorizovaný pro přístup k příslušnému prostředku.</span><span class="sxs-lookup"><span data-stu-id="55a4b-130">In addition, the organization may also require that the user be authorized to access the specific resource in question.</span></span> <span data-ttu-id="55a4b-131">Jedním ze způsobů, jak tento problém vyřešit, a umožnit uživatelům v organizaci A přístup k prostředkům v organizaci B je následující:</span><span class="sxs-lookup"><span data-stu-id="55a4b-131">One way to address this problem and enable users in organization A to access the resource in organization B is as follows:</span></span>  
  
- <span data-ttu-id="55a4b-132">Uživatelé z organizace registrují svá pověření (uživatelské jméno a heslo) s organizací B.</span><span class="sxs-lookup"><span data-stu-id="55a4b-132">Users from organization A register their credentials (a user name and password) with organization B.</span></span>  
  
- <span data-ttu-id="55a4b-133">Během přístupu k prostředkům uživatelé z organizace A předloží své přihlašovací údaje organizaci B a ověřují se před přístupem k prostředku.</span><span class="sxs-lookup"><span data-stu-id="55a4b-133">During the resource access, users from organization A present their credentials to organization B and are authenticated before accessing the resource.</span></span>  
  
 <span data-ttu-id="55a4b-134">Tento přístup má tři významné nevýhody:</span><span class="sxs-lookup"><span data-stu-id="55a4b-134">This approach has three significant drawbacks:</span></span>  
  
- <span data-ttu-id="55a4b-135">Organizace B musí spravovat přihlašovací údaje pro uživatele z organizace A navíc ke správě přihlašovacích údajů místních uživatelů.</span><span class="sxs-lookup"><span data-stu-id="55a4b-135">Organization B has to manage the credentials for users from organization A in addition to managing the credentials of its local users.</span></span>  
  
- <span data-ttu-id="55a4b-136">Uživatelé v organizaci potřebují zachovat další sadu přihlašovacích údajů (to znamená, že si zapamatuje dodatečné uživatelské jméno a heslo) Kromě přihlašovacích údajů, které běžně používají k získání přístupu k prostředkům v organizaci A. To obvykle podporuje postup použití stejného uživatelského jména a hesla v několika lokalitách služby, což je slabé bezpečnostní opatření.</span><span class="sxs-lookup"><span data-stu-id="55a4b-136">Users in organization A need to maintain an additional set of credentials (that is, remember an additional user name and password) apart from the credentials they normally use to gain access to resources within organization A. This usually encourages the practice of using the same user name and password at multiple service sites, which is a weak security measure.</span></span>  
  
- <span data-ttu-id="55a4b-137">Architektura se neškáluje jako více organizací, které by vnímaty prostředek v organizaci B, pokud se jedná o nějakou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="55a4b-137">The architecture does not scale as more organizations perceive the resource at organization B as being of some value.</span></span>  
  
 <span data-ttu-id="55a4b-138">Alternativním přístupem, který řeší výše zmíněné nevýhody, je využívání federovaného zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="55a4b-138">An alternative approach, which addresses the previously mentioned drawbacks, is to employ federated security.</span></span> <span data-ttu-id="55a4b-139">V tomto přístupu organizace a a B navážou vztah důvěryhodnosti a využívají službu tokenů zabezpečení (STS), aby umožnila zprostředkovateli zavedeného vztahu důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="55a4b-139">In this approach, organizations A and B establish a trust relationship and employ Security Token Service (STS) to enable brokering of the established trust.</span></span>  
  
 <span data-ttu-id="55a4b-140">V rámci federované architektury zabezpečení uživatelé z organizace ví, že pokud chtějí přistupovat k webové službě v organizaci B, že musí předložit platný token zabezpečení ze služby STS v organizaci B, která ověřuje a autorizuje svůj přístup k konkrétní služba.</span><span class="sxs-lookup"><span data-stu-id="55a4b-140">In a federated security architecture, users from organization A know that if they want to access the Web service in organization B that they must present a valid security token from the STS at organization B, which authenticates and authorizes their access to the specific service.</span></span>  
  
 <span data-ttu-id="55a4b-141">Při kontaktování služby tokenů zabezpečení (STS B) získají uživatelé další úroveň nepřímých odkazů ze zásad přidružených ke službě STS.</span><span class="sxs-lookup"><span data-stu-id="55a4b-141">On contacting the STS B, the users receive another level of indirection from the policy associated with the STS.</span></span> <span data-ttu-id="55a4b-142">Před tím, než služba STS B může vydávat token zabezpečení, musí mít platný token zabezpečení ze služby STS A (tj. sféra vztahu důvěryhodnosti klienta).</span><span class="sxs-lookup"><span data-stu-id="55a4b-142">They must present a valid security token from the STS A (that is, the client trust realm) before the STS B can issue them a security token.</span></span> <span data-ttu-id="55a4b-143">Jedná se o Corollary vztah důvěryhodnosti mezi dvěma organizacemi a naznačuje, že organizace B nemusí spravovat identity pro uživatele z organizace A. V praxi má STS B obvykle hodnotu null `issuerAddress` a. `issuerMetadataAddress`</span><span class="sxs-lookup"><span data-stu-id="55a4b-143">This is a corollary of the trust relationship established between the two organizations and implies that organization B does not have to manage identities for users from organization A. In practice, STS B typically has a null `issuerAddress` and `issuerMetadataAddress`.</span></span> <span data-ttu-id="55a4b-144">Další informace najdete v tématu [jak: Konfigurace místního vystavitele](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).</span><span class="sxs-lookup"><span data-stu-id="55a4b-144">For more information, see [How to: Configure a Local Issuer](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span> <span data-ttu-id="55a4b-145">V takovém případě klient prohledává službu STS A pomocí místních zásad. Tato konfigurace se nazývá *federace domovské sféry* a je lepší škálovat, protože služba STS B nemusí spravovat informace o STS A.</span><span class="sxs-lookup"><span data-stu-id="55a4b-145">In that case, the client consults a local policy to locate STS A. This configuration is called *home realm federation* and it scales better because STS B does not have to maintain information about STS A.</span></span>  
  
 <span data-ttu-id="55a4b-146">Uživatelé pak budou kontaktovat službu STS v organizaci a a získat token zabezpečení tím, že prezentují ověřovací přihlašovací údaje, které běžně používají k získání přístupu k jakémukoli jinému prostředku v organizaci A. Tím se také řeší problém uživatelů, kteří si mají zachovat více sad přihlašovacích údajů nebo používají stejnou sadu přihlašovacích údajů na více lokalitách služby.</span><span class="sxs-lookup"><span data-stu-id="55a4b-146">The users then contact the STS at organization A and obtain a security token by presenting authentication credentials that they normally use to gain access to any other resource within organization A. This also alleviates the problem of users having to maintain multiple sets of credentials or using the same set of credentials at multiple service sites.</span></span>  
  
 <span data-ttu-id="55a4b-147">Jakmile uživatelé získají token zabezpečení ze služby STS A, prezentují token službě STS B. organizace B pokračuje v provádění autorizace požadavků uživatelů a vydá token zabezpečení uživatelům z vlastní sady tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="55a4b-147">Once the users obtain a security token from the STS A, they present the token to the STS B. Organization B proceeds to perform authorization of the users' requests and issues a security token to the users from its own set of security tokens.</span></span> <span data-ttu-id="55a4b-148">Uživatelé pak mohou svůj token prezentovat k prostředkům v organizaci B a přistupovat ke službě.</span><span class="sxs-lookup"><span data-stu-id="55a4b-148">The users can then present their token to the resource at organization B and access the service.</span></span>  
  
## <a name="support-for-federated-security-in-wcf"></a><span data-ttu-id="55a4b-149">Podpora federovaného zabezpečení ve službě WCF</span><span class="sxs-lookup"><span data-stu-id="55a4b-149">Support for Federated Security in WCF</span></span>  
 <span data-ttu-id="55a4b-150">WCF poskytuje podporu klíč pro nasazení federovaných architektur zabezpečení prostřednictvím [ \<> WSFederationHttpBinding](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="55a4b-150">WCF provides turnkey support for deploying federated security architectures through the [\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span></span>  
  
 <span data-ttu-id="55a4b-151">Element [WSFederationHttpBinding > poskytuje zabezpečenou, spolehlivou a interoperabilní vazbu, která zahrnuje použití http jako základního přenosového mechanismu pro styl komunikace požadavek-odpověď, který používá text a XML jako \<](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) Formát drátěného formátu pro kódování.</span><span class="sxs-lookup"><span data-stu-id="55a4b-151">The [\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) element provides for a secure, reliable, interoperable binding that entails the use of HTTP as the underlying transport mechanism for request-reply communication style, employing text and XML as the wire format for encoding.</span></span>  
  
 <span data-ttu-id="55a4b-152">[ Použití\<> WSFederationHttpBinding](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) ve federovaném scénáři zabezpečení lze oddělit do dvou logicky nezávislých fází, jak je popsáno v následujících částech.</span><span class="sxs-lookup"><span data-stu-id="55a4b-152">The use of [\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) in a federated security scenario can be decoupled into two logically independent phases, as described in the following sections.</span></span>  
  
### <a name="phase-1-design-phase"></a><span data-ttu-id="55a4b-153">Fáze 1: Fáze návrhu</span><span class="sxs-lookup"><span data-stu-id="55a4b-153">Phase 1: Design Phase</span></span>  
 <span data-ttu-id="55a4b-154">Ve fázi návrhu používá klient Nástroj pro dokládání [metadat (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) k přečtení zásad, které zpřístupňuje koncový bod služby, a ke shromažďování požadavků na ověřování a autorizaci služby.</span><span class="sxs-lookup"><span data-stu-id="55a4b-154">During the design phase, the client uses the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to read the policy the service endpoint exposes and to collect the service's authentication and authorization requirements.</span></span> <span data-ttu-id="55a4b-155">Příslušné proxy servery jsou vytvořeny tak, aby na klientovi vytvořily následující vzor federovaného zabezpečení:</span><span class="sxs-lookup"><span data-stu-id="55a4b-155">The appropriate proxies are constructed to create the following federated security communication pattern at the client:</span></span>  
  
- <span data-ttu-id="55a4b-156">Získejte token zabezpečení ze služby STS ve sféře vztahu důvěryhodnosti klienta.</span><span class="sxs-lookup"><span data-stu-id="55a4b-156">Obtain a security token from the STS in the client trust realm.</span></span>  
  
- <span data-ttu-id="55a4b-157">Prezentovat token ke službě STS ve sféře vztahu důvěryhodnosti služby.</span><span class="sxs-lookup"><span data-stu-id="55a4b-157">Present the token to the STS in the service trust realm.</span></span>  
  
- <span data-ttu-id="55a4b-158">Získejte token zabezpečení ze služby STS ve sféře vztahu důvěryhodnosti služby.</span><span class="sxs-lookup"><span data-stu-id="55a4b-158">Obtain a security token from the STS in the service trust realm.</span></span>  
  
- <span data-ttu-id="55a4b-159">Prezentovat token službě pro přístup ke službě.</span><span class="sxs-lookup"><span data-stu-id="55a4b-159">Present the token to the service to access the service.</span></span>  
  
### <a name="phase-2-run-time-phase"></a><span data-ttu-id="55a4b-160">Fáze 2: Fáze run-time</span><span class="sxs-lookup"><span data-stu-id="55a4b-160">Phase 2: Run-Time Phase</span></span>  
 <span data-ttu-id="55a4b-161">Během fáze běhu klient vytvoří instanci objektu třídy klienta WCF a provede volání pomocí klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="55a4b-161">During the run-time phase, the client instantiates an object of the WCF client class and makes a call using the WCF client.</span></span> <span data-ttu-id="55a4b-162">Základní architektura služby WCF zpracovává dříve zmíněné kroky v rámci modelu federované zabezpečení komunikace a umožňuje klientovi bezproblémové využívání služby.</span><span class="sxs-lookup"><span data-stu-id="55a4b-162">The underlying framework of WCF handles the previously mentioned steps in the federated security communication pattern and enables the client to seamlessly consume the service.</span></span>  
  
## <a name="sample-implementation-using-wcf"></a><span data-ttu-id="55a4b-163">Ukázková implementace pomocí WCF</span><span class="sxs-lookup"><span data-stu-id="55a4b-163">Sample Implementation Using WCF</span></span>  
 <span data-ttu-id="55a4b-164">Následující ilustrace znázorňuje ukázkovou implementaci pro federované architektury zabezpečení pomocí nativní podpory služby WCF.</span><span class="sxs-lookup"><span data-stu-id="55a4b-164">The following illustration shows a sample implementation for a federated security architecture using native support from WCF.</span></span>  
  
 ![Diagram znázorňující ukázkovou implementaci zabezpečení federace](./media/federation/federated-security-implementation.gif)  
  
### <a name="example-myservice"></a><span data-ttu-id="55a4b-166">Příklad Mojesluzba</span><span class="sxs-lookup"><span data-stu-id="55a4b-166">Example MyService</span></span>  
 <span data-ttu-id="55a4b-167">Služba `MyService` zpřístupňuje jeden koncový bod prostřednictvím `MyServiceEndpoint`.</span><span class="sxs-lookup"><span data-stu-id="55a4b-167">The service `MyService` exposes a single endpoint through `MyServiceEndpoint`.</span></span> <span data-ttu-id="55a4b-168">Na následujícím obrázku je znázorněna adresa, vazba a kontrakt spojený s koncovým bodem.</span><span class="sxs-lookup"><span data-stu-id="55a4b-168">The following illustration shows the address, binding, and contract associated with the endpoint.</span></span>  
  
 ![Diagram znázorňující MyServiceEndpoint podrobnosti.](./media/federation/myserviceendpoint-details.gif)  
  
 <span data-ttu-id="55a4b-170">Koncový bod `MyServiceEndpoint` služby `accessAuthorized` [ \<používá > WSFederationHttpBinding](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) a vyžaduje platný token SAML (Security Assert Markup Language) s deklarací, kterou vystavila služba STS B. Tato deklarace je deklarativně specifikovaná v konfiguraci služby.</span><span class="sxs-lookup"><span data-stu-id="55a4b-170">The service endpoint `MyServiceEndpoint` uses the [\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) and requires a valid Security Assertions Markup Language (SAML) token with an `accessAuthorized` claim issued by STS B. This is declaratively specified in the service configuration.</span></span>  
  
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
> <span data-ttu-id="55a4b-171">Je třeba si poznamenat jemný bod o deklaracích vyžadovaných nástrojem `MyService`.</span><span class="sxs-lookup"><span data-stu-id="55a4b-171">A subtle point should be noted about the claims required by `MyService`.</span></span> <span data-ttu-id="55a4b-172">Druhý obrázek ukazuje, že `MyService` vyžaduje token SAML `accessAuthorized` s deklarací identity.</span><span class="sxs-lookup"><span data-stu-id="55a4b-172">The second figure indicates that `MyService` requires a SAML token with the `accessAuthorized` claim.</span></span> <span data-ttu-id="55a4b-173">Aby bylo přesnější, určuje typ deklarace identity, který `MyService` vyžaduje.</span><span class="sxs-lookup"><span data-stu-id="55a4b-173">To be more precise, this specifies the claim type that `MyService` requires.</span></span> <span data-ttu-id="55a4b-174">Plně kvalifikovaný název tohoto typu deklarace identity je `http://tempuri.org:accessAuthorized` (spolu s přidruženým oborem názvů), který se používá v konfiguračním souboru služby.</span><span class="sxs-lookup"><span data-stu-id="55a4b-174">The fully-qualified name of this claim type is `http://tempuri.org:accessAuthorized` (along with the associated namespace), which is used in the service configuration file.</span></span> <span data-ttu-id="55a4b-175">Hodnota této deklarace identity označuje přítomnost této deklarace identity a předpokládá se, že je nastavena na `true` službu STS B.</span><span class="sxs-lookup"><span data-stu-id="55a4b-175">The value of this claim indicates the presence of this claim and is assumed to be set to `true` by STS B.</span></span>  
  
 <span data-ttu-id="55a4b-176">Za běhu se tato zásada vynutila `MyServiceOperationRequirement` třídou, která je implementovaná jako součást. `MyService`</span><span class="sxs-lookup"><span data-stu-id="55a4b-176">At runtime, this policy is enforced by the `MyServiceOperationRequirement` class that is implemented as part of the `MyService`.</span></span>  
  
 [!code-csharp[C_Federation#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#0)]
 [!code-vb[C_Federation#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#0)]  
[!code-csharp[C_Federation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#1)]
[!code-vb[C_Federation#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#1)]  
  
#### <a name="sts-b"></a><span data-ttu-id="55a4b-177">STS B</span><span class="sxs-lookup"><span data-stu-id="55a4b-177">STS B</span></span>  
 <span data-ttu-id="55a4b-178">Na následujícím obrázku je znázorněná služba tokenů zabezpečení (STS) B. Jak je uvedeno výše, služba tokenů zabezpečení (STS) je také webová služba a může mít přidružené koncové body, zásady a tak dále.</span><span class="sxs-lookup"><span data-stu-id="55a4b-178">The following illustration shows the STS B. As stated earlier, a security token service (STS) is also a Web service and can have its associated endpoints, policy, and so on.</span></span>  
  
 ![Diagram znázorňující službu tokenu zabezpečení B.](./media/federation/myservice-security-token-service-b.gif)  
  
 <span data-ttu-id="55a4b-180">Služba STS B zpřístupňuje jeden koncový bod `STSEndpoint` , který je možné použít k vyžádání tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="55a4b-180">STS B exposes a single endpoint, called `STSEndpoint` that can be use to request security tokens.</span></span> <span data-ttu-id="55a4b-181">Konkrétně `MyService` služba tokenů zabezpečení (STS B) `accessAuthorized` vystavuje tokeny SAML s deklarací identity, které mohou být uvedeny na webu služby pro přístup k této službě.</span><span class="sxs-lookup"><span data-stu-id="55a4b-181">Specifically, STS B issues SAML tokens with the `accessAuthorized` claim, which can be presented at the `MyService` service site for accessing the service.</span></span> <span data-ttu-id="55a4b-182">Služba STS B ale vyžaduje, aby uživatelé prezentují platný token SAML vydaný službou STS a, `userAuthenticated` který obsahuje deklaraci identity.</span><span class="sxs-lookup"><span data-stu-id="55a4b-182">However, STS B requires users to present a valid SAML token issued by STS A that contains the `userAuthenticated` claim.</span></span> <span data-ttu-id="55a4b-183">Tato deklarace je deklarativně specifikovaná v konfiguraci služby STS.</span><span class="sxs-lookup"><span data-stu-id="55a4b-183">This is declaratively specified in the STS configuration.</span></span>  
  
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
> <span data-ttu-id="55a4b-184">`userAuthenticated` Deklarace identity je znovu typu deklarace identity, který vyžaduje služba tokenů zabezpečení (STS) B. Plně kvalifikovaný název tohoto typu deklarace identity je `http://tempuri.org:userAuthenticated` (spolu s přidruženým oborem názvů), který se používá v konfiguračním souboru STS.</span><span class="sxs-lookup"><span data-stu-id="55a4b-184">Again, the `userAuthenticated` claim is the claim type that is required by STS B. The fully-qualified name of this claim type is `http://tempuri.org:userAuthenticated` (along with the associated namespace), which is used in the STS configuration file.</span></span> <span data-ttu-id="55a4b-185">Hodnota této deklarace identity označuje přítomnost této deklarace identity a předpokládá se, že ji nastaví `true` služba STS a.</span><span class="sxs-lookup"><span data-stu-id="55a4b-185">The value of this claim indicates the presence of this claim and is assumed to be set to `true` by STS A.</span></span>  
  
 <span data-ttu-id="55a4b-186">V době běhu `STS_B_OperationRequirement` třída vynutila tuto zásadu, která je implementována jako součást služby tokenů zabezpečení (STS) B.</span><span class="sxs-lookup"><span data-stu-id="55a4b-186">At runtime, the `STS_B_OperationRequirement` class enforces this policy, which is implemented as part of STS B.</span></span>  
  
 [!code-csharp[C_Federation#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#2)]
 [!code-vb[C_Federation#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#2)]  
  
 <span data-ttu-id="55a4b-187">Pokud je kontroler přístupu jasný, služba tokenů zabezpečení (STS B) `accessAuthorized` vydá token SAML s deklarací identity.</span><span class="sxs-lookup"><span data-stu-id="55a4b-187">If the access check is clear, STS B issues a SAML token with the `accessAuthorized` claim.</span></span>  
  
 [!code-csharp[C_Federation#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#3)]
 [!code-vb[C_Federation#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#3)]  
  
#### <a name="sts-a"></a><span data-ttu-id="55a4b-188">STS A</span><span class="sxs-lookup"><span data-stu-id="55a4b-188">STS A</span></span>  
 <span data-ttu-id="55a4b-189">Na následujícím obrázku je znázorněna služba STS A.</span><span class="sxs-lookup"><span data-stu-id="55a4b-189">The following illustration shows the STS A.</span></span>  
  
 <span data-ttu-id="55a4b-190">![Federace](../../../../docs/framework/wcf/feature-details/media/sts-b.gif "STS_B")</span><span class="sxs-lookup"><span data-stu-id="55a4b-190">![Federation](../../../../docs/framework/wcf/feature-details/media/sts-b.gif "STS_B")</span></span>  
  
 <span data-ttu-id="55a4b-191">Podobně jako služba STS B, STS A je také webová služba, která vydává tokeny zabezpečení a zpřístupňuje jeden koncový bod pro tento účel.</span><span class="sxs-lookup"><span data-stu-id="55a4b-191">Similar to the STS B, the STS A is also a Web service that issues security tokens and exposes a single endpoint for this purpose.</span></span> <span data-ttu-id="55a4b-192">Používá ale jinou vazbu (`wsHttpBinding`) a vyžaduje, aby uživatelé mohli prezentovat platnou službu CardSpace `emailAddress` s deklarací identity.</span><span class="sxs-lookup"><span data-stu-id="55a4b-192">However, it uses a different binding (`wsHttpBinding`) and requires users to present a valid CardSpace with an `emailAddress` claim.</span></span> <span data-ttu-id="55a4b-193">V reakci vydá tokeny SAML s `userAuthenticated` deklarací identity.</span><span class="sxs-lookup"><span data-stu-id="55a4b-193">In response, it issues SAML tokens with the `userAuthenticated` claim.</span></span> <span data-ttu-id="55a4b-194">Tato deklarace je deklarativně specifikovaná v konfiguraci služby.</span><span class="sxs-lookup"><span data-stu-id="55a4b-194">This is declaratively specified in the service configuration.</span></span>  
  
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
  
 <span data-ttu-id="55a4b-195">V době běhu `STS_A_OperationRequirement` třída vynutila tuto zásadu, která je implementována jako součást služby STS a.</span><span class="sxs-lookup"><span data-stu-id="55a4b-195">At runtime, the `STS_A_OperationRequirement` class enforces this policy, which is implemented as part of STS A.</span></span>  
  
 [!code-csharp[C_Federation#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#4)]
 [!code-vb[C_Federation#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#4)]  
  
 <span data-ttu-id="55a4b-196">Pokud je `true`přístup, STS a vydá token SAML s `userAuthenticated` deklarací identity.</span><span class="sxs-lookup"><span data-stu-id="55a4b-196">If the access is `true`, STS A issues a SAML token with `userAuthenticated` claim.</span></span>  
  
 [!code-csharp[C_Federation#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#5)]
 [!code-vb[C_Federation#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#5)]  
  
### <a name="client-at-organization-a"></a><span data-ttu-id="55a4b-197">Klient v organizaci A</span><span class="sxs-lookup"><span data-stu-id="55a4b-197">Client at Organization A</span></span>  
 <span data-ttu-id="55a4b-198">Následující ilustrace znázorňuje klienta v organizaci a spolu s postupem, který je součástí provádění `MyService` volání služby.</span><span class="sxs-lookup"><span data-stu-id="55a4b-198">The following illustration shows the client at organization A, along with the steps involved in making a `MyService` service call.</span></span> <span data-ttu-id="55a4b-199">Další funkční komponenty jsou také zahrnuty pro úplnost.</span><span class="sxs-lookup"><span data-stu-id="55a4b-199">The other functional components are also included for completeness.</span></span>  
  
 ![Diagram znázorňující kroky ve volání služby Mojesluzba](./media/federation/federation-myservice-service-call-process.gif)  
  
## <a name="summary"></a><span data-ttu-id="55a4b-201">Souhrn</span><span class="sxs-lookup"><span data-stu-id="55a4b-201">Summary</span></span>  
 <span data-ttu-id="55a4b-202">Federované zabezpečení poskytuje čistou divizi zodpovědnosti a pomáhá sestavovat zabezpečené a škálovatelné architektury služeb.</span><span class="sxs-lookup"><span data-stu-id="55a4b-202">Federated security provides a clean division of responsibility and helps to build secure, scalable service architectures.</span></span> <span data-ttu-id="55a4b-203">Jako platforma pro sestavování a nasazování distribuovaných aplikací poskytuje WCF nativní podporu pro implementaci federovaného zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="55a4b-203">As a platform for building and deploying distributed applications, WCF provides native support for implementing federated security.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55a4b-204">Viz také:</span><span class="sxs-lookup"><span data-stu-id="55a4b-204">See also</span></span>

- [<span data-ttu-id="55a4b-205">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="55a4b-205">Security</span></span>](../../../../docs/framework/wcf/feature-details/security.md)
