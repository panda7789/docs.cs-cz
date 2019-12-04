---
title: Ukázka federace
ms.date: 03/30/2017
ms.assetid: 7e9da0ca-e925-4644-aa96-8bfaf649d4bb
ms.openlocfilehash: 271790e08476533fc1d83e22c5a0daf2f1eaa42a
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716929"
---
# <a name="federation-sample"></a><span data-ttu-id="30abe-102">Ukázka federace</span><span class="sxs-lookup"><span data-stu-id="30abe-102">Federation Sample</span></span>
<span data-ttu-id="30abe-103">Tato ukázka demonstruje federované zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="30abe-103">This sample demonstrates federated security.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="30abe-104">Podrobnosti ukázky</span><span class="sxs-lookup"><span data-stu-id="30abe-104">Sample Details</span></span>  
 <span data-ttu-id="30abe-105">Windows Communication Foundation (WCF) poskytuje podporu pro nasazení federovaných architektur zabezpečení prostřednictvím `wsFederationHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="30abe-105">Windows Communication Foundation (WCF) provides support for deploying federated security architectures through the `wsFederationHttpBinding`.</span></span> <span data-ttu-id="30abe-106">`wsFederationHttpBinding` poskytuje zabezpečenou, spolehlivou a interoperabilní vazbu, která zahrnuje použití HTTP jako základního přenosového mechanismu pro komunikaci typu požadavek/odpověď a text/XML jako formát přenosu pro kódování.</span><span class="sxs-lookup"><span data-stu-id="30abe-106">The `wsFederationHttpBinding` provides a secure, reliable, and interoperable binding that involves the use of HTTP as the underlying transport mechanism for request/reply communication, and Text/XML as the wire format for encoding.</span></span> <span data-ttu-id="30abe-107">Další informace o federaci v WCF najdete v článku [federace](../../../../docs/framework/wcf/feature-details/federation.md).</span><span class="sxs-lookup"><span data-stu-id="30abe-107">For more information about Federation in WCF, see [Federation](../../../../docs/framework/wcf/feature-details/federation.md).</span></span>  
  
 <span data-ttu-id="30abe-108">Scénář se skládá ze 4 kusů:</span><span class="sxs-lookup"><span data-stu-id="30abe-108">The scenario is made up of 4 pieces:</span></span>  
  
- <span data-ttu-id="30abe-109">Služba BookStore</span><span class="sxs-lookup"><span data-stu-id="30abe-109">BookStore service</span></span>  
  
- <span data-ttu-id="30abe-110">BookStore STS</span><span class="sxs-lookup"><span data-stu-id="30abe-110">BookStore STS</span></span>  
  
- <span data-ttu-id="30abe-111">HomeRealm STS</span><span class="sxs-lookup"><span data-stu-id="30abe-111">HomeRealm STS</span></span>  
  
- <span data-ttu-id="30abe-112">Klient BookStore</span><span class="sxs-lookup"><span data-stu-id="30abe-112">BookStore Client</span></span>  
  
 <span data-ttu-id="30abe-113">Služba BookStore podporuje dvě operace `BrowseBooks` a `BuyBook`.</span><span class="sxs-lookup"><span data-stu-id="30abe-113">The BookStore service supports two operations, `BrowseBooks` and `BuyBook`.</span></span> <span data-ttu-id="30abe-114">Umožňuje anonymní přístup k operaci `BrowseBooks`, ale vyžaduje ověřený přístup pro přístup k operaci `BuyBooks`.</span><span class="sxs-lookup"><span data-stu-id="30abe-114">It allows anonymous access to the `BrowseBooks` operation, but requires authenticated access to access the `BuyBooks` operation.</span></span> <span data-ttu-id="30abe-115">Ověřování má formu tokenu vydaného službou BookStore STS.</span><span class="sxs-lookup"><span data-stu-id="30abe-115">The authentication takes the form of a token issued by the BookStore STS.</span></span> <span data-ttu-id="30abe-116">Konfigurační soubor pro službu BookStore směřuje klienty k knihkupectví STS pomocí `wsFederationHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="30abe-116">The configuration file for the BookStore Service points clients to the BookStore STS using the `wsFederationHttpBinding`.</span></span>  
  
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
  
 <span data-ttu-id="30abe-117">BookStore STS pak vyžaduje, aby se klienti ověřovali pomocí tokenu vydaného službou HomeRealm STS.</span><span class="sxs-lookup"><span data-stu-id="30abe-117">The BookStore STS then requires that clients authenticate using a token issued by the HomeRealm STS.</span></span> <span data-ttu-id="30abe-118">Konfigurační soubor pro službu BookStore STS se znovu odkazuje na HomeRealm STS pomocí `wsFederationHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="30abe-118">Again, the configuration file for the BookStore STS points clients to the HomeRealm STS using the `wsFederationHttpBinding`.</span></span>  
  
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
  
 <span data-ttu-id="30abe-119">Sekvence událostí při přístupu k operaci `BuyBook` je následující:</span><span class="sxs-lookup"><span data-stu-id="30abe-119">The sequence of events when accessing the `BuyBook` operation is as follows:</span></span>  
  
1. <span data-ttu-id="30abe-120">Klient se ověřuje pomocí pověření služby HomeRealm STS prostřednictvím přihlašovacích údajů systému Windows.</span><span class="sxs-lookup"><span data-stu-id="30abe-120">The client authenticates to the HomeRealm STS using Windows credentials.</span></span>  
  
2. <span data-ttu-id="30abe-121">Služba HomeRealm STS vydá token, který se dá použít k ověření v knihkupectví STS.</span><span class="sxs-lookup"><span data-stu-id="30abe-121">The HomeRealm STS issues a token that can be used to authenticate to the BookStore STS.</span></span>  
  
3. <span data-ttu-id="30abe-122">Klient se ověřuje pro službu BookStore STS pomocí tokenu vydaného službou HomeRealm STS.</span><span class="sxs-lookup"><span data-stu-id="30abe-122">The client authenticates to the BookStore STS using the token issued by the HomeRealm STS.</span></span>  
  
4. <span data-ttu-id="30abe-123">Služba BookStore STS vydá token, který lze použít k ověření ve službě BookStore.</span><span class="sxs-lookup"><span data-stu-id="30abe-123">The BookStore STS issues a token that can be used to authenticate to the BookStore Service.</span></span>  
  
5. <span data-ttu-id="30abe-124">Klient se ověřuje pro službu BookStore pomocí tokenu vydaného službou BookStore STS.</span><span class="sxs-lookup"><span data-stu-id="30abe-124">The client authenticates to the BookStore service using the token issued by the BookStore STS.</span></span>  
  
6. <span data-ttu-id="30abe-125">Klient přistupuje k operaci `BuyBook`.</span><span class="sxs-lookup"><span data-stu-id="30abe-125">The client accesses the `BuyBook` operation.</span></span>  
  
 <span data-ttu-id="30abe-126">V následujících pokynech se dozvíte, jak nastavit a spustit tuto ukázku.</span><span class="sxs-lookup"><span data-stu-id="30abe-126">See the following instructions about how to set up and run this sample.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="30abe-127">Pro spuštění této ukázky musíte mít oprávnění k zápisu do adresáře **wwwroot** .</span><span class="sxs-lookup"><span data-stu-id="30abe-127">You must have Write permissions to the **wwwroot** directory to run this sample.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="30abe-128">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="30abe-128">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="30abe-129">Otevřete okno příkazového řádku sady SDK.</span><span class="sxs-lookup"><span data-stu-id="30abe-129">Open the SDK command window.</span></span> <span data-ttu-id="30abe-130">V ukázkové cestě spusťte Setup. bat.</span><span class="sxs-lookup"><span data-stu-id="30abe-130">In the sample path, run Setup.bat.</span></span> <span data-ttu-id="30abe-131">Tím se vytvoří virtuální adresáře vyžadované pro ukázku a nainstalují se požadované certifikáty s příslušnými oprávněními.</span><span class="sxs-lookup"><span data-stu-id="30abe-131">This creates the virtual directories required for the sample and installs the required certificates with appropriate permissions.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="30abe-132">Dávkový soubor Setup. bat je navržený tak, aby se spouštěl z příkazového řádku Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="30abe-132">The Setup.bat batch file is designed to be run from a Windows SDK Command Prompt.</span></span> <span data-ttu-id="30abe-133">Vyžaduje, aby proměnná prostředí MSSDK odkazovala na adresář, ve kterém je sada SDK nainstalována.</span><span class="sxs-lookup"><span data-stu-id="30abe-133">It requires that the MSSDK environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="30abe-134">Tato proměnná prostředí se automaticky nastaví v rámci Windows SDK příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="30abe-134">This environment variable is automatically set within a Windows SDK Command Prompt.</span></span> <span data-ttu-id="30abe-135">Na [!INCLUDE[wv](../../../../includes/wv-md.md)]je potřeba zajistit, aby byla nainstalovaná Kompatibilita správy služby IIS 6,0, protože nastavení používá skripty Správce služby IIS.</span><span class="sxs-lookup"><span data-stu-id="30abe-135">On [!INCLUDE[wv](../../../../includes/wv-md.md)], you must ensure that IIS 6.0 Management Compatibility is installed because the set up uses IIS administrator scripts.</span></span> <span data-ttu-id="30abe-136">Spuštění skriptu pro nastavení na [!INCLUDE[wv](../../../../includes/wv-md.md)] vyžaduje oprávnění správce.</span><span class="sxs-lookup"><span data-stu-id="30abe-136">Running the set-up script on [!INCLUDE[wv](../../../../includes/wv-md.md)] requires administrator privileges.</span></span>  
  
2. <span data-ttu-id="30abe-137">Otevřete FederationSample. sln v aplikaci Visual Studio a v nabídce **sestavení** vyberte **Sestavit řešení** .</span><span class="sxs-lookup"><span data-stu-id="30abe-137">Open FederationSample.sln in Visual Studio and select **Build Solution** from the **Build** menu.</span></span> <span data-ttu-id="30abe-138">Tím se vytvoří společné soubory projektu, služba Bookstore, Bookstore STS, HomeRealm STS a nasadí je ve službě IIS.</span><span class="sxs-lookup"><span data-stu-id="30abe-138">This builds the common project files, Bookstore service, Bookstore STS, HomeRealm STS, and deploys them in IIS.</span></span> <span data-ttu-id="30abe-139">Tím se také vytvoří klientská aplikace pro Bookstore a ve složce FederationSample\BookStoreClient\bin\Debug se umístí spustitelný soubor BookStoreClient. exe.</span><span class="sxs-lookup"><span data-stu-id="30abe-139">This also builds the Bookstore client application and places the executable BookStoreClient.exe in the FederationSample\BookStoreClient\bin\Debug folder.</span></span>  
  
3. <span data-ttu-id="30abe-140">Dvakrát klikněte na BookStoreClient. exe.</span><span class="sxs-lookup"><span data-stu-id="30abe-140">Double-click BookStoreClient.exe.</span></span> <span data-ttu-id="30abe-141">Zobrazí se okno BookStoreClient.</span><span class="sxs-lookup"><span data-stu-id="30abe-141">The BookStoreClient window is displayed.</span></span>  
  
4. <span data-ttu-id="30abe-142">Knihy, které jsou k dispozici v knihkupectví, můžete procházet kliknutím na **Procházet knihy**.</span><span class="sxs-lookup"><span data-stu-id="30abe-142">You can browse the books available in the bookstore by clicking **Browse Books**.</span></span>  
  
5. <span data-ttu-id="30abe-143">Pokud si chcete koupit určitou knihu, vyberte v seznamu knihu a klikněte na **koupit knihu**.</span><span class="sxs-lookup"><span data-stu-id="30abe-143">To purchase a particular book, select the book in the list and click **Buy Book**.</span></span> <span data-ttu-id="30abe-144">Aplikace se spustí a ověří pomocí ověřování systému Windows pomocí služby tokenu zabezpečení HomeRealm.</span><span class="sxs-lookup"><span data-stu-id="30abe-144">The application starts up and authenticates using Windows authentication with the HomeRealm Security Token Service.</span></span>  
  
     <span data-ttu-id="30abe-145">Tato ukázka je nakonfigurovaná tak, aby umožňovala uživatelům koupit knihy, které $15 nebo méně.</span><span class="sxs-lookup"><span data-stu-id="30abe-145">The sample is configured to allow users to purchase books that cost $15 or less.</span></span> <span data-ttu-id="30abe-146">Při pokusu o zakoupení knih s vyššími náklady, než $15, dojde v klientovi k získání zprávy o odepření přístupu ze služby Book Store.</span><span class="sxs-lookup"><span data-stu-id="30abe-146">Attempting to buy books that cost more than $15 results in the client getting an Access Denied message from the Book Store Service.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="30abe-147">Ukázka neaktualizuje limit úvěru uživatele po nákupu.</span><span class="sxs-lookup"><span data-stu-id="30abe-147">The sample does not update the user’s credit limit after a purchase.</span></span> <span data-ttu-id="30abe-148">V rámci limitu úvěru uživatele můžete opakovaně nakupovat knihy.</span><span class="sxs-lookup"><span data-stu-id="30abe-148">You can repeatedly purchase books within the user’s (fixed) credit limit.</span></span>  
  
#### <a name="to-clean-up"></a><span data-ttu-id="30abe-149">Vyčištění</span><span class="sxs-lookup"><span data-stu-id="30abe-149">To clean up</span></span>  
  
1. <span data-ttu-id="30abe-150">Spusťte nástroj CleanUp. bat.</span><span class="sxs-lookup"><span data-stu-id="30abe-150">Run Cleanup.bat.</span></span> <span data-ttu-id="30abe-151">Tím odstraníte virtuální adresáře, které byly vytvořeny během instalace, a zároveň dojde k odebrání certifikátů nainstalovaných během instalace.</span><span class="sxs-lookup"><span data-stu-id="30abe-151">This deletes the virtual directories that were created during set up and also removes the certificates installed during setup.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="30abe-152">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="30abe-152">The samples may already be installed on your machine.</span></span> <span data-ttu-id="30abe-153">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="30abe-153">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="30abe-154">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples.</span><span class="sxs-lookup"><span data-stu-id="30abe-154">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="30abe-155">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="30abe-155">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\Federation`  
