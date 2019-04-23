---
title: 'Postupy: Určení zabezpečovacích pověření kanálu'
ms.date: 03/30/2017
ms.assetid: f8e03f47-9c4f-4dd5-8f85-429e6d876119
ms.openlocfilehash: 0bfbb71ade3822b9f504c2f89a41145ce0d435f6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59297977"
---
# <a name="how-to-specify-channel-security-credentials"></a><span data-ttu-id="1d6cc-102">Postupy: Určení zabezpečovacích pověření kanálu</span><span class="sxs-lookup"><span data-stu-id="1d6cc-102">How to: Specify Channel Security Credentials</span></span>
<span data-ttu-id="1d6cc-103">Monikeru služby Windows Communication Foundation (WCF) umožňuje aplikace modelu COM pro volání služeb WCF.</span><span class="sxs-lookup"><span data-stu-id="1d6cc-103">The Windows Communication Foundation (WCF) Service Moniker allows COM applications to call WCF services.</span></span> <span data-ttu-id="1d6cc-104">Většina služeb WCF vyžaduje klienta a zadejte přihlašovací údaje pro ověřování a autorizaci.</span><span class="sxs-lookup"><span data-stu-id="1d6cc-104">Most WCF services require the client to specify credentials for authentication and authorization.</span></span> <span data-ttu-id="1d6cc-105">Při volání služby WCF z klienta WCF, můžete zadat tyto přihlašovací údaje ve spravovaném kódu nebo konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="1d6cc-105">When calling a WCF service from a WCF client, you can specify these credentials in managed code or in an application configuration file.</span></span> <span data-ttu-id="1d6cc-106">Při volání služby WCF z aplikace COM, můžete použít <xref:System.ServiceModel.ComIntegration.IChannelCredentials> rozhraní a zadat přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="1d6cc-106">When calling a WCF service from a COM application, you can use the <xref:System.ServiceModel.ComIntegration.IChannelCredentials> interface to specify credentials.</span></span> <span data-ttu-id="1d6cc-107">Toto téma popisuje různé způsoby, jak zadat přihlašovací údaje pomocí <xref:System.ServiceModel.ComIntegration.IChannelCredentials> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="1d6cc-107">This topic will illustrate various ways to specify credentials using the <xref:System.ServiceModel.ComIntegration.IChannelCredentials> interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1d6cc-108"><xref:System.ServiceModel.ComIntegration.IChannelCredentials> je rozhraní založené na rozhraní IDispatch a nebudete získáte funkce IntelliSense v prostředí sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1d6cc-108"><xref:System.ServiceModel.ComIntegration.IChannelCredentials> is an IDispatch-based interface and you will not get IntelliSense functionality in the Visual Studio environment.</span></span>  
  
 <span data-ttu-id="1d6cc-109">Používat službě WCF definované v tomto článku [ukázka zabezpečení zpráv](../../../../docs/framework/wcf/samples/message-security-sample.md).</span><span class="sxs-lookup"><span data-stu-id="1d6cc-109">This article will use the WCF service defined in the [Message Security Sample](../../../../docs/framework/wcf/samples/message-security-sample.md).</span></span>  
  
### <a name="to-specify-a-client-certificate"></a><span data-ttu-id="1d6cc-110">K zadání klientského certifikátu</span><span class="sxs-lookup"><span data-stu-id="1d6cc-110">To specify a client certificate</span></span>  
  
1. <span data-ttu-id="1d6cc-111">Spusťte soubor Setup.bat v adresáři zabezpečení zpráv a vytvořte a nainstalujte požadované testovací certifikáty.</span><span class="sxs-lookup"><span data-stu-id="1d6cc-111">Run the Setup.bat file in the Message Security directory to create and install the required test certificates.</span></span>  
  
2. <span data-ttu-id="1d6cc-112">Otevřete projekt zabezpečení zpráv.</span><span class="sxs-lookup"><span data-stu-id="1d6cc-112">Open the Message Security project.</span></span>  
  
3. <span data-ttu-id="1d6cc-113">Přidat `[ServiceBehavior(Namespace="http://Microsoft.ServiceModel.Samples")]` k `ICalculator` definici rozhraní.</span><span class="sxs-lookup"><span data-stu-id="1d6cc-113">Add `[ServiceBehavior(Namespace="http://Microsoft.ServiceModel.Samples")]` to the `ICalculator` interface definition.</span></span>  
  
