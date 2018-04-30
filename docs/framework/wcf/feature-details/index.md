---
title: Podrobnosti o funkcích WCF
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
- features [WCF]
- WCF, features
- Windows Communication Foundation, features
ms.assetid: 9b4368ca-0bd3-40dc-a539-bcd5779cee5f
caps.latest.revision: 22
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 91b22cbcabba95d8cc91ffbc0b74b51e61dae393
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/30/2018
---
# <a name="wcf-feature-details"></a><span data-ttu-id="42a01-102">Podrobnosti o funkcích WCF</span><span class="sxs-lookup"><span data-stu-id="42a01-102">WCF Feature Details</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="42a01-103"> umožňuje rozsáhlé ovládat funkce zasílání zpráv aplikace.</span><span class="sxs-lookup"><span data-stu-id="42a01-103"> allows extensive control over the messaging functions of an application.</span></span> <span data-ttu-id="42a01-104">Témata v této části najdete podrobnosti o dostupných funkcí.</span><span class="sxs-lookup"><span data-stu-id="42a01-104">The topics in this section go into detail about the available features.</span></span> <span data-ttu-id="42a01-105">Další informace o základní programování najdete v tématu [základní programování WCF](../../../../docs/framework/wcf/basic-wcf-programming.md).</span><span class="sxs-lookup"><span data-stu-id="42a01-105">For more information about basic programming, see [Basic WCF Programming](../../../../docs/framework/wcf/basic-wcf-programming.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="42a01-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="42a01-106">In This Section</span></span>  
 [<span data-ttu-id="42a01-107">Služby pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="42a01-107">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 <span data-ttu-id="42a01-108">Popisuje, jak vytvořit a nakonfigurovat služby pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="42a01-108">Describes how to create and configure workflow services.</span></span>  
  
 [<span data-ttu-id="42a01-109">Koncové body: adresy, vazby a kontrakty</span><span class="sxs-lookup"><span data-stu-id="42a01-109">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)  
 <span data-ttu-id="42a01-110">Popisuje, jak řídit několik aspektů služby.</span><span class="sxs-lookup"><span data-stu-id="42a01-110">Describes how to control multiple aspects of your service.</span></span>  
  
 [<span data-ttu-id="42a01-111">Přenos a serializace dat</span><span class="sxs-lookup"><span data-stu-id="42a01-111">Data Transfer and Serialization</span></span>](../../../../docs/framework/wcf/feature-details/data-transfer-and-serialization.md)  
 <span data-ttu-id="42a01-112">Popisuje, jak můžete přizpůsobit serializace dat pro součinnosti nebo budoucí kompatibility.</span><span class="sxs-lookup"><span data-stu-id="42a01-112">Describes how serialization of data can be tailored for interoperation or future compatibility.</span></span>  
  
 [<span data-ttu-id="42a01-113">Relace, vytváření instancí a souběžnost</span><span class="sxs-lookup"><span data-stu-id="42a01-113">Sessions, Instancing, and Concurrency</span></span>](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)  
 <span data-ttu-id="42a01-114">Popisuje vytváření instancí a relace režimy [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] a postup výběru správného režimu pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="42a01-114">Describes the instancing and session modes of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] and how to select the right mode for your application.</span></span>  
  
 [<span data-ttu-id="42a01-115">Přenosy</span><span class="sxs-lookup"><span data-stu-id="42a01-115">Transports</span></span>](../../../../docs/framework/wcf/feature-details/transports.md)  
 <span data-ttu-id="42a01-116">Popisuje postup konfigurace přenosové vrstvy, nejnižší úroveň zásobníku kanálu.</span><span class="sxs-lookup"><span data-stu-id="42a01-116">Describes how to configure the transport layer, the lowest level of the channel stack.</span></span>  
  
 [<span data-ttu-id="42a01-117">Fronty a spolehlivé relace</span><span class="sxs-lookup"><span data-stu-id="42a01-117">Queues and Reliable Sessions</span></span>](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md)  
 <span data-ttu-id="42a01-118">Popisuje front, které ukládají zprávy z odesílající aplikací jménem přijímající aplikace a později předávat tyto zprávy do přijímající aplikace.</span><span class="sxs-lookup"><span data-stu-id="42a01-118">Describes queues, which store messages from a sending application on behalf of a receiving application and later forward these messages to the receiving application.</span></span>  
  
 [<span data-ttu-id="42a01-119">Transakce</span><span class="sxs-lookup"><span data-stu-id="42a01-119">Transactions</span></span>](../../../../docs/framework/wcf/feature-details/transactions-in-wcf.md)  
 <span data-ttu-id="42a01-120">Vysvětluje, jak vytvořit zpracovaných operací, které můžete se vrátit zpět v případě potřeby.</span><span class="sxs-lookup"><span data-stu-id="42a01-120">Explains how to create transacted operations that can be rolled back if needed.</span></span>  
  
 [<span data-ttu-id="42a01-121">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="42a01-121">Security</span></span>](../../../../docs/framework/wcf/feature-details/security.md)  
 <span data-ttu-id="42a01-122">Popisuje, jak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zabezpečení vám pomůže vytvořit aplikace, které mají utajení a integrity.</span><span class="sxs-lookup"><span data-stu-id="42a01-122">Describes how [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] security helps you to create applications that have confidentiality and integrity.</span></span> <span data-ttu-id="42a01-123">Ověřování a autorizace je taky dostupné, jako jsou funkce auditování.</span><span class="sxs-lookup"><span data-stu-id="42a01-123">Authentication and authorization are also available, as are auditing features.</span></span>  
  
 [<span data-ttu-id="42a01-124">Síť rovnocenných počítačů</span><span class="sxs-lookup"><span data-stu-id="42a01-124">Peer-to-Peer Networking</span></span>](../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 <span data-ttu-id="42a01-125">Podrobné informace o tom, jak vytvořit sdílené služeb a klientů.</span><span class="sxs-lookup"><span data-stu-id="42a01-125">Details how to create peer services and clients.</span></span>  
  
 [<span data-ttu-id="42a01-126">Metadata</span><span class="sxs-lookup"><span data-stu-id="42a01-126">Metadata</span></span>](../../../../docs/framework/wcf/feature-details/metadata.md)  
 <span data-ttu-id="42a01-127">Popisuje architektury metadat a formáty.</span><span class="sxs-lookup"><span data-stu-id="42a01-127">Describes metadata architecture and formats.</span></span>  
  
 [<span data-ttu-id="42a01-128">Klienti</span><span class="sxs-lookup"><span data-stu-id="42a01-128">Clients</span></span>](../../../../docs/framework/wcf/feature-details/clients.md)  
 <span data-ttu-id="42a01-129">Popisuje, jak vytvořit různé klienty, kteří přístup ke službám.</span><span class="sxs-lookup"><span data-stu-id="42a01-129">Describes how to create a variety of clients that access services.</span></span>  
  
 [<span data-ttu-id="42a01-130">Hostování</span><span class="sxs-lookup"><span data-stu-id="42a01-130">Hosting</span></span>](../../../../docs/framework/wcf/feature-details/hosting.md)  
 <span data-ttu-id="42a01-131">Popisuje, který je hostitelem.</span><span class="sxs-lookup"><span data-stu-id="42a01-131">Describes hosting.</span></span> <span data-ttu-id="42a01-132">Služby mohou být hostovány systémem jiná aplikace, nebo může být vlastním hostováním.</span><span class="sxs-lookup"><span data-stu-id="42a01-132">A service can be hosted by another application, or it can be self-hosted.</span></span>  
  
 [<span data-ttu-id="42a01-133">Interoperabilita a integrace</span><span class="sxs-lookup"><span data-stu-id="42a01-133">Interoperability and Integration</span></span>](../../../../docs/framework/wcf/feature-details/interoperability-and-integration.md)  
 <span data-ttu-id="42a01-134">Popisuje způsob použití [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] rozšířit existující logiky, místo aby ho přepsání, pokud máte významné investice v logiku aplikace založené na součást hostované v modelu COM +.</span><span class="sxs-lookup"><span data-stu-id="42a01-134">Describes how to use [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] to extend your existing logic rather than having to rewrite it if you have a substantial investment in component-based application logic hosted in COM+.</span></span>  
  
 [<span data-ttu-id="42a01-135">Programovací model webových služeb HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="42a01-135">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)  
 <span data-ttu-id="42a01-136">Popisuje [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] programovací Model Web, který umožňuje vývojářům vystavit [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby operace do koncových bodů protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="42a01-136">Describes the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web Programming Model that allows developers to expose [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service operations to non-SOAP endpoints.</span></span>  
  
 [<span data-ttu-id="42a01-137">Syndikace WCF</span><span class="sxs-lookup"><span data-stu-id="42a01-137">WCF Syndication</span></span>](../../../../docs/framework/wcf/feature-details/wcf-syndication.md)  
 <span data-ttu-id="42a01-138">Popisuje podporu snadno vystavit informační kanály syndikace z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby.</span><span class="sxs-lookup"><span data-stu-id="42a01-138">Describes support to easily expose syndication feeds from a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span>  
  
 [<span data-ttu-id="42a01-139">Integrace jazyka AJAX a podpora JSON</span><span class="sxs-lookup"><span data-stu-id="42a01-139">AJAX Integration and JSON Support</span></span>](../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)  
 <span data-ttu-id="42a01-140">Popisuje podporu pro ASP.NET asynchronní JavaScript a XML (AJAX) a formát dat JavaScript Object Notation (JSON), které povoluje [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby vystavit operations klientům AJAX.</span><span class="sxs-lookup"><span data-stu-id="42a01-140">Describes support for ASP.NET Asynchronous JavaScript and XML (AJAX) and the JavaScript Object Notation (JSON) data format to allow [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services to expose operations to AJAX clients.</span></span>  
  
 [<span data-ttu-id="42a01-141">Zjišťování WCF</span><span class="sxs-lookup"><span data-stu-id="42a01-141">WCF Discovery</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery.md)  
 <span data-ttu-id="42a01-142">Popisuje podporu, aby umožnil services zjistitelný za běhu způsobem vzájemná spolupráce pomocí protokolu WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="42a01-142">Describes support to enable services to be discoverable at runtime in an interoperable way using the WS-Discovery protocol.</span></span>  
  
 [<span data-ttu-id="42a01-143">Směrování</span><span class="sxs-lookup"><span data-stu-id="42a01-143">Routing</span></span>](../../../../docs/framework/wcf/feature-details/routing.md)  
 <span data-ttu-id="42a01-144">Popisuje službu směrování.</span><span class="sxs-lookup"><span data-stu-id="42a01-144">Describes the routing service.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="42a01-145">Odkaz</span><span class="sxs-lookup"><span data-stu-id="42a01-145">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.IdentityModel.Selectors>  
  
 <xref:System.ServiceModel.Routing>  
  
## <a name="related-sections"></a><span data-ttu-id="42a01-146">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="42a01-146">Related Sections</span></span>  
 [<span data-ttu-id="42a01-147">Základní programování WCF</span><span class="sxs-lookup"><span data-stu-id="42a01-147">Basic WCF Programming</span></span>](../../../../docs/framework/wcf/basic-wcf-programming.md)
