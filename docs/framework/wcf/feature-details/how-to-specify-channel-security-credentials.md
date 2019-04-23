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
# <a name="how-to-specify-channel-security-credentials"></a>Postupy: Určení zabezpečovacích pověření kanálu
Monikeru služby Windows Communication Foundation (WCF) umožňuje aplikace modelu COM pro volání služeb WCF. Většina služeb WCF vyžaduje klienta a zadejte přihlašovací údaje pro ověřování a autorizaci. Při volání služby WCF z klienta WCF, můžete zadat tyto přihlašovací údaje ve spravovaném kódu nebo konfiguračního souboru aplikace. Při volání služby WCF z aplikace COM, můžete použít <xref:System.ServiceModel.ComIntegration.IChannelCredentials> rozhraní a zadat přihlašovací údaje. Toto téma popisuje různé způsoby, jak zadat přihlašovací údaje pomocí <xref:System.ServiceModel.ComIntegration.IChannelCredentials> rozhraní.  
  
> [!NOTE]
>  <xref:System.ServiceModel.ComIntegration.IChannelCredentials> je rozhraní založené na rozhraní IDispatch a nebudete získáte funkce IntelliSense v prostředí sady Visual Studio.  
  
 Používat službě WCF definované v tomto článku [ukázka zabezpečení zpráv](../../../../docs/framework/wcf/samples/message-security-sample.md).  
  
### <a name="to-specify-a-client-certificate"></a>K zadání klientského certifikátu  
  
1. Spusťte soubor Setup.bat v adresáři zabezpečení zpráv a vytvořte a nainstalujte požadované testovací certifikáty.  
  
2. Otevřete projekt zabezpečení zpráv.  
  
3. Přidat `[ServiceBehavior(Namespace="http://Microsoft.ServiceModel.Samples")]` k `ICalculator` definici rozhraní.  
  
4. Přidat `bindingNamespace="http://Microsoft.ServiceModel.Samples"` ke značce koncového bodu v souboru App.config pro službu.  
  
5. Ukázka zabezpečení zpráv sestavíte a spustíte Service.exe. Pomocí aplikace Internet Explorer a přejděte na identifikátor URI služby (http://localhost:8000/ServiceModelSamples/Service) zajistit, služba funguje.  
  
6. Otevřete Visual Basic 6.0 a vytvořte nový soubor standardní .exe. Přidání tlačítka do formuláře a dvakrát klikněte na tlačítko Přidat následující kód do obslužné rutiny kliknutí:  
  
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
  
7. Spuštění aplikace Visual Basic a ověřte výsledky.  
  
     Aplikace Visual Basic zobrazí okno se zprávou s výsledkem volání přidat (3, 4). <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromFile%28System.String%2CSystem.String%2CSystem.String%29> nebo <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromStoreByName%28System.String%2CSystem.String%2CSystem.String%29> je také možné místo <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromStore%28System.String%2CSystem.String%2CSystem.String%2CSystem.Object%29> nastavit certifikát klienta:  
  
    ```  
    monikerProxy.ChannelCredentials.SetClientCertificateFromFile "C:\MyClientCert.pfx", "password", "DefaultKeySet"  
    ```  
  
> [!NOTE]
>  Pro toto volání pro práci musí být důvěryhodné. na počítači, na kterém běží klientem na klientský certifikát.  
  
> [!NOTE]
>  Pokud je moniker je poškozený nebo pokud služba není dostupná, volání `GetObject` vrátí chyba s oznámením "Neplatnou syntaxi." Pokud se zobrazí tato chyba, ujistěte se, že zástupný název, který používáte, je správná a služba není k dispozici.  
  
### <a name="to-specify-user-name-and-password"></a>K zadání uživatelského jména a hesla  
  
1. Upravte soubor App.config služba používat `wsHttpBinding`. To je potřeba pro ověřování uživatelského jména a hesla:  

2. Nastavte `clientCredentialType` na uživatelské jméno:  

3. Otevřete Visual Basic 6.0 a vytvořte nový soubor standardní .exe. Přidání tlačítka do formuláře a dvakrát klikněte na tlačítko Přidat následující kód do obslužné rutiny kliknutí:  
  
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
  
4. Spuštění aplikace Visual Basic a ověřte výsledky. Aplikace Visual Basic zobrazí okno se zprávou s výsledkem volání přidat (3, 4).  
  
    > [!NOTE]
    >  Vazby určené v monikeru služby v této ukázce se změnil na WSHttpBinding_ICalculator. Všimněte si také, že musíte zadat platné uživatelské jméno a heslo při volání funkce <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetUserNameCredential%28System.String%2CSystem.String%29>.  
  
### <a name="to-specify-windows-credentials"></a>K zadání přihlašovacích údajů Windows  
  
1. Nastavte `clientCredentialType` pro Windows v souboru App.config služby:  

2. Otevřete Visual Basic 6.0 a vytvořte nový soubor standardní .exe. Přidání tlačítka do formuláře a dvakrát klikněte na tlačítko Přidat následující kód do obslužné rutiny kliknutí:  
  
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
  
3. Spuštění aplikace Visual Basic a ověřte výsledky. Aplikace Visual Basic zobrazí okno se zprávou s výsledkem volání přidat (3, 4).  
  
    > [!NOTE]
    >  Platné hodnoty musí nahradit "domény", "userID" a "password".  
  
### <a name="to-specify-an-issue-token"></a>K určení tokenu problém  
  
1. Tokeny problém se používají pouze pro aplikace pomocí federovaného zabezpečení. Další informace o zabezpečení najdete v tématu [federace a vydané tokeny](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md) a [ukázka federace](../../../../docs/framework/wcf/samples/federation-sample.md).  
  
     Následující příklad kódu jazyka Visual Basic, ukazuje, jak volat <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetIssuedToken%28System.String%2CSystem.String%2CSystem.String%29> metody:  
  
    ```  
        monString = "service:mexAddress=http://localhost:8000/ServiceModelSamples/Service?wsdl"  
        monString = monString + ", address=http://localhost:8000/SomeService/Service"  
        monString = monString + ", contract=ICalculator, contractNamespace=http://SomeService.Samples"  
        monString = monString + ", binding=WSHttpBinding_ISomeContract, bindingNamespace=http://SomeService.Samples"  
  
        Set monikerProxy = GetObject(monString)  
    monikerProxy.SetIssuedToken("http://somemachine/sts", "bindingType", "binding")  
    ```  
  
     Další informace o parametrech pro tuto metodu, najdete v části <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetIssuedToken%28System.String%2CSystem.String%2CSystem.String%29>.  
  
## <a name="see-also"></a>Viz také:

- [Federace](../../../../docs/framework/wcf/feature-details/federation.md)
- [Postupy: Konfigurace pověření ve službě Federation Service](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [Postupy: Vytvoření federovaného klienta](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [Zabezpečení zpráv](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)
- [Vazby a zabezpečení](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)
