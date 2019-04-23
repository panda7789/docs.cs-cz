---
title: Hostování datové služby (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, configuring
- WCF Data Services, Windows Communication Foundation
ms.assetid: b48f42ce-22ce-4f8d-8f0d-f7ddac9125ee
ms.openlocfilehash: e738fa1feebdd91bdb84484340b31e599d7f5f76
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59517938"
---
# <a name="hosting-the-data-service-wcf-data-services"></a><span data-ttu-id="6ef38-102">Hostování datové služby (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="6ef38-102">Hosting the Data Service (WCF Data Services)</span></span>
<span data-ttu-id="6ef38-103">Pomocí služeb WCF Data Services, můžete vytvořit službu, která zveřejňuje data jako [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] informačního kanálu.</span><span class="sxs-lookup"><span data-stu-id="6ef38-103">By using WCF Data Services, you can create a service that exposes data as an [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] feed.</span></span> <span data-ttu-id="6ef38-104">Tato služba dat je definován jako třída, která dědí z <xref:System.Data.Services.DataService%601>.</span><span class="sxs-lookup"><span data-stu-id="6ef38-104">This data service is defined as a class that inherits from <xref:System.Data.Services.DataService%601>.</span></span> <span data-ttu-id="6ef38-105">Tato třída poskytuje funkci požadovanou ke zpracování zpráv požadavků, provádění aktualizací na zdroji dat a vygenerování zprávy odpovědi, podle požadavků OData.</span><span class="sxs-lookup"><span data-stu-id="6ef38-105">This class provides the functionality required to process request messages, perform updates against the data source, and generate responses messages, as required by OData.</span></span> <span data-ttu-id="6ef38-106">Datové služby však nelze svázat a síťových soketů naslouchat příchozím požadavkům HTTP.</span><span class="sxs-lookup"><span data-stu-id="6ef38-106">However, a data service cannot bind to and listen on a network socket for incoming HTTP requests.</span></span> <span data-ttu-id="6ef38-107">Pro tato požadované funkce, která využívá datová služba hostitelská komponenta.</span><span class="sxs-lookup"><span data-stu-id="6ef38-107">For this required functionality, the data service relies on a hosting component.</span></span>

 <span data-ttu-id="6ef38-108">Hostitele datové služby se provádí tyto úlohy jménem datové služby:</span><span class="sxs-lookup"><span data-stu-id="6ef38-108">The data service host performs the following tasks on behalf of the data service:</span></span>

-   <span data-ttu-id="6ef38-109">Čeká na požadavky a směrovat tyto žádosti do datové služby.</span><span class="sxs-lookup"><span data-stu-id="6ef38-109">Listens for requests and routes these requests to the data service.</span></span>

-   <span data-ttu-id="6ef38-110">Vytvoří instance služby data pro každý požadavek.</span><span class="sxs-lookup"><span data-stu-id="6ef38-110">Creates an instance of the data service for each request.</span></span>

-   <span data-ttu-id="6ef38-111">Požadavky, že datové služby zpracování příchozího požadavku.</span><span class="sxs-lookup"><span data-stu-id="6ef38-111">Requests that the data service process the incoming request.</span></span>

-   <span data-ttu-id="6ef38-112">Odešle odpověď jménem datové služby.</span><span class="sxs-lookup"><span data-stu-id="6ef38-112">Sends the response on behalf of the data service.</span></span>

 <span data-ttu-id="6ef38-113">Pro zjednodušení, který je hostitelem datové služby, služeb WCF Data Services slouží k integraci s Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="6ef38-113">To simplify hosting a data service, WCF Data Services is designed to integrate with Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="6ef38-114">Data service poskytuje výchozí implementaci WCF, která slouží jako hostitele datové služby v [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikace.</span><span class="sxs-lookup"><span data-stu-id="6ef38-114">The data service provides a default WCF implementation that serves as the data service host in an [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] application.</span></span> <span data-ttu-id="6ef38-115">Proto může hostovat datové služby v jednom z následujících způsobů:</span><span class="sxs-lookup"><span data-stu-id="6ef38-115">Therefore, you can host a data service in one of the following ways:</span></span>

-   <span data-ttu-id="6ef38-116">V [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikace.</span><span class="sxs-lookup"><span data-stu-id="6ef38-116">In an [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] application.</span></span>

-   <span data-ttu-id="6ef38-117">Ve spravované aplikaci, která podporuje v místním prostředí služby WCF.</span><span class="sxs-lookup"><span data-stu-id="6ef38-117">In a managed application that supports self-hosted WCF services.</span></span>

-   <span data-ttu-id="6ef38-118">V některých jiných vlastního hostitele datové služby.</span><span class="sxs-lookup"><span data-stu-id="6ef38-118">In some other custom data service host.</span></span>

## <a name="hosting-a-data-service-in-an-aspnet-application"></a><span data-ttu-id="6ef38-119">Hostující datovou službu v aplikaci ASP.NET</span><span class="sxs-lookup"><span data-stu-id="6ef38-119">Hosting a Data Service in an ASP.NET Application</span></span>

<span data-ttu-id="6ef38-120">Při použití **přidat novou položku** dialogového okna v sadě Visual Studio 2015 k definování datových služeb v aplikaci ASP.NET, nástroj vygeneruje dva nové soubory v projektu.</span><span class="sxs-lookup"><span data-stu-id="6ef38-120">When you use the **Add New Item** dialog in Visual Studio 2015 to define a data service in an ASP.NET application, the tool generates two new files in the project.</span></span> <span data-ttu-id="6ef38-121">První soubor musí `.svc` rozšíření a předá instrukci modul runtime WCF na tom, jak vytvořit instanci datové služby.</span><span class="sxs-lookup"><span data-stu-id="6ef38-121">The first file has a `.svc` extension and instructs the WCF runtime how to instantiate the data service.</span></span> <span data-ttu-id="6ef38-122">Následuje příklad tohoto souboru pro datová služba Northwind ukázka vytvořit při dokončení [rychlý Start](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md):</span><span class="sxs-lookup"><span data-stu-id="6ef38-122">The following is an example of this file for the Northwind sample data service created when you complete the [quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md):</span></span>

```
<%@ ServiceHost Language="C#"
    Factory="System.Data.Services.DataServiceHostFactory,
            System.Data.Services, Version=4.0.0.0,
            Culture=neutral, PublicKeyToken=b77a5c561934e089"
    Service="NorthwindService.Northwind" %>
```

 <span data-ttu-id="6ef38-123">Tato direktiva řekne aplikaci vytvořit hostitele služby pro třídu pojmenované datové služby pomocí <xref:System.Data.Services.DataServiceHostFactory> třídy.</span><span class="sxs-lookup"><span data-stu-id="6ef38-123">This directive tells the application to create the service host for the named data service class by using the <xref:System.Data.Services.DataServiceHostFactory> class.</span></span>

 <span data-ttu-id="6ef38-124">Na stránce použití modelu code-behind pro `.svc` soubor obsahuje třídu, která je implementace data samotné služby, která je definovaná následujícím způsobem pro ukázková datová služba Northwind:</span><span class="sxs-lookup"><span data-stu-id="6ef38-124">The code-behind page for the `.svc` file contains the class that is the implementation of the data service itself, which is defined as follows for the Northwind sample data service:</span></span>

 [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#servicedefinition)]
 [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#servicedefinition)]

 <span data-ttu-id="6ef38-125">Protože datové služby se chová jako služba WCF, datové služby se integruje s [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] a následuje programovacího modelu WCF Web.</span><span class="sxs-lookup"><span data-stu-id="6ef38-125">Because a data service behaves like a WCF service, the data service integrates with [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] and follows the WCF Web programming model.</span></span> <span data-ttu-id="6ef38-126">Další informace najdete v tématu [služby WCF a ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md) a [WCF Web HTTP programovací Model](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md).</span><span class="sxs-lookup"><span data-stu-id="6ef38-126">For more information, see [WCF Services and ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md) and [WCF Web HTTP Programming Model](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md).</span></span>

## <a name="self-hosted-wcf-services"></a><span data-ttu-id="6ef38-127">Služby WCF v místním prostředí</span><span class="sxs-lookup"><span data-stu-id="6ef38-127">Self-Hosted WCF Services</span></span>
 <span data-ttu-id="6ef38-128">Protože zahrnuje implementace WCF služby WCF Data Services podporují datové služby jako služba WCF s vlastním hostováním.</span><span class="sxs-lookup"><span data-stu-id="6ef38-128">Because it incorporates a WCF implementation, WCF Data Services support self-hosting a data service as a WCF service.</span></span> <span data-ttu-id="6ef38-129">Služba může být v libovolném v místním prostředí [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] aplikace, jako je například konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="6ef38-129">A service can be self-hosted in any [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] application, such as a console application.</span></span> <span data-ttu-id="6ef38-130"><xref:System.Data.Services.DataServiceHost> Třída, která dědí z <xref:System.ServiceModel.Web.WebServiceHost>, se používá k vytvoření instance služby data na konkrétní adrese.</span><span class="sxs-lookup"><span data-stu-id="6ef38-130">The <xref:System.Data.Services.DataServiceHost> class, which inherits from <xref:System.ServiceModel.Web.WebServiceHost>, is used to instantiate the data service at a specific address.</span></span>

 <span data-ttu-id="6ef38-131">Hostování na vlastním lze použít pro vývoj a testování vzhledem k tomu, že se zjednoduší nasazení a řešení potíží se službou.</span><span class="sxs-lookup"><span data-stu-id="6ef38-131">Self-hosting can be used for development and testing because it can make it easier to deploy and troubleshoot the service.</span></span> <span data-ttu-id="6ef38-132">Tento typ hostování však neposkytuje poskytuje pokročilé funkce pro hostování a správu [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] nebo internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="6ef38-132">However, this kind of hosting does not provide the advanced hosting and management features provided by [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] or by Internet Information Services (IIS).</span></span> <span data-ttu-id="6ef38-133">Další informace najdete v tématu [hostování ve spravované aplikaci](../../../../docs/framework/wcf/feature-details/hosting-in-a-managed-application.md).</span><span class="sxs-lookup"><span data-stu-id="6ef38-133">For more information, see [Hosting in a Managed Application](../../../../docs/framework/wcf/feature-details/hosting-in-a-managed-application.md).</span></span>

## <a name="defining-a-custom-data-service-host"></a><span data-ttu-id="6ef38-134">Definování hostitele vlastní datové služby</span><span class="sxs-lookup"><span data-stu-id="6ef38-134">Defining a Custom Data Service Host</span></span>
 <span data-ttu-id="6ef38-135">V případech, kde je příliš omezující implementace hostitele WCF můžete také definovat vlastní hostitele datové služby.</span><span class="sxs-lookup"><span data-stu-id="6ef38-135">For cases where the WCF host implementation is too restrictive, you can also define a custom host for a data service.</span></span> <span data-ttu-id="6ef38-136">Všechny třídy, která implementuje <xref:System.Data.Services.IDataServiceHost> rozhraní může sloužit jako síťovým hostitelem datové služby.</span><span class="sxs-lookup"><span data-stu-id="6ef38-136">Any class that implements <xref:System.Data.Services.IDataServiceHost> interface can be used as the network host for a data service.</span></span> <span data-ttu-id="6ef38-137">Musí implementovat vlastního hostitele <xref:System.Data.Services.IDataServiceHost> rozhraní a být schopná zpracovat tyto základní povinnosti hostitele datové služby:</span><span class="sxs-lookup"><span data-stu-id="6ef38-137">A custom host must implement the <xref:System.Data.Services.IDataServiceHost> interface and be able to handle the following basic responsibilities of the data service host:</span></span>

-   <span data-ttu-id="6ef38-138">Zadejte datové služby s kořenovou cestou za služby.</span><span class="sxs-lookup"><span data-stu-id="6ef38-138">Provide the data service with the service root path.</span></span>

-   <span data-ttu-id="6ef38-139">Zpracovat informace hlavičky požadavku a odpovědi na příslušné <xref:System.Data.Services.IDataServiceHost> implementace členu.</span><span class="sxs-lookup"><span data-stu-id="6ef38-139">Process request and response headers information to the appropriate <xref:System.Data.Services.IDataServiceHost> member implementation.</span></span>

-   <span data-ttu-id="6ef38-140">Zpracování výjimek vyvolaných datové služby.</span><span class="sxs-lookup"><span data-stu-id="6ef38-140">Handle exceptions raised by the data service.</span></span>

-   <span data-ttu-id="6ef38-141">Ověření parametrů v řetězci dotazu.</span><span class="sxs-lookup"><span data-stu-id="6ef38-141">Validate parameters in the query string.</span></span>

## <a name="see-also"></a><span data-ttu-id="6ef38-142">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6ef38-142">See also</span></span>

- [<span data-ttu-id="6ef38-143">Definování datových služeb WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="6ef38-143">Defining WCF Data Services</span></span>](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)
- [<span data-ttu-id="6ef38-144">Vystavení dat jako služby</span><span class="sxs-lookup"><span data-stu-id="6ef38-144">Exposing Your Data as a Service</span></span>](../../../../docs/framework/data/wcf/exposing-your-data-as-a-service-wcf-data-services.md)
- [<span data-ttu-id="6ef38-145">Konfigurace datové služby</span><span class="sxs-lookup"><span data-stu-id="6ef38-145">Configuring the Data Service</span></span>](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)
