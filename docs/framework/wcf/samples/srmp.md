---
title: SRMP
ms.date: 03/30/2017
ms.assetid: cf37078c-dcb4-45e0-acaf-2f196521b226
ms.openlocfilehash: b1b61c18c801059e95cd0b13a3135132a583882f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183343"
---
# <a name="srmp"></a><span data-ttu-id="15063-102">SRMP</span><span class="sxs-lookup"><span data-stu-id="15063-102">SRMP</span></span>
<span data-ttu-id="15063-103">Tato ukázka ukazuje, jak provádět transakční komunikaci ve frontě pomocí služby Řízení front zpráv (Služba MSMQ) přes protokol HTTP.</span><span class="sxs-lookup"><span data-stu-id="15063-103">This sample demonstrates how to perform transacted queued communication by using Message Queuing (MSMQ) over HTTP.</span></span>  
  
 <span data-ttu-id="15063-104">Ve frontové komunikaci klient komunikuje se službou pomocí fronty.</span><span class="sxs-lookup"><span data-stu-id="15063-104">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="15063-105">Přesněji řečeno, klient odesílá zprávy do fronty.</span><span class="sxs-lookup"><span data-stu-id="15063-105">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="15063-106">Služba přijímá zprávy z fronty.</span><span class="sxs-lookup"><span data-stu-id="15063-106">The service receives messages from the queue.</span></span> <span data-ttu-id="15063-107">Služba a klient proto nemusí být spuštěny současně komunikovat pomocí fronty.</span><span class="sxs-lookup"><span data-stu-id="15063-107">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>  
  
 <span data-ttu-id="15063-108">Služba MSMQ umožňuje použití protokolu HTTP (včetně použití protokolu HTTPS) k odesílání zpráv do fronty.</span><span class="sxs-lookup"><span data-stu-id="15063-108">MSMQ enables the use of HTTP (including the use of HTTPS) to send messages to a queue.</span></span> <span data-ttu-id="15063-109">V tomto příkladu jsme demonstrovat pomocí Windows Communication Foundation (WCF) ve frontě komunikace a jak odesílat zprávy přes HTTP.</span><span class="sxs-lookup"><span data-stu-id="15063-109">In this example, we demonstrate using Windows Communication Foundation (WCF) queued communication and how to send messages over HTTP.</span></span> <span data-ttu-id="15063-110">Služba MSMQ používá protokol s názvem SRMP, což je protokol založený na protokolu SOAP pro komunikaci přes protokol HTTP.</span><span class="sxs-lookup"><span data-stu-id="15063-110">MSMQ uses a protocol called SRMP, which is a SOAP-based protocol for communication over HTTP.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="15063-111">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="15063-111">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="15063-112">Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="15063-112">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="15063-113">Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="15063-113">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="15063-114">Chcete-li spustit ukázku v konfiguraci jednoho nebo více počítačů, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="15063-114">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
4. <span data-ttu-id="15063-115">Před spuštěním **ukázky v aplikaci Přidat nebo odebrat součásti systému Windows**zkontrolujte, zda je služba MSMQ nainstalována s podporou protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="15063-115">Before running the sample in **Add/Remove Windows Components**, ensure that MSMQ is installed with HTTP support.</span></span> <span data-ttu-id="15063-116">Instalace podpory protokolu HTTP automaticky nainstaluje internetovou informační službu (IIS) a přidá podporu protokolu do služby IIS pro službu MSMQ.</span><span class="sxs-lookup"><span data-stu-id="15063-116">Installing HTTP support automatically installs Internet Information Services (IIS) and adds the protocol support in IIS for MSMQ.</span></span>  
  
5. <span data-ttu-id="15063-117">Chcete-li si být jisti, že se protokol HTTP používá pro komunikaci, můžete povolit spuštění služby MSMQ v režimu tvrzené.</span><span class="sxs-lookup"><span data-stu-id="15063-117">If you want to be certain that HTTP is used for communication, you can enable MSMQ to run in hardened mode.</span></span> <span data-ttu-id="15063-118">Tím je zajištěno, že žádné zprávy do fronty hostované v počítači může dorazit pomocí jakéhokoli přenosu bez protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="15063-118">This ensures that no messages to any queue hosted on the machine can arrive using any non-HTTP transport.</span></span>  
  
