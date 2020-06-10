---
title: Zabezpečení WCF
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, programming
- security [WCF]
- Windows Communication Foundation, security
ms.assetid: 7ea87fcb-dcfb-4a4a-8b03-6b954575d45b
ms.openlocfilehash: 327fb509a5186a0b3f428efc2ddd7f983bcfa978
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595139"
---
# <a name="windows-communication-foundation-security"></a><span data-ttu-id="fb3b0-102">Zabezpečení WCF</span><span class="sxs-lookup"><span data-stu-id="fb3b0-102">Windows Communication Foundation Security</span></span>
<span data-ttu-id="fb3b0-103">Témata v této části popisují funkce zabezpečení služby Windows Communication Foundation (WCF) a jejich použití k zabezpečení zpráv.</span><span class="sxs-lookup"><span data-stu-id="fb3b0-103">The topics in this section describe Windows Communication Foundation (WCF) security features and how to use them to help secure messages.</span></span>  
  
 <span data-ttu-id="fb3b0-104">Další informace o Windows Server AppFabric a zabezpečení najdete v tématu [model zabezpečení pro Windows Server AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10)) .</span><span class="sxs-lookup"><span data-stu-id="fb3b0-104">For more information about Windows Server AppFabric and security, see [Security Model for Windows Server AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fb3b0-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="fb3b0-105">In This Section</span></span>  
 [<span data-ttu-id="fb3b0-106">Přehled zabezpečení</span><span class="sxs-lookup"><span data-stu-id="fb3b0-106">Security Overview</span></span>](security-overview.md)  
 <span data-ttu-id="fb3b0-107">Popisuje funkce zabezpečení ve službě WCF.</span><span class="sxs-lookup"><span data-stu-id="fb3b0-107">Describes the security features in WCF.</span></span>  
  
 [<span data-ttu-id="fb3b0-108">Koncepce zabezpečení</span><span class="sxs-lookup"><span data-stu-id="fb3b0-108">Security Concepts</span></span>](security-concepts.md)  
 <span data-ttu-id="fb3b0-109">Popisuje základní terminologii a koncepty používané v zabezpečení služby WCF.</span><span class="sxs-lookup"><span data-stu-id="fb3b0-109">Describes the basic terminology and concepts used in WCF security.</span></span>  
  
 [<span data-ttu-id="fb3b0-110">Běžné scénáře zabezpečení</span><span class="sxs-lookup"><span data-stu-id="fb3b0-110">Common Security Scenarios</span></span>](common-security-scenarios.md)  
 <span data-ttu-id="fb3b0-111">Popisuje scénáře a topologie, které můžete konfigurovat pomocí WCF.</span><span class="sxs-lookup"><span data-stu-id="fb3b0-111">Describes scenarios and topologies you can configure with WCF.</span></span>  
  
 [<span data-ttu-id="fb3b0-112">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="fb3b0-112">Security Behaviors</span></span>](security-behaviors-in-wcf.md)  
 <span data-ttu-id="fb3b0-113">Poskytuje přehled o chováních služby WCF, která mají vliv na zabezpečení, jako je například nastavení přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="fb3b0-113">Provides an overview of WCF behaviors that affect security, such as setting credentials.</span></span>  
  
 [<span data-ttu-id="fb3b0-114">Vazby a zabezpečení</span><span class="sxs-lookup"><span data-stu-id="fb3b0-114">Bindings and Security</span></span>](bindings-and-security.md)  
 <span data-ttu-id="fb3b0-115">Zobrazení vazeb orientované na zabezpečení, včetně témat, která ukazují, jak vytvářet vlastní vazby zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="fb3b0-115">A security-oriented view of the bindings, including topics that demonstrate how to create custom security bindings.</span></span>  
  
 [<span data-ttu-id="fb3b0-116">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="fb3b0-116">Securing Services and Clients</span></span>](securing-services-and-clients.md)  
 <span data-ttu-id="fb3b0-117">Popisuje, jak zabezpečit zprávy pomocí funkcí zabezpečení služby WCF.</span><span class="sxs-lookup"><span data-stu-id="fb3b0-117">Describes how to secure messages using WCF security features.</span></span>  
  
 [<span data-ttu-id="fb3b0-118">Authentication</span><span class="sxs-lookup"><span data-stu-id="fb3b0-118">Authentication</span></span>](authentication-in-wcf.md)  
 <span data-ttu-id="fb3b0-119">Ukazuje běžné úlohy ověřování.</span><span class="sxs-lookup"><span data-stu-id="fb3b0-119">Demonstrates common authentication tasks.</span></span>  
  
 [<span data-ttu-id="fb3b0-120">Autorizace</span><span class="sxs-lookup"><span data-stu-id="fb3b0-120">Authorization</span></span>](authorization-in-wcf.md)  
 <span data-ttu-id="fb3b0-121">Popisuje běžné autorizační scénáře s implementacemi zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="fb3b0-121">Describes common authorization scenarios with security implementations.</span></span>  
  
 [<span data-ttu-id="fb3b0-122">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="fb3b0-122">Federation and Issued Tokens</span></span>](federation-and-issued-tokens.md)  
 <span data-ttu-id="fb3b0-123">Popisuje základy federace a vytváření klientů, kteří komunikují s federované servery.</span><span class="sxs-lookup"><span data-stu-id="fb3b0-123">Describes the basics of federation and how to create clients that communicate with federated servers.</span></span>  
  
 [<span data-ttu-id="fb3b0-124">Částečná důvěryhodnost</span><span class="sxs-lookup"><span data-stu-id="fb3b0-124">Partial Trust</span></span>](partial-trust.md)  
 <span data-ttu-id="fb3b0-125">Popisuje spuštění částečně důvěryhodných scénářů a omezení WCF při spuštění částečně důvěryhodného.</span><span class="sxs-lookup"><span data-stu-id="fb3b0-125">Describes how to run partially-trusted scenarios and WCF limitations when running partially trusted.</span></span>  
  
 [<span data-ttu-id="fb3b0-126">Auditování</span><span class="sxs-lookup"><span data-stu-id="fb3b0-126">Auditing</span></span>](auditing-security-events.md)  
 <span data-ttu-id="fb3b0-127">Popisuje, jak auditovat události zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="fb3b0-127">Describes how to audit security events.</span></span>  
  
 [<span data-ttu-id="fb3b0-128">Informace o zabezpečení a doporučené postupy</span><span class="sxs-lookup"><span data-stu-id="fb3b0-128">Security Guidance and Best Practices</span></span>](security-guidance-and-best-practices.md)  
 <span data-ttu-id="fb3b0-129">Pokyny pro vytváření zabezpečených aplikací WCF.</span><span class="sxs-lookup"><span data-stu-id="fb3b0-129">Guidelines for creating secure WCF applications.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="fb3b0-130">Referenční informace</span><span class="sxs-lookup"><span data-stu-id="fb3b0-130">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Security>  
  
## <a name="related-sections"></a><span data-ttu-id="fb3b0-131">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="fb3b0-131">Related Sections</span></span>  
 [<span data-ttu-id="fb3b0-132">Podrobnosti funkce WCF</span><span class="sxs-lookup"><span data-stu-id="fb3b0-132">WCF Feature Details</span></span>](index.md)  
  
 [<span data-ttu-id="fb3b0-133">Základní programování WCF</span><span class="sxs-lookup"><span data-stu-id="fb3b0-133">Basic WCF Programming</span></span>](../basic-wcf-programming.md)  
  
 [<span data-ttu-id="fb3b0-134">Kurz Začínáme</span><span class="sxs-lookup"><span data-stu-id="fb3b0-134">Getting Started Tutorial</span></span>](../getting-started-tutorial.md)  
  
 [<span data-ttu-id="fb3b0-135">Koncepční přehled</span><span class="sxs-lookup"><span data-stu-id="fb3b0-135">Conceptual Overview</span></span>](../conceptual-overview.md)  
  
## <a name="see-also"></a><span data-ttu-id="fb3b0-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="fb3b0-136">See also</span></span>

- [<span data-ttu-id="fb3b0-137">Konfigurace vaší aplikace</span><span class="sxs-lookup"><span data-stu-id="fb3b0-137">Configuring Your Application</span></span>](../diagnostics/configuring-your-application.md)
