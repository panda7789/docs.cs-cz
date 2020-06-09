---
title: Přenos WS s pověřením zpráv
ms.date: 03/30/2017
ms.assetid: 0d092f3a-b309-439b-920b-66d8f46a0e3c
ms.openlocfilehash: 0082a9df5c112b66315236aad91bc891b80d27c7
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596381"
---
# <a name="ws-transport-with-message-credential"></a><span data-ttu-id="13c60-102">Přenos WS s pověřením zpráv</span><span class="sxs-lookup"><span data-stu-id="13c60-102">WS Transport With Message Credential</span></span>
<span data-ttu-id="13c60-103">Tato ukázka demonstruje použití zabezpečení přenosu SSL v kombinaci s přihlašovacími údaji klienta, které jsou přenášeny ve zprávě.</span><span class="sxs-lookup"><span data-stu-id="13c60-103">This sample demonstrates the use of SSL transport security in combination with client credential being carried in the message.</span></span> <span data-ttu-id="13c60-104">Tato ukázka používá `wsHttpBinding` vazbu.</span><span class="sxs-lookup"><span data-stu-id="13c60-104">This sample uses the `wsHttpBinding` binding.</span></span>  
  
 <span data-ttu-id="13c60-105">Ve výchozím nastavení `wsHttpBinding` Vazba poskytuje komunikaci pomocí protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="13c60-105">By default, the `wsHttpBinding` binding provides HTTP communication.</span></span> <span data-ttu-id="13c60-106">Pokud je nakonfigurovaná pro zabezpečení přenosu, vazba podporuje komunikaci pomocí protokolu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="13c60-106">When configured for transport security, the binding supports HTTPS communication.</span></span> <span data-ttu-id="13c60-107">Protokol HTTPS poskytuje ochranu proti utajení a integritě zpráv, které jsou přenášeny přes drát.</span><span class="sxs-lookup"><span data-stu-id="13c60-107">HTTPS provides confidentiality and integrity protection for the messages that are transmitted over the wire.</span></span> <span data-ttu-id="13c60-108">Sada ověřovacích mechanismů, které lze použít k ověření klienta ke službě, je však omezená na to, co podporuje přenos HTTPS.</span><span class="sxs-lookup"><span data-stu-id="13c60-108">However the set of authentication mechanisms that can be used to authenticate the client to the service is limited to what the HTTPS transport supports.</span></span> <span data-ttu-id="13c60-109">Windows Communication Foundation (WCF) nabízí `TransportWithMessageCredential` režim zabezpečení, který je navržený k překonání tohoto omezení.</span><span class="sxs-lookup"><span data-stu-id="13c60-109">Windows Communication Foundation (WCF) offers a `TransportWithMessageCredential` security mode that is designed to overcome this limitation.</span></span> <span data-ttu-id="13c60-110">Pokud je tento režim zabezpečení nakonfigurovaný, použije se k zajištění důvěrnosti a integrity odesílaných zpráv a k provedení ověření služby zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="13c60-110">When this security mode is configured, the transport security is used to provide confidentiality and integrity for the transmitted messages and to perform the service authentication.</span></span> <span data-ttu-id="13c60-111">Ověřování klienta se ale provádí tak, že přihlašovací údaje klienta vložíte přímo do zprávy.</span><span class="sxs-lookup"><span data-stu-id="13c60-111">However, the client authentication is performed by putting the client credential directly in the message.</span></span> <span data-ttu-id="13c60-112">To vám umožní používat libovolný typ přihlašovacích údajů, který je podporovaný režimem zabezpečení zpráv pro ověřování klientů, a přitom zachovat výhody režimu zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="13c60-112">This allows you to use any credential type that is supported by the message security mode for the client authentication while keeping the performance benefit of transport security mode.</span></span>  
  
 <span data-ttu-id="13c60-113">V této ukázce se k `UserName` ověření klienta pro službu používá typ přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="13c60-113">In this sample, a `UserName` credential type is used to authenticate the client to the service.</span></span>  
  
 <span data-ttu-id="13c60-114">Tato ukázka je založená na [Začínáme](getting-started-sample.md) , která implementuje službu kalkulačky.</span><span class="sxs-lookup"><span data-stu-id="13c60-114">This sample is based on the [Getting Started](getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="13c60-115">`wsHttpBinding`Vazba je určena a nakonfigurována v konfiguračních souborech aplikace pro klienta a službu.</span><span class="sxs-lookup"><span data-stu-id="13c60-115">The `wsHttpBinding` binding is specified and configured in the application configuration files for the client and service.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="13c60-116">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="13c60-116">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="13c60-117">Kód programu v ukázce je skoro stejný jako služba [Začínáme](getting-started-sample.md) .</span><span class="sxs-lookup"><span data-stu-id="13c60-117">The program code in the sample is almost identical to that of the [Getting Started](getting-started-sample.md) service.</span></span> <span data-ttu-id="13c60-118">Kontrakt služby poskytuje ještě jednu další operaci – `GetCallerIdentity` .</span><span class="sxs-lookup"><span data-stu-id="13c60-118">There is one additional operation provided by the service contract - `GetCallerIdentity`.</span></span> <span data-ttu-id="13c60-119">Tato operace vrátí název volajícího volajícímu.</span><span class="sxs-lookup"><span data-stu-id="13c60-119">This operation returns the name of the caller's identity to the caller.</span></span>  

```csharp
public string GetCallerIdentity()  
{  
    // Use ServiceSecurityContext.WindowsIdentity to get the name of the caller.  
    return ServiceSecurityContext.Current.WindowsIdentity.Name;  
}  
```

 <span data-ttu-id="13c60-120">Před vytvořením a spuštěním ukázky musíte vytvořit certifikát a přiřadit ho pomocí Průvodce certifikátem webového serveru.</span><span class="sxs-lookup"><span data-stu-id="13c60-120">You must create a certificate and assign it by using the Web Server Certificate Wizard before building and running the sample.</span></span> <span data-ttu-id="13c60-121">Definice koncového bodu a definice vazby v nastavení konfiguračního souboru umožňují `TransportWithMessageCredential` režim zabezpečení, jak je znázorněno v následující ukázkové konfiguraci pro klienta.</span><span class="sxs-lookup"><span data-stu-id="13c60-121">The endpoint definition and binding definition in the configuration file settings enable `TransportWithMessageCredential` security mode, as shown in the following sample configuration for the client.</span></span>  
  
```xml  
<system.serviceModel>  
  <client>  
    <endpoint name=""  
              address="https://localhost/servicemodelsamples/service.svc"
              binding="wsHttpBinding"
              bindingConfiguration="Binding1"
              contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  </client>  
  
  <bindings>  
    <wsHttpBinding>  
      <!--   
        This configuration defines the security mode as TransportWithMessageCredential.  
        and the clientCredentialType as UserName.  
        -->  
      <binding name="Binding1">  
        <security mode ="TransportWithMessageCredential">  
          <message clientCredentialType="UserName" />  
        </security>  
      </binding>  
    </wsHttpBinding>  
  </bindings>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="13c60-122">Zadaná adresa používá `https://` schéma.</span><span class="sxs-lookup"><span data-stu-id="13c60-122">The address specified uses the `https://` scheme.</span></span> <span data-ttu-id="13c60-123">Konfigurace vazby nastaví režim zabezpečení na `TransportWithMessageCredential` .</span><span class="sxs-lookup"><span data-stu-id="13c60-123">The binding configuration sets the security mode to `TransportWithMessageCredential`.</span></span> <span data-ttu-id="13c60-124">V souboru Web. config služby musí být zadaný stejný režim zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="13c60-124">The same security mode must be specified in the service's Web.config file.</span></span>  
  
 <span data-ttu-id="13c60-125">Vzhledem k tomu, že certifikát použitý v této ukázce je testovací certifikát vytvořený pomocí nástroje MakeCert. exe, zobrazí se výstraha zabezpečení při pokusu o přístup k protokolu https: adresa, například `https://localhost/servicemodelsamples/service.svc` , z prohlížeče.</span><span class="sxs-lookup"><span data-stu-id="13c60-125">Because the certificate used in this sample is a test certificate created with Makecert.exe, a security alert appears when you try to access an https: address, such as  `https://localhost/servicemodelsamples/service.svc`, from your browser.</span></span> <span data-ttu-id="13c60-126">Aby mohl klient služby WCF pracovat s testovacím certifikátem, byl do klienta přidán nějaký další kód, který výstrahu zabezpečení potlačí.</span><span class="sxs-lookup"><span data-stu-id="13c60-126">To allow the WCF client to work with a test certificate in place, some additional code has been added to the client to suppress the security alert.</span></span> <span data-ttu-id="13c60-127">Tento kód a doprovodná třída nejsou při použití produkčních certifikátů vyžadovány.</span><span class="sxs-lookup"><span data-stu-id="13c60-127">This code, and the accompanying class, is not required when using production certificates.</span></span>  

```csharp
// WARNING: This code is only needed for test certificates such as those created by makecert. It is
// not recommended for production code.  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```
  
 <span data-ttu-id="13c60-128">Při spuštění ukázky se v okně konzoly klienta zobrazí požadavky na operace a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="13c60-128">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="13c60-129">V okně klienta stiskněte klávesu ENTER pro vypnutí klienta.</span><span class="sxs-lookup"><span data-stu-id="13c60-129">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Username authentication required.  
Provide a valid machine or domain account. [domain\\user]  
   Enter username:
YourDomainName\YourAccountName  
   Enter password:
********  
YourDomainName\YourAccountName  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="13c60-130">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="13c60-130">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="13c60-131">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="13c60-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="13c60-132">Ujistěte se, že jste provedli [pokyny k instalaci certifikátu serveru Internetová informační služba (IIS)](iis-server-certificate-installation-instructions.md).</span><span class="sxs-lookup"><span data-stu-id="13c60-132">Ensure that you have performed the [Internet Information Services (IIS) Server Certificate Installation Instructions](iis-server-certificate-installation-instructions.md).</span></span>  
  
3. <span data-ttu-id="13c60-133">Chcete-li sestavit edici C# nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="13c60-133">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="13c60-134">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="13c60-134">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
