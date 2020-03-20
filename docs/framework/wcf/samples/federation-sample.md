---
title: Ukázka federace
ms.date: 03/30/2017
ms.assetid: 7e9da0ca-e925-4644-aa96-8bfaf649d4bb
ms.openlocfilehash: 9ec462f88c0e3a039b7f288554be3e28f13ece08
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144666"
---
# <a name="federation-sample"></a><span data-ttu-id="869fa-102">Ukázka federace</span><span class="sxs-lookup"><span data-stu-id="869fa-102">Federation Sample</span></span>
<span data-ttu-id="869fa-103">Tato ukázka ukazuje federované zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="869fa-103">This sample demonstrates federated security.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="869fa-104">Podrobnosti ukázky</span><span class="sxs-lookup"><span data-stu-id="869fa-104">Sample Details</span></span>  
 <span data-ttu-id="869fa-105">Windows Communication Foundation (WCF) poskytuje podporu pro nasazení federovaných architektur zabezpečení prostřednictvím `wsFederationHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="869fa-105">Windows Communication Foundation (WCF) provides support for deploying federated security architectures through the `wsFederationHttpBinding`.</span></span> <span data-ttu-id="869fa-106">Poskytuje `wsFederationHttpBinding` zabezpečenou, spolehlivou a interoperabilní vazbu, která zahrnuje použití protokolu HTTP jako základního mechanismu přenosu pro komunikaci požadavku a odpovědi a text/XML jako formát vodiče pro kódování.</span><span class="sxs-lookup"><span data-stu-id="869fa-106">The `wsFederationHttpBinding` provides a secure, reliable, and interoperable binding that involves the use of HTTP as the underlying transport mechanism for request/reply communication, and Text/XML as the wire format for encoding.</span></span> <span data-ttu-id="869fa-107">Další informace o Federaci ve WCF naleznete v [tématu Federation](../../../../docs/framework/wcf/feature-details/federation.md).</span><span class="sxs-lookup"><span data-stu-id="869fa-107">For more information about Federation in WCF, see [Federation](../../../../docs/framework/wcf/feature-details/federation.md).</span></span>  
  
 <span data-ttu-id="869fa-108">Scénář se skládá ze 4 kusů:</span><span class="sxs-lookup"><span data-stu-id="869fa-108">The scenario is made up of 4 pieces:</span></span>  
  
- <span data-ttu-id="869fa-109">Služba Knihkupectví</span><span class="sxs-lookup"><span data-stu-id="869fa-109">BookStore service</span></span>  
  
- <span data-ttu-id="869fa-110">Knihkupectví STS</span><span class="sxs-lookup"><span data-stu-id="869fa-110">BookStore STS</span></span>  
  
- <span data-ttu-id="869fa-111">HomeRealm STS</span><span class="sxs-lookup"><span data-stu-id="869fa-111">HomeRealm STS</span></span>  
  
- <span data-ttu-id="869fa-112">Klient Knihkupectví</span><span class="sxs-lookup"><span data-stu-id="869fa-112">BookStore Client</span></span>  
  
 <span data-ttu-id="869fa-113">Služba BookStore podporuje dvě `BrowseBooks` `BuyBook`operace a .</span><span class="sxs-lookup"><span data-stu-id="869fa-113">The BookStore service supports two operations, `BrowseBooks` and `BuyBook`.</span></span> <span data-ttu-id="869fa-114">Umožňuje anonymní přístup `BrowseBooks` k operaci, ale vyžaduje ověřený přístup pro přístup k `BuyBooks` operaci.</span><span class="sxs-lookup"><span data-stu-id="869fa-114">It allows anonymous access to the `BrowseBooks` operation, but requires authenticated access to access the `BuyBooks` operation.</span></span> <span data-ttu-id="869fa-115">Ověřování má podobu tokenu vydaného službou BookStore STS.</span><span class="sxs-lookup"><span data-stu-id="869fa-115">The authentication takes the form of a token issued by the BookStore STS.</span></span> <span data-ttu-id="869fa-116">Konfigurační soubor služby Knihkupectví odkazuje klienty na `wsFederationHttpBinding`službu BookStore STS pomocí .</span><span class="sxs-lookup"><span data-stu-id="869fa-116">The configuration file for the BookStore Service points clients to the BookStore STS using the `wsFederationHttpBinding`.</span></span>  
  
```xml  
<wsFederationHttpBinding>  
<!-- This is the Service binding for the BuyBooks endpoint. It redirects clients to the BookStore STS -->  
    <binding name='BuyBookBinding'>  
        <security mode="Message">  
            <message>  
                <issuerMetadata  
  address='http://localhost/FederationSample/BookStoreSTS/STS.svc/mex' >  
                    <identity>  
                        <dns value ='BookStoreSTS.com'/>  
                    </identity>  
                </issuerMetadata>  
            </message>  
        </security>  
    </binding>  
