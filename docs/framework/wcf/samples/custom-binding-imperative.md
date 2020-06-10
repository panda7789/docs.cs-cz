---
title: Imperativní vlastní vazby
ms.date: 03/30/2017
ms.assetid: 6e13bf96-5de0-4476-b646-5f150774418d
ms.openlocfilehash: f7ba5c21b35d556be2c8d0817c37d98ad7d7dfcb
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594735"
---
# <a name="custom-binding-imperative"></a><span data-ttu-id="c328e-102">Imperativní vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="c328e-102">Custom Binding Imperative</span></span>
<span data-ttu-id="c328e-103">Ukázka ukazuje, jak napsat imperativní kód pro definování a použití vlastních vazeb bez použití konfiguračního souboru nebo klienta vygenerovaného Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="c328e-103">The sample demonstrates how to write imperative code to define and use custom bindings without using a configuration file or a Windows Communication Foundation (WCF) generated client.</span></span> <span data-ttu-id="c328e-104">Tato ukázka kombinuje funkce poskytované přenosem HTTP a stabilním kanálem relace k vytvoření spolehlivé vazby založené na protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="c328e-104">This sample combines the features provided by the HTTP transport and the reliable session channel to create a reliable HTTP-based binding.</span></span> <span data-ttu-id="c328e-105">Tato ukázka je založená na [Začínáme](getting-started-sample.md) , která implementuje službu kalkulačky.</span><span class="sxs-lookup"><span data-stu-id="c328e-105">This sample is based on the [Getting Started](getting-started-sample.md) that implements a calculator service.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c328e-106">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="c328e-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="c328e-107">V klientovi i ve službě je vytvořena vlastní vazba, která obsahuje dva prvky vazby (Spolehlivá relace a HTTP):</span><span class="sxs-lookup"><span data-stu-id="c328e-107">On both the client and the service, a custom binding is created that contains two binding elements (Reliable Session and HTTP):</span></span>  

```csharp
ReliableSessionBindingElement reliableSession = new ReliableSessionBindingElement();  
reliableSession.Ordered = true;  
  
HttpTransportBindingElement httpTransport = new HttpTransportBindingElement();  
httpTransport.AuthenticationScheme = System.Net.AuthenticationSchemes.Anonymous;  
httpTransport.HostNameComparisonMode = HostNameComparisonMode.StrongWildcard;  
  
CustomBinding binding = new CustomBinding(reliableSession, httpTransport);  
```
  
 <span data-ttu-id="c328e-108">Ve službě se vazba používá přidáním koncového bodu do třídy ServiceHost:</span><span class="sxs-lookup"><span data-stu-id="c328e-108">On the service, the binding is used by adding an endpoint to the ServiceHost:</span></span>  

```csharp
serviceHost.AddServiceEndpoint(typeof(ICalculator), binding, "");  
```

 <span data-ttu-id="c328e-109">V klientovi je vazba používána <xref:System.ServiceModel.ChannelFactory> k vytvoření kanálu ke službě:</span><span class="sxs-lookup"><span data-stu-id="c328e-109">On the client, the binding is used by a <xref:System.ServiceModel.ChannelFactory> to create a channel to the service:</span></span>  

```csharp
EndpointAddress address = new EndpointAddress("http://localhost:8000/servicemodelsamples/service");  
ChannelFactory<ICalculator> channelFactory = new ChannelFactory<ICalculator>(binding, address);  
ICalculator channel = channelFactory.CreateChannel();  
```

 <span data-ttu-id="c328e-110">Tento kanál se pak použije ke komunikaci se službou:</span><span class="sxs-lookup"><span data-stu-id="c328e-110">This channel is then used to interact with the service:</span></span>  

```csharp
// Call the Add service operation.  
double value1 = 100.00D;  
double value2 = 15.99D;  
double result = channel.Add(value1, value2);  
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
```

 <span data-ttu-id="c328e-111">Při spuštění ukázky se v okně konzoly klienta zobrazí požadavky na operace a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="c328e-111">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="c328e-112">V okně klienta stiskněte klávesu ENTER pro vypnutí klienta.</span><span class="sxs-lookup"><span data-stu-id="c328e-112">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c328e-113">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="c328e-113">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="c328e-114">Ujistěte se, že jste provedli [jednorázovou proceduru nastavení Windows Communication Foundation ukázek](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c328e-114">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="c328e-115">Chcete-li sestavit edici C# nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c328e-115">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="c328e-116">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c328e-116">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="c328e-117">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="c328e-117">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c328e-118">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="c328e-118">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="c328e-119">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="c328e-119">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c328e-120">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="c328e-120">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Binding\Custom\Imperative`  
  
## <a name="see-also"></a><span data-ttu-id="c328e-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="c328e-121">See also</span></span>

- [<span data-ttu-id="c328e-122">Ukázky vlastních vazeb</span><span class="sxs-lookup"><span data-stu-id="c328e-122">Custom Binding Samples</span></span>](custom-binding.md)
