---
title: Konfigurace služeb WCF
ms.date: 03/30/2017
helpviewer_keywords:
- configuration [WCF]
ms.assetid: beac771e-f28e-4f84-9ff1-ad9251c726d3
ms.openlocfilehash: e8ac62809b1269ae810f026c003c7611b3ec548c
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65593326"
---
# <a name="configuring-wcf-services"></a><span data-ttu-id="f0bb8-102">Konfigurace služeb WCF</span><span class="sxs-lookup"><span data-stu-id="f0bb8-102">Configuring WCF services</span></span>

<span data-ttu-id="f0bb8-103">Jakmile máte navrženy a implementovány servisní smlouvy, jste připraveni ke konfiguraci služby.</span><span class="sxs-lookup"><span data-stu-id="f0bb8-103">Once you have designed and implemented your service contract, you are ready to configure your service.</span></span> <span data-ttu-id="f0bb8-104">To je, kde definování a přizpůsobení, jak je vaše služba zveřejněné klientům, včetně zadání adresy, kde je možné ji najít, přenos a kódování zpráv, které používá k odesílání a přijímání zpráv a typ zabezpečení, které vyžaduje.</span><span class="sxs-lookup"><span data-stu-id="f0bb8-104">This is where you define and customize how your service is exposed to clients, including specifying the address where it can be found, the transport and message encoding it uses to send and receive messages, and the type of security it requires.</span></span>  
  
 <span data-ttu-id="f0bb8-105">Konfigurace použitý zde zahrnuje všechny způsoby, jak, imperativně v kódu nebo pomocí konfiguračního souboru, ve kterém můžete definovat a přizpůsobení různé aspekty služby, jako je například zadání adresy koncového bodu, přenosy použít a schémata jeho zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="f0bb8-105">Configuration as used here includes all the ways, imperatively in code or by using a configuration file, in which you can define and customize the various aspects of a service, such as specifying its endpoint addresses, the transports used, and its security schemes.</span></span> <span data-ttu-id="f0bb8-106">V praxi, zápis konfigurace je velkou část programování WCF aplikací.</span><span class="sxs-lookup"><span data-stu-id="f0bb8-106">In practice, writing configuration is a major part of programming WCF applications.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f0bb8-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="f0bb8-107">In This Section</span></span>  
 [<span data-ttu-id="f0bb8-108">Zjednodušená konfigurace</span><span class="sxs-lookup"><span data-stu-id="f0bb8-108">Simplified Configuration</span></span>](../../../docs/framework/wcf/simplified-configuration.md)  
 <span data-ttu-id="f0bb8-109">Počínaje [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)], WCF se dodává s novou výchozí konfiguraci modelu, která zjednodušuje požadavky na konfiguraci WCF.</span><span class="sxs-lookup"><span data-stu-id="f0bb8-109">Starting with [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)], WCF comes with a new default configuration model that simplifies WCF configuration requirements.</span></span> <span data-ttu-id="f0bb8-110">Pokud nezadáte žádnou konfiguraci WCF pro konkrétní službu, modul runtime automaticky nakonfiguruje vaši službu s výchozí koncové body, vazby a chování.</span><span class="sxs-lookup"><span data-stu-id="f0bb8-110">If you do not provide any WCF configuration for a particular service, the runtime automatically configures your service with default endpoints, bindings, and behaviors.</span></span>  
  
 [<span data-ttu-id="f0bb8-111">Konfigurace služeb pomocí konfiguračních souborů</span><span class="sxs-lookup"><span data-stu-id="f0bb8-111">Configuring Services Using Configuration Files</span></span>](../../../docs/framework/wcf/configuring-services-using-configuration-files.md)  
 <span data-ttu-id="f0bb8-112">Služba Windows Communication Foundation (WCF) je možné konfigurovat pomocí konfigurace technologie rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f0bb8-112">A Windows Communication Foundation (WCF) service is configurable using the .NET Framework configuration technology.</span></span> <span data-ttu-id="f0bb8-113">Nejčastěji jsou přidány elementy XML v souboru Web.config pro web Internetové informační služby (IIS), který je hostitelem služby WCF.</span><span class="sxs-lookup"><span data-stu-id="f0bb8-113">Most commonly, XML elements are added to the Web.config file for an Internet Information Services (IIS) site that hosts a WCF service.</span></span> <span data-ttu-id="f0bb8-114">Prvky umožňují změnit podrobnosti, jako jsou adresy koncových bodů (skutečné adresy používaný ke komunikaci se službou service) pro počítače podle počítače.</span><span class="sxs-lookup"><span data-stu-id="f0bb8-114">The elements allow you to change details, such as the endpoint addresses (the actual addresses used to communicate with the service) on a machine-by-machine basis.</span></span>  
  
 [<span data-ttu-id="f0bb8-115">Vazby</span><span class="sxs-lookup"><span data-stu-id="f0bb8-115">Bindings</span></span>](../../../docs/framework/wcf/bindings.md)  
 <span data-ttu-id="f0bb8-116">Kromě toho WCF obsahuje několik běžných konfigurací poskytované systémem ve formě vazby, které umožňují rychle vybrat základní funkce pro komunikaci klienta a služby, jako jsou přenosy, zabezpečení a zprávy použít kódování.</span><span class="sxs-lookup"><span data-stu-id="f0bb8-116">In addition, WCF includes several system-provided common configurations in the form of bindings that allow you to quickly select the most basic features for how a client and service communicate, such as the transports, security, and message encodings used.</span></span>  
  
 [<span data-ttu-id="f0bb8-117">Koncové body</span><span class="sxs-lookup"><span data-stu-id="f0bb8-117">Endpoints</span></span>](../../../docs/framework/wcf/endpoints.md)  
 <span data-ttu-id="f0bb8-118">Vyvolá se veškerá komunikace se službou WCF přes *koncové body* služby.</span><span class="sxs-lookup"><span data-stu-id="f0bb8-118">All communication with a WCF service occurs through the *endpoints* of the service.</span></span> <span data-ttu-id="f0bb8-119">Koncové body obsahovat kontrakt, informace o konfiguraci, která je zadána ve vazbách a adresy, které označují, kam chcete najít službu nebo kde můžete získat informace o službě.</span><span class="sxs-lookup"><span data-stu-id="f0bb8-119">Endpoints contain the contract, the configuration information that is specified in the bindings, and the addresses that indicate where to find the service or where to obtain information about the service.</span></span>  
  
 [<span data-ttu-id="f0bb8-120">Zabezpečení služeb</span><span class="sxs-lookup"><span data-stu-id="f0bb8-120">Securing Services</span></span>](../../../docs/framework/wcf/securing-services.md)  
 <span data-ttu-id="f0bb8-121">Pomocí technologie WCF a stávající mechanismy zabezpečení, můžete implementovat důvěrnost, integritu, ověřování a autorizace na libovolnou službu.</span><span class="sxs-lookup"><span data-stu-id="f0bb8-121">Using WCF and existing security mechanisms, you can implement confidentiality, integrity, authentication, and authorization into any service.</span></span> <span data-ttu-id="f0bb8-122">Také můžete auditovat zabezpečení úspěchy a selhání.</span><span class="sxs-lookup"><span data-stu-id="f0bb8-122">You can also audit for security successes and failures.</span></span>  
  
 [<span data-ttu-id="f0bb8-123">Vytváření interoperabilních služeb WS-I Basic Profile 1.1</span><span class="sxs-lookup"><span data-stu-id="f0bb8-123">Creating WS-I Basic Profile 1.1 Interoperable Services</span></span>](../../../docs/framework/wcf/creating-ws-i-basic-profile-1-1-interoperable-services.md)  
 <span data-ttu-id="f0bb8-124">Požadavky na nasazení služby, který je vzájemná spolupráce s služeb a klientů na jakoukoli platformu nebo operační systém jsou uvedeny v WS-I Basic Profile 1.1 specifikace.</span><span class="sxs-lookup"><span data-stu-id="f0bb8-124">The requirements for deploying a service that is interoperable with services and clients on any other platform or operating system are outlined in the WS-I Basic Profile 1.1 specification.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="f0bb8-125">Odkaz</span><span class="sxs-lookup"><span data-stu-id="f0bb8-125">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Description>  
  
