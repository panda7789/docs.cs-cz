---
title: Prvek ws2007FederationHttpBinding
ms.date: 03/30/2017
ms.assetid: 91c1b477-a96e-4bf5-9330-5e9312113371
ms.openlocfilehash: bf61e64733859d96adf42fbacf08266eca1f5b45
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183176"
---
# <a name="ws-2007-federation-http-binding"></a><span data-ttu-id="c7d3c-102">Prvek ws2007FederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="c7d3c-102">WS 2007 Federation HTTP Binding</span></span>

<span data-ttu-id="c7d3c-103">Tato ukázka ukazuje <xref:System.ServiceModel.WS2007FederationHttpBinding>použití , standardní vazby, které můžete použít k vytvoření federované scénáře, které podporují verzi 1.3 specifikace WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="c7d3c-103">This sample demonstrates the use of <xref:System.ServiceModel.WS2007FederationHttpBinding>, a standard binding that you can use to build federated scenarios that support version 1.3 of the WS-Trust specification.</span></span>

> [!NOTE]
> <span data-ttu-id="c7d3c-104">Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="c7d3c-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="c7d3c-105">Ukázka se skládá z klientského programu založeného na konzoli (*Client.exe*), programu služby tokenů zabezpečení založených na konzoli (*Securitytokenservice.exe*) a servisního programu založeného na konzoli (*Service.exe*).</span><span class="sxs-lookup"><span data-stu-id="c7d3c-105">The sample consists of a console-based client program (*Client.exe*), a console-based security token service program (*Securitytokenservice.exe*), and a console-based service program (*Service.exe*).</span></span> <span data-ttu-id="c7d3c-106">Služba implementuje smlouvu, která definuje vzor komunikace požadavek/odpověď.</span><span class="sxs-lookup"><span data-stu-id="c7d3c-106">The service implements a contract that defines a request/reply communication pattern.</span></span> <span data-ttu-id="c7d3c-107">Kontrakt je definován `ICalculator` rozhraním, které zveřejňuje`Add`matematické `Subtract` `Multiply`operace `Divide`( , , , a ).</span><span class="sxs-lookup"><span data-stu-id="c7d3c-107">The contract is defined by the `ICalculator` interface, which exposes math operations (`Add`, `Subtract`, `Multiply`, and `Divide`).</span></span> <span data-ttu-id="c7d3c-108">Klient získá token zabezpečení ze služby TOKEN zabezpečení (STS) a provede synchronní požadavky na službu pro danou matematickou operaci.</span><span class="sxs-lookup"><span data-stu-id="c7d3c-108">The client obtains a security token from the Security Token Service (STS) and makes synchronous requests to the service for a given math operation.</span></span> <span data-ttu-id="c7d3c-109">Služba pak odpoví s výsledkem.</span><span class="sxs-lookup"><span data-stu-id="c7d3c-109">The service then replies with the result.</span></span> <span data-ttu-id="c7d3c-110">Aktivita klienta je viditelná v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="c7d3c-110">Client activity is visible in the console window.</span></span>

<span data-ttu-id="c7d3c-111">Ukázka zpřístupní `ICalculator` kontrakt `ws2007FederationHttpBinding` pomocí prvku.</span><span class="sxs-lookup"><span data-stu-id="c7d3c-111">The sample makes the `ICalculator` contract available using the `ws2007FederationHttpBinding` element.</span></span> <span data-ttu-id="c7d3c-112">Konfigurace této vazby na straně klienta je zobrazena v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="c7d3c-112">The configuration of this binding on the client is shown in the following code:</span></span>

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

<span data-ttu-id="c7d3c-113">Na [ \<>zabezpečení ](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md) `security` určuje hodnota, který má být použit režim zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="c7d3c-113">On the [\<security>](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md), the `security` value specifies which security mode should be used.</span></span> <span data-ttu-id="c7d3c-114">V této `message` ukázce se používá zabezpečení, což je důvod, proč je [ \<zpráva>](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) zadána [ \< ](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md)uvnitř>zabezpečení .</span><span class="sxs-lookup"><span data-stu-id="c7d3c-114">In this sample, `message` security is used, which is why the [\<message>](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) is specified inside the [\<security>](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md).</span></span> <span data-ttu-id="c7d3c-115">[ \<Vystavitel>](../../configure-apps/file-schema/wcf/issuer.md) prvek uvnitř [ \<zprávy>](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) určuje adresu a vazbu pro STS, která vydává token `ICalculator` zabezpečení klientovi tak, aby klient může ověřit službu.</span><span class="sxs-lookup"><span data-stu-id="c7d3c-115">The [\<issuer>](../../configure-apps/file-schema/wcf/issuer.md) element inside the [\<message>](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) specifies the address and binding for the STS that issues a security token to the client so that the client can authenticate to the `ICalculator` service.</span></span>
  
