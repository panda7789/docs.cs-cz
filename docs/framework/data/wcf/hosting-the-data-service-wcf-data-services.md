---
title: "Hostující službu Data (služby WCF Data Services)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, configuring
- WCF Data Services, Windows Communication Foundation
ms.assetid: b48f42ce-22ce-4f8d-8f0d-f7ddac9125ee
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7fa76c5672b4117c446aca145b7cf98dae7801d4
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="hosting-the-data-service-wcf-data-services"></a><span data-ttu-id="f4753-102">Hostující službu Data (služby WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="f4753-102">Hosting the Data Service (WCF Data Services)</span></span>
<span data-ttu-id="f4753-103">Pomocí [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], můžete vytvořit službu, která zveřejňuje data jako [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] informačního kanálu.</span><span class="sxs-lookup"><span data-stu-id="f4753-103">By using [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], you can create a service that exposes data as an [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] feed.</span></span> <span data-ttu-id="f4753-104">Tato služba dat je definovaný jako třída, která dědí z <xref:System.Data.Services.DataService%601>.</span><span class="sxs-lookup"><span data-stu-id="f4753-104">This data service is defined as a class that inherits from <xref:System.Data.Services.DataService%601>.</span></span> <span data-ttu-id="f4753-105">Tato třída poskytuje funkci požadovanou ke zpracování zpráv žádostí, provádění aktualizací na zdroji dat a vygenerování odpovědí na zprávy, podle požadavků [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f4753-105">This class provides the functionality required to process request messages, perform updates against the data source, and generate responses messages, as required by [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)].</span></span> <span data-ttu-id="f4753-106">Datové služby však nelze vytvořit vazbu k a naslouchání soketu sítě pro příchozí požadavky HTTP.</span><span class="sxs-lookup"><span data-stu-id="f4753-106">However, a data service cannot bind to and listen on a network socket for incoming HTTP requests.</span></span> <span data-ttu-id="f4753-107">Tato funkce vyžaduje službu data využívá hostitelská komponenta.</span><span class="sxs-lookup"><span data-stu-id="f4753-107">For this required functionality, the data service relies on a hosting component.</span></span>  
  
 <span data-ttu-id="f4753-108">Hostitel služby dat provádí tyto úlohy jménem službu data:</span><span class="sxs-lookup"><span data-stu-id="f4753-108">The data service host performs the following tasks on behalf of the data service:</span></span>  
  
-   <span data-ttu-id="f4753-109">Čeká na požadavky a směruje tyto požadavky na službu data.</span><span class="sxs-lookup"><span data-stu-id="f4753-109">Listens for requests and routes these requests to the data service.</span></span>  
  
-   <span data-ttu-id="f4753-110">Vytvoří instanci služby dat pro každý požadavek.</span><span class="sxs-lookup"><span data-stu-id="f4753-110">Creates an instance of the data service for each request.</span></span>  
  
-   <span data-ttu-id="f4753-111">Požadavky, že služba data zpracovat příchozí žádosti.</span><span class="sxs-lookup"><span data-stu-id="f4753-111">Requests that the data service process the incoming request.</span></span>  
  
-   <span data-ttu-id="f4753-112">Odešle odpověď jménem službu data.</span><span class="sxs-lookup"><span data-stu-id="f4753-112">Sends the response on behalf of the data service.</span></span>  
  
 <span data-ttu-id="f4753-113">Pro zjednodušení hostování datové služby, [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] slouží k integraci s Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="f4753-113">To simplify hosting a data service, [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] is designed to integrate with Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="f4753-114">Služba data poskytuje výchozí implementaci WCF, který slouží jako hostitel služby data v [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikace.</span><span class="sxs-lookup"><span data-stu-id="f4753-114">The data service provides a default WCF implementation that serves as the data service host in an [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] application.</span></span> <span data-ttu-id="f4753-115">Proto je možné hostovat datové služby v jednom z následujících způsobů:</span><span class="sxs-lookup"><span data-stu-id="f4753-115">Therefore, you can host a data service in one of the following ways:</span></span>  
  
-   <span data-ttu-id="f4753-116">V [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikace.</span><span class="sxs-lookup"><span data-stu-id="f4753-116">In an [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] application.</span></span>  
  
-   <span data-ttu-id="f4753-117">Ve spravované aplikaci, která podporuje samoobslužné hostované služby WCF.</span><span class="sxs-lookup"><span data-stu-id="f4753-117">In a managed application that supports self-hosted WCF services.</span></span>  
  
-   <span data-ttu-id="f4753-118">V některých dalších vlastních dat hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="f4753-118">In some other custom data service host.</span></span>  
  
## <a name="hosting-a-data-service-in-an-aspnet-application"></a><span data-ttu-id="f4753-119">Hostitelská služba dat v aplikaci ASP.NET</span><span class="sxs-lookup"><span data-stu-id="f4753-119">Hosting a Data Service in an ASP.NET Application</span></span>  
 <span data-ttu-id="f4753-120">Při použití **přidat novou položku** dialogové okno v sadě Visual Studio k definování datové služby v aplikaci ASP.NET, nástroj vygeneruje dva nové soubory v projektu.</span><span class="sxs-lookup"><span data-stu-id="f4753-120">When you use the **Add New Item** dialog in Visual Studio to define a data service in an ASP.NET application, the tool generates two new files in the project.</span></span> <span data-ttu-id="f4753-121">První soubor má `.svc` rozšíření a dá pokyn modulu runtime WCF, jak vytvořit instanci službu data.</span><span class="sxs-lookup"><span data-stu-id="f4753-121">The first file has a `.svc` extension and instructs the WCF runtime how to instantiate the data service.</span></span> <span data-ttu-id="f4753-122">Následuje příklad tohoto souboru pro službu Northwind ukázková data vytvořit při dokončení [rychlý Start](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md):</span><span class="sxs-lookup"><span data-stu-id="f4753-122">The following is an example of this file for the Northwind sample data service created when you complete the [quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md):</span></span>  
  
```  
<%@ ServiceHost Language="C#"   
    Factory="System.Data.Services.DataServiceHostFactory,   
            System.Data.Services, Version=4.0.0.0,   
            Culture=neutral, PublicKeyToken=b77a5c561934e089"   
    Service="NorthwindService.Northwind" %>   
```  
  
 <span data-ttu-id="f4753-123">Tato direktiva informuje aplikace pro vytvoření hostitele služby pro třídu s názvem dat služby pomocí <xref:System.Data.Services.DataServiceHostFactory> třídy.</span><span class="sxs-lookup"><span data-stu-id="f4753-123">This directive tells the application to create the service host for the named data service class by using the <xref:System.Data.Services.DataServiceHostFactory> class.</span></span>  
  
 <span data-ttu-id="f4753-124">Na stránce kódu pro `.svc` soubor obsahuje třídu, která je implementace služby data samostatně, který je definován následujícím způsobem pro službu Northwind ukázková data:</span><span class="sxs-lookup"><span data-stu-id="f4753-124">The code-behind page for the `.svc` file contains the class that is the implementation of the data service itself, which is defined as follows for the Northwind sample data service:</span></span>  
  
 [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart service/cs/northwind.svc.cs#servicedefinition)]
 [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart service/vb/northwind.svc.vb#servicedefinition)]  
  
 <span data-ttu-id="f4753-125">Protože chová se jako služby WCF data service, službu data se integruje s [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] a dodržuje programovací model WCF Web.</span><span class="sxs-lookup"><span data-stu-id="f4753-125">Because a data service behaves like a WCF service, the data service integrates with [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] and follows the WCF Web programming model.</span></span> <span data-ttu-id="f4753-126">Další informace najdete v tématu [služby WCF a ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md) a [WCF Web HTTP programovací Model](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md).</span><span class="sxs-lookup"><span data-stu-id="f4753-126">For more information, see [WCF Services and ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md) and [WCF Web HTTP Programming Model](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md).</span></span>  
  
## <a name="self-hosted-wcf-services"></a><span data-ttu-id="f4753-127">Služby WCF s vlastním hostováním</span><span class="sxs-lookup"><span data-stu-id="f4753-127">Self-Hosted WCF Services</span></span>  
 <span data-ttu-id="f4753-128">Vzhledem k tomu, že její součástí jsou WCF implementaci [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] podporovat samoobslužné hostování datové služby jako služby WCF.</span><span class="sxs-lookup"><span data-stu-id="f4753-128">Because it incorporates a WCF implementation, [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] support self-hosting a data service as a WCF service.</span></span> <span data-ttu-id="f4753-129">Služba může být v jednom vlastním hostováním [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] aplikace, jako je například aplikace konzoly.</span><span class="sxs-lookup"><span data-stu-id="f4753-129">A service can be self-hosted in any [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] application, such as a console application.</span></span> <span data-ttu-id="f4753-130"><xref:System.Data.Services.DataServiceHost> Třídy, která dědí z <xref:System.ServiceModel.Web.WebServiceHost>, se používá k vytvoření instance služby data na konkrétní adrese.</span><span class="sxs-lookup"><span data-stu-id="f4753-130">The <xref:System.Data.Services.DataServiceHost> class, which inherits from <xref:System.ServiceModel.Web.WebServiceHost>, is used to instantiate the data service at a specific address.</span></span>  
  
 <span data-ttu-id="f4753-131">Vlastní hostování slouží pro vývoj a testování vzhledem k tomu, že ho můžete usnadňují nasazení a řešení potíží s službu.</span><span class="sxs-lookup"><span data-stu-id="f4753-131">Self-hosting can be used for development and testing because it can make it easier to deploy and troubleshoot the service.</span></span> <span data-ttu-id="f4753-132">Tento druh hostování však neposkytuje pokročilé funkce pro správu a hostování poskytované [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] nebo internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="f4753-132">However, this kind of hosting does not provide the advanced hosting and management features provided by [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] or by Internet Information Services (IIS).</span></span> <span data-ttu-id="f4753-133">Další informace najdete v tématu [hostování ve spravované aplikaci](../../../../docs/framework/wcf/feature-details/hosting-in-a-managed-application.md).</span><span class="sxs-lookup"><span data-stu-id="f4753-133">For more information, see [Hosting in a Managed Application](../../../../docs/framework/wcf/feature-details/hosting-in-a-managed-application.md).</span></span>  
  
## <a name="defining-a-custom-data-service-host"></a><span data-ttu-id="f4753-134">Definování vlastních dat hostitele služby</span><span class="sxs-lookup"><span data-stu-id="f4753-134">Defining a Custom Data Service Host</span></span>  
 <span data-ttu-id="f4753-135">V případech, kde je příliš omezující implementace hostitele WCF můžete také definovat vlastní hostitele pro datové služby.</span><span class="sxs-lookup"><span data-stu-id="f4753-135">For cases where the WCF host implementation is too restrictive, you can also define a custom host for a data service.</span></span> <span data-ttu-id="f4753-136">Všechny třídy, která implementuje <xref:System.Data.Services.IDataServiceHost> rozhraní slouží jako hostitel sítě pro datové služby.</span><span class="sxs-lookup"><span data-stu-id="f4753-136">Any class that implements <xref:System.Data.Services.IDataServiceHost> interface can be used as the network host for a data service.</span></span> <span data-ttu-id="f4753-137">Vlastní hostitel musí implementovat <xref:System.Data.Services.IDataServiceHost> rozhraní a být schopna zpracovávat následující základní zodpovědnosti hostitele data služeb:</span><span class="sxs-lookup"><span data-stu-id="f4753-137">A custom host must implement the <xref:System.Data.Services.IDataServiceHost> interface and be able to handle the following basic responsibilities of the data service host:</span></span>  
  
-   <span data-ttu-id="f4753-138">Zadejte službu data s kořenovou cestou za službu.</span><span class="sxs-lookup"><span data-stu-id="f4753-138">Provide the data service with the service root path.</span></span>  
  
-   <span data-ttu-id="f4753-139">Zpracovat informace o hlavičky požadavku a odpovědi na příslušné <xref:System.Data.Services.IDataServiceHost> implementaci prvku.</span><span class="sxs-lookup"><span data-stu-id="f4753-139">Process request and response headers information to the appropriate <xref:System.Data.Services.IDataServiceHost> member implementation.</span></span>  
  
-   <span data-ttu-id="f4753-140">Zpracování výjimek vyvolaných službu data.</span><span class="sxs-lookup"><span data-stu-id="f4753-140">Handle exceptions raised by the data service.</span></span>  
  
-   <span data-ttu-id="f4753-141">Ověření parametrů v řetězci dotazu.</span><span class="sxs-lookup"><span data-stu-id="f4753-141">Validate parameters in the query string.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4753-142">Viz také</span><span class="sxs-lookup"><span data-stu-id="f4753-142">See Also</span></span>  
 [<span data-ttu-id="f4753-143">Definování datových služeb WCF</span><span class="sxs-lookup"><span data-stu-id="f4753-143">Defining WCF Data Services</span></span>](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)  
 [<span data-ttu-id="f4753-144">Vystavení dat jako službu</span><span class="sxs-lookup"><span data-stu-id="f4753-144">Exposing Your Data as a Service</span></span>](../../../../docs/framework/data/wcf/exposing-your-data-as-a-service-wcf-data-services.md)  
 [<span data-ttu-id="f4753-145">Konfigurace datové služby</span><span class="sxs-lookup"><span data-stu-id="f4753-145">Configuring the Data Service</span></span>](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)
