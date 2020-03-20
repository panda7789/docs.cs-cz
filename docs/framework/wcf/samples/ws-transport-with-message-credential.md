---
title: Přenos WS s pověřením zpráv
ms.date: 03/30/2017
ms.assetid: 0d092f3a-b309-439b-920b-66d8f46a0e3c
ms.openlocfilehash: 076d4490f6edc6efa8eeb50ae8baa23d5c4e369a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183148"
---
# <a name="ws-transport-with-message-credential"></a><span data-ttu-id="05573-102">Přenos WS s pověřením zpráv</span><span class="sxs-lookup"><span data-stu-id="05573-102">WS Transport With Message Credential</span></span>
<span data-ttu-id="05573-103">Tato ukázka ukazuje použití zabezpečení přenosu SSL v kombinaci s pověření klienta přenášených ve zprávě.</span><span class="sxs-lookup"><span data-stu-id="05573-103">This sample demonstrates the use of SSL transport security in combination with client credential being carried in the message.</span></span> <span data-ttu-id="05573-104">Tato ukázka `wsHttpBinding` používá vazbu.</span><span class="sxs-lookup"><span data-stu-id="05573-104">This sample uses the `wsHttpBinding` binding.</span></span>  
  
 <span data-ttu-id="05573-105">Ve výchozím `wsHttpBinding` nastavení poskytuje vazba komunikaci HTTP.</span><span class="sxs-lookup"><span data-stu-id="05573-105">By default, the `wsHttpBinding` binding provides HTTP communication.</span></span> <span data-ttu-id="05573-106">Při konfiguraci pro zabezpečení přenosu podporuje vazba komunikaci HTTPS.</span><span class="sxs-lookup"><span data-stu-id="05573-106">When configured for transport security, the binding supports HTTPS communication.</span></span> <span data-ttu-id="05573-107">Protokol HTTPS poskytuje ochranu důvěrnosti a integrity pro zprávy, které jsou přenášeny po drátě.</span><span class="sxs-lookup"><span data-stu-id="05573-107">HTTPS provides confidentiality and integrity protection for the messages that are transmitted over the wire.</span></span> <span data-ttu-id="05573-108">Sada mechanismů ověřování, které lze použít k ověření klienta ke službě je však omezena na co podporuje přenos HTTPS.</span><span class="sxs-lookup"><span data-stu-id="05573-108">However the set of authentication mechanisms that can be used to authenticate the client to the service is limited to what the HTTPS transport supports.</span></span> <span data-ttu-id="05573-109">Windows Communication Foundation (WCF) nabízí režim `TransportWithMessageCredential` zabezpečení, který je určen k překonání tohoto omezení.</span><span class="sxs-lookup"><span data-stu-id="05573-109">Windows Communication Foundation (WCF) offers a `TransportWithMessageCredential` security mode that is designed to overcome this limitation.</span></span> <span data-ttu-id="05573-110">Při konfiguraci tohoto režimu zabezpečení se zabezpečení přenosu používá k zajištění důvěrnosti a integrity přenášených zpráv a k provedení ověřování služby.</span><span class="sxs-lookup"><span data-stu-id="05573-110">When this security mode is configured, the transport security is used to provide confidentiality and integrity for the transmitted messages and to perform the service authentication.</span></span> <span data-ttu-id="05573-111">Ověřování klienta se však provádí vložením pověření klienta přímo do zprávy.</span><span class="sxs-lookup"><span data-stu-id="05573-111">However, the client authentication is performed by putting the client credential directly in the message.</span></span> <span data-ttu-id="05573-112">To umožňuje použít libovolný typ pověření, který je podporován režimem zabezpečení zpráv pro ověřování klienta při zachování výhod výkonu režimu zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="05573-112">This allows you to use any credential type that is supported by the message security mode for the client authentication while keeping the performance benefit of transport security mode.</span></span>  
  
 <span data-ttu-id="05573-113">V této ukázce se k ověření klienta ke službě používá typ `UserName` pověření.</span><span class="sxs-lookup"><span data-stu-id="05573-113">In this sample, a `UserName` credential type is used to authenticate the client to the service.</span></span>  
  
 <span data-ttu-id="05573-114">Tato ukázka je založena na [Začínáme,](../../../../docs/framework/wcf/samples/getting-started-sample.md) který implementuje službu kalkulačky.</span><span class="sxs-lookup"><span data-stu-id="05573-114">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="05573-115">Vazba `wsHttpBinding` je určena a nakonfigurována v konfiguračních souborech aplikace pro klienta a službu.</span><span class="sxs-lookup"><span data-stu-id="05573-115">The `wsHttpBinding` binding is specified and configured in the application configuration files for the client and service.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="05573-116">Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="05573-116">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="05573-117">Kód programu v ukázce je téměř totožný se službou [Začínáme.](../../../../docs/framework/wcf/samples/getting-started-sample.md)</span><span class="sxs-lookup"><span data-stu-id="05573-117">The program code in the sample is almost identical to that of the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) service.</span></span> <span data-ttu-id="05573-118">Existuje jedna další operace poskytovaná `GetCallerIdentity`servisní smlouvou - .</span><span class="sxs-lookup"><span data-stu-id="05573-118">There is one additional operation provided by the service contract - `GetCallerIdentity`.</span></span> <span data-ttu-id="05573-119">Tato operace vrátí volajícímu jméno identity volajícího.</span><span class="sxs-lookup"><span data-stu-id="05573-119">This operation returns the name of the caller's identity to the caller.</span></span>  

