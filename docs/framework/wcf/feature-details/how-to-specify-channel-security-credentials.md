---
title: 'Postupy: Určení zabezpečovacích pověření kanálu'
ms.date: 03/30/2017
ms.assetid: f8e03f47-9c4f-4dd5-8f85-429e6d876119
ms.openlocfilehash: 3d6131a7488d9932118a988095791dd06fd46c49
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933450"
---
# <a name="how-to-specify-channel-security-credentials"></a><span data-ttu-id="76c70-102">Postupy: Určení zabezpečovacích pověření kanálu</span><span class="sxs-lookup"><span data-stu-id="76c70-102">How to: Specify Channel Security Credentials</span></span>
<span data-ttu-id="76c70-103">Moniker služby Windows Communication Foundation (WCF) umožňuje aplikacím COM volat služby WCF.</span><span class="sxs-lookup"><span data-stu-id="76c70-103">The Windows Communication Foundation (WCF) Service Moniker allows COM applications to call WCF services.</span></span> <span data-ttu-id="76c70-104">Většina služeb WCF vyžaduje, aby klient určil přihlašovací údaje pro ověřování a autorizaci.</span><span class="sxs-lookup"><span data-stu-id="76c70-104">Most WCF services require the client to specify credentials for authentication and authorization.</span></span> <span data-ttu-id="76c70-105">Při volání služby WCF z klienta WCF můžete zadat tyto přihlašovací údaje ve spravovaném kódu nebo v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="76c70-105">When calling a WCF service from a WCF client, you can specify these credentials in managed code or in an application configuration file.</span></span> <span data-ttu-id="76c70-106">Při volání služby WCF z aplikace COM můžete použít <xref:System.ServiceModel.ComIntegration.IChannelCredentials> rozhraní k zadání přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="76c70-106">When calling a WCF service from a COM application, you can use the <xref:System.ServiceModel.ComIntegration.IChannelCredentials> interface to specify credentials.</span></span> <span data-ttu-id="76c70-107">Toto téma popisuje různé způsoby, jak zadat pověření pomocí <xref:System.ServiceModel.ComIntegration.IChannelCredentials> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="76c70-107">This topic will illustrate various ways to specify credentials using the <xref:System.ServiceModel.ComIntegration.IChannelCredentials> interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="76c70-108"><xref:System.ServiceModel.ComIntegration.IChannelCredentials>je rozhraní založené na rozhraní IDispatch a nebude možné získat funkce technologie IntelliSense v prostředí sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="76c70-108"><xref:System.ServiceModel.ComIntegration.IChannelCredentials> is an IDispatch-based interface and you will not get IntelliSense functionality in the Visual Studio environment.</span></span>  
  
 <span data-ttu-id="76c70-109">Tento článek bude používat službu WCF definovanou v [ukázce zabezpečení zpráv](../../../../docs/framework/wcf/samples/message-security-sample.md).</span><span class="sxs-lookup"><span data-stu-id="76c70-109">This article will use the WCF service defined in the [Message Security Sample](../../../../docs/framework/wcf/samples/message-security-sample.md).</span></span>  
  
### <a name="to-specify-a-client-certificate"></a><span data-ttu-id="76c70-110">Určení klientského certifikátu</span><span class="sxs-lookup"><span data-stu-id="76c70-110">To specify a client certificate</span></span>  
  
1. <span data-ttu-id="76c70-111">Spusťte soubor Setup. bat v adresáři zabezpečení zprávy pro vytvoření a instalaci požadovaných testovacích certifikátů.</span><span class="sxs-lookup"><span data-stu-id="76c70-111">Run the Setup.bat file in the Message Security directory to create and install the required test certificates.</span></span>  
  
2. <span data-ttu-id="76c70-112">Otevřete projekt zabezpečení zprávy.</span><span class="sxs-lookup"><span data-stu-id="76c70-112">Open the Message Security project.</span></span>  
  
3. <span data-ttu-id="76c70-113">`[ServiceBehavior(Namespace="http://Microsoft.ServiceModel.Samples")]` Přidejte`ICalculator` do definice rozhraní.</span><span class="sxs-lookup"><span data-stu-id="76c70-113">Add `[ServiceBehavior(Namespace="http://Microsoft.ServiceModel.Samples")]` to the `ICalculator` interface definition.</span></span>  
  