</wsFederationHttpBinding>  
```  
  
 <span data-ttu-id="869fa-117">BookStore STS pak vyžaduje, aby klienti ověřit pomocí tokenu vydaného HomeRealm STS.</span><span class="sxs-lookup"><span data-stu-id="869fa-117">The BookStore STS then requires that clients authenticate using a token issued by the HomeRealm STS.</span></span> <span data-ttu-id="869fa-118">Opět platí, že konfigurační soubor pro BookStore STS `wsFederationHttpBinding`odkazuje klienty na HomeRealm STS pomocí .</span><span class="sxs-lookup"><span data-stu-id="869fa-118">Again, the configuration file for the BookStore STS points clients to the HomeRealm STS using the `wsFederationHttpBinding`.</span></span>  
  
```xml  
<wsFederationHttpBinding>  
 <!-- This is the binding for the clients requesting tokens from this STS. It redirects clients to the HomeRealm STS -->  
    <binding name='BookStoreSTSBinding'>  
        <security mode='Message'>  
            <message>  
                <issuerMetadata  
 address='http://localhost/FederationSample/HomeRealmSTS/STS.svc/mex' >  
                    <identity>  
                        <dns value ='HomeRealmSTS.com' />  
                    </identity>  
                </issuerMetadata>  
            </message>  
        </security>  
    </binding>  
