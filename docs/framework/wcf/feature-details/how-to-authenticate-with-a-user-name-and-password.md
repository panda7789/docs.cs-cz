---
title: 'Postupy: Ověřování pomocí uživatelského jména a hesla'
ms.date: 03/30/2017
helpviewer_keywords:
- authentication [WCF], user name and password
ms.assetid: a5415be2-0ef3-464c-9f76-c255cb8165a4
ms.openlocfilehash: e8dc9177afc590a6467855decfa8450b37c6fc77
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601280"
---
# <a name="how-to-authenticate-with-a-user-name-and-password"></a><span data-ttu-id="167cf-102">Postupy: Ověřování pomocí uživatelského jména a hesla</span><span class="sxs-lookup"><span data-stu-id="167cf-102">How to: Authenticate with a User Name and Password</span></span>

<span data-ttu-id="167cf-103">Toto téma ukazuje, jak povolit službu Windows Communication Foundation (WCF) k ověřování klienta s uživatelským jménem a heslem v doméně systému Windows.</span><span class="sxs-lookup"><span data-stu-id="167cf-103">This topic demonstrates how to enable a Windows Communication Foundation (WCF) service to authenticate a client with a Windows domain username and password.</span></span> <span data-ttu-id="167cf-104">Předpokládá, že máte funkční, samoobslužnou hostovanou službu WCF.</span><span class="sxs-lookup"><span data-stu-id="167cf-104">It assumes you have a working, self-hosted WCF service.</span></span> <span data-ttu-id="167cf-105">Příklad vytvoření základní samoobslužné služby WCF najdete v [kurzu Začínáme](../getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="167cf-105">For an example of creating a basic self-hosted WCF service see, [Getting Started Tutorial](../getting-started-tutorial.md).</span></span> <span data-ttu-id="167cf-106">Toto téma předpokládá, že je služba nakonfigurovaná v kódu.</span><span class="sxs-lookup"><span data-stu-id="167cf-106">This topic assumes the service is configured in code.</span></span> <span data-ttu-id="167cf-107">Pokud se chcete podívat na příklad konfigurace podobné služby pomocí konfiguračního souboru, přečtěte si téma [zabezpečení zpráv – uživatelské jméno](../samples/message-security-user-name.md).</span><span class="sxs-lookup"><span data-stu-id="167cf-107">If you would like to see an example of configuring a similar service using a configuration file, see [Message Security User Name](../samples/message-security-user-name.md).</span></span>

<span data-ttu-id="167cf-108">Pokud chcete nakonfigurovat službu pro ověřování svých klientů pomocí uživatelského jména a hesla domény Windows, použijte <xref:System.ServiceModel.WSHttpBinding> a nastavte jeho `Security.Mode` vlastnost na `Message` .</span><span class="sxs-lookup"><span data-stu-id="167cf-108">To configure a service to authenticate its clients using Windows Domain username and passwords use the <xref:System.ServiceModel.WSHttpBinding> and set its `Security.Mode` property to `Message`.</span></span> <span data-ttu-id="167cf-109">Kromě toho je nutné zadat certifikát x509, který bude použit k zašifrování uživatelského jména a hesla, protože jsou odesílány z klienta do služby.</span><span class="sxs-lookup"><span data-stu-id="167cf-109">In addition you must specify an X509 certificate that will be used to encrypt the username and password as they are sent from the client to the service.</span></span>

<span data-ttu-id="167cf-110">Na straně klienta musíte požádat uživatele o uživatelské jméno a heslo a zadat přihlašovací údaje uživatele na proxy serveru služby WCF.</span><span class="sxs-lookup"><span data-stu-id="167cf-110">On the client, you must prompt the user for the username and password and specify the user’s credentials on the WCF client proxy.</span></span>

## <a name="to-configure-a-wcf-service-to-authenticate-using-windows-domain-username-and-password"></a><span data-ttu-id="167cf-111">Konfigurace služby WCF pro ověřování pomocí uživatelského jména a hesla v doméně Windows</span><span class="sxs-lookup"><span data-stu-id="167cf-111">To configure a WCF service to authenticate using Windows domain username and password</span></span>

1. <span data-ttu-id="167cf-112">Vytvořte instanci <xref:System.ServiceModel.WSHttpBinding> , nastavte režim zabezpečení vazby na <xref:System.ServiceModel.WSHttpSecurity.Message?displayProperty=nameWithType> , nastavte `ClientCredentialType` vazbu na <xref:System.ServiceModel.MessageCredentialType.UserName?displayProperty=nameWithType> a přidejte koncový bod služby pomocí nakonfigurované vazby na hostitele služby, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="167cf-112">Create an instance of the <xref:System.ServiceModel.WSHttpBinding>, set the security mode of the binding to <xref:System.ServiceModel.WSHttpSecurity.Message?displayProperty=nameWithType>, set the `ClientCredentialType` of the binding to <xref:System.ServiceModel.MessageCredentialType.UserName?displayProperty=nameWithType>, and add a service endpoint using the configured binding to the service host as shown in the following code:</span></span>

    ```csharp
    // ...
    var userNameBinding = new WSHttpBinding();
    userNameBinding.Security.Mode = SecurityMode.Message;
    userNameBinding.Security.Message.ClientCredentialType = MessageCredentialType.UserName;
    svcHost.AddServiceEndpoint(typeof(IService1), userNameBinding, "");
    // ...
    ```

2. <span data-ttu-id="167cf-113">Zadejte certifikát serveru, který se používá k šifrování uživatelského jména a hesla odesílaných po drátě.</span><span class="sxs-lookup"><span data-stu-id="167cf-113">Specify the server certificate used to encrypt the username and password information sent over the wire.</span></span> <span data-ttu-id="167cf-114">Tento kód by měl hned následovat po výše uvedeném kódu.</span><span class="sxs-lookup"><span data-stu-id="167cf-114">This code should immediately follow the code above.</span></span> <span data-ttu-id="167cf-115">V následujícím příkladu je použit certifikát, který je vytvořen souborem Setup. bat z ukázkového [uživatelského jména zabezpečení zprávy](../samples/message-security-user-name.md) :</span><span class="sxs-lookup"><span data-stu-id="167cf-115">The following example uses the certificate that is created by the setup.bat file from the [Message Security User Name](../samples/message-security-user-name.md) sample:</span></span>

    ```csharp
    // ...
    svcHost.Credentials.ServiceCertificate.SetCertificate(StoreLocation.LocalMachine, StoreName.My, X509FindType.FindBySubjectName, "localhost");
    // ...
    ```

    <span data-ttu-id="167cf-116">Můžete použít svůj vlastní certifikát. stačí upravit kód, který bude odkazovat na váš certifikát.</span><span class="sxs-lookup"><span data-stu-id="167cf-116">You can use your own certificate, just modify the code to refer to your certificate.</span></span> <span data-ttu-id="167cf-117">Další informace o vytváření a používání certifikátů najdete v tématu [práce s certifikáty](working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="167cf-117">For more information about creating and using certificates see [Working with Certificates](working-with-certificates.md).</span></span> <span data-ttu-id="167cf-118">Ujistěte se, že je certifikát v úložišti certifikátů Důvěryhodné osoby pro místní počítač.</span><span class="sxs-lookup"><span data-stu-id="167cf-118">Make sure the certificate is in the Trusted People certificate store for the Local Machine.</span></span> <span data-ttu-id="167cf-119">Můžete to provést tak, že spustíte MMC. exe a vyberete **soubor**, **Přidat nebo odebrat modul snap-in...** položka nabídky.</span><span class="sxs-lookup"><span data-stu-id="167cf-119">You can do this by running mmc.exe and selecting the **File**, **Add/Remove Snap-in...** menu item.</span></span> <span data-ttu-id="167cf-120">V dialogovém okně **Přidat nebo odebrat moduly snap-in** vyberte **modul snap-in Certifikáty** a klikněte na **Přidat**.</span><span class="sxs-lookup"><span data-stu-id="167cf-120">In the **Add or Remove Snap-ins** dialog, select the **Certificates snap-in** and click **Add**.</span></span> <span data-ttu-id="167cf-121">V dialogovém okně modul snap-in certifikáty vyberte možnost **účet počítače**.</span><span class="sxs-lookup"><span data-stu-id="167cf-121">In the Certificates Snap-in dialog select **Computer account**.</span></span> <span data-ttu-id="167cf-122">Ve výchozím nastavení se certifikát vygenerovaný z ukázka zabezpečení jméno uživatele zprávy nachází ve složce osobní nebo certifikáty.</span><span class="sxs-lookup"><span data-stu-id="167cf-122">By default the certificate generated from the Message Security User name sample will be located in the Personal/Certificates folder.</span></span>  <span data-ttu-id="167cf-123">Bude uveden jako "localhost" pod sloupcem vystaveno pro v okně MMC.</span><span class="sxs-lookup"><span data-stu-id="167cf-123">It will be listed as "localhost" under the Issued to column in the MMC window.</span></span> <span data-ttu-id="167cf-124">Přetáhněte certifikát do složky **Důvěryhodné osoby** .</span><span class="sxs-lookup"><span data-stu-id="167cf-124">Drag and drop the certificate into the **Trusted People** folder.</span></span> <span data-ttu-id="167cf-125">To umožní, aby WCF při ověřování považovalo certifikát za důvěryhodný certifikát.</span><span class="sxs-lookup"><span data-stu-id="167cf-125">This will allow WCF to treat the certificate as a trusted certificate when performing authentication.</span></span>

## <a name="to-call-the-service-passing-username-and-password"></a><span data-ttu-id="167cf-126">Volání služby předávající uživatelské jméno a heslo</span><span class="sxs-lookup"><span data-stu-id="167cf-126">To call the service passing username and password</span></span>

1. <span data-ttu-id="167cf-127">Klientská aplikace musí vyzvat uživatele k zadání uživatelského jména a hesla.</span><span class="sxs-lookup"><span data-stu-id="167cf-127">The client application must prompt the user for their username and password.</span></span> <span data-ttu-id="167cf-128">Následující kód vyzve uživatele k zadání uživatelského jména a hesla:</span><span class="sxs-lookup"><span data-stu-id="167cf-128">The following code asks the user for username and password:</span></span>

    > [!WARNING]
    > <span data-ttu-id="167cf-129">Tento kód by se neměl používat v produkčním prostředí, protože se při zadávání hesla zobrazuje.</span><span class="sxs-lookup"><span data-stu-id="167cf-129">This code should not be used in production as the password is displayed while being entered.</span></span>

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

2. <span data-ttu-id="167cf-130">Vytvořte instanci proxy serveru klienta, který určuje přihlašovací údaje klienta, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="167cf-130">Create an instance of the client proxy specifying the client's credentials as shown in the following code:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="167cf-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="167cf-131">See also</span></span>

- <xref:System.ServiceModel.WSHttpBinding>
- <xref:System.ServiceModel.WSHttpSecurity>
- <xref:System.ServiceModel.SecurityMode>
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential.UserName%2A>
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential.Password%2A>
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>
- <xref:System.ServiceModel.WSHttpSecurity.Mode%2A>
- <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A>
- [<span data-ttu-id="167cf-132">Zabezpečení přenosu pomocí základního ověřování</span><span class="sxs-lookup"><span data-stu-id="167cf-132">Transport Security with Basic Authentication</span></span>](transport-security-with-basic-authentication.md)
- [<span data-ttu-id="167cf-133">Zabezpečení distribuované aplikace</span><span class="sxs-lookup"><span data-stu-id="167cf-133">Distributed Application Security</span></span>](distributed-application-security.md)
- [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md)
