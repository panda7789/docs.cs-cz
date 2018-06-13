---
title: Víc kontraktů
ms.date: 03/30/2017
ms.assetid: 2bef319b-fe9c-4d49-ac6c-dfb23eb35099
ms.openlocfilehash: 8e96d1ac27eb69d8e7e4da76aa8679aa35bf8ad4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33501734"
---
# <a name="multiple-contracts"></a><span data-ttu-id="45a39-102">Víc kontraktů</span><span class="sxs-lookup"><span data-stu-id="45a39-102">Multiple Contracts</span></span>
<span data-ttu-id="45a39-103">Ukázka víc kontraktů ukazuje, jak implementovat více než jeden kontrakt na služby a konfiguraci koncových bodů pro komunikaci s jednotlivými implementovaná kontrakty.</span><span class="sxs-lookup"><span data-stu-id="45a39-103">The Multiple Contracts sample demonstrates how to implement more than one contract on a service and how to configure endpoints for communicating with each of the implemented contracts.</span></span> <span data-ttu-id="45a39-104">Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="45a39-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="45a39-105">Služba byla změněna definovat dvě kontrakty `ICalculator` kontraktu a `ICalculatorSession` kontrakt.</span><span class="sxs-lookup"><span data-stu-id="45a39-105">The service has been modified to define two contracts, the `ICalculator` contract and the `ICalculatorSession` contract.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="45a39-106">V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="45a39-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="45a39-107">Třída služby implementuje i `ICalculator` a `ICalculatorSession` smluv.</span><span class="sxs-lookup"><span data-stu-id="45a39-107">The service class implements both the `ICalculator` and `ICalculatorSession` contracts.</span></span> <span data-ttu-id="45a39-108">Protože jeden z smluv vyžaduje relaci, služba používá <xref:System.ServiceModel.InstanceContextMode.PerSession> režim instancí Udržovat stav po dobu životnosti relace.</span><span class="sxs-lookup"><span data-stu-id="45a39-108">Because one of the contracts requires a session, the service uses the <xref:System.ServiceModel.InstanceContextMode.PerSession> instance mode to maintain the state over the lifetime of the session.</span></span>  
  
 <span data-ttu-id="45a39-109">Konfigurace služby se změnilo definovat dva koncové body vystavit každé smlouvě.</span><span class="sxs-lookup"><span data-stu-id="45a39-109">The service configuration has been modified to define two endpoints to expose each contract.</span></span> <span data-ttu-id="45a39-110">`ICalculator` Koncový bod vystavený v základní adresa pomocí `basicHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="45a39-110">The `ICalculator` endpoint is exposed at the base address using a `basicHttpBinding`.</span></span> <span data-ttu-id="45a39-111">`ICalculatorSession` Koncový bod vystavený v baseaddress/relace pomocí `wsHttpBinding` s `bindingConfiguration` atribut nastaven na `BindingWithSession`, jak ukazuje následující ukázka konfigurace.</span><span class="sxs-lookup"><span data-stu-id="45a39-111">The `ICalculatorSession` endpoint is exposed at the baseaddress/session using a `wsHttpBinding` with the `bindingConfiguration` attribute set to `BindingWithSession`, as shown in the following sample configuration.</span></span>  
  
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
  
 <span data-ttu-id="45a39-112">Kód klienta vygenerovaný teď obsahuje třídu klienta pro obě původní `ICalculator` kontraktu a nové `ICalculatorSession` kontrakt.</span><span class="sxs-lookup"><span data-stu-id="45a39-112">The generated client code now includes a client class for both the original `ICalculator` contract and the new `ICalculatorSession` contract.</span></span> <span data-ttu-id="45a39-113">Konfigurace klienta a kód bylo upraveno, aby komunikovat s každou smlouvu na koncový bod příslušné služby.</span><span class="sxs-lookup"><span data-stu-id="45a39-113">The client configuration and code have been modified to communicate with each contract at the appropriate service endpoint.</span></span>  
  
 <span data-ttu-id="45a39-114">Klient je konzolovou aplikaci systému windows (.exe).</span><span class="sxs-lookup"><span data-stu-id="45a39-114">The client is a console windows application (.exe).</span></span> <span data-ttu-id="45a39-115">Služba je hostovaná Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="45a39-115">The service is hosted by Internet Information Services (IIS).</span></span>  
  
 <span data-ttu-id="45a39-116">V okně konzoly klienta zobrazí operace Odeslat všechny koncové body, nejdřív základní koncový bod, za nímž následuje zabezpečený koncový bod.</span><span class="sxs-lookup"><span data-stu-id="45a39-116">The client console window displays the operations sent to each of the endpoints, first the basic endpoint, followed by the secure endpoint.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="45a39-117">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="45a39-117">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="45a39-118">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="45a39-118">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="45a39-119">Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="45a39-119">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="45a39-120">Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="45a39-120">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="45a39-121">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="45a39-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="45a39-122">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="45a39-122">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="45a39-123">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="45a39-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="45a39-124">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="45a39-124">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\MultipleContracts`  
  
## <a name="see-also"></a><span data-ttu-id="45a39-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="45a39-125">See Also</span></span>