<span data-ttu-id="c7d3c-116">Konfigurace této vazby na službu je zobrazena v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="c7d3c-116">The configuration of this binding on the service is shown in the following code:</span></span>

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

<span data-ttu-id="c7d3c-117">Na [ \<>zabezpečení ](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md) `security` určuje hodnota, který má být použit režim zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="c7d3c-117">On the [\<security>](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md), the `security` value specifies which security mode should be used.</span></span> <span data-ttu-id="c7d3c-118">V této `message` ukázce se používá zabezpečení, což je důvod, proč je [ \<zpráva>](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) zadána [ \< ](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md)uvnitř>zabezpečení .</span><span class="sxs-lookup"><span data-stu-id="c7d3c-118">In this sample, `message` security is used, which is why the [\<message>](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) is specified inside the [\<security>](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md).</span></span> <span data-ttu-id="c7d3c-119">[ \<IssuerMetadata>](../../configure-apps/file-schema/wcf/issuermetadata.md) prvek `ws2007FederationHttpBinding` uvnitř [ \<zprávy>](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) určuje adresu a identitu pro koncový bod, který lze použít k načtení metadat pro STS.</span><span class="sxs-lookup"><span data-stu-id="c7d3c-119">The [\<issuerMetadata>](../../configure-apps/file-schema/wcf/issuermetadata.md) element of `ws2007FederationHttpBinding` inside the [\<message>](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) specifies the address and identity for an endpoint that can be used to retrieve metadata for the STS.</span></span>

<span data-ttu-id="c7d3c-120">Chování služby je zobrazeno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="c7d3c-120">The behavior for the service is shown in the following code:</span></span>

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
  
<span data-ttu-id="c7d3c-121">[ \<IssuedTokenAuthentication>](../../configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)> umožňuje službě určit omezení tokenů, které umožňuje klientům prezentovat během ověřování.</span><span class="sxs-lookup"><span data-stu-id="c7d3c-121">The [\<issuedTokenAuthentication>](../../configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)> allows the service to specify constraints on the tokens it allows clients to present during authentication.</span></span> <span data-ttu-id="c7d3c-122">Tato konfigurace určuje, že tokeny podepsané certifikátem, jehož název subjektu je CN=STS, jsou službou přijímány.</span><span class="sxs-lookup"><span data-stu-id="c7d3c-122">This configuration specifies that tokens signed by a certificate whose subject name is CN=STS are accepted by the service.</span></span>

<span data-ttu-id="c7d3c-123">STS zpřístupňuje jeden koncový <xref:System.ServiceModel.WS2007HttpBinding>bod pomocí standardu .</span><span class="sxs-lookup"><span data-stu-id="c7d3c-123">STS makes a single endpoint available using the standard <xref:System.ServiceModel.WS2007HttpBinding>.</span></span> <span data-ttu-id="c7d3c-124">Služba reaguje na požadavky klientů pro tokeny.</span><span class="sxs-lookup"><span data-stu-id="c7d3c-124">The service responds to requests from clients for tokens.</span></span> <span data-ttu-id="c7d3c-125">Pokud je klient ověřen pomocí účtu systému Windows, služba vydá token, který obsahuje uživatelské jméno klienta jako deklaraci.</span><span class="sxs-lookup"><span data-stu-id="c7d3c-125">If the client is authenticated using a Windows account, the service issues a token that contains the client's user name as a claim.</span></span> <span data-ttu-id="c7d3c-126">Jako součást vytváření tokenu, STS podepisuje token pomocí soukromého klíče přidruženého k certifikátu CN = STS.</span><span class="sxs-lookup"><span data-stu-id="c7d3c-126">As part of creating the token, STS signs the token using the private key associated with the CN=STS certificate.</span></span> <span data-ttu-id="c7d3c-127">Kromě toho vytvoří symetrický klíč a šifruje jej pomocí veřejného klíče přidruženého k certifikátu CN=localhost.</span><span class="sxs-lookup"><span data-stu-id="c7d3c-127">In addition, it creates a symmetric key and encrypts it using the public key associated with the CN=localhost certificate.</span></span> <span data-ttu-id="c7d3c-128">Při vrácení tokenu klientovi STS také vrátí symetrický klíč.</span><span class="sxs-lookup"><span data-stu-id="c7d3c-128">In returning the token to the client, STS also returns the symmetric key.</span></span> <span data-ttu-id="c7d3c-129">Klient představuje vydaný token `ICalculator` do služby a prokáže, že zná symetrický klíč podpisem zprávy s tímto klíčem.</span><span class="sxs-lookup"><span data-stu-id="c7d3c-129">The client presents the issued token to the `ICalculator` service and proves that it knows the symmetric key by signing the message with that key.</span></span>

