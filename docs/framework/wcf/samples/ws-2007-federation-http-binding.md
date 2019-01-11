---
title: Prvek ws2007FederationHttpBinding
ms.date: 03/30/2017
ms.assetid: 91c1b477-a96e-4bf5-9330-5e9312113371
ms.openlocfilehash: 7dffe56cf5593f1cd59cccd7ea9b6b0e173e0c2c
ms.sourcegitcommit: a36cfc9dbbfc04bd88971f96e8a3f8e283c15d42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2019
ms.locfileid: "54221281"
---
# <a name="ws-2007-federation-http-binding"></a><span data-ttu-id="b7c5e-102">Prvek ws2007FederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="b7c5e-102">WS 2007 Federation HTTP Binding</span></span>
<span data-ttu-id="b7c5e-103">Tato ukázka demonstruje použití <xref:System.ServiceModel.WS2007FederationHttpBinding>, standardní vazbu, že můžete použít k sestavení federovaných scénářích podporu verzi 1.3 specifikaci WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="b7c5e-103">This sample demonstrates the use of <xref:System.ServiceModel.WS2007FederationHttpBinding>, a standard binding that you can use to build federated scenarios that support version 1.3 of the WS-Trust specification.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b7c5e-104">Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="b7c5e-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="b7c5e-105">Ukázka se skládá z klienta na základě konzoly programu (Client.exe), programu služby tokenů zabezpečení na základě konzoly (Securitytokenservice.exe) a programu pomocí konzoly služby (Service.exe).</span><span class="sxs-lookup"><span data-stu-id="b7c5e-105">The sample consists of a console-based client program (Client.exe), a console-based security token service program (Securitytokenservice.exe), and a console-based service program (Service.exe).</span></span> <span data-ttu-id="b7c5e-106">Služba implementuje kontrakt, který definuje vzor komunikace požadavku/odpovědi.</span><span class="sxs-lookup"><span data-stu-id="b7c5e-106">The service implements a contract that defines a request/reply communication pattern.</span></span> <span data-ttu-id="b7c5e-107">Smlouva je definován `ICalculator` rozhraní, které zveřejňuje matematických operací (`Add`, `Subtract`, `Multiply`, a `Divide`).</span><span class="sxs-lookup"><span data-stu-id="b7c5e-107">The contract is defined by the `ICalculator` interface, which exposes math operations (`Add`, `Subtract`, `Multiply`, and `Divide`).</span></span> <span data-ttu-id="b7c5e-108">Klient získá token zabezpečení z tokenu služba zabezpečení (STS) a umožňuje synchronní žádosti o službu pro dané matematické operace.</span><span class="sxs-lookup"><span data-stu-id="b7c5e-108">The client obtains a security token from the Security Token Service (STS) and makes synchronous requests to the service for a given math operation.</span></span> <span data-ttu-id="b7c5e-109">Služba potom odpovědi k výsledku.</span><span class="sxs-lookup"><span data-stu-id="b7c5e-109">The service then replies with the result.</span></span> <span data-ttu-id="b7c5e-110">Činnost klienta je vidět v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="b7c5e-110">Client activity is visible in the console window.</span></span>  
  
 <span data-ttu-id="b7c5e-111">Ukázka vytvoří `ICalculator` dostupná pomocí kontraktu `ws2007FederationHttpBinding` elementu.</span><span class="sxs-lookup"><span data-stu-id="b7c5e-111">The sample makes the `ICalculator` contract available using the `ws2007FederationHttpBinding` element.</span></span> <span data-ttu-id="b7c5e-112">Konfiguraci této vazby v klientovi je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="b7c5e-112">The configuration of this binding on the client is shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="b7c5e-113">Na [ \<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md), `security` hodnota určuje, který režim zabezpečení by měl sloužit.</span><span class="sxs-lookup"><span data-stu-id="b7c5e-113">On the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md), the `security` value specifies which security mode should be used.</span></span> <span data-ttu-id="b7c5e-114">V této ukázce `message` zabezpečení se používá, což je důvod, proč [ \<zpráva >](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) je zadat v rámci [ \<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="b7c5e-114">In this sample, `message` security is used, which is why the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) is specified inside the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md).</span></span> <span data-ttu-id="b7c5e-115">[ \<Issuer >](../../../../docs/framework/configure-apps/file-schema/wcf/issuer.md) element v rámci [ \<zpráva >](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) Určuje adresu a vazbu pro službu STS, která vydá token zabezpečení do klienta, takže klient může ověření `ICalculator` služby.</span><span class="sxs-lookup"><span data-stu-id="b7c5e-115">The [\<issuer>](../../../../docs/framework/configure-apps/file-schema/wcf/issuer.md) element inside the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) specifies the address and binding for the STS that issues a security token to the client so that the client can authenticate to the `ICalculator` service.</span></span>  
  
 <span data-ttu-id="b7c5e-116">Konfiguraci této vazby ve službě je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="b7c5e-116">The configuration of this binding on the service is shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="b7c5e-117">Na [ \<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md), `security` hodnota určuje, který režim zabezpečení by měl sloužit.</span><span class="sxs-lookup"><span data-stu-id="b7c5e-117">On the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md), the `security` value specifies which security mode should be used.</span></span> <span data-ttu-id="b7c5e-118">V této ukázce `message` zabezpečení se používá, což je důvod, proč [ \<zpráva >](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) je zadat v rámci [ \<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="b7c5e-118">In this sample, `message` security is used, which is why the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) is specified inside the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md).</span></span> <span data-ttu-id="b7c5e-119">[ \<IssuerMetadata >](../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata.md) prvek `ws2007FederationHttpBinding` uvnitř [ \<zpráva >](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) určuje adrese a identitě pro koncový bod, který slouží k načtení metadata pro službu STS.</span><span class="sxs-lookup"><span data-stu-id="b7c5e-119">The [\<issuerMetadata>](../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata.md) element of `ws2007FederationHttpBinding` inside the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) specifies the address and identity for an endpoint that can be used to retrieve metadata for the STS.</span></span>  
  
 <span data-ttu-id="b7c5e-120">Chování služby je uvedeno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="b7c5e-120">The behavior for the service is shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="b7c5e-121">[ \<IssuedTokenAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)> umožňuje zadat omezení na tokeny, umožňuje klientům k dispozici během ověřování služby.</span><span class="sxs-lookup"><span data-stu-id="b7c5e-121">The [\<issuedTokenAuthentication>](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)> allows the service to specify constraints on the tokens it allows clients to present during authentication.</span></span> <span data-ttu-id="b7c5e-122">Tato konfigurace určuje, že tokeny podepsán certifikátem, jehož název subjektu je CN = služby STS jsou změna přijata službou.</span><span class="sxs-lookup"><span data-stu-id="b7c5e-122">This configuration specifies that tokens signed by a certificate whose subject name is CN=STS are accepted by the service.</span></span>  
  
 <span data-ttu-id="b7c5e-123">Služba STS jeden koncový bod k dispozici prostřednictvím standardních <xref:System.ServiceModel.WS2007HttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="b7c5e-123">STS makes a single endpoint available using the standard <xref:System.ServiceModel.WS2007HttpBinding>.</span></span> <span data-ttu-id="b7c5e-124">Služby jsou reaguje na požadavky od klientů pro tokeny.</span><span class="sxs-lookup"><span data-stu-id="b7c5e-124">The service responds to requests from clients for tokens.</span></span> <span data-ttu-id="b7c5e-125">Pokud klient je ověřený pomocí účtu Windows, služby vystaví token, který obsahuje jméno uživatele klienta jako deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="b7c5e-125">If the client is authenticated using a Windows account, the service issues a token that contains the client's user name as a claim.</span></span> <span data-ttu-id="b7c5e-126">Jako součást vytváření token příznaky STS token pomocí soukromého klíče přidružené k CN = certifikátu STS.</span><span class="sxs-lookup"><span data-stu-id="b7c5e-126">As part of creating the token, STS signs the token using the private key associated with the CN=STS certificate.</span></span> <span data-ttu-id="b7c5e-127">Kromě toho vytvoří symetrický klíč a zašifruje pomocí veřejného klíče přidruženého CN = localhost certifikát.</span><span class="sxs-lookup"><span data-stu-id="b7c5e-127">In addition, it creates a symmetric key and encrypts it using the public key associated with the CN=localhost certificate.</span></span> <span data-ttu-id="b7c5e-128">V vrácením tokenu klientovi, služba tokenů zabezpečení také vrátí hodnotu symetrický klíč.</span><span class="sxs-lookup"><span data-stu-id="b7c5e-128">In returning the token to the client, STS also returns the symmetric key.</span></span> <span data-ttu-id="b7c5e-129">Klient poskytne vydaný token `ICalculator` služby a prokáže, že zná symetrický klíč pomocí podepsání zprávy s tímto klíčem.</span><span class="sxs-lookup"><span data-stu-id="b7c5e-129">The client presents the issued token to the `ICalculator` service and proves that it knows the symmetric key by signing the message with that key.</span></span>  
  
 <span data-ttu-id="b7c5e-130">Když spustíte ukázku, požadavek na token zabezpečení se zobrazí v okně konzoly služby tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="b7c5e-130">When you run the sample, the request for the security token is shown in the STS console window.</span></span> <span data-ttu-id="b7c5e-131">Požadavky a odpovědi operace se zobrazují v oknech konzoly klienta a služby.</span><span class="sxs-lookup"><span data-stu-id="b7c5e-131">The operation's requests and responses are displayed in the client and service console windows.</span></span> <span data-ttu-id="b7c5e-132">Stisknutím klávesy ENTER v některém z okna konzoly vypnout aplikaci.</span><span class="sxs-lookup"><span data-stu-id="b7c5e-132">Press ENTER in any of the console windows to shut down the application.</span></span>  

