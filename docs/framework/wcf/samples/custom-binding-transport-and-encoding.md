---
title: Kódování a přenos vlastní vazby
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6c0b353d-79ee-4e61-b348-be49ad0e9a16
ms.openlocfilehash: 47841b23dc3259aeb233192f396397745864d7ba
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145161"
---
# <a name="custom-binding-transport-and-encoding"></a><span data-ttu-id="59b9f-102">Kódování a přenos vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="59b9f-102">Custom Binding Transport and Encoding</span></span>
<span data-ttu-id="59b9f-103">Vlastní vazba je definována seřazeným seznamem samostatných prvků vazby.</span><span class="sxs-lookup"><span data-stu-id="59b9f-103">A custom binding is defined by an ordered list of discrete binding elements.</span></span> <span data-ttu-id="59b9f-104">Tato ukázka ukazuje, jak nakonfigurovat vlastní vazby s různými prvky přenosu a kódování zpráv.</span><span class="sxs-lookup"><span data-stu-id="59b9f-104">This sample demonstrates how to configure a custom binding with various transport and message encoding elements.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="59b9f-105">Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="59b9f-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="59b9f-106">Tato ukázka je založena na [vlastním hostiteli](../../../../docs/framework/wcf/samples/self-host.md)a byla upravena tak, aby nakonfigurovala tři koncové body pro podporu přenosů HTTP, TCP a NamedPipe s vlastními vazbami.</span><span class="sxs-lookup"><span data-stu-id="59b9f-106">This sample is based on the [Self-Host](../../../../docs/framework/wcf/samples/self-host.md), and has been modified to configure three endpoints to support HTTP, TCP, and NamedPipe transports with custom bindings.</span></span> <span data-ttu-id="59b9f-107">Konfigurace klienta byla podobně upravena a kód klienta byl změněn tak, aby komunikoval s každým ze tří koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="59b9f-107">The client configuration was similarly modified, and the client code changed to communicate with each of the three endpoints.</span></span>  
  
 <span data-ttu-id="59b9f-108">Ukázka ukazuje, jak nakonfigurovat vlastní vazbu, která podporuje konkrétní přenos a kódování zpráv.</span><span class="sxs-lookup"><span data-stu-id="59b9f-108">The sample demonstrates a how to configure a custom binding that supports a particular transport and message encoding.</span></span> <span data-ttu-id="59b9f-109">Toho lze dosáhnout konfigurací přenosu a kódování zprávy `binding` pro prvek.</span><span class="sxs-lookup"><span data-stu-id="59b9f-109">This is accomplished by configuring a transport and a message encoding for the `binding` element.</span></span> <span data-ttu-id="59b9f-110">Řazení elementů vazby je důležité při definování vlastní vazby, protože každý představuje vrstvu v zásobníku kanálu (viz [Vlastní vazby).](../../../../docs/framework/wcf/extending/custom-bindings.md)</span><span class="sxs-lookup"><span data-stu-id="59b9f-110">The ordering of binding elements is important in defining a custom binding, because each represents a layer in the channel stack (see [Custom Bindings](../../../../docs/framework/wcf/extending/custom-bindings.md)).</span></span> <span data-ttu-id="59b9f-111">Tato ukázka konfiguruje tři vlastní vazby: přenos HTTP s kódováním textu, přenos TCP s kódováním textu a přenos NamedPipe s binárním kódováním.</span><span class="sxs-lookup"><span data-stu-id="59b9f-111">This sample configures three custom bindings: an HTTP transport with text encoding, a TCP transport with text encoding, and a NamedPipe transport with a binary encoding.</span></span>  
  
 <span data-ttu-id="59b9f-112">Konfigurace služby definuje vlastní vazby takto:</span><span class="sxs-lookup"><span data-stu-id="59b9f-112">The service configuration defines the custom bindings as follows:</span></span>  
  
```xml  
<bindings>  
    <customBinding>  
        <binding name="HttpBinding" >  
            <textMessageEncoding
                messageVersion="Soap12Addressing10"/>  
            <httpTransport />  
        </binding>  
        <binding name="TcpBinding" >  
            <textMessageEncoding />  
            <tcpTransport />  
        </binding>  
        <binding name="NamedPipeBinding" >  
            <binaryMessageEncoding />  
            <namedPipeTransport />  
        </binding>  
    </customBinding>  
</bindings>  
```  
  
 <span data-ttu-id="59b9f-113">Při spuštění ukázky jsou zobrazeny požadavky na operaci a odpovědi v okně služby i klientské konzole.</span><span class="sxs-lookup"><span data-stu-id="59b9f-113">When you run the sample, the operation requests and responses are displayed in both the service and client console window.</span></span> <span data-ttu-id="59b9f-114">Klient komunikuje s každým ze tří koncových bodů, přístup první HTTP, pak TCP a nakonec NamedPipe.</span><span class="sxs-lookup"><span data-stu-id="59b9f-114">The client communicates with each of the three endpoints, accessing first HTTP, then TCP, and finally NamedPipe.</span></span> <span data-ttu-id="59b9f-115">Stisknutím klávesy ENTER v každém okně konzoly vypněte službu a klienta.</span><span class="sxs-lookup"><span data-stu-id="59b9f-115">Press ENTER in each console window to shut down the service and client.</span></span>  
  
 <span data-ttu-id="59b9f-116">Vazba `namedPipeTransport` nepodporuje operace mezi stroji.</span><span class="sxs-lookup"><span data-stu-id="59b9f-116">The `namedPipeTransport` binding does not support machine-to-machine operations.</span></span> <span data-ttu-id="59b9f-117">Používá se pouze pro komunikaci na stejném počítači.</span><span class="sxs-lookup"><span data-stu-id="59b9f-117">It is used only for communication on the same machine.</span></span> <span data-ttu-id="59b9f-118">Proto při spuštění ukázky ve scénáři mezi počítači, komentář se následující řádky v souboru kódu klienta:</span><span class="sxs-lookup"><span data-stu-id="59b9f-118">Therefore, when running the sample in a cross-machine scenario, comment out the following lines in the client code file:</span></span>  
  
```csharp  
CalculatorClient client = new CalculatorClient("default");  
Console.WriteLine("Communicate with named pipe endpoint.");  
// Call operations.  
DoCalculations(client);  
//Closing the client gracefully closes the connection and cleans up resources  
client.Close();  
```  
  
```vb  
Dim client As New CalculatorClient("default")  
Console.WriteLine("Communicate with named pipe endpoint.")  
' call operations  
DoCalculations(client)  
'Closing the client gracefully closes the connection and cleans up resources  
client.Close()  
```  
  
> [!NOTE]
> <span data-ttu-id="59b9f-119">Pokud používáte Svcutil.exe k obnovení konfigurace pro tuto ukázku, nezapomeňte upravit název koncového bodu v konfiguraci klienta tak, aby odpovídalkódu klienta.</span><span class="sxs-lookup"><span data-stu-id="59b9f-119">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="59b9f-120">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="59b9f-120">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="59b9f-121">Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="59b9f-121">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="59b9f-122">Chcete-li vytvořit c#, C++ nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="59b9f-122">To build the C#, C++, or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="59b9f-123">Chcete-li spustit ukázku v konfiguraci jednoho nebo více počítačů, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="59b9f-123">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="59b9f-124">Ukázky mohou být již nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="59b9f-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="59b9f-125">Před pokračováním zkontrolujte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="59b9f-125">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="59b9f-126">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="59b9f-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="59b9f-127">Tato ukázka je umístěna v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="59b9f-127">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Custom\Transport`  
