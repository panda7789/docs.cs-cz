---
title: Přístupu ke službě z webového prohlížeče (WCF Data Services – rychlý start)
ms.date: 03/30/2017
ms.assetid: 5a6fa180-3094-4e6e-ba2b-8c80975d18d1
ms.openlocfilehash: 15a74e47774c532e75eca8a60a1af3a3e4f03f58
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54591640"
---
# <a name="accessing-the-service-from-a-web-browser-wcf-data-services-quickstart"></a><span data-ttu-id="9cdf2-102">Přístupu ke službě z webového prohlížeče (WCF Data Services – rychlý start)</span><span class="sxs-lookup"><span data-stu-id="9cdf2-102">Accessing the Service from a Web Browser (WCF Data Services Quickstart)</span></span>

<span data-ttu-id="9cdf2-103">Toto je v druhé úloze tohoto rychlého startu služby WCF Data Services.</span><span class="sxs-lookup"><span data-stu-id="9cdf2-103">This is the second task of the WCF Data Services quickstart.</span></span> <span data-ttu-id="9cdf2-104">Při plnění tohoto úkolu spuštění služeb WCF Data Services ze sady Visual Studio a volitelně můžete zakázat čtení informačního kanálu ve webovém prohlížeči.</span><span class="sxs-lookup"><span data-stu-id="9cdf2-104">In this task, you start the WCF Data Services from Visual Studio and optionally disable feed reading in the Web browser.</span></span> <span data-ttu-id="9cdf2-105">Můžete pak načíst definice dokumentu služby také přístup k prostředkům datové služby, odešlete požadavky HTTP GET přes webový prohlížeč na ohrožené prostředky.</span><span class="sxs-lookup"><span data-stu-id="9cdf2-105">You then retrieve the service definition document as well as access data service resources by submitting HTTP GET requests through a Web browser to the exposed resources.</span></span>

> [!NOTE]
> <span data-ttu-id="9cdf2-106">Ve výchozím nastavení, Visual Studio automaticky přiřadí číslo portu, `localhost` identifikátor URI ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="9cdf2-106">By default, Visual Studio auto-assigns a port number to the `localhost` URI on your computer.</span></span> <span data-ttu-id="9cdf2-107">Tato úloha používá číslo portu `12345` v příkladech identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="9cdf2-107">This task uses the port number `12345` in the URI examples.</span></span> <span data-ttu-id="9cdf2-108">Další informace o tom, jak nastavit konkrétní číslo portu v projektu sady Visual Studio naleznete v tématu [vytvoření datové služby](../../../../docs/framework/data/wcf/creating-the-data-service.md).</span><span class="sxs-lookup"><span data-stu-id="9cdf2-108">For more information about how to set a specific port number in your Visual Studio project see [Creating the Data Service](../../../../docs/framework/data/wcf/creating-the-data-service.md).</span></span>

## <a name="to-request-the-default-service-document-by-using-internet-explorer"></a><span data-ttu-id="9cdf2-109">Požádat o výchozí dokument služby pomocí Internet Exploreru</span><span class="sxs-lookup"><span data-stu-id="9cdf2-109">To request the default service document by using Internet Explorer</span></span>

