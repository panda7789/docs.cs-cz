---
title: SRMP
ms.date: 03/30/2017
ms.assetid: cf37078c-dcb4-45e0-acaf-2f196521b226
ms.openlocfilehash: c746897666ae78844df35c2989c803d852c3f70e
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33805496"
---
# <a name="srmp"></a><span data-ttu-id="4b050-102">SRMP</span><span class="sxs-lookup"><span data-stu-id="4b050-102">SRMP</span></span>
<span data-ttu-id="4b050-103">Tato ukázka ukazuje, jak provést zpracovaných komunikace ve frontě pomocí služby Řízení front zpráv (MSMQ) přes protokol HTTP.</span><span class="sxs-lookup"><span data-stu-id="4b050-103">This sample demonstrates how to perform transacted queued communication by using Message Queuing (MSMQ) over HTTP.</span></span>  
  
 <span data-ttu-id="4b050-104">V komunikaci ve frontě klient komunikuje se služby pomocí fronty.</span><span class="sxs-lookup"><span data-stu-id="4b050-104">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="4b050-105">Přesněji řečeno klient odešle zprávy do fronty.</span><span class="sxs-lookup"><span data-stu-id="4b050-105">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="4b050-106">Služba přijímá zprávy z fronty.</span><span class="sxs-lookup"><span data-stu-id="4b050-106">The service receives messages from the queue.</span></span> <span data-ttu-id="4b050-107">Služba a klient proto nemusíte používat současně na komunikaci pomocí fronty.</span><span class="sxs-lookup"><span data-stu-id="4b050-107">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>  
  
 <span data-ttu-id="4b050-108">MSMQ umožňuje použití protokolu HTTP (včetně použití protokolu HTTPS) k odesílání zpráv do fronty.</span><span class="sxs-lookup"><span data-stu-id="4b050-108">MSMQ enables the use of HTTP (including the use of HTTPS) to send messages to a queue.</span></span> <span data-ttu-id="4b050-109">V tomto příkladu jsme ukazují, že pomocí služby Windows Communication Foundation (WCF) zařazených do fronty komunikace a odesílání zpráv přes protokol HTTP.</span><span class="sxs-lookup"><span data-stu-id="4b050-109">In this example, we demonstrate using Windows Communication Foundation (WCF) queued communication and how to send messages over HTTP.</span></span> <span data-ttu-id="4b050-110">MSMQ používá protokol názvem SRMP, což je protokol založený na protokolu SOAP pro komunikaci přes protokol HTTP.</span><span class="sxs-lookup"><span data-stu-id="4b050-110">MSMQ uses a protocol called SRMP, which is a SOAP-based protocol for communication over HTTP.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="4b050-111">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="4b050-111">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="4b050-112">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4b050-112">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="4b050-113">Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4b050-113">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="4b050-114">Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4b050-114">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="4b050-115">Před spuštěním ukázky **přidat nebo odebrat součásti systému Windows**, ujistěte se, že služba MSMQ je nainstalována s podporou protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="4b050-115">Before running the sample in **Add/Remove Windows Components**, ensure that MSMQ is installed with HTTP support.</span></span> <span data-ttu-id="4b050-116">Instalace podpory protokolu HTTP automaticky nainstaluje Internetové informační služby (IIS) a přidává podporu protokolu ve službě IIS pro službu MSMQ.</span><span class="sxs-lookup"><span data-stu-id="4b050-116">Installing HTTP support automatically installs Internet Information Services (IIS) and adds the protocol support in IIS for MSMQ.</span></span>  
  
5.  <span data-ttu-id="4b050-117">Pokud chcete mít jistotu, že protokol HTTP se používá pro komunikaci, můžete povolit služby MSMQ v zesíleném režimu.</span><span class="sxs-lookup"><span data-stu-id="4b050-117">If you want to be certain that HTTP is used for communication, you can enable MSMQ to run in hardened mode.</span></span> <span data-ttu-id="4b050-118">Tím se zajistí, že žádné zprávy do fronty, všechny hostované na počítači můžete doručeny použití jakékoli přenosu jiným protokolem než HTTP.</span><span class="sxs-lookup"><span data-stu-id="4b050-118">This ensures that no messages to any queue hosted on the machine can arrive using any non-HTTP transport.</span></span>  
  
