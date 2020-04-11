---
title: Úvodní příručka (datové služby WCF)
ms.date: 08/24/2018
helpviewer_keywords:
- WCF Data Services, quick-start example
- WCF Data Services, Entity Data Model (EDM) service
ms.assetid: 7b18ca1e-d4d6-4c7a-afb9-ce3cebb98a8d
ms.openlocfilehash: f945d33a4fc789b3c73c1c80040fc8527301758b
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121216"
---
# <a name="quickstart-wcf-data-services"></a><span data-ttu-id="e92db-102">Úvodní příručka (datové služby WCF)</span><span class="sxs-lookup"><span data-stu-id="e92db-102">Quickstart (WCF Data Services)</span></span>

<span data-ttu-id="e92db-103">Tento rychlý start vám pomůže seznámit se s datovými službami WCF a protokolem OData (Open Data Protocol) prostřednictvím řady úkolů, které podporují témata v [tématu Začínáme](getting-started-with-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="e92db-103">This quickstart helps you become familiar with WCF Data Services and the Open Data Protocol (OData) through a series of tasks that support the topics in [Getting Started](getting-started-with-wcf-data-services.md).</span></span>

## <a name="what-youll-learn"></a><span data-ttu-id="e92db-104">Co se dozvíte</span><span class="sxs-lookup"><span data-stu-id="e92db-104">What you'll learn</span></span>

<span data-ttu-id="e92db-105">První úkol v tomto rychlém startu ukazuje, jak vytvořit datovou službu pro vystavení datového kanálu OData z ukázkové databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="e92db-105">The first task in this quickstart shows how to create a data service to expose an OData feed from the Northwind sample database.</span></span> <span data-ttu-id="e92db-106">V pozdějších tématech budete přistupovat k informačnímu kanálu OData pomocí webového prohlížeče a také vytvoříte klientskou aplikaci WPF (Windows Presentation Foundation), která využívá informační kanál OData pomocí klientských knihoven.</span><span class="sxs-lookup"><span data-stu-id="e92db-106">In later topics, you will access the OData feed by using a Web browser, and also create a Windows Presentation Foundation (WPF) client application that consumes the OData feed by using client libraries.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e92db-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e92db-107">Prerequisites</span></span>

<span data-ttu-id="e92db-108">Chcete-li tento rychlý start dokončit, nainstalujte následující součásti:</span><span class="sxs-lookup"><span data-stu-id="e92db-108">To complete this quickstart, install the following components:</span></span>

- <span data-ttu-id="e92db-109">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e92db-109">Visual Studio</span></span>

- <span data-ttu-id="e92db-110">Instance serveru SQL Server.</span><span class="sxs-lookup"><span data-stu-id="e92db-110">An instance of SQL Server.</span></span> <span data-ttu-id="e92db-111">To zahrnuje SQL Server Express, který je součástí výchozí instalace Visual Studio 2015 nebo jako součást **úlohy ukládání dat a zpracování** v sadě Visual Studio 2017 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="e92db-111">This includes SQL Server Express, which is included in a default installation of Visual Studio 2015, or as part of the **Data storage and processing** workload in Visual Studio 2017 or later.</span></span>

- <span data-ttu-id="e92db-112">Ukázkovou databázi Northwind</span><span class="sxs-lookup"><span data-stu-id="e92db-112">The Northwind sample database.</span></span> <span data-ttu-id="e92db-113">Chcete-li databázi nainstalovat, spusťte skript Transact-SQL z [ukázkových databází Northwind a pubs pro microsoft sql server](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs).</span><span class="sxs-lookup"><span data-stu-id="e92db-113">To install the database, run the Transact-SQL script from [Northwind and pubs sample databases for Microsoft SQL Server](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs).</span></span>

## <a name="wcf-data-services-quickstart-tasks"></a><span data-ttu-id="e92db-114">Úlohy rychlého spuštění datových služeb WCF</span><span class="sxs-lookup"><span data-stu-id="e92db-114">WCF data services quickstart tasks</span></span>

 [<span data-ttu-id="e92db-115">Vytvoření datové služby</span><span class="sxs-lookup"><span data-stu-id="e92db-115">Create the Data Service</span></span>](creating-the-data-service.md)

 <span data-ttu-id="e92db-116">Definujte ASP.NET aplikaci, definujte datový model, vytvořte datovou službu a povolte přístup k prostředkům.</span><span class="sxs-lookup"><span data-stu-id="e92db-116">Define the ASP.NET application, define the data model, create the data service, and enable access to resources.</span></span>

 [<span data-ttu-id="e92db-117">Přístup ke službě z webového prohlížeče</span><span class="sxs-lookup"><span data-stu-id="e92db-117">Access the Service from a Web Browser</span></span>](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)

 <span data-ttu-id="e92db-118">Spusťte službu z aplikace Visual Studio a získejte přístup ke službě odesláním požadavků HTTP GET prostřednictvím webového prohlížeče do informačního kanálu.</span><span class="sxs-lookup"><span data-stu-id="e92db-118">Start the service from Visual Studio and access the service by submitting HTTP GET requests through a Web browser to the exposed feed.</span></span>

 [<span data-ttu-id="e92db-119">Vytvoření klientské aplikace rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="e92db-119">Create the .NET Framework Client Application</span></span>](creating-the-dotnet-client-application-wcf-data-services-quickstart.md)

 <span data-ttu-id="e92db-120">Vytvořte aplikaci WPF, která spotřebovává datový kanál OData, váže data s ovládacími prvky systému Windows, mění data v vázaných ovládacích prvcích a pak odešle změny zpět do datové služby.</span><span class="sxs-lookup"><span data-stu-id="e92db-120">Create a WPF app to consume the OData feed, bind data to Windows controls, change data in the bound controls, and then send the changes back to the data service.</span></span>

> [!NOTE]
> <span data-ttu-id="e92db-121">Soubory projektu z dokončené verze rychlého startu lze stáhnout z [GitHubu](https://github.com/microsoftarchive/msdn-code-gallery-community-s-z/tree/master/WCF%20Data%20Services%20Quickstart%20(OData%20Service%20and%20WPF%20Client)).</span><span class="sxs-lookup"><span data-stu-id="e92db-121">Project files from a completed version of the quickstart can be downloaded from [GitHub](https://github.com/microsoftarchive/msdn-code-gallery-community-s-z/tree/master/WCF%20Data%20Services%20Quickstart%20(OData%20Service%20and%20WPF%20Client)).</span></span>

## <a name="next-steps"></a><span data-ttu-id="e92db-122">Další kroky</span><span class="sxs-lookup"><span data-stu-id="e92db-122">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="e92db-123">Spuštění rychlého startu</span><span class="sxs-lookup"><span data-stu-id="e92db-123">Start the quickstart</span></span>](creating-the-data-service.md)

## <a name="see-also"></a><span data-ttu-id="e92db-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="e92db-124">See also</span></span>

- [<span data-ttu-id="e92db-125">ADO.NET Entity Framework</span><span class="sxs-lookup"><span data-stu-id="e92db-125">ADO.NET Entity Framework</span></span>](../adonet/ef/index.md)
