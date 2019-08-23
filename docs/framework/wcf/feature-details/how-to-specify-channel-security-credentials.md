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
# <a name="how-to-specify-channel-security-credentials"></a>Postupy: Určení zabezpečovacích pověření kanálu
Moniker služby Windows Communication Foundation (WCF) umožňuje aplikacím COM volat služby WCF. Většina služeb WCF vyžaduje, aby klient určil přihlašovací údaje pro ověřování a autorizaci. Při volání služby WCF z klienta WCF můžete zadat tyto přihlašovací údaje ve spravovaném kódu nebo v konfiguračním souboru aplikace. Při volání služby WCF z aplikace COM můžete použít <xref:System.ServiceModel.ComIntegration.IChannelCredentials> rozhraní k zadání přihlašovacích údajů. Toto téma popisuje různé způsoby, jak zadat pověření pomocí <xref:System.ServiceModel.ComIntegration.IChannelCredentials> rozhraní.  
  
> [!NOTE]
> <xref:System.ServiceModel.ComIntegration.IChannelCredentials>je rozhraní založené na rozhraní IDispatch a nebude možné získat funkce technologie IntelliSense v prostředí sady Visual Studio.  
  
 Tento článek bude používat službu WCF definovanou v [ukázce zabezpečení zpráv](../../../../docs/framework/wcf/samples/message-security-sample.md).  
  
### <a name="to-specify-a-client-certificate"></a>Určení klientského certifikátu  
  
1. Spusťte soubor Setup. bat v adresáři zabezpečení zprávy pro vytvoření a instalaci požadovaných testovacích certifikátů.  
  
2. Otevřete projekt zabezpečení zprávy.  
  
3. `[ServiceBehavior(Namespace="http://Microsoft.ServiceModel.Samples")]` Přidejte`ICalculator` do definice rozhraní.  
  
4. Přidá `bindingNamespace="http://Microsoft.ServiceModel.Samples"` se do značky Endpoint v App. config pro službu.  
  
5. Sestavte ukázku zabezpečení zpráv a spusťte Service. exe. Použijte Internet Explorer a přejděte k identifikátoru URI služby (http://localhost:8000/ServiceModelSamples/Service) abyste zajistili, že služba funguje.  
  
6. Otevřete Visual Basic 6,0 a vytvořte nový standardní soubor. exe. Přidejte do formuláře tlačítko a dvakrát klikněte na tlačítko a přidejte následující kód do obslužné rutiny Click:  
  
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
  
7. Spusťte aplikaci Visual Basic a ověřte výsledky.  
  
     V aplikaci Visual Basic se zobrazí okno se zprávou s výsledkem volání metody Add (3, 4). <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromFile%28System.String%2CSystem.String%2CSystem.String%29>Můžete také použít <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromStore%28System.String%2CSystem.String%2CSystem.String%2CSystem.Object%29> místo pro nastavení klientského certifikátu: <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromStoreByName%28System.String%2CSystem.String%2CSystem.String%29>  
  
    ```  
    monikerProxy.ChannelCredentials.SetClientCertificateFromFile "C:\MyClientCert.pfx", "password", "DefaultKeySet"  
    ```  
  
> [!NOTE]
> Aby toto volání fungovalo, musí být klientský certifikát důvěryhodný na počítači, na kterém je spuštěný klient nástroje.  
  
> [!NOTE]
> Pokud je moniker poškozený nebo pokud není služba k dispozici, volání vrátí chybu `GetObject` s názvem neplatná syntaxe. Pokud se zobrazí tato chyba, ujistěte se, že moniker, který používáte, je správný a služba je k dispozici.  
  
### <a name="to-specify-user-name-and-password"></a>Zadání uživatelského jména a hesla  
  
1. Upravte soubor App. config aplikace služby tak, aby `wsHttpBinding`používal. Tato akce je nutná pro ověření uživatelského jména a hesla:  

2. `clientCredentialType` Nastavte na uživatelské jméno:  

3. Otevřete Visual Basic 6,0 a vytvořte nový standardní soubor. exe. Přidejte do formuláře tlačítko a dvakrát klikněte na tlačítko a přidejte následující kód do obslužné rutiny Click:  
  
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
  
4. Spusťte aplikaci Visual Basic a ověřte výsledky. V aplikaci Visual Basic se zobrazí okno se zprávou s výsledkem volání metody Add (3, 4).  
  
    > [!NOTE]
    > Vazba zadaná v monikeru služby v této ukázce se změnila na WSHttpBinding_ICalculator. Všimněte si také, že při volání <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetUserNameCredential%28System.String%2CSystem.String%29>je nutné uvést platné uživatelské jméno a heslo.  
  
### <a name="to-specify-windows-credentials"></a>Zadání přihlašovacích údajů systému Windows  
  
1. Nastavte `clientCredentialType` na Windows v souboru App. config aplikace služby:  

2. Otevřete Visual Basic 6,0 a vytvořte nový standardní soubor. exe. Přidejte do formuláře tlačítko a dvakrát klikněte na tlačítko a přidejte následující kód do obslužné rutiny Click:  
  
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
  
3. Spusťte aplikaci Visual Basic a ověřte výsledky. V aplikaci Visual Basic se zobrazí okno se zprávou s výsledkem volání metody Add (3, 4).  
  
    > [!NOTE]
    > Platné hodnoty musí nahradit "doména", "userID" a "heslo".  
  
### <a name="to-specify-an-issue-token"></a>Určení tokenu problému  
  
1. Tokeny vydávání se používají jenom pro aplikace, které používají federované zabezpečení. Další informace o federovaném zabezpečení najdete v tématu [federace a vystavené tokeny](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md) a [Ukázka federace](../../../../docs/framework/wcf/samples/federation-sample.md).  
  
     Následující příklad kódu Visual Basic ukazuje, jak zavolat <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetIssuedToken%28System.String%2CSystem.String%2CSystem.String%29> metodu:  
  
    ```  
        monString = "service:mexAddress=http://localhost:8000/ServiceModelSamples/Service?wsdl"  
        monString = monString + ", address=http://localhost:8000/SomeService/Service"  
        monString = monString + ", contract=ICalculator, contractNamespace=http://SomeService.Samples"  
        monString = monString + ", binding=WSHttpBinding_ISomeContract, bindingNamespace=http://SomeService.Samples"  
  
        Set monikerProxy = GetObject(monString)  
    monikerProxy.SetIssuedToken("http://somemachine/sts", "bindingType", "binding")  
    ```  
  
     Další informace o parametrech této metody naleznete v tématu <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetIssuedToken%28System.String%2CSystem.String%2CSystem.String%29>.  
  
## <a name="see-also"></a>Viz také:

- [Federace](../../../../docs/framework/wcf/feature-details/federation.md)
- [Postupy: Konfigurace přihlašovacích údajů na služba FS (Federation Service)](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [Postupy: Vytvoření federovaného klienta](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [Zabezpečení zpráv](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)
- [Vazby a zabezpečení](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)
