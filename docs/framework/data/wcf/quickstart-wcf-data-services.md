---
title: Rychlý start (WCF Data Services)
ms.date: 08/24/2018
helpviewer_keywords:
- WCF Data Services, quick-start example
- WCF Data Services, Entity Data Model (EDM) service
ms.assetid: 7b18ca1e-d4d6-4c7a-afb9-ce3cebb98a8d
ms.openlocfilehash: f20ffcf356aa0493b1e2356746d9ad7b27d9a1aa
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2018
ms.locfileid: "43480510"
---
# <a name="quickstart-wcf-data-services"></a><span data-ttu-id="fc296-102">Rychlý start (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="fc296-102">Quickstart (WCF Data Services)</span></span>

<span data-ttu-id="fc296-103">V tomto rychlém startu jste se seznámili se službou WCF Data Services pomáhá a [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] řadou úkolů, které podporují témata v [Začínáme](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="fc296-103">This quickstart helps you become familiar with WCF Data Services and the [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] through a series of tasks that support the topics in [Getting Started](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md).</span></span>

## <a name="what-youll-learn"></a><span data-ttu-id="fc296-104">Co se dozvíte</span><span class="sxs-lookup"><span data-stu-id="fc296-104">What you'll learn</span></span>

<span data-ttu-id="fc296-105">První úkol v rámci tohoto rychlého startu ukazuje, jak vytvořit datovou službu vystavit z ukázkové databáze Northwind datového kanálu OData.</span><span class="sxs-lookup"><span data-stu-id="fc296-105">The first task in this quickstart shows how to create a data service to expose an OData feed from the Northwind sample database.</span></span> <span data-ttu-id="fc296-106">V pozdějších tématech, získáte přístup k prostředí OData kanálu pomocí webového prohlížeče a také vytvořit Windows Presentation Foundation (WPF) informační kanál klientskou aplikaci, která využívá OData pomocí klientské knihovny.</span><span class="sxs-lookup"><span data-stu-id="fc296-106">In later topics, you will access the OData feed by using a Web browser, and also create a Windows Presentation Foundation (WPF) client application that consumes the OData feed by using client libraries.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="fc296-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fc296-107">Prerequisites</span></span>

<span data-ttu-id="fc296-108">Abyste mohli absolvovat tento rychlý start, je třeba nainstalovat následující komponenty:</span><span class="sxs-lookup"><span data-stu-id="fc296-108">To complete this quickstart, you must install the following components:</span></span>

- <span data-ttu-id="fc296-109">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="fc296-109">Visual Studio</span></span>

- <span data-ttu-id="fc296-110">Instance systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="fc296-110">An instance of SQL Server.</span></span> <span data-ttu-id="fc296-111">Jedná se o SQL serveru Express, který je součástí výchozí instalace sady Visual Studio 2015 nebo jako součást **ukládání a zpracování dat** úlohy v sadě Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="fc296-111">This includes SQL Server Express, which is included in a default installation of Visual Studio 2015, or as part of the **Data storage and processing** workload in Visual Studio 2017.</span></span>

- <span data-ttu-id="fc296-112">Ukázkovou databázi Northwind</span><span class="sxs-lookup"><span data-stu-id="fc296-112">The Northwind sample database.</span></span> <span data-ttu-id="fc296-113">Stáhněte si tuto ukázkovou databázi, naleznete na stránce stahování [ukázkové databáze systému SQL Server](https://go.microsoft.com/fwlink/?linkid=24758).</span><span class="sxs-lookup"><span data-stu-id="fc296-113">To download this sample database, see the download page, [Sample Databases for SQL Server](https://go.microsoft.com/fwlink/?linkid=24758).</span></span>

## <a name="wcf-data-services-quickstart-tasks"></a><span data-ttu-id="fc296-114">WCF data services – rychlý start úlohy</span><span class="sxs-lookup"><span data-stu-id="fc296-114">WCF data services quickstart tasks</span></span>

 [<span data-ttu-id="fc296-115">Vytvoření datové služby</span><span class="sxs-lookup"><span data-stu-id="fc296-115">Create the Data Service</span></span>](../../../../docs/framework/data/wcf/creating-the-data-service.md)

 <span data-ttu-id="fc296-116">Definovat [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikace, definovat datový model, vytvoření datové služby a povolení přístupu k prostředkům.</span><span class="sxs-lookup"><span data-stu-id="fc296-116">Define the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] application, define the data model, create the data service, and enable access to resources.</span></span>

 [<span data-ttu-id="fc296-117">Přístup ke službě z webového prohlížeče</span><span class="sxs-lookup"><span data-stu-id="fc296-117">Access the Service from a Web Browser</span></span>](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)

 <span data-ttu-id="fc296-118">Spusťte službu ze sady Visual Studio a přístup ke službě, odešlete požadavky HTTP GET prostřednictvím webového prohlížeče a vystavené informačního kanálu.</span><span class="sxs-lookup"><span data-stu-id="fc296-118">Start the service from Visual Studio and access the service by submitting HTTP GET requests through a Web browser to the exposed feed.</span></span>

 [<span data-ttu-id="fc296-119">Vytvoření klientské aplikace .NET Framework</span><span class="sxs-lookup"><span data-stu-id="fc296-119">Create the .NET Framework Client Application</span></span>](../../../../docs/framework/data/wcf/creating-the-dotnet-client-application-wcf-data-services-quickstart.md)

 <span data-ttu-id="fc296-120">Vytvoření aplikace WPF využívat datového kanálu OData, vytvoření vazby dat k ovládacím prvkům Windows, změnu dat v vázané ovládací prvky a potom odešlete změny zpět do datové služby.</span><span class="sxs-lookup"><span data-stu-id="fc296-120">Create a WPF app to consume the OData feed, bind data to Windows controls, change data in the bound controls, and then send the changes back to the data service.</span></span>

> [!NOTE]
> <span data-ttu-id="fc296-121">Soubory projektu z úplnou verzi tohoto rychlého startu si můžete stáhnout z [Ukázky WCF Data Services dokumentaci](https://go.microsoft.com/fwlink/?LinkId=179994) stránky.</span><span class="sxs-lookup"><span data-stu-id="fc296-121">Project files from a completed version of the quickstart can be downloaded from the [WCF Data Services Documentation Samples](https://go.microsoft.com/fwlink/?LinkId=179994) page.</span></span>

## <a name="next-steps"></a><span data-ttu-id="fc296-122">Další kroky</span><span class="sxs-lookup"><span data-stu-id="fc296-122">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="fc296-123">Spuštění tohoto rychlého startu</span><span class="sxs-lookup"><span data-stu-id="fc296-123">Start the quickstart</span></span>](../../../../docs/framework/data/wcf/creating-the-data-service.md)

## <a name="see-also"></a><span data-ttu-id="fc296-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fc296-124">See also</span></span>

- [<span data-ttu-id="fc296-125">ADO.NET Entity Framework</span><span class="sxs-lookup"><span data-stu-id="fc296-125">ADO.NET Entity Framework</span></span>](../../../../docs/framework/data/adonet/ef/index.md)
