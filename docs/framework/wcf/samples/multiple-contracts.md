---
title: Víc kontraktů
ms.date: 03/30/2017
ms.assetid: 2bef319b-fe9c-4d49-ac6c-dfb23eb35099
ms.openlocfilehash: ed59803b867dfe7994aceea010aa656c53927a0c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144341"
---
# <a name="multiple-contracts"></a><span data-ttu-id="707ca-102">Víc kontraktů</span><span class="sxs-lookup"><span data-stu-id="707ca-102">Multiple Contracts</span></span>
<span data-ttu-id="707ca-103">Ukázka více smluv ukazuje, jak implementovat více než jednu smlouvu na službu a jak nakonfigurovat koncové body pro komunikaci s každou z implementovaných smluv.</span><span class="sxs-lookup"><span data-stu-id="707ca-103">The Multiple Contracts sample demonstrates how to implement more than one contract on a service and how to configure endpoints for communicating with each of the implemented contracts.</span></span> <span data-ttu-id="707ca-104">Tato ukázka je založena na [začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="707ca-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="707ca-105">Služba byla upravena tak, aby `ICalculator` definovala `ICalculatorSession` dvě smlouvy, smlouvu a smlouvu.</span><span class="sxs-lookup"><span data-stu-id="707ca-105">The service has been modified to define two contracts, the `ICalculator` contract and the `ICalculatorSession` contract.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="707ca-106">Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="707ca-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="707ca-107">Třída služeb implementuje `ICalculator` `ICalculatorSession` a smlouvy.</span><span class="sxs-lookup"><span data-stu-id="707ca-107">The service class implements both the `ICalculator` and `ICalculatorSession` contracts.</span></span> <span data-ttu-id="707ca-108">Vzhledem k tomu, že jedna ze <xref:System.ServiceModel.InstanceContextMode.PerSession> smluv vyžaduje relaci, služba používá režim instance k udržení stavu po celou dobu trvání relace.</span><span class="sxs-lookup"><span data-stu-id="707ca-108">Because one of the contracts requires a session, the service uses the <xref:System.ServiceModel.InstanceContextMode.PerSession> instance mode to maintain the state over the lifetime of the session.</span></span>  
  
 <span data-ttu-id="707ca-109">Konfigurace služby byla upravena tak, aby definovala dva koncové body pro vystavení každé smlouvy.</span><span class="sxs-lookup"><span data-stu-id="707ca-109">The service configuration has been modified to define two endpoints to expose each contract.</span></span> <span data-ttu-id="707ca-110">Koncový `ICalculator` bod je vystaven na základní `basicHttpBinding`adrese pomocí .</span><span class="sxs-lookup"><span data-stu-id="707ca-110">The `ICalculator` endpoint is exposed at the base address using a `basicHttpBinding`.</span></span> <span data-ttu-id="707ca-111">Koncový `ICalculatorSession` bod je vystaven na baseaddress/session pomocí `wsHttpBinding` `bindingConfiguration` atribut `BindingWithSession`nastavit na , jak je znázorněno v následující konfiguraci vzorku.</span><span class="sxs-lookup"><span data-stu-id="707ca-111">The `ICalculatorSession` endpoint is exposed at the baseaddress/session using a `wsHttpBinding` with the `bindingConfiguration` attribute set to `BindingWithSession`, as shown in the following sample configuration.</span></span>  
  
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
  
 <span data-ttu-id="707ca-112">Generovaný kód klienta nyní zahrnuje třídu klienta pro původní `ICalculator` smlouvu i novou `ICalculatorSession` smlouvu.</span><span class="sxs-lookup"><span data-stu-id="707ca-112">The generated client code now includes a client class for both the original `ICalculator` contract and the new `ICalculatorSession` contract.</span></span> <span data-ttu-id="707ca-113">Konfigurace klienta a kód byly upraveny tak, aby komunikovaly s každou smlouvou v příslušném koncovém bodu služby.</span><span class="sxs-lookup"><span data-stu-id="707ca-113">The client configuration and code have been modified to communicate with each contract at the appropriate service endpoint.</span></span>  
  
 <span data-ttu-id="707ca-114">Klient je aplikace systému Windows konzoly (.exe).</span><span class="sxs-lookup"><span data-stu-id="707ca-114">The client is a console windows application (.exe).</span></span> <span data-ttu-id="707ca-115">Služba je hostována internetovou informační službou (IIS).</span><span class="sxs-lookup"><span data-stu-id="707ca-115">The service is hosted by Internet Information Services (IIS).</span></span>  
  
 <span data-ttu-id="707ca-116">Okno klientské konzole zobrazí operace odeslané do každého koncového bodu, nejprve základní koncový bod následovaný zabezpečeným koncovým bodem.</span><span class="sxs-lookup"><span data-stu-id="707ca-116">The client console window displays the operations sent to each of the endpoints, first the basic endpoint, followed by the secure endpoint.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="707ca-117">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="707ca-117">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="707ca-118">Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="707ca-118">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="707ca-119">Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="707ca-119">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="707ca-120">Chcete-li spustit ukázku v konfiguraci jednoho nebo více počítačů, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="707ca-120">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="707ca-121">Ukázky mohou být již nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="707ca-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="707ca-122">Před pokračováním zkontrolujte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="707ca-122">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="707ca-123">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="707ca-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="707ca-124">Tato ukázka je umístěna v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="707ca-124">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\MultipleContracts`  
