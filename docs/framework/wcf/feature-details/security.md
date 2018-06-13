---
title: Zabezpečení WCF
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, programming
- security [WCF]
- Windows Communication Foundation, security
ms.assetid: 7ea87fcb-dcfb-4a4a-8b03-6b954575d45b
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: fb48ae39d269f21a7120ecf143dc4c4680efe39d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33499086"
---
# <a name="windows-communication-foundation-security"></a><span data-ttu-id="ee2c3-102">Zabezpečení WCF</span><span class="sxs-lookup"><span data-stu-id="ee2c3-102">Windows Communication Foundation Security</span></span>
<span data-ttu-id="ee2c3-103">Témata v této části popisují funkce zabezpečení Windows Communication Foundation (WCF) a jejich použití ke zabezpečených zpráv.</span><span class="sxs-lookup"><span data-stu-id="ee2c3-103">The topics in this section describe Windows Communication Foundation (WCF) security features and how to use them to help secure messages.</span></span>  
  
 <span data-ttu-id="ee2c3-104">Další informace o systému Windows Server AppFabric a zabezpečení najdete v tématu [Model zabezpečení pro Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)</span><span class="sxs-lookup"><span data-stu-id="ee2c3-104">For more information about Windows Server AppFabric and security, see [Security Model for Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ee2c3-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="ee2c3-105">In This Section</span></span>  
 [<span data-ttu-id="ee2c3-106">Přehled zabezpečení</span><span class="sxs-lookup"><span data-stu-id="ee2c3-106">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 <span data-ttu-id="ee2c3-107">Popisuje funkce zabezpečení ve WCF.</span><span class="sxs-lookup"><span data-stu-id="ee2c3-107">Describes the security features in WCF.</span></span>  
  
 [<span data-ttu-id="ee2c3-108">Koncepty zabezpečení</span><span class="sxs-lookup"><span data-stu-id="ee2c3-108">Security Concepts</span></span>](../../../../docs/framework/wcf/feature-details/security-concepts.md)  
 <span data-ttu-id="ee2c3-109">Popisuje základní terminologie a koncepty používané v zabezpečení WCF.</span><span class="sxs-lookup"><span data-stu-id="ee2c3-109">Describes the basic terminology and concepts used in WCF security.</span></span>  
  
 [<span data-ttu-id="ee2c3-110">Běžné scénáře zabezpečení</span><span class="sxs-lookup"><span data-stu-id="ee2c3-110">Common Security Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)  
 <span data-ttu-id="ee2c3-111">Popisuje scénáře a topologie, které můžete konfigurovat s použitím technologie WCF.</span><span class="sxs-lookup"><span data-stu-id="ee2c3-111">Describes scenarios and topologies you can configure with WCF.</span></span>  
  
 [<span data-ttu-id="ee2c3-112">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="ee2c3-112">Security Behaviors</span></span>](../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 <span data-ttu-id="ee2c3-113">Poskytuje přehled o chování WCF, které mají vliv na zabezpečení, jako je například nastavení přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="ee2c3-113">Provides an overview of WCF behaviors that affect security, such as setting credentials.</span></span>  
  
 [<span data-ttu-id="ee2c3-114">Vazby a zabezpečení</span><span class="sxs-lookup"><span data-stu-id="ee2c3-114">Bindings and Security</span></span>](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)  
 <span data-ttu-id="ee2c3-115">Zobrazení orientované zabezpečení vazby, včetně témat, která ukazují, jak vytvořit vlastní zabezpečení vazby.</span><span class="sxs-lookup"><span data-stu-id="ee2c3-115">A security-oriented view of the bindings, including topics that demonstrate how to create custom security bindings.</span></span>  
  
 [<span data-ttu-id="ee2c3-116">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="ee2c3-116">Securing Services and Clients</span></span>](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 <span data-ttu-id="ee2c3-117">Popisuje, jak zabezpečit zprávy pomocí funkce zabezpečení WCF.</span><span class="sxs-lookup"><span data-stu-id="ee2c3-117">Describes how to secure messages using WCF security features.</span></span>  
  
 [<span data-ttu-id="ee2c3-118">Ověřování</span><span class="sxs-lookup"><span data-stu-id="ee2c3-118">Authentication</span></span>](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)  
 <span data-ttu-id="ee2c3-119">Představuje běžné úlohy ověřování.</span><span class="sxs-lookup"><span data-stu-id="ee2c3-119">Demonstrates common authentication tasks.</span></span>  
  
 [<span data-ttu-id="ee2c3-120">Autorizace</span><span class="sxs-lookup"><span data-stu-id="ee2c3-120">Authorization</span></span>](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
 <span data-ttu-id="ee2c3-121">Popisuje běžné scénáře autorizace s implementacemi zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="ee2c3-121">Describes common authorization scenarios with security implementations.</span></span>  
  
 [<span data-ttu-id="ee2c3-122">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="ee2c3-122">Federation and Issued Tokens</span></span>](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 <span data-ttu-id="ee2c3-123">Obsahuje základní informace o federaci a postup vytvoření klientů, které komunikují se servery pro federované.</span><span class="sxs-lookup"><span data-stu-id="ee2c3-123">Describes the basics of federation and how to create clients that communicate with federated servers.</span></span>  
  
 [<span data-ttu-id="ee2c3-124">Částečná důvěryhodnost</span><span class="sxs-lookup"><span data-stu-id="ee2c3-124">Partial Trust</span></span>](../../../../docs/framework/wcf/feature-details/partial-trust.md)  
 <span data-ttu-id="ee2c3-125">Popisuje postup při spuštění částečně důvěryhodného spuštění částečně důvěryhodného scénářích a omezeních WCF.</span><span class="sxs-lookup"><span data-stu-id="ee2c3-125">Describes how to run partially-trusted scenarios and WCF limitations when running partially trusted.</span></span>  
  
 [<span data-ttu-id="ee2c3-126">Auditování</span><span class="sxs-lookup"><span data-stu-id="ee2c3-126">Auditing</span></span>](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)  
 <span data-ttu-id="ee2c3-127">Popisuje, jak auditování událostí zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="ee2c3-127">Describes how to audit security events.</span></span>  
  
 [<span data-ttu-id="ee2c3-128">Informace o zabezpečení a osvědčené postupy</span><span class="sxs-lookup"><span data-stu-id="ee2c3-128">Security Guidance and Best Practices</span></span>](../../../../docs/framework/wcf/feature-details/security-guidance-and-best-practices.md)  
 <span data-ttu-id="ee2c3-129">Pokyny pro vytváření zabezpečených aplikací WCF.</span><span class="sxs-lookup"><span data-stu-id="ee2c3-129">Guidelines for creating secure WCF applications.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="ee2c3-130">Odkaz</span><span class="sxs-lookup"><span data-stu-id="ee2c3-130">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Security>  
  
## <a name="related-sections"></a><span data-ttu-id="ee2c3-131">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="ee2c3-131">Related Sections</span></span>  
 [<span data-ttu-id="ee2c3-132">Podrobnosti o funkcích WCF</span><span class="sxs-lookup"><span data-stu-id="ee2c3-132">WCF Feature Details</span></span>](../../../../docs/framework/wcf/feature-details/index.md)  
  
 [<span data-ttu-id="ee2c3-133">Základní programování WCF</span><span class="sxs-lookup"><span data-stu-id="ee2c3-133">Basic WCF Programming</span></span>](../../../../docs/framework/wcf/basic-wcf-programming.md)  
  
 [<span data-ttu-id="ee2c3-134">Kurz Začínáme</span><span class="sxs-lookup"><span data-stu-id="ee2c3-134">Getting Started Tutorial</span></span>](../../../../docs/framework/wcf/getting-started-tutorial.md)  
  
 [<span data-ttu-id="ee2c3-135">Koncepční přehled</span><span class="sxs-lookup"><span data-stu-id="ee2c3-135">Conceptual Overview</span></span>](../../../../docs/framework/wcf/conceptual-overview.md)  
  
## <a name="see-also"></a><span data-ttu-id="ee2c3-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="ee2c3-136">See Also</span></span>  
 [<span data-ttu-id="ee2c3-137">Konfigurace vaší aplikace</span><span class="sxs-lookup"><span data-stu-id="ee2c3-137">Configuring Your Application</span></span>](../../../../docs/framework/wcf/diagnostics/configuring-your-application.md)
