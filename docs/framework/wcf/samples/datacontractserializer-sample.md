---
title: "Ukázka třídy DataContractSerializer"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XML Formatter
ms.assetid: e0a2fe89-3534-48c8-aa3c-819862224571
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 99ef79ee9e17074989bcf5a2d4e586dc790373c2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="datacontractserializer-sample"></a><span data-ttu-id="94267-102">Ukázka třídy DataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="94267-102">DataContractSerializer Sample</span></span>
<span data-ttu-id="94267-103">Ukázka třídy DataContractSerializer ukazuje <xref:System.Runtime.Serialization.DataContractSerializer>, která provede obecné serializace a deserializace služeb pro data třídy kontrakt.</span><span class="sxs-lookup"><span data-stu-id="94267-103">The DataContractSerializer sample demonstrates the <xref:System.Runtime.Serialization.DataContractSerializer>, which performs general serialization and deserialization services for the data contract classes.</span></span> <span data-ttu-id="94267-104">Ukázka vytvoří `Record` objektu, serializuje na datový proud paměti a deserializuje datový proud paměti zpět do jiného `Record` objekt, který chcete ukazují použití <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="94267-104">The sample creates a `Record` object, serializes it to a memory stream and deserializes the memory stream back to another `Record` object to demonstrate the use of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="94267-105">Ukázka poté serializuje `Record` pomocí binární zapisovač k předvedení toho, jak zapisovač ovlivňuje serializace.</span><span class="sxs-lookup"><span data-stu-id="94267-105">The sample then serializes the `Record` object using a binary writer to demonstrate how the writer affects serialization.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="94267-106">V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="94267-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="94267-107">Kontraktu dat pro `Record` je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="94267-107">The data contract for `Record` is shown in the following sample code.</span></span>  
  
```  
[DataContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
internal class Record  
{  
    private double n1;  
    private double n2;  
    private string operation;  
    private double result;  
  
    internal Record(double n1, double n2, string operation, double result)  
    {  
        this.n1 = n1;  
        this.n2 = n2;  
        this.operation = operation;  
        this.result = result;  
    }  
  
    [DataMember]  
    internal double OperandNumberOne  
    {  
        get { return n1; }  
        set { n1 = value; }  
    }  
  
    [DataMember]  
    internal double OperandNumberTwo  
    {  
        get { return n2; }  
        set { n2 = value; }  
    }  
  
    [DataMember]  
    internal string Operation  
    {  
        get { return operation; }  
        set { operation = value; }  
    }  
  
    [DataMember]  
    internal double Result  
    {  
        get { return result; }  
        set { result = value; }  
    }  
  
    public override string ToString()  
    {  
        return string.Format("Record: {0} {1} {2} = {3}", n1,  
            operation, n2, result);  
    }  
}  
```  
  
 <span data-ttu-id="94267-108">Ukázkový kód vytvoří `Record` objekt s názvem `record1` pak zobrazí objekt.</span><span class="sxs-lookup"><span data-stu-id="94267-108">The sample code creates a `Record` object named `record1` then displays the object.</span></span>  
  
```  
Record record1 = new Record(1, 2, "+", 3);  
Console.WriteLine("Original record: {0}", record1.ToString());  
```  
  
 <span data-ttu-id="94267-109">Ukázka použije <xref:System.Runtime.Serialization.DataContractSerializer> k serializaci `record1` do datový proud paměti.</span><span class="sxs-lookup"><span data-stu-id="94267-109">The sample then uses the <xref:System.Runtime.Serialization.DataContractSerializer> to serialize `record1` into a memory stream.</span></span>  
  
```  
MemoryStream stream1 = new MemoryStream();  
  
//Serialize the Record object to a memory stream using DataContractSerializer.  
DataContractSerializer serializer = new DataContractSerializer(typeof(Record));  
serializer.WriteObject(stream1, record1);  
```  
  
 <span data-ttu-id="94267-110">V dalším kroku ukázce se používá <xref:System.Runtime.Serialization.DataContractSerializer> k deserializaci datový proud paměti zpět do nového `Record` objektu a zobrazí se.</span><span class="sxs-lookup"><span data-stu-id="94267-110">Next, the sample uses the <xref:System.Runtime.Serialization.DataContractSerializer> to deserialize the memory stream back into a new `Record` object and displays it.</span></span>  
  
