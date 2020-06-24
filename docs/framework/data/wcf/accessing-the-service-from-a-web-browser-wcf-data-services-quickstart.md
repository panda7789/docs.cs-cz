---
title: Přístup ke službě z webového prohlížeče (rychlý Start WCF Data Services)
description: Naučte se, jak začít WCF Data Services v aplikaci Visual Studio a zakázat čtení informačního kanálu v prohlížeči. Získejte dokument definice služby a přístup k prostředkům datové služby.
ms.date: 03/30/2017
ms.assetid: 5a6fa180-3094-4e6e-ba2b-8c80975d18d1
ms.openlocfilehash: 713436c31bc3f622c4f44a83e33fff3fcbba1c1c
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247775"
---
# <a name="accessing-the-service-from-a-web-browser-wcf-data-services-quickstart"></a><span data-ttu-id="293e0-104">Přístup ke službě z webového prohlížeče (rychlý Start WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="293e0-104">Accessing the Service from a Web Browser (WCF Data Services Quickstart)</span></span>

<span data-ttu-id="293e0-105">Toto je druhý úkol rychlého startu WCF Data Services.</span><span class="sxs-lookup"><span data-stu-id="293e0-105">This is the second task of the WCF Data Services quickstart.</span></span> <span data-ttu-id="293e0-106">V této úloze spustíte WCF Data Services ze sady Visual Studio a případně zakážete čtení informačního kanálu ve webovém prohlížeči.</span><span class="sxs-lookup"><span data-stu-id="293e0-106">In this task, you start the WCF Data Services from Visual Studio and optionally disable feed reading in the Web browser.</span></span> <span data-ttu-id="293e0-107">Pak načtete dokument definice služby a také prostředky datové služby přístupu odesláním požadavků HTTP GET prostřednictvím webového prohlížeče na vystavené prostředky.</span><span class="sxs-lookup"><span data-stu-id="293e0-107">You then retrieve the service definition document as well as access data service resources by submitting HTTP GET requests through a Web browser to the exposed resources.</span></span>

> [!NOTE]
> <span data-ttu-id="293e0-108">Ve výchozím nastavení Visual Studio automaticky přiřadí číslo portu `localhost` identifikátoru URI ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="293e0-108">By default, Visual Studio auto-assigns a port number to the `localhost` URI on your computer.</span></span> <span data-ttu-id="293e0-109">Tato úloha používá číslo portu `12345` v příkladech identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="293e0-109">This task uses the port number `12345` in the URI examples.</span></span> <span data-ttu-id="293e0-110">Další informace o tom, jak nastavit konkrétní číslo portu v projektu sady Visual Studio, najdete v tématu [Vytvoření datové služby](creating-the-data-service.md).</span><span class="sxs-lookup"><span data-stu-id="293e0-110">For more information about how to set a specific port number in your Visual Studio project see [Creating the Data Service](creating-the-data-service.md).</span></span>

## <a name="to-request-the-default-service-document-by-using-internet-explorer"></a><span data-ttu-id="293e0-111">Vyžádání výchozího dokumentu služby pomocí aplikace Internet Explorer</span><span class="sxs-lookup"><span data-stu-id="293e0-111">To request the default service document by using Internet Explorer</span></span>

1. <span data-ttu-id="293e0-112">V aplikaci Internet Explorer v nabídce **nástroje** vyberte **Možnosti Internetu**, klikněte na kartu **obsah** , klikněte na nastavení a zrušte zaškrtnutí **Možnosti** **zapnout zobrazování informačního kanálu**.</span><span class="sxs-lookup"><span data-stu-id="293e0-112">In Internet Explorer, from the **Tools** menu, select **Internet Options**, click the **Content** tab, click **Settings**, and clear **Turn on feed viewing**.</span></span>

     <span data-ttu-id="293e0-113">Tím se zajistí, že čtení informačního kanálu je zakázané.</span><span class="sxs-lookup"><span data-stu-id="293e0-113">This makes sure that feed reading is disabled.</span></span> <span data-ttu-id="293e0-114">Pokud tuto funkci nezakážete, webový prohlížeč bude s vráceným dokumentem AtomPub zacházet jako s datovým kanálem XML namísto zobrazení nezpracovaných dat XML.</span><span class="sxs-lookup"><span data-stu-id="293e0-114">If you do not disable this functionality, then the Web browser will treat the returned AtomPub encoded document as an XML feed instead of displaying the raw XML data.</span></span>

    > [!NOTE]
    > <span data-ttu-id="293e0-115">Pokud Váš prohlížeč nemůže informační kanál zobrazit jako nezpracovaná data XML, je vhodné zobrazit informační kanál jako zdrojový kód stránky.</span><span class="sxs-lookup"><span data-stu-id="293e0-115">If your browser cannot display the feed as raw XML data, you should still be able to view the feed as the source code for the page.</span></span>

2. <span data-ttu-id="293e0-116">V aplikaci Visual Studio stiskněte klávesu **F5** a spusťte ladění aplikace.</span><span class="sxs-lookup"><span data-stu-id="293e0-116">In Visual Studio, press the **F5** key to start debugging the application.</span></span>

3. <span data-ttu-id="293e0-117">Otevřete webový prohlížeč na místním počítači.</span><span class="sxs-lookup"><span data-stu-id="293e0-117">Open a Web browser on the local computer.</span></span> <span data-ttu-id="293e0-118">Do adresního řádku zadejte následující identifikátor URI:</span><span class="sxs-lookup"><span data-stu-id="293e0-118">In the address bar, enter the following URI:</span></span>

    ```http
    http://localhost:12345/northwind.svc
    ```

     <span data-ttu-id="293e0-119">Tím se vrátí výchozí dokument služby, který obsahuje seznam sad entit, které jsou zpřístupněny touto datovou službou.</span><span class="sxs-lookup"><span data-stu-id="293e0-119">This returns the default service document, which contains a list of entity sets that are exposed by this data service.</span></span>

