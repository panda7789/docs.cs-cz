---
title: Ukázka třídy DataContractSerializer
ms.date: 03/30/2017
helpviewer_keywords:
- XML Formatter
ms.assetid: e0a2fe89-3534-48c8-aa3c-819862224571
ms.openlocfilehash: 5e1a471cc4cc43b2aa36143eeecc18f7ec17b81a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183780"
---
# <a name="datacontractserializer-sample"></a><span data-ttu-id="e1ed0-102">Ukázka třídy DataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="e1ed0-102">DataContractSerializer Sample</span></span>
<span data-ttu-id="e1ed0-103">DataContractSerializer ukázka ukazuje <xref:System.Runtime.Serialization.DataContractSerializer>, který provádí obecné serializace a deserializace služby pro třídy smlouvy dat.</span><span class="sxs-lookup"><span data-stu-id="e1ed0-103">The DataContractSerializer sample demonstrates the <xref:System.Runtime.Serialization.DataContractSerializer>, which performs general serialization and deserialization services for the data contract classes.</span></span> <span data-ttu-id="e1ed0-104">Ukázka vytvoří `Record` objekt, serializuje jej do datového proudu paměti a deserializuje `Record` datový proud paměti <xref:System.Runtime.Serialization.DataContractSerializer>zpět do jiného objektu, aby demonstroval použití .</span><span class="sxs-lookup"><span data-stu-id="e1ed0-104">The sample creates a `Record` object, serializes it to a memory stream and deserializes the memory stream back to another `Record` object to demonstrate the use of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="e1ed0-105">Ukázka pak serializuje `Record` objekt pomocí binárního zapisovače, aby ukázala, jak zapisovač ovlivňuje serializaci.</span><span class="sxs-lookup"><span data-stu-id="e1ed0-105">The sample then serializes the `Record` object using a binary writer to demonstrate how the writer affects serialization.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e1ed0-106">Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="e1ed0-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="e1ed0-107">Kontrakt dat `Record` pro je uveden v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="e1ed0-107">The data contract for `Record` is shown in the following sample code.</span></span>  
  
```csharp  
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
        return $"Record: {n1} {operation} {n2} = {result}";
    }  
}  
```  
  
 <span data-ttu-id="e1ed0-108">Ukázkový kód `Record` vytvoří `record1` objekt s názvem pak zobrazí objekt.</span><span class="sxs-lookup"><span data-stu-id="e1ed0-108">The sample code creates a `Record` object named `record1` then displays the object.</span></span>  
  
```csharp
Record record1 = new Record(1, 2, "+", 3);  
Console.WriteLine("Original record: {0}", record1.ToString());  
```  
  
 <span data-ttu-id="e1ed0-109">Ukázka pak <xref:System.Runtime.Serialization.DataContractSerializer> používá serializovat `record1` do datového proudu paměti.</span><span class="sxs-lookup"><span data-stu-id="e1ed0-109">The sample then uses the <xref:System.Runtime.Serialization.DataContractSerializer> to serialize `record1` into a memory stream.</span></span>  
  
```csharp  
MemoryStream stream1 = new MemoryStream();  
  
//Serialize the Record object to a memory stream using DataContractSerializer.  
DataContractSerializer serializer = new DataContractSerializer(typeof(Record));  
serializer.WriteObject(stream1, record1);  
```  
  
 <span data-ttu-id="e1ed0-110">Dále ukázka používá <xref:System.Runtime.Serialization.DataContractSerializer> k dekonstruovat datový proud `Record` paměti zpět do nového objektu a zobrazí jej.</span><span class="sxs-lookup"><span data-stu-id="e1ed0-110">Next, the sample uses the <xref:System.Runtime.Serialization.DataContractSerializer> to deserialize the memory stream back into a new `Record` object and displays it.</span></span>  
  