4. <span data-ttu-id="1d6cc-114">Přidat `bindingNamespace="http://Microsoft.ServiceModel.Samples"` ke značce koncového bodu v souboru App.config pro službu.</span><span class="sxs-lookup"><span data-stu-id="1d6cc-114">Add `bindingNamespace="http://Microsoft.ServiceModel.Samples"` to the endpoint tag in the App.config for the service.</span></span>  
  
5. <span data-ttu-id="1d6cc-115">Ukázka zabezpečení zpráv sestavíte a spustíte Service.exe.</span><span class="sxs-lookup"><span data-stu-id="1d6cc-115">Build the Message Security Sample and run Service.exe.</span></span> <span data-ttu-id="1d6cc-116">Pomocí aplikace Internet Explorer a přejděte na identifikátor URI služby (http://localhost:8000/ServiceModelSamples/Service) zajistit, služba funguje.</span><span class="sxs-lookup"><span data-stu-id="1d6cc-116">Use Internet Explorer and browse to the service's URI (http://localhost:8000/ServiceModelSamples/Service) to ensure that the service is working.</span></span>  
  
6. <span data-ttu-id="1d6cc-117">Otevřete Visual Basic 6.0 a vytvořte nový soubor standardní .exe.</span><span class="sxs-lookup"><span data-stu-id="1d6cc-117">Open Visual Basic 6.0 and create a new Standard .exe file.</span></span> <span data-ttu-id="1d6cc-118">Přidání tlačítka do formuláře a dvakrát klikněte na tlačítko Přidat následující kód do obslužné rutiny kliknutí:</span><span class="sxs-lookup"><span data-stu-id="1d6cc-118">Add a button to the form and double-click the button to add the following code to the Click handler:</span></span>  
  
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
  
7. <span data-ttu-id="1d6cc-119">Spuštění aplikace Visual Basic a ověřte výsledky.</span><span class="sxs-lookup"><span data-stu-id="1d6cc-119">Run the Visual Basic application and verify the results.</span></span>  
  
     <span data-ttu-id="1d6cc-120">Aplikace Visual Basic zobrazí okno se zprávou s výsledkem volání přidat (3, 4).</span><span class="sxs-lookup"><span data-stu-id="1d6cc-120">The Visual Basic application will display a message box with the result from calling Add(3, 4).</span></span> <span data-ttu-id="1d6cc-121"><xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromFile%28System.String%2CSystem.String%2CSystem.String%29> nebo <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromStoreByName%28System.String%2CSystem.String%2CSystem.String%29> je také možné místo <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromStore%28System.String%2CSystem.String%2CSystem.String%2CSystem.Object%29> nastavit certifikát klienta:</span><span class="sxs-lookup"><span data-stu-id="1d6cc-121"><xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromFile%28System.String%2CSystem.String%2CSystem.String%29> or <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromStoreByName%28System.String%2CSystem.String%2CSystem.String%29> can also be used in place of <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromStore%28System.String%2CSystem.String%2CSystem.String%2CSystem.Object%29> to set the Client Certificate:</span></span>  
  
    ```  
    monikerProxy.ChannelCredentials.SetClientCertificateFromFile "C:\MyClientCert.pfx", "password", "DefaultKeySet"  
    ```  
  
> [!NOTE]
>  <span data-ttu-id="1d6cc-122">Pro toto volání pro práci musí být důvěryhodné. na počítači, na kterém běží klientem na klientský certifikát.</span><span class="sxs-lookup"><span data-stu-id="1d6cc-122">For this call to work, the client certificate needs to be trusted on the machine the client is running on.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1d6cc-123">Pokud je moniker je poškozený nebo pokud služba není dostupná, volání `GetObject` vrátí chyba s oznámením "Neplatnou syntaxi."</span><span class="sxs-lookup"><span data-stu-id="1d6cc-123">If the moniker is malformed or if the service is unavailable, the call to `GetObject` will return an error saying "Invalid Syntax."</span></span> <span data-ttu-id="1d6cc-124">Pokud se zobrazí tato chyba, ujistěte se, že zástupný název, který používáte, je správná a služba není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="1d6cc-124">If you receive this error, make sure the moniker you are using is correct and the service is available.</span></span>  
  
### <a name="to-specify-user-name-and-password"></a><span data-ttu-id="1d6cc-125">K zadání uživatelského jména a hesla</span><span class="sxs-lookup"><span data-stu-id="1d6cc-125">To specify user name and password</span></span>  
  
1. <span data-ttu-id="1d6cc-126">Upravte soubor App.config služba používat `wsHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="1d6cc-126">Modify the Service App.config file to use the `wsHttpBinding`.</span></span> <span data-ttu-id="1d6cc-127">To je potřeba pro ověřování uživatelského jména a hesla:</span><span class="sxs-lookup"><span data-stu-id="1d6cc-127">This is required for user name and password validation:</span></span>  

2. <span data-ttu-id="1d6cc-128">Nastavte `clientCredentialType` na uživatelské jméno:</span><span class="sxs-lookup"><span data-stu-id="1d6cc-128">Set the `clientCredentialType` to UserName:</span></span>  

3. <span data-ttu-id="1d6cc-129">Otevřete Visual Basic 6.0 a vytvořte nový soubor standardní .exe.</span><span class="sxs-lookup"><span data-stu-id="1d6cc-129">Open Visual Basic 6.0 and create a new Standard .exe file.</span></span> <span data-ttu-id="1d6cc-130">Přidání tlačítka do formuláře a dvakrát klikněte na tlačítko Přidat následující kód do obslužné rutiny kliknutí:</span><span class="sxs-lookup"><span data-stu-id="1d6cc-130">Add a button to the form and double-click the button to add the following code to the Click handler:</span></span>  
  
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
  
4. <span data-ttu-id="1d6cc-131">Spuštění aplikace Visual Basic a ověřte výsledky.</span><span class="sxs-lookup"><span data-stu-id="1d6cc-131">Run the Visual Basic application and verify the results.</span></span> <span data-ttu-id="1d6cc-132">Aplikace Visual Basic zobrazí okno se zprávou s výsledkem volání přidat (3, 4).</span><span class="sxs-lookup"><span data-stu-id="1d6cc-132">The Visual Basic application will display a message box with the result from calling Add(3, 4).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1d6cc-133">Vazby určené v monikeru služby v této ukázce se změnil na WSHttpBinding_ICalculator.</span><span class="sxs-lookup"><span data-stu-id="1d6cc-133">The binding specified in the service moniker in this sample has been changed to WSHttpBinding_ICalculator.</span></span> <span data-ttu-id="1d6cc-134">Všimněte si také, že musíte zadat platné uživatelské jméno a heslo při volání funkce <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetUserNameCredential%28System.String%2CSystem.String%29>.</span><span class="sxs-lookup"><span data-stu-id="1d6cc-134">Also note that you must supply a valid user name and password in the call to <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetUserNameCredential%28System.String%2CSystem.String%29>.</span></span>  
  
### <a name="to-specify-windows-credentials"></a><span data-ttu-id="1d6cc-135">K zadání přihlašovacích údajů Windows</span><span class="sxs-lookup"><span data-stu-id="1d6cc-135">To specify Windows Credentials</span></span>  
  
1. <span data-ttu-id="1d6cc-136">Nastavte `clientCredentialType` pro Windows v souboru App.config služby:</span><span class="sxs-lookup"><span data-stu-id="1d6cc-136">Set `clientCredentialType` to Windows in the Service App.config file:</span></span>  

2. <span data-ttu-id="1d6cc-137">Otevřete Visual Basic 6.0 a vytvořte nový soubor standardní .exe.</span><span class="sxs-lookup"><span data-stu-id="1d6cc-137">Open Visual Basic 6.0 and create a new Standard .exe file.</span></span> <span data-ttu-id="1d6cc-138">Přidání tlačítka do formuláře a dvakrát klikněte na tlačítko Přidat následující kód do obslužné rutiny kliknutí:</span><span class="sxs-lookup"><span data-stu-id="1d6cc-138">Add a button to the form and double-click the button to add the following code to the Click handler:</span></span>  
  
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
  
3. <span data-ttu-id="1d6cc-139">Spuštění aplikace Visual Basic a ověřte výsledky.</span><span class="sxs-lookup"><span data-stu-id="1d6cc-139">Run the Visual Basic application and verify the results.</span></span> <span data-ttu-id="1d6cc-140">Aplikace Visual Basic zobrazí okno se zprávou s výsledkem volání přidat (3, 4).</span><span class="sxs-lookup"><span data-stu-id="1d6cc-140">The Visual Basic application will display a message box with the result from calling Add(3, 4).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1d6cc-141">Platné hodnoty musí nahradit "domény", "userID" a "password".</span><span class="sxs-lookup"><span data-stu-id="1d6cc-141">You must replace "domain", "userID", and "password" with valid values.</span></span>  
  
### <a name="to-specify-an-issue-token"></a><span data-ttu-id="1d6cc-142">K určení tokenu problém</span><span class="sxs-lookup"><span data-stu-id="1d6cc-142">To specify an issue token</span></span>  
  
1. <span data-ttu-id="1d6cc-143">Tokeny problém se používají pouze pro aplikace pomocí federovaného zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="1d6cc-143">Issue tokens are used only for applications using federated security.</span></span> <span data-ttu-id="1d6cc-144">Další informace o zabezpečení najdete v tématu [federace a vydané tokeny](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md) a [ukázka federace](../../../../docs/framework/wcf/samples/federation-sample.md).</span><span class="sxs-lookup"><span data-stu-id="1d6cc-144">For more information about federated security, see [Federation and Issued Tokens](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md) and [Federation Sample](../../../../docs/framework/wcf/samples/federation-sample.md).</span></span>  
  
     <span data-ttu-id="1d6cc-145">Následující příklad kódu jazyka Visual Basic, ukazuje, jak volat <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetIssuedToken%28System.String%2CSystem.String%2CSystem.String%29> metody:</span><span class="sxs-lookup"><span data-stu-id="1d6cc-145">The following Visual Basic code example illustrates how to call the <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetIssuedToken%28System.String%2CSystem.String%2CSystem.String%29> method:</span></span>  
  
    ```  
        monString = "service:mexAddress=http://localhost:8000/ServiceModelSamples/Service?wsdl"  
        monString = monString + ", address=http://localhost:8000/SomeService/Service"  
        monString = monString + ", contract=ICalculator, contractNamespace=http://SomeService.Samples"  
        monString = monString + ", binding=WSHttpBinding_ISomeContract, bindingNamespace=http://SomeService.Samples"  
  
        Set monikerProxy = GetObject(monString)  
    monikerProxy.SetIssuedToken("http://somemachine/sts", "bindingType", "binding")  
    ```  
  
     <span data-ttu-id="1d6cc-146">Další informace o parametrech pro tuto metodu, najdete v části <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetIssuedToken%28System.String%2CSystem.String%2CSystem.String%29>.</span><span class="sxs-lookup"><span data-stu-id="1d6cc-146">For more information about the parameters for this method, see <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetIssuedToken%28System.String%2CSystem.String%2CSystem.String%29>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d6cc-147">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1d6cc-147">See also</span></span>

- [<span data-ttu-id="1d6cc-148">Federace</span><span class="sxs-lookup"><span data-stu-id="1d6cc-148">Federation</span></span>](../../../../docs/framework/wcf/feature-details/federation.md)
- [<span data-ttu-id="1d6cc-149">Postupy: Konfigurace pověření ve službě Federation Service</span><span class="sxs-lookup"><span data-stu-id="1d6cc-149">How to: Configure Credentials on a Federation Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [<span data-ttu-id="1d6cc-150">Postupy: Vytvoření federovaného klienta</span><span class="sxs-lookup"><span data-stu-id="1d6cc-150">How to: Create a Federated Client</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="1d6cc-151">Zabezpečení zpráv</span><span class="sxs-lookup"><span data-stu-id="1d6cc-151">Message Security</span></span>](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)
- [<span data-ttu-id="1d6cc-152">Vazby a zabezpečení</span><span class="sxs-lookup"><span data-stu-id="1d6cc-152">Bindings and Security</span></span>](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)
