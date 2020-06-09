---
title: Zabezpečení služeb a klientů
ms.date: 03/30/2017
helpviewer_keywords:
- message security [WCF]
ms.assetid: e681f3bd-0c09-4a58-b0e4-0ecbdf1aa6c7
ms.openlocfilehash: db0a0dcfbe04a7b7dbfabfed59f9b8637d0a2797
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84586205"
---
# <a name="securing-services-and-clients"></a><span data-ttu-id="2409c-102">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="2409c-102">Securing Services and Clients</span></span>
<span data-ttu-id="2409c-103">Informace v této části se zaměřují na zabezpečení programování v Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="2409c-103">The information in this section focuses on programming security in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="2409c-104">Obecně to zahrnuje výběr vhodné vazby ze systému, nastavení vlastností elementu zabezpečení a nastavení vlastností chování služby, které určují, jak jsou načteny přihlašovací údaje pro použití buď pomocí služby, nebo klienta.</span><span class="sxs-lookup"><span data-stu-id="2409c-104">Generally, this includes selecting an appropriate system-provided binding, setting the properties of the security element, and then setting properties of the service behaviors that govern how credentials are retrieved for use by either the service or the client.</span></span> <span data-ttu-id="2409c-105">Tyto postupy pokrývají požadavky na zabezpečení většiny uživatelů pro většinu scénářů, jak je znázorněno v [běžných scénářích zabezpečení](common-security-scenarios.md).</span><span class="sxs-lookup"><span data-stu-id="2409c-105">These techniques cover the security requirements of most users for most scenarios, as shown in [Common Security Scenarios](common-security-scenarios.md).</span></span> <span data-ttu-id="2409c-106">Pokud váš scénář vyžaduje více možností, napřed si přečtěte [Možnosti zabezpečení s vlastními vazbami](security-capabilities-with-custom-bindings.md). Pokud řešení není zřejmé, přečtěte si téma [rozšíření zabezpečení](../extending/extending-security.md).</span><span class="sxs-lookup"><span data-stu-id="2409c-106">If your scenario requires more capabilities, first see [Security Capabilities with Custom Bindings](security-capabilities-with-custom-bindings.md); if a solution is not apparent, see [Extending Security](../extending/extending-security.md).</span></span> <span data-ttu-id="2409c-107">Pokud vytváříte (nebo pracujete s) systémem, který používá bohatou deklaraci identity, přečtěte si témata v části [autorizace](authorization-in-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="2409c-107">If you are creating (or interoperating with) a system that uses rich claims, see the topics in [Authorization](authorization-in-wcf.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2409c-108">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="2409c-108">In This Section</span></span>  
 [<span data-ttu-id="2409c-109">Programování zabezpečení WCF</span><span class="sxs-lookup"><span data-stu-id="2409c-109">Programming WCF Security</span></span>](programming-wcf-security.md)  
 <span data-ttu-id="2409c-110">Přehled programovacího modelu používaného pro zabezpečení zpráv.</span><span class="sxs-lookup"><span data-stu-id="2409c-110">An overview of the programming model used to secure messages.</span></span>  
  
 [<span data-ttu-id="2409c-111">Přehled zabezpečení přenosu</span><span class="sxs-lookup"><span data-stu-id="2409c-111">Transport Security Overview</span></span>](transport-security-overview.md)  
 <span data-ttu-id="2409c-112">Přehled, jak zabezpečit zprávy přes přenosovou vrstvu.</span><span class="sxs-lookup"><span data-stu-id="2409c-112">An overview of how to secure messages through the transport layer.</span></span>  
  
 [<span data-ttu-id="2409c-113">Zabezpečení zpráv</span><span class="sxs-lookup"><span data-stu-id="2409c-113">Message Security</span></span>](message-security-in-wcf.md)  
 <span data-ttu-id="2409c-114">Shrnuje důvody pro použití zabezpečení na úrovni zprávy v Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="2409c-114">Summarizes reasons for using message-level security in Windows Communication Foundation (WCF).</span></span>  
  
 [<span data-ttu-id="2409c-115">Zabezpečené relace</span><span class="sxs-lookup"><span data-stu-id="2409c-115">Secure Sessions</span></span>](secure-sessions.md)  
 <span data-ttu-id="2409c-116">Diskuze o požadavcích požadovaných při zabezpečení relace WCF.</span><span class="sxs-lookup"><span data-stu-id="2409c-116">A discussion of the considerations required when securing a WCF session.</span></span>  
  
 [<span data-ttu-id="2409c-117">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="2409c-117">Working with Certificates</span></span>](working-with-certificates.md)  
 <span data-ttu-id="2409c-118">Vysvětlení některých běžných úloh, které jsou vyžadovány při použití certifikátů X. 509.</span><span class="sxs-lookup"><span data-stu-id="2409c-118">An explanation of some of the common tasks required when using X.509 certificates.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="2409c-119">Referenční informace</span><span class="sxs-lookup"><span data-stu-id="2409c-119">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Security>  
  
## <a name="related-sections"></a><span data-ttu-id="2409c-120">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="2409c-120">Related Sections</span></span>  
 [<span data-ttu-id="2409c-121">Koncepce zabezpečení</span><span class="sxs-lookup"><span data-stu-id="2409c-121">Security Concepts</span></span>](security-concepts.md)  
  
 [<span data-ttu-id="2409c-122">Rozšíření zabezpečení</span><span class="sxs-lookup"><span data-stu-id="2409c-122">Extending Security</span></span>](../extending/extending-security.md)  
  
 [<span data-ttu-id="2409c-123">Běžné scénáře zabezpečení</span><span class="sxs-lookup"><span data-stu-id="2409c-123">Common Security Scenarios</span></span>](common-security-scenarios.md)  
  
 [<span data-ttu-id="2409c-124">Vazby a zabezpečení</span><span class="sxs-lookup"><span data-stu-id="2409c-124">Bindings and Security</span></span>](bindings-and-security.md)  
  
 [<span data-ttu-id="2409c-125">Možnosti zabezpečení u vlastních vazeb</span><span class="sxs-lookup"><span data-stu-id="2409c-125">Security Capabilities with Custom Bindings</span></span>](security-capabilities-with-custom-bindings.md)  
  
 [<span data-ttu-id="2409c-126">Rozšíření zabezpečení</span><span class="sxs-lookup"><span data-stu-id="2409c-126">Extending Security</span></span>](../extending/extending-security.md)  
  
 [<span data-ttu-id="2409c-127">Autorizace</span><span class="sxs-lookup"><span data-stu-id="2409c-127">Authorization</span></span>](authorization-in-wcf.md)  
  
## <a name="see-also"></a><span data-ttu-id="2409c-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="2409c-128">See also</span></span>

- [<span data-ttu-id="2409c-129">Základní programování WCF</span><span class="sxs-lookup"><span data-stu-id="2409c-129">Basic WCF Programming</span></span>](../basic-wcf-programming.md)
- <span data-ttu-id="2409c-130">[Model zabezpečení pro Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="2409c-130">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
