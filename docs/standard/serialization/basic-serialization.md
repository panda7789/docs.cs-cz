---
title: "Základní serializace"
ms.date: 03/30/2017
ms.prod: .net
ms.topic: article
helpviewer_keywords:
- binary serialization, basic serialization
- serialization, basic serialization
ms.assetid: d899d43c-335a-433e-a589-cd187192984f
dev_langs:
- CSharp
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 822b05758c7751e6f82f7a7f46a219d2c0001cd1
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="basic-serialization"></a>Základní serializace

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

Nejjednodušší způsob, jak vytvořit třídu serializovatelný je označte ji s <xref:System.SerializableAttribute> následujícím způsobem.  
  
```csharp  
[Serializable]  
public class MyObject {  
  public int n1 = 0;  
  public int n2 = 0;  
  public String str = null;  
}  
```  
  
Následující příklad kódu ukazuje, jak lze do souboru serializovat instance této třídy.  
  
```csharp  
MyObject obj = new MyObject();  
obj.n1 = 1;  
obj.n2 = 24;  
obj.str = "Some String";  
IFormatter formatter = new BinaryFormatter();  
Stream stream = new FileStream("MyFile.bin", FileMode.Create, FileAccess.Write, FileShare.None);  
formatter.Serialize(stream, obj);  
stream.Close();  
```  
  
V tomto příkladu binární formátovací modul použije k serializaci. Je potřeba udělat je vytvoření instance datového proudu a formátovací modul, který chcete použít a pak zavolají **serializace** metodu formátování. Datový proud a objekt určený k serializaci jsou poskytovány jako parametry pro toto volání. I když není ukázáno explicitně v tomto příkladu, bude serializována všechny proměnné členů třídy – i proměnné, které jsou označeny jako soukromé. V tento aspekt binární serializace se liší od <xref:System.Xml.Serialization.XmlSerializer> třídy, která pouze serializuje veřejná pole. Informace na vyloučení členské proměnné z binární serializace najdete v tématu [selektivní serializace](selective-serialization.md).  
  
Obnovení objektu zpět do původní stavu je stejně jednoduché. Nejprve vytvořte datový proud pro čtení a <xref:System.Runtime.Serialization.Formatter>, a potom dá pokyn formátovací modul k deserializaci objektu. Následující příklad kódu ukazuje, jak to lze provést.  
  
```csharp  
IFormatter formatter = new BinaryFormatter();  
Stream stream = new FileStream("MyFile.bin", FileMode.Open, FileAccess.Read, FileShare.Read);  
MyObject obj = (MyObject) formatter.Deserialize(stream);  
stream.Close();  
  
// Here's the proof.  
Console.WriteLine("n1: {0}", obj.n1);  
Console.WriteLine("n2: {0}", obj.n2);  
Console.WriteLine("str: {0}", obj.str);  
```  
  
<xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> Používá vyšší je velmi efektivně a vytvoří datový proud s compact bajtů. Všechny objekty serializované pomocí tohoto formátování lze deserializovat také s ním, díky čemuž je ideální nástroj pro serializaci objektů, které k deserializaci na rozhraní .NET Framework. Je důležité si všimnout, že konstruktory nejsou volána, když je objekt deserializován. Toto omezení je umístěn na deserializace z hlediska výkonu. Však to porušuje některé obvyklé smluv, které modul runtime provede pomocí objektu zapisovače a vývojáři se ujistěte, že znají důsledky při označení objektu jako serializovatelný.  
  
Pokud přenositelnost je vyžadováno, použijte <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> místo. Jednoduše nahradit **BinaryFormatter** v kódu výše s **SoapFormatter,** a volání **serializace** a **Deserialize** jako předtím. Tento formátovací modul vytváří následující výstup například využité nad.  
  
```xml  
<SOAP-ENV:Envelope  
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"  
  xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
  xmlns:SOAP- ENC="http://schemas.xmlsoap.org/soap/encoding/"  
  xmlns:SOAP- ENV="http://schemas.xmlsoap.org/soap/envelope/"  
  SOAP-ENV:encodingStyle=  
  "http://schemas.microsoft.com/soap/encoding/clr/1.0"  
  "http://schemas.xmlsoap.org/soap/encoding/"  
  xmlns:a1="http://schemas.microsoft.com/clr/assem/ToFile">  
  
  <SOAP-ENV:Body>  
    <a1:MyObject id="ref-1">  
      <n1>1</n1>  
      <n2>24</n2>  
      <str id="ref-3">Some String</str>  
    </a1:MyObject>  
  </SOAP-ENV:Body>  
</SOAP-ENV:Envelope>  
```  
  
Je důležité si uvědomit, že [Serializable](xref:System.SerializableAttribute) atribut nemůže být dědí. Je-li odvodit novou třídu z `MyObject`, musí být označen nové třídy s atributem také nebo nemůže být serializován. Například při pokusu o serializaci instance třídy níže získáte <xref:System.Runtime.Serialization.SerializationException> vás informuje o který `MyStuff` typ není označen jako serializovatelný.  
  
```csharp  
public class MyStuff : MyObject   
{  
  public int n3;  
}  
```  
  
 Pomocí [Serializable](xref:System.SerializableAttribute) atribut je vhodné, ale má omezení popsaná ukázán. Odkazovat [serializace pokyny](serialization-guidelines.md) informace o kdy byste měli označit třídy pro serializaci. Serializace nelze přidat do třídy, poté, co byl zkompilován.  
  
## <a name="see-also"></a>Viz také  
 [Binární serializace](binary-serialization.md)  
 [Serializace XML a SOAP](xml-and-soap-serialization.md)
