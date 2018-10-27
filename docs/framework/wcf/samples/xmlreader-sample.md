---
title: Ukázka třídy XmlReader
ms.date: 03/30/2017
helpviewer_keywords:
- XML Reader
ms.assetid: 60e5848d-7d9c-4ea5-bed9-22758c9ac16c
ms.openlocfilehash: 5ac97afd2efc1bb57a81f5cd2d78fed18ca3804d
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50039254"
---
# <a name="xmlreader-sample"></a><span data-ttu-id="c8de0-102">Ukázka třídy XmlReader</span><span class="sxs-lookup"><span data-stu-id="c8de0-102">XmlReader Sample</span></span>
<span data-ttu-id="c8de0-103">Ukázka třídy XmlReader ukazuje zpracování textu zprávy pomocí <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="c8de0-103">The XmlReader sample demonstrates the processing of a message body using an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="c8de0-104">Vzorek je založen na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md), který implementuje Kalkulačka služby.</span><span class="sxs-lookup"><span data-stu-id="c8de0-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements a calculator service.</span></span> <span data-ttu-id="c8de0-105">Operace další službu `Sum`, byla přidána, který přijme zprávu, která obsahuje pole hodnot, které chcete přidat najednou.</span><span class="sxs-lookup"><span data-stu-id="c8de0-105">An additional service operation, `Sum`, has been added that accepts a message that contains an array of values to add together.</span></span> <span data-ttu-id="c8de0-106">Služba načte zprávy pomocí <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="c8de0-106">The service reads the message using an <xref:System.Xml.XmlReader>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c8de0-107">Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="c8de0-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="c8de0-108">Kalkulačka rozhraní zahrnuje operace služby s názvem `Sum` , který přijme <xref:System.ServiceModel.Channels.Message> parametru, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="c8de0-108">The calculator interface includes a service operation named `Sum` that accepts a <xref:System.ServiceModel.Channels.Message> parameter, as shown in the following sample code.</span></span>  
  
```csharp
public interface ICalculator  
{  
    [OperationContract]  
    double Add(double n1, double n2);  
    [OperationContract]  
    double Subtract(double n1, double n2);  
    [OperationContract]  
    double Multiply(double n1, double n2);  
    [OperationContract]  
    double Divide(double n1, double n2);  
    [OperationContract]  
    Message Sum(Message message);  
}  
```  
  
 <span data-ttu-id="c8de0-109">Klient přistupuje k `Sum` prvním vytvoření pole celočíselných hodnot, pak vytváření zprávy z pole a potom voláním `Sum` metodu pomocí vytvořenou zprávu, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="c8de0-109">The client accesses `Sum` by first creating an array of integer values, then creating a message from the array, and then calling the `Sum` method using the created message, as shown in the following sample code.</span></span>  
  
```csharp
CalculatorClient client = new CalculatorClient();  
//...  

// Call the Sum service operation.  
int[] values = { 1, 2, 3, 4, 5 };  
using (new OperationContextScope(client.InnerChannel))  
{  
    Message request = Message.CreateMessage(OperationContext.Current.OutgoingMessageHeaders.MessageVersion, "http://Microsoft.ServiceModel.Samples/ICalculator/Sum", values);  
    Message reply = client.Sum(request);  
    int sum = reply.GetBody<int>();  
  
    Console.WriteLine("Sum(1,2,3,4,5) = {0}", sum);  
}  
```  
  
 <span data-ttu-id="c8de0-110">Ve službě, provádění operace služby `Sum` přistupuje k textu zprávy použijte <xref:System.Xml.XmlReader> objektu k iteraci v rámci hodnoty tak, aby součet.</span><span class="sxs-lookup"><span data-stu-id="c8de0-110">In the service, the implementation of the service operation `Sum` accesses the message body using an <xref:System.Xml.XmlReader> object to iterate through the values to sum.</span></span> <span data-ttu-id="c8de0-111"><xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> Metoda je volána pro přístup k textu zprávy, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="c8de0-111">The <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> method is called to access the message body, as shown in the following sample code.</span></span>  
  
```csharp  
public int Sum(Message message)  
{  
    int sum = 0;  
    string text = "";  
  
    //The body of the message contains a list of numbers that are read  
    //directly using an XmlReader.  
    XmlReader body = message.GetReaderAtBodyContents ();  
    while (body.Read())  
    {  
        text = body.ReadString().Trim();  
        if (text.Length>0)  
        {  
            sum += Convert.ToInt32(text);  
        }  
    }  
    body.Close();  
    Message response = Message.CreateMessage(  
       "http://Microsoft.ServiceModel.Samples/ICalculator/SumResponse",  
       sum);  
    return response;  
}  
```  
  
 <span data-ttu-id="c8de0-112">Když spustíte ukázku, požadavky a odpovědi z operace se zobrazují v okně konzoly klienta.</span><span class="sxs-lookup"><span data-stu-id="c8de0-112">When you run the sample, the requests and responses of the operation are displayed in the client console window.</span></span> <span data-ttu-id="c8de0-113">Stisknutím klávesy ENTER v okně Klient vypnutí klient.</span><span class="sxs-lookup"><span data-stu-id="c8de0-113">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Sum(1,2,3,4,5) = 15  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c8de0-114">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="c8de0-114">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="c8de0-115">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c8de0-115">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="c8de0-116">K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c8de0-116">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="c8de0-117">Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c8de0-117">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c8de0-118">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="c8de0-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c8de0-119">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="c8de0-119">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="c8de0-120">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="c8de0-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c8de0-121">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="c8de0-121">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\XmlReader`  
  
## <a name="see-also"></a><span data-ttu-id="c8de0-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="c8de0-122">See Also</span></span>
