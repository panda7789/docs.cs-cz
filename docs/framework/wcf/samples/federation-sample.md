---
title: Ukázka federace
ms.date: 03/30/2017
ms.assetid: 7e9da0ca-e925-4644-aa96-8bfaf649d4bb
ms.openlocfilehash: 49a13b292a627c054510a10445e1e64ab869162c
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43389485"
---
# <a name="federation-sample"></a><span data-ttu-id="ed7b8-102">Ukázka federace</span><span class="sxs-lookup"><span data-stu-id="ed7b8-102">Federation Sample</span></span>
<span data-ttu-id="ed7b8-103">V této ukázce federovaného zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="ed7b8-103">This sample demonstrates federated security.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="ed7b8-104">Ukázka podrobnosti</span><span class="sxs-lookup"><span data-stu-id="ed7b8-104">Sample Details</span></span>  
 <span data-ttu-id="ed7b8-105">Windows Communication Foundation (WCF) poskytuje podporu pro nasazení architektury zabezpečení prostřednictvím `wsFederationHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="ed7b8-105">Windows Communication Foundation (WCF) provides support for deploying federated security architectures through the `wsFederationHttpBinding`.</span></span> <span data-ttu-id="ed7b8-106">`wsFederationHttpBinding` Poskytuje zabezpečené, spolehlivé a interoperabilní vazbu, která zahrnuje použití protokolu HTTP jako podkladový přenosový mechanismus pro komunikaci požadavek/odpověď a Text/XML jako přenosový formát pro kódování.</span><span class="sxs-lookup"><span data-stu-id="ed7b8-106">The `wsFederationHttpBinding` provides a secure, reliable, and interoperable binding that involves the use of HTTP as the underlying transport mechanism for request/reply communication, and Text/XML as the wire format for encoding.</span></span> <span data-ttu-id="ed7b8-107">Další informace o federace ve službě WCF najdete v tématu [federace](../../../../docs/framework/wcf/feature-details/federation.md).</span><span class="sxs-lookup"><span data-stu-id="ed7b8-107">For more information about Federation in WCF, see [Federation](../../../../docs/framework/wcf/feature-details/federation.md).</span></span>  
  
 <span data-ttu-id="ed7b8-108">Tento scénář se skládá ze 4 částí:</span><span class="sxs-lookup"><span data-stu-id="ed7b8-108">The scenario is made up of 4 pieces:</span></span>  
  
-   <span data-ttu-id="ed7b8-109">Služba knihkupectví</span><span class="sxs-lookup"><span data-stu-id="ed7b8-109">BookStore service</span></span>  
  
-   <span data-ttu-id="ed7b8-110">Knihkupectví služby tokenů zabezpečení</span><span class="sxs-lookup"><span data-stu-id="ed7b8-110">BookStore STS</span></span>  
  
-   <span data-ttu-id="ed7b8-111">HomeRealm služby tokenů zabezpečení</span><span class="sxs-lookup"><span data-stu-id="ed7b8-111">HomeRealm STS</span></span>  
  
-   <span data-ttu-id="ed7b8-112">Knihkupectví klienta</span><span class="sxs-lookup"><span data-stu-id="ed7b8-112">BookStore Client</span></span>  
  
 <span data-ttu-id="ed7b8-113">Služba knihkupectví podporuje dvě operace `BrowseBooks` a `BuyBook`.</span><span class="sxs-lookup"><span data-stu-id="ed7b8-113">The BookStore service supports two operations, `BrowseBooks` and `BuyBook`.</span></span> <span data-ttu-id="ed7b8-114">To umožňuje anonymní přístup k `BrowseBooks` operace, ale vyžaduje ověřený přístup k přístupu `BuyBooks` operace.</span><span class="sxs-lookup"><span data-stu-id="ed7b8-114">It allows anonymous access to the `BrowseBooks` operation, but requires authenticated access to access the `BuyBooks` operation.</span></span> <span data-ttu-id="ed7b8-115">Ověřování má formu tokenem vydaným službou tokenů zabezpečení knihkupectví.</span><span class="sxs-lookup"><span data-stu-id="ed7b8-115">The authentication takes the form of a token issued by the BookStore STS.</span></span> <span data-ttu-id="ed7b8-116">Konfigurační soubor služby knihkupectví body klientů pomocí služby tokenů zabezpečení knihkupectví `wsFederationHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="ed7b8-116">The configuration file for the BookStore Service points clients to the BookStore STS using the `wsFederationHttpBinding`.</span></span>  
  
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
  
 <span data-ttu-id="ed7b8-117">Služba tokenů zabezpečení knihkupectví pak vyžaduje, že klienti ověřování pomocí tokenu vydaného službou HomeRealm STS.</span><span class="sxs-lookup"><span data-stu-id="ed7b8-117">The BookStore STS then requires that clients authenticate using a token issued by the HomeRealm STS.</span></span> <span data-ttu-id="ed7b8-118">Znovu, konfigurační soubor služby STS knihkupectví odkazuje klientů pomocí služby tokenů zabezpečení HomeRealm `wsFederationHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="ed7b8-118">Again, the configuration file for the BookStore STS points clients to the HomeRealm STS using the `wsFederationHttpBinding`.</span></span>  
  
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
  
 <span data-ttu-id="ed7b8-119">Posloupnost událostí, když přistupoval k `BuyBook` operace vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="ed7b8-119">The sequence of events when accessing the `BuyBook` operation is as follows:</span></span>  
  
1.  <span data-ttu-id="ed7b8-120">Klient se ověří na službu STS HomeRealm pomocí přihlašovacích údajů Windows.</span><span class="sxs-lookup"><span data-stu-id="ed7b8-120">The client authenticates to the HomeRealm STS using Windows credentials.</span></span>  
  
2.  <span data-ttu-id="ed7b8-121">Služba tokenů zabezpečení HomeRealm vystaví token, který slouží k ověření na službu STS knihkupectví.</span><span class="sxs-lookup"><span data-stu-id="ed7b8-121">The HomeRealm STS issues a token that can be used to authenticate to the BookStore STS.</span></span>  
  
3.  <span data-ttu-id="ed7b8-122">Klient se ověří pomocí tokenu vystaví služba HomeRealm STS Služba tokenů zabezpečení knihkupectví.</span><span class="sxs-lookup"><span data-stu-id="ed7b8-122">The client authenticates to the BookStore STS using the token issued by the HomeRealm STS.</span></span>  
  
4.  <span data-ttu-id="ed7b8-123">Služba tokenů zabezpečení knihkupectví vystaví token, který slouží k ověření služby knihkupectví.</span><span class="sxs-lookup"><span data-stu-id="ed7b8-123">The BookStore STS issues a token that can be used to authenticate to the BookStore Service.</span></span>  
  
5.  <span data-ttu-id="ed7b8-124">Klient se ověří ve službě knihkupectví pomocí tokenu vystaví služba STS knihkupectví.</span><span class="sxs-lookup"><span data-stu-id="ed7b8-124">The client authenticates to the BookStore service using the token issued by the BookStore STS.</span></span>  
  
6.  <span data-ttu-id="ed7b8-125">Klient přistupuje k `BuyBook` operace.</span><span class="sxs-lookup"><span data-stu-id="ed7b8-125">The client accesses the `BuyBook` operation.</span></span>  
  
 <span data-ttu-id="ed7b8-126">Přečtěte si následující pokyny o tom, jak nastavit a spustit tento příklad.</span><span class="sxs-lookup"><span data-stu-id="ed7b8-126">See the following instructions about how to set up and run this sample.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ed7b8-127">Musíte mít oprávnění k zápisu **wwwroot** adresář pro tuto ukázku spustit.</span><span class="sxs-lookup"><span data-stu-id="ed7b8-127">You must have Write permissions to the **wwwroot** directory to run this sample.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ed7b8-128">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="ed7b8-128">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="ed7b8-129">Otevřete příkazové okno sady SDK.</span><span class="sxs-lookup"><span data-stu-id="ed7b8-129">Open the SDK command window.</span></span> <span data-ttu-id="ed7b8-130">V cestě ukázkové spuštění Setup.bat.</span><span class="sxs-lookup"><span data-stu-id="ed7b8-130">In the sample path, run Setup.bat.</span></span> <span data-ttu-id="ed7b8-131">To vytvoří virtuální adresáře, vyžaduje se pro ukázku a nainstaluje požadované certifikáty s příslušnými oprávněními.</span><span class="sxs-lookup"><span data-stu-id="ed7b8-131">This creates the virtual directories required for the sample and installs the required certificates with appropriate permissions.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ed7b8-132">Dávkový soubor Setup.bat je navržena pro spouštění na příkazovém řádku sady SDK Windows.</span><span class="sxs-lookup"><span data-stu-id="ed7b8-132">The Setup.bat batch file is designed to be run from a Windows SDK Command Prompt.</span></span> <span data-ttu-id="ed7b8-133">To vyžaduje, aby proměnné prostředí MSSDK bodu do adresáře, ve kterém je nainstalována sada SDK.</span><span class="sxs-lookup"><span data-stu-id="ed7b8-133">It requires that the MSSDK environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="ed7b8-134">Tato proměnná prostředí je nastavena automaticky v příkazovém řádku Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="ed7b8-134">This environment variable is automatically set within a Windows SDK Command Prompt.</span></span> <span data-ttu-id="ed7b8-135">Na [!INCLUDE[wv](../../../../includes/wv-md.md)], ujistěte se, že Kompatibilita správy služby IIS 6.0 je nainstalovat, protože nastavení používá skripty Správce služby IIS.</span><span class="sxs-lookup"><span data-stu-id="ed7b8-135">On [!INCLUDE[wv](../../../../includes/wv-md.md)], you must ensure that IIS 6.0 Management Compatibility is installed because the set up uses IIS administrator scripts.</span></span> <span data-ttu-id="ed7b8-136">Spouštění skriptu nastavení na [!INCLUDE[wv](../../../../includes/wv-md.md)] vyžaduje oprávnění správce.</span><span class="sxs-lookup"><span data-stu-id="ed7b8-136">Running the set-up script on [!INCLUDE[wv](../../../../includes/wv-md.md)] requires administrator privileges.</span></span>  
  
2.  <span data-ttu-id="ed7b8-137">Otevřete FederationSample.sln v sadě Visual Studio a vyberte **sestavit řešení** z **sestavení** nabídky.</span><span class="sxs-lookup"><span data-stu-id="ed7b8-137">Open FederationSample.sln in Visual Studio and select **Build Solution** from the **Build** menu.</span></span> <span data-ttu-id="ed7b8-138">To vytvoří běžné soubory projektu, knihkupectví služby, knihkupectví STS, HomeRealm STS a nasadí ve službě IIS.</span><span class="sxs-lookup"><span data-stu-id="ed7b8-138">This builds the common project files, Bookstore service, Bookstore STS, HomeRealm STS, and deploys them in IIS.</span></span> <span data-ttu-id="ed7b8-139">To také vytvoří knihkupectví klientská aplikace a umístí BookStoreClient.exe spustitelný soubor ve složce FederationSample\BookStoreClient\bin\Debug.</span><span class="sxs-lookup"><span data-stu-id="ed7b8-139">This also builds the Bookstore client application and places the executable BookStoreClient.exe in the FederationSample\BookStoreClient\bin\Debug folder.</span></span>  
  
3.  <span data-ttu-id="ed7b8-140">Dvakrát klikněte na panel BookStoreClient.exe.</span><span class="sxs-lookup"><span data-stu-id="ed7b8-140">Double-click BookStoreClient.exe.</span></span> <span data-ttu-id="ed7b8-141">Zobrazí se okno BookStoreClient.</span><span class="sxs-lookup"><span data-stu-id="ed7b8-141">The BookStoreClient window is displayed.</span></span>  
  
4.  <span data-ttu-id="ed7b8-142">K dispozici v knihkupectví knih můžete procházet kliknutím **procházet knihy**.</span><span class="sxs-lookup"><span data-stu-id="ed7b8-142">You can browse the books available in the bookstore by clicking **Browse Books**.</span></span>  
  
5.  <span data-ttu-id="ed7b8-143">Pokud chcete zakoupit konkrétní adresáře, v seznamu vyberte knihy a klikněte na **zakoupení knihy**.</span><span class="sxs-lookup"><span data-stu-id="ed7b8-143">To purchase a particular book, select the book in the list and click **Buy Book**.</span></span> <span data-ttu-id="ed7b8-144">Aplikace spuštění a ověřuje pomocí služby tokenů zabezpečení HomeRealm ověřování Windows.</span><span class="sxs-lookup"><span data-stu-id="ed7b8-144">The application starts up and authenticates using Windows authentication with the HomeRealm Security Token Service.</span></span>  
  
     <span data-ttu-id="ed7b8-145">Ukázka je nakonfigurovaná tak, aby uživatelům nákup knih, které nákladů 15 USD nebo nižší.</span><span class="sxs-lookup"><span data-stu-id="ed7b8-145">The sample is configured to allow users to purchase books that cost $15 or less.</span></span> <span data-ttu-id="ed7b8-146">Došlo k pokusu o zakoupení knihy, které víc než 15 USD za následek klienta získávání zpráva Přístup byl odepřen z službu Store knihy nákladů.</span><span class="sxs-lookup"><span data-stu-id="ed7b8-146">Attempting to buy books that cost more than $15 results in the client getting an Access Denied message from the Book Store Service.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ed7b8-147">Ukázka neaktualizuje uživatele kreditního limitu po nákupu.</span><span class="sxs-lookup"><span data-stu-id="ed7b8-147">The sample does not update the user’s credit limit after a purchase.</span></span> <span data-ttu-id="ed7b8-148">Můžete opakovaně nákup knih v rámci daného uživatele (pevné) kreditního limitu.</span><span class="sxs-lookup"><span data-stu-id="ed7b8-148">You can repeatedly purchase books within the user’s (fixed) credit limit.</span></span>  
  
#### <a name="to-clean-up"></a><span data-ttu-id="ed7b8-149">Vyčistit</span><span class="sxs-lookup"><span data-stu-id="ed7b8-149">To clean up</span></span>  
  
1.  <span data-ttu-id="ed7b8-150">Spusťte Cleanup.bat.</span><span class="sxs-lookup"><span data-stu-id="ed7b8-150">Run Cleanup.bat.</span></span> <span data-ttu-id="ed7b8-151">To odstraní virtuální adresáře, které byly vytvořené během nastavení a také odebere během instalace nainstalovat certifikáty.</span><span class="sxs-lookup"><span data-stu-id="ed7b8-151">This deletes the virtual directories that were created during set up and also removes the certificates installed during setup.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ed7b8-152">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="ed7b8-152">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ed7b8-153">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="ed7b8-153">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="ed7b8-154">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="ed7b8-154">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ed7b8-155">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="ed7b8-155">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\Federation`  
  
## <a name="see-also"></a><span data-ttu-id="ed7b8-156">Viz také</span><span class="sxs-lookup"><span data-stu-id="ed7b8-156">See Also</span></span>