## <a name="related-sections"></a><span data-ttu-id="f0bb8-126">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="f0bb8-126">Related Sections</span></span>  
 [<span data-ttu-id="f0bb8-127">Základní programovací životní cyklus</span><span class="sxs-lookup"><span data-stu-id="f0bb8-127">Basic Programming Lifecycle</span></span>](../../../docs/framework/wcf/basic-programming-lifecycle.md)  
  
 [<span data-ttu-id="f0bb8-128">Navrhování a implementace služeb</span><span class="sxs-lookup"><span data-stu-id="f0bb8-128">Designing and Implementing Services</span></span>](../../../docs/framework/wcf/designing-and-implementing-services.md)  
  
 [<span data-ttu-id="f0bb8-129">Služby hostování</span><span class="sxs-lookup"><span data-stu-id="f0bb8-129">Hosting Services</span></span>](../../../docs/framework/wcf/hosting-services.md)  
  
 [<span data-ttu-id="f0bb8-130">Sestavování klientů</span><span class="sxs-lookup"><span data-stu-id="f0bb8-130">Building Clients</span></span>](../../../docs/framework/wcf/building-clients.md)  
  
 [<span data-ttu-id="f0bb8-131">Úvod do rozšířitelnosti</span><span class="sxs-lookup"><span data-stu-id="f0bb8-131">Introduction to Extensibility</span></span>](../../../docs/framework/wcf/introduction-to-extensibility.md)  
  
 [<span data-ttu-id="f0bb8-132">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="f0bb8-132">Administration and Diagnostics</span></span>](../../../docs/framework/wcf/diagnostics/index.md)  
  
## <a name="see-also"></a><span data-ttu-id="f0bb8-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f0bb8-133">See also</span></span>

- [<span data-ttu-id="f0bb8-134">Základní programování WCF</span><span class="sxs-lookup"><span data-stu-id="f0bb8-134">Basic WCF Programming</span></span>](../../../docs/framework/wcf/basic-wcf-programming.md)
- [<span data-ttu-id="f0bb8-135">Koncepční přehled</span><span class="sxs-lookup"><span data-stu-id="f0bb8-135">Conceptual Overview</span></span>](../../../docs/framework/wcf/conceptual-overview.md)
- [<span data-ttu-id="f0bb8-136">Podrobnosti o funkcích WCF</span><span class="sxs-lookup"><span data-stu-id="f0bb8-136">WCF Feature Details</span></span>](../../../docs/framework/wcf/feature-details/index.md)
