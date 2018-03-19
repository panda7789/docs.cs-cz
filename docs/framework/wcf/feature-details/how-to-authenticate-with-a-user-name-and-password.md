---
title: "Postupy: Ověřování pomocí uživatelského jména a hesla"
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: article
helpviewer_keywords:
- authentication [WCF], user name and password
ms.assetid: a5415be2-0ef3-464c-9f76-c255cb8165a4
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 194a84ef7c2af3bfce6af3625eabf07d4d0b06fb
ms.sourcegitcommit: 15316053918995cc1380163a7d7e7edd5c44e6d7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/19/2018
---
# <a name="how-to-authenticate-with-a-user-name-and-password"></a><span data-ttu-id="8e72d-102">Postupy: Ověřování pomocí uživatelského jména a hesla</span><span class="sxs-lookup"><span data-stu-id="8e72d-102">How to: Authenticate with a User Name and Password</span></span>

<span data-ttu-id="8e72d-103">Toto téma ukazuje, jak povolit [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] služby k ověření klienta s uživatelské jméno domény systému Windows a heslo.</span><span class="sxs-lookup"><span data-stu-id="8e72d-103">This topic demonstrates how to enable a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service to authenticate a client with a Windows domain username and password.</span></span> <span data-ttu-id="8e72d-104">Předpokládá se, že máte funkční, služba WCF s vlastním hostováním.</span><span class="sxs-lookup"><span data-stu-id="8e72d-104">It assumes you have a working, self-hosted WCF service.</span></span> <span data-ttu-id="8e72d-105">Pro příklad vytvoření základní vlastním hostováním WCF služby naleznete v tématu [kurzu Začínáme](../../../../docs/framework/wcf/getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="8e72d-105">For an example of creating a basic self-hosted WCF service see, [Getting Started Tutorial](../../../../docs/framework/wcf/getting-started-tutorial.md).</span></span> <span data-ttu-id="8e72d-106">Toto téma předpokládá, že služba je nakonfigurována v kódu.</span><span class="sxs-lookup"><span data-stu-id="8e72d-106">This topic assumes the service is configured in code.</span></span> <span data-ttu-id="8e72d-107">Pokud byste chtěli vidět najdete příklad konfigurace podobně jako služby pomocí konfiguračního souboru [zpráva zabezpečení uživatelské jméno](../../../../docs/framework/wcf/samples/message-security-user-name.md)</span><span class="sxs-lookup"><span data-stu-id="8e72d-107">If you would like to see an example of configuring a similar service using a configuration file see [Message Security User Name](../../../../docs/framework/wcf/samples/message-security-user-name.md)</span></span>  
  
 <span data-ttu-id="8e72d-108">Pro konfiguraci služby k ověření jeho klienty z uživatelského jména a hesla pomocí domény systému Windows <xref:System.ServiceModel.WSHttpBinding> a nastavit jeho `Security.Mode` vlastnost `Message`.</span><span class="sxs-lookup"><span data-stu-id="8e72d-108">To configure a service to authenticate its clients using Windows Domain username and passwords use the <xref:System.ServiceModel.WSHttpBinding> and set its `Security.Mode` property to `Message`.</span></span> <span data-ttu-id="8e72d-109">Kromě toho je nutné zadat X509 certifikát, který se použije k zašifrování uživatelské jméno a heslo odeslaných z klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="8e72d-109">In addition you must specify an X509 certificate that will be used to encrypt the username and password as they are sent from the client to the service.</span></span>  
  
 <span data-ttu-id="8e72d-110">Na klientovi musíte požádat uživatele o uživatelské jméno a heslo a zadejte pověření uživatele na proxy serveru klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="8e72d-110">On the client, you must prompt the user for the username and password and specify the user’s credentials on the WCF client proxy.</span></span>  
  
## <a name="to-configure-a-wcf-service-to-authenticate-using-windows-domain-username-and-password"></a><span data-ttu-id="8e72d-111">Konfigurace ověřování pomocí domény systému Windows uživatelské jméno a heslo ve službě WCF</span><span class="sxs-lookup"><span data-stu-id="8e72d-111">To configure a WCF service to authenticate using Windows domain username and password</span></span>
  
1.  <span data-ttu-id="8e72d-112">Vytvoření instance <xref:System.ServiceModel.WSHttpBinding>, nastavení režimu zabezpečení vazby ke `SecurityMode.Message`, nastavte `ClientCredentialType` vazby ke `MessageCredentialType.UserName`a přidat koncový bod služby pomocí vazby nakonfigurované hostitele služby, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="8e72d-112">Create an instance of the <xref:System.ServiceModel.WSHttpBinding>, set the security mode of the binding to `SecurityMode.Message`, set the `ClientCredentialType` of the binding to `MessageCredentialType.UserName`, and add a service endpoint using the configured binding to the service host as shown in the following code:</span></span>  
  
    ```  
    // ...  
    WSHttpBinding userNameBinding = new WSHttpBinding();  
    userNameBinding.Security.Mode = SecurityMode.Message;  
    userNameBinding.Security.Message.ClientCredentialType = MessageCredentialType.UserName;  
    svcHost.AddServiceEndpoint(typeof(IService1), userNameBinding, "");  
    // ...  
    ```  
  
2.  <span data-ttu-id="8e72d-113">Zadejte server certifikát použitý k šifrování uživatelské jméno a heslo informace odeslány prostřednictvím sítě.</span><span class="sxs-lookup"><span data-stu-id="8e72d-113">Specify the server certificate used to encrypt the username and password information sent over the wire.</span></span> <span data-ttu-id="8e72d-114">Tento kód by mělo vycházet okamžitě výše uvedený kód.</span><span class="sxs-lookup"><span data-stu-id="8e72d-114">This code should immediately follow the code above.</span></span> <span data-ttu-id="8e72d-115">Následující příklad používá certifikát, který se vytvoří soubor setup.bat z [zpráva zabezpečení uživatelské jméno](../../../../docs/framework/wcf/samples/message-security-user-name.md) ukázka:</span><span class="sxs-lookup"><span data-stu-id="8e72d-115">The following example uses the certificate that is created by the setup.bat file from the [Message Security User Name](../../../../docs/framework/wcf/samples/message-security-user-name.md) sample:</span></span>  
  
    ```  
    // ...  
    svcHost.Credentials.ServiceCertificate.SetCertificate(StoreLocation.LocalMachine, StoreName.My, X509FindType.FindBySubjectName, "localhost");  
    // ...  
    ```  
  
     <span data-ttu-id="8e72d-116">Můžete použít vlastní certifikát, stačí upravit kód, který bude odkazovat na certifikát.</span><span class="sxs-lookup"><span data-stu-id="8e72d-116">You can use your own certificate, just modify the code to refer to your certificate.</span></span> <span data-ttu-id="8e72d-117">Další informace o vytváření a používání certifikátů najdete v části [práce s certifikáty](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="8e72d-117">For more information about creating and using certificates see [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span> <span data-ttu-id="8e72d-118">Ověřte, zda je certifikát v úložišti certifikátů důvěryhodné osoby pro místní počítač.</span><span class="sxs-lookup"><span data-stu-id="8e72d-118">Make sure the certificate is in the Trusted People certificate store for the Local Machine.</span></span> <span data-ttu-id="8e72d-119">To provedete spuštěním mmc.exe a výběr **soubor**, **přidat nebo odebrat modul Snap-in...**  položku nabídky.</span><span class="sxs-lookup"><span data-stu-id="8e72d-119">You can do this by running mmc.exe and selecting the **File**, **Add/Remove Snap-in...** menu item.</span></span> <span data-ttu-id="8e72d-120">V **přidat nebo odebrat moduly Snap in** dialogovém okně, vyberte **modul snap-in Certifikáty** a klikněte na tlačítko **přidat**.</span><span class="sxs-lookup"><span data-stu-id="8e72d-120">In the **Add or Remove Snap-ins** dialog, select the **Certificates snap-in** and click **Add**.</span></span> <span data-ttu-id="8e72d-121">V dialogovém okně modulu Snap-in Certifikáty vyberte **účet počítače**.</span><span class="sxs-lookup"><span data-stu-id="8e72d-121">In the Certificates Snap-in dialog select **Computer account**.</span></span> <span data-ttu-id="8e72d-122">Ve výchozím nastavení se nacházet ve složce osobní certifikáty certifikát vygenerovaný z název ukázku zprávu zabezpečení uživatele.</span><span class="sxs-lookup"><span data-stu-id="8e72d-122">By default the certificate generated from the Message Security User name sample will be located in the Personal/Certificates folder.</span></span>  <span data-ttu-id="8e72d-123">Objeví se jako "localhost" v části vystaveno pro sloupce v okně konzoly MMC.</span><span class="sxs-lookup"><span data-stu-id="8e72d-123">It will be listed as "localhost" under the Issued to column in the MMC window.</span></span> <span data-ttu-id="8e72d-124">Přetáhnout myší certifikát do **důvěryhodné osoby** složky.</span><span class="sxs-lookup"><span data-stu-id="8e72d-124">Drag and drop the certificate into the **Trusted People** folder.</span></span> <span data-ttu-id="8e72d-125">To vám umožní WCF na certifikát považovat certifikát důvěryhodný při ověřování.</span><span class="sxs-lookup"><span data-stu-id="8e72d-125">This will allow WCF to treat the certificate as a trusted certificate when performing authentication.</span></span>  
  
## <a name="to-call-the-service-passing-username-and-password"></a><span data-ttu-id="8e72d-126">Pro volání služby předávání uživatelské jméno a heslo</span><span class="sxs-lookup"><span data-stu-id="8e72d-126">To call the service passing username and password</span></span>  
  
1.  <span data-ttu-id="8e72d-127">Klientská aplikace musí požádat uživatele o uživatelského jména a hesla.</span><span class="sxs-lookup"><span data-stu-id="8e72d-127">The client application must prompt the user for their username and password.</span></span> <span data-ttu-id="8e72d-128">Následující kód požádá uživatele o uživatelské jméno a heslo.</span><span class="sxs-lookup"><span data-stu-id="8e72d-128">The following code asks the user for username and password.</span></span>  
  
    > [!WARNING]
    >  <span data-ttu-id="8e72d-129">Tento kód nesmí použít v produkčním prostředí, jako při zadávání se zobrazí heslo.</span><span class="sxs-lookup"><span data-stu-id="8e72d-129">This code should not be used in production as the password is displayed while being entered.</span></span>  
  
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
  
2.  <span data-ttu-id="8e72d-130">Vytvoření instance proxy serveru klienta zadání pověření klienta, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="8e72d-130">Create an instance of the client proxy specifying the client’s credentials as shown in the following code:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8e72d-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="8e72d-131">See Also</span></span>  
 <xref:System.ServiceModel.WSHttpBinding>  
 <xref:System.ServiceModel.WSHttpSecurity>  
 <xref:System.ServiceModel.SecurityMode>  
 <xref:System.ServiceModel.Security.UserNamePasswordClientCredential.UserName%2A>  
 <xref:System.ServiceModel.Security.UserNamePasswordClientCredential.Password%2A>  
 <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>  
 <xref:System.ServiceModel.WSHttpSecurity.Mode%2A>  
 <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A>  
 [<span data-ttu-id="8e72d-132">Zabezpečení přenosu pomocí základního ověřování</span><span class="sxs-lookup"><span data-stu-id="8e72d-132">Transport Security with Basic Authentication</span></span>](../../../../docs/framework/wcf/feature-details/transport-security-with-basic-authentication.md)  
 [<span data-ttu-id="8e72d-133">Zabezpečení distribuované aplikace</span><span class="sxs-lookup"><span data-stu-id="8e72d-133">Distributed Application Security</span></span>](../../../../docs/framework/wcf/feature-details/distributed-application-security.md)  
 [<span data-ttu-id="8e72d-134">\<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="8e72d-134">\<wsHttpBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)
