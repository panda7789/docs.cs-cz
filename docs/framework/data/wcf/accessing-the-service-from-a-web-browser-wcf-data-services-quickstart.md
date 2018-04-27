---
title: Přístupu ke službě z webového prohlížeče (rychlý start WCF Data Services)
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5a6fa180-3094-4e6e-ba2b-8c80975d18d1
caps.latest.revision: 4
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c9ae96facd79ae3d268c630ff7bf8adf411eb775
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="accessing-the-service-from-a-web-browser-wcf-data-services-quickstart"></a><span data-ttu-id="8413c-102">Přístupu ke službě z webového prohlížeče (rychlý start WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="8413c-102">Accessing the Service from a Web Browser (WCF Data Services Quickstart)</span></span>
<span data-ttu-id="8413c-103">V této úloze se spustí [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] ze sady Visual Studio a volitelně zakázat kanál čtení ve webovém prohlížeči.</span><span class="sxs-lookup"><span data-stu-id="8413c-103">In this task, you will start the [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] from Visual Studio and optionally disable feed reading in the Web browser.</span></span> <span data-ttu-id="8413c-104">Můžete se pak načtení dokumentu definice služby a také přístup k prostředkům služby data odesláním požadavky HTTP GET prostřednictvím webového prohlížeče na zveřejněné prostředky.</span><span class="sxs-lookup"><span data-stu-id="8413c-104">You will then retrieve the service definition document as well as access data service resources by submitting HTTP GET requests through a Web browser to the exposed resources.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8413c-105">Ve výchozím nastavení, Visual Studio automaticky přiřadí číslo portu, `localhost` URI ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="8413c-105">By default, Visual Studio auto-assigns a port number to the `localhost` URI on your computer.</span></span> <span data-ttu-id="8413c-106">Tato úloha používá číslo portu `12345` v příkladech identifikátor URI.</span><span class="sxs-lookup"><span data-stu-id="8413c-106">This task uses the port number `12345` in the URI examples.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="8413c-107"> jak nastavit číslo specifického portu najdete v tématu vaše sady Visual Studio projektu [vytváření službu Data](../../../../docs/framework/data/wcf/creating-the-data-service.md).</span><span class="sxs-lookup"><span data-stu-id="8413c-107"> how to set a specific port number in your Visual Studio project see [Creating the Data Service](../../../../docs/framework/data/wcf/creating-the-data-service.md).</span></span>  
  
### <a name="to-request-the-default-service-document-by-using-internet-explorer"></a><span data-ttu-id="8413c-108">Požádat o výchozí dokument služby v aplikaci Internet Explorer</span><span class="sxs-lookup"><span data-stu-id="8413c-108">To request the default service document by using Internet Explorer</span></span>  
  
1.  <span data-ttu-id="8413c-109">V aplikaci Internet Explorer z **nástroje** nabídce vyberte možnost **Možnosti Internetu**, klikněte na tlačítko **obsahu** , klikněte na **nastavení**a zrušte zaškrtnutí  **Zapnout informačního kanálu zobrazení**.</span><span class="sxs-lookup"><span data-stu-id="8413c-109">In Internet Explorer, from the **Tools** menu, select **Internet Options**, click the **Content** tab, click **Settings**, and clear **Turn on feed viewing**.</span></span>  
  
     <span data-ttu-id="8413c-110">Tím je zajištěno, který informační kanál čtení je zakázána.</span><span class="sxs-lookup"><span data-stu-id="8413c-110">This makes sure that feed reading is disabled.</span></span> <span data-ttu-id="8413c-111">Pokud tuto funkci nezakážete, pak webový prohlížeč bude považovat za vrácený AtomPub kódovaného dokumentu XML kanálu místo nezpracovaná data XML.</span><span class="sxs-lookup"><span data-stu-id="8413c-111">If you do not disable this functionality, then the Web browser will treat the returned AtomPub encoded document as an XML feed instead of displaying the raw XML data.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8413c-112">Pokud váš prohlížeč nemůže zobrazit informační kanál jako nezpracovaná data XML, měli stále mohli zobrazit informační kanál jako zdrojový kód pro stránku.</span><span class="sxs-lookup"><span data-stu-id="8413c-112">If your browser cannot display the feed as raw XML data, you should still be able to view the feed as the source code for the page.</span></span>  
  
2.  <span data-ttu-id="8413c-113">Ve Visual Studiu stisknutím klávesy F5 spusťte ladění aplikace.</span><span class="sxs-lookup"><span data-stu-id="8413c-113">In Visual Studio, press the F5 key to start debugging the application.</span></span>  
  
3.  <span data-ttu-id="8413c-114">Otevřete webový prohlížeč v místním počítači.</span><span class="sxs-lookup"><span data-stu-id="8413c-114">Open a Web browser on the local computer.</span></span> <span data-ttu-id="8413c-115">Na panelu Adresa zadejte identifikátor URI následující:</span><span class="sxs-lookup"><span data-stu-id="8413c-115">In the address bar, enter the following URI:</span></span>  
  
    ```  
    http://localhost:12345/northwind.svc  
    ```  
  
     <span data-ttu-id="8413c-116">Vrátí výchozí dokument služby, který obsahuje seznam sad entit zpřístupněných tuto službu data.</span><span class="sxs-lookup"><span data-stu-id="8413c-116">This returns the default service document, which contains a list of entity sets that are exposed by this data service.</span></span>  
  
### <a name="to-access-entity-set-resources-from-a-web-browser"></a><span data-ttu-id="8413c-117">Pro přístup k entity nastavit prostředky z webového prohlížeče</span><span class="sxs-lookup"><span data-stu-id="8413c-117">To access entity set resources from a Web browser</span></span>  
  
1.  <span data-ttu-id="8413c-118">Do adresního řádku webového prohlížeče zadejte následující identifikátor URI:</span><span class="sxs-lookup"><span data-stu-id="8413c-118">In the address bar of your Web browser, enter the following URI:</span></span>  
  
    ```  
    http://localhost:12345/northwind.svc/Customers  
    ```  
  
     <span data-ttu-id="8413c-119">Vrátí sadu odběratelů v ukázková databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="8413c-119">This returns a set of all customers in the Northwind sample database.</span></span>  
  
2.  <span data-ttu-id="8413c-120">Do adresního řádku webového prohlížeče zadejte následující identifikátor URI:</span><span class="sxs-lookup"><span data-stu-id="8413c-120">In the address bar of your Web browser, enter the following URI:</span></span>  
  
    ```  
    http://localhost:12345/northwind.svc/Customers('ALFKI')  
    ```  
  
     <span data-ttu-id="8413c-121">Vrátí instanci entity pro konkrétního zákazníka `ALFKI`.</span><span class="sxs-lookup"><span data-stu-id="8413c-121">This returns an entity instance for the specific customer, `ALFKI`.</span></span>  
  
3.  <span data-ttu-id="8413c-122">Do adresního řádku webového prohlížeče zadejte následující identifikátor URI:</span><span class="sxs-lookup"><span data-stu-id="8413c-122">In the address bar of your Web browser, enter the following URI:</span></span>  
  
    ```  
    http://localhost:12345/northwind.svc/Customers('ALFKI')/Orders  
    ```  
  
     <span data-ttu-id="8413c-123">To prochází vztah mezi zákazníci a objednávky vrátit sadu všechny objednávky pro konkrétního zákazníka `ALFKI`.</span><span class="sxs-lookup"><span data-stu-id="8413c-123">This traverses the relationship between customers and orders to return a set of all orders for the specific customer `ALFKI`.</span></span>  
  
4.  <span data-ttu-id="8413c-124">Do adresního řádku webového prohlížeče zadejte následující identifikátor URI:</span><span class="sxs-lookup"><span data-stu-id="8413c-124">In the address bar of your Web browser, enter the following URI:</span></span>  
  
    ```  
    http://localhost:12345/northwind.svc/Customers('ALFKI')/Orders?$filter=OrderID eq 10643  
    ```  
  
     <span data-ttu-id="8413c-125">Tím se odfiltrují objednávky, které patří do konkrétního zákazníka `ALFKI` tak, aby konkrétní pořadí dochází na základě zadaných `OrderID` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="8413c-125">This filters orders that belong to the specific customer `ALFKI` so that only a specific order is returned based on the supplied `OrderID` value.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="8413c-126">Další kroky</span><span class="sxs-lookup"><span data-stu-id="8413c-126">Next Steps</span></span>  
 <span data-ttu-id="8413c-127">Úspěšně jste získali přístup [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] z webového prohlížeče, pomocí prohlížeče vydání HTTP GET požadavky do zadané prostředky.</span><span class="sxs-lookup"><span data-stu-id="8413c-127">You have successfully accessed the [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] from a Web browser, with the browser issuing HTTP GET requests to specified resources.</span></span> <span data-ttu-id="8413c-128">Webový prohlížeč poskytuje snadný způsob, jak experimentovat s adresování syntaxe požadavků a zobrazit výsledky.</span><span class="sxs-lookup"><span data-stu-id="8413c-128">A Web browser provides an easy way to experiment with the addressing syntax of requests and view the results.</span></span> <span data-ttu-id="8413c-129">Datové služby produkční není však přístup obecně touto metodou.</span><span class="sxs-lookup"><span data-stu-id="8413c-129">However, a production data service is not generally accessed by this method.</span></span> <span data-ttu-id="8413c-130">Obvykle aplikace komunikovat se službou data prostřednictvím aplikace kód nebo skriptovací jazyky.</span><span class="sxs-lookup"><span data-stu-id="8413c-130">Typically, applications interact with the data service through application code or scripting languages.</span></span> <span data-ttu-id="8413c-131">V dalším kroku vytvoříte klientská aplikace, která používá klientské knihovny pro přístup k prostředkům služby data, jako kdyby byly běžně používané objekty language runtime (CLR):</span><span class="sxs-lookup"><span data-stu-id="8413c-131">Next, you will create a client application that uses client libraries to access data service resources as if they were common language runtime (CLR) objects:</span></span>  
  
 [<span data-ttu-id="8413c-132">Vytvoření klientské aplikace .NET Framework</span><span class="sxs-lookup"><span data-stu-id="8413c-132">Creating the .NET Framework Client Application</span></span>](../../../../docs/framework/data/wcf/creating-the-dotnet-client-application-wcf-data-services-quickstart.md)  
  
## <a name="see-also"></a><span data-ttu-id="8413c-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="8413c-133">See Also</span></span>  
 [<span data-ttu-id="8413c-134">Přístup k prostředkům datové služby</span><span class="sxs-lookup"><span data-stu-id="8413c-134">Accessing Data Service Resources</span></span>](../../../../docs/framework/data/wcf/accessing-data-service-resources-wcf-data-services.md)
