---
title: Prvek ws2007FederationHttpBinding
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 91c1b477-a96e-4bf5-9330-5e9312113371
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3cdba8b43c109b8fbd0a5892bfa4c4c15e1caabf
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ws-2007-federation-http-binding"></a><span data-ttu-id="081f7-102">Prvek ws2007FederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="081f7-102">WS 2007 Federation HTTP Binding</span></span>
<span data-ttu-id="081f7-103">Tento příklad znázorňuje použití <xref:System.ServiceModel.WS2007FederationHttpBinding>, standard, můžete použít k vytvoření této verze podpory 1.3 specifikace WS-Trust federovaných scénářích vazby.</span><span class="sxs-lookup"><span data-stu-id="081f7-103">This sample demonstrates the use of <xref:System.ServiceModel.WS2007FederationHttpBinding>, a standard binding that you can use to build federated scenarios that support version 1.3 of the WS-Trust specification.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="081f7-104">V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="081f7-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="081f7-105">Ukázka se skládá z programu pomocí konzoly klienta (Client.exe), programu služby tokenů zabezpečení na základě konzoly (Securitytokenservice.exe) a programu pomocí konzoly služby (Service.exe).</span><span class="sxs-lookup"><span data-stu-id="081f7-105">The sample consists of a console-based client program (Client.exe), a console-based security token service program (Securitytokenservice.exe), and a console-based service program (Service.exe).</span></span> <span data-ttu-id="081f7-106">Služba se implementuje kontrakt, který definuje komunikační vzor požadavek nebo odpověď.</span><span class="sxs-lookup"><span data-stu-id="081f7-106">The service implements a contract that defines a request/reply communication pattern.</span></span> <span data-ttu-id="081f7-107">Kontrakt je definována `ICalculator` rozhraní, která zpřístupňuje matematické operace (`Add`, `Subtract`, `Multiply`, a `Divide`).</span><span class="sxs-lookup"><span data-stu-id="081f7-107">The contract is defined by the `ICalculator` interface, which exposes math operations (`Add`, `Subtract`, `Multiply`, and `Divide`).</span></span> <span data-ttu-id="081f7-108">Klient získá token zabezpečení ze zabezpečení tokenu služby (STS) a zadává synchronní požadavků službou pro danou matematické operace.</span><span class="sxs-lookup"><span data-stu-id="081f7-108">The client obtains a security token from the Security Token Service (STS) and makes synchronous requests to the service for a given math operation.</span></span> <span data-ttu-id="081f7-109">Služby a odpovědi s výsledek.</span><span class="sxs-lookup"><span data-stu-id="081f7-109">The service then replies with the result.</span></span> <span data-ttu-id="081f7-110">Činnost klienta je viditelný v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="081f7-110">Client activity is visible in the console window.</span></span>  
  
 <span data-ttu-id="081f7-111">Díky vzorku `ICalculator` kontrakt dostupné pomocí `ws2007FederationHttpBinding` element.</span><span class="sxs-lookup"><span data-stu-id="081f7-111">The sample makes the `ICalculator` contract available using the `ws2007FederationHttpBinding` element.</span></span> <span data-ttu-id="081f7-112">Konfigurace této vazby v klientovi je zobrazena v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="081f7-112">The configuration of this binding on the client is shown in the following code.</span></span>  
  
```xml  
<bindings>  
  <ws2007FederationHttpBinding>  
    <binding name="ServiceFed" >  
      <security mode ="Message">  
        <message issuedKeyType ="SymmetricKey"  
                 issuedTokenType ="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1" >  
          <!-- Endpoint address and binding for Security Token Service -->  
          <issuer address ="http://localhost:8000/sts/windows"   
                  binding ="ws2007HttpBinding" />                
        </message>  
      </security>  
    </binding>  
  </ws2007FederationHttpBinding>  
</bindings>  
```  
  
 <span data-ttu-id="081f7-113">Na [ \<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md), `security` hodnota určuje, které režim zabezpečení by měl použít.</span><span class="sxs-lookup"><span data-stu-id="081f7-113">On the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md), the `security` value specifies which security mode should be used.</span></span> <span data-ttu-id="081f7-114">V této ukázce `message` zabezpečení se používá, což je důvod, proč [ \<zpráva >](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) je zadat v rámci [ \<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="081f7-114">In this sample, `message` security is used, which is why the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) is specified inside the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md).</span></span> <span data-ttu-id="081f7-115">[ \<Vystavitele >](../../../../docs/framework/configure-apps/file-schema/wcf/issuer.md) prvku v [ \<zpráva >](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) Určuje adresu a vydá token zabezpečení do klienta, takže klient může vazbu pro Služba tokenů zabezpečení ověření `ICalculator` služby.</span><span class="sxs-lookup"><span data-stu-id="081f7-115">The [\<issuer>](../../../../docs/framework/configure-apps/file-schema/wcf/issuer.md) element inside the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) specifies the address and binding for the STS that issues a security token to the client so that the client can authenticate to the `ICalculator` service.</span></span>  
  
 <span data-ttu-id="081f7-116">Konfigurace tuto vazbu na službu je vidět v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="081f7-116">The configuration of this binding on the service is shown in the following code.</span></span>  
  