```
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714
Press <ENTER> to terminate client.
```

 <span data-ttu-id="b7c5e-133">Soubor Setup.bat zahrnuté v této ukázce umožňuje nakonfigurovat server a služba tokenů zabezpečení pomocí příslušné certifikáty, které budou spouštět aplikace v místním prostředí.</span><span class="sxs-lookup"><span data-stu-id="b7c5e-133">The Setup.bat file included with this sample allows you to configure the server and STS with the relevant certificates to run a self-hosted application.</span></span> <span data-ttu-id="b7c5e-134">Dávkový soubor se vytvoří dva certifikáty v úložišti LocalMachine/TrustedPeople certifikátů.</span><span class="sxs-lookup"><span data-stu-id="b7c5e-134">The batch file creates two certificates in the LocalMachine/TrustedPeople certificate store.</span></span> <span data-ttu-id="b7c5e-135">První certifikát má název předmětu CN = STS a služba tokenů zabezpečení používá k podepisování tokenů zabezpečení, které vystavuje do klienta.</span><span class="sxs-lookup"><span data-stu-id="b7c5e-135">The first certificate has a subject name of CN=STS and is used by STS to sign the security tokens that it issues to the client.</span></span> <span data-ttu-id="b7c5e-136">Druhý certifikát má název předmětu CN = localhost a služba tokenů zabezpečení používá k šifrování klíče tak, aby mohly dešifrovat služby.</span><span class="sxs-lookup"><span data-stu-id="b7c5e-136">The second certificate has a subject name of CN=localhost and is used by STS to encrypt a key in a way that the service can decrypt.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b7c5e-137">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="b7c5e-137">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="b7c5e-138">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b7c5e-138">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="b7c5e-139">Otevřete příkazový řádek vývojáře pro sadu Visual Studio s oprávněními správce a spusťte soubor Setup.bat vytvořit požadované certifikáty.</span><span class="sxs-lookup"><span data-stu-id="b7c5e-139">Open a Developer Command Prompt for Visual Studio with administrator privileges and run the Setup.bat file to create the required certificates.</span></span>  
  
 <span data-ttu-id="b7c5e-140">Tento dávkový soubor používá Certmgr.exe a Makecert.exe, které jsou distribuovány v sadě Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="b7c5e-140">This batch file uses Certmgr.exe and Makecert.exe, which are distributed with the Windows SDK.</span></span> <span data-ttu-id="b7c5e-141">Však musíte spustit Setup.bat z v rámci příkazový řádek sady Visual Studio umožňuje skript, který chcete najít těchto nástrojů.</span><span class="sxs-lookup"><span data-stu-id="b7c5e-141">However, you must run Setup.bat from within a Visual Studio  command prompt to enable the script to find these tools.</span></span>  
  
1.  <span data-ttu-id="b7c5e-142">K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b7c5e-142">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2.  <span data-ttu-id="b7c5e-143">Spusťte ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b7c5e-143">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span> <span data-ttu-id="b7c5e-144">Pokud používáte [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)], je nutné spustit Service.exe, Client.exe, a SecurityTokenService.exe s se zvýšenými oprávněními (pravým tlačítkem myši na soubory a pak klikněte na tlačítko **spustit jako správce**).</span><span class="sxs-lookup"><span data-stu-id="b7c5e-144">If you are using [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)], you must run Service.exe, Client.exe, and SecurityTokenService.exe with elevated privileges (right-click the files and then click **Run as administrator**).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b7c5e-145">Vzorky mohou již být nainstalováno ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="b7c5e-145">The samples may already be installed on your computer.</span></span> <span data-ttu-id="b7c5e-146">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="b7c5e-146">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="b7c5e-147">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="b7c5e-147">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b7c5e-148">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="b7c5e-148">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\WS2007FederationHttp`  
  
## <a name="see-also"></a><span data-ttu-id="b7c5e-149">Viz také</span><span class="sxs-lookup"><span data-stu-id="b7c5e-149">See Also</span></span>
