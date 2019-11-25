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
ms.openlocfilehash: 3abcd901bcb8a175aa6f30e53b142cbbde56a579
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975245"
---
# <a name="hosting-the-data-service-wcf-data-services"></a><span data-ttu-id="3ed5c-102">Hostování datové služby (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="3ed5c-102">Hosting the Data Service (WCF Data Services)</span></span>
<span data-ttu-id="3ed5c-103">Pomocí WCF Data Services můžete vytvořit službu, která zpřístupňuje data jako informační kanál OData (Open Data Protocol).</span><span class="sxs-lookup"><span data-stu-id="3ed5c-103">By using WCF Data Services, you can create a service that exposes data as an Open Data Protocol (OData) feed.</span></span> <span data-ttu-id="3ed5c-104">Tato datová služba je definována jako třída, která dědí z <xref:System.Data.Services.DataService%601>.</span><span class="sxs-lookup"><span data-stu-id="3ed5c-104">This data service is defined as a class that inherits from <xref:System.Data.Services.DataService%601>.</span></span> <span data-ttu-id="3ed5c-105">Tato třída poskytuje funkce potřebné ke zpracování zpráv požadavků, provádění aktualizací proti zdroji dat a generování zpráv odpovědí podle požadavků OData.</span><span class="sxs-lookup"><span data-stu-id="3ed5c-105">This class provides the functionality required to process request messages, perform updates against the data source, and generate responses messages, as required by OData.</span></span> <span data-ttu-id="3ed5c-106">Datová služba ale nemůže navazovat a naslouchat síťovému soketu pro příchozí požadavky HTTP.</span><span class="sxs-lookup"><span data-stu-id="3ed5c-106">However, a data service cannot bind to and listen on a network socket for incoming HTTP requests.</span></span> <span data-ttu-id="3ed5c-107">Pro tuto požadovanou funkci datová služba spoléhá na komponentu hostování.</span><span class="sxs-lookup"><span data-stu-id="3ed5c-107">For this required functionality, the data service relies on a hosting component.</span></span>

 <span data-ttu-id="3ed5c-108">Hostitel datové služby provádí následující úkoly jménem datové služby:</span><span class="sxs-lookup"><span data-stu-id="3ed5c-108">The data service host performs the following tasks on behalf of the data service:</span></span>

- <span data-ttu-id="3ed5c-109">Naslouchá žádostem a směruje tyto požadavky na datovou službu.</span><span class="sxs-lookup"><span data-stu-id="3ed5c-109">Listens for requests and routes these requests to the data service.</span></span>

- <span data-ttu-id="3ed5c-110">Vytvoří instanci datové služby pro každý požadavek.</span><span class="sxs-lookup"><span data-stu-id="3ed5c-110">Creates an instance of the data service for each request.</span></span>

- <span data-ttu-id="3ed5c-111">Požaduje, aby datová služba zpracovala příchozí požadavek.</span><span class="sxs-lookup"><span data-stu-id="3ed5c-111">Requests that the data service process the incoming request.</span></span>

- <span data-ttu-id="3ed5c-112">Odešle odpověď jménem datové služby.</span><span class="sxs-lookup"><span data-stu-id="3ed5c-112">Sends the response on behalf of the data service.</span></span>

 <span data-ttu-id="3ed5c-113">Aby bylo možné zjednodušit hostování datové služby, WCF Data Services je navržena pro integraci s Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="3ed5c-113">To simplify hosting a data service, WCF Data Services is designed to integrate with Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="3ed5c-114">Datová služba poskytuje výchozí implementaci služby WCF, která slouží jako hostitel datové služby v aplikaci ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="3ed5c-114">The data service provides a default WCF implementation that serves as the data service host in an ASP.NET application.</span></span> <span data-ttu-id="3ed5c-115">Proto můžete hostovat datovou službu jedním z následujících způsobů:</span><span class="sxs-lookup"><span data-stu-id="3ed5c-115">Therefore, you can host a data service in one of the following ways:</span></span>

- <span data-ttu-id="3ed5c-116">V aplikaci ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="3ed5c-116">In an ASP.NET application.</span></span>

- <span data-ttu-id="3ed5c-117">Ve spravované aplikaci, která podporuje samoobslužně hostované služby WCF.</span><span class="sxs-lookup"><span data-stu-id="3ed5c-117">In a managed application that supports self-hosted WCF services.</span></span>

- <span data-ttu-id="3ed5c-118">V některém jiném vlastním hostiteli datové služby.</span><span class="sxs-lookup"><span data-stu-id="3ed5c-118">In some other custom data service host.</span></span>

