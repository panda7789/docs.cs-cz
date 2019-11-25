---
title: Konfigurace služeb WCF
ms.date: 03/30/2017
helpviewer_keywords:
- configuration [WCF]
ms.assetid: beac771e-f28e-4f84-9ff1-ad9251c726d3
ms.openlocfilehash: 332a88530010197187ca3ea787e152b0c95a5514
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141595"
---
# <a name="configuring-wcf-services"></a><span data-ttu-id="6a3f1-102">Konfigurace služeb WCF</span><span class="sxs-lookup"><span data-stu-id="6a3f1-102">Configuring WCF services</span></span>

<span data-ttu-id="6a3f1-103">Po navržení a implementaci kontraktu služby jste připraveni ke konfiguraci služby.</span><span class="sxs-lookup"><span data-stu-id="6a3f1-103">Once you have designed and implemented your service contract, you are ready to configure your service.</span></span> <span data-ttu-id="6a3f1-104">Tady je místo, kde definujete a přizpůsobíte, jak je vaše služba vystavena klientům, včetně určení adresy, kde se dá najít, přenos a kódování zpráv, které používá k odesílání a přijímání zpráv, a o typu zabezpečení, které vyžaduje.</span><span class="sxs-lookup"><span data-stu-id="6a3f1-104">This is where you define and customize how your service is exposed to clients, including specifying the address where it can be found, the transport and message encoding it uses to send and receive messages, and the type of security it requires.</span></span>  
  
 <span data-ttu-id="6a3f1-105">Zde uvedená konfigurace zahrnuje všechny způsoby, imperativně v kódu nebo pomocí konfiguračního souboru, ve kterém můžete definovat a přizpůsobit různé aspekty služby, například zadání adres koncových bodů, používaných přenosů a jejich schémat zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="6a3f1-105">Configuration as used here includes all the ways, imperatively in code or by using a configuration file, in which you can define and customize the various aspects of a service, such as specifying its endpoint addresses, the transports used, and its security schemes.</span></span> <span data-ttu-id="6a3f1-106">V praxi je psaní konfigurace hlavní součástí programování aplikací WCF.</span><span class="sxs-lookup"><span data-stu-id="6a3f1-106">In practice, writing configuration is a major part of programming WCF applications.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6a3f1-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="6a3f1-107">In This Section</span></span>  
 [<span data-ttu-id="6a3f1-108">Zjednodušená konfigurace</span><span class="sxs-lookup"><span data-stu-id="6a3f1-108">Simplified Configuration</span></span>](simplified-configuration.md)  
 <span data-ttu-id="6a3f1-109">Počínaje .NET Framework 4 přichází WCF k dispozici nový výchozí konfigurační model, který zjednodušuje požadavky na konfiguraci WCF.</span><span class="sxs-lookup"><span data-stu-id="6a3f1-109">Starting with .NET Framework 4, WCF comes with a new default configuration model that simplifies WCF configuration requirements.</span></span> <span data-ttu-id="6a3f1-110">Pokud neposkytnete konfiguraci služby WCF pro konkrétní službu, modul runtime automaticky nakonfiguruje vaši službu s výchozími koncovými body, vazbami a chováními.</span><span class="sxs-lookup"><span data-stu-id="6a3f1-110">If you do not provide any WCF configuration for a particular service, the runtime automatically configures your service with default endpoints, bindings, and behaviors.</span></span>  
  
 [<span data-ttu-id="6a3f1-111">Konfigurace služeb pomocí konfiguračních souborů</span><span class="sxs-lookup"><span data-stu-id="6a3f1-111">Configuring Services Using Configuration Files</span></span>](configuring-services-using-configuration-files.md)  
 <span data-ttu-id="6a3f1-112">Službu Windows Communication Foundation (WCF) lze konfigurovat pomocí technologie .NET Framework konfigurace.</span><span class="sxs-lookup"><span data-stu-id="6a3f1-112">A Windows Communication Foundation (WCF) service is configurable using the .NET Framework configuration technology.</span></span> <span data-ttu-id="6a3f1-113">Nejčastěji se prvky XML přidávají do souboru Web. config pro web Internetová informační služba (IIS), který je hostitelem služby WCF.</span><span class="sxs-lookup"><span data-stu-id="6a3f1-113">Most commonly, XML elements are added to the Web.config file for an Internet Information Services (IIS) site that hosts a WCF service.</span></span> <span data-ttu-id="6a3f1-114">Tyto prvky umožňují změnit podrobnosti, jako jsou adresy koncových bodů (skutečné adresy používané ke komunikaci se službou) na počítačích jednotlivých počítačů.</span><span class="sxs-lookup"><span data-stu-id="6a3f1-114">The elements allow you to change details, such as the endpoint addresses (the actual addresses used to communicate with the service) on a machine-by-machine basis.</span></span>  
  
 [<span data-ttu-id="6a3f1-115">Vazby</span><span class="sxs-lookup"><span data-stu-id="6a3f1-115">Bindings</span></span>](bindings.md)  
 <span data-ttu-id="6a3f1-116">Kromě toho WCF zahrnuje několik běžných konfigurací poskytovaných systémem ve formě vazeb, které vám umožní rychle vybrat základní funkce pro komunikaci klientů a služeb, jako jsou třeba přenosy, zabezpečení a kódování zpráv.</span><span class="sxs-lookup"><span data-stu-id="6a3f1-116">In addition, WCF includes several system-provided common configurations in the form of bindings that allow you to quickly select the most basic features for how a client and service communicate, such as the transports, security, and message encodings used.</span></span>  
  
 [<span data-ttu-id="6a3f1-117">Koncové body</span><span class="sxs-lookup"><span data-stu-id="6a3f1-117">Endpoints</span></span>](endpoints.md)  
 <span data-ttu-id="6a3f1-118">Veškerá komunikace se službou WCF probíhá prostřednictvím *koncových bodů* služby.</span><span class="sxs-lookup"><span data-stu-id="6a3f1-118">All communication with a WCF service occurs through the *endpoints* of the service.</span></span> <span data-ttu-id="6a3f1-119">Koncové body obsahují kontrakt, informace o konfiguraci, které jsou zadány ve vazbách, a adresy, které označují, kde se služba nachází, nebo kde získat informace o službě.</span><span class="sxs-lookup"><span data-stu-id="6a3f1-119">Endpoints contain the contract, the configuration information that is specified in the bindings, and the addresses that indicate where to find the service or where to obtain information about the service.</span></span>  
  
 [<span data-ttu-id="6a3f1-120">Zabezpečení služeb</span><span class="sxs-lookup"><span data-stu-id="6a3f1-120">Securing Services</span></span>](securing-services.md)  
 <span data-ttu-id="6a3f1-121">Pomocí WCF a stávajících mechanismů zabezpečení můžete implementovat do jakékoli služby důvěrnost, integritu, ověřování a autorizaci.</span><span class="sxs-lookup"><span data-stu-id="6a3f1-121">Using WCF and existing security mechanisms, you can implement confidentiality, integrity, authentication, and authorization into any service.</span></span> <span data-ttu-id="6a3f1-122">Můžete také provést audit na úspěšné a neúspěšné zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="6a3f1-122">You can also audit for security successes and failures.</span></span>  
  
 [<span data-ttu-id="6a3f1-123">Vytváření interoperabilních služeb WS-I Basic Profile 1.1</span><span class="sxs-lookup"><span data-stu-id="6a3f1-123">Creating WS-I Basic Profile 1.1 Interoperable Services</span></span>](./creating-ws-i-basic-profile-1-1-interoperable-services.md)  
 <span data-ttu-id="6a3f1-124">Požadavky na nasazení služby, která se vzájemně spolupracují se službami a klienty na jakékoli jiné platformě nebo operačním systémem, jsou uvedené ve specifikaci 1,1 profilu WS-I Basic.</span><span class="sxs-lookup"><span data-stu-id="6a3f1-124">The requirements for deploying a service that is interoperable with services and clients on any other platform or operating system are outlined in the WS-I Basic Profile 1.1 specification.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="6a3f1-125">Odkaz</span><span class="sxs-lookup"><span data-stu-id="6a3f1-125">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Description>  
  
