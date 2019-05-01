---
title: Ukázka třídy DataContractSerializer
ms.date: 03/30/2017
helpviewer_keywords:
- XML Formatter
ms.assetid: e0a2fe89-3534-48c8-aa3c-819862224571
ms.openlocfilehash: 3cfa4691376689bb8e7b1f8e8f41ed5d93ba0e61
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61990350"
---
# <a name="datacontractserializer-sample"></a>Ukázka třídy DataContractSerializer
Ukázka třídy DataContractSerializer ukazuje <xref:System.Runtime.Serialization.DataContractSerializer>, které provádí obecné serializace a deserializace služeb pro data třídy kontraktu. Ukázka vytvoří `Record` objektu, serializuje do datového proudu paměti a deserializuje zpět do jiného datového proudu paměti `Record` objekt pro demonstraci použití <xref:System.Runtime.Serialization.DataContractSerializer>. Ukázka pak serializuje `Record` pomocí binární zapisovače k předvedení jak zapisovač, který ovlivňuje serializace.  
  
> [!NOTE]
>  Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.  
  
 Kontraktu dat pro `Record` je znázorněno v následujícím ukázkovém kódu.  
  
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
  
 Vzorový kód vytvoří `Record` objekt s názvem `record1` zobrazí objekt.  
  
```csharp
Record record1 = new Record(1, 2, "+", 3);  
Console.WriteLine("Original record: {0}", record1.ToString());  
```  
  
 Ukázka pak používá <xref:System.Runtime.Serialization.DataContractSerializer> k serializaci `record1` do datový proud paměti.  
  
```csharp  
MemoryStream stream1 = new MemoryStream();  
  
//Serialize the Record object to a memory stream using DataContractSerializer.  
DataContractSerializer serializer = new DataContractSerializer(typeof(Record));  
serializer.WriteObject(stream1, record1);  
```  
  
 Dále Ukázka používá <xref:System.Runtime.Serialization.DataContractSerializer> deserializovat datový proud paměti zpět do nového `Record` objektu a zobrazí ji.  
  
```csharp  
stream1.Position = 0;  
  
//Deserialize the Record object back into a new record object.  
Record record2 = (Record)serializer.ReadObject(stream1);  
  
Console.WriteLine("Deserialized record: {0}", record2.ToString());  
```  
  
 Ve výchozím nastavení `DataContractSerializer` kóduje objekty do datového proudu pomocí textovou reprezentaci řetězce XML. Však můžete ovlivnit kódování XML předáváním různých zapisovače. Ukázka vytvoří binární zapisovače voláním <xref:System.Xml.XmlDictionaryWriter.CreateBinaryWriter%2A>. Pak předá modul pro zápis a záznam objekt serializátoru, který je při volání <xref:System.Runtime.Serialization.DataContractSerializer.WriteObjectContent%2A>. Nakonec vzorku vyprázdní modul pro zápis, informuje o délce datové proudy.  
  
```csharp  
MemoryStream stream2 = new MemoryStream();  
  
XmlDictionaryWriter binaryDictionaryWriter = XmlDictionaryWriter.CreateBinaryWriter(stream2);  
serializer.WriteObject(binaryDictionaryWriter, record1);  
binaryDictionaryWriter.Flush();  
  
//report the length of the streams  
Console.WriteLine("Text Stream is {0} bytes long", stream1.Length);  
Console.WriteLine("Binary Stream is {0} bytes long", stream2.Length);  
```  
  
 Při spuštění ukázky původní záznam a deserializovat záznam se zobrazí, za nímž následuje porovnání mezi binární kódování a délka kódování textu. Stisknutím klávesy ENTER v okně Klient vypnutí klient.  
  
```console  
Original record: Record: 1 + 2 = 3  
Deserialized record: Record: 1 + 2 = 3  
Text Stream is 233 bytes long  
Binary Stream is 156 bytes long  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1. Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Ke spuštění ukázky, spusťte z příkazového řádku zadáním client\bin\client.exe klienta.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\DataContractSerializer`  