1.  <span data-ttu-id="9cdf2-110">V aplikaci Internet Explorer z **nástroje** nabídce vyberte možnost **Možnosti Internetu**, klikněte na tlačítko **obsahu** klikněte na tlačítko **nastavení**a zrušte zaškrtnutí  **Zapnout informačního kanálu zobrazení**.</span><span class="sxs-lookup"><span data-stu-id="9cdf2-110">In Internet Explorer, from the **Tools** menu, select **Internet Options**, click the **Content** tab, click **Settings**, and clear **Turn on feed viewing**.</span></span>

     <span data-ttu-id="9cdf2-111">Tím zajistíte, který informační kanál čtení je zakázaný.</span><span class="sxs-lookup"><span data-stu-id="9cdf2-111">This makes sure that feed reading is disabled.</span></span> <span data-ttu-id="9cdf2-112">Pokud tato funkce není zakázána, pak webový prohlížeč bude považovat za vrácené AtomPub kódovaného dokumentu XML informačního kanálu místo zobrazují se nezpracovaná data XML.</span><span class="sxs-lookup"><span data-stu-id="9cdf2-112">If you do not disable this functionality, then the Web browser will treat the returned AtomPub encoded document as an XML feed instead of displaying the raw XML data.</span></span>

    > [!NOTE]
    > <span data-ttu-id="9cdf2-113">Pokud váš prohlížeč nelze zobrazit jako nezpracovaná data XML informačního kanálu, by měl stále možné zobrazit jako zdrojový kód pro stránku informačního kanálu.</span><span class="sxs-lookup"><span data-stu-id="9cdf2-113">If your browser cannot display the feed as raw XML data, you should still be able to view the feed as the source code for the page.</span></span>

2.  <span data-ttu-id="9cdf2-114">V sadě Visual Studio, stiskněte **F5** spusťte ladění aplikace.</span><span class="sxs-lookup"><span data-stu-id="9cdf2-114">In Visual Studio, press the **F5** key to start debugging the application.</span></span>

3.  <span data-ttu-id="9cdf2-115">Otevřete webový prohlížeč v místním počítači.</span><span class="sxs-lookup"><span data-stu-id="9cdf2-115">Open a Web browser on the local computer.</span></span> <span data-ttu-id="9cdf2-116">Na panelu Adresa zadejte následující identifikátor URI:</span><span class="sxs-lookup"><span data-stu-id="9cdf2-116">In the address bar, enter the following URI:</span></span>

    ```
    http://localhost:12345/northwind.svc
    ```

     <span data-ttu-id="9cdf2-117">Vrátí výchozí dokument služby, který obsahuje seznam sad entit, které jsou vystaveny touto službou data.</span><span class="sxs-lookup"><span data-stu-id="9cdf2-117">This returns the default service document, which contains a list of entity sets that are exposed by this data service.</span></span>

## <a name="to-access-entity-set-resources-from-a-web-browser"></a><span data-ttu-id="9cdf2-118">Pro přístup k entitě nastavit prostředky z webového prohlížeče</span><span class="sxs-lookup"><span data-stu-id="9cdf2-118">To access entity set resources from a Web browser</span></span>

1.  <span data-ttu-id="9cdf2-119">Do adresního řádku webového prohlížeče zadejte následující identifikátor URI:</span><span class="sxs-lookup"><span data-stu-id="9cdf2-119">In the address bar of your Web browser, enter the following URI:</span></span>

    ```
    http://localhost:12345/northwind.svc/Customers
    ```

     <span data-ttu-id="9cdf2-120">Vrátí sadu všem zákazníkům v ukázkové databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="9cdf2-120">This returns a set of all customers in the Northwind sample database.</span></span>

2.  <span data-ttu-id="9cdf2-121">Do adresního řádku webového prohlížeče zadejte následující identifikátor URI:</span><span class="sxs-lookup"><span data-stu-id="9cdf2-121">In the address bar of your Web browser, enter the following URI:</span></span>

    ```
    http://localhost:12345/northwind.svc/Customers('ALFKI')
    ```

     <span data-ttu-id="9cdf2-122">Vrátí instanci entity pro konkrétního zákazníka `ALFKI`.</span><span class="sxs-lookup"><span data-stu-id="9cdf2-122">This returns an entity instance for the specific customer, `ALFKI`.</span></span>

