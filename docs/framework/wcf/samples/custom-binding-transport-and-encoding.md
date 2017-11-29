---
title: "Kódování a přenos vlastní vazby"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 6c0b353d-79ee-4e61-b348-be49ad0e9a16
caps.latest.revision: "21"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e86b4c63a65c141046e833a9c1b0345fe9c029fe
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="custom-binding-transport-and-encoding"></a><span data-ttu-id="ab545-102">Kódování a přenos vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="ab545-102">Custom Binding Transport and Encoding</span></span>
<span data-ttu-id="ab545-103">Vlastní vazby je definována seřazený seznam prvky diskrétní vazby.</span><span class="sxs-lookup"><span data-stu-id="ab545-103">A custom binding is defined by an ordered list of discrete binding elements.</span></span> <span data-ttu-id="ab545-104">Tento příklad znázorňuje, jak nakonfigurovat vlastní vazby s různými přenosu a elementy kódování zprávy.</span><span class="sxs-lookup"><span data-stu-id="ab545-104">This sample demonstrates how to configure a custom binding with various transport and message encoding elements.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ab545-105">V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="ab545-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="ab545-106">Tato ukázka je založena na [hostování na vlastním](../../../../docs/framework/wcf/samples/self-host.md)a byla změněna konfigurace tři koncových bodů pro podporu protokolu HTTP, TCP a pojmenovaný kanál přenosy u vlastních vazeb.</span><span class="sxs-lookup"><span data-stu-id="ab545-106">This sample is based on the [Self-Host](../../../../docs/framework/wcf/samples/self-host.md), and has been modified to configure three endpoints to support HTTP, TCP, and NamedPipe transports with custom bindings.</span></span> <span data-ttu-id="ab545-107">Podobně byla změněna konfigurace klienta a změnit kód klienta ke komunikaci s jednotlivými tři koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="ab545-107">The client configuration was similarly modified, and the client code changed to communicate with each of the three endpoints.</span></span>  
  
 <span data-ttu-id="ab545-108">Ukázka předvádí nakonfigurovat vlastní vazby, která podporuje konkrétního přenosu a kódování zprávy.</span><span class="sxs-lookup"><span data-stu-id="ab545-108">The sample demonstrates a how to configure a custom binding that supports a particular transport and message encoding.</span></span> <span data-ttu-id="ab545-109">To se provádí konfigurace přenos a zprávy pro kódování `binding` elementu.</span><span class="sxs-lookup"><span data-stu-id="ab545-109">This is accomplished by configuring a transport and a message encoding for the `binding` element.</span></span> <span data-ttu-id="ab545-110">Řazení elementů vazby je důležité k definování vlastní vazby, protože každý představuje vrstvy v zásobníku kanál (viz [vlastní vazby](../../../../docs/framework/wcf/extending/custom-bindings.md)).</span><span class="sxs-lookup"><span data-stu-id="ab545-110">The ordering of binding elements is important in defining a custom binding, because each represents a layer in the channel stack (see [Custom Bindings](../../../../docs/framework/wcf/extending/custom-bindings.md)).</span></span> <span data-ttu-id="ab545-111">Tato ukázka nakonfiguruje tři vlastní vazby: přenosového protokolu HTTP s kódování textu, přenos TCP s kódování textu a přenos pojmenovaný kanál s binárního kódování.</span><span class="sxs-lookup"><span data-stu-id="ab545-111">This sample configures three custom bindings: an HTTP transport with text encoding, a TCP transport with text encoding, and a NamedPipe transport with a binary encoding.</span></span>  
  
 <span data-ttu-id="ab545-112">Konfigurace služby definuje vlastní vazby následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="ab545-112">The service configuration defines the custom bindings as follows:</span></span>  
  
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
  
 <span data-ttu-id="ab545-113">Když spustíte ukázku, operace požadavky a odpovědi se zobrazí v okně konzoly služby a klienta.</span><span class="sxs-lookup"><span data-stu-id="ab545-113">When you run the sample, the operation requests and responses are displayed in both the service and client console window.</span></span> <span data-ttu-id="ab545-114">Klient komunikuje s jednotlivými tři koncové body, přístup k první protokolu HTTP, pak TCP a nakonec pojmenovaný kanál.</span><span class="sxs-lookup"><span data-stu-id="ab545-114">The client communicates with each of the three endpoints, accessing first HTTP, then TCP, and finally NamedPipe.</span></span> <span data-ttu-id="ab545-115">Stisknutím klávesy ENTER v každé okna konzoly vypnout klienta a služby.</span><span class="sxs-lookup"><span data-stu-id="ab545-115">Press ENTER in each console window to shut down the service and client.</span></span>  
  
 <span data-ttu-id="ab545-116">`namedPipeTransport` Vazba nepodporuje operace počítač počítače.</span><span class="sxs-lookup"><span data-stu-id="ab545-116">The `namedPipeTransport` binding does not support machine-to-machine operations.</span></span> <span data-ttu-id="ab545-117">Použije se pouze pro komunikaci ve stejném počítači.</span><span class="sxs-lookup"><span data-stu-id="ab545-117">It is used only for communication on the same machine.</span></span> <span data-ttu-id="ab545-118">Proto při spuštění ukázky ve scénáři mezi počítači, komentář následující řádky do souboru kódu klienta:</span><span class="sxs-lookup"><span data-stu-id="ab545-118">Therefore, when running the sample in a cross-machine scenario, comment out the following lines in the client code file:</span></span>  
  
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
>  <span data-ttu-id="ab545-119">Pokud používáte Svcutil.exe znovu vygenerovat konfigurace pro tuto ukázku, nezapomeňte změnit název koncového bodu v konfiguraci klienta tak, aby odpovídaly kódu klienta.</span><span class="sxs-lookup"><span data-stu-id="ab545-119">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ab545-120">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="ab545-120">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="ab545-121">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ab545-121">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="ab545-122">Sestavení C#, C++ nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ab545-122">To build the C#, C++, or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="ab545-123">Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ab545-123">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ab545-124">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="ab545-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ab545-125">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="ab545-125">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="ab545-126">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="ab545-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ab545-127">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="ab545-127">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Custom\Transport`  
  
## <a name="see-also"></a><span data-ttu-id="ab545-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="ab545-128">See Also</span></span>
