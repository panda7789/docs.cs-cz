---
title: Kódování a přenos vlastní vazby
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6c0b353d-79ee-4e61-b348-be49ad0e9a16
ms.openlocfilehash: 98d264cb081af0c0ed96b7e439f93224608467d4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54717412"
---
# <a name="custom-binding-transport-and-encoding"></a><span data-ttu-id="ce7db-102">Kódování a přenos vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="ce7db-102">Custom Binding Transport and Encoding</span></span>
<span data-ttu-id="ce7db-103">Seřazený seznam elementů diskrétní vazby je definován vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="ce7db-103">A custom binding is defined by an ordered list of discrete binding elements.</span></span> <span data-ttu-id="ce7db-104">Tento příklad ukazuje, jak nakonfigurovat vlastní vazby s různými přenos a kódování prvků zprávy.</span><span class="sxs-lookup"><span data-stu-id="ce7db-104">This sample demonstrates how to configure a custom binding with various transport and message encoding elements.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ce7db-105">Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="ce7db-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="ce7db-106">Tato ukázka je založena na [hostování na vlastním serveru](../../../../docs/framework/wcf/samples/self-host.md)a byla změněna konfigurace tři koncových bodech, které podporují přenosy HTTP, TCP a pojmenovaného kanálu u vlastních vazeb.</span><span class="sxs-lookup"><span data-stu-id="ce7db-106">This sample is based on the [Self-Host](../../../../docs/framework/wcf/samples/self-host.md), and has been modified to configure three endpoints to support HTTP, TCP, and NamedPipe transports with custom bindings.</span></span> <span data-ttu-id="ce7db-107">Podobně změnil konfiguraci klienta a změněn kód klienta ke komunikaci s každým tři koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="ce7db-107">The client configuration was similarly modified, and the client code changed to communicate with each of the three endpoints.</span></span>  
  
 <span data-ttu-id="ce7db-108">Vzorek ukazuje ke konfiguraci vlastních vazbu, která podporuje konkrétní přenos a kódování zprávy.</span><span class="sxs-lookup"><span data-stu-id="ce7db-108">The sample demonstrates a how to configure a custom binding that supports a particular transport and message encoding.</span></span> <span data-ttu-id="ce7db-109">Toho dosahuje tím, že nakonfigurujete přenos a kódování pro zprávu `binding` elementu.</span><span class="sxs-lookup"><span data-stu-id="ce7db-109">This is accomplished by configuring a transport and a message encoding for the `binding` element.</span></span> <span data-ttu-id="ce7db-110">Řazení elementů vazby je důležité při definování vlastní vazby, protože každý reprezentuje vrstvu v kanálu zásobníku (viz [vlastních vazeb](../../../../docs/framework/wcf/extending/custom-bindings.md)).</span><span class="sxs-lookup"><span data-stu-id="ce7db-110">The ordering of binding elements is important in defining a custom binding, because each represents a layer in the channel stack (see [Custom Bindings](../../../../docs/framework/wcf/extending/custom-bindings.md)).</span></span> <span data-ttu-id="ce7db-111">Tato vzorovým kódem se nakonfiguruje tři vlastních vazeb: přenos pomocí protokolu HTTP s kódování textu, přenosu protokolu TCP s kódování textu a pojmenovaný kanál přenosu pomocí binárního kódování.</span><span class="sxs-lookup"><span data-stu-id="ce7db-111">This sample configures three custom bindings: an HTTP transport with text encoding, a TCP transport with text encoding, and a NamedPipe transport with a binary encoding.</span></span>  
  
 <span data-ttu-id="ce7db-112">Konfigurace služby definuje vlastní vazby následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="ce7db-112">The service configuration defines the custom bindings as follows:</span></span>  
  
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
  
 <span data-ttu-id="ce7db-113">Při spuštění ukázky operace žádosti a odpovědi jsou zobrazeny v okně konzoly služby a klienta.</span><span class="sxs-lookup"><span data-stu-id="ce7db-113">When you run the sample, the operation requests and responses are displayed in both the service and client console window.</span></span> <span data-ttu-id="ce7db-114">Klient komunikuje s jednotlivými tři koncové body, přístup k první HTTP a TCP a nakonec pojmenovaného kanálu.</span><span class="sxs-lookup"><span data-stu-id="ce7db-114">The client communicates with each of the three endpoints, accessing first HTTP, then TCP, and finally NamedPipe.</span></span> <span data-ttu-id="ce7db-115">Stisknutím klávesy ENTER v každé okno konzoly pro vypnutí klienta a služby.</span><span class="sxs-lookup"><span data-stu-id="ce7db-115">Press ENTER in each console window to shut down the service and client.</span></span>  
  
 <span data-ttu-id="ce7db-116">`namedPipeTransport` Vazby nepodporuje operace machine-to-machine.</span><span class="sxs-lookup"><span data-stu-id="ce7db-116">The `namedPipeTransport` binding does not support machine-to-machine operations.</span></span> <span data-ttu-id="ce7db-117">Používá se pouze pro komunikaci ve stejném počítači.</span><span class="sxs-lookup"><span data-stu-id="ce7db-117">It is used only for communication on the same machine.</span></span> <span data-ttu-id="ce7db-118">Při spuštění ukázky ve scénáři mezi počítači, okomentujte proto následující řádky do souboru kódu klienta:</span><span class="sxs-lookup"><span data-stu-id="ce7db-118">Therefore, when running the sample in a cross-machine scenario, comment out the following lines in the client code file:</span></span>  
  
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
>  <span data-ttu-id="ce7db-119">Pokud používáte Svcutil.exe k opětovnému vytvoření konfigurace pro tuto ukázku, nezapomeňte změnit název koncového bodu v konfiguraci klienta tak, aby odpovídaly klientský kód.</span><span class="sxs-lookup"><span data-stu-id="ce7db-119">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ce7db-120">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="ce7db-120">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="ce7db-121">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ce7db-121">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="ce7db-122">K sestavení edice řešení C#, C++ nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ce7db-122">To build the C#, C++, or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="ce7db-123">Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ce7db-123">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ce7db-124">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="ce7db-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ce7db-125">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="ce7db-125">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="ce7db-126">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="ce7db-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ce7db-127">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="ce7db-127">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Custom\Transport`  
  
## <a name="see-also"></a><span data-ttu-id="ce7db-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ce7db-128">See also</span></span>