<span data-ttu-id="c7d3c-130">Při spuštění ukázky je v okně konzoly STS zobrazen požadavek na token zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="c7d3c-130">When you run the sample, the request for the security token is shown in the STS console window.</span></span> <span data-ttu-id="c7d3c-131">Požadavky a odpovědi operace jsou zobrazeny v oknech klienta a konzoly služby.</span><span class="sxs-lookup"><span data-stu-id="c7d3c-131">The operation's requests and responses are displayed in the client and service console windows.</span></span> <span data-ttu-id="c7d3c-132">Stisknutím klávesy ENTER v libovolném systému konzoly aplikaci vypněte.</span><span class="sxs-lookup"><span data-stu-id="c7d3c-132">Press ENTER in any of the console windows to shut down the application.</span></span>

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714
Press <ENTER> to terminate client.
```

<span data-ttu-id="c7d3c-133">Soubor *Setup.bat,* který je součástí této ukázky, umožňuje nakonfigurovat server a službu STS s příslušnými certifikáty pro spuštění samoobslužné aplikace.</span><span class="sxs-lookup"><span data-stu-id="c7d3c-133">The *Setup.bat* file included with this sample allows you to configure the server and STS with the relevant certificates to run a self-hosted application.</span></span> <span data-ttu-id="c7d3c-134">Dávkový soubor vytvoří dva certifikáty v úložišti certifikátů LocalMachine/TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="c7d3c-134">The batch file creates two certificates in the LocalMachine/TrustedPeople certificate store.</span></span> <span data-ttu-id="c7d3c-135">První certifikát má název subjektu CN = STS a používá STS k podepsání tokeny zabezpečení, které vydává klientovi.</span><span class="sxs-lookup"><span data-stu-id="c7d3c-135">The first certificate has a subject name of CN=STS and is used by STS to sign the security tokens that it issues to the client.</span></span> <span data-ttu-id="c7d3c-136">Druhý certifikát má název subjektu CN = localhost a je používán STS k šifrování klíče způsobem, který služba může dešifrovat.</span><span class="sxs-lookup"><span data-stu-id="c7d3c-136">The second certificate has a subject name of CN=localhost and is used by STS to encrypt a key in a way that the service can decrypt.</span></span>

## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c7d3c-137">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="c7d3c-137">To set up, build, and run the sample</span></span>
  
1. <span data-ttu-id="c7d3c-138">Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c7d3c-138">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="c7d3c-139">Otevřete příkazový řádek pro vývojáře pro visual studio s oprávněními správce a spusťte soubor Setup.bat a vytvořte požadované certifikáty.</span><span class="sxs-lookup"><span data-stu-id="c7d3c-139">Open a Developer Command Prompt for Visual Studio with administrator privileges and run the Setup.bat file to create the required certificates.</span></span>

 <span data-ttu-id="c7d3c-140">Tento dávkový soubor používá *certmgr.exe* a makecert.exe, které jsou distribuovány se sadou Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="c7d3c-140">This batch file uses *Certmgr.exe* and Makecert.exe, which are distributed with the Windows SDK.</span></span> <span data-ttu-id="c7d3c-141">Je však nutné spustit *Setup.bat* z příkazového řádku sady Visual Studio, aby skript tyto nástroje našel.</span><span class="sxs-lookup"><span data-stu-id="c7d3c-141">However, you must run *Setup.bat* from within a Visual Studio command prompt to enable the script to find these tools.</span></span>

1. <span data-ttu-id="c7d3c-142">Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c7d3c-142">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

2. <span data-ttu-id="c7d3c-143">Chcete-li spustit ukázku v konfiguraci jednoho nebo mezi počítači, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c7d3c-143">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span> <span data-ttu-id="c7d3c-144">Používáte-li systém Windows Vista, je nutné spustit program *Service.exe*, *Client.exe*a *securitytokenservice.exe* se zvýšenými oprávněními (klepněte pravým tlačítkem myši na soubory a potom klepněte na příkaz **Spustit jako správce**).</span><span class="sxs-lookup"><span data-stu-id="c7d3c-144">If you are using Windows Vista, you must run *Service.exe*, *Client.exe*, and *SecurityTokenService.exe* with elevated privileges (right-click the files and then click **Run as administrator**).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c7d3c-145">Ukázky mohou být již nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="c7d3c-145">The samples may already be installed on your computer.</span></span> <span data-ttu-id="c7d3c-146">Před pokračováním zkontrolujte následující (výchozí) adresář:</span><span class="sxs-lookup"><span data-stu-id="c7d3c-146">Check for the following (default) directory before continuing:</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="c7d3c-147">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="c7d3c-147">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c7d3c-148">Tato ukázka je umístěna v následujícím adresáři:</span><span class="sxs-lookup"><span data-stu-id="c7d3c-148">This sample is located in the following directory:</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\WS2007FederationHttp`
