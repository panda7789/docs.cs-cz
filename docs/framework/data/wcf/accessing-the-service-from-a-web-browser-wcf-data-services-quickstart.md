---
title: Přístup ke službě z webového prohlížeče (rychlý Start WCF Data Services)
ms.date: 03/30/2017
ms.assetid: 5a6fa180-3094-4e6e-ba2b-8c80975d18d1
ms.openlocfilehash: d89f84cd3ea4f56bbae34cbefe0c3891df96fa8b
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2019
ms.locfileid: "70894332"
---
# <a name="accessing-the-service-from-a-web-browser-wcf-data-services-quickstart"></a><span data-ttu-id="ec674-102">Přístup ke službě z webového prohlížeče (rychlý Start WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="ec674-102">Accessing the Service from a Web Browser (WCF Data Services Quickstart)</span></span>

<span data-ttu-id="ec674-103">Toto je druhý úkol rychlého startu WCF Data Services.</span><span class="sxs-lookup"><span data-stu-id="ec674-103">This is the second task of the WCF Data Services quickstart.</span></span> <span data-ttu-id="ec674-104">V této úloze spustíte WCF Data Services ze sady Visual Studio a případně zakážete čtení informačního kanálu ve webovém prohlížeči.</span><span class="sxs-lookup"><span data-stu-id="ec674-104">In this task, you start the WCF Data Services from Visual Studio and optionally disable feed reading in the Web browser.</span></span> <span data-ttu-id="ec674-105">Pak načtete dokument definice služby a také prostředky datové služby přístupu odesláním požadavků HTTP GET prostřednictvím webového prohlížeče na vystavené prostředky.</span><span class="sxs-lookup"><span data-stu-id="ec674-105">You then retrieve the service definition document as well as access data service resources by submitting HTTP GET requests through a Web browser to the exposed resources.</span></span>

> [!NOTE]
> <span data-ttu-id="ec674-106">Ve výchozím nastavení Visual Studio automaticky přiřadí číslo `localhost` portu identifikátoru URI ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="ec674-106">By default, Visual Studio auto-assigns a port number to the `localhost` URI on your computer.</span></span> <span data-ttu-id="ec674-107">Tato úloha používá číslo `12345` portu v příkladech identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="ec674-107">This task uses the port number `12345` in the URI examples.</span></span> <span data-ttu-id="ec674-108">Další informace o tom, jak nastavit konkrétní číslo portu v projektu sady Visual Studio, najdete v tématu [Vytvoření datové služby](creating-the-data-service.md).</span><span class="sxs-lookup"><span data-stu-id="ec674-108">For more information about how to set a specific port number in your Visual Studio project see [Creating the Data Service](creating-the-data-service.md).</span></span>

## <a name="to-request-the-default-service-document-by-using-internet-explorer"></a><span data-ttu-id="ec674-109">Vyžádání výchozího dokumentu služby pomocí aplikace Internet Explorer</span><span class="sxs-lookup"><span data-stu-id="ec674-109">To request the default service document by using Internet Explorer</span></span>

1. <span data-ttu-id="ec674-110">V aplikaci Internet Explorer v nabídce **nástroje** vyberte **Možnosti Internetu**, klikněte na kartu **obsah** , klikněte na nastavení a zrušte zaškrtnutí **Možnosti** **zapnout zobrazování informačního kanálu**.</span><span class="sxs-lookup"><span data-stu-id="ec674-110">In Internet Explorer, from the **Tools** menu, select **Internet Options**, click the **Content** tab, click **Settings**, and clear **Turn on feed viewing**.</span></span>

     <span data-ttu-id="ec674-111">Tím se zajistí, že čtení informačního kanálu je zakázané.</span><span class="sxs-lookup"><span data-stu-id="ec674-111">This makes sure that feed reading is disabled.</span></span> <span data-ttu-id="ec674-112">Pokud tuto funkci nezakážete, webový prohlížeč bude s vráceným dokumentem AtomPub zacházet jako s datovým kanálem XML namísto zobrazení nezpracovaných dat XML.</span><span class="sxs-lookup"><span data-stu-id="ec674-112">If you do not disable this functionality, then the Web browser will treat the returned AtomPub encoded document as an XML feed instead of displaying the raw XML data.</span></span>

    > [!NOTE]
    > <span data-ttu-id="ec674-113">Pokud Váš prohlížeč nemůže informační kanál zobrazit jako nezpracovaná data XML, je vhodné zobrazit informační kanál jako zdrojový kód stránky.</span><span class="sxs-lookup"><span data-stu-id="ec674-113">If your browser cannot display the feed as raw XML data, you should still be able to view the feed as the source code for the page.</span></span>

2. <span data-ttu-id="ec674-114">V aplikaci Visual Studio stiskněte klávesu **F5** a spusťte ladění aplikace.</span><span class="sxs-lookup"><span data-stu-id="ec674-114">In Visual Studio, press the **F5** key to start debugging the application.</span></span>

3. <span data-ttu-id="ec674-115">Otevřete webový prohlížeč na místním počítači.</span><span class="sxs-lookup"><span data-stu-id="ec674-115">Open a Web browser on the local computer.</span></span> <span data-ttu-id="ec674-116">Do adresního řádku zadejte následující identifikátor URI:</span><span class="sxs-lookup"><span data-stu-id="ec674-116">In the address bar, enter the following URI:</span></span>

    ```http
    http://localhost:12345/northwind.svc
    ```

     <span data-ttu-id="ec674-117">Tím se vrátí výchozí dokument služby, který obsahuje seznam sad entit, které jsou zpřístupněny touto datovou službou.</span><span class="sxs-lookup"><span data-stu-id="ec674-117">This returns the default service document, which contains a list of entity sets that are exposed by this data service.</span></span>

