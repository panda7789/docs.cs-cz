---
title: Spolehlivá relace vlastních vazeb přes HTTPS
ms.date: 03/30/2017
ms.assetid: 16aaa80d-3ffe-47c4-8b16-ec65c4d25f8d
ms.openlocfilehash: 051e7f56662a2ca67018ae7dd29189ff50245fc8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183877"
---
# <a name="custom-binding-reliable-session-over-https"></a><span data-ttu-id="447aa-102">Spolehlivá relace vlastních vazeb přes HTTPS</span><span class="sxs-lookup"><span data-stu-id="447aa-102">Custom Binding Reliable Session over HTTPS</span></span>
<span data-ttu-id="447aa-103">Tato ukázka ukazuje použití zabezpečení přenosu SSL se spolehlivými relacemi.</span><span class="sxs-lookup"><span data-stu-id="447aa-103">This sample demonstrates the use of SSL transport security with Reliable Sessions.</span></span> <span data-ttu-id="447aa-104">Spolehlivé relace implementuje ws spolehlivé zasílání zpráv protokol.</span><span class="sxs-lookup"><span data-stu-id="447aa-104">Reliable Sessions implements the WS-Reliable Messaging protocol.</span></span> <span data-ttu-id="447aa-105">Můžete mít zabezpečené spolehlivé relace tím, že skládá WS-Security přes spolehlivé relace.</span><span class="sxs-lookup"><span data-stu-id="447aa-105">You can have a secure reliable session by composing WS-Security over Reliable Sessions.</span></span> <span data-ttu-id="447aa-106">Někdy se však můžete rozhodnout místo toho použít zabezpečení přenosu HTTP s protokolem SSL.</span><span class="sxs-lookup"><span data-stu-id="447aa-106">But sometimes, you may choose to instead use HTTP transport security with SSL.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="447aa-107">Ukázky mohou být již nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="447aa-107">The samples may already be installed on your machine.</span></span> <span data-ttu-id="447aa-108">Před pokračováním zkontrolujte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="447aa-108">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="447aa-109">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="447aa-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="447aa-110">Tato ukázka je umístěna v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="447aa-110">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Custom\ReliableSessionOverHttps`  
  
## <a name="sample-details"></a><span data-ttu-id="447aa-111">Podrobnosti ukázky</span><span class="sxs-lookup"><span data-stu-id="447aa-111">Sample Details</span></span>  
 <span data-ttu-id="447aa-112">SSL zajišťuje, že pakety samotné jsou zabezpečeny.</span><span class="sxs-lookup"><span data-stu-id="447aa-112">SSL ensures that the packets themselves are secured.</span></span> <span data-ttu-id="447aa-113">Je důležité si uvědomit, že se liší od zabezpečení spolehlivé relace pomocí konverzace WS Zabezpečené.</span><span class="sxs-lookup"><span data-stu-id="447aa-113">It is important to note that this is different from securing the reliable session using WS-Secure Conversation.</span></span>  
  
 <span data-ttu-id="447aa-114">Chcete-li použít spolehlivé relace přes protokol HTTPS, musíte vytvořit vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="447aa-114">To use reliable session over HTTPS, you must create a custom binding.</span></span> <span data-ttu-id="447aa-115">Tato ukázka je založena na [Začínáme,](../../../../docs/framework/wcf/samples/getting-started-sample.md) který implementuje službu kalkulačky.</span><span class="sxs-lookup"><span data-stu-id="447aa-115">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="447aa-116">Vlastní vazba je vytvořena pomocí elementu vazby spolehlivé relace a [ \<>httpsTransport ](../../../../docs/framework/configure-apps/file-schema/wcf/httpstransport.md).</span><span class="sxs-lookup"><span data-stu-id="447aa-116">A custom binding is created using the reliable session binding element and the [\<httpsTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/httpstransport.md).</span></span> <span data-ttu-id="447aa-117">Následující konfigurace je vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="447aa-117">The following configuration is of the custom binding.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service
          name="Microsoft.ServiceModel.Samples.CalculatorService"  
          behaviorConfiguration="CalculatorServiceBehavior">  
        <!-- use base address provided by host -->  
        <endpoint address=""  
                  binding="customBinding"  
                  bindingConfiguration="reliableSessionOverHttps"
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />  
        <!-- the mex endpoint is exposed as http://localhost/servicemodelsamples/service.svc/mex-->  
        <endpoint address="mex"  
                  binding="mexHttpBinding"  
                  contract="IMetadataExchange"/>  
      </service>  
    </services>  
  
    <bindings>  
      <customBinding>  
        <binding name="reliableSessionOverHttps">  
          <reliableSession />  
          <httpsTransport />  
        </binding>  
      </customBinding>  
    </bindings>  
  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <serviceMetadata httpGetEnabled="true" />  
          <serviceDebug includeExceptionDetailInFaults="False" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  
  </system.serviceModel>  
  
