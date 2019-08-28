---
title: Integrace mezipaměti ASP.NET
ms.date: 03/30/2017
ms.assetid: f581923a-8a72-42fc-bd6a-46de2aaeecc1
ms.openlocfilehash: 56f686b83deb576f1245a9d4b9df2df433ea1e2f
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045781"
---
# <a name="aspnet-caching-integration"></a><span data-ttu-id="ed196-102">Integrace mezipaměti ASP.NET</span><span class="sxs-lookup"><span data-stu-id="ed196-102">ASP.NET Caching Integration</span></span>

<span data-ttu-id="ed196-103">Tato ukázka předvádí, jak využít výstupní mezipaměť ASP.NET s modelem programování webového HTTP WCF.</span><span class="sxs-lookup"><span data-stu-id="ed196-103">This sample demonstrates how to utilize the ASP.NET output cache with the WCF WEB HTTP programming model.</span></span> <span data-ttu-id="ed196-104">Toto téma se zaměřuje na funkci integrace výstupní mezipaměti ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="ed196-104">This topic focuses on the ASP.NET output cache integration feature.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="ed196-105">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="ed196-105">Demonstrates</span></span>

<span data-ttu-id="ed196-106">Integrace s výstupní mezipamětí ASP.NET</span><span class="sxs-lookup"><span data-stu-id="ed196-106">Integration with the ASP.NET Output Cache</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ed196-107">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="ed196-107">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ed196-108">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="ed196-108">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="ed196-109">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="ed196-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ed196-110">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="ed196-110">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\AspNetCachingIntegration`

## <a name="discussion"></a><span data-ttu-id="ed196-111">Účely</span><span class="sxs-lookup"><span data-stu-id="ed196-111">Discussion</span></span>

<span data-ttu-id="ed196-112">Ukázka používá <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> pro použití ukládání výstupu ASP.NET do mezipaměti s využitím služby Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="ed196-112">The sample uses the <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> to utilize ASP.NET output caching with the Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="ed196-113"><xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> Je aplikován na operace služby a poskytuje název profilu mezipaměti v konfiguračním souboru, který by měl být použit na odpovědi z dané operace.</span><span class="sxs-lookup"><span data-stu-id="ed196-113">The <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> is applied to service operations, and provides the name of a cache profile in a configuration file that should be applied to responses from the given operation.</span></span>

<span data-ttu-id="ed196-114">V souboru Service.cs ukázkového projektu `GetCustomer` služby jsou <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute>operace a `GetCustomers` označeny pomocí příkazu, který poskytuje název profilu mezipaměti "CacheFor60Seconds".</span><span class="sxs-lookup"><span data-stu-id="ed196-114">In the Service.cs file of the sample Service project, both the `GetCustomer` and `GetCustomers` operations are marked with the <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute>, which provides the cache profile name "CacheFor60Seconds".</span></span> <span data-ttu-id="ed196-115">V souboru Web. config projektu služby je profil mezipaměti "CacheFor60Seconds" uveden pod <`caching`> prvek <`system.web`>.</span><span class="sxs-lookup"><span data-stu-id="ed196-115">In the Web.config file of the Service project, the cache profile "CacheFor60Seconds" is provided under the <`caching`> element of <`system.web`>.</span></span> <span data-ttu-id="ed196-116">Pro tento profil mezipaměti je hodnota `duration` atributu "60", takže odpovědi spojené s tímto profilem jsou uloženy v mezipaměti ve výstupní mezipaměti ASP.NET po dobu 60 sekund.</span><span class="sxs-lookup"><span data-stu-id="ed196-116">For this cache profile, the value of the `duration` attribute is "60", so responses associated with this profile are cached in the ASP.NET output cache for 60 seconds.</span></span> <span data-ttu-id="ed196-117">Také pro tento profil `varmByParam` mezipaměti je atribut nastaven na "formát", takže požadavky s různými hodnotami `format` pro parametr řetězce dotazu mají své odpovědi v mezipaměti odděleně.</span><span class="sxs-lookup"><span data-stu-id="ed196-117">Also, for this cache profile, the `varmByParam` attribute is set to "format" so requests with different values for the `format` query string parameter have their responses cached separately.</span></span> <span data-ttu-id="ed196-118">Nakonec `varyByHeader` atribut profilu mezipaměti je nastaven na hodnotu přijmout, takže požadavky s různými hodnotami Accept Header mají své odpovědi v mezipaměti odděleně.</span><span class="sxs-lookup"><span data-stu-id="ed196-118">Lastly, the cache profile’s `varyByHeader` attribute is set to "Accept", so requests with different Accept header values have their responses cached separately.</span></span>

<span data-ttu-id="ed196-119">Program.cs v klientském projektu ukazuje, jak může být takový klient vytvořen pomocí <xref:System.Net.HttpWebRequest>.</span><span class="sxs-lookup"><span data-stu-id="ed196-119">Program.cs in the Client project demonstrates how such a client can be authored using <xref:System.Net.HttpWebRequest>.</span></span> <span data-ttu-id="ed196-120">Všimněte si, že toto je pouze jeden způsob, jak získat přístup ke službě WCF.</span><span class="sxs-lookup"><span data-stu-id="ed196-120">Note that this is just one way to access a WCF service.</span></span> <span data-ttu-id="ed196-121">Ke službě je také možné přistupovat pomocí jiných tříd .NET Framework, jako je například objekt pro vytváření kanálů <xref:System.Net.WebClient>WCF a.</span><span class="sxs-lookup"><span data-stu-id="ed196-121">It is also possible to access the service using other .NET Framework classes like the WCF channel factory and <xref:System.Net.WebClient>.</span></span> <span data-ttu-id="ed196-122">Další ukázky v sadě SDK (například základní ukázka [služby http](../../../../docs/framework/wcf/samples/basic-http-service.md) ) ilustrují způsob použití těchto tříd ke komunikaci se službou WCF.</span><span class="sxs-lookup"><span data-stu-id="ed196-122">Other samples in the SDK (such as the [Basic HTTP Service](../../../../docs/framework/wcf/samples/basic-http-service.md) sample) illustrate how to use these classes to communicate with a WCF service.</span></span>

## <a name="to-run-the-sample"></a><span data-ttu-id="ed196-123">Chcete-li spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="ed196-123">To run the sample</span></span>

<span data-ttu-id="ed196-124">Ukázka se skládá ze tří projektů:</span><span class="sxs-lookup"><span data-stu-id="ed196-124">The sample consists of three projects:</span></span>

- <span data-ttu-id="ed196-125">**Služba**: Projekt webové aplikace, který obsahuje službu WCF HTTP hostovanou v ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="ed196-125">**Service**: A Web Application project that includes a WCF HTTP service hosted in ASP.NET.</span></span>

- <span data-ttu-id="ed196-126">**Klient**: Projekt konzolové aplikace, který provádí volání služby.</span><span class="sxs-lookup"><span data-stu-id="ed196-126">**Client**: A console application project that makes calls to the service.</span></span>

- <span data-ttu-id="ed196-127">**Běžné**: Sdílená knihovna, která obsahuje typ zákazníka, který používá klient a služba.</span><span class="sxs-lookup"><span data-stu-id="ed196-127">**Common**: A shared library that contains the Customer type used by the client and service.</span></span>

<span data-ttu-id="ed196-128">Při spuštění aplikace konzoly klienta provede klient požadavek na službu a zapíše příslušné informace z odpovědí do okna konzoly.</span><span class="sxs-lookup"><span data-stu-id="ed196-128">As the Client console application runs, the client makes requests to the service and writes the pertinent information from the responses to the console window.</span></span>

#### <a name="to-run-the-sample"></a><span data-ttu-id="ed196-129">Chcete-li spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="ed196-129">To run the sample</span></span>

1. <span data-ttu-id="ed196-130">Otevřete řešení pro ukázkovou integraci ASP.NET pro ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="ed196-130">Open the solution for the ASP.NET Caching Integration Sample.</span></span>

2. <span data-ttu-id="ed196-131">Stisknutím kombinace kláves CTRL + SHIFT + B Sestavte řešení.</span><span class="sxs-lookup"><span data-stu-id="ed196-131">Press CTRL+SHIFT+B to build the solution.</span></span>

3. <span data-ttu-id="ed196-132">Pokud okno **Průzkumník řešení** ještě není otevřené, stiskněte Ctrl + W + S.</span><span class="sxs-lookup"><span data-stu-id="ed196-132">If the **Solution Explorer** window is not already open, press CTRL+W+S.</span></span>

4. <span data-ttu-id="ed196-133">V okně **Průzkumník řešení** klikněte pravým tlačítkem na projekt **služby** a vyberte **spustit novou instanci**.</span><span class="sxs-lookup"><span data-stu-id="ed196-133">From the **Solution Explorer** window, right click the **Service** project and select **Start New Instance**.</span></span> <span data-ttu-id="ed196-134">Tím se spustí vývojový server ASP.NET, který je hostitelem služby.</span><span class="sxs-lookup"><span data-stu-id="ed196-134">This launches the ASP.NET development server, which hosts the service.</span></span>

5. <span data-ttu-id="ed196-135">V okně **Průzkumník řešení** klikněte pravým tlačítkem na projekt **klienta** a vyberte **spustit novou instanci**.</span><span class="sxs-lookup"><span data-stu-id="ed196-135">From the **Solution Explorer** window, right click the **Client** project and select **Start New Instance**.</span></span>

6. <span data-ttu-id="ed196-136">Zobrazí se okno Konzola klienta, ve kterém je uveden identifikátor URI běžící služby a identifikátor URI stránky s nápovědu HTML pro běžící službu.</span><span class="sxs-lookup"><span data-stu-id="ed196-136">The client console window appears and provides the URI of the running service and the URI of the HTML help page for the running service.</span></span> <span data-ttu-id="ed196-137">V jakémkoli okamžiku můžete zobrazit stránku HTML Help zadáním identifikátoru URI stránky s nastavením v prohlížeči.</span><span class="sxs-lookup"><span data-stu-id="ed196-137">At any point in time you can view the HTML help page by typing the URI of the help page in a browser.</span></span>

7. <span data-ttu-id="ed196-138">Po spuštění ukázkového klienta zapíše klient stav aktuální aktivity.</span><span class="sxs-lookup"><span data-stu-id="ed196-138">As the sample runs, the client writes the status of the current activity.</span></span>

8. <span data-ttu-id="ed196-139">Stisknutím libovolné klávesy ukončete konzolovou aplikaci klienta.</span><span class="sxs-lookup"><span data-stu-id="ed196-139">Press any key to terminate the client console application.</span></span>

9. <span data-ttu-id="ed196-140">Stisknutím SHIFT + F5 zastavíte ladění služby.</span><span class="sxs-lookup"><span data-stu-id="ed196-140">Press SHIFT+F5 to stop debugging the service.</span></span>

10. <span data-ttu-id="ed196-141">V oznamovací oblasti systému Windows klikněte pravým tlačítkem myši na ikonu vývojového serveru ASP.NET a vyberte **zastavit**.</span><span class="sxs-lookup"><span data-stu-id="ed196-141">In the Windows Notification Area, right click the ASP.NET development server icon and select **Stop**.</span></span>
