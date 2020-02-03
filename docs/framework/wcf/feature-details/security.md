---
title: Zabezpečení WCF
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, programming
- security [WCF]
- Windows Communication Foundation, security
ms.assetid: 7ea87fcb-dcfb-4a4a-8b03-6b954575d45b
ms.openlocfilehash: 0f79ac28af45e8c05922373955c5317095d2c682
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744631"
---
# <a name="windows-communication-foundation-security"></a><span data-ttu-id="7ebcd-102">Zabezpečení WCF</span><span class="sxs-lookup"><span data-stu-id="7ebcd-102">Windows Communication Foundation Security</span></span>
<span data-ttu-id="7ebcd-103">Témata v této části popisují funkce zabezpečení služby Windows Communication Foundation (WCF) a jejich použití k zabezpečení zpráv.</span><span class="sxs-lookup"><span data-stu-id="7ebcd-103">The topics in this section describe Windows Communication Foundation (WCF) security features and how to use them to help secure messages.</span></span>  
  
 <span data-ttu-id="7ebcd-104">Další informace o Windows Server AppFabric a zabezpečení najdete v tématu [model zabezpečení pro Windows Server AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10)) .</span><span class="sxs-lookup"><span data-stu-id="7ebcd-104">For more information about Windows Server AppFabric and security, see [Security Model for Windows Server AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7ebcd-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="7ebcd-105">In This Section</span></span>  
 [<span data-ttu-id="7ebcd-106">Přehled zabezpečení</span><span class="sxs-lookup"><span data-stu-id="7ebcd-106">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 <span data-ttu-id="7ebcd-107">Popisuje funkce zabezpečení ve službě WCF.</span><span class="sxs-lookup"><span data-stu-id="7ebcd-107">Describes the security features in WCF.</span></span>  
  
 [<span data-ttu-id="7ebcd-108">Koncepty zabezpečení</span><span class="sxs-lookup"><span data-stu-id="7ebcd-108">Security Concepts</span></span>](../../../../docs/framework/wcf/feature-details/security-concepts.md)  
 <span data-ttu-id="7ebcd-109">Popisuje základní terminologii a koncepty používané v zabezpečení služby WCF.</span><span class="sxs-lookup"><span data-stu-id="7ebcd-109">Describes the basic terminology and concepts used in WCF security.</span></span>  
  
 [<span data-ttu-id="7ebcd-110">Běžné scénáře zabezpečení</span><span class="sxs-lookup"><span data-stu-id="7ebcd-110">Common Security Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)  
 <span data-ttu-id="7ebcd-111">Popisuje scénáře a topologie, které můžete konfigurovat pomocí WCF.</span><span class="sxs-lookup"><span data-stu-id="7ebcd-111">Describes scenarios and topologies you can configure with WCF.</span></span>  
  
 [<span data-ttu-id="7ebcd-112">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="7ebcd-112">Security Behaviors</span></span>](../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 <span data-ttu-id="7ebcd-113">Poskytuje přehled o chováních služby WCF, která mají vliv na zabezpečení, jako je například nastavení přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="7ebcd-113">Provides an overview of WCF behaviors that affect security, such as setting credentials.</span></span>  
  
 [<span data-ttu-id="7ebcd-114">Vazby a zabezpečení</span><span class="sxs-lookup"><span data-stu-id="7ebcd-114">Bindings and Security</span></span>](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)  
 <span data-ttu-id="7ebcd-115">Zobrazení vazeb orientované na zabezpečení, včetně témat, která ukazují, jak vytvářet vlastní vazby zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="7ebcd-115">A security-oriented view of the bindings, including topics that demonstrate how to create custom security bindings.</span></span>  
  
 [<span data-ttu-id="7ebcd-116">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="7ebcd-116">Securing Services and Clients</span></span>](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 <span data-ttu-id="7ebcd-117">Popisuje, jak zabezpečit zprávy pomocí funkcí zabezpečení služby WCF.</span><span class="sxs-lookup"><span data-stu-id="7ebcd-117">Describes how to secure messages using WCF security features.</span></span>  
  
 [<span data-ttu-id="7ebcd-118">Ověřování</span><span class="sxs-lookup"><span data-stu-id="7ebcd-118">Authentication</span></span>](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)  
 <span data-ttu-id="7ebcd-119">Ukazuje běžné úlohy ověřování.</span><span class="sxs-lookup"><span data-stu-id="7ebcd-119">Demonstrates common authentication tasks.</span></span>  
  
 [<span data-ttu-id="7ebcd-120">Autorizace</span><span class="sxs-lookup"><span data-stu-id="7ebcd-120">Authorization</span></span>](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
 <span data-ttu-id="7ebcd-121">Popisuje běžné autorizační scénáře s implementacemi zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="7ebcd-121">Describes common authorization scenarios with security implementations.</span></span>  
  
 [<span data-ttu-id="7ebcd-122">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="7ebcd-122">Federation and Issued Tokens</span></span>](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 <span data-ttu-id="7ebcd-123">Popisuje základy federace a vytváření klientů, kteří komunikují s federované servery.</span><span class="sxs-lookup"><span data-stu-id="7ebcd-123">Describes the basics of federation and how to create clients that communicate with federated servers.</span></span>  
  
 [<span data-ttu-id="7ebcd-124">Částečná důvěryhodnost</span><span class="sxs-lookup"><span data-stu-id="7ebcd-124">Partial Trust</span></span>](../../../../docs/framework/wcf/feature-details/partial-trust.md)  
 <span data-ttu-id="7ebcd-125">Popisuje spuštění částečně důvěryhodných scénářů a omezení WCF při spuštění částečně důvěryhodného.</span><span class="sxs-lookup"><span data-stu-id="7ebcd-125">Describes how to run partially-trusted scenarios and WCF limitations when running partially trusted.</span></span>  
  
 [<span data-ttu-id="7ebcd-126">Auditování</span><span class="sxs-lookup"><span data-stu-id="7ebcd-126">Auditing</span></span>](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)  
 <span data-ttu-id="7ebcd-127">Popisuje, jak auditovat události zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="7ebcd-127">Describes how to audit security events.</span></span>  
  
 [<span data-ttu-id="7ebcd-128">Informace o zabezpečení a osvědčené postupy</span><span class="sxs-lookup"><span data-stu-id="7ebcd-128">Security Guidance and Best Practices</span></span>](../../../../docs/framework/wcf/feature-details/security-guidance-and-best-practices.md)  
 <span data-ttu-id="7ebcd-129">Pokyny pro vytváření zabezpečených aplikací WCF.</span><span class="sxs-lookup"><span data-stu-id="7ebcd-129">Guidelines for creating secure WCF applications.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="7ebcd-130">Referenční informace</span><span class="sxs-lookup"><span data-stu-id="7ebcd-130">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Security>  
  
## <a name="related-sections"></a><span data-ttu-id="7ebcd-131">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="7ebcd-131">Related Sections</span></span>  
 [<span data-ttu-id="7ebcd-132">Podrobnosti o funkcích WCF</span><span class="sxs-lookup"><span data-stu-id="7ebcd-132">WCF Feature Details</span></span>](../../../../docs/framework/wcf/feature-details/index.md)  
  
 [<span data-ttu-id="7ebcd-133">Základní programování WCF</span><span class="sxs-lookup"><span data-stu-id="7ebcd-133">Basic WCF Programming</span></span>](../../../../docs/framework/wcf/basic-wcf-programming.md)  
  
 [<span data-ttu-id="7ebcd-134">Kurz Začínáme</span><span class="sxs-lookup"><span data-stu-id="7ebcd-134">Getting Started Tutorial</span></span>](../../../../docs/framework/wcf/getting-started-tutorial.md)  
  
 [<span data-ttu-id="7ebcd-135">Koncepční přehled</span><span class="sxs-lookup"><span data-stu-id="7ebcd-135">Conceptual Overview</span></span>](../../../../docs/framework/wcf/conceptual-overview.md)  
  
## <a name="see-also"></a><span data-ttu-id="7ebcd-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="7ebcd-136">See also</span></span>

- [<span data-ttu-id="7ebcd-137">Konfigurace vaší aplikace</span><span class="sxs-lookup"><span data-stu-id="7ebcd-137">Configuring Your Application</span></span>](../../../../docs/framework/wcf/diagnostics/configuring-your-application.md)
