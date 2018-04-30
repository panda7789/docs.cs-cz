---
title: Zabezpečení WCF
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Windows Communication Foundation, programming
- security [WCF]
- Windows Communication Foundation, security
ms.assetid: 7ea87fcb-dcfb-4a4a-8b03-6b954575d45b
caps.latest.revision: 21
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: 6b93bfff2cd97e10d9c0dba4373839337f36aacb
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/30/2018
---
# <a name="windows-communication-foundation-security"></a><span data-ttu-id="85933-102">Zabezpečení WCF</span><span class="sxs-lookup"><span data-stu-id="85933-102">Windows Communication Foundation Security</span></span>
<span data-ttu-id="85933-103">Témata v této části popisují [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] funkce zabezpečení a jejich použití ke zabezpečených zpráv.</span><span class="sxs-lookup"><span data-stu-id="85933-103">The topics in this section describe [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] security features and how to use them to help secure messages.</span></span>  
  
 <span data-ttu-id="85933-104">Další informace o systému Windows Server AppFabric a zabezpečení najdete v tématu [Model zabezpečení pro Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)</span><span class="sxs-lookup"><span data-stu-id="85933-104">For more information about Windows Server AppFabric and security, see [Security Model for Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="85933-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="85933-105">In This Section</span></span>  
 [<span data-ttu-id="85933-106">Přehled zabezpečení</span><span class="sxs-lookup"><span data-stu-id="85933-106">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 <span data-ttu-id="85933-107">Popisuje funkce zabezpečení v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="85933-107">Describes the security features in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 [<span data-ttu-id="85933-108">Koncepty zabezpečení</span><span class="sxs-lookup"><span data-stu-id="85933-108">Security Concepts</span></span>](../../../../docs/framework/wcf/feature-details/security-concepts.md)  
 <span data-ttu-id="85933-109">Popisuje základní terminologie a koncepty používané v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="85933-109">Describes the basic terminology and concepts used in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] security.</span></span>  
  
 [<span data-ttu-id="85933-110">Běžné scénáře zabezpečení</span><span class="sxs-lookup"><span data-stu-id="85933-110">Common Security Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)  
 <span data-ttu-id="85933-111">Popisuje scénáře a topologie, můžete nakonfigurovat s [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="85933-111">Describes scenarios and topologies you can configure with [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 [<span data-ttu-id="85933-112">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="85933-112">Security Behaviors</span></span>](../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 <span data-ttu-id="85933-113">Poskytuje přehled o chování WCF, které mají vliv na zabezpečení, jako je například nastavení přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="85933-113">Provides an overview of WCF behaviors that affect security, such as setting credentials.</span></span>  
  
 [<span data-ttu-id="85933-114">Vazby a zabezpečení</span><span class="sxs-lookup"><span data-stu-id="85933-114">Bindings and Security</span></span>](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)  
 <span data-ttu-id="85933-115">Zobrazení orientované zabezpečení vazby, včetně témat, která ukazují, jak vytvořit vlastní zabezpečení vazby.</span><span class="sxs-lookup"><span data-stu-id="85933-115">A security-oriented view of the bindings, including topics that demonstrate how to create custom security bindings.</span></span>  
  
 [<span data-ttu-id="85933-116">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="85933-116">Securing Services and Clients</span></span>](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 <span data-ttu-id="85933-117">Popisuje, jak zabezpečit zprávy pomocí [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] funkce zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="85933-117">Describes how to secure messages using [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] security features.</span></span>  
  
 [<span data-ttu-id="85933-118">Ověřování</span><span class="sxs-lookup"><span data-stu-id="85933-118">Authentication</span></span>](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)  
 <span data-ttu-id="85933-119">Představuje běžné úlohy ověřování.</span><span class="sxs-lookup"><span data-stu-id="85933-119">Demonstrates common authentication tasks.</span></span>  
  
 [<span data-ttu-id="85933-120">Autorizace</span><span class="sxs-lookup"><span data-stu-id="85933-120">Authorization</span></span>](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
 <span data-ttu-id="85933-121">Popisuje běžné scénáře autorizace s implementacemi zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="85933-121">Describes common authorization scenarios with security implementations.</span></span>  
  
 [<span data-ttu-id="85933-122">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="85933-122">Federation and Issued Tokens</span></span>](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 <span data-ttu-id="85933-123">Obsahuje základní informace o federaci a postup vytvoření klientů, které komunikují se servery pro federované.</span><span class="sxs-lookup"><span data-stu-id="85933-123">Describes the basics of federation and how to create clients that communicate with federated servers.</span></span>  
  
 [<span data-ttu-id="85933-124">Částečná důvěryhodnost</span><span class="sxs-lookup"><span data-stu-id="85933-124">Partial Trust</span></span>](../../../../docs/framework/wcf/feature-details/partial-trust.md)  
 <span data-ttu-id="85933-125">Popisuje, jak spustit částečně důvěryhodné scénáře a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] omezení při spuštění částečně důvěryhodného.</span><span class="sxs-lookup"><span data-stu-id="85933-125">Describes how to run partially-trusted scenarios and [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] limitations when running partially trusted.</span></span>  
  
 [<span data-ttu-id="85933-126">Auditování</span><span class="sxs-lookup"><span data-stu-id="85933-126">Auditing</span></span>](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)  
 <span data-ttu-id="85933-127">Popisuje, jak auditování událostí zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="85933-127">Describes how to audit security events.</span></span>  
  
 [<span data-ttu-id="85933-128">Informace o zabezpečení a osvědčené postupy</span><span class="sxs-lookup"><span data-stu-id="85933-128">Security Guidance and Best Practices</span></span>](../../../../docs/framework/wcf/feature-details/security-guidance-and-best-practices.md)  
 <span data-ttu-id="85933-129">Pokyny pro vytvoření zabezpečeného [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikace.</span><span class="sxs-lookup"><span data-stu-id="85933-129">Guidelines for creating secure [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="85933-130">Odkaz</span><span class="sxs-lookup"><span data-stu-id="85933-130">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Security>  
  
## <a name="related-sections"></a><span data-ttu-id="85933-131">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="85933-131">Related Sections</span></span>  
 [<span data-ttu-id="85933-132">Podrobnosti o funkcích WCF</span><span class="sxs-lookup"><span data-stu-id="85933-132">WCF Feature Details</span></span>](../../../../docs/framework/wcf/feature-details/index.md)  
  
 [<span data-ttu-id="85933-133">Základní programování WCF</span><span class="sxs-lookup"><span data-stu-id="85933-133">Basic WCF Programming</span></span>](../../../../docs/framework/wcf/basic-wcf-programming.md)  
  
 [<span data-ttu-id="85933-134">Kurz Začínáme</span><span class="sxs-lookup"><span data-stu-id="85933-134">Getting Started Tutorial</span></span>](../../../../docs/framework/wcf/getting-started-tutorial.md)  
  
 [<span data-ttu-id="85933-135">Koncepční přehled</span><span class="sxs-lookup"><span data-stu-id="85933-135">Conceptual Overview</span></span>](../../../../docs/framework/wcf/conceptual-overview.md)  
  
## <a name="see-also"></a><span data-ttu-id="85933-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="85933-136">See Also</span></span>  
 [<span data-ttu-id="85933-137">Konfigurace vaší aplikace</span><span class="sxs-lookup"><span data-stu-id="85933-137">Configuring Your Application</span></span>](../../../../docs/framework/wcf/diagnostics/configuring-your-application.md)
