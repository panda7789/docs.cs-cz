---
title: Základní serializace
ms.date: 03/30/2017
helpviewer_keywords:
- binary serialization, basic serialization
- serialization, basic serialization
ms.assetid: d899d43c-335a-433e-a589-cd187192984f
dev_langs:
- CSharp
ms.openlocfilehash: a2dde9f795dfe31ff6ef821272a0d5e8d20e8b2f
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159946"
---
# <a name="basic-serialization"></a>Základní serializace

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

Nejjednodušší způsob, jak nastavit třídu jako serializovatelný, je označit ji <xref:System.SerializableAttribute> následujícím způsobem.  
  
```csharp  
[Serializable]  
public class MyObject {  
  public int n1 = 0;  
  public int n2 = 0;  
  public String str = null;  
}  
```  
  
Následující příklad kódu ukazuje, jak může být instance této třídy serializována do souboru.  
  
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
  
V tomto příkladu binární formátovací modul použije k serializaci. Vše, co potřebujete udělat, je vytvořit instanci datového proudu a formátovací modul, který chcete použít, a pak zavolat metodu **serializace** na formátovací modul. Datový proud a objekt určený k serializaci jsou poskytovány jako parametry pro toto volání. I když není ukázáno explicitně v tomto příkladu, bude serializována všechny proměnné členů třídy – i proměnné, které jsou označeny jako soukromé. V tomto aspektu se binární serializace liší od <xref:System.Xml.Serialization.XmlSerializer> třídy, která pouze serializovat veřejná pole. Informace o vyloučení členských proměnných z binární serializace naleznete v tématu [selektivní serializace](selective-serialization.md).  
  
Obnovení objektu zpět do původní stavu je stejně jednoduché. Nejprve vytvořte datový proud pro čtení a <xref:System.Runtime.Serialization.Formatter>a potom dejte pokyn k deserializaci objektu. Následující příklad kódu ukazuje, jak to lze provést.  
  
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
  
Výše použitá <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> je velice efektivní a vytváří proud kompaktních bajtů. Všechny objekty serializované pomocí tohoto formátování lze deserializovat také s ním, díky čemuž je ideální nástroj pro serializaci objektů, které k deserializaci na rozhraní .NET Framework. Je důležité si všimnout, že konstruktory nejsou volána, když je objekt deserializován. Toto omezení je umístěn na deserializace z hlediska výkonu. Však to porušuje některé obvyklé smluv, které modul runtime provede pomocí objektu zapisovače a vývojáři se ujistěte, že znají důsledky při označení objektu jako serializovatelný.  
  
Pokud je přenositelnost požadavek, použijte místo toho <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>. Jednoduše nahraďte **BinaryFormatter** v kódu výše pomocí **SoapFormatter** a volejte **serializaci** a **deserializaci** jako dříve. Tento formátovací modul vytváří následující výstup například využité nad.  
  
```xml  
<SOAP-ENV:Envelope  
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"  
  xmlns:xsd="http://www.w3.org/2001/XMLSchema"
  xmlns:SOAP-ENC="http://schemas.xmlsoap.org/soap/encoding/"  
  xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/"  
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
  
Je důležité si uvědomit, že [serializovatelný](xref:System.SerializableAttribute) atribut nelze zdědit. Je-li odvodit novou třídu z `MyObject`, musí být označen nové třídy s atributem také nebo nemůže být serializován. Například při pokusu o serializaci instance třídy níže se zobrazí <xref:System.Runtime.Serialization.SerializationException> informující o tom, že typ `MyStuff` není označen jako serializovatelný.  
  
```csharp  
public class MyStuff : MyObject
{  
  public int n3;  
}  
```  
  
 Použití [serializovatelného](xref:System.SerializableAttribute) atributu je pohodlné, ale má omezení, jak bylo uvedeno dříve. Informace o tom, kdy byste měli označit třídu pro serializaci, najdete v [pokynech k serializaci](serialization-guidelines.md) . Serializaci nelze přidat do třídy poté, co byla zkompilována.  
  
## <a name="see-also"></a>Viz také

- [Binární serializace](binary-serialization.md)
- [Serializace XML a SOAP](xml-and-soap-serialization.md)