3.  <span data-ttu-id="9cdf2-123">Do adresního řádku webového prohlížeče zadejte následující identifikátor URI:</span><span class="sxs-lookup"><span data-stu-id="9cdf2-123">In the address bar of your Web browser, enter the following URI:</span></span>

    ```
    http://localhost:12345/northwind.svc/Customers('ALFKI')/Orders
    ```

     <span data-ttu-id="9cdf2-124">To prochází přes vztah mezi zákazníky a objednávkami vrátit sadu všech objednávek pro konkrétního zákazníka `ALFKI`.</span><span class="sxs-lookup"><span data-stu-id="9cdf2-124">This traverses the relationship between customers and orders to return a set of all orders for the specific customer `ALFKI`.</span></span>

4.  <span data-ttu-id="9cdf2-125">Do adresního řádku webového prohlížeče zadejte následující identifikátor URI:</span><span class="sxs-lookup"><span data-stu-id="9cdf2-125">In the address bar of your Web browser, enter the following URI:</span></span>

    ```
    http://localhost:12345/northwind.svc/Customers('ALFKI')/Orders?$filter=OrderID eq 10643
    ```

     <span data-ttu-id="9cdf2-126">Tím se vyfiltrují objednávky, které patří do konkrétního zákazníka `ALFKI` tak, aby se vrátí pouze konkrétní pořadí na základě na zadané `OrderID` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="9cdf2-126">This filters orders that belong to the specific customer `ALFKI` so that only a specific order is returned based on the supplied `OrderID` value.</span></span>

## <a name="next-steps"></a><span data-ttu-id="9cdf2-127">Další kroky</span><span class="sxs-lookup"><span data-stu-id="9cdf2-127">Next Steps</span></span>

<span data-ttu-id="9cdf2-128">Služby WCF Data Services mají úspěšně přistupovat z webového prohlížeče a prohlížeč vydávající požadavky HTTP GET pro zadané prostředky.</span><span class="sxs-lookup"><span data-stu-id="9cdf2-128">You have successfully accessed the WCF Data Services from a Web browser, with the browser issuing HTTP GET requests to specified resources.</span></span> <span data-ttu-id="9cdf2-129">Webový prohlížeč poskytuje snadný způsob, jak experimentovat s adresování syntaxe požadavky a prohlédněte si výsledky.</span><span class="sxs-lookup"><span data-stu-id="9cdf2-129">A Web browser provides an easy way to experiment with the addressing syntax of requests and view the results.</span></span> <span data-ttu-id="9cdf2-130">Ale za touto metodou obvykle nepřistupuje produkční datové služby.</span><span class="sxs-lookup"><span data-stu-id="9cdf2-130">However, a production data service is not generally accessed by this method.</span></span> <span data-ttu-id="9cdf2-131">Obvykle aplikace interakci se službou data prostřednictvím aplikace kódu nebo skriptovací jazyky.</span><span class="sxs-lookup"><span data-stu-id="9cdf2-131">Typically, applications interact with the data service through application code or scripting languages.</span></span> <span data-ttu-id="9cdf2-132">V dalším kroku vytvoříte klientskou aplikaci, která používá klientské knihovny pro přístup k prostředkům datové služby, jako by byly common language runtime (CLR) objekty:</span><span class="sxs-lookup"><span data-stu-id="9cdf2-132">Next, you will create a client application that uses client libraries to access data service resources as if they were common language runtime (CLR) objects:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="9cdf2-133">Vytvoření klientské aplikace .NET Framework</span><span class="sxs-lookup"><span data-stu-id="9cdf2-133">Creating the .NET Framework Client Application</span></span>](../../../../docs/framework/data/wcf/creating-the-dotnet-client-application-wcf-data-services-quickstart.md)

## <a name="see-also"></a><span data-ttu-id="9cdf2-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9cdf2-134">See also</span></span>

- [<span data-ttu-id="9cdf2-135">Přístup k prostředkům datové služby</span><span class="sxs-lookup"><span data-stu-id="9cdf2-135">Accessing Data Service Resources</span></span>](../../../../docs/framework/data/wcf/accessing-data-service-resources-wcf-data-services.md)
