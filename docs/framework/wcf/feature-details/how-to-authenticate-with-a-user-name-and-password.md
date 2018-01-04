---
title: "Postupy: Ověřování pomocí uživatelského jména a hesla"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: authentication [WCF], user name and password
ms.assetid: a5415be2-0ef3-464c-9f76-c255cb8165a4
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1554e8594a611aa75876d14ee7ad0689932372e8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-authenticate-with-a-user-name-and-password"></a>Postupy: Ověřování pomocí uživatelského jména a hesla
Toto téma ukazuje, jak povolit [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] služby k ověření klienta s uživatelské jméno domény systému Windows a heslo. Předpokládá se, že máte funkční, služba WCF s vlastním hostováním. Pro příklad vytvoření základní vlastním hostováním WCF služby naleznete v tématu [kurzu Začínáme](../../../../docs/framework/wcf/getting-started-tutorial.md). Toto téma předpokládá, že služba je nakonfigurována v kódu. Pokud byste chtěli vidět najdete příklad konfigurace podobně jako služby pomocí konfiguračního souboru [zpráva zabezpečení uživatelské jméno](../../../../docs/framework/wcf/samples/message-security-user-name.md)  
  
 Pro konfiguraci služby k ověření jeho klienty z uživatelského jména a hesla pomocí domény systému Windows <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> a nastavte její `Security.Mode` vlastnost `Message`. Kromě toho je nutné zadat X509 certifikát, který se použije k zašifrování uživatelské jméno a heslo odeslaných z klienta ke službě.  
  
 Na klientovi musíte požádat uživatele o uživatelské jméno a heslo a zadejte pověření uživatele na proxy serveru klienta WCF.  
  
### <a name="to-configure-a-wcf-service-to-authenticate-using-windows-domain-username-and-password"></a>Konfigurace služby WCF, který chcete ověřit pomocí domény systému Windows uživatelské jméno a heslo.  
  
1.  Vytvoření instance <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`>, nastavení režimu zabezpečení vazby ke `SecurityMode.Message`, nastavte `ClientCredentialType` vazby ke `MessageCredentialType.UserName`a přidat koncový bod služby pomocí vazby nakonfigurované hostitele služby, jak je znázorněno v následujícím kódu:  
  
    ```  
    // ...  
    WSHttpBinding userNameBinding = new WSHttpBinding();  
    userNameBinding.Security.Mode = SecurityMode.Message;  
    userNameBinding.Security.Message.ClientCredentialType = MessageCredentialType.UserName;  
    svcHost.AddServiceEndpoint(typeof(IService1), userNameBinding, "");  
    // ...  
    ```  
  
2.  Zadejte server certifikát použitý k šifrování uživatelské jméno a heslo informace odeslány prostřednictvím sítě. Tento kód by mělo vycházet okamžitě výše uvedený kód. Následující příklad používá certifikát, který se vytvoří soubor setup.bat z [zpráva zabezpečení uživatelské jméno](../../../../docs/framework/wcf/samples/message-security-user-name.md) ukázka:  
  
    ```  
    // ...  
    svcHost.Credentials.ServiceCertificate.SetCertificate(StoreLocation.LocalMachine, StoreName.My, X509FindType.FindBySubjectName, "localhost");  
    // ...  
    ```  
  
     Můžete použít vlastní certifikát, stačí upravit kód, který bude odkazovat na certifikát. Další informace o vytváření a používání certifikátů najdete v části [práce s certifikáty](../../../../docs/framework/wcf/feature-details/working-with-certificates.md). Ověřte, zda je certifikát v úložišti certifikátů důvěryhodné osoby pro místní počítač. To provedete spuštěním mmc.exe a výběr **soubor**, **přidat nebo odebrat modul Snap-in...**  položku nabídky. V **přidat nebo odebrat moduly Snap in** dialogovém okně, vyberte **modul snap-in Certifikáty** a klikněte na tlačítko **přidat**. V dialogovém okně modulu Snap-in Certifikáty vyberte **účet počítače**. Ve výchozím nastavení se nacházet ve složce osobní certifikáty certifikát vygenerovaný z název ukázku zprávu zabezpečení uživatele.  Objeví se jako "localhost" v části vystaveno pro sloupce v okně konzoly MMC. Přetáhnout myší certifikát do **důvěryhodné osoby** složky. To vám umožní WCF na certifikát považovat certifikát důvěryhodný při ověřování.  
  
### <a name="to-call-the-service-passing-username-and-password"></a>Pro volání služby předávání uživatelské jméno a heslo  
  
1.  Klientská aplikace musí požádat uživatele o uživatelského jména a hesla. Následující kód požádá uživatele o uživatelské jméno a heslo.  
  
    > [!WARNING]
    >  Tento kód nesmí použít v produkčním prostředí, jako při zadávání se zobrazí heslo.  
  
    ```  
    public static void GetPassword(out string username, out string password)  
            {  
                Console.WriteLine("Provide a valid machine or domain account. [domain\\user]");  
                Console.WriteLine("   Enter username:");  
                username = Console.ReadLine();  
                Console.WriteLine("   Enter password:");  
                password = Console.ReadLine();             
                return;  
            }  
    ```  
  
2.  Vytvoření instance proxy serveru klienta zadání pověření klienta, jak je znázorněno v následujícím kódu:  
  
    ```  
    string username;  
    string password;  
  
    // Instantiate the proxy  
    Service1Client proxy = new Service1Client();  
  
    // Prompt the user for username & password  
    GetPassword(out username, out password);  
  
    // Set the user’s credentials on the proxy  
    proxy.ClientCredentials.UserName.UserName = username;  
    proxy.ClientCredentials.UserName.Password = password;  
  
    // Treat the test certificate as trusted  
    proxy.ClientCredentials.ServiceCertificate.Authentication.CertificateValidationMode = System.ServiceModel.Security.X509CertificateValidationMode.PeerOrChainTrust;  
    // Call the service operation using the proxy  
    ```  
  
## <a name="see-also"></a>Viz také  
 <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`>  
 <xref:System.ServiceModel.WSHttpSecurity>  
 <xref:System.ServiceModel.SecurityMode>  
 <xref:System.ServiceModel.Security.UserNamePasswordClientCredential.UserName%2A>  
 <xref:System.ServiceModel.Security.UserNamePasswordClientCredential.Password%2A>  
 <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>  
 <xref:System.ServiceModel.WSHttpSecurity.Mode%2A>  
 <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A>  
 [Zabezpečení přenosu pomocí základního ověřování](../../../../docs/framework/wcf/feature-details/transport-security-with-basic-authentication.md)  
 [Zabezpečení distribuované aplikace](../../../../docs/framework/wcf/feature-details/distributed-application-security.md)  
 [\<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)
