---
title: "Konfigurace služeb"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuration [WCF]
ms.assetid: beac771e-f28e-4f84-9ff1-ad9251c726d3
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 857ec77e54d6a55bde1a94fd9fd5758ef7a24309
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="configuring-services"></a><span data-ttu-id="22708-102">Konfigurace služeb</span><span class="sxs-lookup"><span data-stu-id="22708-102">Configuring Services</span></span>
<span data-ttu-id="22708-103">Jakmile určené a implementovat vaše kontrakt služby, jste připraveni ke konfiguraci služby.</span><span class="sxs-lookup"><span data-stu-id="22708-103">Once you have designed and implemented your service contract, you are ready to configure your service.</span></span> <span data-ttu-id="22708-104">Toto je, kde definice a přizpůsobení, jak je vystaven služby pro klienty, včetně zadání adresy, kde se nachází, zprávy, který se používá k odesílání a přijímání zpráv a typ zabezpečení, která vyžaduje kódování a přenos.</span><span class="sxs-lookup"><span data-stu-id="22708-104">This is where you define and customize how your service is exposed to clients, including specifying the address where it can be found, the transport and message encoding it uses to send and receive messages, and the type of security it requires.</span></span>  
  
 <span data-ttu-id="22708-105">Konfigurace použitý zde zahrnuje všechny způsoby, imperativní v kódu nebo pomocí konfiguračního souboru, ve kterém můžete definovat a přizpůsobit různé aspekty služby, například určení jeho adresy koncových bodů, přenosy použít a schémata jeho zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="22708-105">Configuration as used here includes all the ways, imperatively in code or by using a configuration file, in which you can define and customize the various aspects of a service, such as specifying its endpoint addresses, the transports used, and its security schemes.</span></span> <span data-ttu-id="22708-106">V praxi, zápis konfigurace je hlavní část programování [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] aplikací.</span><span class="sxs-lookup"><span data-stu-id="22708-106">In practice, writing configuration is a major part of programming [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] applications.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="22708-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="22708-107">In This Section</span></span>  
 [<span data-ttu-id="22708-108">Zjednodušená konfigurace</span><span class="sxs-lookup"><span data-stu-id="22708-108">Simplified Configuration</span></span>](../../../docs/framework/wcf/simplified-configuration.md)  
 <span data-ttu-id="22708-109">Počínaje [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)], [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] se dodává s nový model výchozí konfigurace, který zjednodušuje [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] požadavky na konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="22708-109">Starting with [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)], [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] comes with a new default configuration model that simplifies [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] configuration requirements.</span></span> <span data-ttu-id="22708-110">Pokud nezadáte žádné [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] konfigurace pro konkrétní službu, modul runtime automaticky nakonfiguruje vaši službu s výchozí koncové body, vazby a chování.</span><span class="sxs-lookup"><span data-stu-id="22708-110">If you do not provide any [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] configuration for a particular service, the runtime automatically configures your service with default endpoints, bindings, and behaviors.</span></span>  
  
 [<span data-ttu-id="22708-111">Konfigurace služeb pomocí konfiguračních souborů</span><span class="sxs-lookup"><span data-stu-id="22708-111">Configuring Services Using Configuration Files</span></span>](../../../docs/framework/wcf/configuring-services-using-configuration-files.md)  
 <span data-ttu-id="22708-112">A [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] služba je konfigurovatelná pomocí [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] technologie konfigurace.</span><span class="sxs-lookup"><span data-stu-id="22708-112">A [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] service is configurable using the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] configuration technology.</span></span> <span data-ttu-id="22708-113">Nejčastěji, jsou přidány elementy XML v souboru Web.config pro stránku Internetové informační služby (IIS), který je hostitelem [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] služby.</span><span class="sxs-lookup"><span data-stu-id="22708-113">Most commonly, XML elements are added to the Web.config file for an Internet Information Services (IIS) site that hosts a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service.</span></span> <span data-ttu-id="22708-114">Prvky umožňují změnit podrobnosti, např. adresy koncových bodů (skutečná adresami používaný ke komunikaci se službou) na základě počítače podle počítače.</span><span class="sxs-lookup"><span data-stu-id="22708-114">The elements allow you to change details, such as the endpoint addresses (the actual addresses used to communicate with the service) on a machine-by-machine basis.</span></span>  
  
 [<span data-ttu-id="22708-115">Vazby</span><span class="sxs-lookup"><span data-stu-id="22708-115">Bindings</span></span>](../../../docs/framework/wcf/bindings.md)  
 <span data-ttu-id="22708-116">Kromě toho [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] zahrnuje několik běžných konfigurací poskytované systémem ve formě vazby, které vám umožní rychle vybrat nejzákladnější funkce pro jak klientem a službou komunikovat, jako je například přenosy, zabezpečení a kódování zpráv použít.</span><span class="sxs-lookup"><span data-stu-id="22708-116">In addition, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] includes several system-provided common configurations in the form of bindings that allow you to quickly select the most basic features for how a client and service communicate, such as the transports, security, and message encodings used.</span></span>  
  
 [<span data-ttu-id="22708-117">Koncové body</span><span class="sxs-lookup"><span data-stu-id="22708-117">Endpoints</span></span>](../../../docs/framework/wcf/endpoints.md)  
 <span data-ttu-id="22708-118">Veškerá komunikace s [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] služby dojde k prostřednictvím *koncové body* služby.</span><span class="sxs-lookup"><span data-stu-id="22708-118">All communication with a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service occurs through the *endpoints* of the service.</span></span> <span data-ttu-id="22708-119">Koncové body obsahovat kontrakt, informace o konfiguraci, který je uveden v vazeb a adresy, které označují, kde se služba nebo kde můžete získat informace o službě.</span><span class="sxs-lookup"><span data-stu-id="22708-119">Endpoints contain the contract, the configuration information that is specified in the bindings, and the addresses that indicate where to find the service or where to obtain information about the service.</span></span>  
  
 [<span data-ttu-id="22708-120">Zabezpečení služeb</span><span class="sxs-lookup"><span data-stu-id="22708-120">Securing Services</span></span>](../../../docs/framework/wcf/securing-services.md)  
 <span data-ttu-id="22708-121">Pomocí [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] a existující mechanismy zabezpečení, můžete implementovat důvěrnost, integritu, ověřování a autorizace do jakékoli služby.</span><span class="sxs-lookup"><span data-stu-id="22708-121">Using [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] and existing security mechanisms, you can implement confidentiality, integrity, authentication, and authorization into any service.</span></span> <span data-ttu-id="22708-122">Také můžete auditovat pro zabezpečení úspěchy a selhání.</span><span class="sxs-lookup"><span data-stu-id="22708-122">You can also audit for security successes and failures.</span></span>  
  
 [<span data-ttu-id="22708-123">Vytváření interoperabilních služeb WS-I Basic Profile 1.1</span><span class="sxs-lookup"><span data-stu-id="22708-123">Creating WS-I Basic Profile 1.1 Interoperable Services</span></span>](../../../docs/framework/wcf/creating-ws-i-basic-profile-1-1-interoperable-services.md)  
 <span data-ttu-id="22708-124">Požadavky na nasazení služby, který je vzájemná spolupráce s služeb a klientů na všechny platformy a operačního systému jsou uvedeny v WS-I Basic Profile 1.1 specifikace.</span><span class="sxs-lookup"><span data-stu-id="22708-124">The requirements for deploying a service that is interoperable with services and clients on any other platform or operating system are outlined in the WS-I Basic Profile 1.1 specification.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="22708-125">Odkaz</span><span class="sxs-lookup"><span data-stu-id="22708-125">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Description>  
  
