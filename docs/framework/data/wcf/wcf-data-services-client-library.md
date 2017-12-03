---
title: "Klientská knihovna pro WCF Data Services"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF Data Services, client library
- DataServiceQuery class, about DataServiceQuery class
- DataServiceContext class, about DataServiceContext class
ms.assetid: 21075e50-8917-413e-a8ea-35a0f6e65aa5
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 65b02945aa81fdf18ad328a833f8f85744035871
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="wcf-data-services-client-library"></a><span data-ttu-id="329d1-102">Klientská knihovna pro WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="329d1-102">WCF Data Services Client Library</span></span>
<span data-ttu-id="329d1-103">Všechny aplikace mohou komunikovat s [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]-založené služba dat v případě, že může posílat proces a požadavek HTTP [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] kanálu, vrátí datové služby.</span><span class="sxs-lookup"><span data-stu-id="329d1-103">Any application can interact with an [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]-based data service if it can send an HTTP request and process the [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed that a data service returns.</span></span> <span data-ttu-id="329d1-104">Tato interoperabilita umožňuje přístup k [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]– na základě služby z široké povoleno rozsahu webových aplikací.</span><span class="sxs-lookup"><span data-stu-id="329d1-104">This interoperability enables you to access [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]-based services from a broad range of Web-enabled applications.</span></span> [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]<span data-ttu-id="329d1-105">zahrnuje knihovny klienta, které poskytují bohatší programovací prostředí spotřebuje [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] kanály v rozhraní .NET Framework nebo aplikace programu Silverlight.</span><span class="sxs-lookup"><span data-stu-id="329d1-105"> includes client libraries that provide a richer programming experience when you consume [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feeds from .NET Framework or Silverlight-based applications.</span></span>  
  
 <span data-ttu-id="329d1-106">Jsou dvě hlavní třídy klientské knihovny <xref:System.Data.Services.Client.DataServiceContext> třídy a <xref:System.Data.Services.Client.DataServiceQuery%601> třídy.</span><span class="sxs-lookup"><span data-stu-id="329d1-106">The two main classes of the client library are the <xref:System.Data.Services.Client.DataServiceContext> class and the <xref:System.Data.Services.Client.DataServiceQuery%601> class.</span></span> <span data-ttu-id="329d1-107"><xref:System.Data.Services.Client.DataServiceContext> Třída zapouzdří operace, které jsou podporovány službě zadaná data.</span><span class="sxs-lookup"><span data-stu-id="329d1-107">The <xref:System.Data.Services.Client.DataServiceContext> class encapsulates operations that are supported against a specified data service.</span></span> <span data-ttu-id="329d1-108">I když [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] jsou bezstavové služby, není kontextu.</span><span class="sxs-lookup"><span data-stu-id="329d1-108">Although [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] services are stateless, the context is not.</span></span> <span data-ttu-id="329d1-109">Proto můžete použít <xref:System.Data.Services.Client.DataServiceContext> třídy pro uchování stavu na straně klienta mezi interakce s službu data za účelem podpory funkcí, jako například Správa změn.</span><span class="sxs-lookup"><span data-stu-id="329d1-109">Therefore, you can use the <xref:System.Data.Services.Client.DataServiceContext> class to maintain state on the client between interactions with the data service in order to support features such as change management.</span></span> <span data-ttu-id="329d1-110">Tato třída také spravuje identit a sleduje změny.</span><span class="sxs-lookup"><span data-stu-id="329d1-110">This class also manages identities and tracks changes.</span></span> <span data-ttu-id="329d1-111"><xref:System.Data.Services.Client.DataServiceQuery%601> Třída reprezentuje dotazu oproti sadě konkrétní entity.</span><span class="sxs-lookup"><span data-stu-id="329d1-111">The <xref:System.Data.Services.Client.DataServiceQuery%601> class represents a query against a specific entity set.</span></span>  
  
 <span data-ttu-id="329d1-112">Tato část popisuje postup používání klientské knihovny pro přístup a měnit data z klientské aplikace rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="329d1-112">This section describes how to use client libraries to access and change data from a .NET Framework client application.</span></span> <span data-ttu-id="329d1-113">Další informace o tom, jak používat [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Klientská knihovna pro s aplikací založená na technologii Silverlight, najdete v části [datové služby WCF (Silverlight)](http://go.microsoft.com/fwlink/?LinkId=186016).</span><span class="sxs-lookup"><span data-stu-id="329d1-113">For more information about how to use the [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] client library with a Silverlight-based application, see [WCF Data Services (Silverlight)](http://go.microsoft.com/fwlink/?LinkId=186016).</span></span> <span data-ttu-id="329d1-114">Ostatní klientské knihovny jsou k dispozici které umožňují využívat [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] kanálu v jiné typy aplikací.</span><span class="sxs-lookup"><span data-stu-id="329d1-114">Other client libraries are available that enable you to consume an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed in other kinds of applications.</span></span> <span data-ttu-id="329d1-115">Další informace najdete v tématu [OData SDK](http://go.microsoft.com/fwlink/?LinkID=185796).</span><span class="sxs-lookup"><span data-stu-id="329d1-115">For more information, see the [OData SDK](http://go.microsoft.com/fwlink/?LinkID=185796).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="329d1-116">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="329d1-116">In This Section</span></span>  
 [<span data-ttu-id="329d1-117">Generování dat služby klientské knihovny</span><span class="sxs-lookup"><span data-stu-id="329d1-117">Generating the Data Service Client Library</span></span>](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)  
 <span data-ttu-id="329d1-118">Popisuje, jak generovat klientské knihovny a třídy klienta dat služby, které jsou založeny na [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] kanály.</span><span class="sxs-lookup"><span data-stu-id="329d1-118">Describes how to generate a client library and client data service classes that are based on [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feeds.</span></span>  
  
 [<span data-ttu-id="329d1-119">Dotaz na službu Data</span><span class="sxs-lookup"><span data-stu-id="329d1-119">Querying the Data Service</span></span>](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)  
 <span data-ttu-id="329d1-120">Popisuje, jak dotazovat služby data z aplikace založené na rozhraní .NET Framework pomocí knihovny klienta.</span><span class="sxs-lookup"><span data-stu-id="329d1-120">Describes how to query a data service from a .NET Framework-based application by using client libraries.</span></span>  
  
 [<span data-ttu-id="329d1-121">Odložené načtení obsahu</span><span class="sxs-lookup"><span data-stu-id="329d1-121">Loading Deferred Content</span></span>](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md)  
 <span data-ttu-id="329d1-122">Popisuje, jak načíst dalšího obsahu, které nejsou zahrnuty v odpovědi počátečního dotazu.</span><span class="sxs-lookup"><span data-stu-id="329d1-122">Describes how to load additional content not included in the initial query response.</span></span>  
  
 [<span data-ttu-id="329d1-123">Aktualizaci datové služby</span><span class="sxs-lookup"><span data-stu-id="329d1-123">Updating the Data Service</span></span>](../../../../docs/framework/data/wcf/updating-the-data-service-wcf-data-services.md)  
 <span data-ttu-id="329d1-124">Popisuje, jak vytvářet, upravovat a odstraňovat entity a vztahy s použitím knihovny klienta.</span><span class="sxs-lookup"><span data-stu-id="329d1-124">Describes how to create, modify, and delete entities and relationships by using the client libraries.</span></span>  
  
 [<span data-ttu-id="329d1-125">Asynchronní operace</span><span class="sxs-lookup"><span data-stu-id="329d1-125">Asynchronous Operations</span></span>](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md)  
 <span data-ttu-id="329d1-126">Popisuje poskytované systémem klientské knihovny pro práci se službou dat v asynchronním režimu.</span><span class="sxs-lookup"><span data-stu-id="329d1-126">Describes the facilities provided by the client libraries for working with a data service in an asynchronous manner.</span></span>  
  
 [<span data-ttu-id="329d1-127">Dávkování operací</span><span class="sxs-lookup"><span data-stu-id="329d1-127">Batching Operations</span></span>](../../../../docs/framework/data/wcf/batching-operations-wcf-data-services.md)  
 <span data-ttu-id="329d1-128">Popisuje, jak k odesílání více požadavků na službu data v jedné dávce pomocí knihovny klienta.</span><span class="sxs-lookup"><span data-stu-id="329d1-128">Describes how to send multiple requests to the data service in a single batch by using the client libraries.</span></span>  
  
 [<span data-ttu-id="329d1-129">Vazba dat s ovládacími prvky</span><span class="sxs-lookup"><span data-stu-id="329d1-129">Binding Data to Controls</span></span>](../../../../docs/framework/data/wcf/binding-data-to-controls-wcf-data-services.md)  
 <span data-ttu-id="329d1-130">Popisuje postup vytvoření vazby ovládacích prvků k [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] kanálu vrácený datové služby.</span><span class="sxs-lookup"><span data-stu-id="329d1-130">Describes how to bind controls to a [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed returned by a data service.</span></span>  
  
 [<span data-ttu-id="329d1-131">Volání operací služby</span><span class="sxs-lookup"><span data-stu-id="329d1-131">Calling Service Operations</span></span>](../../../../docs/framework/data/wcf/calling-service-operations-wcf-data-services.md)  
 <span data-ttu-id="329d1-132">Popisuje postup používání klientské knihovny pro volání operací služby.</span><span class="sxs-lookup"><span data-stu-id="329d1-132">Describes how to use the client library to call service operations.</span></span>  
  
 [<span data-ttu-id="329d1-133">Správa služby kontextu dat</span><span class="sxs-lookup"><span data-stu-id="329d1-133">Managing the Data Service Context</span></span>](../../../../docs/framework/data/wcf/managing-the-data-service-context-wcf-data-services.md)  
 <span data-ttu-id="329d1-134">Popisuje možnosti pro správu chování klientské knihovny.</span><span class="sxs-lookup"><span data-stu-id="329d1-134">Describes options for managing the behavior of the client library.</span></span>  
  
 [<span data-ttu-id="329d1-135">Práce s binární Data</span><span class="sxs-lookup"><span data-stu-id="329d1-135">Working with Binary Data</span></span>](../../../../docs/framework/data/wcf/working-with-binary-data-wcf-data-services.md)  
 <span data-ttu-id="329d1-136">Popisuje, jak získávat přístup a měnit binární data vrácená službou data jako datový proud.</span><span class="sxs-lookup"><span data-stu-id="329d1-136">Describes how to access and change binary data returned by the data service as a data stream.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="329d1-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="329d1-137">See Also</span></span>  
 [<span data-ttu-id="329d1-138">Definování datových služeb WCF</span><span class="sxs-lookup"><span data-stu-id="329d1-138">Defining WCF Data Services</span></span>](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)  
 [<span data-ttu-id="329d1-139">Začínáme</span><span class="sxs-lookup"><span data-stu-id="329d1-139">Getting Started</span></span>](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)