6. <span data-ttu-id="15063-119">Po výběru služby MSMQ pro spuštění v režimu tvrzené technologie vyžaduje počítač opětovné spuštění v systému Windows Server 2003.</span><span class="sxs-lookup"><span data-stu-id="15063-119">After you have selected MSMQ to run in hardened mode, the machine requires a re-boot on Windows Server 2003.</span></span>  
  
7. <span data-ttu-id="15063-120">Spusťte službu.</span><span class="sxs-lookup"><span data-stu-id="15063-120">Run the service.</span></span>  
  
8. <span data-ttu-id="15063-121">Spusťte klienta.</span><span class="sxs-lookup"><span data-stu-id="15063-121">Run the client.</span></span> <span data-ttu-id="15063-122">Ujistěte se, že změníte adresu koncového bodu tak, aby ukazovala na název počítače nebo ADRESU IP místo localhost.</span><span class="sxs-lookup"><span data-stu-id="15063-122">Ensure that you change the endpoint address to point to the machine name or IP address instead of localhost.</span></span> <span data-ttu-id="15063-123">Klient odešle zprávu a ukončí.</span><span class="sxs-lookup"><span data-stu-id="15063-123">The client sends a message and exits.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15063-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="15063-124">Requirements</span></span>  
 <span data-ttu-id="15063-125">Chcete-li spustit tuto ukázku, musí být služba IIS nainstalována na službu i na klientských počítačích kromě služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="15063-125">To run this sample, IIS must be installed on both the service and the client machines in addition to MSMQ.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="15063-126">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="15063-126">Demonstrates</span></span>  
 <span data-ttu-id="15063-127">Ukázka ukazuje odesílání zpráv ve frontě WCF pomocí služby MSMQ přes protokol HTTP.</span><span class="sxs-lookup"><span data-stu-id="15063-127">The sample demonstrates sending WCF queued messages using MSMQ over HTTP.</span></span> <span data-ttu-id="15063-128">To se také nazývá zasílání zpráv SRMP.</span><span class="sxs-lookup"><span data-stu-id="15063-128">This is also called SRMP messaging.</span></span> <span data-ttu-id="15063-129">Při odeslání zprávy ve frontě převede služba MSMQ v odesílajícím počítači zprávy do přijímajícího správce front prostřednictvím přenosu TCP nebo HTTP.</span><span class="sxs-lookup"><span data-stu-id="15063-129">When a queued message is sent, MSMQ on the sending machine transfers the messages to the receiving queue manager over TCP or HTTP transport.</span></span> <span data-ttu-id="15063-130">Výběrem SRMP, uživatel označuje volbu PROTOKOLU HTTP jako přenos pro přenos fronty.</span><span class="sxs-lookup"><span data-stu-id="15063-130">By choosing SRMP, the user indicates the choice of HTTP as a transport for queue transfer.</span></span> <span data-ttu-id="15063-131">SRMP Secure umožňuje použití protokolu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="15063-131">SRMP Secure enables the use of HTTPS.</span></span>  
  
