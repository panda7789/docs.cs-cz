---
title: Vytvoření postupu kanálu
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 09b53aa1-b13c-476c-a461-e82fcacd2a8b
caps.latest.revision: 24
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 37b5f880b18f4caac9dc452d93129922ecc33543
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2018
---
# <a name="channel-factory"></a><span data-ttu-id="b3b28-102">Vytvoření postupu kanálu</span><span class="sxs-lookup"><span data-stu-id="b3b28-102">Channel Factory</span></span>
<span data-ttu-id="b3b28-103">Tento příklad ukazuje, jak klientská aplikace můžete vytvořit kanál s <xref:System.ServiceModel.ChannelFactory> třída místo generovaného klienta.</span><span class="sxs-lookup"><span data-stu-id="b3b28-103">This sample demonstrates how a client application can create a channel with the <xref:System.ServiceModel.ChannelFactory> class instead of a generated client.</span></span> <span data-ttu-id="b3b28-104">Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) službu kalkulačky, která implementuje.</span><span class="sxs-lookup"><span data-stu-id="b3b28-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b3b28-105">V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="b3b28-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="b3b28-106">V tomto příkladu <xref:System.ServiceModel.ChannelFactory%601> třída k vytvoření kanálu pro koncový bod služby.</span><span class="sxs-lookup"><span data-stu-id="b3b28-106">This sample uses the <xref:System.ServiceModel.ChannelFactory%601> class to create a channel to a service endpoint.</span></span> <span data-ttu-id="b3b28-107">Obvykle k vytvoření kanálu pro koncový bod služby, můžete vygenerovat typu klienta s [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) a vytvořit instanci typu generované.</span><span class="sxs-lookup"><span data-stu-id="b3b28-107">Typically, to create a channel to a service endpoint you generate a client type with the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) and create an instance of the generated type.</span></span> <span data-ttu-id="b3b28-108">Můžete také vytvořit kanál pomocí <xref:System.ServiceModel.ChannelFactory%601> třídy, jak je předvedeno v této ukázce.</span><span class="sxs-lookup"><span data-stu-id="b3b28-108">You can also create a channel by using the <xref:System.ServiceModel.ChannelFactory%601> class, as demonstrated in this sample.</span></span> <span data-ttu-id="b3b28-109">Službu vytvořené následující vzorový kód je stejný jako do služby [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="b3b28-109">The service created by the following sample code is identical to the service in the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>  
  
```csharp  
EndpointAddress address = new EndpointAddress("http://localhost/servicemodelsamples/service.svc");  
WSHttpBinding binding = new WSHttpBinding();  
ChannelFactory<ICalculator> factory = new   
                    ChannelFactory<ICalculator>(binding, address);  
ICalculator channel = factory.CreateChannel();  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="b3b28-110">Pokud používáte této ukázky ve scénáři mezi počítači, je potřeba "localhost" v předchozí kód nahradit plně kvalifikovaný název počítače, ve kterém je spuštěna služba.</span><span class="sxs-lookup"><span data-stu-id="b3b28-110">If you are running this sample in a cross-machine scenario, you must replace "localhost" in the preceding code with the fully-qualified name of the machine that is running the service.</span></span> <span data-ttu-id="b3b28-111">Tato ukázka nepoužívá konfigurace nastavit adresa koncového bodu, musí provést v kódu.</span><span class="sxs-lookup"><span data-stu-id="b3b28-111">This sample does not use configuration to set the endpoint address, so this must be done in code.</span></span>  
  
 <span data-ttu-id="b3b28-112">Po vytvoření kanálu operací služby nelze vyvolat stejně jako v generovaného klienta.</span><span class="sxs-lookup"><span data-stu-id="b3b28-112">Once the channel is created, service operations can be invoked just as with a generated client.</span></span>  
  
```csharp  
// Call the Add service operation.  
double value1 = 100.00D;  
double value2 = 15.99D;  
double result = channel.Add(value1, value2);  
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
```  
  
 <span data-ttu-id="b3b28-113">Zavřete kanál, se musí nejprve přetypovat <xref:System.ServiceModel.IClientChannel> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b3b28-113">To close the channel, it must first be cast to an <xref:System.ServiceModel.IClientChannel> interface.</span></span> <span data-ttu-id="b3b28-114">Důvodem je, že je v klientská aplikace používající deklarována kanál generovaná `ICalculator` rozhraní, které se má metody jako `Add` a `Subtract` ale ne `Close`.</span><span class="sxs-lookup"><span data-stu-id="b3b28-114">This is because the channel as generated is declared in the client application using the `ICalculator` interface, which has methods like `Add` and `Subtract` but not `Close`.</span></span> <span data-ttu-id="b3b28-115">`Close` Metoda pochází <xref:System.ServiceModel.ICommunicationObject> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b3b28-115">The `Close` method originates on the <xref:System.ServiceModel.ICommunicationObject> interface.</span></span>  
  
```csharp  
// Close the channel.  
 ((IClientChannel)client).Close();  
```  
  
 <span data-ttu-id="b3b28-116">Když spustíte ukázku, operace požadavky a odpovědi se zobrazí v okně konzoly klienta.</span><span class="sxs-lookup"><span data-stu-id="b3b28-116">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="b3b28-117">Stisknutím klávesy ENTER v okně klienta vypnout klientské aplikace.</span><span class="sxs-lookup"><span data-stu-id="b3b28-117">Press ENTER in the client window to shut down the client application.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b3b28-118">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="b3b28-118">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="b3b28-119">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b3b28-119">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="b3b28-120">Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b3b28-120">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span> <span data-ttu-id="b3b28-121">Všimněte si, že tato ukázka neumožňuje publikování metadat.</span><span class="sxs-lookup"><span data-stu-id="b3b28-121">Note that this sample does not enable metadata publishing.</span></span> <span data-ttu-id="b3b28-122">Nejprve je nutné povolit publikování metadat pro tato ukázka se znova vygenerovat typ klienta.</span><span class="sxs-lookup"><span data-stu-id="b3b28-122">You must first enable metadata publishing for this sample to regenerate the client type.</span></span>  
  
3.  <span data-ttu-id="b3b28-123">Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b3b28-123">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-cross-machine"></a><span data-ttu-id="b3b28-124">Ke spuštění ukázky pro různé počítače</span><span class="sxs-lookup"><span data-stu-id="b3b28-124">To run the sample cross machine</span></span>  
  
1.  <span data-ttu-id="b3b28-125">Nahraďte plně kvalifikovaný název počítače, ve kterém je spuštěna služba "localhost" v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="b3b28-125">Replace "localhost" in the following code with the fully-qualified name of the machine that is running the service.</span></span>  
  
    ```csharp  
    EndpointAddress address = new EndpointAddress("http://localhost/servicemodelsamples/service.svc");  
    ```  
  
> [!IMPORTANT]
>  <span data-ttu-id="b3b28-126">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="b3b28-126">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b3b28-127">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="b3b28-127">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="b3b28-128">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="b3b28-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b3b28-129">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="b3b28-129">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\ChannelFactory`  
  
## <a name="see-also"></a><span data-ttu-id="b3b28-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="b3b28-130">See Also</span></span>
