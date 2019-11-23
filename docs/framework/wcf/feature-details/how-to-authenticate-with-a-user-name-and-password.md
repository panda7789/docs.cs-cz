---
title: 'Postupy: Ověřování pomocí uživatelského jména a hesla'
ms.date: 03/30/2017
helpviewer_keywords:
- authentication [WCF], user name and password
ms.assetid: a5415be2-0ef3-464c-9f76-c255cb8165a4
ms.openlocfilehash: 33205f9e12fcee53f2f29b63b836ea0cbc792025
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834738"
---
# <a name="how-to-authenticate-with-a-user-name-and-password"></a>Postupy: Ověřování pomocí uživatelského jména a hesla

Toto téma ukazuje, jak povolit službu Windows Communication Foundation (WCF) k ověřování klienta s uživatelským jménem a heslem v doméně systému Windows. Předpokládá, že máte funkční, samoobslužnou hostovanou službu WCF. Příklad vytvoření základní samoobslužné služby WCF najdete v [kurzu Začínáme](../../../../docs/framework/wcf/getting-started-tutorial.md). Toto téma předpokládá, že je služba nakonfigurovaná v kódu. Pokud se chcete podívat na příklad konfigurace podobné služby pomocí konfiguračního souboru, přečtěte si téma [zabezpečení zpráv – uživatelské jméno](../samples/message-security-user-name.md).

Pokud chcete nakonfigurovat službu pro ověřování svých klientů pomocí uživatelského jména a hesla domény Windows, použijte <xref:System.ServiceModel.WSHttpBinding> a nastavte jeho vlastnost `Security.Mode` na `Message`. Kromě toho je nutné zadat certifikát x509, který bude použit k zašifrování uživatelského jména a hesla, protože jsou odesílány z klienta do služby.

Na straně klienta musíte požádat uživatele o uživatelské jméno a heslo a zadat přihlašovací údaje uživatele na proxy serveru služby WCF.

## <a name="to-configure-a-wcf-service-to-authenticate-using-windows-domain-username-and-password"></a>Konfigurace služby WCF pro ověřování pomocí uživatelského jména a hesla v doméně Windows

1. Vytvořte instanci <xref:System.ServiceModel.WSHttpBinding>, nastavte režim zabezpečení vazby na <xref:System.ServiceModel.WSHttpSecurity.Message?displayProperty=nameWithType>, nastavte `ClientCredentialType` vazby na <xref:System.ServiceModel.MessageCredentialType.UserName?displayProperty=nameWithType>a přidejte koncový bod služby s použitím nakonfigurované vazby na hostitele služby, jak je znázorněno v následujícím kódu:

    ```csharp
    // ...
    var userNameBinding = new WSHttpBinding();
    userNameBinding.Security.Mode = SecurityMode.Message;
    userNameBinding.Security.Message.ClientCredentialType = MessageCredentialType.UserName;
    svcHost.AddServiceEndpoint(typeof(IService1), userNameBinding, "");
    // ...
    ```

2. Zadejte certifikát serveru, který se používá k šifrování uživatelského jména a hesla odesílaných po drátě. Tento kód by měl hned následovat po výše uvedeném kódu. V následujícím příkladu je použit certifikát, který je vytvořen souborem Setup. bat z ukázkového [uživatelského jména zabezpečení zprávy](../samples/message-security-user-name.md) :

    ```csharp
    // ...
    svcHost.Credentials.ServiceCertificate.SetCertificate(StoreLocation.LocalMachine, StoreName.My, X509FindType.FindBySubjectName, "localhost");
    // ...
    ```

    Můžete použít svůj vlastní certifikát. stačí upravit kód, který bude odkazovat na váš certifikát. Další informace o vytváření a používání certifikátů najdete v tématu [práce s certifikáty](../../../../docs/framework/wcf/feature-details/working-with-certificates.md). Ujistěte se, že je certifikát v úložišti certifikátů Důvěryhodné osoby pro místní počítač. Můžete to provést tak, že spustíte MMC. exe a vyberete **soubor**, **Přidat nebo odebrat modul snap-in...** položka nabídky. V dialogovém okně **Přidat nebo odebrat moduly snap-in** vyberte **modul snap-in Certifikáty** a klikněte na **Přidat**. V dialogovém okně modul snap-in certifikáty vyberte možnost **účet počítače**. Ve výchozím nastavení se certifikát vygenerovaný z ukázka zabezpečení jméno uživatele zprávy nachází ve složce osobní nebo certifikáty.  Bude uveden jako "localhost" pod sloupcem vystaveno pro v okně MMC. Přetáhněte certifikát do složky **Důvěryhodné osoby** . To umožní, aby WCF při ověřování považovalo certifikát za důvěryhodný certifikát.

## <a name="to-call-the-service-passing-username-and-password"></a>Volání služby předávající uživatelské jméno a heslo

1. Klientská aplikace musí vyzvat uživatele k zadání uživatelského jména a hesla. Následující kód vyzve uživatele k zadání uživatelského jména a hesla:

    > [!WARNING]
    > Tento kód by se neměl používat v produkčním prostředí, protože se při zadávání hesla zobrazuje.

    ```csharp
    public static void GetPassword(out string username, out string password)
    {
        Console.WriteLine("Provide a valid machine or domain account. [domain\\user]");
        Console.WriteLine("   Enter username:");
        username = Console.ReadLine();
        Console.WriteLine("   Enter password:");
        password = Console.ReadLine();
    }
    ```

2. Vytvořte instanci proxy serveru klienta, který určuje přihlašovací údaje klienta, jak je znázorněno v následujícím kódu:

    ```csharp
    string username;
    string password;

    // Instantiate the proxy.
    var proxy = new Service1Client();

    // Prompt the user for username & password.
    GetPassword(out username, out password);

    // Set the user's credentials on the proxy.
    proxy.ClientCredentials.UserName.UserName = username;
    proxy.ClientCredentials.UserName.Password = password;

    // Treat the test certificate as trusted.
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
- [Zabezpečení přenosu pomocí základního ověřování](transport-security-with-basic-authentication.md)
- [Zabezpečení distribuované aplikace](distributed-application-security.md)
- [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md)
