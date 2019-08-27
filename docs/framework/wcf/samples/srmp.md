---
title: SRMP
ms.date: 03/30/2017
ms.assetid: cf37078c-dcb4-45e0-acaf-2f196521b226
ms.openlocfilehash: e3015e7185fd52a1161b91c74dee57f694fbeebd
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044720"
---
# <a name="srmp"></a><span data-ttu-id="f9dfd-102">SRMP</span><span class="sxs-lookup"><span data-stu-id="f9dfd-102">SRMP</span></span>
<span data-ttu-id="f9dfd-103">Tato ukázka předvádí, jak pomocí služby Řízení front zpráv (MSMQ) přes protokol HTTP provádět komunikaci v transakční frontě.</span><span class="sxs-lookup"><span data-stu-id="f9dfd-103">This sample demonstrates how to perform transacted queued communication by using Message Queuing (MSMQ) over HTTP.</span></span>  
  
 <span data-ttu-id="f9dfd-104">V komunikaci ve frontě klient komunikuje se službou pomocí fronty.</span><span class="sxs-lookup"><span data-stu-id="f9dfd-104">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="f9dfd-105">Klient přesněji odesílá zprávy do fronty.</span><span class="sxs-lookup"><span data-stu-id="f9dfd-105">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="f9dfd-106">Služba přijímá zprávy z fronty.</span><span class="sxs-lookup"><span data-stu-id="f9dfd-106">The service receives messages from the queue.</span></span> <span data-ttu-id="f9dfd-107">Službu a klient proto nemusí běžet současně, aby bylo možné komunikovat pomocí fronty.</span><span class="sxs-lookup"><span data-stu-id="f9dfd-107">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>  
  
 <span data-ttu-id="f9dfd-108">Služba MSMQ umožňuje používat protokol HTTP (včetně použití protokolu HTTPS) k posílání zpráv do fronty.</span><span class="sxs-lookup"><span data-stu-id="f9dfd-108">MSMQ enables the use of HTTP (including the use of HTTPS) to send messages to a queue.</span></span> <span data-ttu-id="f9dfd-109">V tomto příkladu ukážeme, že používáme komunikaci ve frontě Windows Communication Foundation (WCF) a jak odesílat zprávy přes protokol HTTP.</span><span class="sxs-lookup"><span data-stu-id="f9dfd-109">In this example, we demonstrate using Windows Communication Foundation (WCF) queued communication and how to send messages over HTTP.</span></span> <span data-ttu-id="f9dfd-110">Služba MSMQ používá protokol s názvem SRMP, což je protokol založený na protokolu SOAP pro komunikaci přes protokol HTTP.</span><span class="sxs-lookup"><span data-stu-id="f9dfd-110">MSMQ uses a protocol called SRMP, which is a SOAP-based protocol for communication over HTTP.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="f9dfd-111">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="f9dfd-111">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="f9dfd-112">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f9dfd-112">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="f9dfd-113">Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu sestavování [ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f9dfd-113">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="f9dfd-114">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f9dfd-114">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
4. <span data-ttu-id="f9dfd-115">Před spuštěním ukázky v **části Přidat nebo odebrat součásti systému Windows**se ujistěte, že je služba MSMQ nainstalovaná s podporou protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="f9dfd-115">Before running the sample in **Add/Remove Windows Components**, ensure that MSMQ is installed with HTTP support.</span></span> <span data-ttu-id="f9dfd-116">Instalace podpory protokolu HTTP automaticky nainstaluje Internetová informační služba (IIS) a přidá podporu protokolu ve službě IIS pro službu MSMQ.</span><span class="sxs-lookup"><span data-stu-id="f9dfd-116">Installing HTTP support automatically installs Internet Information Services (IIS) and adds the protocol support in IIS for MSMQ.</span></span>  
  
5. <span data-ttu-id="f9dfd-117">Pokud chcete mít jistotu, že se protokol HTTP používá ke komunikaci, můžete povolit spuštění služby MSMQ v zesíleném režimu.</span><span class="sxs-lookup"><span data-stu-id="f9dfd-117">If you want to be certain that HTTP is used for communication, you can enable MSMQ to run in hardened mode.</span></span> <span data-ttu-id="f9dfd-118">Tím se zajistí, že žádné zprávy, které se na tomto počítači hostují, nemůžou dorazit pomocí jakéhokoli přenosu bez protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="f9dfd-118">This ensures that no messages to any queue hosted on the machine can arrive using any non-HTTP transport.</span></span>  
  
