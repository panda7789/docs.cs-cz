---
title: Ukázka třídy DataContractSerializer
ms.date: 03/30/2017
helpviewer_keywords:
- XML Formatter
ms.assetid: e0a2fe89-3534-48c8-aa3c-819862224571
ms.openlocfilehash: 675b6b8a177fe5851c2abd1f785ac617de2cf37d
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045062"
---
# <a name="datacontractserializer-sample"></a>Ukázka třídy DataContractSerializer
Ukázka DataContractSerializer demonstruje <xref:System.Runtime.Serialization.DataContractSerializer>, který provádí obecné serializace a deserializaci služeb pro třídy kontraktu dat. Ukázka vytvoří `Record` objekt, zaserializace jej do paměťového proudu a deserializace paměťového proudu zpět na jiný `Record` objekt k <xref:System.Runtime.Serialization.DataContractSerializer>demonstraci použití. Ukázka potom serializaci `Record` objektu pomocí binárního zapisovače k předvedení, jak má zapisovač vliv na serializaci.  
  
> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.  
  
 Kontrakt dat pro `Record` je zobrazen v následujícím ukázkovém kódu.  
  
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
  
 Vzorový kód vytvoří `Record` objekt s názvem `record1` a potom zobrazí objekt.  
  
```csharp
Record record1 = new Record(1, 2, "+", 3);  
Console.WriteLine("Original record: {0}", record1.ToString());  
```  
  
 Ukázka potom používá <xref:System.Runtime.Serialization.DataContractSerializer> k serializaci `record1` do paměťového proudu.  
  
```csharp  
MemoryStream stream1 = new MemoryStream();  
  
//Serialize the Record object to a memory stream using DataContractSerializer.  
DataContractSerializer serializer = new DataContractSerializer(typeof(Record));  
serializer.WriteObject(stream1, record1);  
```  
  
 Dále ukázka používá <xref:System.Runtime.Serialization.DataContractSerializer> k deserializaci paměťového proudu zpátky do nového `Record` objektu a zobrazí jej.  
  
```csharp  
stream1.Position = 0;  
  
//Deserialize the Record object back into a new record object.  
Record record2 = (Record)serializer.ReadObject(stream1);  
  
Console.WriteLine("Deserialized record: {0}", record2.ToString());  
```  
  
 Ve výchozím nastavení `DataContractSerializer` kóduje objekty do datového proudu pomocí textové reprezentace XML. Můžete však ovlivnit kódování XML předáním jiného zapisovače. Ukázka vytvoří binární zapisovač pomocí volání <xref:System.Xml.XmlDictionaryWriter.CreateBinaryWriter%2A>. Pak předá serializátor a objekt záznamu do serializátoru při volání <xref:System.Runtime.Serialization.DataContractSerializer.WriteObjectContent%2A>. Nakonec ukázka vyprázdní zapisovač a sestavy o délce datových proudů.  
  
```csharp  
MemoryStream stream2 = new MemoryStream();  
  
XmlDictionaryWriter binaryDictionaryWriter = XmlDictionaryWriter.CreateBinaryWriter(stream2);  
serializer.WriteObject(binaryDictionaryWriter, record1);  
binaryDictionaryWriter.Flush();  
  
//report the length of the streams  
Console.WriteLine("Text Stream is {0} bytes long", stream1.Length);  
Console.WriteLine("Binary Stream is {0} bytes long", stream2.Length);  
```  
  
 Při spuštění ukázky se zobrazí původní záznam a deserializovaný záznam následovaný porovnáváním mezi délkou kódování textu a binárním kódováním. V okně klienta stiskněte klávesu ENTER pro vypnutí klienta.  
  
```console  
Original record: Record: 1 + 2 = 3  
Deserialized record: Record: 1 + 2 = 3  
Text Stream is 233 bytes long  
Binary Stream is 156 bytes long  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu sestavování [ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Chcete-li spustit ukázku, spusťte klienta z příkazového řádku zadáním příkazu client\bin\client.exe.  
  
> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\DataContractSerializer`  