4. <span data-ttu-id="76c70-114">Přidá `bindingNamespace="http://Microsoft.ServiceModel.Samples"` se do značky Endpoint v App. config pro službu.</span><span class="sxs-lookup"><span data-stu-id="76c70-114">Add `bindingNamespace="http://Microsoft.ServiceModel.Samples"` to the endpoint tag in the App.config for the service.</span></span>  
  
5. <span data-ttu-id="76c70-115">Sestavte ukázku zabezpečení zpráv a spusťte Service. exe.</span><span class="sxs-lookup"><span data-stu-id="76c70-115">Build the Message Security Sample and run Service.exe.</span></span> <span data-ttu-id="76c70-116">Použijte Internet Explorer a přejděte k identifikátoru URI služby (http://localhost:8000/ServiceModelSamples/Service) abyste zajistili, že služba funguje.</span><span class="sxs-lookup"><span data-stu-id="76c70-116">Use Internet Explorer and browse to the service's URI (http://localhost:8000/ServiceModelSamples/Service) to ensure that the service is working.</span></span>  
  
6. <span data-ttu-id="76c70-117">Otevřete Visual Basic 6,0 a vytvořte nový standardní soubor. exe.</span><span class="sxs-lookup"><span data-stu-id="76c70-117">Open Visual Basic 6.0 and create a new Standard .exe file.</span></span> <span data-ttu-id="76c70-118">Přidejte do formuláře tlačítko a dvakrát klikněte na tlačítko a přidejte následující kód do obslužné rutiny Click:</span><span class="sxs-lookup"><span data-stu-id="76c70-118">Add a button to the form and double-click the button to add the following code to the Click handler:</span></span>  
  
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
  
7. <span data-ttu-id="76c70-119">Spusťte aplikaci Visual Basic a ověřte výsledky.</span><span class="sxs-lookup"><span data-stu-id="76c70-119">Run the Visual Basic application and verify the results.</span></span>  
  
     <span data-ttu-id="76c70-120">V aplikaci Visual Basic se zobrazí okno se zprávou s výsledkem volání metody Add (3, 4).</span><span class="sxs-lookup"><span data-stu-id="76c70-120">The Visual Basic application will display a message box with the result from calling Add(3, 4).</span></span> <span data-ttu-id="76c70-121"><xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromFile%28System.String%2CSystem.String%2CSystem.String%29>Můžete také použít <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromStore%28System.String%2CSystem.String%2CSystem.String%2CSystem.Object%29> místo pro nastavení klientského certifikátu: <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromStoreByName%28System.String%2CSystem.String%2CSystem.String%29></span><span class="sxs-lookup"><span data-stu-id="76c70-121"><xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromFile%28System.String%2CSystem.String%2CSystem.String%29> or <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromStoreByName%28System.String%2CSystem.String%2CSystem.String%29> can also be used in place of <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromStore%28System.String%2CSystem.String%2CSystem.String%2CSystem.Object%29> to set the Client Certificate:</span></span>  
  
    ```  
    monikerProxy.ChannelCredentials.SetClientCertificateFromFile "C:\MyClientCert.pfx", "password", "DefaultKeySet"  
    ```  
  
> [!NOTE]
> <span data-ttu-id="76c70-122">Aby toto volání fungovalo, musí být klientský certifikát důvěryhodný na počítači, na kterém je spuštěný klient nástroje.</span><span class="sxs-lookup"><span data-stu-id="76c70-122">For this call to work, the client certificate needs to be trusted on the machine the client is running on.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="76c70-123">Pokud je moniker poškozený nebo pokud není služba k dispozici, volání vrátí chybu `GetObject` s názvem neplatná syntaxe.</span><span class="sxs-lookup"><span data-stu-id="76c70-123">If the moniker is malformed or if the service is unavailable, the call to `GetObject` will return an error saying "Invalid Syntax."</span></span> <span data-ttu-id="76c70-124">Pokud se zobrazí tato chyba, ujistěte se, že moniker, který používáte, je správný a služba je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="76c70-124">If you receive this error, make sure the moniker you are using is correct and the service is available.</span></span>  
  
### <a name="to-specify-user-name-and-password"></a><span data-ttu-id="76c70-125">Zadání uživatelského jména a hesla</span><span class="sxs-lookup"><span data-stu-id="76c70-125">To specify user name and password</span></span>  
  
1. <span data-ttu-id="76c70-126">Upravte soubor App. config aplikace služby tak, aby `wsHttpBinding`používal.</span><span class="sxs-lookup"><span data-stu-id="76c70-126">Modify the Service App.config file to use the `wsHttpBinding`.</span></span> <span data-ttu-id="76c70-127">Tato akce je nutná pro ověření uživatelského jména a hesla:</span><span class="sxs-lookup"><span data-stu-id="76c70-127">This is required for user name and password validation:</span></span>  

2. <span data-ttu-id="76c70-128">`clientCredentialType` Nastavte na uživatelské jméno:</span><span class="sxs-lookup"><span data-stu-id="76c70-128">Set the `clientCredentialType` to UserName:</span></span>  

3. <span data-ttu-id="76c70-129">Otevřete Visual Basic 6,0 a vytvořte nový standardní soubor. exe.</span><span class="sxs-lookup"><span data-stu-id="76c70-129">Open Visual Basic 6.0 and create a new Standard .exe file.</span></span> <span data-ttu-id="76c70-130">Přidejte do formuláře tlačítko a dvakrát klikněte na tlačítko a přidejte následující kód do obslužné rutiny Click:</span><span class="sxs-lookup"><span data-stu-id="76c70-130">Add a button to the form and double-click the button to add the following code to the Click handler:</span></span>  
  
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
  
4. <span data-ttu-id="76c70-131">Spusťte aplikaci Visual Basic a ověřte výsledky.</span><span class="sxs-lookup"><span data-stu-id="76c70-131">Run the Visual Basic application and verify the results.</span></span> <span data-ttu-id="76c70-132">V aplikaci Visual Basic se zobrazí okno se zprávou s výsledkem volání metody Add (3, 4).</span><span class="sxs-lookup"><span data-stu-id="76c70-132">The Visual Basic application will display a message box with the result from calling Add(3, 4).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="76c70-133">Vazba zadaná v monikeru služby v této ukázce se změnila na WSHttpBinding_ICalculator.</span><span class="sxs-lookup"><span data-stu-id="76c70-133">The binding specified in the service moniker in this sample has been changed to WSHttpBinding_ICalculator.</span></span> <span data-ttu-id="76c70-134">Všimněte si také, že při volání <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetUserNameCredential%28System.String%2CSystem.String%29>je nutné uvést platné uživatelské jméno a heslo.</span><span class="sxs-lookup"><span data-stu-id="76c70-134">Also note that you must supply a valid user name and password in the call to <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetUserNameCredential%28System.String%2CSystem.String%29>.</span></span>  
  
### <a name="to-specify-windows-credentials"></a><span data-ttu-id="76c70-135">Zadání přihlašovacích údajů systému Windows</span><span class="sxs-lookup"><span data-stu-id="76c70-135">To specify Windows Credentials</span></span>  
  
1. <span data-ttu-id="76c70-136">Nastavte `clientCredentialType` na Windows v souboru App. config aplikace služby:</span><span class="sxs-lookup"><span data-stu-id="76c70-136">Set `clientCredentialType` to Windows in the Service App.config file:</span></span>  

2. <span data-ttu-id="76c70-137">Otevřete Visual Basic 6,0 a vytvořte nový standardní soubor. exe.</span><span class="sxs-lookup"><span data-stu-id="76c70-137">Open Visual Basic 6.0 and create a new Standard .exe file.</span></span> <span data-ttu-id="76c70-138">Přidejte do formuláře tlačítko a dvakrát klikněte na tlačítko a přidejte následující kód do obslužné rutiny Click:</span><span class="sxs-lookup"><span data-stu-id="76c70-138">Add a button to the form and double-click the button to add the following code to the Click handler:</span></span>  
  
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
  
3. <span data-ttu-id="76c70-139">Spusťte aplikaci Visual Basic a ověřte výsledky.</span><span class="sxs-lookup"><span data-stu-id="76c70-139">Run the Visual Basic application and verify the results.</span></span> <span data-ttu-id="76c70-140">V aplikaci Visual Basic se zobrazí okno se zprávou s výsledkem volání metody Add (3, 4).</span><span class="sxs-lookup"><span data-stu-id="76c70-140">The Visual Basic application will display a message box with the result from calling Add(3, 4).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="76c70-141">Platné hodnoty musí nahradit "doména", "userID" a "heslo".</span><span class="sxs-lookup"><span data-stu-id="76c70-141">You must replace "domain", "userID", and "password" with valid values.</span></span>  
  
### <a name="to-specify-an-issue-token"></a><span data-ttu-id="76c70-142">Určení tokenu problému</span><span class="sxs-lookup"><span data-stu-id="76c70-142">To specify an issue token</span></span>  
  
1. <span data-ttu-id="76c70-143">Tokeny vydávání se používají jenom pro aplikace, které používají federované zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="76c70-143">Issue tokens are used only for applications using federated security.</span></span> <span data-ttu-id="76c70-144">Další informace o federovaném zabezpečení najdete v tématu [federace a vystavené tokeny](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md) a [Ukázka federace](../../../../docs/framework/wcf/samples/federation-sample.md).</span><span class="sxs-lookup"><span data-stu-id="76c70-144">For more information about federated security, see [Federation and Issued Tokens](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md) and [Federation Sample](../../../../docs/framework/wcf/samples/federation-sample.md).</span></span>  
  
     <span data-ttu-id="76c70-145">Následující příklad kódu Visual Basic ukazuje, jak zavolat <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetIssuedToken%28System.String%2CSystem.String%2CSystem.String%29> metodu:</span><span class="sxs-lookup"><span data-stu-id="76c70-145">The following Visual Basic code example illustrates how to call the <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetIssuedToken%28System.String%2CSystem.String%2CSystem.String%29> method:</span></span>  
  
    ```  
        monString = "service:mexAddress=http://localhost:8000/ServiceModelSamples/Service?wsdl"  
        monString = monString + ", address=http://localhost:8000/SomeService/Service"  
        monString = monString + ", contract=ICalculator, contractNamespace=http://SomeService.Samples"  
        monString = monString + ", binding=WSHttpBinding_ISomeContract, bindingNamespace=http://SomeService.Samples"  
  
        Set monikerProxy = GetObject(monString)  
    monikerProxy.SetIssuedToken("http://somemachine/sts", "bindingType", "binding")  
    ```  
  
     <span data-ttu-id="76c70-146">Další informace o parametrech této metody naleznete v tématu <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetIssuedToken%28System.String%2CSystem.String%2CSystem.String%29>.</span><span class="sxs-lookup"><span data-stu-id="76c70-146">For more information about the parameters for this method, see <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetIssuedToken%28System.String%2CSystem.String%2CSystem.String%29>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76c70-147">Viz také:</span><span class="sxs-lookup"><span data-stu-id="76c70-147">See also</span></span>

- [<span data-ttu-id="76c70-148">Federace</span><span class="sxs-lookup"><span data-stu-id="76c70-148">Federation</span></span>](../../../../docs/framework/wcf/feature-details/federation.md)
- [<span data-ttu-id="76c70-149">Postupy: Konfigurace přihlašovacích údajů na služba FS (Federation Service)</span><span class="sxs-lookup"><span data-stu-id="76c70-149">How to: Configure Credentials on a Federation Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [<span data-ttu-id="76c70-150">Postupy: Vytvoření federovaného klienta</span><span class="sxs-lookup"><span data-stu-id="76c70-150">How to: Create a Federated Client</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="76c70-151">Zabezpečení zpráv</span><span class="sxs-lookup"><span data-stu-id="76c70-151">Message Security</span></span>](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)
- [<span data-ttu-id="76c70-152">Vazby a zabezpečení</span><span class="sxs-lookup"><span data-stu-id="76c70-152">Bindings and Security</span></span>](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)