6. <span data-ttu-id="f9dfd-119">Po výběru možnosti MSMQ pro spuštění v zesíleném režimu vyžaduje počítač opětovné spuštění [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f9dfd-119">After you have selected MSMQ to run in hardened mode, the machine requires a re-boot on [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)].</span></span>  
  
7. <span data-ttu-id="f9dfd-120">Spusťte službu.</span><span class="sxs-lookup"><span data-stu-id="f9dfd-120">Run the service.</span></span>  
  
8. <span data-ttu-id="f9dfd-121">Spusťte klienta.</span><span class="sxs-lookup"><span data-stu-id="f9dfd-121">Run the client.</span></span> <span data-ttu-id="f9dfd-122">Ujistěte se, že jste změnili adresu koncového bodu tak, aby odkazovala na název počítače nebo IP adresu namísto localhost.</span><span class="sxs-lookup"><span data-stu-id="f9dfd-122">Ensure that you change the endpoint address to point to the machine name or IP address instead of localhost.</span></span> <span data-ttu-id="f9dfd-123">Klient pošle zprávu a ukončí se.</span><span class="sxs-lookup"><span data-stu-id="f9dfd-123">The client sends a message and exits.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9dfd-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f9dfd-124">Requirements</span></span>  
 <span data-ttu-id="f9dfd-125">Aby bylo možné tuto ukázku spustit, musí být služba IIS nainstalována kromě služby MSMQ do služby i klientských počítačů.</span><span class="sxs-lookup"><span data-stu-id="f9dfd-125">To run this sample, IIS must be installed on both the service and the client machines in addition to MSMQ.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="f9dfd-126">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="f9dfd-126">Demonstrates</span></span>  
 <span data-ttu-id="f9dfd-127">Ukázka ukazuje, jak odesílat zprávy ve frontě WCF pomocí služby MSMQ přes HTTP.</span><span class="sxs-lookup"><span data-stu-id="f9dfd-127">The sample demonstrates sending WCF queued messages using MSMQ over HTTP.</span></span> <span data-ttu-id="f9dfd-128">Tato služba se také nazývá zpráva SRMP.</span><span class="sxs-lookup"><span data-stu-id="f9dfd-128">This is also called SRMP messaging.</span></span> <span data-ttu-id="f9dfd-129">Při odeslání zprávy ve frontě přenáší MSMQ na odesílajícím počítači zprávy do přijímacího správce front přes přenos přes protokol TCP nebo HTTP.</span><span class="sxs-lookup"><span data-stu-id="f9dfd-129">When a queued message is sent, MSMQ on the sending machine transfers the messages to the receiving queue manager over TCP or HTTP transport.</span></span> <span data-ttu-id="f9dfd-130">Zvolíte-li protokol SRMP, uživatel určí možnost protokolu HTTP jako přenosu pro přenos fronty.</span><span class="sxs-lookup"><span data-stu-id="f9dfd-130">By choosing SRMP, the user indicates the choice of HTTP as a transport for queue transfer.</span></span> <span data-ttu-id="f9dfd-131">Protokol SRMP Secure umožňuje použití protokolu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="f9dfd-131">SRMP Secure enables the use of HTTPS.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f9dfd-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="f9dfd-132">Example</span></span>  
 <span data-ttu-id="f9dfd-133">Vzorový kód je založený na ukázce v transakčním režimu.</span><span class="sxs-lookup"><span data-stu-id="f9dfd-133">The sample code is based on the transacted sample.</span></span> <span data-ttu-id="f9dfd-134">Způsob odeslání zprávy do fronty a příjem zprávy z fronty pomocí protokolu SRMP je stejný jako odesílání a příjem zpráv pomocí nativního protokolu.</span><span class="sxs-lookup"><span data-stu-id="f9dfd-134">How you send a message to the queue and receive a message from the queue using SRMP is the same as sending and receiving messages using a Native protocol.</span></span>  
  
 <span data-ttu-id="f9dfd-135">Konfigurace klienta se změnila tak, aby označovala možnost protokolu přenosu fronty.</span><span class="sxs-lookup"><span data-stu-id="f9dfd-135">The configuration for the client is changed to indicate the choice of the queue transfer protocol.</span></span> <span data-ttu-id="f9dfd-136">Přenosový protokol fronty může být jeden z nativních, SRMP nebo SrmpSecure.</span><span class="sxs-lookup"><span data-stu-id="f9dfd-136">The queue transfer protocol can be one of Native, SRMP or SrmpSecure.</span></span> <span data-ttu-id="f9dfd-137">Ve výchozím nastavení je přenosový protokol nativní.</span><span class="sxs-lookup"><span data-stu-id="f9dfd-137">By default, the transfer protocol is Native.</span></span> <span data-ttu-id="f9dfd-138">Klient a služba v tomto příkladu určují v konfiguraci použití SRMP.</span><span class="sxs-lookup"><span data-stu-id="f9dfd-138">The client and service specify in the configuration to use SRMP in this example.</span></span>  
  
 <span data-ttu-id="f9dfd-139">V souvislosti se zabezpečením přenosu existují omezení protokolu SRMP.</span><span class="sxs-lookup"><span data-stu-id="f9dfd-139">There are limitations to SRMP in relation to transport security.</span></span> <span data-ttu-id="f9dfd-140">Výchozí zabezpečení přenosu služby MSMQ vyžaduje službu Active Directory, která vyžaduje, aby se správce fronty odesílání a přijímací správce fronty nacházel ve stejné doméně systému Windows.</span><span class="sxs-lookup"><span data-stu-id="f9dfd-140">The default MSMQ transport security requires Active Directory that requires that the sending queue manager and the receiving queue manager reside in the same Windows domain.</span></span> <span data-ttu-id="f9dfd-141">Při posílání zpráv přes hranice HTTP to není možné.</span><span class="sxs-lookup"><span data-stu-id="f9dfd-141">This is not possible when sending messages over HTTP boundary.</span></span> <span data-ttu-id="f9dfd-142">V takovém případě výchozí zabezpečení přenosu nefunguje.</span><span class="sxs-lookup"><span data-stu-id="f9dfd-142">As such, the default transport security does not work.</span></span> <span data-ttu-id="f9dfd-143">Pokud je požadováno zabezpečení přenosu, musí být zabezpečení přenosu nastaveno na certifikát.</span><span class="sxs-lookup"><span data-stu-id="f9dfd-143">The transport security must be set to Certificate if transport security is desired.</span></span> <span data-ttu-id="f9dfd-144">Zabezpečení zpráv lze také použít k zabezpečení zprávy.</span><span class="sxs-lookup"><span data-stu-id="f9dfd-144">Message security can also be used to secure the message.</span></span> <span data-ttu-id="f9dfd-145">V této ukázce je pro ilustraci zpráv protokolu SRMP vypnutá jak přenos, tak zabezpečení zpráv.</span><span class="sxs-lookup"><span data-stu-id="f9dfd-145">In this sample, both transport and message security is turned off to illustrate SRMP messaging.</span></span>  
  
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
  
 <span data-ttu-id="f9dfd-146">Spuštění ukázky poskytne následující výstup.</span><span class="sxs-lookup"><span data-stu-id="f9dfd-146">Running the sample yields the following output.</span></span>  
  
```  
Processing Purchase Order: 556b70be-31ee-4a3b-8df4-ed5e538015a4   
Customer: somecustomer.com   
OrderDetails   
    Order LineItem: 54 of Blue Widget @unit price: $29.99   
    Order LineItem: 890 of Red Widget @unit price: $45.89   
    Total cost of this order: $42461.56   
    Order status: Pending  
```  
  
> [!IMPORTANT]
> <span data-ttu-id="f9dfd-147">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="f9dfd-147">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f9dfd-148">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="f9dfd-148">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="f9dfd-149">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="f9dfd-149">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f9dfd-150">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="f9dfd-150">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\SRMP`  