```csharp
public string GetCallerIdentity()  
{  
    // Use ServiceSecurityContext.WindowsIdentity to get the name of the caller.  
    return ServiceSecurityContext.Current.WindowsIdentity.Name;  
}  
```

 <span data-ttu-id="05573-120">Před sestavením a spuštěním ukázky je nutné vytvořit certifikát a přiřadit jej pomocí Průvodce certifikátem webového serveru.</span><span class="sxs-lookup"><span data-stu-id="05573-120">You must create a certificate and assign it by using the Web Server Certificate Wizard before building and running the sample.</span></span> <span data-ttu-id="05573-121">Definice koncového bodu a definice vazby `TransportWithMessageCredential` v nastavení konfiguračního souboru umožňují režim zabezpečení, jak je znázorněno v následující ukázkové konfiguraci pro klienta.</span><span class="sxs-lookup"><span data-stu-id="05573-121">The endpoint definition and binding definition in the configuration file settings enable `TransportWithMessageCredential` security mode, as shown in the following sample configuration for the client.</span></span>  
  
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
  
 <span data-ttu-id="05573-122">Zadaná adresa používá schéma https://.</span><span class="sxs-lookup"><span data-stu-id="05573-122">The address specified uses the https:// scheme.</span></span> <span data-ttu-id="05573-123">Konfigurace vazby nastaví `TransportWithMessageCredential`režim zabezpečení na .</span><span class="sxs-lookup"><span data-stu-id="05573-123">The binding configuration sets the security mode to `TransportWithMessageCredential`.</span></span> <span data-ttu-id="05573-124">Stejný režim zabezpečení musí být zadán v souboru Web.config služby.</span><span class="sxs-lookup"><span data-stu-id="05573-124">The same security mode must be specified in the service's Web.config file.</span></span>  
  
 <span data-ttu-id="05573-125">Vzhledem k tomu, že certifikát použitý v této ukázce je testovací certifikát vytvořený pomocí programu Makecert.exe, zobrazí se při pokusu o přístup k adrese https: adresa, například `https://localhost/servicemodelsamples/service.svc`, z prohlížeče.</span><span class="sxs-lookup"><span data-stu-id="05573-125">Because the certificate used in this sample is a test certificate created with Makecert.exe, a security alert appears when you try to access an https: address, such as  `https://localhost/servicemodelsamples/service.svc`, from your browser.</span></span> <span data-ttu-id="05573-126">Chcete-li povolit wcf klienta pracovat s certifikátem test na místě, některé další kód byl přidán do klienta potlačit výstrahu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="05573-126">To allow the WCF client to work with a test certificate in place, some additional code has been added to the client to suppress the security alert.</span></span> <span data-ttu-id="05573-127">Tento kód a doprovodná třída se nevyžadují při použití produkčních certifikátů.</span><span class="sxs-lookup"><span data-stu-id="05573-127">This code, and the accompanying class, is not required when using production certificates.</span></span>  

```csharp
// WARNING: This code is only needed for test certificates such as those created by makecert. It is
// not recommended for production code.  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```
  
 <span data-ttu-id="05573-128">Při spuštění ukázky jsou v okně klientské konzole zobrazeny požadavky na operaci a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="05573-128">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="05573-129">Stisknutím klávesy ENTER v okně klienta vypněte klienta.</span><span class="sxs-lookup"><span data-stu-id="05573-129">Press ENTER in the client window to shut down the client.</span></span>  
  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="05573-130">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="05573-130">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="05573-131">Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="05573-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="05573-132">Zkontrolujte, zda jste provedli [pokyny k instalaci certifikátu serveru Internetové informační služby (IIS)](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).</span><span class="sxs-lookup"><span data-stu-id="05573-132">Ensure that you have performed the [Internet Information Services (IIS) Server Certificate Installation Instructions](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).</span></span>  
  
3. <span data-ttu-id="05573-133">Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="05573-133">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="05573-134">Chcete-li spustit ukázku v konfiguraci jednoho nebo více počítačů, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="05573-134">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
