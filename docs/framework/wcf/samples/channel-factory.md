---
title: Vytvoření postupu kanálu
ms.date: 03/30/2017
ms.assetid: 09b53aa1-b13c-476c-a461-e82fcacd2a8b
ms.openlocfilehash: 6bf0668c6b846671db12dc20465ee70137d70b35
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43442756"
---
# <a name="channel-factory"></a><span data-ttu-id="93bef-102">Vytvoření postupu kanálu</span><span class="sxs-lookup"><span data-stu-id="93bef-102">Channel Factory</span></span>
<span data-ttu-id="93bef-103">Tato ukázka předvádí, jak vytvořit kanál s klientskou aplikaci <xref:System.ServiceModel.ChannelFactory> třídy namísto generovaného klienta.</span><span class="sxs-lookup"><span data-stu-id="93bef-103">This sample demonstrates how a client application can create a channel with the <xref:System.ServiceModel.ChannelFactory> class instead of a generated client.</span></span> <span data-ttu-id="93bef-104">Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) službu kalkulačky, která implementuje.</span><span class="sxs-lookup"><span data-stu-id="93bef-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="93bef-105">Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="93bef-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="93bef-106">Tento příklad používá <xref:System.ServiceModel.ChannelFactory%601> třídy za účelem vytvoření kanálu pro koncový bod služby.</span><span class="sxs-lookup"><span data-stu-id="93bef-106">This sample uses the <xref:System.ServiceModel.ChannelFactory%601> class to create a channel to a service endpoint.</span></span> <span data-ttu-id="93bef-107">Obvykle k vytvoření kanálu pro koncový bod služby, můžete generovat typ klienta s [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) a vytvořte její instanci generovaným typem.</span><span class="sxs-lookup"><span data-stu-id="93bef-107">Typically, to create a channel to a service endpoint you generate a client type with the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) and create an instance of the generated type.</span></span> <span data-ttu-id="93bef-108">Můžete také vytvořit kanál pomocí <xref:System.ServiceModel.ChannelFactory%601> třídy, jak je uvedeno v této ukázce.</span><span class="sxs-lookup"><span data-stu-id="93bef-108">You can also create a channel by using the <xref:System.ServiceModel.ChannelFactory%601> class, as demonstrated in this sample.</span></span> <span data-ttu-id="93bef-109">Služba vytvořené následující ukázkový kód je stejný jako službu v [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="93bef-109">The service created by the following sample code is identical to the service in the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>  
  
```csharp  
EndpointAddress address = new EndpointAddress("http://localhost/servicemodelsamples/service.svc");  
WSHttpBinding binding = new WSHttpBinding();  
ChannelFactory<ICalculator> factory = new   
                    ChannelFactory<ICalculator>(binding, address);  
ICalculator channel = factory.CreateChannel();  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="93bef-110">Pokud tuto ukázku spustíte ve scénáři mezi počítači, je "localhost" v předchozím kódu nahradit plně kvalifikovaný název počítače, na kterém je spuštěná služba.</span><span class="sxs-lookup"><span data-stu-id="93bef-110">If you are running this sample in a cross-machine scenario, you must replace "localhost" in the preceding code with the fully-qualified name of the machine that is running the service.</span></span> <span data-ttu-id="93bef-111">Tato ukázka nepoužívá konfigurace nastavit adresu koncového bodu, aby to je nutné provést v kódu.</span><span class="sxs-lookup"><span data-stu-id="93bef-111">This sample does not use configuration to set the endpoint address, so this must be done in code.</span></span>  
  
 <span data-ttu-id="93bef-112">Po vytvoření kanálu můžete stejně jako u generovaného klienta vyvolat operace služby.</span><span class="sxs-lookup"><span data-stu-id="93bef-112">Once the channel is created, service operations can be invoked just as with a generated client.</span></span>  
  
```csharp  
// Call the Add service operation.  
double value1 = 100.00D;  
double value2 = 15.99D;  
double result = channel.Add(value1, value2);  
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
```  
  
 <span data-ttu-id="93bef-113">Zavřete kanál, je nutné nejprve přetypovat na <xref:System.ServiceModel.IClientChannel> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="93bef-113">To close the channel, it must first be cast to an <xref:System.ServiceModel.IClientChannel> interface.</span></span> <span data-ttu-id="93bef-114">Důvodem je, že kanál generovaná je deklarován v klientská aplikace používající `ICalculator` rozhraní, které obsahuje metody jako `Add` a `Subtract` , ale ne `Close`.</span><span class="sxs-lookup"><span data-stu-id="93bef-114">This is because the channel as generated is declared in the client application using the `ICalculator` interface, which has methods like `Add` and `Subtract` but not `Close`.</span></span> <span data-ttu-id="93bef-115">`Close` Metoda pochází <xref:System.ServiceModel.ICommunicationObject> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="93bef-115">The `Close` method originates on the <xref:System.ServiceModel.ICommunicationObject> interface.</span></span>  
  
```csharp  
// Close the channel.  
 ((IClientChannel)client).Close();  
```  
  
 <span data-ttu-id="93bef-116">Při spuštění ukázky operace žádosti a odpovědi se zobrazí v okně konzoly klienta.</span><span class="sxs-lookup"><span data-stu-id="93bef-116">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="93bef-117">Stisknutím klávesy ENTER v okně klienta vypnout klientské aplikace.</span><span class="sxs-lookup"><span data-stu-id="93bef-117">Press ENTER in the client window to shut down the client application.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="93bef-118">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="93bef-118">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="93bef-119">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="93bef-119">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="93bef-120">K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="93bef-120">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span> <span data-ttu-id="93bef-121">Všimněte si, že tato ukázka není povoleno publikování metadat.</span><span class="sxs-lookup"><span data-stu-id="93bef-121">Note that this sample does not enable metadata publishing.</span></span> <span data-ttu-id="93bef-122">Nejprve je nutné povolit publikování metadat pro tuto ukázku se znova vygenerovat typu klienta.</span><span class="sxs-lookup"><span data-stu-id="93bef-122">You must first enable metadata publishing for this sample to regenerate the client type.</span></span>  
  
3.  <span data-ttu-id="93bef-123">Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="93bef-123">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-cross-machine"></a><span data-ttu-id="93bef-124">Ke spuštění ukázky pro různé počítače</span><span class="sxs-lookup"><span data-stu-id="93bef-124">To run the sample cross machine</span></span>  
  
1.  <span data-ttu-id="93bef-125">Nahraďte plně kvalifikovaný název počítače, na kterém je spuštěná služba "localhost" v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="93bef-125">Replace "localhost" in the following code with the fully-qualified name of the machine that is running the service.</span></span>  
  
    ```csharp  
    EndpointAddress address = new EndpointAddress("http://localhost/servicemodelsamples/service.svc");  
    ```  
  
> [!IMPORTANT]
>  <span data-ttu-id="93bef-126">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="93bef-126">The samples may already be installed on your machine.</span></span> <span data-ttu-id="93bef-127">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="93bef-127">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="93bef-128">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="93bef-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="93bef-129">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="93bef-129">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\ChannelFactory`  
  
## <a name="see-also"></a><span data-ttu-id="93bef-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="93bef-130">See Also</span></span>
