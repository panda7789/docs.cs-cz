---
title: 'Postupy: Ověřování pomocí uživatelského jména a hesla'
ms.date: 03/30/2017
helpviewer_keywords:
- authentication [WCF], user name and password
ms.assetid: a5415be2-0ef3-464c-9f76-c255cb8165a4
ms.openlocfilehash: 08703209fd465f87e9dbc5e81a6ed90a4056324c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59174132"
---
# <a name="how-to-authenticate-with-a-user-name-and-password"></a>Postupy: Ověřování pomocí uživatelského jména a hesla

Toto téma ukazuje, jak povolit službu Windows Communication Foundation (WCF) k ověření klienta s Windows doména uživatelské jméno a heslo. Předpokládá se, že máte funkční, služba WCF v místním prostředí. Příklad vytvoření základní v místním prostředí WCF service naleznete v tématu [kurz Začínáme](../../../../docs/framework/wcf/getting-started-tutorial.md). Toto téma předpokládá, že služba je nakonfigurována v kódu. Pokud chcete zobrazit příklad konfigurace podobné služby promocí konfiguračního souboru najdete v [zabezpečení zpráv s uživatelským jménem](../../../../docs/framework/wcf/samples/message-security-user-name.md)  
  
 Nakonfigurujte službu k ověření klientů z domény s Windows pomocí uživatelského jména a hesla <xref:System.ServiceModel.WSHttpBinding> a nastavte jeho `Security.Mode` vlastnost `Message`. Kromě toho je nutné zadat x X509 certifikát, který se použije k zašifrování uživatelské jméno a heslo jsou odeslaných z klienta do služby.  
  
 Na straně klienta musíte výzva k zadání uživatelského jména a hesla a zadat pověření uživatele v klientovi proxy WCF.  
  
## <a name="to-configure-a-wcf-service-to-authenticate-using-windows-domain-username-and-password"></a>Konfigurace ověřování pomocí Windows doména uživatelské jméno a heslo ve službě WCF
  
1.  Vytvoření instance <xref:System.ServiceModel.WSHttpBinding>, nastavení režimu zabezpečení vazby ke <xref:System.ServiceModel.WSHttpSecurity.Message?displayProperty=nameWithType>, nastavte `ClientCredentialType` vazby ke <xref:System.ServiceModel.MessageCredentialType.UserName?displayProperty=nameWithType>a přidat koncový bod služby pomocí nakonfigurovanou vazbu k hostiteli služby, jak je znázorněno v následujícím kódu:  
  
    ```  
    // ...  
    WSHttpBinding userNameBinding = new WSHttpBinding();  
    userNameBinding.Security.Mode = SecurityMode.Message;  
    userNameBinding.Security.Message.ClientCredentialType = MessageCredentialType.UserName;  
    svcHost.AddServiceEndpoint(typeof(IService1), userNameBinding, "");  
    // ...  
    ```  
  
2.  Zadejte certifikát serveru použitý k šifrování uživatelské jméno a heslo informace odesílané při přenosu. Tento kód by měl bezprostředně následuje po výše uvedeném kódu. Následující příklad používá certifikát, který je vytvořen soubor setup.bat z [zabezpečení zpráv s uživatelským jménem](../../../../docs/framework/wcf/samples/message-security-user-name.md) vzorku:  
  
    ```  
    // ...  
    svcHost.Credentials.ServiceCertificate.SetCertificate(StoreLocation.LocalMachine, StoreName.My, X509FindType.FindBySubjectName, "localhost");  
    // ...  
    ```  
  
     Můžete použít svůj vlastní certifikát, upravit kód pro odkazování na váš certifikát. Další informace o vytváření a používání certifikátů najdete v části [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md). Ujistěte se, že je certifikát v úložišti certifikátů důvěryhodné osoby pro místní počítač. Můžete to provést spuštěním mmc.exe a výběr **souboru**, **Přidat/odebrat modul Snap-in...**  položky nabídky. V **přidat nebo odebrat moduly Snap in** dialogového okna, vyberte **modul snap-in Certifikáty** a klikněte na tlačítko **přidat**. V dialogovém okně modulu Snap-in Certifikáty vyberte **účet počítače**. Ve výchozím nastavení se nacházet ve složce osobní/certifikáty certifikátem vygenerovaným z Ukázkový název zprávy zabezpečení uživatele.  Zobrazí se jako "localhost" v části vystaveno pro sloupce v okně konzoly MMC. Přetáhnout myší certifikát do **důvěryhodné osoby** složky. To vám umožní WCF přistupovat ke všem certifikát jako certifikát důvěryhodný při provádění ověřování.  
  
## <a name="to-call-the-service-passing-username-and-password"></a>K volání služby předávání uživatelské jméno a heslo  
  
1.  Klientská aplikace musí požádat uživatele o uživatelského jména a hesla. Následující kód uživatele vyzve k zadání uživatelského jména a hesla.  
  
    > [!WARNING]
    >  Tento kód by neměl použít v produkčním prostředí, protože heslo se zobrazí při zadávání.  
  
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
  
2.  Vytvořte instanci proxy serveru klienta zadávání přihlašovacích údajů klienta, jak je znázorněno v následujícím kódu:  
  
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.WSHttpBinding>
- <xref:System.ServiceModel.WSHttpSecurity>
- <xref:System.ServiceModel.SecurityMode>
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential.UserName%2A>
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential.Password%2A>
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>
- <xref:System.ServiceModel.WSHttpSecurity.Mode%2A>
- <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A>
- [Zabezpečení přenosu se základním ověřováním](../../../../docs/framework/wcf/feature-details/transport-security-with-basic-authentication.md)
- [Zabezpečení distribuované aplikace](../../../../docs/framework/wcf/feature-details/distributed-application-security.md)
- [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)
