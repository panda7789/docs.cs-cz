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
ms.openlocfilehash: 2a1b2ba0ab49ebf470c0245f0827f82e1fe20ce8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-specify-channel-security-credentials"></a>Postupy: Zadejte pověření zabezpečení kanálu
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Monikeru služby umožňuje aplikacím COM volání [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby. Většina [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby vyžadují klienta a zadejte pověření pro ověřování a autorizaci. Při volání metody [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta, můžete zadat tyto přihlašovací údaje ve spravovaném kódu nebo v konfiguračním souboru aplikace. Při volání metody [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby z aplikace modelu COM, můžete použít <xref:System.ServiceModel.ComIntegration.IChannelCredentials> rozhraní k zadání přihlašovacích údajů. Toto téma se ilustrují různé způsoby, jak zadat přihlašovací údaje pomocí <xref:System.ServiceModel.ComIntegration.IChannelCredentials> rozhraní.  
  
> [!NOTE]
>  <xref:System.ServiceModel.ComIntegration.IChannelCredentials>je rozhraní, na základě IDispatch a nebude používat funkci IntelliSense v prostředí Visual Studio.  
  
 Tento článek se použije [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby definované v [ukázka zabezpečení zpráv](../../../../docs/framework/wcf/samples/message-security-sample.md).  
  
### <a name="to-specify-a-client-certificate"></a>Chcete zadat klientský certifikát  
  
1.  Spusťte soubor Setup.bat v zabezpečení zpráv adresář, který chcete vytvořit a nainstalovat požadované testovací certifikáty.  
  
2.  Otevřete projekt zabezpečení zpráv.  
  
3.  Přidat `[ServiceBehavior(Namespace=``http://Microsoft.ServiceModel.Samples``)]` k `ICalculator` definici rozhraní.  
  
4.  Přidat `bindingNamespace=``http://Microsoft.ServiceModel.Samples` ke značce koncový bod v souboru App.config pro službu.  
  
5.  Ukázka zabezpečení zpráv sestavit a spustit Service.exe. Použijte Internet Explorer a přejděte do služby URI (http://localhost: 8000/ServiceModelSamples/Service) k zajištění, že služba funguje.  
  
6.  Otevřete Visual Basic 6.0 a vytvořte nový soubor standardní .exe. Přidání tlačítka do formuláře a dvakrát klikněte na tlačítko pro přidání do obslužná rutina kliknutí na následující kód:  
  
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
  
7.  Spuštění aplikace Visual Basic a ověřte výsledky.  
  
     Visual Basic aplikace se zobrazí okno se zprávou o výsledky volání metody přidat (3, 4). <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromFile%28System.String%2CSystem.String%2CSystem.String%29>nebo <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromStoreByName%28System.String%2CSystem.String%2CSystem.String%29> lze také použít místě <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromStore%28System.String%2CSystem.String%2CSystem.String%2CSystem.Object%29> nastavit certifikát klienta:  
  
    ```  
    monikerProxy.ChannelCredentials.SetClientCertificateFromFile "C:\MyClientCert.pfx", "password", "DefaultKeySet"  
    ```  
  
> [!NOTE]
>  Pro toto volání pracovat klientský certifikát musí být v počítači, na kterém běží klient na považován za důvěryhodný.  
  
> [!NOTE]
>  Pokud Přezdívka je poškozený nebo pokud služba není dostupná, volání `GetObject` se vrátí chyba s oznámením "Neplatnou syntaxi." Pokud se zobrazí tato chyba, ujistěte se, kterou používáte Přezdívka je správný a služba není k dispozici.  
  
### <a name="to-specify-user-name-and-password"></a>Chcete-li určit uživatelské jméno a heslo  
  
1.  Upravte soubor Service App.config a používat `wsHttpBinding`. Toto je vyžadován pro ověření uživatelské jméno a heslo:  
  
  
  
2.  Nastavte `clientCredentialType` uživatelské jméno:  
  
  
  
3.  Otevřete Visual Basic 6.0 a vytvořte nový soubor standardní .exe. Přidání tlačítka do formuláře a dvakrát klikněte na tlačítko pro přidání do obslužná rutina kliknutí na následující kód:  
  
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
  
4.  Spuštění aplikace Visual Basic a ověřte výsledky. Visual Basic aplikace se zobrazí okno se zprávou o výsledky volání metody přidat (3, 4).  
  
    > [!NOTE]
    >  Vazba, zadaný v monikeru služby v této ukázce se změnil na WSHttpBinding_ICalculator. Všimněte si, že musíte zadat platné uživatelské jméno a heslo ve volání <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetUserNameCredential%28System.String%2CSystem.String%29>.  
  
### <a name="to-specify-windows-credentials"></a>K zadání pověření systému Windows  
  
1.  Nastavit `clientCredentialType` do systému Windows v souboru App.config služby:  
  
  
  
2.  Otevřete Visual Basic 6.0 a vytvořte nový soubor standardní .exe. Přidání tlačítka do formuláře a dvakrát klikněte na tlačítko pro přidání do obslužná rutina kliknutí na následující kód:  
  
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
  
3.  Spuštění aplikace Visual Basic a ověřte výsledky. Visual Basic aplikace se zobrazí okno se zprávou o výsledky volání metody přidat (3, 4).  
  
    > [!NOTE]
    >  Je potřeba nahradit "domény", "userID" a "password" platné hodnoty.  
  
### <a name="to-specify-an-issue-token"></a>K určení tokenu problém  
  
1.  Tokeny problém se používají pouze pro aplikace, které používají federované zabezpečení. Další informace o federované zabezpečení najdete v tématu [federace a vystavené tokeny](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md) a [ukázka federace](../../../../docs/framework/wcf/samples/federation-sample.md).  
  
     Následující příklad kódu jazyka Visual Basic ukazuje, jak volat <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetIssuedToken%28System.String%2CSystem.String%2CSystem.String%29> metoda:  
  
    ```  
        monString = "service:mexAddress=http://localhost:8000/ServiceModelSamples/Service?wsdl"  
        monString = monString + ", address=http://localhost:8000/SomeService/Service"  
        monString = monString + ", contract=ICalculator, contractNamespace=http://SomeService.Samples"  
        monString = monString + ", binding=WSHttpBinding_ISomeContract, bindingNamespace=http://SomeService.Samples"  
  
        Set monikerProxy = GetObject(monString)  
    monikerProxy.SetIssuedToken("http://somemachine/sts", "bindingType", "binding")  
    ```  
  
     Další informace o parametrech pro tuto metodu, najdete v části <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetIssuedToken%28System.String%2CSystem.String%2CSystem.String%29>.  
  
## <a name="see-also"></a>Viz také  
 [Federace](../../../../docs/framework/wcf/feature-details/federation.md)  
 [Postupy: Konfigurace pověření ve službě Federation](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)  
 [Postupy: vytvoření federovaného klienta](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [Zabezpečení zpráv](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)  
 [Vazby a zabezpečení](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)
