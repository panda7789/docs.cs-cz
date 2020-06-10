---
title: Zabezpečení přenosu WS
ms.date: 03/30/2017
ms.assetid: 33a20358-5e1b-458a-a6a9-15753bc7b99b
ms.openlocfilehash: d0f357ddcfc355bac8eeb86d57641add0013a052
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596394"
---
# <a name="ws-transport-security"></a><span data-ttu-id="f12f8-102">Zabezpečení přenosu WS</span><span class="sxs-lookup"><span data-stu-id="f12f8-102">WS Transport Security</span></span>
<span data-ttu-id="f12f8-103">Tato ukázka demonstruje použití zabezpečení přenosu SSL s <xref:System.ServiceModel.WSHttpBinding> vazbou.</span><span class="sxs-lookup"><span data-stu-id="f12f8-103">This sample demonstrates the use of SSL transport security with the <xref:System.ServiceModel.WSHttpBinding> binding.</span></span> <span data-ttu-id="f12f8-104">Ve výchozím nastavení `wsHttpBinding` Vazba poskytuje komunikaci pomocí protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="f12f8-104">By default, the `wsHttpBinding` binding provides HTTP communication.</span></span> <span data-ttu-id="f12f8-105">Pokud je nakonfigurovaná pro zabezpečení přenosu, vazba podporuje komunikaci pomocí protokolu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="f12f8-105">When configured for transport security, the binding supports HTTPS communication.</span></span> <span data-ttu-id="f12f8-106">Tato ukázka je založená na [Začínáme](getting-started-sample.md) , která implementuje službu kalkulačky.</span><span class="sxs-lookup"><span data-stu-id="f12f8-106">This sample is based on the [Getting Started](getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="f12f8-107">`wsHttpBinding`Je určen a nakonfigurován v konfiguračních souborech aplikace pro klienta a službu.</span><span class="sxs-lookup"><span data-stu-id="f12f8-107">The `wsHttpBinding` is specified and configured in the application configuration files for the client and service.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f12f8-108">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="f12f8-108">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="f12f8-109">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="f12f8-109">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f12f8-110">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="f12f8-110">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="f12f8-111">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="f12f8-111">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f12f8-112">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="f12f8-112">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsTransportSecurity`  
  
 <span data-ttu-id="f12f8-113">Kód programu v ukázce je stejný jako u služby [Začínáme](getting-started-sample.md) .</span><span class="sxs-lookup"><span data-stu-id="f12f8-113">The program code in the sample is identical to that of the [Getting Started](getting-started-sample.md) service.</span></span> <span data-ttu-id="f12f8-114">Před vytvořením a spuštěním ukázky musíte vytvořit certifikát a přiřadit ho pomocí Průvodce certifikátem webového serveru.</span><span class="sxs-lookup"><span data-stu-id="f12f8-114">You must create a certificate and assign it by using the Web Server Certificate Wizard before building and running the sample.</span></span> <span data-ttu-id="f12f8-115">Definice koncového bodu a definice vazby v nastavení konfiguračního souboru umožňují `Transport` režim zabezpečení, jak je znázorněno v následující ukázkové konfiguraci pro klienta.</span><span class="sxs-lookup"><span data-stu-id="f12f8-115">The endpoint definition and binding definition in the configuration file settings enable `Transport` security mode, as shown in the following sample configuration for the client.</span></span>  
  
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
  
 <span data-ttu-id="f12f8-116">Zadaná adresa používá `https://` schéma.</span><span class="sxs-lookup"><span data-stu-id="f12f8-116">The address specified uses the `https://` scheme.</span></span> <span data-ttu-id="f12f8-117">Konfigurace vazby nastaví režim zabezpečení na `Transport` .</span><span class="sxs-lookup"><span data-stu-id="f12f8-117">The binding configuration sets the security mode to `Transport`.</span></span> <span data-ttu-id="f12f8-118">V souboru Web. config služby musí být zadaný stejný režim zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="f12f8-118">The same security mode must be specified in the service's Web.config file.</span></span>  
  
 <span data-ttu-id="f12f8-119">Vzhledem k tomu, že certifikát použitý v této ukázce je testovací certifikát vytvořený pomocí nástroje MakeCert. exe, zobrazí se výstraha zabezpečení při pokusu o přístup k protokolu https: adresa, například `https://localhost/servicemodelsamples/service.svc` , z prohlížeče.</span><span class="sxs-lookup"><span data-stu-id="f12f8-119">Because the certificate used in this sample is a test certificate created with Makecert.exe, a security alert appears when you try to access an https: address, such as `https://localhost/servicemodelsamples/service.svc`, from your browser.</span></span> <span data-ttu-id="f12f8-120">Aby mohl klient služby Windows Communication Foundation (WCF) pracovat s testovacím certifikátem, byl do klienta přidán nějaký další kód pro potlačení výstrahy zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="f12f8-120">To allow the Windows Communication Foundation (WCF) client to work with a test certificate in place, some additional code has been added to the client to suppress the security alert.</span></span> <span data-ttu-id="f12f8-121">Tento kód a doprovodná třída nejsou při použití produkčních certifikátů vyžadovány.</span><span class="sxs-lookup"><span data-stu-id="f12f8-121">This code, and the accompanying class, is not required when using production certificates.</span></span>  

```csharp
// This code is required only for test certificates like those created by Makecert.exe.  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```

 <span data-ttu-id="f12f8-122">Při spuštění ukázky se v okně konzoly klienta zobrazí požadavky na operace a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="f12f8-122">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="f12f8-123">V okně klienta stiskněte klávesu ENTER pro vypnutí klienta.</span><span class="sxs-lookup"><span data-stu-id="f12f8-123">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="f12f8-124">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="f12f8-124">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="f12f8-125">Pomocí následujícího příkazu nainstalujte ASP.NET 4,0.</span><span class="sxs-lookup"><span data-stu-id="f12f8-125">Install ASP.NET 4.0 using the following command.</span></span>  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="f12f8-126">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f12f8-126">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="f12f8-127">Ujistěte se, že jste provedli [pokyny k instalaci certifikátu serveru Internetová informační služba (IIS)](iis-server-certificate-installation-instructions.md).</span><span class="sxs-lookup"><span data-stu-id="f12f8-127">Ensure that you have performed the [Internet Information Services (IIS) Server Certificate Installation Instructions](iis-server-certificate-installation-instructions.md).</span></span>  
  
4. <span data-ttu-id="f12f8-128">Chcete-li sestavit edici C# nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f12f8-128">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
5. <span data-ttu-id="f12f8-129">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f12f8-129">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
