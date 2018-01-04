---
title: "Základní vazby u zabezpečení přenosu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f49b1de6-0254-4362-8ef2-fccd8ff9688b
caps.latest.revision: "26"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 2a65adbb908aded9f4124f473f0b298d573a521f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="basicbinding-with-transport-security"></a><span data-ttu-id="88e5d-102">Základní vazby u zabezpečení přenosu</span><span class="sxs-lookup"><span data-stu-id="88e5d-102">BasicBinding with Transport Security</span></span>
<span data-ttu-id="88e5d-103">Tento příklad znázorňuje použití protokolu SSL zabezpečení přenosu s základní vazby.</span><span class="sxs-lookup"><span data-stu-id="88e5d-103">This sample demonstrates the use of SSL transport security with the basic binding.</span></span> <span data-ttu-id="88e5d-104">Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) službu kalkulačky, která implementuje.</span><span class="sxs-lookup"><span data-stu-id="88e5d-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="88e5d-105">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="88e5d-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="88e5d-106">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="88e5d-106">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="88e5d-107">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="88e5d-107">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="88e5d-108">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="88e5d-108">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Basic\TransportSecurity`  
  
## <a name="sample-details"></a><span data-ttu-id="88e5d-109">Ukázka podrobnosti</span><span class="sxs-lookup"><span data-stu-id="88e5d-109">Sample Details</span></span>  
 <span data-ttu-id="88e5d-110">Základní vazby ve výchozím nastavení podporuje komunikaci prostřednictvím protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="88e5d-110">By default, the basic binding supports HTTP communication.</span></span> <span data-ttu-id="88e5d-111">Ukázka ukazuje, jak povolit zabezpečení přenosu pro základní vazby.</span><span class="sxs-lookup"><span data-stu-id="88e5d-111">The sample shows how to enable transport security for the basic binding.</span></span> <span data-ttu-id="88e5d-112">Před spuštěním ukázky, musíte vytvořit certifikát a přiřaďte ho pomocí Průvodce certifikátem webového serveru.</span><span class="sxs-lookup"><span data-stu-id="88e5d-112">Before you run the sample, you must create a certificate and assign it by using the Web Server Certificate Wizard.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="88e5d-113">V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="88e5d-113">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="88e5d-114">Program kód v ukázce je shodná s [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) služby.</span><span class="sxs-lookup"><span data-stu-id="88e5d-114">The program code in the sample is identical to that of the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) service.</span></span> <span data-ttu-id="88e5d-115">Definice koncového bodu a vazba definice v souboru nastavení konfigurace jsou upravit pro zajištění zabezpečené komunikace, jak je znázorněno v následující ukázka konfigurace.</span><span class="sxs-lookup"><span data-stu-id="88e5d-115">The endpoint definition and binding definition in the configuration file settings are modified to enable secure communication, as shown in the following sample configuration.</span></span>  
  
```xml  
<system.serviceModel>  
  <services>  
    <service type="Microsoft.ServiceModel.Samples.CalculatorService"  
             behaviorConfiguration="CalculatorServiceBehavior">  
      <endpoint address=""  
                binding="basicHttpBinding"  
                bindingConfiguration="Binding1"   
                contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    </service>  
   </services>  
  <bindings>  
    <basicHttpBinding>  
      <!-- Configure basicHttpBinding with Transport security -- >  
      <!-- mode and clientCredentialType set to None.-->  
      <binding name="Binding1">  
        <security mode="Transport">  
          <transport clientCredentialType="None"/>  
        </security>  
      </binding>  
    </basicHttpBinding>  
  </bindings>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="88e5d-116">Vzhledem k tomu, že certifikát použitý v této ukázce je testovací certifikát vytvořen s Makecert.exe, zobrazí se výstraha zabezpečení při pokusu o přístup protokolu HTTPS: adresa v prohlížeči, jako je například https://localhost/servicemodelsamples/service.svc.</span><span class="sxs-lookup"><span data-stu-id="88e5d-116">Because the certificate used in this sample is a test certificate created with Makecert.exe, a security alert appears when you try to access an HTTPS: address in your browser, such as https://localhost/servicemodelsamples/service.svc.</span></span> <span data-ttu-id="88e5d-117">Chcete-li povolit [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] klienta pro práci s testovacím certifikátem, některé další kód se přidá do klienta pro potlačení výstrahy zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="88e5d-117">To allow the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] client to work with a test certificate, some additional code is added to the client to suppress the security alert.</span></span> <span data-ttu-id="88e5d-118">Při použití skutečné certifikátů, tento kód a doprovodné třída, není nutné.</span><span class="sxs-lookup"><span data-stu-id="88e5d-118">This code, and the accompanying class, is not necessary when using real certificates.</span></span>  
  
```  
// This code is required only for test certificates such as those   
// created by Makecert.exe.  
PermissiveCertificatePolicy.Enact(  
                           "CN=ServiceModelSamples-HTTPS-Server");  
```  
  
 <span data-ttu-id="88e5d-119">Když spustíte ukázku, operace požadavky a odpovědi se zobrazí v okně konzoly klienta.</span><span class="sxs-lookup"><span data-stu-id="88e5d-119">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="88e5d-120">Stisknutím klávesy ENTER v okně klienta vypnout klienta.</span><span class="sxs-lookup"><span data-stu-id="88e5d-120">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="88e5d-121">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="88e5d-121">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="88e5d-122">Nainstalujte [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 pomocí následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="88e5d-122">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command:</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  <span data-ttu-id="88e5d-123">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="88e5d-123">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3.  <span data-ttu-id="88e5d-124">Ujistěte se, že jste provedli [pokyny k instalaci certifikátu serveru Internetové informační služby (IIS)](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).</span><span class="sxs-lookup"><span data-stu-id="88e5d-124">Ensure that you have performed the [Internet Information Services (IIS) Server Certificate Installation Instructions](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).</span></span>  
  
4.  <span data-ttu-id="88e5d-125">Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="88e5d-125">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
5.  <span data-ttu-id="88e5d-126">Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="88e5d-126">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88e5d-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="88e5d-127">See Also</span></span>
