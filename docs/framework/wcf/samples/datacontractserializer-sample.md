---
title: Ukázka třídy DataContractSerializer
ms.date: 03/30/2017
helpviewer_keywords:
- XML Formatter
ms.assetid: e0a2fe89-3534-48c8-aa3c-819862224571
ms.openlocfilehash: 41340eeb7e68bb1951da33fb2d5d93a7218d64b1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="datacontractserializer-sample"></a>Ukázka třídy DataContractSerializer
Ukázka třídy DataContractSerializer ukazuje <xref:System.Runtime.Serialization.DataContractSerializer>, která provede obecné serializace a deserializace služeb pro data třídy kontrakt. Ukázka vytvoří `Record` objektu, serializuje na datový proud paměti a deserializuje datový proud paměti zpět do jiného `Record` objekt, který chcete ukazují použití <xref:System.Runtime.Serialization.DataContractSerializer>. Ukázka poté serializuje `Record` pomocí binární zapisovač k předvedení toho, jak zapisovač ovlivňuje serializace.  
  
> [!NOTE]
>  V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.  
  
 Kontraktu dat pro `Record` je znázorněno v následujícím ukázkovém kódu.  
  
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
  
 Ukázkový kód vytvoří `Record` objekt s názvem `record1` pak zobrazí objekt.  
  
```  
Record record1 = new Record(1, 2, "+", 3);  
Console.WriteLine("Original record: {0}", record1.ToString());  
```  
  
 Ukázka použije <xref:System.Runtime.Serialization.DataContractSerializer> k serializaci `record1` do datový proud paměti.  
  
```  
MemoryStream stream1 = new MemoryStream();  
  
//Serialize the Record object to a memory stream using DataContractSerializer.  
DataContractSerializer serializer = new DataContractSerializer(typeof(Record));  
serializer.WriteObject(stream1, record1);  
```  
  
 V dalším kroku ukázce se používá <xref:System.Runtime.Serialization.DataContractSerializer> k deserializaci datový proud paměti zpět do nového `Record` objektu a zobrazí se.  
  
```  
stream1.Position = 0;  
  
//Deserialize the Record object back into a new record object.  
Record record2 = (Record)serializer.ReadObject(stream1);  
  
Console.WriteLine("Deserialized record: {0}", record2.ToString());  
```  
  
 Ve výchozím nastavení `DataContractSerializer` kóduje objekty do datového proudu pomocí textovou reprezentaci XML. Můžete však ovlivnit kódování XML předáním v různých zapisovač. Ukázka vytvoří binární zapisovač voláním <xref:System.Xml.XmlDictionaryWriter.CreateBinaryWriter%2A>. Potom předává Zapisovač a objekt záznam do serializátor při volání <xref:System.Runtime.Serialization.DataContractSerializer.WriteObjectContent%2A>. Nakonec vzorek vyprázdnění Zapisovač a sestavy na délce datové proudy.  
  
```  
MemoryStream stream2 = new MemoryStream();  
  
XmlDictionaryWriter binaryDictionaryWriter = XmlDictionaryWriter.CreateBinaryWriter(stream2);  
serializer.WriteObject(binaryDictionaryWriter, record1);  
binaryDictionaryWriter.Flush();  
  
//report the length of the streams  
Console.WriteLine("Text Stream is {0} bytes long", stream1.Length);  
Console.WriteLine("Binary Stream is {0} bytes long", stream2.Length);  
```  
  
 Když spustíte ukázku, zobrazují se původní záznam a deserializovat záznam následuje porovnání mezi binární kódování a délka kódování textu. Stisknutím klávesy ENTER v okně klienta vypnout klienta.  
  
```  
Original record: Record: 1 + 2 = 3  
Deserialized record: Record: 1 + 2 = 3  
Text Stream is 233 bytes long  
Binary Stream is 156 bytes long  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Pokud chcete spustit ukázku, spusťte z příkazového řádku zadáním client\bin\client.exe klienta.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\DataContractSerializer`  
  
## <a name="see-also"></a>Viz také
