---
title: Kódování a přenos vlastní vazby
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6c0b353d-79ee-4e61-b348-be49ad0e9a16
ms.openlocfilehash: 3b3a0f1b52afce495ca41a426ebc9e57314d8254
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84592525"
---
# <a name="custom-binding-transport-and-encoding"></a><span data-ttu-id="282bf-102">Kódování a přenos vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="282bf-102">Custom Binding Transport and Encoding</span></span>
<span data-ttu-id="282bf-103">Vlastní vazba je definována seřazeným seznamem diskrétních prvků vazby.</span><span class="sxs-lookup"><span data-stu-id="282bf-103">A custom binding is defined by an ordered list of discrete binding elements.</span></span> <span data-ttu-id="282bf-104">Tato ukázka předvádí, jak nakonfigurovat vlastní vazbu s různými typy přenosů a kódování zpráv.</span><span class="sxs-lookup"><span data-stu-id="282bf-104">This sample demonstrates how to configure a custom binding with various transport and message encoding elements.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="282bf-105">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="282bf-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="282bf-106">Tato ukázka je založená na [vlastním hostiteli](self-host.md)a byla upravena pro konfiguraci tří koncových bodů pro podporu přenosů http, TCP a pojmenovaný kanál s vlastními vazbami.</span><span class="sxs-lookup"><span data-stu-id="282bf-106">This sample is based on the [Self-Host](self-host.md), and has been modified to configure three endpoints to support HTTP, TCP, and NamedPipe transports with custom bindings.</span></span> <span data-ttu-id="282bf-107">Konfigurace klienta se obdobně změnila a kód klienta se změnil, aby komunikoval s každým ze tří koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="282bf-107">The client configuration was similarly modified, and the client code changed to communicate with each of the three endpoints.</span></span>  
  
 <span data-ttu-id="282bf-108">Ukázka ukazuje, jak nakonfigurovat vlastní vazbu, která podporuje konkrétní přenos a kódování zpráv.</span><span class="sxs-lookup"><span data-stu-id="282bf-108">The sample demonstrates a how to configure a custom binding that supports a particular transport and message encoding.</span></span> <span data-ttu-id="282bf-109">To je provedeno konfigurací přenosu a kódováním zpráv pro `binding` element.</span><span class="sxs-lookup"><span data-stu-id="282bf-109">This is accomplished by configuring a transport and a message encoding for the `binding` element.</span></span> <span data-ttu-id="282bf-110">Řazení elementů vazby je důležité při definování vlastní vazby, protože každá představuje vrstvu v zásobníku kanálů (viz [vlastní vazby](../extending/custom-bindings.md)).</span><span class="sxs-lookup"><span data-stu-id="282bf-110">The ordering of binding elements is important in defining a custom binding, because each represents a layer in the channel stack (see [Custom Bindings](../extending/custom-bindings.md)).</span></span> <span data-ttu-id="282bf-111">Tato ukázka konfiguruje tři vlastní vazby: přenos HTTP s kódováním textu, přenos TCP s kódováním textu a pojmenovaný kanál přenos s binárním kódováním.</span><span class="sxs-lookup"><span data-stu-id="282bf-111">This sample configures three custom bindings: an HTTP transport with text encoding, a TCP transport with text encoding, and a NamedPipe transport with a binary encoding.</span></span>  
  
 <span data-ttu-id="282bf-112">Konfigurace služby definuje vlastní vazby následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="282bf-112">The service configuration defines the custom bindings as follows:</span></span>  
  
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
  
 <span data-ttu-id="282bf-113">Při spuštění ukázky se požadavky na operace a odpovědi zobrazují v okně konzoly služby i klienta.</span><span class="sxs-lookup"><span data-stu-id="282bf-113">When you run the sample, the operation requests and responses are displayed in both the service and client console window.</span></span> <span data-ttu-id="282bf-114">Klient komunikuje s každým ze tří koncových bodů, přistupuje k prvnímu HTTP, pak TCP a finally pojmenovaný kanál.</span><span class="sxs-lookup"><span data-stu-id="282bf-114">The client communicates with each of the three endpoints, accessing first HTTP, then TCP, and finally NamedPipe.</span></span> <span data-ttu-id="282bf-115">V každém okně konzoly stiskněte klávesu ENTER a ukončete službu a klienta.</span><span class="sxs-lookup"><span data-stu-id="282bf-115">Press ENTER in each console window to shut down the service and client.</span></span>  
  
 <span data-ttu-id="282bf-116">`namedPipeTransport`Vazba nepodporuje operace mezi počítačem a počítačem.</span><span class="sxs-lookup"><span data-stu-id="282bf-116">The `namedPipeTransport` binding does not support machine-to-machine operations.</span></span> <span data-ttu-id="282bf-117">Používá se pouze pro komunikaci ve stejném počítači.</span><span class="sxs-lookup"><span data-stu-id="282bf-117">It is used only for communication on the same machine.</span></span> <span data-ttu-id="282bf-118">Proto při spuštění ukázky v případě více počítačů přidejte do souboru s klientským kódem následující řádky:</span><span class="sxs-lookup"><span data-stu-id="282bf-118">Therefore, when running the sample in a cross-machine scenario, comment out the following lines in the client code file:</span></span>  
  
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
> <span data-ttu-id="282bf-119">Pokud pro obnovení konfigurace této ukázky používáte Svcutil. exe, nezapomeňte změnit název koncového bodu v konfiguraci klienta tak, aby odpovídal kódu klienta.</span><span class="sxs-lookup"><span data-stu-id="282bf-119">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="282bf-120">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="282bf-120">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="282bf-121">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="282bf-121">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="282bf-122">Chcete-li sestavit edici C#, C++ nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="282bf-122">To build the C#, C++, or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="282bf-123">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="282bf-123">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="282bf-124">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="282bf-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="282bf-125">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="282bf-125">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="282bf-126">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="282bf-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="282bf-127">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="282bf-127">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Custom\Transport`  
