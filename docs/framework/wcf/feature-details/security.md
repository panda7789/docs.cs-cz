---
title: Zabezpečení WCF
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, programming
- security [WCF]
- Windows Communication Foundation, security
ms.assetid: 7ea87fcb-dcfb-4a4a-8b03-6b954575d45b
author: BrucePerlerMS
ms.openlocfilehash: 2d4f2d67c8afd1687d9de506cf8a7616408069d2
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2018
ms.locfileid: "47200786"
---
# <a name="windows-communication-foundation-security"></a><span data-ttu-id="21ea1-102">Zabezpečení WCF</span><span class="sxs-lookup"><span data-stu-id="21ea1-102">Windows Communication Foundation Security</span></span>
<span data-ttu-id="21ea1-103">Témata v této části popisují funkce zabezpečení Windows Communication Foundation (WCF) a pomocí nich můžete pomoct zabezpečených zpráv.</span><span class="sxs-lookup"><span data-stu-id="21ea1-103">The topics in this section describe Windows Communication Foundation (WCF) security features and how to use them to help secure messages.</span></span>  
  
 <span data-ttu-id="21ea1-104">Další informace o systému Windows Server AppFabric a zabezpečení najdete v tématu [Model zabezpečení pro Windows Server AppFabric](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)</span><span class="sxs-lookup"><span data-stu-id="21ea1-104">For more information about Windows Server AppFabric and security, see [Security Model for Windows Server AppFabric](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="21ea1-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="21ea1-105">In This Section</span></span>  
 [<span data-ttu-id="21ea1-106">Přehled zabezpečení</span><span class="sxs-lookup"><span data-stu-id="21ea1-106">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 <span data-ttu-id="21ea1-107">Popisuje funkce zabezpečení ve službě WCF.</span><span class="sxs-lookup"><span data-stu-id="21ea1-107">Describes the security features in WCF.</span></span>  
  
 [<span data-ttu-id="21ea1-108">Koncepty zabezpečení</span><span class="sxs-lookup"><span data-stu-id="21ea1-108">Security Concepts</span></span>](../../../../docs/framework/wcf/feature-details/security-concepts.md)  
 <span data-ttu-id="21ea1-109">Popisuje základní terminologie a koncepty používané v zabezpečení WCF.</span><span class="sxs-lookup"><span data-stu-id="21ea1-109">Describes the basic terminology and concepts used in WCF security.</span></span>  
  
 [<span data-ttu-id="21ea1-110">Běžné scénáře zabezpečení</span><span class="sxs-lookup"><span data-stu-id="21ea1-110">Common Security Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)  
 <span data-ttu-id="21ea1-111">Popisuje scénářů a topologií, které můžete nakonfigurovat s použitím technologie WCF.</span><span class="sxs-lookup"><span data-stu-id="21ea1-111">Describes scenarios and topologies you can configure with WCF.</span></span>  
  
 [<span data-ttu-id="21ea1-112">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="21ea1-112">Security Behaviors</span></span>](../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 <span data-ttu-id="21ea1-113">Poskytuje přehled o chování WCF, které mají vliv na zabezpečení, jako je například nastavení přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="21ea1-113">Provides an overview of WCF behaviors that affect security, such as setting credentials.</span></span>  
  
 [<span data-ttu-id="21ea1-114">Vazby a zabezpečení</span><span class="sxs-lookup"><span data-stu-id="21ea1-114">Bindings and Security</span></span>](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)  
 <span data-ttu-id="21ea1-115">Zobrazení vazeb, včetně témata, která ukazují, jak vytvořit vlastní zabezpečení vazby týkající se zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="21ea1-115">A security-oriented view of the bindings, including topics that demonstrate how to create custom security bindings.</span></span>  
  
 [<span data-ttu-id="21ea1-116">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="21ea1-116">Securing Services and Clients</span></span>](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 <span data-ttu-id="21ea1-117">Popisuje postup zabezpečení zpráv pomocí funkce zabezpečení WCF.</span><span class="sxs-lookup"><span data-stu-id="21ea1-117">Describes how to secure messages using WCF security features.</span></span>  
  
 [<span data-ttu-id="21ea1-118">Ověřování</span><span class="sxs-lookup"><span data-stu-id="21ea1-118">Authentication</span></span>](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)  
 <span data-ttu-id="21ea1-119">Ukazuje běžné úlohy ověřování.</span><span class="sxs-lookup"><span data-stu-id="21ea1-119">Demonstrates common authentication tasks.</span></span>  
  
 [<span data-ttu-id="21ea1-120">Autorizace</span><span class="sxs-lookup"><span data-stu-id="21ea1-120">Authorization</span></span>](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
 <span data-ttu-id="21ea1-121">Popisuje běžné scénáře ověření s implementacemi zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="21ea1-121">Describes common authorization scenarios with security implementations.</span></span>  
  
 [<span data-ttu-id="21ea1-122">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="21ea1-122">Federation and Issued Tokens</span></span>](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 <span data-ttu-id="21ea1-123">Popisuje základní informace o federaci a jak vytvořit klienty, kteří komunikují se servery pro federované.</span><span class="sxs-lookup"><span data-stu-id="21ea1-123">Describes the basics of federation and how to create clients that communicate with federated servers.</span></span>  
  
 [<span data-ttu-id="21ea1-124">Částečná důvěryhodnost</span><span class="sxs-lookup"><span data-stu-id="21ea1-124">Partial Trust</span></span>](../../../../docs/framework/wcf/feature-details/partial-trust.md)  
 <span data-ttu-id="21ea1-125">Popisuje způsob spuštění částečně důvěryhodné scénářích a omezeních WCF při spuštění částečně důvěryhodné.</span><span class="sxs-lookup"><span data-stu-id="21ea1-125">Describes how to run partially-trusted scenarios and WCF limitations when running partially trusted.</span></span>  
  
 [<span data-ttu-id="21ea1-126">Auditování</span><span class="sxs-lookup"><span data-stu-id="21ea1-126">Auditing</span></span>](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)  
 <span data-ttu-id="21ea1-127">Popisuje, jak auditování událostí zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="21ea1-127">Describes how to audit security events.</span></span>  
  
 [<span data-ttu-id="21ea1-128">Informace o zabezpečení a osvědčené postupy</span><span class="sxs-lookup"><span data-stu-id="21ea1-128">Security Guidance and Best Practices</span></span>](../../../../docs/framework/wcf/feature-details/security-guidance-and-best-practices.md)  
 <span data-ttu-id="21ea1-129">Pokyny pro vytváření zabezpečených aplikací WCF.</span><span class="sxs-lookup"><span data-stu-id="21ea1-129">Guidelines for creating secure WCF applications.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="21ea1-130">Odkaz</span><span class="sxs-lookup"><span data-stu-id="21ea1-130">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Security>  
  
## <a name="related-sections"></a><span data-ttu-id="21ea1-131">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="21ea1-131">Related Sections</span></span>  
 [<span data-ttu-id="21ea1-132">Podrobnosti o funkcích WCF</span><span class="sxs-lookup"><span data-stu-id="21ea1-132">WCF Feature Details</span></span>](../../../../docs/framework/wcf/feature-details/index.md)  
  
 [<span data-ttu-id="21ea1-133">Základní programování WCF</span><span class="sxs-lookup"><span data-stu-id="21ea1-133">Basic WCF Programming</span></span>](../../../../docs/framework/wcf/basic-wcf-programming.md)  
  
 [<span data-ttu-id="21ea1-134">Kurz Začínáme</span><span class="sxs-lookup"><span data-stu-id="21ea1-134">Getting Started Tutorial</span></span>](../../../../docs/framework/wcf/getting-started-tutorial.md)  
  
 [<span data-ttu-id="21ea1-135">Koncepční přehled</span><span class="sxs-lookup"><span data-stu-id="21ea1-135">Conceptual Overview</span></span>](../../../../docs/framework/wcf/conceptual-overview.md)  
  
## <a name="see-also"></a><span data-ttu-id="21ea1-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="21ea1-136">See Also</span></span>  
 [<span data-ttu-id="21ea1-137">Konfigurace vaší aplikace</span><span class="sxs-lookup"><span data-stu-id="21ea1-137">Configuring Your Application</span></span>](../../../../docs/framework/wcf/diagnostics/configuring-your-application.md)
