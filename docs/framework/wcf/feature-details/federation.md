---
title: Federace
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation [WCF]
ms.assetid: 2f1e646f-8361-48d4-9d5d-1b961f31ede4
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3c87fa08a698350d601f72d5d19ef353bd4257a9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="federation"></a><span data-ttu-id="e57df-102">Federace</span><span class="sxs-lookup"><span data-stu-id="e57df-102">Federation</span></span>
<span data-ttu-id="e57df-103">Toto téma obsahuje stručný přehled koncept federované zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="e57df-103">This topic provides a brief overview of the concept of federated security.</span></span> <span data-ttu-id="e57df-104">Také popisuje [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] podporu pro nasazení architektury federované zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="e57df-104">It also describes [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] support for deploying federated security architectures.</span></span> <span data-ttu-id="e57df-105">Ukázkovou aplikaci, která demonstruje federace, najdete v části [ukázka federace](../../../../docs/framework/wcf/samples/federation-sample.md).</span><span class="sxs-lookup"><span data-stu-id="e57df-105">For a sample application that demonstrates federation, see [Federation Sample](../../../../docs/framework/wcf/samples/federation-sample.md).</span></span>  
  
## <a name="definition-of-federated-security"></a><span data-ttu-id="e57df-106">Definice federované zabezpečení</span><span class="sxs-lookup"><span data-stu-id="e57df-106">Definition of Federated Security</span></span>  
 <span data-ttu-id="e57df-107">Federované zabezpečení umožňuje čistou oddělení mezi službu, kterou klient přistupuje a přidružené postupů ověřování a autorizace.</span><span class="sxs-lookup"><span data-stu-id="e57df-107">Federated security allows for clean separation between the service a client is accessing and the associated authentication and authorization procedures.</span></span> <span data-ttu-id="e57df-108">Federované zabezpečení taky umožňuje spolupráci mezi více systémy, sítě a organizace v různých důvěryhodnosti sfér.</span><span class="sxs-lookup"><span data-stu-id="e57df-108">Federated security also enables collaboration across multiple systems, networks, and organizations in different trust realms.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="e57df-109">poskytuje podporu pro vytváření a nasazování distribuovaných systémů, které využívají federované zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="e57df-109"> provides support for building and deploying distributed systems that employ federated security.</span></span>  
  
### <a name="elements-of-a-federated-security-architecture"></a><span data-ttu-id="e57df-110">Prvky architektury federované zabezpečení</span><span class="sxs-lookup"><span data-stu-id="e57df-110">Elements of a Federated Security Architecture</span></span>  
 <span data-ttu-id="e57df-111">Architektura federované zabezpečení má tři klíčové prvky, jak je popsáno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="e57df-111">The federated security architecture has three key elements, as described in the following table.</span></span>  
  
|<span data-ttu-id="e57df-112">Prvek</span><span class="sxs-lookup"><span data-stu-id="e57df-112">Element</span></span>|<span data-ttu-id="e57df-113">Popis</span><span class="sxs-lookup"><span data-stu-id="e57df-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e57df-114">Domény nebo sféry</span><span class="sxs-lookup"><span data-stu-id="e57df-114">Domain/realm</span></span>|<span data-ttu-id="e57df-115">Na jednu jednotku správu zabezpečení nebo vztah důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="e57df-115">A single unit of security administration or trust.</span></span> <span data-ttu-id="e57df-116">Typické domény mohou zahrnovat jedné organizace.</span><span class="sxs-lookup"><span data-stu-id="e57df-116">A typical domain might include a single organization.</span></span>|  
|<span data-ttu-id="e57df-117">Federace</span><span class="sxs-lookup"><span data-stu-id="e57df-117">Federation</span></span>|<span data-ttu-id="e57df-118">Kolekce domén, které mají vztah důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="e57df-118">A collection of domains that have established trust.</span></span> <span data-ttu-id="e57df-119">Úroveň důvěryhodnosti může lišit, ale obvykle zahrnuje ověřování a téměř vždy obsahuje autorizace.</span><span class="sxs-lookup"><span data-stu-id="e57df-119">The level of trust may vary, but typically includes authentication and almost always includes authorization.</span></span> <span data-ttu-id="e57df-120">Typické federace může obsahovat několik organizací, které mají vztah důvěryhodnosti pro sdílený přístup k sadu prostředků.</span><span class="sxs-lookup"><span data-stu-id="e57df-120">A typical federation might include a number of organizations that have established trust for shared access to a set of resources.</span></span>|  
|<span data-ttu-id="e57df-121">Služba tokenů zabezpečení (STS)</span><span class="sxs-lookup"><span data-stu-id="e57df-121">Security Token Service (STS)</span></span>|<span data-ttu-id="e57df-122">Webová služba, která vydává tokeny zabezpečení; To znamená provede kontrolních výrazů založené na důkaz, která důvěřuje na všechny uživatele, kteří důvěřuje.</span><span class="sxs-lookup"><span data-stu-id="e57df-122">A Web service that issues security tokens; that is, it makes assertions based on evidence that it trusts, to whomever trusts it.</span></span> <span data-ttu-id="e57df-123">Tento balíček je základem zprostředkování vztahu důvěryhodnosti mezi doménami.</span><span class="sxs-lookup"><span data-stu-id="e57df-123">This forms the basis of trust brokering between domains.</span></span>|  
  
