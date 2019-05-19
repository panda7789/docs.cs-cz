---
title: Spolehlivá relace vlastních vazeb přes HTTPS
ms.date: 03/30/2017
ms.assetid: 16aaa80d-3ffe-47c4-8b16-ec65c4d25f8d
ms.openlocfilehash: a5d697c1649499f2be6b3ab1f69348065db59df8
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2019
ms.locfileid: "65878446"
---
# <a name="custom-binding-reliable-session-over-https"></a><span data-ttu-id="bcd2a-102">Spolehlivá relace vlastních vazeb přes HTTPS</span><span class="sxs-lookup"><span data-stu-id="bcd2a-102">Custom Binding Reliable Session over HTTPS</span></span>
<span data-ttu-id="bcd2a-103">Tento příklad ukazuje použití zabezpečení přenosu SSL pomocí spolehlivé relace.</span><span class="sxs-lookup"><span data-stu-id="bcd2a-103">This sample demonstrates the use of SSL transport security with Reliable Sessions.</span></span> <span data-ttu-id="bcd2a-104">Spolehlivé relace implementuje protokol zasílání zpráv WS-Reliable.</span><span class="sxs-lookup"><span data-stu-id="bcd2a-104">Reliable Sessions implements the WS-Reliable Messaging protocol.</span></span> <span data-ttu-id="bcd2a-105">Využitím WS-Security spolehlivých relací může mít zabezpečené stabilní relace.</span><span class="sxs-lookup"><span data-stu-id="bcd2a-105">You can have a secure reliable session by composing WS-Security over Reliable Sessions.</span></span> <span data-ttu-id="bcd2a-106">Ale v některých případech můžete místo toho použijte zabezpečení přenosu HTTP s protokolem SSL.</span><span class="sxs-lookup"><span data-stu-id="bcd2a-106">But sometimes, you may choose to instead use HTTP transport security with SSL.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="bcd2a-107">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="bcd2a-107">The samples may already be installed on your machine.</span></span> <span data-ttu-id="bcd2a-108">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="bcd2a-108">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="bcd2a-109">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="bcd2a-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="bcd2a-110">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="bcd2a-110">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Custom\ReliableSessionOverHttps`  
  
## <a name="sample-details"></a><span data-ttu-id="bcd2a-111">Ukázka podrobnosti</span><span class="sxs-lookup"><span data-stu-id="bcd2a-111">Sample Details</span></span>  
 <span data-ttu-id="bcd2a-112">Protokol SSL zajišťuje, že jsou pakety sami zabezpečené.</span><span class="sxs-lookup"><span data-stu-id="bcd2a-112">SSL ensures that the packets themselves are secured.</span></span> <span data-ttu-id="bcd2a-113">Je důležité si uvědomit, že se liší od zabezpečení ve stabilní relaci pomocí WS-Secure Conversation.</span><span class="sxs-lookup"><span data-stu-id="bcd2a-113">It is important to note that this is different from securing the reliable session using WS-Secure Conversation.</span></span>  
  
 <span data-ttu-id="bcd2a-114">Pokud chcete použít stabilní relace přes protokol HTTPS, musíte vytvořit vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="bcd2a-114">To use reliable session over HTTPS, you must create a custom binding.</span></span> <span data-ttu-id="bcd2a-115">Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) službu kalkulačky, která implementuje.</span><span class="sxs-lookup"><span data-stu-id="bcd2a-115">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="bcd2a-116">Vytvoření vlastní vazby pomocí elementu vazby stabilní relace a [ \<httpsTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httpstransport.md).</span><span class="sxs-lookup"><span data-stu-id="bcd2a-116">A custom binding is created using the reliable session binding element and the [\<httpsTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/httpstransport.md).</span></span> <span data-ttu-id="bcd2a-117">Následující konfigurace je pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="bcd2a-117">The following configuration is of the custom binding.</span></span>  
  
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
  
 <span data-ttu-id="bcd2a-118">Programového kódu v ukázce je shodná s [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) služby.</span><span class="sxs-lookup"><span data-stu-id="bcd2a-118">The program code in the sample is identical to that of the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) service.</span></span> <span data-ttu-id="bcd2a-119">Musíte vytvořit certifikát a přiřaďte ho pomocí Průvodce certifikát webového serveru před sestavováním a spouštěním vzorku.</span><span class="sxs-lookup"><span data-stu-id="bcd2a-119">You must create a certificate and assign it by using the Web Server Certificate Wizard before building and running the sample.</span></span> <span data-ttu-id="bcd2a-120">Definice koncového bodu a vazby definice v souboru nastavení konfigurace povolit použití vlastní vazby, jak je znázorněno v následující ukázková konfigurace pro klienta.</span><span class="sxs-lookup"><span data-stu-id="bcd2a-120">The endpoint definition and binding definition in the configuration file settings enable the use of custom binding as shown in the following sample configuration for the client.</span></span>  
  
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
  
 <span data-ttu-id="bcd2a-121">Zadaná adresa používá schéma https://.</span><span class="sxs-lookup"><span data-stu-id="bcd2a-121">The address specified uses the https:// scheme.</span></span>  
  
 <span data-ttu-id="bcd2a-122">Vzhledem k tomu, že certifikát použitý v této ukázce je testovací certifikát vytvořen s Makecert.exe, výstrahu zabezpečení se zobrazí při pokusu o přístup protokolu https: adresy, jako například https://localhost/servicemodelsamples/service.svc, v prohlížeči.</span><span class="sxs-lookup"><span data-stu-id="bcd2a-122">Because the certificate used in this sample is a test certificate created with Makecert.exe, a security alert appears when you try to access an https: address, such as https://localhost/servicemodelsamples/service.svc, from your browser.</span></span> <span data-ttu-id="bcd2a-123">Povolit klienta Windows Communication Foundation (WCF) se službou testovací certifikát na místě, byla přidána další kód klienta pro potlačení výstrahy zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="bcd2a-123">To allow the Windows Communication Foundation (WCF) client to work with a test certificate in place, some additional code has been added to the client to suppress the security alert.</span></span> <span data-ttu-id="bcd2a-124">Tento kód a související třídy se nevyžaduje při použití certifikátů produkčního prostředí.</span><span class="sxs-lookup"><span data-stu-id="bcd2a-124">This code, and the accompanying class, is not required when using production certificates.</span></span>  

```csharp
// This code is required only for test certificates like those created by Makecert.exe.  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```

 <span data-ttu-id="bcd2a-125">Při spuštění ukázky operace žádosti a odpovědi se zobrazí v okně konzoly klienta.</span><span class="sxs-lookup"><span data-stu-id="bcd2a-125">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="bcd2a-126">Stisknutím klávesy ENTER v okně Klient vypnutí klient.</span><span class="sxs-lookup"><span data-stu-id="bcd2a-126">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="bcd2a-127">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="bcd2a-127">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="bcd2a-128">Instalace technologie ASP.NET 4.0 pomocí následujícího příkazu.</span><span class="sxs-lookup"><span data-stu-id="bcd2a-128">Install  ASP.NET 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="bcd2a-129">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="bcd2a-129">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="bcd2a-130">Ujistěte se, že jste provedli [pokyny k instalaci certifikátu serveru Internetové informační služby (IIS)](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).</span><span class="sxs-lookup"><span data-stu-id="bcd2a-130">Ensure that you have performed the [Internet Information Services (IIS) Server Certificate Installation Instructions](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).</span></span>  
  
4. <span data-ttu-id="bcd2a-131">K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="bcd2a-131">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
5. <span data-ttu-id="bcd2a-132">Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="bcd2a-132">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
