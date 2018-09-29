---
title: Zabezpečení přenosu WS
ms.date: 03/30/2017
ms.assetid: 33a20358-5e1b-458a-a6a9-15753bc7b99b
author: BrucePerlerMS
ms.openlocfilehash: 99f8e038657a620de56d1d759a95bbbdf93b1ed4
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/29/2018
ms.locfileid: "47454299"
---
# <a name="ws-transport-security"></a><span data-ttu-id="f7916-102">Zabezpečení přenosu WS</span><span class="sxs-lookup"><span data-stu-id="f7916-102">WS Transport Security</span></span>
<span data-ttu-id="f7916-103">Tato ukázka demonstruje použití zabezpečení přenosu SSL pomocí <xref:System.ServiceModel.WSHttpBinding> vazby.</span><span class="sxs-lookup"><span data-stu-id="f7916-103">This sample demonstrates the use of SSL transport security with the <xref:System.ServiceModel.WSHttpBinding> binding.</span></span> <span data-ttu-id="f7916-104">Ve výchozím nastavení `wsHttpBinding` vazby poskytuje komunikaci pomocí protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="f7916-104">By default, the `wsHttpBinding` binding provides HTTP communication.</span></span> <span data-ttu-id="f7916-105">Když je nakonfigurován pro zabezpečení přenosu, vazba podporuje komunikaci přes protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="f7916-105">When configured for transport security, the binding supports HTTPS communication.</span></span> <span data-ttu-id="f7916-106">Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) službu kalkulačky, která implementuje.</span><span class="sxs-lookup"><span data-stu-id="f7916-106">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="f7916-107">`wsHttpBinding` Je zadán a nakonfigurovat v konfiguračních souborech aplikace pro klienta a služby.</span><span class="sxs-lookup"><span data-stu-id="f7916-107">The `wsHttpBinding` is specified and configured in the application configuration files for the client and service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f7916-108">Postupu a sestavení pokyny k instalaci pro tuto ukázku se nachází na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="f7916-108">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f7916-109">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="f7916-109">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f7916-110">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="f7916-110">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="f7916-111">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="f7916-111">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f7916-112">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="f7916-112">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsTransportSecurity`  
  
 <span data-ttu-id="f7916-113">Programového kódu v ukázce je shodná s [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) služby.</span><span class="sxs-lookup"><span data-stu-id="f7916-113">The program code in the sample is identical to that of the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) service.</span></span> <span data-ttu-id="f7916-114">Musíte vytvořit certifikát a přiřaďte ho pomocí Průvodce certifikát webového serveru před sestavováním a spouštěním vzorku.</span><span class="sxs-lookup"><span data-stu-id="f7916-114">You must create a certificate and assign it by using the Web Server Certificate Wizard before building and running the sample.</span></span> <span data-ttu-id="f7916-115">Definice koncového bodu a definice vazby v konfiguraci souboru nastavení Povolit `Transport` režim zabezpečení, jak je znázorněno v následující ukázková konfigurace pro klienta.</span><span class="sxs-lookup"><span data-stu-id="f7916-115">The endpoint definition and binding definition in the configuration file settings enable `Transport` security mode, as shown in the following sample configuration for the client.</span></span>  
  
```xml  
<system.serviceModel>  
  
    <client>  
      <!-- this endpoint has an https: address -->  
      <endpoint address="https://localhost/servicemodelsamples/service.svc" binding="wsHttpBinding" bindingConfiguration="Binding1" contract="Microsoft.Samples.TransportSecurity.ICalculator"/>  
    </client>  
  
    <bindings>  
      <wsHttpBinding>  
        <!-- configure wsHttpbinding with Transport security mode  
                   and clientCredentialType as None -->  
        <binding name="Binding1">  
          <security mode="Transport">  
            <transport clientCredentialType="None"/>  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
  
  </system.serviceModel>  
```  
  
 <span data-ttu-id="f7916-116">Zadaná adresa používá schéma https://.</span><span class="sxs-lookup"><span data-stu-id="f7916-116">The address specified uses the https:// scheme.</span></span> <span data-ttu-id="f7916-117">Konfigurace vazby nastaví režim zabezpečení na `Transport`.</span><span class="sxs-lookup"><span data-stu-id="f7916-117">The binding configuration sets the security mode to `Transport`.</span></span> <span data-ttu-id="f7916-118">Stejný režim zabezpečení musí být zadaný v souboru Web.config dané služby.</span><span class="sxs-lookup"><span data-stu-id="f7916-118">The same security mode must be specified in the service's Web.config file.</span></span>  
  
 <span data-ttu-id="f7916-119">Vzhledem k tomu, že certifikát použitý v této ukázce je testovací certifikát vytvořen s Makecert.exe, výstrahu zabezpečení se zobrazí při pokusu o přístup protokolu https: adresy, jako například https://localhost/servicemodelsamples/service.svc, v prohlížeči.</span><span class="sxs-lookup"><span data-stu-id="f7916-119">Because the certificate used in this sample is a test certificate created with Makecert.exe, a security alert appears when you try to access an https: address, such as https://localhost/servicemodelsamples/service.svc, from your browser.</span></span> <span data-ttu-id="f7916-120">Povolit klienta Windows Communication Foundation (WCF) se službou testovací certifikát na místě, byla přidána další kód klienta pro potlačení výstrahy zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="f7916-120">To allow the Windows Communication Foundation (WCF) client to work with a test certificate in place, some additional code has been added to the client to suppress the security alert.</span></span> <span data-ttu-id="f7916-121">Tento kód a související třídy se nevyžaduje při použití certifikátů produkčního prostředí.</span><span class="sxs-lookup"><span data-stu-id="f7916-121">This code, and the accompanying class, is not required when using production certificates.</span></span>  

```csharp
// This code is required only for test certificates like those created by Makecert.exe.  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```

 <span data-ttu-id="f7916-122">Při spuštění ukázky operace žádosti a odpovědi se zobrazí v okně konzoly klienta.</span><span class="sxs-lookup"><span data-stu-id="f7916-122">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="f7916-123">Stisknutím klávesy ENTER v okně Klient vypnutí klient.</span><span class="sxs-lookup"><span data-stu-id="f7916-123">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="f7916-124">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="f7916-124">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="f7916-125">Nainstalujte [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 pomocí následujícího příkazu.</span><span class="sxs-lookup"><span data-stu-id="f7916-125">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  <span data-ttu-id="f7916-126">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f7916-126">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3.  <span data-ttu-id="f7916-127">Ujistěte se, že jste provedli [pokyny k instalaci certifikátu serveru Internetové informační služby (IIS)](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).</span><span class="sxs-lookup"><span data-stu-id="f7916-127">Ensure that you have performed the [Internet Information Services (IIS) Server Certificate Installation Instructions](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).</span></span>  
  
4.  <span data-ttu-id="f7916-128">K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f7916-128">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
5.  <span data-ttu-id="f7916-129">Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f7916-129">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7916-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="f7916-130">See Also</span></span>
