---
title: Rychlý Start (WCF Data Services)
ms.date: 08/24/2018
helpviewer_keywords:
- WCF Data Services, quick-start example
- WCF Data Services, Entity Data Model (EDM) service
ms.assetid: 7b18ca1e-d4d6-4c7a-afb9-ce3cebb98a8d
ms.openlocfilehash: df3151dfd3628231d84d2d128c61d1c0b6b0d48e
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/04/2019
ms.locfileid: "74800362"
---
# <a name="quickstart-wcf-data-services"></a><span data-ttu-id="89c70-102">Rychlý Start (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="89c70-102">Quickstart (WCF Data Services)</span></span>

<span data-ttu-id="89c70-103">Tento rychlý Start vám pomůže se seznámení s WCF Data Services a protokolem Open Data Protocol (OData) prostřednictvím řady úloh, které podporují témata v [Začínáme](getting-started-with-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="89c70-103">This quickstart helps you become familiar with WCF Data Services and the Open Data Protocol (OData) through a series of tasks that support the topics in [Getting Started](getting-started-with-wcf-data-services.md).</span></span>

## <a name="what-youll-learn"></a><span data-ttu-id="89c70-104">Co se naučíte</span><span class="sxs-lookup"><span data-stu-id="89c70-104">What you'll learn</span></span>

<span data-ttu-id="89c70-105">První úkol v tomto rychlém startu ukazuje, jak vytvořit datovou službu k vystavení datového kanálu OData z ukázkové databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="89c70-105">The first task in this quickstart shows how to create a data service to expose an OData feed from the Northwind sample database.</span></span> <span data-ttu-id="89c70-106">V pozdějších tématech budete mít přístup k datovému kanálu OData pomocí webového prohlížeče a také vytvoříte klientskou aplikaci Windows Presentation Foundation (WPF), která využívá kanál OData pomocí klientských knihoven.</span><span class="sxs-lookup"><span data-stu-id="89c70-106">In later topics, you will access the OData feed by using a Web browser, and also create a Windows Presentation Foundation (WPF) client application that consumes the OData feed by using client libraries.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="89c70-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="89c70-107">Prerequisites</span></span>

<span data-ttu-id="89c70-108">K dokončení tohoto rychlého startu je nutné nainstalovat následující komponenty:</span><span class="sxs-lookup"><span data-stu-id="89c70-108">To complete this quickstart, you must install the following components:</span></span>

- <span data-ttu-id="89c70-109">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="89c70-109">Visual Studio</span></span>

- <span data-ttu-id="89c70-110">Instance SQL Server.</span><span class="sxs-lookup"><span data-stu-id="89c70-110">An instance of SQL Server.</span></span> <span data-ttu-id="89c70-111">To zahrnuje SQL Server Express, který je součástí výchozí instalace sady Visual Studio 2015 nebo jako součást úlohy **ukládání a zpracování dat** v aplikaci Visual Studio 2017 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="89c70-111">This includes SQL Server Express, which is included in a default installation of Visual Studio 2015, or as part of the **Data storage and processing** workload in Visual Studio 2017 or later.</span></span>

- <span data-ttu-id="89c70-112">Ukázkovou databázi Northwind</span><span class="sxs-lookup"><span data-stu-id="89c70-112">The Northwind sample database.</span></span> <span data-ttu-id="89c70-113">Pokud si chcete stáhnout tuto ukázkovou databázi, přečtěte si část [databáze pro stahování a ukázkové databáze pro SQL Server](https://go.microsoft.com/fwlink/?linkid=24758).</span><span class="sxs-lookup"><span data-stu-id="89c70-113">To download this sample database, see the download page, [Sample Databases for SQL Server](https://go.microsoft.com/fwlink/?linkid=24758).</span></span>

## <a name="wcf-data-services-quickstart-tasks"></a><span data-ttu-id="89c70-114">Úlohy rychlého startu WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="89c70-114">WCF data services quickstart tasks</span></span>

 [<span data-ttu-id="89c70-115">Vytvoření datové služby</span><span class="sxs-lookup"><span data-stu-id="89c70-115">Create the Data Service</span></span>](creating-the-data-service.md)

 <span data-ttu-id="89c70-116">Definujte aplikaci ASP.NET, definujte datový model, vytvořte datovou službu a povolte přístup k prostředkům.</span><span class="sxs-lookup"><span data-stu-id="89c70-116">Define the ASP.NET application, define the data model, create the data service, and enable access to resources.</span></span>

 [<span data-ttu-id="89c70-117">Přístup ke službě z webového prohlížeče</span><span class="sxs-lookup"><span data-stu-id="89c70-117">Access the Service from a Web Browser</span></span>](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)

 <span data-ttu-id="89c70-118">Spusťte službu ze sady Visual Studio a získejte přístup ke službě odesláním požadavků HTTP GET přes webový prohlížeč do vystaveného informačního kanálu.</span><span class="sxs-lookup"><span data-stu-id="89c70-118">Start the service from Visual Studio and access the service by submitting HTTP GET requests through a Web browser to the exposed feed.</span></span>

 [<span data-ttu-id="89c70-119">Vytvoření klientské aplikace .NET Framework</span><span class="sxs-lookup"><span data-stu-id="89c70-119">Create the .NET Framework Client Application</span></span>](creating-the-dotnet-client-application-wcf-data-services-quickstart.md)

 <span data-ttu-id="89c70-120">Vytvořte aplikaci WPF, která bude využívat datový kanál OData, svázat data s ovládacími prvky systému Windows, změnit data v vázaných ovládacích prvcích a pak tyto změny odeslat zpět do datové služby.</span><span class="sxs-lookup"><span data-stu-id="89c70-120">Create a WPF app to consume the OData feed, bind data to Windows controls, change data in the bound controls, and then send the changes back to the data service.</span></span>

> [!NOTE]
> <span data-ttu-id="89c70-121">Soubory projektu z dokončené verze rychlého startu lze stáhnout ze stránky [ukázek dokumentace WCF Data Services](https://go.microsoft.com/fwlink/?LinkId=179994) .</span><span class="sxs-lookup"><span data-stu-id="89c70-121">Project files from a completed version of the quickstart can be downloaded from the [WCF Data Services Documentation Samples](https://go.microsoft.com/fwlink/?LinkId=179994) page.</span></span>

## <a name="next-steps"></a><span data-ttu-id="89c70-122">Další kroky</span><span class="sxs-lookup"><span data-stu-id="89c70-122">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="89c70-123">Začínáme s rychlým startem</span><span class="sxs-lookup"><span data-stu-id="89c70-123">Start the quickstart</span></span>](creating-the-data-service.md)

## <a name="see-also"></a><span data-ttu-id="89c70-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="89c70-124">See also</span></span>

- [<span data-ttu-id="89c70-125">ADO.NET Entity Framework</span><span class="sxs-lookup"><span data-stu-id="89c70-125">ADO.NET Entity Framework</span></span>](../adonet/ef/index.md)