</wsFederationHttpBinding>  
```  
  
 <span data-ttu-id="869fa-119">Posloupnost událostí při `BuyBook` přístupu k operaci je následující:</span><span class="sxs-lookup"><span data-stu-id="869fa-119">The sequence of events when accessing the `BuyBook` operation is as follows:</span></span>  
  
1. <span data-ttu-id="869fa-120">Klient se ověřuje na HomeRealm STS pomocí pověření systému Windows.</span><span class="sxs-lookup"><span data-stu-id="869fa-120">The client authenticates to the HomeRealm STS using Windows credentials.</span></span>  
  
2. <span data-ttu-id="869fa-121">HomeRealm STS vydává token, který lze použít k ověření na BookStore STS.</span><span class="sxs-lookup"><span data-stu-id="869fa-121">The HomeRealm STS issues a token that can be used to authenticate to the BookStore STS.</span></span>  
  
3. <span data-ttu-id="869fa-122">Klient se ověřuje do úložiště služby StS pomocí tokenu vydaného službou HomeRealm STS.</span><span class="sxs-lookup"><span data-stu-id="869fa-122">The client authenticates to the BookStore STS using the token issued by the HomeRealm STS.</span></span>  
  
4. <span data-ttu-id="869fa-123">BookStore STS vydává token, který lze použít k ověření služby Knihkupectví.</span><span class="sxs-lookup"><span data-stu-id="869fa-123">The BookStore STS issues a token that can be used to authenticate to the BookStore Service.</span></span>  
  
5. <span data-ttu-id="869fa-124">Klient se ověřuje službě BookStore pomocí tokenu vydaného službou StS knihkupectví.</span><span class="sxs-lookup"><span data-stu-id="869fa-124">The client authenticates to the BookStore service using the token issued by the BookStore STS.</span></span>  
  
6. <span data-ttu-id="869fa-125">Klient přistupuje k `BuyBook` operaci.</span><span class="sxs-lookup"><span data-stu-id="869fa-125">The client accesses the `BuyBook` operation.</span></span>  
  
 <span data-ttu-id="869fa-126">Naleznete v následujících pokynech o nastavení a spuštění této ukázky.</span><span class="sxs-lookup"><span data-stu-id="869fa-126">See the following instructions about how to set up and run this sample.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="869fa-127">Chcete-li spustit tuto ukázku, musíte mít oprávnění k zápisu do adresáře **wwwroot.**</span><span class="sxs-lookup"><span data-stu-id="869fa-127">You must have Write permissions to the **wwwroot** directory to run this sample.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="869fa-128">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="869fa-128">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="869fa-129">Otevřete příkazové okno sady SDK.</span><span class="sxs-lookup"><span data-stu-id="869fa-129">Open the SDK command window.</span></span> <span data-ttu-id="869fa-130">V cestě ukázky spusťte Setup.bat.</span><span class="sxs-lookup"><span data-stu-id="869fa-130">In the sample path, run Setup.bat.</span></span> <span data-ttu-id="869fa-131">Tím se vytvoří virtuální adresáře požadované pro ukázku a nainstaluje požadované certifikáty s příslušnými oprávněními.</span><span class="sxs-lookup"><span data-stu-id="869fa-131">This creates the virtual directories required for the sample and installs the required certificates with appropriate permissions.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="869fa-132">Dávkový soubor Setup.bat je určen ke spuštění z příkazového řádku sady Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="869fa-132">The Setup.bat batch file is designed to be run from a Windows SDK Command Prompt.</span></span> <span data-ttu-id="869fa-133">Vyžaduje, aby proměnná prostředí sady MSSDK přecšuje do adresáře, ve kterém je sada SDK nainstalována.</span><span class="sxs-lookup"><span data-stu-id="869fa-133">It requires that the MSSDK environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="869fa-134">Tato proměnná prostředí je automaticky nastavena v příkazovém řádku sady Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="869fa-134">This environment variable is automatically set within a Windows SDK Command Prompt.</span></span> <span data-ttu-id="869fa-135">V systému Windows Vista je nutné zajistit, aby byla nainstalována kompatibilita služby IIS 6.0, protože nastavení používá skripty správce služby IIS.</span><span class="sxs-lookup"><span data-stu-id="869fa-135">On Windows Vista, you must ensure that IIS 6.0 Management Compatibility is installed because the set up uses IIS administrator scripts.</span></span> <span data-ttu-id="869fa-136">Spuštění skriptu nastavení v systému Windows Vista vyžaduje oprávnění správce.</span><span class="sxs-lookup"><span data-stu-id="869fa-136">Running the set-up script on Windows Vista requires administrator privileges.</span></span>  
  
2. <span data-ttu-id="869fa-137">Otevřete federationsample.sln v sadě Visual Studio a z nabídky **Sestavení** vyberte **Sestavit řešení.**</span><span class="sxs-lookup"><span data-stu-id="869fa-137">Open FederationSample.sln in Visual Studio and select **Build Solution** from the **Build** menu.</span></span> <span data-ttu-id="869fa-138">To vytvoří společné soubory projektu, služba Knihkupectví, Knihkupectví STS, HomeRealm STS a nasazuje je ve službě IIS.</span><span class="sxs-lookup"><span data-stu-id="869fa-138">This builds the common project files, Bookstore service, Bookstore STS, HomeRealm STS, and deploys them in IIS.</span></span> <span data-ttu-id="869fa-139">Tím se také vytvoří klientská aplikace knihkupectví a uloží spustitelný soubor BookStoreClient.exe do složky FederationSample\BookStoreClient\bin\Debug.</span><span class="sxs-lookup"><span data-stu-id="869fa-139">This also builds the Bookstore client application and places the executable BookStoreClient.exe in the FederationSample\BookStoreClient\bin\Debug folder.</span></span>  
  
3. <span data-ttu-id="869fa-140">Poklepejte na soubor BookStoreClient.exe.</span><span class="sxs-lookup"><span data-stu-id="869fa-140">Double-click BookStoreClient.exe.</span></span> <span data-ttu-id="869fa-141">Zobrazí se okno Klienta knihkupectví.</span><span class="sxs-lookup"><span data-stu-id="869fa-141">The BookStoreClient window is displayed.</span></span>  
  
4. <span data-ttu-id="869fa-142">Knihy dostupné v knihkupectví můžete procházet kliknutím na **procházet knihy**.</span><span class="sxs-lookup"><span data-stu-id="869fa-142">You can browse the books available in the bookstore by clicking **Browse Books**.</span></span>  
  
5. <span data-ttu-id="869fa-143">Chcete-li zakoupit určitou knihu, vyberte ji v seznamu a klepněte na tlačítko **Koupit knihu**.</span><span class="sxs-lookup"><span data-stu-id="869fa-143">To purchase a particular book, select the book in the list and click **Buy Book**.</span></span> <span data-ttu-id="869fa-144">Aplikace se spustí a ověřuje pomocí ověřování systému Windows pomocí služby Token zabezpečení HomeRealm.</span><span class="sxs-lookup"><span data-stu-id="869fa-144">The application starts up and authenticates using Windows authentication with the HomeRealm Security Token Service.</span></span>  
  
     <span data-ttu-id="869fa-145">Ukázka je nakonfigurována tak, aby uživatelům umožnila nakupovat knihy, které stojí 15 USD nebo méně.</span><span class="sxs-lookup"><span data-stu-id="869fa-145">The sample is configured to allow users to purchase books that cost $15 or less.</span></span> <span data-ttu-id="869fa-146">Pokus o nákup knih, které stojí více než 15 USD, má za následek, že klient získá zprávu o odepření přístupu ze služby Knihkupectví.</span><span class="sxs-lookup"><span data-stu-id="869fa-146">Attempting to buy books that cost more than $15 results in the client getting an Access Denied message from the Book Store Service.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="869fa-147">Ukázka neaktualizuje limit kreditu uživatele po nákupu.</span><span class="sxs-lookup"><span data-stu-id="869fa-147">The sample does not update the user’s credit limit after a purchase.</span></span> <span data-ttu-id="869fa-148">Knihy můžete opakovaně nakupovat v rámci limitu kreditu uživatele (pevné).</span><span class="sxs-lookup"><span data-stu-id="869fa-148">You can repeatedly purchase books within the user’s (fixed) credit limit.</span></span>  
  
#### <a name="to-clean-up"></a><span data-ttu-id="869fa-149">Chcete-li vyčistit</span><span class="sxs-lookup"><span data-stu-id="869fa-149">To clean up</span></span>  
  
1. <span data-ttu-id="869fa-150">Spusťte Cleanup.bat.</span><span class="sxs-lookup"><span data-stu-id="869fa-150">Run Cleanup.bat.</span></span> <span data-ttu-id="869fa-151">Tím odstraníte virtuální adresáře, které byly vytvořeny během instalace, a také odeberete certifikáty nainstalované během instalace.</span><span class="sxs-lookup"><span data-stu-id="869fa-151">This deletes the virtual directories that were created during set up and also removes the certificates installed during setup.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="869fa-152">Ukázky mohou být již nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="869fa-152">The samples may already be installed on your machine.</span></span> <span data-ttu-id="869fa-153">Před pokračováním zkontrolujte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="869fa-153">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="869fa-154">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="869fa-154">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="869fa-155">Tato ukázka je umístěna v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="869fa-155">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\Federation`  
