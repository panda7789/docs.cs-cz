---
title: Kódování MTOM
ms.date: 03/30/2017
ms.assetid: 820e316f-4ee1-4eb5-ae38-b6a536e8a14f
ms.openlocfilehash: 52fe91e5ab4967190d7654b232143adbf0a49d65
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70039271"
---
# <a name="mtom-encoding"></a><span data-ttu-id="7861a-102">Kódování MTOM</span><span class="sxs-lookup"><span data-stu-id="7861a-102">MTOM Encoding</span></span>
<span data-ttu-id="7861a-103">Tato ukázka demonstruje použití kódování zprávy MTOM (Message Transmission Optimization Mechanism) pomocí WSHttpBinding.</span><span class="sxs-lookup"><span data-stu-id="7861a-103">This sample demonstrates the use of the Message Transmission Optimization Mechanism (MTOM) message encoding with a WSHttpBinding.</span></span> <span data-ttu-id="7861a-104">MTOM je mechanismus pro přenos rozsáhlých binárních příloh se zprávami SOAP jako nezpracovaných bajtů, což umožňuje menší zprávy.</span><span class="sxs-lookup"><span data-stu-id="7861a-104">MTOM is a mechanism for transmitting large binary attachments with SOAP messages as raw bytes, allowing for smaller messages.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="7861a-105">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="7861a-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="7861a-106">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="7861a-106">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="7861a-107">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="7861a-107">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7861a-108">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="7861a-108">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\MTOM`  
  
 <span data-ttu-id="7861a-109">Ve výchozím nastavení WSHttpBinding odesílá a přijímá zprávy jako normální text XML.</span><span class="sxs-lookup"><span data-stu-id="7861a-109">By default, the WSHttpBinding sends and received messages as normal text XML.</span></span> <span data-ttu-id="7861a-110">Chcete-li povolit odesílání a příjem zpráv MTOM, `messageEncoding` nastavte atribut v konfiguraci vazby (jako v následujícím ukázkovém kódu) nebo přímo na vazbu `MessageEncoding` pomocí vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="7861a-110">To enable sending and receiving MTOM messages, set the `messageEncoding` attribute on the binding's configuration (as in the following example code), or directly on the binding using the `MessageEncoding` property.</span></span> <span data-ttu-id="7861a-111">Služba nebo klient teď může odesílat a přijímat zprávy MTOM.</span><span class="sxs-lookup"><span data-stu-id="7861a-111">The service or client can now send and receive MTOM messages.</span></span>  
  
```xml  
<wsHttpBinding>  
  <binding name="WSHttpBinding_IUpload" messageEncoding="Mtom" />  
</wsHttpBinding>  
```  
  
 <span data-ttu-id="7861a-112">Kodér MTOM může optimalizovat pole bajtů a datových proudů.</span><span class="sxs-lookup"><span data-stu-id="7861a-112">The MTOM encoder can optimize arrays of bytes and streams.</span></span> <span data-ttu-id="7861a-113">V této ukázce operace používá `Stream` parametr a může být proto optimalizována.</span><span class="sxs-lookup"><span data-stu-id="7861a-113">In this sample, the operation uses a `Stream` parameter and can therefore be optimized.</span></span>  

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
  public interface IUpload  
  {  
      [OperationContract]  
      int Upload(Stream data);  
  }  
```
  
 <span data-ttu-id="7861a-114">Kontrakt vybraný pro tento příklad odesílá binární data do služby a přijímá počet bajtů odeslaných jako návratovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="7861a-114">The contract chosen for this sample transmits binary data to the service and receives the number of bytes uploaded as the return value.</span></span> <span data-ttu-id="7861a-115">Po instalaci služby a spuštění klienta se zobrazí číslo 1000, které indikuje, že byly přijaty všechny 1000 bajtů.</span><span class="sxs-lookup"><span data-stu-id="7861a-115">When the service is installed and the client is run, it prints out the number 1000, which indicates that all 1000 bytes were received.</span></span> <span data-ttu-id="7861a-116">Zbývající část výstupu obsahuje optimalizované a neoptimalizované velikosti zpráv pro různé datové části.</span><span class="sxs-lookup"><span data-stu-id="7861a-116">The remainder of the output lists optimized and non-optimized message sizes for various payloads.</span></span>  
  
```  
Output:  
1000  
  
Text encoding with a 100 byte payload: 433  
MTOM encoding with a 100 byte payload: 912  
  
Text encoding with a 1000 byte payload: 1633  
MTOM encoding with a 1000 byte payload: 2080  
  
Text encoding with a 10000 byte payload: 13633  
MTOM encoding with a 10000 byte payload: 11080  
  
Text encoding with a 100000 byte payload: 133633  
MTOM encoding with a 100000 byte payload: 101080  
  
Text encoding with a 1000000 byte payload: 1333633  
MTOM encoding with a 1000000 byte payload: 1001080  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="7861a-117">Účelem použití nástroje MTOM je optimalizace přenosu rozsáhlých binárních datových částí.</span><span class="sxs-lookup"><span data-stu-id="7861a-117">The purpose for using MTOM is to optimize the transmission of large binary payloads.</span></span> <span data-ttu-id="7861a-118">Odeslání zprávy protokolu SOAP pomocí nástroje MTOM má znatelný nárok na malé binární datové části, ale stane se skvělým úsporou, pokud se rozrůstá o několik tisíc bajtů.</span><span class="sxs-lookup"><span data-stu-id="7861a-118">Sending a SOAP message using MTOM has a noticeable overhead for small binary payloads, but becomes a great savings when they grow over a few thousand bytes.</span></span> <span data-ttu-id="7861a-119">Důvodem je to, že normální text XML kóduje binární data pomocí Base64, který vyžaduje čtyři znaky pro každé tři bajty a zvětšuje velikost dat o jednu třetinu.</span><span class="sxs-lookup"><span data-stu-id="7861a-119">The reason for this is that normal text XML encodes binary data using Base64, which requires four characters for every three bytes, and increases the size of the data by one third.</span></span> <span data-ttu-id="7861a-120">MTOM dokáže přenášet binární data jako nezpracované bajty, ušetřit čas kódování a dekódování a výsledkem je menší počet zpráv.</span><span class="sxs-lookup"><span data-stu-id="7861a-120">MTOM is able to transmit binary data as raw bytes, saving the encoding/decoding time and resulting is smaller messages.</span></span> <span data-ttu-id="7861a-121">V porovnání s dnešními obchodními dokumenty a digitálními fotografiemi je malá prahová hodnota několika tisíc bajtů.</span><span class="sxs-lookup"><span data-stu-id="7861a-121">The threshold of a few thousand bytes is small when compared to today's business documents and digital photographs.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="7861a-122">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="7861a-122">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="7861a-123">Pomocí následujícího příkazu nainstalujte ASP.NET 4,0.</span><span class="sxs-lookup"><span data-stu-id="7861a-123">Install ASP.NET 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="7861a-124">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7861a-124">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="7861a-125">Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu sestavování [ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7861a-125">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="7861a-126">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7861a-126">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