## <a name="hosting-a-data-service-in-an-aspnet-application"></a><span data-ttu-id="3ed5c-119">Hostování datové služby v aplikaci ASP.NET</span><span class="sxs-lookup"><span data-stu-id="3ed5c-119">Hosting a Data Service in an ASP.NET Application</span></span>

<span data-ttu-id="3ed5c-120">Při použití dialogového okna **Přidat novou položku** v aplikaci Visual Studio 2015 k definování datové služby v aplikaci ASP.NET generuje nástroj v projektu dva nové soubory.</span><span class="sxs-lookup"><span data-stu-id="3ed5c-120">When you use the **Add New Item** dialog in Visual Studio 2015 to define a data service in an ASP.NET application, the tool generates two new files in the project.</span></span> <span data-ttu-id="3ed5c-121">První soubor má rozšíření `.svc` a instruuje modul runtime WCF, jak vytvořit instanci datové služby.</span><span class="sxs-lookup"><span data-stu-id="3ed5c-121">The first file has a `.svc` extension and instructs the WCF runtime how to instantiate the data service.</span></span> <span data-ttu-id="3ed5c-122">Následuje příklad tohoto souboru pro ukázkovou datovou službu Northwind vytvořenou po dokončení [rychlého](quickstart-wcf-data-services.md)startu:</span><span class="sxs-lookup"><span data-stu-id="3ed5c-122">The following is an example of this file for the Northwind sample data service created when you complete the [quickstart](quickstart-wcf-data-services.md):</span></span>

