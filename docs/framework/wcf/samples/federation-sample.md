---
title: "Ukázka federace"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7e9da0ca-e925-4644-aa96-8bfaf649d4bb
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a13632318902ce08678a01c3e63b3d12cc2f4f20
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="federation-sample"></a><span data-ttu-id="7a623-102">Ukázka federace</span><span class="sxs-lookup"><span data-stu-id="7a623-102">Federation Sample</span></span>
<span data-ttu-id="7a623-103">Tento příklad znázorňuje federované zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="7a623-103">This sample demonstrates federated security.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="7a623-104">Ukázka podrobnosti</span><span class="sxs-lookup"><span data-stu-id="7a623-104">Sample Details</span></span>  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="7a623-105">poskytuje podporu pro nasazení architektury federované zabezpečení prostřednictvím `wsFederationHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="7a623-105"> provides support for deploying federated security architectures through the `wsFederationHttpBinding`.</span></span> <span data-ttu-id="7a623-106">`wsFederationHttpBinding` Poskytuje vazbu zabezpečeným, spolehlivým a vzájemná spolupráce, který zahrnuje použití protokolu HTTP jako podkladový přenosový mechanismus pro požadavek nebo odpověď komunikace a Text/XML jako přenosový formát pro kódování.</span><span class="sxs-lookup"><span data-stu-id="7a623-106">The `wsFederationHttpBinding` provides a secure, reliable, and interoperable binding that involves the use of HTTP as the underlying transport mechanism for request/reply communication, and Text/XML as the wire format for encoding.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="7a623-107">Federace v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], najdete v části [Federation](../../../../docs/framework/wcf/feature-details/federation.md).</span><span class="sxs-lookup"><span data-stu-id="7a623-107"> Federation in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], see [Federation](../../../../docs/framework/wcf/feature-details/federation.md).</span></span>  
  
 <span data-ttu-id="7a623-108">Tento scénář se skládá ze 4 částí:</span><span class="sxs-lookup"><span data-stu-id="7a623-108">The scenario is made up of 4 pieces:</span></span>  
  
-   <span data-ttu-id="7a623-109">Služba pro knihkupectví</span><span class="sxs-lookup"><span data-stu-id="7a623-109">BookStore service</span></span>  
  
-   <span data-ttu-id="7a623-110">Knihkupectví služby tokenů zabezpečení</span><span class="sxs-lookup"><span data-stu-id="7a623-110">BookStore STS</span></span>  
  
-   <span data-ttu-id="7a623-111">HomeRealm služby tokenů zabezpečení</span><span class="sxs-lookup"><span data-stu-id="7a623-111">HomeRealm STS</span></span>  
  
-   <span data-ttu-id="7a623-112">Klient pro knihkupectví</span><span class="sxs-lookup"><span data-stu-id="7a623-112">BookStore Client</span></span>  
  
 <span data-ttu-id="7a623-113">Službu pro knihkupectví podporuje dvě operace `BrowseBooks` a `BuyBook`.</span><span class="sxs-lookup"><span data-stu-id="7a623-113">The BookStore service supports two operations, `BrowseBooks` and `BuyBook`.</span></span> <span data-ttu-id="7a623-114">Umožňuje anonymní přístup k `BrowseBooks` operaci, ale vyžaduje ověřený přístup k přístupu `BuyBooks` operaci.</span><span class="sxs-lookup"><span data-stu-id="7a623-114">It allows anonymous access to the `BrowseBooks` operation, but requires authenticated access to access the `BuyBooks` operation.</span></span> <span data-ttu-id="7a623-115">Ověřování má podobu tokenem vydaným službou tokenů zabezpečení pro knihkupectví.</span><span class="sxs-lookup"><span data-stu-id="7a623-115">The authentication takes the form of a token issued by the BookStore STS.</span></span> <span data-ttu-id="7a623-116">Konfigurační soubor pro knihkupectví službu bodů klienty pomocí tokenů zabezpečení pro knihkupectví `wsFederationHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="7a623-116">The configuration file for the BookStore Service points clients to the BookStore STS using the `wsFederationHttpBinding`.</span></span>  
  
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
  
 <span data-ttu-id="7a623-117">STS pro knihkupectví pak vyžaduje, aby klienti ověřovat pomocí tokenem vydaným službou tokenů zabezpečení HomeRealm.</span><span class="sxs-lookup"><span data-stu-id="7a623-117">The BookStore STS then requires that clients authenticate using a token issued by the HomeRealm STS.</span></span> <span data-ttu-id="7a623-118">Znovu konfiguračního souboru pro knihkupectví STS bodů klienty pomocí služby tokenů zabezpečení HomeRealm `wsFederationHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="7a623-118">Again, the configuration file for the BookStore STS points clients to the HomeRealm STS using the `wsFederationHttpBinding`.</span></span>  
  
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
  
 <span data-ttu-id="7a623-119">Posloupnost událostí při přístupu k `BuyBook` operace vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="7a623-119">The sequence of events when accessing the `BuyBook` operation is as follows:</span></span>  
  
1.  <span data-ttu-id="7a623-120">Klient se ověří na službu STS HomeRealm pomocí pověření systému Windows.</span><span class="sxs-lookup"><span data-stu-id="7a623-120">The client authenticates to the HomeRealm STS using Windows credentials.</span></span>  
  
2.  <span data-ttu-id="7a623-121">Služba tokenů zabezpečení HomeRealm vystaví token, který můžete použít k ověřování pro knihkupectví tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="7a623-121">The HomeRealm STS issues a token that can be used to authenticate to the BookStore STS.</span></span>  
  
3.  <span data-ttu-id="7a623-122">Klient se ověří na službu STS knihkupectví pomocí tokenem vydaným službou tokenů zabezpečení HomeRealm.</span><span class="sxs-lookup"><span data-stu-id="7a623-122">The client authenticates to the BookStore STS using the token issued by the HomeRealm STS.</span></span>  
  
4.  <span data-ttu-id="7a623-123">Služba tokenů zabezpečení knihkupectví vystaví token, který slouží k ověření pro knihkupectví službu.</span><span class="sxs-lookup"><span data-stu-id="7a623-123">The BookStore STS issues a token that can be used to authenticate to the BookStore Service.</span></span>  
  
5.  <span data-ttu-id="7a623-124">Klient se ověří pro knihkupectví služby pomocí tokenem vydaným službou tokenů zabezpečení pro knihkupectví.</span><span class="sxs-lookup"><span data-stu-id="7a623-124">The client authenticates to the BookStore service using the token issued by the BookStore STS.</span></span>  
  
6.  <span data-ttu-id="7a623-125">Klient přistupuje k `BuyBook` operaci.</span><span class="sxs-lookup"><span data-stu-id="7a623-125">The client accesses the `BuyBook` operation.</span></span>  
  
 <span data-ttu-id="7a623-126">Přečtěte si následující pokyny o tom, jak nastavit a tuto ukázku spustit.</span><span class="sxs-lookup"><span data-stu-id="7a623-126">See the following instructions about how to set up and run this sample.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7a623-127">Musíte mít oprávnění k zápisu do **wwwroot** directory chcete tuto ukázku spustit.</span><span class="sxs-lookup"><span data-stu-id="7a623-127">You must have Write permissions to the **wwwroot** directory to run this sample.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="7a623-128">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="7a623-128">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="7a623-129">Otevřete příkazové okno SDK.</span><span class="sxs-lookup"><span data-stu-id="7a623-129">Open the SDK command window.</span></span> <span data-ttu-id="7a623-130">V cestě ukázka spustit Setup.bat.</span><span class="sxs-lookup"><span data-stu-id="7a623-130">In the sample path, run Setup.bat.</span></span> <span data-ttu-id="7a623-131">Tím se vytvoří virtuální adresáře, které jsou potřebné pro vzorovou a nainstaluje požadované certifikáty s příslušnými oprávněními.</span><span class="sxs-lookup"><span data-stu-id="7a623-131">This creates the virtual directories required for the sample and installs the required certificates with appropriate permissions.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7a623-132">Dávkový soubor Setup.bat slouží ke spuštění z Windows příkazový řádek SDK.</span><span class="sxs-lookup"><span data-stu-id="7a623-132">The Setup.bat batch file is designed to be run from a Windows SDK Command Prompt.</span></span> <span data-ttu-id="7a623-133">Se vyžaduje, aby proměnné prostředí MSSDK bodu na adresář, kam nainstalovat sadu SDK.</span><span class="sxs-lookup"><span data-stu-id="7a623-133">It requires that the MSSDK environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="7a623-134">Tato proměnná prostředí bude automaticky nastavena v příkazovém řádku Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="7a623-134">This environment variable is automatically set within a Windows SDK Command Prompt.</span></span> <span data-ttu-id="7a623-135">Na [!INCLUDE[wv](../../../../includes/wv-md.md)], ujistěte se, že Kompatibilita správy služby IIS 6.0 je nainstalovat, protože nastavení používá skripty Správce služby IIS.</span><span class="sxs-lookup"><span data-stu-id="7a623-135">On [!INCLUDE[wv](../../../../includes/wv-md.md)], you must ensure that IIS 6.0 Management Compatibility is installed because the set up uses IIS administrator scripts.</span></span> <span data-ttu-id="7a623-136">Spuštění skriptu nastavení [!INCLUDE[wv](../../../../includes/wv-md.md)] vyžaduje oprávnění správce.</span><span class="sxs-lookup"><span data-stu-id="7a623-136">Running the set-up script on [!INCLUDE[wv](../../../../includes/wv-md.md)] requires administrator privileges.</span></span>  
  
2.  <span data-ttu-id="7a623-137">Otevřete FederationSample.sln v sadě Visual Studio a vyberte **sestavit řešení** z **sestavení** nabídky.</span><span class="sxs-lookup"><span data-stu-id="7a623-137">Open FederationSample.sln in Visual Studio and select **Build Solution** from the **Build** menu.</span></span> <span data-ttu-id="7a623-138">Toto sestavení společné soubory projektu, služba pro knihkupectví, tokenů zabezpečení pro knihkupectví, HomeRealm služby tokenů zabezpečení a nasadí je ve službě IIS.</span><span class="sxs-lookup"><span data-stu-id="7a623-138">This builds the common project files, Bookstore service, Bookstore STS, HomeRealm STS, and deploys them in IIS.</span></span> <span data-ttu-id="7a623-139">To také sestavení klientská aplikace pro knihkupectví a umístí BookStoreClient.exe spustitelný soubor ve složce FederationSample\BookStoreClient\bin\Debug.</span><span class="sxs-lookup"><span data-stu-id="7a623-139">This also builds the Bookstore client application and places the executable BookStoreClient.exe in the FederationSample\BookStoreClient\bin\Debug folder.</span></span>  
  
3.  <span data-ttu-id="7a623-140">Dvakrát klikněte na BookStoreClient.exe.</span><span class="sxs-lookup"><span data-stu-id="7a623-140">Double-click BookStoreClient.exe.</span></span> <span data-ttu-id="7a623-141">Zobrazí se okno BookStoreClient.</span><span class="sxs-lookup"><span data-stu-id="7a623-141">The BookStoreClient window is displayed.</span></span>  
  
4.  <span data-ttu-id="7a623-142">Můžete procházet k dispozici v knihkupectví webu knihy kliknutím **procházet knihy**.</span><span class="sxs-lookup"><span data-stu-id="7a623-142">You can browse the books available in the bookstore by clicking **Browse Books**.</span></span>  
  
5.  <span data-ttu-id="7a623-143">Chcete-li zakoupit konkrétního seznamu, vyberte seznamu v seznamu a klikněte na tlačítko **koupit kniha**.</span><span class="sxs-lookup"><span data-stu-id="7a623-143">To purchase a particular book, select the book in the list and click **Buy Book**.</span></span> <span data-ttu-id="7a623-144">Aplikace spuštění a ověřuje pomocí služby tokenů zabezpečení HomeRealm ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="7a623-144">The application starts up and authenticates using Windows authentication with the HomeRealm Security Token Service.</span></span>  
  
     <span data-ttu-id="7a623-145">Ukázka je nakonfigurován, aby uživatelé mohli nákup knih, které náklady $15 nebo méně.</span><span class="sxs-lookup"><span data-stu-id="7a623-145">The sample is configured to allow users to purchase books that cost $15 or less.</span></span> <span data-ttu-id="7a623-146">Probíhá pokus o koupit knih, které náklady více než 15 $ má za následek klient pro získávání zpráva Přístup byl odepřen z adresáře služby úložiště.</span><span class="sxs-lookup"><span data-stu-id="7a623-146">Attempting to buy books that cost more than $15 results in the client getting an Access Denied message from the Book Store Service.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7a623-147">Ukázka neaktualizuje úvěr uživatele po nákupu.</span><span class="sxs-lookup"><span data-stu-id="7a623-147">The sample does not update the user’s credit limit after a purchase.</span></span> <span data-ttu-id="7a623-148">Můžete opakovaně nákup knih v rámci limitu (pevné) platební uživatele.</span><span class="sxs-lookup"><span data-stu-id="7a623-148">You can repeatedly purchase books within the user’s (fixed) credit limit.</span></span>  
  
#### <a name="to-clean-up"></a><span data-ttu-id="7a623-149">Vyčistěte</span><span class="sxs-lookup"><span data-stu-id="7a623-149">To clean up</span></span>  
  
1.  <span data-ttu-id="7a623-150">Spusťte Cleanup.bat.</span><span class="sxs-lookup"><span data-stu-id="7a623-150">Run Cleanup.bat.</span></span> <span data-ttu-id="7a623-151">Tím odstraní virtuální adresáře, které byly vytvořeny během nahoru a také odebere certifikáty nainstalovat během instalace.</span><span class="sxs-lookup"><span data-stu-id="7a623-151">This deletes the virtual directories that were created during set up and also removes the certificates installed during setup.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7a623-152">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="7a623-152">The samples may already be installed on your machine.</span></span> <span data-ttu-id="7a623-153">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="7a623-153">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="7a623-154">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="7a623-154">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7a623-155">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="7a623-155">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\Federation`  
  
## <a name="see-also"></a><span data-ttu-id="7a623-156">Viz také</span><span class="sxs-lookup"><span data-stu-id="7a623-156">See Also</span></span>
