---
title: Prvek ws2007FederationHttpBinding
ms.date: 03/30/2017
ms.assetid: 91c1b477-a96e-4bf5-9330-5e9312113371
ms.openlocfilehash: 0a01cd3790e17f532b2f6405f83c9507ecc2f6fd
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70038523"
---
# <a name="ws-2007-federation-http-binding"></a><span data-ttu-id="a4230-102">Prvek ws2007FederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="a4230-102">WS 2007 Federation HTTP Binding</span></span>
<span data-ttu-id="a4230-103">Tato ukázka předvádí použití <xref:System.ServiceModel.WS2007FederationHttpBinding>standardní vazby, kterou můžete použít k sestavení federovaných scénářů, které podporují verzi 1,3 specifikace WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="a4230-103">This sample demonstrates the use of <xref:System.ServiceModel.WS2007FederationHttpBinding>, a standard binding that you can use to build federated scenarios that support version 1.3 of the WS-Trust specification.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a4230-104">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="a4230-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="a4230-105">Ukázka se skládá z klientského programu založeného na konzole (soubor Client. exe), programu služby tokenu zabezpečení založeného na konzole (SecurityTokenService. exe) a programu služby (Service. exe) založeném na konzole.</span><span class="sxs-lookup"><span data-stu-id="a4230-105">The sample consists of a console-based client program (Client.exe), a console-based security token service program (Securitytokenservice.exe), and a console-based service program (Service.exe).</span></span> <span data-ttu-id="a4230-106">Služba implementuje kontrakt definující způsob komunikace požadavků a odpovědí.</span><span class="sxs-lookup"><span data-stu-id="a4230-106">The service implements a contract that defines a request/reply communication pattern.</span></span> <span data-ttu-id="a4230-107">Kontrakt `ICalculator` je definován rozhraním, které zpřístupňuje matematické operace ( `Subtract``Add`,, `Multiply`a `Divide`).</span><span class="sxs-lookup"><span data-stu-id="a4230-107">The contract is defined by the `ICalculator` interface, which exposes math operations (`Add`, `Subtract`, `Multiply`, and `Divide`).</span></span> <span data-ttu-id="a4230-108">Klient získá token zabezpečení ze služby tokenu zabezpečení (STS) a provede synchronní požadavky služby pro danou matematickou operaci.</span><span class="sxs-lookup"><span data-stu-id="a4230-108">The client obtains a security token from the Security Token Service (STS) and makes synchronous requests to the service for a given math operation.</span></span> <span data-ttu-id="a4230-109">Služba pak odpoví s výsledkem.</span><span class="sxs-lookup"><span data-stu-id="a4230-109">The service then replies with the result.</span></span> <span data-ttu-id="a4230-110">Aktivita klienta se zobrazí v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="a4230-110">Client activity is visible in the console window.</span></span>  
  
 <span data-ttu-id="a4230-111">Ukázka zpřístupňuje `ICalculator` kontrakt `ws2007FederationHttpBinding` pomocí elementu.</span><span class="sxs-lookup"><span data-stu-id="a4230-111">The sample makes the `ICalculator` contract available using the `ws2007FederationHttpBinding` element.</span></span> <span data-ttu-id="a4230-112">Konfigurace této vazby na klientovi je uvedena v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="a4230-112">The configuration of this binding on the client is shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="a4230-113">V [> zabezpečení hodnota určuje, který režim zabezpečení má být použit. \<](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md) `security`</span><span class="sxs-lookup"><span data-stu-id="a4230-113">On the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md), the `security` value specifies which security mode should be used.</span></span> <span data-ttu-id="a4230-114">V této ukázce `message` se používá zabezpečení, což je [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) důvod, proč je > [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md)zprávy zadán v > zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="a4230-114">In this sample, `message` security is used, which is why the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) is specified inside the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md).</span></span> <span data-ttu-id="a4230-115">Vystavitel > element ve [ \<zprávě >](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) Určuje adresu a vazbu pro službu STS, která vydá token zabezpečení pro klienta, aby se klient mohl ověřit ve `ICalculator` službě. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/issuer.md)</span><span class="sxs-lookup"><span data-stu-id="a4230-115">The [\<issuer>](../../../../docs/framework/configure-apps/file-schema/wcf/issuer.md) element inside the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) specifies the address and binding for the STS that issues a security token to the client so that the client can authenticate to the `ICalculator` service.</span></span>  
  
 <span data-ttu-id="a4230-116">Konfigurace této vazby ve službě je uvedena v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="a4230-116">The configuration of this binding on the service is shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="a4230-117">V [> zabezpečení hodnota určuje, který režim zabezpečení má být použit. \<](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md) `security`</span><span class="sxs-lookup"><span data-stu-id="a4230-117">On the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md), the `security` value specifies which security mode should be used.</span></span> <span data-ttu-id="a4230-118">V této ukázce `message` se používá zabezpečení, což je [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) důvod, proč je > [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md)zprávy zadán v > zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="a4230-118">In this sample, `message` security is used, which is why the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) is specified inside the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md).</span></span> <span data-ttu-id="a4230-119">Element [IssuerMetadata > uvnitř zprávy > Určuje adresu a identitu koncového bodu, který lze použít k načtení metadat pro službu STS. \<](../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata.md) `ws2007FederationHttpBinding` [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="a4230-119">The [\<issuerMetadata>](../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata.md) element of `ws2007FederationHttpBinding` inside the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) specifies the address and identity for an endpoint that can be used to retrieve metadata for the STS.</span></span>  
  
 <span data-ttu-id="a4230-120">Chování služby se zobrazí v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="a4230-120">The behavior for the service is shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="a4230-121">Služba [IssuedTokenAuthentication > > umožňuje službě určovat omezení pro tokeny, které umožňuje klientům prezentovat během ověřování. \<](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="a4230-121">The [\<issuedTokenAuthentication>](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)> allows the service to specify constraints on the tokens it allows clients to present during authentication.</span></span> <span data-ttu-id="a4230-122">Tato konfigurace určuje, že služba přijímá tokeny podepsané certifikátem, jehož název subjektu je CN = STS.</span><span class="sxs-lookup"><span data-stu-id="a4230-122">This configuration specifies that tokens signed by a certificate whose subject name is CN=STS are accepted by the service.</span></span>  
  
 <span data-ttu-id="a4230-123">Služba STS zpřístupňuje jeden koncový bod pomocí standardu <xref:System.ServiceModel.WS2007HttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="a4230-123">STS makes a single endpoint available using the standard <xref:System.ServiceModel.WS2007HttpBinding>.</span></span> <span data-ttu-id="a4230-124">Služba reaguje na žádosti klientů o tokeny.</span><span class="sxs-lookup"><span data-stu-id="a4230-124">The service responds to requests from clients for tokens.</span></span> <span data-ttu-id="a4230-125">Pokud je klient ověřený pomocí účtu systému Windows, služba vydá token, který obsahuje uživatelské jméno klienta jako deklaraci identity.</span><span class="sxs-lookup"><span data-stu-id="a4230-125">If the client is authenticated using a Windows account, the service issues a token that contains the client's user name as a claim.</span></span> <span data-ttu-id="a4230-126">V rámci vytváření tokenu token STS podepíše token pomocí privátního klíče přidruženého k certifikátu CN = STS.</span><span class="sxs-lookup"><span data-stu-id="a4230-126">As part of creating the token, STS signs the token using the private key associated with the CN=STS certificate.</span></span> <span data-ttu-id="a4230-127">Kromě toho vytvoří symetrický klíč a zašifruje ho pomocí veřejného klíče přidruženého k certifikátu CN = localhost.</span><span class="sxs-lookup"><span data-stu-id="a4230-127">In addition, it creates a symmetric key and encrypts it using the public key associated with the CN=localhost certificate.</span></span> <span data-ttu-id="a4230-128">Při vrácení tokenu klientovi vrátí služba tokenů zabezpečení také symetrický klíč.</span><span class="sxs-lookup"><span data-stu-id="a4230-128">In returning the token to the client, STS also returns the symmetric key.</span></span> <span data-ttu-id="a4230-129">Klient prezentuje vydaný token `ICalculator` službě a potvrzuje, že zná symetrický klíč tím, že podepisuje zprávu s tímto klíčem.</span><span class="sxs-lookup"><span data-stu-id="a4230-129">The client presents the issued token to the `ICalculator` service and proves that it knows the symmetric key by signing the message with that key.</span></span>  
  
 <span data-ttu-id="a4230-130">Při spuštění ukázky se v okně konzoly STS zobrazí požadavek na token zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="a4230-130">When you run the sample, the request for the security token is shown in the STS console window.</span></span> <span data-ttu-id="a4230-131">Požadavky a odpovědi operace operace se zobrazí v oknech konzoly klienta a služby.</span><span class="sxs-lookup"><span data-stu-id="a4230-131">The operation's requests and responses are displayed in the client and service console windows.</span></span> <span data-ttu-id="a4230-132">Ukončete aplikaci stisknutím klávesy ENTER v libovolném z oken konzoly.</span><span class="sxs-lookup"><span data-stu-id="a4230-132">Press ENTER in any of the console windows to shut down the application.</span></span>  

```
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714
Press <ENTER> to terminate client.
```

 <span data-ttu-id="a4230-133">Soubor Setup. bat, který je součástí této ukázky, vám umožní nakonfigurovat server a STS s příslušnými certifikáty pro spuštění samoobslužné aplikace.</span><span class="sxs-lookup"><span data-stu-id="a4230-133">The Setup.bat file included with this sample allows you to configure the server and STS with the relevant certificates to run a self-hosted application.</span></span> <span data-ttu-id="a4230-134">Dávkový soubor vytvoří dva certifikáty v úložišti certifikátů LocalMachine/TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="a4230-134">The batch file creates two certificates in the LocalMachine/TrustedPeople certificate store.</span></span> <span data-ttu-id="a4230-135">První certifikát má název subjektu CN = STS a používá službu STS k podepisování tokenů zabezpečení, které vystaví klientovi.</span><span class="sxs-lookup"><span data-stu-id="a4230-135">The first certificate has a subject name of CN=STS and is used by STS to sign the security tokens that it issues to the client.</span></span> <span data-ttu-id="a4230-136">Druhý certifikát má název subjektu CN = localhost a používá službu STS k šifrování klíče způsobem, který může služba dešifrovat.</span><span class="sxs-lookup"><span data-stu-id="a4230-136">The second certificate has a subject name of CN=localhost and is used by STS to encrypt a key in a way that the service can decrypt.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a4230-137">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="a4230-137">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="a4230-138">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a4230-138">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="a4230-139">Otevřete Developer Command Prompt pro Visual Studio s oprávněními správce a spuštěním souboru Setup. bat vytvořte požadované certifikáty.</span><span class="sxs-lookup"><span data-stu-id="a4230-139">Open a Developer Command Prompt for Visual Studio with administrator privileges and run the Setup.bat file to create the required certificates.</span></span>  
  
 <span data-ttu-id="a4230-140">Tento dávkový soubor používá soubory certmgr. exe a Makecert. exe, které jsou distribuovány s Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="a4230-140">This batch file uses Certmgr.exe and Makecert.exe, which are distributed with the Windows SDK.</span></span> <span data-ttu-id="a4230-141">Je však nutné spustit Setup. bat z příkazového řádku sady Visual Studio, aby skript mohl tyto nástroje najít.</span><span class="sxs-lookup"><span data-stu-id="a4230-141">However, you must run Setup.bat from within a Visual Studio  command prompt to enable the script to find these tools.</span></span>  
  
1. <span data-ttu-id="a4230-142">Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu sestavování [ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a4230-142">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="a4230-143">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a4230-143">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span> <span data-ttu-id="a4230-144">Pokud používáte [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)], musíte spustit Service. exe, Client. exe a SecurityTokenService. exe se zvýšenými oprávněními (pravým tlačítkem myši klikněte na soubory a pak klikněte na **Spustit jako správce**).</span><span class="sxs-lookup"><span data-stu-id="a4230-144">If you are using [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)], you must run Service.exe, Client.exe, and SecurityTokenService.exe with elevated privileges (right-click the files and then click **Run as administrator**).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="a4230-145">Ukázky již mohou být nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="a4230-145">The samples may already be installed on your computer.</span></span> <span data-ttu-id="a4230-146">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="a4230-146">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="a4230-147">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="a4230-147">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a4230-148">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="a4230-148">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\WS2007FederationHttp`  