</configuration>  
```  
  
 <span data-ttu-id="447aa-118">Kód programu v ukázce je shodný se službou [Začínáme.](../../../../docs/framework/wcf/samples/getting-started-sample.md)</span><span class="sxs-lookup"><span data-stu-id="447aa-118">The program code in the sample is identical to that of the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) service.</span></span> <span data-ttu-id="447aa-119">Před sestavením a spuštěním ukázky je nutné vytvořit certifikát a přiřadit jej pomocí Průvodce certifikátem webového serveru.</span><span class="sxs-lookup"><span data-stu-id="447aa-119">You must create a certificate and assign it by using the Web Server Certificate Wizard before building and running the sample.</span></span> <span data-ttu-id="447aa-120">Definice koncového bodu a definice vazby v nastavení konfiguračního souboru umožňují použití vlastní vazby, jak je znázorněno v následující ukázkové konfiguraci pro klienta.</span><span class="sxs-lookup"><span data-stu-id="447aa-120">The endpoint definition and binding definition in the configuration file settings enable the use of custom binding as shown in the following sample configuration for the client.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
  
    <client>  
      <!-- this endpoint has an https: address -->  
      <endpoint name=""  
                address="https://localhost/servicemodelsamples/service.svc"
                binding="customBinding"
                bindingConfiguration="reliableSessionOverHttps"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    </client>  
  
      <bindings>  
        <customBinding>  
          <binding name="reliableSessionOverHttps">  
            <reliableSession />  
            <httpsTransport />  
          </binding>  
        </customBinding>
    </bindings>  
  
  </system.serviceModel>  
  
</configuration>  
```  
  
 <span data-ttu-id="447aa-121">Zadaná adresa používá schéma https://.</span><span class="sxs-lookup"><span data-stu-id="447aa-121">The address specified uses the https:// scheme.</span></span>  
  
 <span data-ttu-id="447aa-122">Vzhledem k tomu, že certifikát použitý v této ukázce je testovací certifikát vytvořený pomocí programu Makecert.exe, zobrazí se při pokusu o přístup k adrese https: adresa, například https://localhost/servicemodelsamples/service.svc, z prohlížeče.</span><span class="sxs-lookup"><span data-stu-id="447aa-122">Because the certificate used in this sample is a test certificate created with Makecert.exe, a security alert appears when you try to access an https: address, such as https://localhost/servicemodelsamples/service.svc, from your browser.</span></span> <span data-ttu-id="447aa-123">Chcete-li umožnit klientovi Windows Communication Foundation (WCF) pracovat s certifikátem test na místě, některé další kód byl přidán do klienta potlačit výstrahu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="447aa-123">To allow the Windows Communication Foundation (WCF) client to work with a test certificate in place, some additional code has been added to the client to suppress the security alert.</span></span> <span data-ttu-id="447aa-124">Tento kód a doprovodná třída se nevyžadují při použití produkčních certifikátů.</span><span class="sxs-lookup"><span data-stu-id="447aa-124">This code, and the accompanying class, is not required when using production certificates.</span></span>  

```csharp
// This code is required only for test certificates like those created by Makecert.exe.  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```

 <span data-ttu-id="447aa-125">Při spuštění ukázky jsou v okně klientské konzole zobrazeny požadavky na operaci a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="447aa-125">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="447aa-126">Stisknutím klávesy ENTER v okně klienta vypněte klienta.</span><span class="sxs-lookup"><span data-stu-id="447aa-126">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="447aa-127">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="447aa-127">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="447aa-128">Nainstalujte ASP.NET 4.0 pomocí následujícího příkazu.</span><span class="sxs-lookup"><span data-stu-id="447aa-128">Install  ASP.NET 4.0 using the following command.</span></span>  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="447aa-129">Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="447aa-129">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="447aa-130">Zkontrolujte, zda jste provedli [pokyny k instalaci certifikátu serveru Internetové informační služby (IIS)](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).</span><span class="sxs-lookup"><span data-stu-id="447aa-130">Ensure that you have performed the [Internet Information Services (IIS) Server Certificate Installation Instructions](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).</span></span>  
  
4. <span data-ttu-id="447aa-131">Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="447aa-131">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
5. <span data-ttu-id="447aa-132">Chcete-li spustit ukázku v konfiguraci jednoho nebo více počítačů, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="447aa-132">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
