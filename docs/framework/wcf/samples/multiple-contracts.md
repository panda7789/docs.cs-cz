---
title: Víc kontraktů
ms.date: 03/30/2017
ms.assetid: 2bef319b-fe9c-4d49-ac6c-dfb23eb35099
ms.openlocfilehash: e8451c49395a1dad55c5afca419f47a8e856b61f
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602502"
---
# <a name="multiple-contracts"></a><span data-ttu-id="c9312-102">Víc kontraktů</span><span class="sxs-lookup"><span data-stu-id="c9312-102">Multiple Contracts</span></span>
<span data-ttu-id="c9312-103">Ukázka více kontraktů ukazuje, jak implementovat více kontraktů ve službě a jak nakonfigurovat koncové body pro komunikaci se všemi implementovanými kontrakty.</span><span class="sxs-lookup"><span data-stu-id="c9312-103">The Multiple Contracts sample demonstrates how to implement more than one contract on a service and how to configure endpoints for communicating with each of the implemented contracts.</span></span> <span data-ttu-id="c9312-104">Tato ukázka je založena na [Začínáme](getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="c9312-104">This sample is based on the [Getting Started](getting-started-sample.md).</span></span> <span data-ttu-id="c9312-105">Služba byla změněna tak, aby definovala dvě smlouvy, `ICalculator` kontrakt a `ICalculatorSession` kontrakt.</span><span class="sxs-lookup"><span data-stu-id="c9312-105">The service has been modified to define two contracts, the `ICalculator` contract and the `ICalculatorSession` contract.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c9312-106">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="c9312-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="c9312-107">Třída služby implementuje `ICalculator` `ICalculatorSession` kontrakty i.</span><span class="sxs-lookup"><span data-stu-id="c9312-107">The service class implements both the `ICalculator` and `ICalculatorSession` contracts.</span></span> <span data-ttu-id="c9312-108">Vzhledem k tomu, že jedna z kontraktů vyžaduje relaci, služba používá <xref:System.ServiceModel.InstanceContextMode.PerSession> režim instance k udržení stavu po celou dobu životnosti relace.</span><span class="sxs-lookup"><span data-stu-id="c9312-108">Because one of the contracts requires a session, the service uses the <xref:System.ServiceModel.InstanceContextMode.PerSession> instance mode to maintain the state over the lifetime of the session.</span></span>  
  
 <span data-ttu-id="c9312-109">Konfigurace služby byla změněna tak, aby definovala dva koncové body, aby bylo možné všechny kontrakty zveřejnit.</span><span class="sxs-lookup"><span data-stu-id="c9312-109">The service configuration has been modified to define two endpoints to expose each contract.</span></span> <span data-ttu-id="c9312-110">`ICalculator`Koncový bod se zveřejňuje na základní adrese pomocí `basicHttpBinding` .</span><span class="sxs-lookup"><span data-stu-id="c9312-110">The `ICalculator` endpoint is exposed at the base address using a `basicHttpBinding`.</span></span> <span data-ttu-id="c9312-111">`ICalculatorSession`Koncový bod se zveřejňuje v rámci BaseAddress/Session pomocí `wsHttpBinding` atributu s `bindingConfiguration` atributem nastaveným na `BindingWithSession` , jak je znázorněno v následující ukázkové konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="c9312-111">The `ICalculatorSession` endpoint is exposed at the baseaddress/session using a `wsHttpBinding` with the `bindingConfiguration` attribute set to `BindingWithSession`, as shown in the following sample configuration.</span></span>  
  
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
  
 <span data-ttu-id="c9312-112">Generovaný kód klienta teď obsahuje třídu klienta pro původní `ICalculator` kontrakt i novou `ICalculatorSession` kontrakt.</span><span class="sxs-lookup"><span data-stu-id="c9312-112">The generated client code now includes a client class for both the original `ICalculator` contract and the new `ICalculatorSession` contract.</span></span> <span data-ttu-id="c9312-113">Konfigurace a kód klienta byly upraveny tak, aby komunikovaly s každou kontraktovou službou příslušného koncového bodu služby.</span><span class="sxs-lookup"><span data-stu-id="c9312-113">The client configuration and code have been modified to communicate with each contract at the appropriate service endpoint.</span></span>  
  
 <span data-ttu-id="c9312-114">Klient je Konzolová aplikace pro Windows (. exe).</span><span class="sxs-lookup"><span data-stu-id="c9312-114">The client is a console windows application (.exe).</span></span> <span data-ttu-id="c9312-115">Služba je hostována službou Internetová informační služba (IIS).</span><span class="sxs-lookup"><span data-stu-id="c9312-115">The service is hosted by Internet Information Services (IIS).</span></span>  
  
 <span data-ttu-id="c9312-116">Okno konzoly klienta zobrazuje operace odesílané do každého koncového bodu, nejprve základní koncový bod následovaný zabezpečeným koncovým bodem.</span><span class="sxs-lookup"><span data-stu-id="c9312-116">The client console window displays the operations sent to each of the endpoints, first the basic endpoint, followed by the secure endpoint.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c9312-117">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="c9312-117">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="c9312-118">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c9312-118">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="c9312-119">Chcete-li sestavit edici C# nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c9312-119">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="c9312-120">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c9312-120">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="c9312-121">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="c9312-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c9312-122">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="c9312-122">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="c9312-123">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="c9312-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c9312-124">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="c9312-124">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\MultipleContracts`  
