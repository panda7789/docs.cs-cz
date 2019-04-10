---
title: Kódování MTOM
ms.date: 03/30/2017
ms.assetid: 820e316f-4ee1-4eb5-ae38-b6a536e8a14f
ms.openlocfilehash: abca7810e9d414808ddc195b95de05922edb6238
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59323132"
---
# <a name="mtom-encoding"></a><span data-ttu-id="dce02-102">Kódování MTOM</span><span class="sxs-lookup"><span data-stu-id="dce02-102">MTOM Encoding</span></span>
<span data-ttu-id="dce02-103">Tento příklad ukazuje použití kódování s WSHttpBinding zprávy zpráv přenosu optimalizace mechanismus (MTOM).</span><span class="sxs-lookup"><span data-stu-id="dce02-103">This sample demonstrates the use of the Message Transmission Optimization Mechanism (MTOM) message encoding with a WSHttpBinding.</span></span> <span data-ttu-id="dce02-104">MTOM je mechanismus pro předávání velké binární jejich přílohy pomocí zprávy protokolu SOAP jako nezpracovaný bajtů, umožňuje menší zprávy.</span><span class="sxs-lookup"><span data-stu-id="dce02-104">MTOM is a mechanism for transmitting large binary attachments with SOAP messages as raw bytes, allowing for smaller messages.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="dce02-105">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="dce02-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="dce02-106">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="dce02-106">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="dce02-107">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="dce02-107">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="dce02-108">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="dce02-108">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\MTOM`  
  
 <span data-ttu-id="dce02-109">Ve výchozím nastavení, odešle WSHttpBinding a přijaté zprávy jako normální text XML.</span><span class="sxs-lookup"><span data-stu-id="dce02-109">By default, the WSHttpBinding sends and received messages as normal text XML.</span></span> <span data-ttu-id="dce02-110">Pokud chcete povolit posílat a přijímat zprávy MTOM, nastavte `messageEncoding` atribut u vazby konfigurace (viz následující příklad kódu), nebo přímo u vazby pomocí `MessageEncoding` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="dce02-110">To enable sending and receiving MTOM messages, set the `messageEncoding` attribute on the binding's configuration (as in the following example code), or directly on the binding using the `MessageEncoding` property.</span></span> <span data-ttu-id="dce02-111">Služba nebo klient teď můžete odesílat a přijímat zprávy MTOM.</span><span class="sxs-lookup"><span data-stu-id="dce02-111">The service or client can now send and receive MTOM messages.</span></span>  
  
```xml  
<wsHttpBinding>  
  <binding name="WSHttpBinding_IUpload" messageEncoding="Mtom" />  
</wsHttpBinding>  
```  
  
 <span data-ttu-id="dce02-112">Kodér MTOM můžete optimalizovat pole bajtů a datových proudů.</span><span class="sxs-lookup"><span data-stu-id="dce02-112">The MTOM encoder can optimize arrays of bytes and streams.</span></span> <span data-ttu-id="dce02-113">V této ukázce se používá operaci `Stream` parametrů a proto se dá optimalizovat.</span><span class="sxs-lookup"><span data-stu-id="dce02-113">In this sample, the operation uses a `Stream` parameter and can therefore be optimized.</span></span>  

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
  public interface IUpload  
  {  
      [OperationContract]  
      int Upload(Stream data);  
  }  
```
  
 <span data-ttu-id="dce02-114">Kontrakt pro tuto ukázku zvolili přenáší binárních dat ve službě a přijímá počet bajtů odeslat jako návratovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="dce02-114">The contract chosen for this sample transmits binary data to the service and receives the number of bytes uploaded as the return value.</span></span> <span data-ttu-id="dce02-115">Když je služba nainstalována a klient je spuštěn, vytiskne číslo 1 000, což znamená, že byly přijaty všechny 1 000 bajtů.</span><span class="sxs-lookup"><span data-stu-id="dce02-115">When the service is installed and the client is run, it prints out the number 1000, which indicates that all 1000 bytes were received.</span></span> <span data-ttu-id="dce02-116">Zbývající část ve výstupu zobrazit seznam velikostí optimalizované a neoptimalizované zprávu pro různé datové části.</span><span class="sxs-lookup"><span data-stu-id="dce02-116">The remainder of the output lists optimized and non-optimized message sizes for various payloads.</span></span>  
  
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
  
 <span data-ttu-id="dce02-117">Účelem použití MTOM je k optimalizaci přenosu velké binární datové části.</span><span class="sxs-lookup"><span data-stu-id="dce02-117">The purpose for using MTOM is to optimize the transmission of large binary payloads.</span></span> <span data-ttu-id="dce02-118">Odeslání zprávy protokolu SOAP pomocí MTOM má znatelný režijní náklady pro malé binární datové části, ale změní na velké úspory, pokud se jejich průběhu několika tisíc bajtů.</span><span class="sxs-lookup"><span data-stu-id="dce02-118">Sending a SOAP message using MTOM has a noticeable overhead for small binary payloads, but becomes a great savings when they grow over a few thousand bytes.</span></span> <span data-ttu-id="dce02-119">Důvodem je, že normální text XML zakóduje binární data pomocí kódování Base64, který vyžaduje čtyři znaky pro každých třech bajtech a zvýší množství dat o jednu třetinu.</span><span class="sxs-lookup"><span data-stu-id="dce02-119">The reason for this is that normal text XML encodes binary data using Base64, which requires four characters for every three bytes, and increases the size of the data by one third.</span></span> <span data-ttu-id="dce02-120">Výsledkem je menší zprávy MTOM je moct přenášet binárních dat jako nezpracovaný bajtů, úspory času kódování/dekódování.</span><span class="sxs-lookup"><span data-stu-id="dce02-120">MTOM is able to transmit binary data as raw bytes, saving the encoding/decoding time and resulting is smaller messages.</span></span> <span data-ttu-id="dce02-121">Prahové hodnoty několika tisíc bajtů je malé ve srovnání s dnešní firemní dokumenty a digitální fotografie.</span><span class="sxs-lookup"><span data-stu-id="dce02-121">The threshold of a few thousand bytes is small when compared to today's business documents and digital photographs.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="dce02-122">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="dce02-122">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="dce02-123">Nainstalujte [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 pomocí následujícího příkazu.</span><span class="sxs-lookup"><span data-stu-id="dce02-123">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="dce02-124">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="dce02-124">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="dce02-125">K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="dce02-125">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="dce02-126">Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="dce02-126">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