## <a name="to-access-entity-set-resources-from-a-web-browser"></a><span data-ttu-id="ec674-118">Přístup k prostředkům sady entit z webového prohlížeče</span><span class="sxs-lookup"><span data-stu-id="ec674-118">To access entity set resources from a Web browser</span></span>

1. <span data-ttu-id="ec674-119">Do adresního řádku webového prohlížeče zadejte následující identifikátor URI:</span><span class="sxs-lookup"><span data-stu-id="ec674-119">In the address bar of your Web browser, enter the following URI:</span></span>

    ```http
    http://localhost:12345/northwind.svc/Customers
    ```

     <span data-ttu-id="ec674-120">Tím se vrátí sada všech zákazníků v ukázkové databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="ec674-120">This returns a set of all customers in the Northwind sample database.</span></span>

2. <span data-ttu-id="ec674-121">Do adresního řádku webového prohlížeče zadejte následující identifikátor URI:</span><span class="sxs-lookup"><span data-stu-id="ec674-121">In the address bar of your Web browser, enter the following URI:</span></span>

    ```http
    http://localhost:12345/northwind.svc/Customers('ALFKI')
    ```

     <span data-ttu-id="ec674-122">Tím se vrátí instance entity pro konkrétního zákazníka, `ALFKI`.</span><span class="sxs-lookup"><span data-stu-id="ec674-122">This returns an entity instance for the specific customer, `ALFKI`.</span></span>

3. <span data-ttu-id="ec674-123">Do adresního řádku webového prohlížeče zadejte následující identifikátor URI:</span><span class="sxs-lookup"><span data-stu-id="ec674-123">In the address bar of your Web browser, enter the following URI:</span></span>

    ```http
    http://localhost:12345/northwind.svc/Customers('ALFKI')/Orders
    ```

     <span data-ttu-id="ec674-124">Tím se projde vztah mezi zákazníky a objednávkami a vrátí sadu všech objednávek pro konkrétního zákazníka `ALFKI`.</span><span class="sxs-lookup"><span data-stu-id="ec674-124">This traverses the relationship between customers and orders to return a set of all orders for the specific customer `ALFKI`.</span></span>

4. <span data-ttu-id="ec674-125">Do adresního řádku webového prohlížeče zadejte následující identifikátor URI:</span><span class="sxs-lookup"><span data-stu-id="ec674-125">In the address bar of your Web browser, enter the following URI:</span></span>

    ```http
    http://localhost:12345/northwind.svc/Customers('ALFKI')/Orders?$filter=OrderID eq 10643
    ```

     <span data-ttu-id="ec674-126">Tato klauzule filtruje objednávky náležející konkrétnímu zákazníkovi `ALFKI` , takže se na základě zadané `OrderID` hodnoty vrátí jenom konkrétní objednávka.</span><span class="sxs-lookup"><span data-stu-id="ec674-126">This filters orders that belong to the specific customer `ALFKI` so that only a specific order is returned based on the supplied `OrderID` value.</span></span>

## <a name="next-steps"></a><span data-ttu-id="ec674-127">Další kroky</span><span class="sxs-lookup"><span data-stu-id="ec674-127">Next Steps</span></span>

<span data-ttu-id="ec674-128">Úspěšně jste se přistupovali k WCF Data Services z webového prohlížeče, a to v prohlížeči, který vydává požadavky HTTP GET na zadané prostředky.</span><span class="sxs-lookup"><span data-stu-id="ec674-128">You have successfully accessed the WCF Data Services from a Web browser, with the browser issuing HTTP GET requests to specified resources.</span></span> <span data-ttu-id="ec674-129">Webový prohlížeč poskytuje snadný způsob, jak experimentovat se syntaxí adresování požadavků a zobrazením výsledků.</span><span class="sxs-lookup"><span data-stu-id="ec674-129">A Web browser provides an easy way to experiment with the addressing syntax of requests and view the results.</span></span> <span data-ttu-id="ec674-130">Tato metoda ale obecně nepoužívá službu produkčních dat.</span><span class="sxs-lookup"><span data-stu-id="ec674-130">However, a production data service is not generally accessed by this method.</span></span> <span data-ttu-id="ec674-131">Aplikace obvykle komunikují s datovou službou prostřednictvím kódu aplikace nebo skriptovacích jazyků.</span><span class="sxs-lookup"><span data-stu-id="ec674-131">Typically, applications interact with the data service through application code or scripting languages.</span></span> <span data-ttu-id="ec674-132">V dalším kroku vytvoříte klientskou aplikaci, která používá klientské knihovny pro přístup k prostředkům datové služby, jako by šlo o objekty modulu CLR (Common Language Runtime):</span><span class="sxs-lookup"><span data-stu-id="ec674-132">Next, you will create a client application that uses client libraries to access data service resources as if they were common language runtime (CLR) objects:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ec674-133">Vytvoření klientské aplikace .NET Framework</span><span class="sxs-lookup"><span data-stu-id="ec674-133">Creating the .NET Framework Client Application</span></span>](creating-the-dotnet-client-application-wcf-data-services-quickstart.md)

## <a name="see-also"></a><span data-ttu-id="ec674-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ec674-134">See also</span></span>

- [<span data-ttu-id="ec674-135">Přístup k prostředkům datové služby</span><span class="sxs-lookup"><span data-stu-id="ec674-135">Accessing Data Service Resources</span></span>](accessing-data-service-resources-wcf-data-services.md)
