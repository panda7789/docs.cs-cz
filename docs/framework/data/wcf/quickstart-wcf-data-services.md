---
title: Rychlý Start (WCF Data Services)
ms.date: 08/24/2018
helpviewer_keywords:
- WCF Data Services, quick-start example
- WCF Data Services, Entity Data Model (EDM) service
ms.assetid: 7b18ca1e-d4d6-4c7a-afb9-ce3cebb98a8d
ms.openlocfilehash: d0002182c5ae519c36348acdd2587bca499fe72e
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975143"
---
# <a name="quickstart-wcf-data-services"></a><span data-ttu-id="71ec5-102">Rychlý Start (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="71ec5-102">Quickstart (WCF Data Services)</span></span>

<span data-ttu-id="71ec5-103">Tento rychlý Start vám pomůže se seznámení s WCF Data Services a protokolem Open Data Protocol (OData) prostřednictvím řady úloh, které podporují témata v [Začínáme](getting-started-with-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="71ec5-103">This quickstart helps you become familiar with WCF Data Services and the Open Data Protocol (OData) through a series of tasks that support the topics in [Getting Started](getting-started-with-wcf-data-services.md).</span></span>

## <a name="what-youll-learn"></a><span data-ttu-id="71ec5-104">Co se naučíte</span><span class="sxs-lookup"><span data-stu-id="71ec5-104">What you'll learn</span></span>

<span data-ttu-id="71ec5-105">První úkol v tomto rychlém startu ukazuje, jak vytvořit datovou službu k vystavení datového kanálu OData z ukázkové databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="71ec5-105">The first task in this quickstart shows how to create a data service to expose an OData feed from the Northwind sample database.</span></span> <span data-ttu-id="71ec5-106">V pozdějších tématech budete mít přístup k datovému kanálu OData pomocí webového prohlížeče a také vytvoříte klientskou aplikaci Windows Presentation Foundation (WPF), která využívá kanál OData pomocí klientských knihoven.</span><span class="sxs-lookup"><span data-stu-id="71ec5-106">In later topics, you will access the OData feed by using a Web browser, and also create a Windows Presentation Foundation (WPF) client application that consumes the OData feed by using client libraries.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="71ec5-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="71ec5-107">Prerequisites</span></span>

<span data-ttu-id="71ec5-108">K dokončení tohoto rychlého startu je nutné nainstalovat následující komponenty:</span><span class="sxs-lookup"><span data-stu-id="71ec5-108">To complete this quickstart, you must install the following components:</span></span>

- <span data-ttu-id="71ec5-109">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="71ec5-109">Visual Studio</span></span>

- <span data-ttu-id="71ec5-110">Instance SQL Server.</span><span class="sxs-lookup"><span data-stu-id="71ec5-110">An instance of SQL Server.</span></span> <span data-ttu-id="71ec5-111">To zahrnuje SQL Server Express, který je součástí výchozí instalace sady Visual Studio 2015 nebo jako součást úlohy **ukládání a zpracování dat** v aplikaci Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="71ec5-111">This includes SQL Server Express, which is included in a default installation of Visual Studio 2015, or as part of the **Data storage and processing** workload in Visual Studio 2017.</span></span>

- <span data-ttu-id="71ec5-112">Ukázkovou databázi Northwind</span><span class="sxs-lookup"><span data-stu-id="71ec5-112">The Northwind sample database.</span></span> <span data-ttu-id="71ec5-113">Pokud si chcete stáhnout tuto ukázkovou databázi, přečtěte si část [databáze pro stahování a ukázkové databáze pro SQL Server](https://go.microsoft.com/fwlink/?linkid=24758).</span><span class="sxs-lookup"><span data-stu-id="71ec5-113">To download this sample database, see the download page, [Sample Databases for SQL Server](https://go.microsoft.com/fwlink/?linkid=24758).</span></span>

## <a name="wcf-data-services-quickstart-tasks"></a><span data-ttu-id="71ec5-114">Úlohy rychlého startu WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="71ec5-114">WCF data services quickstart tasks</span></span>

 [<span data-ttu-id="71ec5-115">Vytvoření datové služby</span><span class="sxs-lookup"><span data-stu-id="71ec5-115">Create the Data Service</span></span>](creating-the-data-service.md)

 <span data-ttu-id="71ec5-116">Definujte aplikaci ASP.NET, definujte datový model, vytvořte datovou službu a povolte přístup k prostředkům.</span><span class="sxs-lookup"><span data-stu-id="71ec5-116">Define the ASP.NET application, define the data model, create the data service, and enable access to resources.</span></span>

 [<span data-ttu-id="71ec5-117">Přístup ke službě z webového prohlížeče</span><span class="sxs-lookup"><span data-stu-id="71ec5-117">Access the Service from a Web Browser</span></span>](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)

 <span data-ttu-id="71ec5-118">Spusťte službu ze sady Visual Studio a získejte přístup ke službě odesláním požadavků HTTP GET přes webový prohlížeč do vystaveného informačního kanálu.</span><span class="sxs-lookup"><span data-stu-id="71ec5-118">Start the service from Visual Studio and access the service by submitting HTTP GET requests through a Web browser to the exposed feed.</span></span>

 [<span data-ttu-id="71ec5-119">Vytvoření klientské aplikace .NET Framework</span><span class="sxs-lookup"><span data-stu-id="71ec5-119">Create the .NET Framework Client Application</span></span>](creating-the-dotnet-client-application-wcf-data-services-quickstart.md)

 <span data-ttu-id="71ec5-120">Vytvořte aplikaci WPF, která bude využívat datový kanál OData, svázat data s ovládacími prvky systému Windows, změnit data v vázaných ovládacích prvcích a pak tyto změny odeslat zpět do datové služby.</span><span class="sxs-lookup"><span data-stu-id="71ec5-120">Create a WPF app to consume the OData feed, bind data to Windows controls, change data in the bound controls, and then send the changes back to the data service.</span></span>

> [!NOTE]
> <span data-ttu-id="71ec5-121">Soubory projektu z dokončené verze rychlého startu lze stáhnout ze stránky [ukázek dokumentace WCF Data Services](https://go.microsoft.com/fwlink/?LinkId=179994) .</span><span class="sxs-lookup"><span data-stu-id="71ec5-121">Project files from a completed version of the quickstart can be downloaded from the [WCF Data Services Documentation Samples](https://go.microsoft.com/fwlink/?LinkId=179994) page.</span></span>

## <a name="next-steps"></a><span data-ttu-id="71ec5-122">Další kroky</span><span class="sxs-lookup"><span data-stu-id="71ec5-122">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="71ec5-123">Začínáme s rychlým startem</span><span class="sxs-lookup"><span data-stu-id="71ec5-123">Start the quickstart</span></span>](creating-the-data-service.md)

## <a name="see-also"></a><span data-ttu-id="71ec5-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="71ec5-124">See also</span></span>

- [<span data-ttu-id="71ec5-125">ADO.NET Entity Framework</span><span class="sxs-lookup"><span data-stu-id="71ec5-125">ADO.NET Entity Framework</span></span>](../adonet/ef/index.md)
