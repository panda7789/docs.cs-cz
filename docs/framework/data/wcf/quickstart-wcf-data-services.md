---
title: Rychlý start (služby WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, quick-start example
- WCF Data Services, Entity Data Model (EDM) service
ms.assetid: 7b18ca1e-d4d6-4c7a-afb9-ce3cebb98a8d
ms.openlocfilehash: 1a30f7e65efc65bf47abd61e5bfdfa85b58ae3a2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33365394"
---
# <a name="quickstart-wcf-data-services"></a><span data-ttu-id="8f219-102">Rychlý start (služby WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="8f219-102">Quickstart (WCF Data Services)</span></span>
<span data-ttu-id="8f219-103">Tento rychlý Start umožňuje seznámit se s [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] a [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] prostřednictvím řadu úloh, které podporují témata v [Začínáme](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="8f219-103">This quickstart helps you become familiar with [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] and the [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] through a series of tasks that support the topics in [Getting Started](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md).</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="8f219-104">Co se dozvíte</span><span class="sxs-lookup"><span data-stu-id="8f219-104">What You Will Learn</span></span>  
 <span data-ttu-id="8f219-105">První úlohou tento rychlý start ukazuje, jak vytvořit službu data ke zveřejnění [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] kanálu z ukázková databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="8f219-105">The first task in this quickstart shows how to create a data service to expose an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed from the Northwind sample database.</span></span> <span data-ttu-id="8f219-106">V následujících tématech, bude přístup [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] kanálu pomocí webového prohlížeče a také vytvořit klientskou aplikaci Windows Presentation Foundation (WPF), který využívá [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] kanálu pomocí knihovny klienta.</span><span class="sxs-lookup"><span data-stu-id="8f219-106">In later topics, you will access the [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed by using a Web browser, and also create a Windows Presentation Foundation (WPF) client application that consumes the [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed by using client libraries.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="8f219-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8f219-107">Prerequisites</span></span>  
 <span data-ttu-id="8f219-108">Chcete-li dokončit tento rychlý start, je nutné nainstalovat následující součásti:</span><span class="sxs-lookup"><span data-stu-id="8f219-108">To complete this quickstart, you must install the following components:</span></span>  
  
-   [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]<span data-ttu-id="8f219-109">.</span><span class="sxs-lookup"><span data-stu-id="8f219-109">.</span></span>  
  
-   <span data-ttu-id="8f219-110">Instance [!INCLUDE[msCoName](../../../../includes/msconame-md.md)] systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="8f219-110">An instance of [!INCLUDE[msCoName](../../../../includes/msconame-md.md)] SQL Server.</span></span> <span data-ttu-id="8f219-111">To zahrnuje, SQL Server Express, který je zahrnutý ve výchozí instalaci sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8f219-111">This includes SQL Server Express, which is included in a default installation of Visual Studio.</span></span>  
  
-   <span data-ttu-id="8f219-112">Ukázkovou databázi Northwind</span><span class="sxs-lookup"><span data-stu-id="8f219-112">The Northwind sample database.</span></span> <span data-ttu-id="8f219-113">Stažení této ukázkové databáze, najdete v článku stránce pro stažení [ukázkové databáze systému SQL Server](http://go.microsoft.com/fwlink/?linkid=24758).</span><span class="sxs-lookup"><span data-stu-id="8f219-113">To download this sample database, see the download page, [Sample Databases for SQL Server](http://go.microsoft.com/fwlink/?linkid=24758).</span></span>  
  
## <a name="wcf-data-services-quickstart-tasks"></a><span data-ttu-id="8f219-114">Rychlé spuštění úlohy služeb WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="8f219-114">WCF Data Services Quickstart Tasks</span></span>  
 [<span data-ttu-id="8f219-115">Vytvoření datové služby</span><span class="sxs-lookup"><span data-stu-id="8f219-115">Creating the Data Service</span></span>](../../../../docs/framework/data/wcf/creating-the-data-service.md)  
 <span data-ttu-id="8f219-116">Definování [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikace, definovat datového modelu, vytvořit službu data a povolení přístupu k prostředkům.</span><span class="sxs-lookup"><span data-stu-id="8f219-116">Define the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] application, define the data model, create the data service, and enable access to resources.</span></span>  
  
 [<span data-ttu-id="8f219-117">Přístup ke službě z webového prohlížeče</span><span class="sxs-lookup"><span data-stu-id="8f219-117">Accessing the Service from a Web Browser</span></span>](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)  
 <span data-ttu-id="8f219-118">Spusťte službu ze sady Visual Studio a získat přístup ke službě odesílá požadavky HTTP GET prostřednictvím webového prohlížeče do zveřejněné informačního kanálu.</span><span class="sxs-lookup"><span data-stu-id="8f219-118">Start the service from Visual Studio and access the service by submitting HTTP GET requests through a Web browser to the exposed feed.</span></span>  
  
 [<span data-ttu-id="8f219-119">Vytvoření klientské aplikace .NET Framework</span><span class="sxs-lookup"><span data-stu-id="8f219-119">Creating the .NET Framework Client Application</span></span>](../../../../docs/framework/data/wcf/creating-the-dotnet-client-application-wcf-data-services-quickstart.md)  
 <span data-ttu-id="8f219-120">Vytvoření [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] klientská aplikace používat [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] kanálu, vazby dat k ovládacím prvkům Windows, změnit data vázané ovládací prvky a potom odešlete změny zpátky na službu data.</span><span class="sxs-lookup"><span data-stu-id="8f219-120">Create a [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] client application to consume the [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed, bind data to Windows controls, change data in the bound controls, and then send the changes back to the data service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8f219-121">Soubory projektu z dokončené verze rychlého startu si můžete stáhnout z [Ukázky WCF Data Services dokumentaci](http://go.microsoft.com/fwlink/?LinkId=179994) stránky.</span><span class="sxs-lookup"><span data-stu-id="8f219-121">Project files from a completed version of the quickstart can be downloaded from the [WCF Data Services Documentation Samples](http://go.microsoft.com/fwlink/?LinkId=179994) page.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="8f219-122">Další kroky</span><span class="sxs-lookup"><span data-stu-id="8f219-122">Next Steps</span></span>  
 <span data-ttu-id="8f219-123">[Spustit Rychlé spuštění](../../../../docs/framework/data/wcf/creating-the-data-service.md).</span><span class="sxs-lookup"><span data-stu-id="8f219-123">[Start the Quickstart](../../../../docs/framework/data/wcf/creating-the-data-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f219-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="8f219-124">See Also</span></span>  
 [<span data-ttu-id="8f219-125">ADO.NET Entity Framework</span><span class="sxs-lookup"><span data-stu-id="8f219-125">ADO.NET Entity Framework</span></span>](../../../../docs/framework/data/adonet/ef/index.md)