## <a name="example"></a><span data-ttu-id="15063-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="15063-132">Example</span></span>  
 <span data-ttu-id="15063-133">Ukázkový kód je založen na transakčním vzorku.</span><span class="sxs-lookup"><span data-stu-id="15063-133">The sample code is based on the transacted sample.</span></span> <span data-ttu-id="15063-134">Způsob odeslání zprávy do fronty a přijetí zprávy z fronty pomocí protokolu SRMP je stejný jako odesílání a přijímání zpráv pomocí nativního protokolu.</span><span class="sxs-lookup"><span data-stu-id="15063-134">How you send a message to the queue and receive a message from the queue using SRMP is the same as sending and receiving messages using a Native protocol.</span></span>  
  
 <span data-ttu-id="15063-135">Konfigurace klienta je změněna tak, aby označovala volbu protokolu přenosu fronty.</span><span class="sxs-lookup"><span data-stu-id="15063-135">The configuration for the client is changed to indicate the choice of the queue transfer protocol.</span></span> <span data-ttu-id="15063-136">Protokol přenosu fronty může být jedním z nativní, SRMP nebo SrmpSecure.</span><span class="sxs-lookup"><span data-stu-id="15063-136">The queue transfer protocol can be one of Native, SRMP or SrmpSecure.</span></span> <span data-ttu-id="15063-137">Ve výchozím nastavení je přenosový protokol nativní.</span><span class="sxs-lookup"><span data-stu-id="15063-137">By default, the transfer protocol is Native.</span></span> <span data-ttu-id="15063-138">Klient a služba zadat v konfiguraci pro použití SRMP v tomto příkladu.</span><span class="sxs-lookup"><span data-stu-id="15063-138">The client and service specify in the configuration to use SRMP in this example.</span></span>  
  
 <span data-ttu-id="15063-139">Existují omezení SRMP ve vztahu k bezpečnosti dopravy.</span><span class="sxs-lookup"><span data-stu-id="15063-139">There are limitations to SRMP in relation to transport security.</span></span> <span data-ttu-id="15063-140">Výchozí zabezpečení přenosu služby MSMQ vyžaduje službu Active Directory, která vyžaduje, aby se správce fronty odesílání a správce přijímající fronty byli umístěni ve stejné doméně systému Windows.</span><span class="sxs-lookup"><span data-stu-id="15063-140">The default MSMQ transport security requires Active Directory that requires that the sending queue manager and the receiving queue manager reside in the same Windows domain.</span></span> <span data-ttu-id="15063-141">To není možné při odesílání zpráv přes hranice PROTOKOLU HTTP.</span><span class="sxs-lookup"><span data-stu-id="15063-141">This is not possible when sending messages over HTTP boundary.</span></span> <span data-ttu-id="15063-142">Jako takové výchozí zabezpečení přenosu nefunguje.</span><span class="sxs-lookup"><span data-stu-id="15063-142">As such, the default transport security does not work.</span></span> <span data-ttu-id="15063-143">Zabezpečení přenosu musí být nastaveno na certifikát, pokud je požadováno zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="15063-143">The transport security must be set to Certificate if transport security is desired.</span></span> <span data-ttu-id="15063-144">Zabezpečení zpráv lze také použít k zabezpečení zprávy.</span><span class="sxs-lookup"><span data-stu-id="15063-144">Message security can also be used to secure the message.</span></span> <span data-ttu-id="15063-145">V této ukázce je vypnuto zabezpečení přenosu i zpráv pro ilustraci zasílání zpráv SRMP.</span><span class="sxs-lookup"><span data-stu-id="15063-145">In this sample, both transport and message security is turned off to illustrate SRMP messaging.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  
  <system.serviceModel>  
  
    <client>  
      <!-- Define NetMsmqEndpoint -->  
      <endpoint name="OrderProcessorEndpoint"  
           address=  
          "net.msmq://localhost/private/ServiceModelSamplesSrmp"
           bindingConfiguration="srmpBinding"
           binding="netMsmqBinding"
           contract="IOrderProcessor" />  
    </client>  
    <bindings>  
      <netMsmqBinding>  
        <binding name="srmpBinding"  
                 queueTransferProtocol="Srmp">  
          <security mode="None" />  
        </binding>  
      </netMsmqBinding>  
    </bindings>  
  </system.serviceModel>  
  
</configuration>  
```  
  
 <span data-ttu-id="15063-146">Spuštění ukázky dává následující výstup.</span><span class="sxs-lookup"><span data-stu-id="15063-146">Running the sample yields the following output.</span></span>  
  
```console  
Processing Purchase Order: 556b70be-31ee-4a3b-8df4-ed5e538015a4
Customer: somecustomer.com
OrderDetails
    Order LineItem: 54 of Blue Widget @unit price: $29.99
    Order LineItem: 890 of Red Widget @unit price: $45.89
    Total cost of this order: $42461.56
    Order status: Pending  
```  
  
> [!IMPORTANT]
> <span data-ttu-id="15063-147">Ukázky mohou být již nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="15063-147">The samples may already be installed on your machine.</span></span> <span data-ttu-id="15063-148">Před pokračováním zkontrolujte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="15063-148">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="15063-149">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="15063-149">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="15063-150">Tato ukázka je umístěna v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="15063-150">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\SRMP`  
