---
title: Kódování MTOM
ms.date: 03/30/2017
ms.assetid: 820e316f-4ee1-4eb5-ae38-b6a536e8a14f
ms.openlocfilehash: 83dbe9e51da1cc9e55bfffb862e2601d70fc7695
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144380"
---
# <a name="mtom-encoding"></a><span data-ttu-id="b73bd-102">Kódování MTOM</span><span class="sxs-lookup"><span data-stu-id="b73bd-102">MTOM Encoding</span></span>
<span data-ttu-id="b73bd-103">Tato ukázka ukazuje použití kódování zprávy mechanismus optimalizace přenosu zpráv (MTOM) s WSHttpBinding.</span><span class="sxs-lookup"><span data-stu-id="b73bd-103">This sample demonstrates the use of the Message Transmission Optimization Mechanism (MTOM) message encoding with a WSHttpBinding.</span></span> <span data-ttu-id="b73bd-104">MTOM je mechanismus pro přenos velkých binárních příloh s SOAP zprávy jako nezpracované bajty, umožňující menší zprávy.</span><span class="sxs-lookup"><span data-stu-id="b73bd-104">MTOM is a mechanism for transmitting large binary attachments with SOAP messages as raw bytes, allowing for smaller messages.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="b73bd-105">Ukázky mohou být již nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="b73bd-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b73bd-106">Před pokračováním zkontrolujte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="b73bd-106">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="b73bd-107">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="b73bd-107">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b73bd-108">Tato ukázka je umístěna v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="b73bd-108">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\MTOM`  
  
 <span data-ttu-id="b73bd-109">Ve výchozím nastavení wshttpbinding odesílá a přijímá zprávy jako normální textový XML.</span><span class="sxs-lookup"><span data-stu-id="b73bd-109">By default, the WSHttpBinding sends and received messages as normal text XML.</span></span> <span data-ttu-id="b73bd-110">Chcete-li povolit odesílání a `messageEncoding` přijímání zpráv MTOM, nastavte atribut na konfiguraci vazby (jako `MessageEncoding` v následujícím příkladu kódu) nebo přímo na vazbě pomocí vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="b73bd-110">To enable sending and receiving MTOM messages, set the `messageEncoding` attribute on the binding's configuration (as in the following example code), or directly on the binding using the `MessageEncoding` property.</span></span> <span data-ttu-id="b73bd-111">Služba nebo klient nyní může odesílat a přijímat zprávy MTOM.</span><span class="sxs-lookup"><span data-stu-id="b73bd-111">The service or client can now send and receive MTOM messages.</span></span>  
  
```xml  
<wsHttpBinding>  
  <binding name="WSHttpBinding_IUpload" messageEncoding="Mtom" />  
</wsHttpBinding>  
```  
  
 <span data-ttu-id="b73bd-112">Kodér MTOM může optimalizovat pole bajtů a datových proudů.</span><span class="sxs-lookup"><span data-stu-id="b73bd-112">The MTOM encoder can optimize arrays of bytes and streams.</span></span> <span data-ttu-id="b73bd-113">V této ukázce `Stream` operace používá parametr a proto může být optimalizována.</span><span class="sxs-lookup"><span data-stu-id="b73bd-113">In this sample, the operation uses a `Stream` parameter and can therefore be optimized.</span></span>  

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
  public interface IUpload  
  {  
      [OperationContract]  
      int Upload(Stream data);  
  }  
```
  
 <span data-ttu-id="b73bd-114">Smlouva zvolená pro tento vzorek přenáší binární data do služby a přijímá počet bajtů odeslaných jako vrácená hodnota.</span><span class="sxs-lookup"><span data-stu-id="b73bd-114">The contract chosen for this sample transmits binary data to the service and receives the number of bytes uploaded as the return value.</span></span> <span data-ttu-id="b73bd-115">Když je služba nainstalována a klient je spuštěn, vytiskne číslo 1000, což znamená, že bylo přijato všech 1000 bajtů.</span><span class="sxs-lookup"><span data-stu-id="b73bd-115">When the service is installed and the client is run, it prints out the number 1000, which indicates that all 1000 bytes were received.</span></span> <span data-ttu-id="b73bd-116">Zbývající část výstupu obsahuje optimalizované a neoptimalizované velikosti zpráv pro různé datové části.</span><span class="sxs-lookup"><span data-stu-id="b73bd-116">The remainder of the output lists optimized and non-optimized message sizes for various payloads.</span></span>  
  
```console
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
  
 <span data-ttu-id="b73bd-117">Účelem použití MTOM je optimalizovat přenos velkých binárních datových částí.</span><span class="sxs-lookup"><span data-stu-id="b73bd-117">The purpose for using MTOM is to optimize the transmission of large binary payloads.</span></span> <span data-ttu-id="b73bd-118">Odesílání zprávy SOAP pomocí MTOM má znatelnou režii pro malé binární datové části, ale stane se velké úspory při jejich růstu přes několik tisíc bajtů.</span><span class="sxs-lookup"><span data-stu-id="b73bd-118">Sending a SOAP message using MTOM has a noticeable overhead for small binary payloads, but becomes a great savings when they grow over a few thousand bytes.</span></span> <span data-ttu-id="b73bd-119">Důvodem je, že normální text XML kóduje binární data pomocí Base64, který vyžaduje čtyři znaky pro každé tři bajty a zvyšuje velikost dat o jednu třetinu.</span><span class="sxs-lookup"><span data-stu-id="b73bd-119">The reason for this is that normal text XML encodes binary data using Base64, which requires four characters for every three bytes, and increases the size of the data by one third.</span></span> <span data-ttu-id="b73bd-120">MTOM je schopen přenášet binární data jako nezpracované bajty, ukládání kódování / dekódování čas a výsledné je menší zprávy.</span><span class="sxs-lookup"><span data-stu-id="b73bd-120">MTOM is able to transmit binary data as raw bytes, saving the encoding/decoding time and resulting is smaller messages.</span></span> <span data-ttu-id="b73bd-121">Práh několika tisíc bajtů je malý ve srovnání s dnešními obchodními dokumenty a digitálními fotografiemi.</span><span class="sxs-lookup"><span data-stu-id="b73bd-121">The threshold of a few thousand bytes is small when compared to today's business documents and digital photographs.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b73bd-122">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="b73bd-122">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="b73bd-123">Nainstalujte ASP.NET 4.0 pomocí následujícího příkazu.</span><span class="sxs-lookup"><span data-stu-id="b73bd-123">Install ASP.NET 4.0 using the following command.</span></span>  
  
    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="b73bd-124">Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b73bd-124">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="b73bd-125">Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b73bd-125">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="b73bd-126">Chcete-li spustit ukázku v konfiguraci jednoho nebo více počítačů, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b73bd-126">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