```csharp  
stream1.Position = 0;  
  
//Deserialize the Record object back into a new record object.  
Record record2 = (Record)serializer.ReadObject(stream1);  
  
Console.WriteLine("Deserialized record: {0}", record2.ToString());  
```  
  
 <span data-ttu-id="e1ed0-111">Ve výchozím `DataContractSerializer` nastavení kóduje objekty do datového proudu pomocí textové reprezentace XML.</span><span class="sxs-lookup"><span data-stu-id="e1ed0-111">By default, the `DataContractSerializer` encodes objects into a stream using a textual representation of XML.</span></span> <span data-ttu-id="e1ed0-112">Můžete však ovlivnit kódování XML předáním v jiném zapisovači.</span><span class="sxs-lookup"><span data-stu-id="e1ed0-112">However, you can influence the encoding of the XML by passing in a different writer.</span></span> <span data-ttu-id="e1ed0-113">Ukázka vytvoří binární zapisovač voláním <xref:System.Xml.XmlDictionaryWriter.CreateBinaryWriter%2A>.</span><span class="sxs-lookup"><span data-stu-id="e1ed0-113">The sample creates a binary writer by calling <xref:System.Xml.XmlDictionaryWriter.CreateBinaryWriter%2A>.</span></span> <span data-ttu-id="e1ed0-114">Potom předá zapisovač a objekt záznamu <xref:System.Runtime.Serialization.DataContractSerializer.WriteObjectContent%2A>serializátoru při volání .</span><span class="sxs-lookup"><span data-stu-id="e1ed0-114">It then passes the writer and the record object to the serializer when it calls <xref:System.Runtime.Serialization.DataContractSerializer.WriteObjectContent%2A>.</span></span> <span data-ttu-id="e1ed0-115">Nakonec ukázka vyprázdní zapisovač a zprávy o délce datových proudů.</span><span class="sxs-lookup"><span data-stu-id="e1ed0-115">Finally, the sample flushes the writer and reports on the length of the streams.</span></span>  
  
```csharp  
MemoryStream stream2 = new MemoryStream();  
  
XmlDictionaryWriter binaryDictionaryWriter = XmlDictionaryWriter.CreateBinaryWriter(stream2);  
serializer.WriteObject(binaryDictionaryWriter, record1);  
binaryDictionaryWriter.Flush();  
  
//report the length of the streams  
Console.WriteLine("Text Stream is {0} bytes long", stream1.Length);  
Console.WriteLine("Binary Stream is {0} bytes long", stream2.Length);  
```  
  
 <span data-ttu-id="e1ed0-116">Při spuštění ukázky se zobrazí původní záznam a rekonstruovaný záznam následovaný porovnáním délky kódování textu a binárního kódování.</span><span class="sxs-lookup"><span data-stu-id="e1ed0-116">When you run the sample, the original record and the deserialized record are displayed, followed by the comparison between the length of the text encoding and the binary encoding.</span></span> <span data-ttu-id="e1ed0-117">Stisknutím klávesy ENTER v okně klienta vypněte klienta.</span><span class="sxs-lookup"><span data-stu-id="e1ed0-117">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Original record: Record: 1 + 2 = 3  
Deserialized record: Record: 1 + 2 = 3  
Text Stream is 233 bytes long  
Binary Stream is 156 bytes long  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e1ed0-118">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="e1ed0-118">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="e1ed0-119">Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e1ed0-119">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="e1ed0-120">Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e1ed0-120">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="e1ed0-121">Chcete-li spustit ukázku, spusťte klienta z příkazového řádku zadáním client\bin\client.exe.</span><span class="sxs-lookup"><span data-stu-id="e1ed0-121">To run the sample, start the client from the command prompt by typing client\bin\client.exe.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="e1ed0-122">Ukázky mohou být již nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="e1ed0-122">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e1ed0-123">Před pokračováním zkontrolujte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="e1ed0-123">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="e1ed0-124">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="e1ed0-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e1ed0-125">Tato ukázka je umístěna v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="e1ed0-125">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\DataContractSerializer`  
