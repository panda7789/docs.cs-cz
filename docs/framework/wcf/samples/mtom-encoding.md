---
title: "Kódování MTOM"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 820e316f-4ee1-4eb5-ae38-b6a536e8a14f
caps.latest.revision: "14"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 46984ea1ac08aa1128a4f32144285f590eafb6c0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="mtom-encoding"></a><span data-ttu-id="73609-102">Kódování MTOM</span><span class="sxs-lookup"><span data-stu-id="73609-102">MTOM Encoding</span></span>
<span data-ttu-id="73609-103">Tento příklad znázorňuje použití kódování s WSHttpBinding zprávy zpráva přenosu optimalizace mechanismus (MTOM).</span><span class="sxs-lookup"><span data-stu-id="73609-103">This sample demonstrates the use of the Message Transmission Optimization Mechanism (MTOM) message encoding with a WSHttpBinding.</span></span> <span data-ttu-id="73609-104">MTOM je mechanismus pro přenos velkých binární příloh protokolu SOAP zprávy nezpracovaná bajtů, umožňuje pro menší zprávy.</span><span class="sxs-lookup"><span data-stu-id="73609-104">MTOM is a mechanism for transmitting large binary attachments with SOAP messages as raw bytes, allowing for smaller messages.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="73609-105">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="73609-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="73609-106">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="73609-106">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="73609-107">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="73609-107">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="73609-108">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="73609-108">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\MTOM`  
  
 <span data-ttu-id="73609-109">Ve výchozím nastavení, odešle WSHttpBinding a přijaté zprávy jako běžný text XML.</span><span class="sxs-lookup"><span data-stu-id="73609-109">By default, the WSHttpBinding sends and received messages as normal text XML.</span></span> <span data-ttu-id="73609-110">Chcete-li povolit odesílání a přijímání zpráv MTOM, nastavte `messageEncoding` atribut v konfiguraci vazby (jako v následujícím příkladu kódu), nebo přímo na vazbu pomocí `MessageEncoding` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="73609-110">To enable sending and receiving MTOM messages, set the `messageEncoding` attribute on the binding's configuration (as in the following example code), or directly on the binding using the `MessageEncoding` property.</span></span> <span data-ttu-id="73609-111">Služba nebo klienta můžete nyní odesílat a přijímat zprávy MTOM.</span><span class="sxs-lookup"><span data-stu-id="73609-111">The service or client can now send and receive MTOM messages.</span></span>  
  
```xml  
<wsHttpBinding>  
  <binding name="WSHttpBinding_IUpload" messageEncoding="Mtom" />  
</wsHttpBinding>  
```  
  
 <span data-ttu-id="73609-112">Kodér MTOM můžete optimalizovat pole bajtů a datových proudů.</span><span class="sxs-lookup"><span data-stu-id="73609-112">The MTOM encoder can optimize arrays of bytes and streams.</span></span> <span data-ttu-id="73609-113">V této ukázce používá operaci `Stream` parametr a proto může být optimalizované.</span><span class="sxs-lookup"><span data-stu-id="73609-113">In this sample, the operation uses a `Stream` parameter and can therefore be optimized.</span></span>  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
  public interface IUpload  
  {  
      [OperationContract]  
      int Upload(Stream data);  
  }  
```  
  
 <span data-ttu-id="73609-114">Kontrakt zvolené pro tuto ukázku odesílá binární data do služby a získá počet bajtů odesílané jako návratovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="73609-114">The contract chosen for this sample transmits binary data to the service and receives the number of bytes uploaded as the return value.</span></span> <span data-ttu-id="73609-115">Když je služba nainstalována a klient je spuštěn, vytiskne číslo 1 000, což znamená, že bylo přijato všechny 1 000 bajtů.</span><span class="sxs-lookup"><span data-stu-id="73609-115">When the service is installed and the client is run, it prints out the number 1000, which indicates that all 1000 bytes were received.</span></span> <span data-ttu-id="73609-116">Zbývající část výstupu uvádí zprávy optimalizovaným a Neaktivní optimalizované velikosti pro různé datové části.</span><span class="sxs-lookup"><span data-stu-id="73609-116">The remainder of the output lists optimized and non-optimized message sizes for various payloads.</span></span>  
  
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
  
 <span data-ttu-id="73609-117">Účelem pro používání MTOM je za účelem optimalizace přenos velkých binární datové části.</span><span class="sxs-lookup"><span data-stu-id="73609-117">The purpose for using MTOM is to optimize the transmission of large binary payloads.</span></span> <span data-ttu-id="73609-118">Odesílání protokolu SOAP zprávy pomocí MTOM má znatelné režijní náklady pro malé binární datové části, ale změní skvělé úspory, pokud jejich výskytu prostřednictvím několika tisíc bajtů.</span><span class="sxs-lookup"><span data-stu-id="73609-118">Sending a SOAP message using MTOM has a noticeable overhead for small binary payloads, but becomes a great savings when they grow over a few thousand bytes.</span></span> <span data-ttu-id="73609-119">Důvodem je, že běžného textu XML zakóduje binární data pomocí Base64, který vyžaduje čtyři znaky pro každé tři bajtů a zvyšuje velikost dat o jednu třetinu.</span><span class="sxs-lookup"><span data-stu-id="73609-119">The reason for this is that normal text XML encodes binary data using Base64, which requires four characters for every three bytes, and increases the size of the data by one third.</span></span> <span data-ttu-id="73609-120">MTOM je schopen přenášet binární data nezpracovaná bajtů, což šetří čas kódování a dekódování a výsledná je menší zprávy.</span><span class="sxs-lookup"><span data-stu-id="73609-120">MTOM is able to transmit binary data as raw bytes, saving the encoding/decoding time and resulting is smaller messages.</span></span> <span data-ttu-id="73609-121">Prahové hodnoty několika tisíc bajtů je malé ve srovnání s dnešní obchodní dokumenty a digitální fotografie.</span><span class="sxs-lookup"><span data-stu-id="73609-121">The threshold of a few thousand bytes is small when compared to today's business documents and digital photographs.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="73609-122">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="73609-122">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="73609-123">Nainstalujte [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 pomocí následujícího příkazu.</span><span class="sxs-lookup"><span data-stu-id="73609-123">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  <span data-ttu-id="73609-124">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="73609-124">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3.  <span data-ttu-id="73609-125">Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="73609-125">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="73609-126">Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="73609-126">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73609-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="73609-127">See Also</span></span>
