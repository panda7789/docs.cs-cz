---
title: "Rychlý start (služby WCF Data Services)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF Data Services, quick-start example
- WCF Data Services, Entity Data Model (EDM) service
ms.assetid: 7b18ca1e-d4d6-4c7a-afb9-ce3cebb98a8d
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 08296be1002ee50e18a45c546645f4cc117d6bb5
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="quickstart-wcf-data-services"></a><span data-ttu-id="5cc90-102">Rychlý start (služby WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="5cc90-102">Quickstart (WCF Data Services)</span></span>
<span data-ttu-id="5cc90-103">Tento rychlý Start umožňuje seznámit se s [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] a [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] prostřednictvím řadu úloh, které podporují témata v [Začínáme](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="5cc90-103">This quickstart helps you become familiar with [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] and the [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] through a series of tasks that support the topics in [Getting Started](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md).</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="5cc90-104">Co se dozvíte</span><span class="sxs-lookup"><span data-stu-id="5cc90-104">What You Will Learn</span></span>  
 <span data-ttu-id="5cc90-105">První úlohou tento rychlý start ukazuje, jak vytvořit službu data ke zveřejnění [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] kanálu z ukázková databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="5cc90-105">The first task in this quickstart shows how to create a data service to expose an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed from the Northwind sample database.</span></span> <span data-ttu-id="5cc90-106">V následujících tématech, bude přístup [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] kanálu pomocí webového prohlížeče a také vytvořit [!INCLUDE[avalon1](../../../../includes/avalon1-md.md)] klientskou aplikaci, která využívá [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] kanálu pomocí knihovny klienta.</span><span class="sxs-lookup"><span data-stu-id="5cc90-106">In later topics, you will access the [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed by using a Web browser, and also create a [!INCLUDE[avalon1](../../../../includes/avalon1-md.md)] client application that consumes the [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed by using client libraries.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="5cc90-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5cc90-107">Prerequisites</span></span>  
 <span data-ttu-id="5cc90-108">Chcete-li dokončit tento rychlý start, je nutné nainstalovat následující součásti:</span><span class="sxs-lookup"><span data-stu-id="5cc90-108">To complete this quickstart, you must install the following components:</span></span>  
  
-   [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]<span data-ttu-id="5cc90-109">.</span><span class="sxs-lookup"><span data-stu-id="5cc90-109">.</span></span>  
  
-   <span data-ttu-id="5cc90-110">Instance [!INCLUDE[msCoName](../../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5cc90-110">An instance of [!INCLUDE[msCoName](../../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="5cc90-111">To zahrnuje SQL Server Express, který je zahrnutý ve výchozí instalaci [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5cc90-111">This includes SQL Server Express, which is included in a default installation of [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)].</span></span>  
  
-   <span data-ttu-id="5cc90-112">Ukázkovou databázi Northwind</span><span class="sxs-lookup"><span data-stu-id="5cc90-112">The Northwind sample database.</span></span> <span data-ttu-id="5cc90-113">Stažení této ukázkové databáze, najdete v článku stránce pro stažení [ukázkové databáze systému SQL Server](http://go.microsoft.com/fwlink/?linkid=24758).</span><span class="sxs-lookup"><span data-stu-id="5cc90-113">To download this sample database, see the download page, [Sample Databases for SQL Server](http://go.microsoft.com/fwlink/?linkid=24758).</span></span>  
  
## <a name="wcf-data-services-quickstart-tasks"></a><span data-ttu-id="5cc90-114">Rychlé spuštění úlohy služeb WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="5cc90-114">WCF Data Services Quickstart Tasks</span></span>  
 [<span data-ttu-id="5cc90-115">Vytváření datové služby</span><span class="sxs-lookup"><span data-stu-id="5cc90-115">Creating the Data Service</span></span>](../../../../docs/framework/data/wcf/creating-the-data-service.md)  
 <span data-ttu-id="5cc90-116">Definování [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikace, definovat datového modelu, vytvořit službu data a povolení přístupu k prostředkům.</span><span class="sxs-lookup"><span data-stu-id="5cc90-116">Define the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] application, define the data model, create the data service, and enable access to resources.</span></span>  
  
 [<span data-ttu-id="5cc90-117">Přístupu ke službě z webového prohlížeče</span><span class="sxs-lookup"><span data-stu-id="5cc90-117">Accessing the Service from a Web Browser</span></span>](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)  
 <span data-ttu-id="5cc90-118">Spusťte službu z [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] a přístup ke službě odesláním požadavky HTTP GET prostřednictvím webového prohlížeče do zveřejněné informačního kanálu.</span><span class="sxs-lookup"><span data-stu-id="5cc90-118">Start the service from [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] and access the service by submitting HTTP GET requests through a Web browser to the exposed feed.</span></span>  
  
 [<span data-ttu-id="5cc90-119">Vytvoření aplikace klienta rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="5cc90-119">Creating the .NET Framework Client Application</span></span>](../../../../docs/framework/data/wcf/creating-the-dotnet-client-application-wcf-data-services-quickstart.md)  
 <span data-ttu-id="5cc90-120">Vytvoření [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] klientská aplikace používat [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] kanálu, vazby dat k ovládacím prvkům Windows, změnit data vázané ovládací prvky a potom odešlete změny zpátky na službu data.</span><span class="sxs-lookup"><span data-stu-id="5cc90-120">Create a [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] client application to consume the [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed, bind data to Windows controls, change data in the bound controls, and then send the changes back to the data service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5cc90-121">Soubory projektu z dokončené verze rychlého startu si můžete stáhnout z [Ukázky WCF Data Services dokumentaci](http://go.microsoft.com/fwlink/?LinkId=179994) stránky.</span><span class="sxs-lookup"><span data-stu-id="5cc90-121">Project files from a completed version of the quickstart can be downloaded from the [WCF Data Services Documentation Samples](http://go.microsoft.com/fwlink/?LinkId=179994) page.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="5cc90-122">Další kroky</span><span class="sxs-lookup"><span data-stu-id="5cc90-122">Next Steps</span></span>  
 <span data-ttu-id="5cc90-123">[Spustit Rychlé spuštění](../../../../docs/framework/data/wcf/creating-the-data-service.md).</span><span class="sxs-lookup"><span data-stu-id="5cc90-123">[Start the Quickstart](../../../../docs/framework/data/wcf/creating-the-data-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5cc90-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="5cc90-124">See Also</span></span>  
 [<span data-ttu-id="5cc90-125">ADO.NET Entity Framework</span><span class="sxs-lookup"><span data-stu-id="5cc90-125">ADO.NET Entity Framework</span></span>](../../../../docs/framework/data/adonet/ef/index.md)
