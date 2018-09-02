---
title: Víc kontraktů
ms.date: 03/30/2017
ms.assetid: 2bef319b-fe9c-4d49-ac6c-dfb23eb35099
ms.openlocfilehash: 040ab9b80e9567139ca4588e3ddf83b8f43f2d76
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43392449"
---
# <a name="multiple-contracts"></a><span data-ttu-id="20e05-102">Víc kontraktů</span><span class="sxs-lookup"><span data-stu-id="20e05-102">Multiple Contracts</span></span>
<span data-ttu-id="20e05-103">Více kontraktů Ukázka předvádí, jak implementovat více než jeden kontrakt na služby a jak nakonfigurovat koncové body pro komunikaci s každým implementovaných kontraktů.</span><span class="sxs-lookup"><span data-stu-id="20e05-103">The Multiple Contracts sample demonstrates how to implement more than one contract on a service and how to configure endpoints for communicating with each of the implemented contracts.</span></span> <span data-ttu-id="20e05-104">Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="20e05-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="20e05-105">Služba byla změněna definovat dva kontrakty `ICalculator` smlouvy a `ICalculatorSession` kontraktu.</span><span class="sxs-lookup"><span data-stu-id="20e05-105">The service has been modified to define two contracts, the `ICalculator` contract and the `ICalculatorSession` contract.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="20e05-106">Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="20e05-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="20e05-107">Implementuje třídu služby i `ICalculator` a `ICalculatorSession` smluv.</span><span class="sxs-lookup"><span data-stu-id="20e05-107">The service class implements both the `ICalculator` and `ICalculatorSession` contracts.</span></span> <span data-ttu-id="20e05-108">Vzhledem k tomu, že jeden smlouvách vyžaduje relaci, služba používá <xref:System.ServiceModel.InstanceContextMode.PerSession> režimu instance k uchování stavu během životního cyklu relace.</span><span class="sxs-lookup"><span data-stu-id="20e05-108">Because one of the contracts requires a session, the service uses the <xref:System.ServiceModel.InstanceContextMode.PerSession> instance mode to maintain the state over the lifetime of the session.</span></span>  
  
 <span data-ttu-id="20e05-109">Konfigurace služby byla změněna definovat dvě koncových bodů ke zveřejnění každou smlouvu.</span><span class="sxs-lookup"><span data-stu-id="20e05-109">The service configuration has been modified to define two endpoints to expose each contract.</span></span> <span data-ttu-id="20e05-110">`ICalculator` Koncový bod vystavený v základní adresu pomocí `basicHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="20e05-110">The `ICalculator` endpoint is exposed at the base address using a `basicHttpBinding`.</span></span> <span data-ttu-id="20e05-111">`ICalculatorSession` Koncový bod je přístupný pomocí baseaddress/relace `wsHttpBinding` s `bindingConfiguration` atribut nastaven na `BindingWithSession`, jak je znázorněno v následující ukázkové konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="20e05-111">The `ICalculatorSession` endpoint is exposed at the baseaddress/session using a `wsHttpBinding` with the `bindingConfiguration` attribute set to `BindingWithSession`, as shown in the following sample configuration.</span></span>  
  
```xml  
<service   
    name="Microsoft.ServiceModel.Samples.CalculatorService"  
    behaviorConfiguration="CalculatorServiceBehavior">  
  <!-- ICalculator endpoint is exposed using BasicBinding at the base  
       address provided by host:   
       http://localhost/servicemodelsamples/service.svc  -->  
  <endpoint address=""  
            binding="basicHttpBinding"  
            contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  <!-- ICalculatorSession endpoint is exposed using BindingWithSession  
       at {baseaddress}/session:  
       http://localhost/servicemodelsamples/service.svc/session -->  
  <endpoint address="session"  
            binding="wsHttpBinding"  
            bindingConfiguration="BindingWithSession"   
           contract="Microsoft.ServiceModel.Samples.ICalculatorSession" />  
  ...  
</service>  
```  
  
 <span data-ttu-id="20e05-112">Kód klienta vygenerovaný nyní obsahuje třídu klienta pro původní `ICalculator` kontraktu a nové `ICalculatorSession` kontraktu.</span><span class="sxs-lookup"><span data-stu-id="20e05-112">The generated client code now includes a client class for both the original `ICalculator` contract and the new `ICalculatorSession` contract.</span></span> <span data-ttu-id="20e05-113">Konfigurace klienta a kód se upravila tak komunikaci s každou smlouvu v koncovém bodě příslušnou službu.</span><span class="sxs-lookup"><span data-stu-id="20e05-113">The client configuration and code have been modified to communicate with each contract at the appropriate service endpoint.</span></span>  
  
 <span data-ttu-id="20e05-114">Klient je konzolová aplikace systému windows (.exe).</span><span class="sxs-lookup"><span data-stu-id="20e05-114">The client is a console windows application (.exe).</span></span> <span data-ttu-id="20e05-115">Služba je hostována v Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="20e05-115">The service is hosted by Internet Information Services (IIS).</span></span>  
  
 <span data-ttu-id="20e05-116">V okně konzoly klienta zobrazí operace odeslání na jednotlivé koncové body, nejdřív základní koncového bodu, za nímž následuje zabezpečeného koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="20e05-116">The client console window displays the operations sent to each of the endpoints, first the basic endpoint, followed by the secure endpoint.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="20e05-117">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="20e05-117">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="20e05-118">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="20e05-118">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="20e05-119">K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="20e05-119">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="20e05-120">Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="20e05-120">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="20e05-121">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="20e05-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="20e05-122">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="20e05-122">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="20e05-123">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="20e05-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="20e05-124">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="20e05-124">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\MultipleContracts`  
  
## <a name="see-also"></a><span data-ttu-id="20e05-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="20e05-125">See Also</span></span>