```  
stream1.Position = 0;  
  
//Deserialize the Record object back into a new record object.  
Record record2 = (Record)serializer.ReadObject(stream1);  
  
Console.WriteLine("Deserialized record: {0}", record2.ToString());  
```  
  
 <span data-ttu-id="94267-111">Ve výchozím nastavení `DataContractSerializer` kóduje objekty do datového proudu pomocí textovou reprezentaci XML.</span><span class="sxs-lookup"><span data-stu-id="94267-111">By default, the `DataContractSerializer` encodes objects into a stream using a textual representation of XML.</span></span> <span data-ttu-id="94267-112">Můžete však ovlivnit kódování XML předáním v různých zapisovač.</span><span class="sxs-lookup"><span data-stu-id="94267-112">However, you can influence the encoding of the XML by passing in a different writer.</span></span> <span data-ttu-id="94267-113">Ukázka vytvoří binární zapisovač voláním <xref:System.Xml.XmlDictionaryWriter.CreateBinaryWriter%2A>.</span><span class="sxs-lookup"><span data-stu-id="94267-113">The sample creates a binary writer by calling <xref:System.Xml.XmlDictionaryWriter.CreateBinaryWriter%2A>.</span></span> <span data-ttu-id="94267-114">Potom předává Zapisovač a objekt záznam do serializátor při volání <xref:System.Runtime.Serialization.DataContractSerializer.WriteObjectContent%2A>.</span><span class="sxs-lookup"><span data-stu-id="94267-114">It then passes the writer and the record object to the serializer when it calls <xref:System.Runtime.Serialization.DataContractSerializer.WriteObjectContent%2A>.</span></span> <span data-ttu-id="94267-115">Nakonec vzorek vyprázdnění Zapisovač a sestavy na délce datové proudy.</span><span class="sxs-lookup"><span data-stu-id="94267-115">Finally, the sample flushes the writer and reports on the length of the streams.</span></span>  
  
```  
MemoryStream stream2 = new MemoryStream();  
  
XmlDictionaryWriter binaryDictionaryWriter = XmlDictionaryWriter.CreateBinaryWriter(stream2);  
serializer.WriteObject(binaryDictionaryWriter, record1);  
binaryDictionaryWriter.Flush();  
  
//report the length of the streams  
Console.WriteLine("Text Stream is {0} bytes long", stream1.Length);  
Console.WriteLine("Binary Stream is {0} bytes long", stream2.Length);  
```  
  
 <span data-ttu-id="94267-116">Když spustíte ukázku, zobrazují se původní záznam a deserializovat záznam následuje porovnání mezi binární kódování a délka kódování textu.</span><span class="sxs-lookup"><span data-stu-id="94267-116">When you run the sample, the original record and the deserialized record are displayed, followed by the comparison between the length of the text encoding and the binary encoding.</span></span> <span data-ttu-id="94267-117">Stisknutím klávesy ENTER v okně klienta vypnout klienta.</span><span class="sxs-lookup"><span data-stu-id="94267-117">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Original record: Record: 1 + 2 = 3  
Deserialized record: Record: 1 + 2 = 3  
Text Stream is 233 bytes long  
Binary Stream is 156 bytes long  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="94267-118">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="94267-118">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="94267-119">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="94267-119">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="94267-120">Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="94267-120">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="94267-121">Pokud chcete spustit ukázku, spusťte z příkazového řádku zadáním client\bin\client.exe klienta.</span><span class="sxs-lookup"><span data-stu-id="94267-121">To run the sample, start the client from the command prompt by typing client\bin\client.exe.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="94267-122">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="94267-122">The samples may already be installed on your machine.</span></span> <span data-ttu-id="94267-123">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="94267-123">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="94267-124">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="94267-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="94267-125">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="94267-125">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\DataContractSerializer`  
  
## <a name="see-also"></a><span data-ttu-id="94267-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="94267-126">See Also</span></span>
