---
title: "Postupy: Zadejte pověření zabezpečení kanálu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f8e03f47-9c4f-4dd5-8f85-429e6d876119
caps.latest.revision: "18"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: e2aedb06ec694f6c7dfb12b70ab919ae23eed17e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-channel-security-credentials"></a><span data-ttu-id="73755-102">Postupy: Zadejte pověření zabezpečení kanálu</span><span class="sxs-lookup"><span data-stu-id="73755-102">How to: Specify Channel Security Credentials</span></span>
<span data-ttu-id="73755-103">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Monikeru služby umožňuje aplikacím COM volání [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby.</span><span class="sxs-lookup"><span data-stu-id="73755-103">The [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Service Moniker allows COM applications to call [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services.</span></span> <span data-ttu-id="73755-104">Většina [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby vyžadují klienta a zadejte pověření pro ověřování a autorizaci.</span><span class="sxs-lookup"><span data-stu-id="73755-104">Most [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services require the client to specify credentials for authentication and authorization.</span></span> <span data-ttu-id="73755-105">Při volání metody [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta, můžete zadat tyto přihlašovací údaje ve spravovaném kódu nebo v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="73755-105">When calling a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service from a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client, you can specify these credentials in managed code or in an application configuration file.</span></span> <span data-ttu-id="73755-106">Při volání metody [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby z aplikace modelu COM, můžete použít <xref:System.ServiceModel.ComIntegration.IChannelCredentials> rozhraní k zadání přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="73755-106">When calling a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service from a COM application, you can use the <xref:System.ServiceModel.ComIntegration.IChannelCredentials> interface to specify credentials.</span></span> <span data-ttu-id="73755-107">Toto téma se ilustrují různé způsoby, jak zadat přihlašovací údaje pomocí <xref:System.ServiceModel.ComIntegration.IChannelCredentials> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="73755-107">This topic will illustrate various ways to specify credentials using the <xref:System.ServiceModel.ComIntegration.IChannelCredentials> interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="73755-108"><xref:System.ServiceModel.ComIntegration.IChannelCredentials>je rozhraní, na základě IDispatch a nebude používat funkci IntelliSense v prostředí Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="73755-108"><xref:System.ServiceModel.ComIntegration.IChannelCredentials> is an IDispatch-based interface and you will not get IntelliSense functionality in the Visual Studio environment.</span></span>  
  
 <span data-ttu-id="73755-109">Tento článek se použije [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby definované v [ukázka zabezpečení zpráv](../../../../docs/framework/wcf/samples/message-security-sample.md).</span><span class="sxs-lookup"><span data-stu-id="73755-109">This article will use the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service defined in the [Message Security Sample](../../../../docs/framework/wcf/samples/message-security-sample.md).</span></span>  
  
### <a name="to-specify-a-client-certificate"></a><span data-ttu-id="73755-110">Chcete zadat klientský certifikát</span><span class="sxs-lookup"><span data-stu-id="73755-110">To specify a client certificate</span></span>  
  
1.  <span data-ttu-id="73755-111">Spusťte soubor Setup.bat v zabezpečení zpráv adresář, který chcete vytvořit a nainstalovat požadované testovací certifikáty.</span><span class="sxs-lookup"><span data-stu-id="73755-111">Run the Setup.bat file in the Message Security directory to create and install the required test certificates.</span></span>  
  
2.  <span data-ttu-id="73755-112">Otevřete projekt zabezpečení zpráv.</span><span class="sxs-lookup"><span data-stu-id="73755-112">Open the Message Security project.</span></span>  
  
3.  <span data-ttu-id="73755-113">Přidat `[ServiceBehavior(Namespace=``http://Microsoft.ServiceModel.Samples``)]` k `ICalculator` definici rozhraní.</span><span class="sxs-lookup"><span data-stu-id="73755-113">Add `[ServiceBehavior(Namespace=``http://Microsoft.ServiceModel.Samples``)]` to the `ICalculator` interface definition.</span></span>  
  
4.  <span data-ttu-id="73755-114">Přidat `bindingNamespace=``http://Microsoft.ServiceModel.Samples` ke značce koncový bod v souboru App.config pro službu.</span><span class="sxs-lookup"><span data-stu-id="73755-114">Add `bindingNamespace=``http://Microsoft.ServiceModel.Samples` to the endpoint tag in the App.config for the service.</span></span>  
  
5.  <span data-ttu-id="73755-115">Ukázka zabezpečení zpráv sestavit a spustit Service.exe.</span><span class="sxs-lookup"><span data-stu-id="73755-115">Build the Message Security Sample and run Service.exe.</span></span> <span data-ttu-id="73755-116">Použijte Internet Explorer a přejděte do služby URI (http://localhost: 8000/ServiceModelSamples/Service) k zajištění, že služba funguje.</span><span class="sxs-lookup"><span data-stu-id="73755-116">Use Internet Explorer and browse to the service's URI (http://localhost:8000/ServiceModelSamples/Service) to ensure that the service is working.</span></span>  
  
6.  <span data-ttu-id="73755-117">Otevřete Visual Basic 6.0 a vytvořte nový soubor standardní .exe.</span><span class="sxs-lookup"><span data-stu-id="73755-117">Open Visual Basic 6.0 and create a new Standard .exe file.</span></span> <span data-ttu-id="73755-118">Přidání tlačítka do formuláře a dvakrát klikněte na tlačítko pro přidání do obslužná rutina kliknutí na následující kód:</span><span class="sxs-lookup"><span data-stu-id="73755-118">Add a button to the form and double-click the button to add the following code to the Click handler:</span></span>  
  
    ```  
        monString = "service:mexAddress=http://localhost:8000/ServiceModelSamples/Service?wsdl"  
        monString = monString + ", address=http://localhost:8000/ServiceModelSamples/Service"  
        monString = monString + ", contract=ICalculator, contractNamespace=http://Microsoft.ServiceModel.Samples"  
        monString = monString + ", binding=BasicHttpBinding_ICalculator, bindingNamespace=http://Microsoft.ServiceModel.Samples"  
  
        Set monikerProxy = GetObject(monString)  
  
        'Set the Service Certificate.  
     monikerProxy.ChannelCredentials.SetServiceCertificateAuthentication "CurrentUser", "NoCheck", "PeerOrChainTrust"  
    monikerProxy.ChannelCredentials.SetDefaultServiceCertificateFromStore "CurrentUser", "TrustedPeople", "FindBySubjectName", "localhost"  
  
        'Set the Client Certificate.  
        monikerProxy.ChannelCredentials.SetClientCertificateFromStoreByName "CN=client.com", "CurrentUser", "My"  
        MsgBox monikerProxy.Add(3, 4)  
    ```  
  
7.  <span data-ttu-id="73755-119">Spuštění aplikace Visual Basic a ověřte výsledky.</span><span class="sxs-lookup"><span data-stu-id="73755-119">Run the Visual Basic application and verify the results.</span></span>  
  
     <span data-ttu-id="73755-120">Visual Basic aplikace se zobrazí okno se zprávou o výsledky volání metody přidat (3, 4).</span><span class="sxs-lookup"><span data-stu-id="73755-120">The Visual Basic application will display a message box with the result from calling Add(3, 4).</span></span> <span data-ttu-id="73755-121"><xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromFile%28System.String%2CSystem.String%2CSystem.String%29>nebo <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromStoreByName%28System.String%2CSystem.String%2CSystem.String%29> lze také použít místě <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromStore%28System.String%2CSystem.String%2CSystem.String%2CSystem.Object%29> nastavit certifikát klienta:</span><span class="sxs-lookup"><span data-stu-id="73755-121"><xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromFile%28System.String%2CSystem.String%2CSystem.String%29> or <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromStoreByName%28System.String%2CSystem.String%2CSystem.String%29> can also be used in place of <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromStore%28System.String%2CSystem.String%2CSystem.String%2CSystem.Object%29> to set the Client Certificate:</span></span>  
  
    ```  
    monikerProxy.ChannelCredentials.SetClientCertificateFromFile "C:\MyClientCert.pfx", "password", "DefaultKeySet"  
    ```  
  
> [!NOTE]
>  <span data-ttu-id="73755-122">Pro toto volání pracovat klientský certifikát musí být v počítači, na kterém běží klient na považován za důvěryhodný.</span><span class="sxs-lookup"><span data-stu-id="73755-122">For this call to work, the client certificate needs to be trusted on the machine the client is running on.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="73755-123">Pokud Přezdívka je poškozený nebo pokud služba není dostupná, volání `GetObject` se vrátí chyba s oznámením "Neplatnou syntaxi."</span><span class="sxs-lookup"><span data-stu-id="73755-123">If the moniker is malformed or if the service is unavailable, the call to `GetObject` will return an error saying "Invalid Syntax."</span></span> <span data-ttu-id="73755-124">Pokud se zobrazí tato chyba, ujistěte se, kterou používáte Přezdívka je správný a služba není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="73755-124">If you receive this error, make sure the moniker you are using is correct and the service is available.</span></span>  
  
### <a name="to-specify-user-name-and-password"></a><span data-ttu-id="73755-125">Chcete-li určit uživatelské jméno a heslo</span><span class="sxs-lookup"><span data-stu-id="73755-125">To specify user name and password</span></span>  
  
1.  <span data-ttu-id="73755-126">Upravte soubor Service App.config a používat `wsHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="73755-126">Modify the Service App.config file to use the `wsHttpBinding`.</span></span> <span data-ttu-id="73755-127">Toto je vyžadován pro ověření uživatelské jméno a heslo:</span><span class="sxs-lookup"><span data-stu-id="73755-127">This is required for user name and password validation:</span></span>  
  
  
  
2.  <span data-ttu-id="73755-128">Nastavte `clientCredentialType` uživatelské jméno:</span><span class="sxs-lookup"><span data-stu-id="73755-128">Set the `clientCredentialType` to UserName:</span></span>  
  
  
  
3.  <span data-ttu-id="73755-129">Otevřete Visual Basic 6.0 a vytvořte nový soubor standardní .exe.</span><span class="sxs-lookup"><span data-stu-id="73755-129">Open Visual Basic 6.0 and create a new Standard .exe file.</span></span> <span data-ttu-id="73755-130">Přidání tlačítka do formuláře a dvakrát klikněte na tlačítko pro přidání do obslužná rutina kliknutí na následující kód:</span><span class="sxs-lookup"><span data-stu-id="73755-130">Add a button to the form and double-click the button to add the following code to the Click handler:</span></span>  
  
    ```  
    monString = "service:mexAddress=http://localhost:8000/ServiceModelSamples/Service?wsdl"  
    monString = monString + ", address=http://localhost:8000/ServiceModelSamples/Service"  
    monString = monString + ", contract=ICalculator, contractNamespace=http://Microsoft.ServiceModel.Samples"  
    monString = monString + ", binding=WSHttpBinding_ICalculator, bindingNamespace=http://Microsoft.ServiceModel.Samples"  
  
    Set monikerProxy = GetObject(monString)  
  
    monikerProxy.ChannelCredentials.SetServiceCertificateAuthentication "CurrentUser", "NoCheck", "PeerOrChainTrust"  
    monikerProxy.ChannelCredentials.SetUserNameCredential "username", "password"  
  
    MsgBox monikerProxy.Add(3, 4)  
    ```  
  
4.  <span data-ttu-id="73755-131">Spuštění aplikace Visual Basic a ověřte výsledky.</span><span class="sxs-lookup"><span data-stu-id="73755-131">Run the Visual Basic application and verify the results.</span></span> <span data-ttu-id="73755-132">Visual Basic aplikace se zobrazí okno se zprávou o výsledky volání metody přidat (3, 4).</span><span class="sxs-lookup"><span data-stu-id="73755-132">The Visual Basic application will display a message box with the result from calling Add(3, 4).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="73755-133">Vazba, zadaný v monikeru služby v této ukázce se změnil na WSHttpBinding_ICalculator.</span><span class="sxs-lookup"><span data-stu-id="73755-133">The binding specified in the service moniker in this sample has been changed to WSHttpBinding_ICalculator.</span></span> <span data-ttu-id="73755-134">Všimněte si, že musíte zadat platné uživatelské jméno a heslo ve volání <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetUserNameCredential%28System.String%2CSystem.String%29>.</span><span class="sxs-lookup"><span data-stu-id="73755-134">Also note that you must supply a valid user name and password in the call to <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetUserNameCredential%28System.String%2CSystem.String%29>.</span></span>  
  
### <a name="to-specify-windows-credentials"></a><span data-ttu-id="73755-135">K zadání pověření systému Windows</span><span class="sxs-lookup"><span data-stu-id="73755-135">To specify Windows Credentials</span></span>  
  
1.  <span data-ttu-id="73755-136">Nastavit `clientCredentialType` do systému Windows v souboru App.config služby:</span><span class="sxs-lookup"><span data-stu-id="73755-136">Set `clientCredentialType` to Windows in the Service App.config file:</span></span>  
  
  
  
2.  <span data-ttu-id="73755-137">Otevřete Visual Basic 6.0 a vytvořte nový soubor standardní .exe.</span><span class="sxs-lookup"><span data-stu-id="73755-137">Open Visual Basic 6.0 and create a new Standard .exe file.</span></span> <span data-ttu-id="73755-138">Přidání tlačítka do formuláře a dvakrát klikněte na tlačítko pro přidání do obslužná rutina kliknutí na následující kód:</span><span class="sxs-lookup"><span data-stu-id="73755-138">Add a button to the form and double-click the button to add the following code to the Click handler:</span></span>  
  
    ```  
    monString = "service:mexAddress=http://localhost:8000/ServiceModelSamples/Service?wsdl"  
    monString = monString + ", address=http://localhost:8000/ServiceModelSamples/Service"  
    monString = monString + ", contract=ICalculator, contractNamespace=http://Microsoft.ServiceModel.Samples"  
    monString = monString + ", binding=WSHttpBinding_ICalculator, bindingNamespace=http://Microsoft.ServiceModel.Samples"  
    monString = monString + ", upnidentity=domain\userID"  
  
    Set monikerProxy = GetObject(monString)  
     monikerProxy.ChannelCredentials.SetWindowsCredential "domain", "userID", "password", 1, True  
  
    MsgBox monikerProxy.Add(3, 4)  
    ```  
  
3.  <span data-ttu-id="73755-139">Spuštění aplikace Visual Basic a ověřte výsledky.</span><span class="sxs-lookup"><span data-stu-id="73755-139">Run the Visual Basic application and verify the results.</span></span> <span data-ttu-id="73755-140">Visual Basic aplikace se zobrazí okno se zprávou o výsledky volání metody přidat (3, 4).</span><span class="sxs-lookup"><span data-stu-id="73755-140">The Visual Basic application will display a message box with the result from calling Add(3, 4).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="73755-141">Je potřeba nahradit "domény", "userID" a "password" platné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="73755-141">You must replace "domain", "userID", and "password" with valid values.</span></span>  
  
### <a name="to-specify-an-issue-token"></a><span data-ttu-id="73755-142">K určení tokenu problém</span><span class="sxs-lookup"><span data-stu-id="73755-142">To specify an issue token</span></span>  
  
1.  <span data-ttu-id="73755-143">Tokeny problém se používají pouze pro aplikace, které používají federované zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="73755-143">Issue tokens are used only for applications using federated security.</span></span> <span data-ttu-id="73755-144">Další informace o federované zabezpečení najdete v tématu [federace a vystavené tokeny](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md) a [ukázka federace](../../../../docs/framework/wcf/samples/federation-sample.md).</span><span class="sxs-lookup"><span data-stu-id="73755-144">For more information about federated security, see [Federation and Issued Tokens](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md) and [Federation Sample](../../../../docs/framework/wcf/samples/federation-sample.md).</span></span>  
  
     <span data-ttu-id="73755-145">Následující příklad kódu jazyka Visual Basic ukazuje, jak volat <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetIssuedToken%28System.String%2CSystem.String%2CSystem.String%29> metoda:</span><span class="sxs-lookup"><span data-stu-id="73755-145">The following Visual Basic code example illustrates how to call the <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetIssuedToken%28System.String%2CSystem.String%2CSystem.String%29> method:</span></span>  
  
    ```  
        monString = "service:mexAddress=http://localhost:8000/ServiceModelSamples/Service?wsdl"  
        monString = monString + ", address=http://localhost:8000/SomeService/Service"  
        monString = monString + ", contract=ICalculator, contractNamespace=http://SomeService.Samples"  
        monString = monString + ", binding=WSHttpBinding_ISomeContract, bindingNamespace=http://SomeService.Samples"  
  
        Set monikerProxy = GetObject(monString)  
    monikerProxy.SetIssuedToken("http://somemachine/sts", "bindingType", "binding")  
    ```  
  
     <span data-ttu-id="73755-146">Další informace o parametrech pro tuto metodu, najdete v části <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetIssuedToken%28System.String%2CSystem.String%2CSystem.String%29>.</span><span class="sxs-lookup"><span data-stu-id="73755-146">For more information about the parameters for this method, see <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetIssuedToken%28System.String%2CSystem.String%2CSystem.String%29>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73755-147">Viz také</span><span class="sxs-lookup"><span data-stu-id="73755-147">See Also</span></span>  
 [<span data-ttu-id="73755-148">Federace</span><span class="sxs-lookup"><span data-stu-id="73755-148">Federation</span></span>](../../../../docs/framework/wcf/feature-details/federation.md)  
 [<span data-ttu-id="73755-149">Postupy: Konfigurace přihlašovacích údajů ve službě Federation Service</span><span class="sxs-lookup"><span data-stu-id="73755-149">How to: Configure Credentials on a Federation Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)  
 [<span data-ttu-id="73755-150">Postupy: Vytvoření federovaného klienta</span><span class="sxs-lookup"><span data-stu-id="73755-150">How to: Create a Federated Client</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [<span data-ttu-id="73755-151">Zabezpečení zpráv</span><span class="sxs-lookup"><span data-stu-id="73755-151">Message Security</span></span>](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)  
 [<span data-ttu-id="73755-152">Vazby a zabezpečení</span><span class="sxs-lookup"><span data-stu-id="73755-152">Bindings and Security</span></span>](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)