6.  <span data-ttu-id="4b050-119">Po výběru služby MSMQ v zesíleném režimu, daný počítač vyžaduje znovu spustit na [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4b050-119">After you have selected MSMQ to run in hardened mode, the machine requires a re-boot on [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)].</span></span>  
  
7.  <span data-ttu-id="4b050-120">Spusťte službu.</span><span class="sxs-lookup"><span data-stu-id="4b050-120">Run the service.</span></span>  
  
8.  <span data-ttu-id="4b050-121">Spuštění klienta.</span><span class="sxs-lookup"><span data-stu-id="4b050-121">Run the client.</span></span> <span data-ttu-id="4b050-122">Ujistěte se, že změníte adresa koncového bodu tak, aby odkazoval na název počítače nebo IP adresu místo localhost.</span><span class="sxs-lookup"><span data-stu-id="4b050-122">Ensure that you change the endpoint address to point to the machine name or IP address instead of localhost.</span></span> <span data-ttu-id="4b050-123">Klient odešle zprávu a ukončí.</span><span class="sxs-lookup"><span data-stu-id="4b050-123">The client sends a message and exits.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b050-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4b050-124">Requirements</span></span>  
 <span data-ttu-id="4b050-125">Pokud chcete tuto ukázku spustit, služba IIS musí být nainstalován na službu a klientské počítače kromě služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="4b050-125">To run this sample, IIS must be installed on both the service and the client machines in addition to MSMQ.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="4b050-126">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="4b050-126">Demonstrates</span></span>  
 <span data-ttu-id="4b050-127">Ukázka ukazuje odesílání WCF pomocí služby MSMQ přes HTTP zpráv zařazených do fronty.</span><span class="sxs-lookup"><span data-stu-id="4b050-127">The sample demonstrates sending WCF queued messages using MSMQ over HTTP.</span></span> <span data-ttu-id="4b050-128">To je také označován SRMP zasílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="4b050-128">This is also called SRMP messaging.</span></span> <span data-ttu-id="4b050-129">Když je odeslána zpráva zařazených do fronty, MSMQ na odesílání přenosů počítač zprávy, aby se využívá správce fronty pomocí přenosového protokolu TCP nebo HTTP.</span><span class="sxs-lookup"><span data-stu-id="4b050-129">When a queued message is sent, MSMQ on the sending machine transfers the messages to the receiving queue manager over TCP or HTTP transport.</span></span> <span data-ttu-id="4b050-130">Výběrem SRMP označuje uživatele volba HTTP přenos pro přenos fronty.</span><span class="sxs-lookup"><span data-stu-id="4b050-130">By choosing SRMP, the user indicates the choice of HTTP as a transport for queue transfer.</span></span> <span data-ttu-id="4b050-131">Zabezpečení SRMP umožňuje použití protokolu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="4b050-131">SRMP Secure enables the use of HTTPS.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4b050-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="4b050-132">Example</span></span>  
 <span data-ttu-id="4b050-133">Ukázkový kód je založena na zpracovaných vzorku.</span><span class="sxs-lookup"><span data-stu-id="4b050-133">The sample code is based on the transacted sample.</span></span> <span data-ttu-id="4b050-134">Jak odeslat zprávu do fronty a přijímat zprávy z fronty pomocí SRMP je stejný jako odesílání a přijímání zpráv pomocí nativního protokolu.</span><span class="sxs-lookup"><span data-stu-id="4b050-134">How you send a message to the queue and receive a message from the queue using SRMP is the same as sending and receiving messages using a Native protocol.</span></span>  
  
 <span data-ttu-id="4b050-135">Konfigurace pro klienta se změní na znamenat výběr protokol fronty přenosu.</span><span class="sxs-lookup"><span data-stu-id="4b050-135">The configuration for the client is changed to indicate the choice of the queue transfer protocol.</span></span> <span data-ttu-id="4b050-136">Protokol fronty přenosu může mít jednu z nativní, SRMP nebo SrmpSecure.</span><span class="sxs-lookup"><span data-stu-id="4b050-136">The queue transfer protocol can be one of Native, SRMP or SrmpSecure.</span></span> <span data-ttu-id="4b050-137">Ve výchozím nastavení je přenos protokolu nativní.</span><span class="sxs-lookup"><span data-stu-id="4b050-137">By default, the transfer protocol is Native.</span></span> <span data-ttu-id="4b050-138">Klient a služba zadejte v konfiguraci použít SRMP v tomto příkladu.</span><span class="sxs-lookup"><span data-stu-id="4b050-138">The client and service specify in the configuration to use SRMP in this example.</span></span>  
  
 <span data-ttu-id="4b050-139">Je třeba SRMP omezení ve vztahu k zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="4b050-139">There are limitations to SRMP in relation to transport security.</span></span> <span data-ttu-id="4b050-140">Zabezpečení přenosu služby MSMQ výchozí vyžaduje služby Active Directory, která vyžaduje, aby správce fronty odesílání a příjmu správce front jsou umístěny ve stejné doméně systému Windows.</span><span class="sxs-lookup"><span data-stu-id="4b050-140">The default MSMQ transport security requires Active Directory that requires that the sending queue manager and the receiving queue manager reside in the same Windows domain.</span></span> <span data-ttu-id="4b050-141">To není možné při odesílání zpráv přes HTTP hranici.</span><span class="sxs-lookup"><span data-stu-id="4b050-141">This is not possible when sending messages over HTTP boundary.</span></span> <span data-ttu-id="4b050-142">Zabezpečení přenosu výchozí jako takový nefunguje.</span><span class="sxs-lookup"><span data-stu-id="4b050-142">As such, the default transport security does not work.</span></span> <span data-ttu-id="4b050-143">Zabezpečení přenosu musí být nastavena na certifikát, pokud se požaduje zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="4b050-143">The transport security must be set to Certificate if transport security is desired.</span></span> <span data-ttu-id="4b050-144">Zabezpečení zpráv lze také zabezpečit zprávy.</span><span class="sxs-lookup"><span data-stu-id="4b050-144">Message security can also be used to secure the message.</span></span> <span data-ttu-id="4b050-145">V této ukázce je zabezpečení přenosu a zprávy pro ilustraci zasílání zpráv SRMP vypnutý.</span><span class="sxs-lookup"><span data-stu-id="4b050-145">In this sample, both transport and message security is turned off to illustrate SRMP messaging.</span></span>  
  
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
          <security mode="None"></security>  
        </binding>  
      </netMsmqBinding>  
    </bindings>  
  </system.serviceModel>  
  
</configuration>  
```  
  
 <span data-ttu-id="4b050-146">Spuštění ukázky vypočítá následující výstup.</span><span class="sxs-lookup"><span data-stu-id="4b050-146">Running the sample yields the following output.</span></span>  
  
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
>  <span data-ttu-id="4b050-147">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="4b050-147">The samples may already be installed on your machine.</span></span> <span data-ttu-id="4b050-148">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="4b050-148">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="4b050-149">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="4b050-149">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4b050-150">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="4b050-150">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\SRMP`  
  
## <a name="see-also"></a><span data-ttu-id="4b050-151">Viz také</span><span class="sxs-lookup"><span data-stu-id="4b050-151">See Also</span></span>
