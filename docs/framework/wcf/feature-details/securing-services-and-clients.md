---
title: Zabezpečení služeb a klientů
ms.date: 03/30/2017
helpviewer_keywords:
- message security [WCF]
ms.assetid: e681f3bd-0c09-4a58-b0e4-0ecbdf1aa6c7
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 60aa4da95666de01daa087c4c8e826c8cf72ba85
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2018
ms.locfileid: "45583713"
---
# <a name="securing-services-and-clients"></a><span data-ttu-id="f4ea7-102">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="f4ea7-102">Securing Services and Clients</span></span>
<span data-ttu-id="f4ea7-103">Informace v této části se zaměřuje na programování zabezpečení ve Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="f4ea7-103">The information in this section focuses on programming security in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="f4ea7-104">Obvykle to zahrnuje výběrem příslušné vazeb poskytovaných systémem, nastavení vlastnosti elementu zabezpečení a upravením vlastnosti chování služby, které určují, jak načíst přihlašovací údaje pro použití služba nebo klient.</span><span class="sxs-lookup"><span data-stu-id="f4ea7-104">Generally, this includes selecting an appropriate system-provided binding, setting the properties of the security element, and then setting properties of the service behaviors that govern how credentials are retrieved for use by either the service or the client.</span></span> <span data-ttu-id="f4ea7-105">Tyto postupy zahrnují požadavky na zabezpečení většiny uživatelů pro většinu scénářů, jak je znázorněno v [běžné scénáře zabezpečení](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md).</span><span class="sxs-lookup"><span data-stu-id="f4ea7-105">These techniques cover the security requirements of most users for most scenarios, as shown in [Common Security Scenarios](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md).</span></span> <span data-ttu-id="f4ea7-106">Pokud váš scénář vyžaduje další možnosti, nejprve zobrazí [možnosti zabezpečení u vlastních vazeb](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md); Pokud řešení není zřejmé, naleznete v tématu [rozšíření zabezpečení](../../../../docs/framework/wcf/extending/extending-security.md).</span><span class="sxs-lookup"><span data-stu-id="f4ea7-106">If your scenario requires more capabilities, first see [Security Capabilities with Custom Bindings](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md); if a solution is not apparent, see [Extending Security](../../../../docs/framework/wcf/extending/extending-security.md).</span></span> <span data-ttu-id="f4ea7-107">Při vytváření (nebo spolupráce s) systému, který používá bohaté deklarace identity, najdete v tématech [autorizace](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="f4ea7-107">If you are creating (or interoperating with) a system that uses rich claims, see the topics in [Authorization](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f4ea7-108">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="f4ea7-108">In This Section</span></span>  
 [<span data-ttu-id="f4ea7-109">Programování zabezpečení WCF</span><span class="sxs-lookup"><span data-stu-id="f4ea7-109">Programming WCF Security</span></span>](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)  
 <span data-ttu-id="f4ea7-110">Přehled programovacího modelu sloužící k zabezpečení zprávy.</span><span class="sxs-lookup"><span data-stu-id="f4ea7-110">An overview of the programming model used to secure messages.</span></span>  
  
 [<span data-ttu-id="f4ea7-111">Přehled zabezpečení přenosu</span><span class="sxs-lookup"><span data-stu-id="f4ea7-111">Transport Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/transport-security-overview.md)  
 <span data-ttu-id="f4ea7-112">Přehled zabezpečení zpráv pomocí přenosové vrstvy.</span><span class="sxs-lookup"><span data-stu-id="f4ea7-112">An overview of how to secure messages through the transport layer.</span></span>  
  
 [<span data-ttu-id="f4ea7-113">Zabezpečení zpráv</span><span class="sxs-lookup"><span data-stu-id="f4ea7-113">Message Security</span></span>](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)  
 <span data-ttu-id="f4ea7-114">Shrnuje důvodů pro použití zabezpečení na úrovni zpráv Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="f4ea7-114">Summarizes reasons for using message-level security in Windows Communication Foundation (WCF).</span></span>  
  
 [<span data-ttu-id="f4ea7-115">Zabezpečené relace</span><span class="sxs-lookup"><span data-stu-id="f4ea7-115">Secure Sessions</span></span>](../../../../docs/framework/wcf/feature-details/secure-sessions.md)  
 <span data-ttu-id="f4ea7-116">Diskuze nad aspekty zabezpečení WCF relaci je vyžadována.</span><span class="sxs-lookup"><span data-stu-id="f4ea7-116">A discussion of the considerations required when securing a WCF session.</span></span>  
  
 [<span data-ttu-id="f4ea7-117">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="f4ea7-117">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 <span data-ttu-id="f4ea7-118">Vysvětlení některých běžných úloh potřebných při použití certifikátů X.509.</span><span class="sxs-lookup"><span data-stu-id="f4ea7-118">An explanation of some of the common tasks required when using X.509 certificates.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="f4ea7-119">Odkaz</span><span class="sxs-lookup"><span data-stu-id="f4ea7-119">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Security>  
  
## <a name="related-sections"></a><span data-ttu-id="f4ea7-120">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="f4ea7-120">Related Sections</span></span>  
 [<span data-ttu-id="f4ea7-121">Koncepty zabezpečení</span><span class="sxs-lookup"><span data-stu-id="f4ea7-121">Security Concepts</span></span>](../../../../docs/framework/wcf/feature-details/security-concepts.md)  
  
 [<span data-ttu-id="f4ea7-122">Rozšíření zabezpečení</span><span class="sxs-lookup"><span data-stu-id="f4ea7-122">Extending Security</span></span>](../../../../docs/framework/wcf/extending/extending-security.md)  
  
 [<span data-ttu-id="f4ea7-123">Běžné scénáře zabezpečení</span><span class="sxs-lookup"><span data-stu-id="f4ea7-123">Common Security Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)  
  
 [<span data-ttu-id="f4ea7-124">Vazby a zabezpečení</span><span class="sxs-lookup"><span data-stu-id="f4ea7-124">Bindings and Security</span></span>](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)  
  
 [<span data-ttu-id="f4ea7-125">Možnosti zabezpečení u vlastních vazeb</span><span class="sxs-lookup"><span data-stu-id="f4ea7-125">Security Capabilities with Custom Bindings</span></span>](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
  
 [<span data-ttu-id="f4ea7-126">Rozšíření zabezpečení</span><span class="sxs-lookup"><span data-stu-id="f4ea7-126">Extending Security</span></span>](../../../../docs/framework/wcf/extending/extending-security.md)  
  
 [<span data-ttu-id="f4ea7-127">Autorizace</span><span class="sxs-lookup"><span data-stu-id="f4ea7-127">Authorization</span></span>](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
  
## <a name="see-also"></a><span data-ttu-id="f4ea7-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="f4ea7-128">See Also</span></span>  
 [<span data-ttu-id="f4ea7-129">Základní programování WCF</span><span class="sxs-lookup"><span data-stu-id="f4ea7-129">Basic WCF Programming</span></span>](../../../../docs/framework/wcf/basic-wcf-programming.md)  
 [<span data-ttu-id="f4ea7-130">Model zabezpečení pro Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="f4ea7-130">Security Model for Windows Server App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