## <a name="to-access-entity-set-resources-from-a-web-browser"></a><span data-ttu-id="293e0-120">Přístup k prostředkům sady entit z webového prohlížeče</span><span class="sxs-lookup"><span data-stu-id="293e0-120">To access entity set resources from a Web browser</span></span>

1. <span data-ttu-id="293e0-121">Do adresního řádku webového prohlížeče zadejte následující identifikátor URI:</span><span class="sxs-lookup"><span data-stu-id="293e0-121">In the address bar of your Web browser, enter the following URI:</span></span>

    ```http
    http://localhost:12345/northwind.svc/Customers
    ```

     <span data-ttu-id="293e0-122">Tím se vrátí sada všech zákazníků v ukázkové databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="293e0-122">This returns a set of all customers in the Northwind sample database.</span></span>

2. <span data-ttu-id="293e0-123">Do adresního řádku webového prohlížeče zadejte následující identifikátor URI:</span><span class="sxs-lookup"><span data-stu-id="293e0-123">In the address bar of your Web browser, enter the following URI:</span></span>

    ```http
    http://localhost:12345/northwind.svc/Customers('ALFKI')
    ```

     <span data-ttu-id="293e0-124">Tím se vrátí instance entity pro konkrétního zákazníka, `ALFKI` .</span><span class="sxs-lookup"><span data-stu-id="293e0-124">This returns an entity instance for the specific customer, `ALFKI`.</span></span>

3. <span data-ttu-id="293e0-125">Do adresního řádku webového prohlížeče zadejte následující identifikátor URI:</span><span class="sxs-lookup"><span data-stu-id="293e0-125">In the address bar of your Web browser, enter the following URI:</span></span>

    ```http
    http://localhost:12345/northwind.svc/Customers('ALFKI')/Orders
    ```

     <span data-ttu-id="293e0-126">Tím se projde vztah mezi zákazníky a objednávkami a vrátí sadu všech objednávek pro konkrétního zákazníka `ALFKI` .</span><span class="sxs-lookup"><span data-stu-id="293e0-126">This traverses the relationship between customers and orders to return a set of all orders for the specific customer `ALFKI`.</span></span>

4. <span data-ttu-id="293e0-127">Do adresního řádku webového prohlížeče zadejte následující identifikátor URI:</span><span class="sxs-lookup"><span data-stu-id="293e0-127">In the address bar of your Web browser, enter the following URI:</span></span>

    ```http
    http://localhost:12345/northwind.svc/Customers('ALFKI')/Orders?$filter=OrderID eq 10643
    ```

     <span data-ttu-id="293e0-128">Tato klauzule filtruje objednávky náležející konkrétnímu zákazníkovi `ALFKI` , takže se na základě zadané hodnoty vrátí jenom konkrétní objednávka `OrderID` .</span><span class="sxs-lookup"><span data-stu-id="293e0-128">This filters orders that belong to the specific customer `ALFKI` so that only a specific order is returned based on the supplied `OrderID` value.</span></span>

## <a name="next-steps"></a><span data-ttu-id="293e0-129">Další kroky</span><span class="sxs-lookup"><span data-stu-id="293e0-129">Next Steps</span></span>

<span data-ttu-id="293e0-130">Úspěšně jste se přistupovali k WCF Data Services z webového prohlížeče, a to v prohlížeči, který vydává požadavky HTTP GET na zadané prostředky.</span><span class="sxs-lookup"><span data-stu-id="293e0-130">You have successfully accessed the WCF Data Services from a Web browser, with the browser issuing HTTP GET requests to specified resources.</span></span> <span data-ttu-id="293e0-131">Webový prohlížeč poskytuje snadný způsob, jak experimentovat se syntaxí adresování požadavků a zobrazením výsledků.</span><span class="sxs-lookup"><span data-stu-id="293e0-131">A Web browser provides an easy way to experiment with the addressing syntax of requests and view the results.</span></span> <span data-ttu-id="293e0-132">Tato metoda ale obecně nepoužívá službu produkčních dat.</span><span class="sxs-lookup"><span data-stu-id="293e0-132">However, a production data service is not generally accessed by this method.</span></span> <span data-ttu-id="293e0-133">Aplikace obvykle komunikují s datovou službou prostřednictvím kódu aplikace nebo skriptovacích jazyků.</span><span class="sxs-lookup"><span data-stu-id="293e0-133">Typically, applications interact with the data service through application code or scripting languages.</span></span> <span data-ttu-id="293e0-134">V dalším kroku vytvoříte klientskou aplikaci, která používá klientské knihovny pro přístup k prostředkům datové služby, jako by šlo o objekty modulu CLR (Common Language Runtime):</span><span class="sxs-lookup"><span data-stu-id="293e0-134">Next, you will create a client application that uses client libraries to access data service resources as if they were common language runtime (CLR) objects:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="293e0-135">Vytvoření klientské aplikace .NET Framework</span><span class="sxs-lookup"><span data-stu-id="293e0-135">Creating the .NET Framework Client Application</span></span>](creating-the-dotnet-client-application-wcf-data-services-quickstart.md)

## <a name="see-also"></a><span data-ttu-id="293e0-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="293e0-136">See also</span></span>

- [<span data-ttu-id="293e0-137">Přístup k prostředkům datové služby</span><span class="sxs-lookup"><span data-stu-id="293e0-137">Accessing Data Service Resources</span></span>](accessing-data-service-resources-wcf-data-services.md)