### <a name="example-scenario"></a><span data-ttu-id="e57df-124">Příklad scénáře</span><span class="sxs-lookup"><span data-stu-id="e57df-124">Example Scenario</span></span>  
 <span data-ttu-id="e57df-125">Následující obrázek znázorňuje příklad federované zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="e57df-125">The following illustration shows an example of federated security.</span></span>  
  
 <span data-ttu-id="e57df-126">![Federační](../../../../docs/framework/wcf/feature-details/media/typicalfederatedsecurityscenario.gif "TypicalFederatedSecurityScenario")</span><span class="sxs-lookup"><span data-stu-id="e57df-126">![Federation](../../../../docs/framework/wcf/feature-details/media/typicalfederatedsecurityscenario.gif "TypicalFederatedSecurityScenario")</span></span>  
  
 <span data-ttu-id="e57df-127">Tento scénář zahrnuje dvě organizace: A a B. organizace B má někteří uživatelé v organizaci A najít cenné webové prostředky (webová služba).</span><span class="sxs-lookup"><span data-stu-id="e57df-127">This scenario includes two organizations: A and B. Organization B has a Web resource (a Web service) that some users in organization A find valuable.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e57df-128">Tato část používá podmínky *prostředků*, *služby*, a *webovou službu* zcela zaměnitelným významem.</span><span class="sxs-lookup"><span data-stu-id="e57df-128">This section uses the terms *resource*, *service*, and *Web service* interchangeably.</span></span>  
  
 <span data-ttu-id="e57df-129">Organizace B, obvykle vyžaduje, aby uživatel z organizace A zadali některé platné formu ověřování před přístupem ke službě.</span><span class="sxs-lookup"><span data-stu-id="e57df-129">Typically, organization B requires that a user from organization A provide some valid form of authentication before accessing the service.</span></span> <span data-ttu-id="e57df-130">Kromě toho organizace může také vyžadovat, uživatel povolen přístup k určitému konkrétní prostředku.</span><span class="sxs-lookup"><span data-stu-id="e57df-130">In addition, the organization may also require that the user be authorized to access the specific resource in question.</span></span> <span data-ttu-id="e57df-131">Jeden způsob, jak vyřešit tento problém a povolit uživatelům v organizaci A pro přístup k prostředku v organizaci B je následující:</span><span class="sxs-lookup"><span data-stu-id="e57df-131">One way to address this problem and enable users in organization A to access the resource in organization B is as follows:</span></span>  
  
-   <span data-ttu-id="e57df-132">Uživatelé z organizace A zaregistrovat svoje přihlašovací údaje (uživatelské jméno a heslo) s organizace B.</span><span class="sxs-lookup"><span data-stu-id="e57df-132">Users from organization A register their credentials (a user name and password) with organization B.</span></span>  
  
-   <span data-ttu-id="e57df-133">Během přístupu k prostředkům uživatelům v organizaci A k dispozici přihlašovacích údajů pro organizaci B a ověření před přístupem k prostředku.</span><span class="sxs-lookup"><span data-stu-id="e57df-133">During the resource access, users from organization A present their credentials to organization B and are authenticated before accessing the resource.</span></span>  
  
 <span data-ttu-id="e57df-134">Tento přístup má tři významné nevýhody:</span><span class="sxs-lookup"><span data-stu-id="e57df-134">This approach has three significant drawbacks:</span></span>  
  
