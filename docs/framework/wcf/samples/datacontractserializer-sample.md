---
title: Ukázka třídy DataContractSerializer
ms.date: 03/30/2017
helpviewer_keywords:
- XML Formatter
ms.assetid: e0a2fe89-3534-48c8-aa3c-819862224571
ms.openlocfilehash: 07c6d3b10f2a0478f8fb3835f0b040668c5013ce
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600007"
---
# <a name="datacontractserializer-sample"></a><span data-ttu-id="7a149-102">Ukázka třídy DataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="7a149-102">DataContractSerializer Sample</span></span>
<span data-ttu-id="7a149-103">Ukázka DataContractSerializer demonstruje <xref:System.Runtime.Serialization.DataContractSerializer> , který provádí obecné serializace a deserializaci služeb pro třídy kontraktu dat.</span><span class="sxs-lookup"><span data-stu-id="7a149-103">The DataContractSerializer sample demonstrates the <xref:System.Runtime.Serialization.DataContractSerializer>, which performs general serialization and deserialization services for the data contract classes.</span></span> <span data-ttu-id="7a149-104">Ukázka vytvoří `Record` objekt, zaserializace jej do paměťového proudu a deserializace paměťového proudu zpět na jiný `Record` objekt k demonstraci použití <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="7a149-104">The sample creates a `Record` object, serializes it to a memory stream and deserializes the memory stream back to another `Record` object to demonstrate the use of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="7a149-105">Ukázka potom serializaci `Record` objektu pomocí binárního zapisovače k předvedení, jak má zapisovač vliv na serializaci.</span><span class="sxs-lookup"><span data-stu-id="7a149-105">The sample then serializes the `Record` object using a binary writer to demonstrate how the writer affects serialization.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7a149-106">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="7a149-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="7a149-107">Kontrakt dat pro `Record` je zobrazen v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="7a149-107">The data contract for `Record` is shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="7a149-108">Vzorový kód vytvoří `Record` objekt s názvem `record1` a potom zobrazí objekt.</span><span class="sxs-lookup"><span data-stu-id="7a149-108">The sample code creates a `Record` object named `record1` then displays the object.</span></span>  
  
```csharp
Record record1 = new Record(1, 2, "+", 3);  
Console.WriteLine("Original record: {0}", record1.ToString());  
```  
  
 <span data-ttu-id="7a149-109">Ukázka potom používá <xref:System.Runtime.Serialization.DataContractSerializer> k serializaci `record1` do paměťového proudu.</span><span class="sxs-lookup"><span data-stu-id="7a149-109">The sample then uses the <xref:System.Runtime.Serialization.DataContractSerializer> to serialize `record1` into a memory stream.</span></span>  
  
```csharp  
MemoryStream stream1 = new MemoryStream();  
  
//Serialize the Record object to a memory stream using DataContractSerializer.  
DataContractSerializer serializer = new DataContractSerializer(typeof(Record));  
serializer.WriteObject(stream1, record1);  
```  
  
 <span data-ttu-id="7a149-110">Dále ukázka používá <xref:System.Runtime.Serialization.DataContractSerializer> k deserializaci paměťového proudu zpátky do nového `Record` objektu a zobrazí jej.</span><span class="sxs-lookup"><span data-stu-id="7a149-110">Next, the sample uses the <xref:System.Runtime.Serialization.DataContractSerializer> to deserialize the memory stream back into a new `Record` object and displays it.</span></span>  
  
```csharp  
stream1.Position = 0;  
  
//Deserialize the Record object back into a new record object.  
Record record2 = (Record)serializer.ReadObject(stream1);  
  
Console.WriteLine("Deserialized record: {0}", record2.ToString());  
```  
  
 <span data-ttu-id="7a149-111">Ve výchozím nastavení `DataContractSerializer` kóduje objekty do datového proudu pomocí textové reprezentace XML.</span><span class="sxs-lookup"><span data-stu-id="7a149-111">By default, the `DataContractSerializer` encodes objects into a stream using a textual representation of XML.</span></span> <span data-ttu-id="7a149-112">Můžete však ovlivnit kódování XML předáním jiného zapisovače.</span><span class="sxs-lookup"><span data-stu-id="7a149-112">However, you can influence the encoding of the XML by passing in a different writer.</span></span> <span data-ttu-id="7a149-113">Ukázka vytvoří binární zapisovač pomocí volání <xref:System.Xml.XmlDictionaryWriter.CreateBinaryWriter%2A> .</span><span class="sxs-lookup"><span data-stu-id="7a149-113">The sample creates a binary writer by calling <xref:System.Xml.XmlDictionaryWriter.CreateBinaryWriter%2A>.</span></span> <span data-ttu-id="7a149-114">Pak předá serializátor a objekt záznamu do serializátoru při volání <xref:System.Runtime.Serialization.DataContractSerializer.WriteObjectContent%2A> .</span><span class="sxs-lookup"><span data-stu-id="7a149-114">It then passes the writer and the record object to the serializer when it calls <xref:System.Runtime.Serialization.DataContractSerializer.WriteObjectContent%2A>.</span></span> <span data-ttu-id="7a149-115">Nakonec ukázka vyprázdní zapisovač a sestavy o délce datových proudů.</span><span class="sxs-lookup"><span data-stu-id="7a149-115">Finally, the sample flushes the writer and reports on the length of the streams.</span></span>  
  
```csharp  
MemoryStream stream2 = new MemoryStream();  
  
XmlDictionaryWriter binaryDictionaryWriter = XmlDictionaryWriter.CreateBinaryWriter(stream2);  
serializer.WriteObject(binaryDictionaryWriter, record1);  
binaryDictionaryWriter.Flush();  
  
//report the length of the streams  
Console.WriteLine("Text Stream is {0} bytes long", stream1.Length);  
Console.WriteLine("Binary Stream is {0} bytes long", stream2.Length);  
```  
  
 <span data-ttu-id="7a149-116">Při spuštění ukázky se zobrazí původní záznam a deserializovaný záznam následovaný porovnáváním mezi délkou kódování textu a binárním kódováním.</span><span class="sxs-lookup"><span data-stu-id="7a149-116">When you run the sample, the original record and the deserialized record are displayed, followed by the comparison between the length of the text encoding and the binary encoding.</span></span> <span data-ttu-id="7a149-117">V okně klienta stiskněte klávesu ENTER pro vypnutí klienta.</span><span class="sxs-lookup"><span data-stu-id="7a149-117">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Original record: Record: 1 + 2 = 3  
Deserialized record: Record: 1 + 2 = 3  
Text Stream is 233 bytes long  
Binary Stream is 156 bytes long  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="7a149-118">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="7a149-118">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="7a149-119">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7a149-119">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="7a149-120">Chcete-li sestavit edici C# nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7a149-120">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="7a149-121">Chcete-li spustit ukázku, spusťte klienta z příkazového řádku zadáním příkazu client\bin\client.exe.</span><span class="sxs-lookup"><span data-stu-id="7a149-121">To run the sample, start the client from the command prompt by typing client\bin\client.exe.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="7a149-122">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="7a149-122">The samples may already be installed on your machine.</span></span> <span data-ttu-id="7a149-123">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="7a149-123">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="7a149-124">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="7a149-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7a149-125">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="7a149-125">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\DataContractSerializer`  
