---
title: Zabezpečení služeb a klientů
ms.date: 03/30/2017
helpviewer_keywords:
- message security [WCF]
ms.assetid: e681f3bd-0c09-4a58-b0e4-0ecbdf1aa6c7
ms.openlocfilehash: 719ab26198bd7b83310025e03e541fa11b109612
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746412"
---
# <a name="securing-services-and-clients"></a><span data-ttu-id="65bc4-102">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="65bc4-102">Securing Services and Clients</span></span>
<span data-ttu-id="65bc4-103">Informace v této části se zaměřují na zabezpečení programování v Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="65bc4-103">The information in this section focuses on programming security in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="65bc4-104">Obecně to zahrnuje výběr vhodné vazby ze systému, nastavení vlastností elementu zabezpečení a nastavení vlastností chování služby, které určují, jak jsou načteny přihlašovací údaje pro použití buď pomocí služby, nebo klienta.</span><span class="sxs-lookup"><span data-stu-id="65bc4-104">Generally, this includes selecting an appropriate system-provided binding, setting the properties of the security element, and then setting properties of the service behaviors that govern how credentials are retrieved for use by either the service or the client.</span></span> <span data-ttu-id="65bc4-105">Tyto postupy pokrývají požadavky na zabezpečení většiny uživatelů pro většinu scénářů, jak je znázorněno v [běžných scénářích zabezpečení](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md).</span><span class="sxs-lookup"><span data-stu-id="65bc4-105">These techniques cover the security requirements of most users for most scenarios, as shown in [Common Security Scenarios](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md).</span></span> <span data-ttu-id="65bc4-106">Pokud váš scénář vyžaduje více možností, napřed si přečtěte [Možnosti zabezpečení s vlastními vazbami](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md). Pokud řešení není zřejmé, přečtěte si téma [rozšíření zabezpečení](../../../../docs/framework/wcf/extending/extending-security.md).</span><span class="sxs-lookup"><span data-stu-id="65bc4-106">If your scenario requires more capabilities, first see [Security Capabilities with Custom Bindings](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md); if a solution is not apparent, see [Extending Security](../../../../docs/framework/wcf/extending/extending-security.md).</span></span> <span data-ttu-id="65bc4-107">Pokud vytváříte (nebo pracujete s) systémem, který používá bohatou deklaraci identity, přečtěte si témata v části [autorizace](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="65bc4-107">If you are creating (or interoperating with) a system that uses rich claims, see the topics in [Authorization](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="65bc4-108">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="65bc4-108">In This Section</span></span>  
 [<span data-ttu-id="65bc4-109">Programování zabezpečení WCF</span><span class="sxs-lookup"><span data-stu-id="65bc4-109">Programming WCF Security</span></span>](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)  
 <span data-ttu-id="65bc4-110">Přehled programovacího modelu používaného pro zabezpečení zpráv.</span><span class="sxs-lookup"><span data-stu-id="65bc4-110">An overview of the programming model used to secure messages.</span></span>  
  
 [<span data-ttu-id="65bc4-111">Přehled zabezpečení přenosu</span><span class="sxs-lookup"><span data-stu-id="65bc4-111">Transport Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/transport-security-overview.md)  
 <span data-ttu-id="65bc4-112">Přehled, jak zabezpečit zprávy přes přenosovou vrstvu.</span><span class="sxs-lookup"><span data-stu-id="65bc4-112">An overview of how to secure messages through the transport layer.</span></span>  
  
 [<span data-ttu-id="65bc4-113">Zabezpečení zpráv</span><span class="sxs-lookup"><span data-stu-id="65bc4-113">Message Security</span></span>](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)  
 <span data-ttu-id="65bc4-114">Shrnuje důvody pro použití zabezpečení na úrovni zprávy v Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="65bc4-114">Summarizes reasons for using message-level security in Windows Communication Foundation (WCF).</span></span>  
  
 [<span data-ttu-id="65bc4-115">Zabezpečené relace</span><span class="sxs-lookup"><span data-stu-id="65bc4-115">Secure Sessions</span></span>](../../../../docs/framework/wcf/feature-details/secure-sessions.md)  
 <span data-ttu-id="65bc4-116">Diskuze o požadavcích požadovaných při zabezpečení relace WCF.</span><span class="sxs-lookup"><span data-stu-id="65bc4-116">A discussion of the considerations required when securing a WCF session.</span></span>  
  
 [<span data-ttu-id="65bc4-117">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="65bc4-117">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 <span data-ttu-id="65bc4-118">Vysvětlení některých běžných úloh, které jsou vyžadovány při použití certifikátů X. 509.</span><span class="sxs-lookup"><span data-stu-id="65bc4-118">An explanation of some of the common tasks required when using X.509 certificates.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="65bc4-119">Referenční informace</span><span class="sxs-lookup"><span data-stu-id="65bc4-119">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Security>  
  
## <a name="related-sections"></a><span data-ttu-id="65bc4-120">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="65bc4-120">Related Sections</span></span>  
 [<span data-ttu-id="65bc4-121">Koncepty zabezpečení</span><span class="sxs-lookup"><span data-stu-id="65bc4-121">Security Concepts</span></span>](../../../../docs/framework/wcf/feature-details/security-concepts.md)  
  
 [<span data-ttu-id="65bc4-122">Rozšíření zabezpečení</span><span class="sxs-lookup"><span data-stu-id="65bc4-122">Extending Security</span></span>](../../../../docs/framework/wcf/extending/extending-security.md)  
  
 [<span data-ttu-id="65bc4-123">Běžné scénáře zabezpečení</span><span class="sxs-lookup"><span data-stu-id="65bc4-123">Common Security Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)  
  
 [<span data-ttu-id="65bc4-124">Vazby a zabezpečení</span><span class="sxs-lookup"><span data-stu-id="65bc4-124">Bindings and Security</span></span>](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)  
  
 [<span data-ttu-id="65bc4-125">Možnosti zabezpečení u vlastních vazeb</span><span class="sxs-lookup"><span data-stu-id="65bc4-125">Security Capabilities with Custom Bindings</span></span>](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
  
 [<span data-ttu-id="65bc4-126">Rozšíření zabezpečení</span><span class="sxs-lookup"><span data-stu-id="65bc4-126">Extending Security</span></span>](../../../../docs/framework/wcf/extending/extending-security.md)  
  
 [<span data-ttu-id="65bc4-127">Autorizace</span><span class="sxs-lookup"><span data-stu-id="65bc4-127">Authorization</span></span>](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
  
## <a name="see-also"></a><span data-ttu-id="65bc4-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="65bc4-128">See also</span></span>

- [<span data-ttu-id="65bc4-129">Základní programování WCF</span><span class="sxs-lookup"><span data-stu-id="65bc4-129">Basic WCF Programming</span></span>](../../../../docs/framework/wcf/basic-wcf-programming.md)
- <span data-ttu-id="65bc4-130">[Model zabezpečení pro Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="65bc4-130">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