## <a name="related-sections"></a><span data-ttu-id="22708-126">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="22708-126">Related Sections</span></span>  
 [<span data-ttu-id="22708-127">Základní programovací životní cyklus</span><span class="sxs-lookup"><span data-stu-id="22708-127">Basic Programming Lifecycle</span></span>](../../../docs/framework/wcf/basic-programming-lifecycle.md)  
  
 [<span data-ttu-id="22708-128">Navrhování a implementace služeb</span><span class="sxs-lookup"><span data-stu-id="22708-128">Designing and Implementing Services</span></span>](../../../docs/framework/wcf/designing-and-implementing-services.md)  
  
 [<span data-ttu-id="22708-129">Služby hostování</span><span class="sxs-lookup"><span data-stu-id="22708-129">Hosting Services</span></span>](../../../docs/framework/wcf/hosting-services.md)  
  
 [<span data-ttu-id="22708-130">Sestavování klientů</span><span class="sxs-lookup"><span data-stu-id="22708-130">Building Clients</span></span>](../../../docs/framework/wcf/building-clients.md)  
  
 [<span data-ttu-id="22708-131">Úvod do rozšířitelnosti</span><span class="sxs-lookup"><span data-stu-id="22708-131">Introduction to Extensibility</span></span>](../../../docs/framework/wcf/introduction-to-extensibility.md)  
  
 [<span data-ttu-id="22708-132">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="22708-132">Administration and Diagnostics</span></span>](../../../docs/framework/wcf/diagnostics/index.md)  
  
## <a name="see-also"></a><span data-ttu-id="22708-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="22708-133">See Also</span></span>  
 [<span data-ttu-id="22708-134">Základní programování WCF</span><span class="sxs-lookup"><span data-stu-id="22708-134">Basic WCF Programming</span></span>](../../../docs/framework/wcf/basic-wcf-programming.md)  
 [<span data-ttu-id="22708-135">Koncepční přehled</span><span class="sxs-lookup"><span data-stu-id="22708-135">Conceptual Overview</span></span>](../../../docs/framework/wcf/conceptual-overview.md)  
 [<span data-ttu-id="22708-136">Podrobnosti o funkcích WCF</span><span class="sxs-lookup"><span data-stu-id="22708-136">WCF Feature Details</span></span>](../../../docs/framework/wcf/feature-details/index.md)