```aspx-csharp
<%@ ServiceHost Language="C#"
    Factory="System.Data.Services.DataServiceHostFactory,
            System.Data.Services, Version=4.0.0.0,
            Culture=neutral, PublicKeyToken=b77a5c561934e089"
    Service="NorthwindService.Northwind" %>
```

 <span data-ttu-id="3ed5c-123">Tato direktiva oznamuje aplikaci, aby vytvořila hostitele služby pro třídu pojmenované datové služby pomocí třídy <xref:System.Data.Services.DataServiceHostFactory>.</span><span class="sxs-lookup"><span data-stu-id="3ed5c-123">This directive tells the application to create the service host for the named data service class by using the <xref:System.Data.Services.DataServiceHostFactory> class.</span></span>

 <span data-ttu-id="3ed5c-124">Stránka s kódem na pozadí pro `.svc` soubor obsahuje třídu, která je implementací samotné datové služby, která je definována následujícím způsobem pro ukázkovou datovou službu Northwind:</span><span class="sxs-lookup"><span data-stu-id="3ed5c-124">The code-behind page for the `.svc` file contains the class that is the implementation of the data service itself, which is defined as follows for the Northwind sample data service:</span></span>

 [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#servicedefinition)]
 [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#servicedefinition)]

 <span data-ttu-id="3ed5c-125">Vzhledem k tomu, že se datová služba chová jako služba WCF, datová služba se integruje s ASP.NET a sleduje model webového programování WCF.</span><span class="sxs-lookup"><span data-stu-id="3ed5c-125">Because a data service behaves like a WCF service, the data service integrates with ASP.NET and follows the WCF Web programming model.</span></span> <span data-ttu-id="3ed5c-126">Další informace najdete v tématu model programování [služeb WCF a ASP.NET](../../wcf/feature-details/wcf-services-and-aspnet.md) a [WCF web http](../../wcf/feature-details/wcf-web-http-programming-model.md).</span><span class="sxs-lookup"><span data-stu-id="3ed5c-126">For more information, see [WCF Services and ASP.NET](../../wcf/feature-details/wcf-services-and-aspnet.md) and [WCF Web HTTP Programming Model](../../wcf/feature-details/wcf-web-http-programming-model.md).</span></span>

## <a name="self-hosted-wcf-services"></a><span data-ttu-id="3ed5c-127">Samoobslužné služby WCF</span><span class="sxs-lookup"><span data-stu-id="3ed5c-127">Self-Hosted WCF Services</span></span>
 <span data-ttu-id="3ed5c-128">Protože zahrnuje implementaci WCF, WCF Data Services podporu samoobslužného hostování datové služby jako služby WCF.</span><span class="sxs-lookup"><span data-stu-id="3ed5c-128">Because it incorporates a WCF implementation, WCF Data Services support self-hosting a data service as a WCF service.</span></span> <span data-ttu-id="3ed5c-129">Služba může být samoobslužně hostována v libovolné .NET Framework aplikaci, jako je například Konzolová aplikace.</span><span class="sxs-lookup"><span data-stu-id="3ed5c-129">A service can be self-hosted in any .NET Framework application, such as a console application.</span></span> <span data-ttu-id="3ed5c-130">Třída <xref:System.Data.Services.DataServiceHost>, která dědí z <xref:System.ServiceModel.Web.WebServiceHost>, slouží k vytvoření instance datové služby na konkrétní adrese.</span><span class="sxs-lookup"><span data-stu-id="3ed5c-130">The <xref:System.Data.Services.DataServiceHost> class, which inherits from <xref:System.ServiceModel.Web.WebServiceHost>, is used to instantiate the data service at a specific address.</span></span>

 <span data-ttu-id="3ed5c-131">Samoobslužné hostování lze použít pro vývoj a testování, protože může usnadnit jeho nasazení a odstraňování potíží.</span><span class="sxs-lookup"><span data-stu-id="3ed5c-131">Self-hosting can be used for development and testing because it can make it easier to deploy and troubleshoot the service.</span></span> <span data-ttu-id="3ed5c-132">Tento druh hostování ale neposkytuje pokročilé funkce pro hostování a správu, které poskytuje ASP.NET nebo Internetová informační služba (IIS).</span><span class="sxs-lookup"><span data-stu-id="3ed5c-132">However, this kind of hosting does not provide the advanced hosting and management features provided by ASP.NET or by Internet Information Services (IIS).</span></span> <span data-ttu-id="3ed5c-133">Další informace najdete v tématu [hostování ve spravované aplikaci](../../wcf/feature-details/hosting-in-a-managed-application.md).</span><span class="sxs-lookup"><span data-stu-id="3ed5c-133">For more information, see [Hosting in a Managed Application](../../wcf/feature-details/hosting-in-a-managed-application.md).</span></span>

## <a name="defining-a-custom-data-service-host"></a><span data-ttu-id="3ed5c-134">Definování vlastního hostitele datové služby</span><span class="sxs-lookup"><span data-stu-id="3ed5c-134">Defining a Custom Data Service Host</span></span>
 <span data-ttu-id="3ed5c-135">V případech, kdy je implementace hostitele WCF příliš omezující, můžete také definovat vlastního hostitele pro datovou službu.</span><span class="sxs-lookup"><span data-stu-id="3ed5c-135">For cases where the WCF host implementation is too restrictive, you can also define a custom host for a data service.</span></span> <span data-ttu-id="3ed5c-136">Jakákoli třída, která implementuje rozhraní <xref:System.Data.Services.IDataServiceHost>, může být použita jako síťový hostitel pro datovou službu.</span><span class="sxs-lookup"><span data-stu-id="3ed5c-136">Any class that implements <xref:System.Data.Services.IDataServiceHost> interface can be used as the network host for a data service.</span></span> <span data-ttu-id="3ed5c-137">Vlastní hostitel musí implementovat rozhraní <xref:System.Data.Services.IDataServiceHost> a být schopný zvládnout následující základní zodpovědnosti hostitele datové služby:</span><span class="sxs-lookup"><span data-stu-id="3ed5c-137">A custom host must implement the <xref:System.Data.Services.IDataServiceHost> interface and be able to handle the following basic responsibilities of the data service host:</span></span>

- <span data-ttu-id="3ed5c-138">Zadejte datovou službu s kořenovou cestou služby.</span><span class="sxs-lookup"><span data-stu-id="3ed5c-138">Provide the data service with the service root path.</span></span>

- <span data-ttu-id="3ed5c-139">Zpracujte informace hlavičky žádosti a odpovědi příslušné implementaci <xref:System.Data.Services.IDataServiceHost> členů.</span><span class="sxs-lookup"><span data-stu-id="3ed5c-139">Process request and response headers information to the appropriate <xref:System.Data.Services.IDataServiceHost> member implementation.</span></span>

- <span data-ttu-id="3ed5c-140">Zpracování výjimek vyvolaných datovou službou.</span><span class="sxs-lookup"><span data-stu-id="3ed5c-140">Handle exceptions raised by the data service.</span></span>

- <span data-ttu-id="3ed5c-141">Ověřte parametry v řetězci dotazu.</span><span class="sxs-lookup"><span data-stu-id="3ed5c-141">Validate parameters in the query string.</span></span>

## <a name="see-also"></a><span data-ttu-id="3ed5c-142">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3ed5c-142">See also</span></span>

- [<span data-ttu-id="3ed5c-143">Definování datových služeb WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="3ed5c-143">Defining WCF Data Services</span></span>](defining-wcf-data-services.md)
- [<span data-ttu-id="3ed5c-144">Vystavení dat jako služby</span><span class="sxs-lookup"><span data-stu-id="3ed5c-144">Exposing Your Data as a Service</span></span>](exposing-your-data-as-a-service-wcf-data-services.md)
- [<span data-ttu-id="3ed5c-145">Konfigurace datové služby</span><span class="sxs-lookup"><span data-stu-id="3ed5c-145">Configuring the Data Service</span></span>](configuring-the-data-service-wcf-data-services.md)