-   <span data-ttu-id="e57df-135">Organizace B má ke správě pověření pro uživatele z organizace A kromě správy pověření své místní uživatelé.</span><span class="sxs-lookup"><span data-stu-id="e57df-135">Organization B has to manage the credentials for users from organization A in addition to managing the credentials of its local users.</span></span>  
  
-   <span data-ttu-id="e57df-136">Třeba uživatelům v organizaci A spravovat další sadu pověření (to znamená, nezapomeňte další uživatelské jméno a heslo) kromě přihlašovací údaje, obvykle používají pro přístup k prostředkům v rámci organizace A. To obvykle doporučuje postup pomocí stejné uživatelské jméno a heslo ve více lokalitách služby, což je slabé bezpečnostní opatření.</span><span class="sxs-lookup"><span data-stu-id="e57df-136">Users in organization A need to maintain an additional set of credentials (that is, remember an additional user name and password) apart from the credentials they normally use to gain access to resources within organization A. This usually encourages the practice of using the same user name and password at multiple service sites, which is a weak security measure.</span></span>  
  
-   <span data-ttu-id="e57df-137">Architektura se nedá použít jako další organizace vnímat prostředků v organizaci B, že některé hodnoty.</span><span class="sxs-lookup"><span data-stu-id="e57df-137">The architecture does not scale as more organizations perceive the resource at organization B as being of some value.</span></span>  
  
 <span data-ttu-id="e57df-138">Alternativní způsob, který řeší výše uvedených nevýhody, je použít federované zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="e57df-138">An alternative approach, which addresses the previously mentioned drawbacks, is to employ federated security.</span></span> <span data-ttu-id="e57df-139">V tomto přístupu organizace A a B navázání vztahu důvěryhodnosti a využít zabezpečení tokenu služby (STS) Chcete-li povolit zprostředkování zavedených vztahu důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="e57df-139">In this approach, organizations A and B establish a trust relationship and employ Security Token Service (STS) to enable brokering of the established trust.</span></span>  
  
 <span data-ttu-id="e57df-140">V architektuře federované zabezpečení uživatele organizaci A vědět, že pokud chtějí přístup k webové službě v organizaci B, který se musí představovat platný zabezpečení token zabezpečení ze služby tokenů zabezpečení v organizaci B, který provádí ověřování a autorizaci svůj přístup k konkrétní službu.</span><span class="sxs-lookup"><span data-stu-id="e57df-140">In a federated security architecture, users from organization A know that if they want to access the Web service in organization B that they must present a valid security token from the STS at organization B, which authenticates and authorizes their access to the specific service.</span></span>  
  
 <span data-ttu-id="e57df-141">Na kontaktování služby tokenů zabezpečení B, uživatelé přijímat jinou úroveň dereference z zásady přidružené Služba tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="e57df-141">On contacting the STS B, the users receive another level of indirection from the policy associated with the STS.</span></span> <span data-ttu-id="e57df-142">Se musí představovat platný zabezpečení od služby tokenů zabezpečení A (tedy sféry klienta vztahu důvěryhodnosti) token před B služby tokenů zabezpečení můžete vydat, je token zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="e57df-142">They must present a valid security token from the STS A (that is, the client trust realm) before the STS B can issue them a security token.</span></span> <span data-ttu-id="e57df-143">Toto je důsledkem této vztah důvěryhodnosti mezi dvěma organizacemi a znamená, že organizace B nemá spravovat identity pro uživatele z organizace A. V praxi, STS B, obvykle má hodnotu null `issuerAddress` a `issuerMetadataAddress`.</span><span class="sxs-lookup"><span data-stu-id="e57df-143">This is a corollary of the trust relationship established between the two organizations and implies that organization B does not have to manage identities for users from organization A. In practice, STS B typically has a null `issuerAddress` and `issuerMetadataAddress`.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="e57df-144">[Postupy: Konfigurace místního vystavitele](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).</span><span class="sxs-lookup"><span data-stu-id="e57df-144"> [How to: Configure a Local Issuer](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span> <span data-ttu-id="e57df-145">V takovém případě klienta zajímají místní zásady najít službu tokenů zabezpečení A. Tato konfigurace se nazývá *domácí sféry federace* a škáluje líp, protože není nutné udržovat informace o STS A. B služby tokenů zabezpečení</span><span class="sxs-lookup"><span data-stu-id="e57df-145">In that case, the client consults a local policy to locate STS A. This configuration is called *home realm federation* and it scales better because STS B does not have to maintain information about STS A.</span></span>  
  
 <span data-ttu-id="e57df-146">Uživatelé pak, obraťte se na službu tokenů zabezpečení v organizaci A a získat token zabezpečení prezentací ověřování přihlašovacích údajů, které standardně používáte k získání přístupu k jakémukoli prostředku, v rámci organizace A. To také řeší problém uživatelů bude potřeba udržovat několik sad přihlašovacích údajů, nebo pomocí stejné sady přihlašovacích údajů ve více lokalitách služby.</span><span class="sxs-lookup"><span data-stu-id="e57df-146">The users then contact the STS at organization A and obtain a security token by presenting authentication credentials that they normally use to gain access to any other resource within organization A. This also alleviates the problem of users having to maintain multiple sets of credentials or using the same set of credentials at multiple service sites.</span></span>  
  
 <span data-ttu-id="e57df-147">Jakmile se uživatelé získat token zabezpečení od služby tokenů zabezpečení A, se nachází token, který má služba tokenů zabezpečení B. organizace B pokračuje k autorizaci požadavků uživatelů a vydá token zabezpečení pro uživatele z vlastní sadu tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="e57df-147">Once the users obtain a security token from the STS A, they present the token to the STS B. Organization B proceeds to perform authorization of the users' requests and issues a security token to the users from its own set of security tokens.</span></span> <span data-ttu-id="e57df-148">Uživatele můžete prezentovat token k prostředku v organizaci B a přístup ke službě.</span><span class="sxs-lookup"><span data-stu-id="e57df-148">The users can then present their token to the resource at organization B and access the service.</span></span>  
  
## <a name="support-for-federated-security-in-wcf"></a><span data-ttu-id="e57df-149">Podpora pro federované zabezpečení ve WCF</span><span class="sxs-lookup"><span data-stu-id="e57df-149">Support for Federated Security in WCF</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="e57df-150">To podporuje pro nasazení architektury federované zabezpečení prostřednictvím [ \<– wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="e57df-150"> provides turnkey support for deploying federated security architectures through the [\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span></span>  
  
 <span data-ttu-id="e57df-151">[ \<– WsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) element poskytuje bezpečné, spolehlivé a umožňuje vzájemnou spolupráci vazby, která se používá jako podkladový přenosový mechanismus pro komunikaci styl požadavku a odpovědi HTTP nasazení jako přenosový formát pro kódování textu a XML.</span><span class="sxs-lookup"><span data-stu-id="e57df-151">The [\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) element provides for a secure, reliable, interoperable binding that entails the use of HTTP as the underlying transport mechanism for request-reply communication style, employing text and XML as the wire format for encoding.</span></span>  
  
 <span data-ttu-id="e57df-152">Použití [ \<– wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) v federované zabezpečení scénáři může být odděleno do dvou fází logicky nezávislý, jak je popsáno v následujících částech.</span><span class="sxs-lookup"><span data-stu-id="e57df-152">The use of [\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) in a federated security scenario can be decoupled into two logically independent phases, as described in the following sections.</span></span>  
  
### <a name="phase-1-design-phase"></a><span data-ttu-id="e57df-153">Fáze 1: Fáze návrhu</span><span class="sxs-lookup"><span data-stu-id="e57df-153">Phase 1: Design Phase</span></span>  
 <span data-ttu-id="e57df-154">Během fáze návrhu, klient použije [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ke čtení zásad zpřístupní koncový bod služby a shromažďovat služby ověřování a autorizaci požadavků.</span><span class="sxs-lookup"><span data-stu-id="e57df-154">During the design phase, the client uses the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to read the policy the service endpoint exposes and to collect the service's authentication and authorization requirements.</span></span> <span data-ttu-id="e57df-155">Odpovídající proxy sestavení tak, aby vytvořit následující vzor federované zabezpečení komunikace na straně klienta:</span><span class="sxs-lookup"><span data-stu-id="e57df-155">The appropriate proxies are constructed to create the following federated security communication pattern at the client:</span></span>  
  
-   <span data-ttu-id="e57df-156">Získejte token zabezpečení od služby tokenů zabezpečení ve sféře, důvěryhodnosti klienta.</span><span class="sxs-lookup"><span data-stu-id="e57df-156">Obtain a security token from the STS in the client trust realm.</span></span>  
  
-   <span data-ttu-id="e57df-157">Token k dispozici na službu STS ve sféře, vztah důvěryhodnosti služby.</span><span class="sxs-lookup"><span data-stu-id="e57df-157">Present the token to the STS in the service trust realm.</span></span>  
  
-   <span data-ttu-id="e57df-158">Získejte token zabezpečení od služby tokenů zabezpečení ve sféře, vztah důvěryhodnosti služby.</span><span class="sxs-lookup"><span data-stu-id="e57df-158">Obtain a security token from the STS in the service trust realm.</span></span>  
  
-   <span data-ttu-id="e57df-159">K dispozici token, který má služba pro přístup ke službě.</span><span class="sxs-lookup"><span data-stu-id="e57df-159">Present the token to the service to access the service.</span></span>  
  
### <a name="phase-2-run-time-phase"></a><span data-ttu-id="e57df-160">Fáze 2: Run-Time fáze</span><span class="sxs-lookup"><span data-stu-id="e57df-160">Phase 2: Run-Time Phase</span></span>  
 <span data-ttu-id="e57df-161">Během fáze spuštění klienta vytvoří objekt [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] třída klienta a umožňuje volání pomocí [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta.</span><span class="sxs-lookup"><span data-stu-id="e57df-161">During the run-time phase, the client instantiates an object of the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client class and makes a call using the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client.</span></span> <span data-ttu-id="e57df-162">Základní architektura [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zpracovává výše uvedených kroků ve vzoru federované zabezpečení komunikace a umožňuje klientovi bez problémů používat službu.</span><span class="sxs-lookup"><span data-stu-id="e57df-162">The underlying framework of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] handles the previously mentioned steps in the federated security communication pattern and enables the client to seamlessly consume the service.</span></span>  
  
## <a name="sample-implementation-using-wcf"></a><span data-ttu-id="e57df-163">Ukázka implementace pomocí WCF</span><span class="sxs-lookup"><span data-stu-id="e57df-163">Sample Implementation Using WCF</span></span>  
 <span data-ttu-id="e57df-164">Následující obrázek znázorňuje implementaci ukázka pro federované zabezpečení architektury pomocí nativní podporu z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e57df-164">The following illustration shows a sample implementation for a federated security architecture using native support from [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 <span data-ttu-id="e57df-165">![Federační zabezpečení ve WCF](../../../../docs/framework/wcf/feature-details/media/federatedsecurityinwcf.gif "FederatedSecurityInWCF")</span><span class="sxs-lookup"><span data-stu-id="e57df-165">![Federation security in WCF](../../../../docs/framework/wcf/feature-details/media/federatedsecurityinwcf.gif "FederatedSecurityInWCF")</span></span>  
  
### <a name="example-myservice"></a><span data-ttu-id="e57df-166">Příklad Moje_služba</span><span class="sxs-lookup"><span data-stu-id="e57df-166">Example MyService</span></span>  
 <span data-ttu-id="e57df-167">Služba `MyService` vystavuje jeden koncový bod prostřednictvím `MyServiceEndpoint`.</span><span class="sxs-lookup"><span data-stu-id="e57df-167">The service `MyService` exposes a single endpoint through `MyServiceEndpoint`.</span></span> <span data-ttu-id="e57df-168">Následující obrázek znázorňuje adresy, vazby a kontraktu přiřazené ke koncovému bodu.</span><span class="sxs-lookup"><span data-stu-id="e57df-168">The following illustration shows the address, binding, and contract associated with the endpoint.</span></span>  
  
 <span data-ttu-id="e57df-169">![Federační](../../../../docs/framework/wcf/feature-details/media/myservice.gif "Moje_služba")</span><span class="sxs-lookup"><span data-stu-id="e57df-169">![Federation](../../../../docs/framework/wcf/feature-details/media/myservice.gif "MyService")</span></span>  
  
 <span data-ttu-id="e57df-170">Koncový bod služby `MyServiceEndpoint` používá [ \<– wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) a vyžaduje platný token zabezpečení kontrolní výrazy Markup Language (SAML) s `accessAuthorized` deklarace identity vystavený B. služby tokenů zabezpečení Toto nastavení je deklarativně zadané v konfiguraci služby.</span><span class="sxs-lookup"><span data-stu-id="e57df-170">The service endpoint `MyServiceEndpoint` uses the [\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) and requires a valid Security Assertions Markup Language (SAML) token with an `accessAuthorized` claim issued by STS B. This is declaratively specified in the service configuration.</span></span>  
  
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
>  <span data-ttu-id="e57df-171">O deklaracích identity vyžaduje potřeba poznamenat bod jemně `MyService`.</span><span class="sxs-lookup"><span data-stu-id="e57df-171">A subtle point should be noted about the claims required by `MyService`.</span></span> <span data-ttu-id="e57df-172">Druhý obrázek znamená, že `MyService` vyžaduje tokenu SAML s `accessAuthorized` deklarací identity.</span><span class="sxs-lookup"><span data-stu-id="e57df-172">The second figure indicates that `MyService` requires a SAML token with the `accessAuthorized` claim.</span></span> <span data-ttu-id="e57df-173">Jako přesnější, určuje typ deklarace identity, aby `MyService` vyžaduje.</span><span class="sxs-lookup"><span data-stu-id="e57df-173">To be more precise, this specifies the claim type that `MyService` requires.</span></span> <span data-ttu-id="e57df-174">Plně kvalifikovaný název tohoto typu deklarace identity je http://tempuri.org:accessAuthorized (spolu s přidružené oboru názvů), který se používá v konfiguračním souboru služby.</span><span class="sxs-lookup"><span data-stu-id="e57df-174">The fully-qualified name of this claim type is http://tempuri.org:accessAuthorized (along with the associated namespace), which is used in the service configuration file.</span></span> <span data-ttu-id="e57df-175">Hodnota této deklarace indikuje přítomnost této deklarace identity a se předpokládá, že bude nastaven na `true` pomocí služby tokenů zabezpečení B.</span><span class="sxs-lookup"><span data-stu-id="e57df-175">The value of this claim indicates the presence of this claim and is assumed to be set to `true` by STS B.</span></span>  
  
 <span data-ttu-id="e57df-176">Za běhu, je tato zásada vynucené `MyServiceOperationRequirement` třídu, která je implementovaná jako součást `MyService`.</span><span class="sxs-lookup"><span data-stu-id="e57df-176">At runtime, this policy is enforced by the `MyServiceOperationRequirement` class that is implemented as part of the `MyService`.</span></span>  
  
 [!code-csharp[C_Federation#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#0)]
 [!code-vb[C_Federation#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#0)]  
[!code-csharp[C_Federation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#1)]
[!code-vb[C_Federation#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#1)]  
  
#### <a name="sts-b"></a><span data-ttu-id="e57df-177">SLUŽBA TOKENŮ ZABEZPEČENÍ B</span><span class="sxs-lookup"><span data-stu-id="e57df-177">STS B</span></span>  
 <span data-ttu-id="e57df-178">Následující obrázek znázorňuje B. služby tokenů zabezpečení Jak jsme uvedli dříve, služby tokenů zabezpečení (STS) je také webová služba a může mít jeho přidružené koncových bodů, zásad a tak dále.</span><span class="sxs-lookup"><span data-stu-id="e57df-178">The following illustration shows the STS B. As stated earlier, a security token service (STS) is also a Web service and can have its associated endpoints, policy, and so on.</span></span>  
  
 <span data-ttu-id="e57df-179">![Federační](../../../../docs/framework/wcf/feature-details/media/msservicestsb.gif "MsServiceSTSB")</span><span class="sxs-lookup"><span data-stu-id="e57df-179">![Federation](../../../../docs/framework/wcf/feature-details/media/msservicestsb.gif "MsServiceSTSB")</span></span>  
  
 <span data-ttu-id="e57df-180">Služby tokenů zabezpečení B vystavuje jeden koncový bod, který volá `STSEndpoint` který lze použít k žádosti o tokeny zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="e57df-180">STS B exposes a single endpoint, called `STSEndpoint` that can be use to request security tokens.</span></span> <span data-ttu-id="e57df-181">Konkrétně STS B vydává tokeny SAML s `accessAuthorized` deklarace identity, které lze zobrazit v `MyService` služeb – web pro přístup k službě.</span><span class="sxs-lookup"><span data-stu-id="e57df-181">Specifically, STS B issues SAML tokens with the `accessAuthorized` claim, which can be presented at the `MyService` service site for accessing the service.</span></span> <span data-ttu-id="e57df-182">Však B služby tokenů zabezpečení vyžaduje uživatelům k dispozici platný token SAML vydaný A služby tokenů zabezpečení, který obsahuje `userAuthenticated` deklarací identity.</span><span class="sxs-lookup"><span data-stu-id="e57df-182">However, STS B requires users to present a valid SAML token issued by STS A that contains the `userAuthenticated` claim.</span></span> <span data-ttu-id="e57df-183">To je deklarativně zadaný v konfiguraci služby tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="e57df-183">This is declaratively specified in the STS configuration.</span></span>  
  
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
>  <span data-ttu-id="e57df-184">Znovu `userAuthenticated` deklarace identity je typ deklarace identity, který vyžaduje službu tokenů zabezpečení B. Plně kvalifikovaný název tohoto typu deklarace identity je http://tempuri.org:userAuthenticated (spolu s přidružené oboru názvů), který se používá v konfiguračním souboru služby tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="e57df-184">Again, the `userAuthenticated` claim is the claim type that is required by STS B. The fully-qualified name of this claim type is http://tempuri.org:userAuthenticated (along with the associated namespace), which is used in the STS configuration file.</span></span> <span data-ttu-id="e57df-185">Hodnota této deklarace indikuje přítomnost této deklarace identity a se předpokládá, že bude nastaven na `true` služby tokenů zabezpečení a.</span><span class="sxs-lookup"><span data-stu-id="e57df-185">The value of this claim indicates the presence of this claim and is assumed to be set to `true` by STS A.</span></span>  
  
 <span data-ttu-id="e57df-186">V době běhu `STS_B_OperationRequirement` třída vynucuje tato zásada, která je implementovaná jako součást služby tokenů zabezpečení B.</span><span class="sxs-lookup"><span data-stu-id="e57df-186">At runtime, the `STS_B_OperationRequirement` class enforces this policy, which is implemented as part of STS B.</span></span>  
  
 [!code-csharp[C_Federation#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#2)]
 [!code-vb[C_Federation#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#2)]  
  
 <span data-ttu-id="e57df-187">Pokud kontrola přístupu není zaškrtnuto, služba tokenů zabezpečení B vydá token SAML s `accessAuthorized` deklarací identity.</span><span class="sxs-lookup"><span data-stu-id="e57df-187">If the access check is clear, STS B issues a SAML token with the `accessAuthorized` claim.</span></span>  
  
 [!code-csharp[C_Federation#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#3)]
 [!code-vb[C_Federation#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#3)]  
  
#### <a name="sts-a"></a><span data-ttu-id="e57df-188">SLUŽBA TOKENŮ ZABEZPEČENÍ A</span><span class="sxs-lookup"><span data-stu-id="e57df-188">STS A</span></span>  
 <span data-ttu-id="e57df-189">Následující obrázek znázorňuje A. služby tokenů zabezpečení</span><span class="sxs-lookup"><span data-stu-id="e57df-189">The following illustration shows the STS A.</span></span>  
  
 <span data-ttu-id="e57df-190">![Federační](../../../../docs/framework/wcf/feature-details/media/sts-b.gif "STS_B")</span><span class="sxs-lookup"><span data-stu-id="e57df-190">![Federation](../../../../docs/framework/wcf/feature-details/media/sts-b.gif "STS_B")</span></span>  
  
 <span data-ttu-id="e57df-191">Podobně jako u služby tokenů zabezpečení B, A služby tokenů zabezpečení je taky webová služba, která vydává tokeny zabezpečení a zveřejňuje jeden koncový bod pro tento účel.</span><span class="sxs-lookup"><span data-stu-id="e57df-191">Similar to the STS B, the STS A is also a Web service that issues security tokens and exposes a single endpoint for this purpose.</span></span> <span data-ttu-id="e57df-192">Ale používá jinou vazbou (`wsHttpBinding`) a vyžaduje, aby uživatelé k dispozici platný [!INCLUDE[infocard](../../../../includes/infocard-md.md)] s `emailAddress` deklarací identity.</span><span class="sxs-lookup"><span data-stu-id="e57df-192">However, it uses a different binding (`wsHttpBinding`) and requires users to present a valid [!INCLUDE[infocard](../../../../includes/infocard-md.md)] with an `emailAddress` claim.</span></span> <span data-ttu-id="e57df-193">V odpovědi, vydává tokeny SAML s `userAuthenticated` deklarací identity.</span><span class="sxs-lookup"><span data-stu-id="e57df-193">In response, it issues SAML tokens with the `userAuthenticated` claim.</span></span> <span data-ttu-id="e57df-194">Toto nastavení je deklarativně zadané v konfiguraci služby.</span><span class="sxs-lookup"><span data-stu-id="e57df-194">This is declaratively specified in the service configuration.</span></span>  
  
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
  
 <span data-ttu-id="e57df-195">V době běhu `STS_A_OperationRequirement` třída vynucuje tato zásada, která je implementovaná jako součást služby tokenů zabezpečení A.</span><span class="sxs-lookup"><span data-stu-id="e57df-195">At runtime, the `STS_A_OperationRequirement` class enforces this policy, which is implemented as part of STS A.</span></span>  
  
 [!code-csharp[C_Federation#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#4)]
 [!code-vb[C_Federation#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#4)]  
  
 <span data-ttu-id="e57df-196">Pokud je přístup `true`, služby tokenů zabezpečení A vydá token SAML s `userAuthenticated` deklarací identity.</span><span class="sxs-lookup"><span data-stu-id="e57df-196">If the access is `true`, STS A issues a SAML token with `userAuthenticated` claim.</span></span>  
  
 [!code-csharp[C_Federation#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#5)]
 [!code-vb[C_Federation#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#5)]  
  
### <a name="client-at-organization-a"></a><span data-ttu-id="e57df-197">Klient v organizaci A</span><span class="sxs-lookup"><span data-stu-id="e57df-197">Client at Organization A</span></span>  
 <span data-ttu-id="e57df-198">Následující obrázek znázorňuje klienta v organizaci A, společně s kroky při vytváření `MyService` služby volání.</span><span class="sxs-lookup"><span data-stu-id="e57df-198">The following illustration shows the client at organization A, along with the steps involved in making a `MyService` service call.</span></span> <span data-ttu-id="e57df-199">Ostatní funkční součásti jsou také zahrnuté pro úplnost.</span><span class="sxs-lookup"><span data-stu-id="e57df-199">The other functional components are also included for completeness.</span></span>  
  
 <span data-ttu-id="e57df-200">![Federační](../../../../docs/framework/wcf/feature-details/media/federationclienta.gif "FederationClientA")</span><span class="sxs-lookup"><span data-stu-id="e57df-200">![Federation](../../../../docs/framework/wcf/feature-details/media/federationclienta.gif "FederationClientA")</span></span>  
  
## <a name="summary"></a><span data-ttu-id="e57df-201">Souhrn</span><span class="sxs-lookup"><span data-stu-id="e57df-201">Summary</span></span>  
 <span data-ttu-id="e57df-202">Federované zabezpečení poskytuje čistou dělení zodpovědnosti a pomáhá k vytvoření zabezpečeného a škálovatelného služby architektury.</span><span class="sxs-lookup"><span data-stu-id="e57df-202">Federated security provides a clean division of responsibility and helps to build secure, scalable service architectures.</span></span> <span data-ttu-id="e57df-203">Jako platforma pro vytváření a nasazování distribuované aplikace [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] poskytuje nativní podporu pro implementaci federované zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="e57df-203">As a platform for building and deploying distributed applications, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] provides native support for implementing federated security.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e57df-204">Viz také</span><span class="sxs-lookup"><span data-stu-id="e57df-204">See Also</span></span>  
 [<span data-ttu-id="e57df-205">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="e57df-205">Security</span></span>](../../../../docs/framework/wcf/feature-details/security.md)