```xml  
<bindings>  
  <ws2007FederationHttpBinding>  
    <binding name="ServiceFed" >  
      <security mode ="Message">  
        <message issuedKeyType ="SymmetricKey"  
                 issuedTokenType ="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1" >  
          <!-- Metadata address for Security Token Service -->  
          <issuerMetadata address ="http://localhost:8000/sts/mex" >  
            <identity>  
              <certificateReference storeLocation ="CurrentUser"   
                                    storeName="TrustedPeople"   
                                    x509FindType ="FindBySubjectDistinguishedName"   
                                    findValue ="CN=STS" />  
            </identity>  
          </issuerMetadata>  
        </message>  
      </security>  
    </binding>  
  </ws2007FederationHttpBinding>  
</bindings>  
```  
  
 <span data-ttu-id="081f7-117">Na [ \<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md), `security` hodnota určuje, které režim zabezpečení by měl použít.</span><span class="sxs-lookup"><span data-stu-id="081f7-117">On the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md), the `security` value specifies which security mode should be used.</span></span> <span data-ttu-id="081f7-118">V této ukázce `message` zabezpečení se používá, což je důvod, proč [ \<zpráva >](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) je zadat v rámci [ \<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="081f7-118">In this sample, `message` security is used, which is why the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) is specified inside the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md).</span></span> <span data-ttu-id="081f7-119">[ \<IssuerMetadata >](../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata.md) element `ws2007FederationHttpBinding` uvnitř [ \<zpráva >](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) určuje adrese a identitě pro koncový bod, který slouží k načtení metadata pro Služba tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="081f7-119">The [\<issuerMetadata>](../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata.md) element of `ws2007FederationHttpBinding` inside the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) specifies the address and identity for an endpoint that can be used to retrieve metadata for the STS.</span></span>  
  
 <span data-ttu-id="081f7-120">Chování pro službu je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="081f7-120">The behavior for the service is shown in the following code.</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name ="ServiceBehaviour" >  
      <serviceDebug includeExceptionDetailInFaults ="true"/>  
      <serviceMetadata httpGetEnabled ="true"/>  
      <serviceCredentials>  
        <issuedTokenAuthentication>  
          <knownCertificates>  
            <add storeLocation ="LocalMachine"  
                 storeName="TrustedPeople"  
                 x509FindType="FindBySubjectDistinguishedName"  
                 findValue="CN=STS" />  
          </knownCertificates>  
        </issuedTokenAuthentication>  
        <serviceCertificate storeLocation ="LocalMachine"  
                            storeName ="My"  
                            x509FindType ="FindBySubjectDistinguishedName"  
                            findValue ="CN=localhost"/>  
      </serviceCredentials>  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="081f7-121">[ \<IssuedTokenAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)> umožňuje službě zadejte omezení umožňuje klientům k dispozici při ověřování tokenů.</span><span class="sxs-lookup"><span data-stu-id="081f7-121">The [\<issuedTokenAuthentication>](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)> allows the service to specify constraints on the tokens it allows clients to present during authentication.</span></span> <span data-ttu-id="081f7-122">Tato konfigurace určuje, že tokeny podepsaný certifikát, jehož název subjektu CN = přijímat jsou služby tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="081f7-122">This configuration specifies that tokens signed by a certificate whose subject name is CN=STS are accepted by the service.</span></span>  
  
 <span data-ttu-id="081f7-123">Služba tokenů zabezpečení zpřístupní jeden koncový bod přes standardní <xref:System.ServiceModel.WS2007HttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="081f7-123">STS makes a single endpoint available using the standard <xref:System.ServiceModel.WS2007HttpBinding>.</span></span> <span data-ttu-id="081f7-124">Služba odpovídá na požadavky od klientů pro tokeny.</span><span class="sxs-lookup"><span data-stu-id="081f7-124">The service responds to requests from clients for tokens.</span></span> <span data-ttu-id="081f7-125">Pokud je klient ověřen pomocí účtu Windows, službu vystaví token, který obsahuje jméno uživatele klienta jako deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="081f7-125">If the client is authenticated using a Windows account, the service issues a token that contains the client's user name as a claim.</span></span> <span data-ttu-id="081f7-126">Při vytváření tokenu služby tokenů zabezpečení přihlásí token pomocí privátní klíč přidružený CN = certifikát služby tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="081f7-126">As part of creating the token, STS signs the token using the private key associated with the CN=STS certificate.</span></span> <span data-ttu-id="081f7-127">Kromě toho vytvoří symetrického klíče a zašifruje pomocí veřejného klíče přidruženého CN = localhost certifikátu.</span><span class="sxs-lookup"><span data-stu-id="081f7-127">In addition, it creates a symmetric key and encrypts it using the public key associated with the CN=localhost certificate.</span></span> <span data-ttu-id="081f7-128">Při vracení token do klienta, služby tokenů zabezpečení také vrátí symetrický klíč.</span><span class="sxs-lookup"><span data-stu-id="081f7-128">In returning the token to the client, STS also returns the symmetric key.</span></span> <span data-ttu-id="081f7-129">Klient poskytne vystavený token, který má `ICalculator` služby a prokáže, že zná symetrický klíč podepsáním zprávu s tímto klíčem.</span><span class="sxs-lookup"><span data-stu-id="081f7-129">The client presents the issued token to the `ICalculator` service and proves that it knows the symmetric key by signing the message with that key.</span></span>  
  
 <span data-ttu-id="081f7-130">Při spuštění vzorového žádost o token zabezpečení se zobrazí v okně konzoly služby tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="081f7-130">When you run the sample, the request for the security token is shown in the STS console window.</span></span> <span data-ttu-id="081f7-131">Požadavky a odpovědi operace se zobrazují v oknech konzoly klienta a služby.</span><span class="sxs-lookup"><span data-stu-id="081f7-131">The operation's requests and responses are displayed in the client and service console windows.</span></span> <span data-ttu-id="081f7-132">Stisknutím klávesy ENTER v některém z okna konzoly vypnout aplikaci.</span><span class="sxs-lookup"><span data-stu-id="081f7-132">Press ENTER in any of the console windows to shut down the application.</span></span>  
  
 `Add(100,15.99) = 115.99`  
  
 `Subtract(145,76.54) = 68.46`  
  
 `Multiply(9,81.25) = 731.25`  
  
 `Divide(22,7) = 3.14285714285714`  
  
 `Press <ENTER> to terminate client.`  
  
 <span data-ttu-id="081f7-133">Tato ukázka je součástí souboru Setup.bat umožňuje nakonfigurovat server a službu tokenů zabezpečení příslušné certifikáty, spuštění aplikace s vlastním hostováním.</span><span class="sxs-lookup"><span data-stu-id="081f7-133">The Setup.bat file included with this sample allows you to configure the server and STS with the relevant certificates to run a self-hosted application.</span></span> <span data-ttu-id="081f7-134">Dávkový soubor vytvoří dva certifikáty v úložišti certifikátů LocalMachine/TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="081f7-134">The batch file creates two certificates in the LocalMachine/TrustedPeople certificate store.</span></span> <span data-ttu-id="081f7-135">První certifikát obsahuje název subjektu z CN = služby tokenů zabezpečení a slouží k podepisování tokenů zabezpečení, které vystavuje klientovi službou tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="081f7-135">The first certificate has a subject name of CN=STS and is used by STS to sign the security tokens that it issues to the client.</span></span> <span data-ttu-id="081f7-136">Druhý certifikát obsahuje název subjektu z CN = localhost a slouží k šifrování klíče tak, aby mohly dešifrovat službu službou tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="081f7-136">The second certificate has a subject name of CN=localhost and is used by STS to encrypt a key in a way that the service can decrypt.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="081f7-137">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="081f7-137">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="081f7-138">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="081f7-138">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="081f7-139">Otevřete příkazový řádek sady Visual Studio s oprávněními správce a spusťte soubor Setup.bat k vytvoření požadované certifikáty.</span><span class="sxs-lookup"><span data-stu-id="081f7-139">Open a Visual Studio command prompt with administrator privileges and run the Setup.bat file to create the required certificates.</span></span>  
  
 <span data-ttu-id="081f7-140">Tento dávkový soubor používá Certmgr.exe a Makecert.exe, které jsou distribuovány sada Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="081f7-140">This batch file uses Certmgr.exe and Makecert.exe, which are distributed with the Windows SDK.</span></span> <span data-ttu-id="081f7-141">Setup.bat z však musíte spustit v rámci příkazového řádku Visual Studia povolit skript, který chcete najít těchto nástrojů.</span><span class="sxs-lookup"><span data-stu-id="081f7-141">However, you must run Setup.bat from within a Visual Studio  command prompt to enable the script to find these tools.</span></span>  
  
1.  <span data-ttu-id="081f7-142">Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="081f7-142">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2.  <span data-ttu-id="081f7-143">Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="081f7-143">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span> <span data-ttu-id="081f7-144">Pokud používáte [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)], je nutné spustit Service.exe Client.exe, a SecurityTokenService.exe se zvýšenými oprávněními (pravým tlačítkem myši na a pak klikněte na **spustit jako správce**).</span><span class="sxs-lookup"><span data-stu-id="081f7-144">If you are using [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)], you must run Service.exe, Client.exe, and SecurityTokenService.exe with elevated privileges (right-click the files and then click **Run as administrator**).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="081f7-145">Ukázky může být již nainstalován ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="081f7-145">The samples may already be installed on your computer.</span></span> <span data-ttu-id="081f7-146">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="081f7-146">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="081f7-147">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="081f7-147">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="081f7-148">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="081f7-148">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\WS2007FederationHttp`  
  
## <a name="see-also"></a><span data-ttu-id="081f7-149">Viz také</span><span class="sxs-lookup"><span data-stu-id="081f7-149">See Also</span></span>