## <a name="related-sections"></a><span data-ttu-id="6a3f1-126">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="6a3f1-126">Related Sections</span></span>  
 [<span data-ttu-id="6a3f1-127">Základní programovací životní cyklus</span><span class="sxs-lookup"><span data-stu-id="6a3f1-127">Basic Programming Lifecycle</span></span>](basic-programming-lifecycle.md)  
  
 [<span data-ttu-id="6a3f1-128">Navrhování a implementace služeb</span><span class="sxs-lookup"><span data-stu-id="6a3f1-128">Designing and Implementing Services</span></span>](designing-and-implementing-services.md)  
  
 [<span data-ttu-id="6a3f1-129">Služby hostování</span><span class="sxs-lookup"><span data-stu-id="6a3f1-129">Hosting Services</span></span>](hosting-services.md)  
  
 [<span data-ttu-id="6a3f1-130">Sestavování klientů</span><span class="sxs-lookup"><span data-stu-id="6a3f1-130">Building Clients</span></span>](building-clients.md)  
  
 [<span data-ttu-id="6a3f1-131">Úvod do rozšířitelnosti</span><span class="sxs-lookup"><span data-stu-id="6a3f1-131">Introduction to Extensibility</span></span>](introduction-to-extensibility.md)  
  
 [<span data-ttu-id="6a3f1-132">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="6a3f1-132">Administration and Diagnostics</span></span>](./diagnostics/index.md)  
  
## <a name="see-also"></a><span data-ttu-id="6a3f1-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6a3f1-133">See also</span></span>

- [<span data-ttu-id="6a3f1-134">Základní programování WCF</span><span class="sxs-lookup"><span data-stu-id="6a3f1-134">Basic WCF Programming</span></span>](basic-wcf-programming.md)
- [<span data-ttu-id="6a3f1-135">Koncepční přehled</span><span class="sxs-lookup"><span data-stu-id="6a3f1-135">Conceptual Overview</span></span>](conceptual-overview.md)
- [<span data-ttu-id="6a3f1-136">Podrobnosti o funkcích WCF</span><span class="sxs-lookup"><span data-stu-id="6a3f1-136">WCF Feature Details</span></span>](./feature-details/index.md)
