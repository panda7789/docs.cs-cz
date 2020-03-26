---
title: Základní serializace
ms.date: 03/30/2017
helpviewer_keywords:
- binary serialization, basic serialization
- serialization, basic serialization
ms.assetid: d899d43c-335a-433e-a589-cd187192984f
dev_langs:
- CSharp
ms.openlocfilehash: ce86f7897c5c117c4fd6f1eabc4c8b802103261c
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2020
ms.locfileid: "80248027"
---
# <a name="basic-serialization"></a>Základní serializace

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

Nejjednodušší způsob, jak třídy serializovatelné je označit <xref:System.SerializableAttribute> ji následujícím způsobem.  
  
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
  
V tomto příkladu binární formátovací modul použije k serializaci. Vše, co musíte udělat, je vytvořit instanci datového proudu a modul pro vytváření modulu umožňuje použít a potom volat **Serialize** metoda na modul pro vytváření forových kláves. Datový proud a objekt určený k serializaci jsou poskytovány jako parametry pro toto volání. I když není ukázáno explicitně v tomto příkladu, bude serializována všechny proměnné členů třídy – i proměnné, které jsou označeny jako soukromé. V tomto ohledu se binární serializace liší od <xref:System.Xml.Serialization.XmlSerializer> třídy, která pouze serializuje veřejná pole. Informace o vyloučení členských proměnných z binární serializace naleznete v [tématu Selektivní serializace](selective-serialization.md).  
  
Obnovení objektu zpět do původní stavu je stejně jednoduché. Nejprve vytvořte datový proud <xref:System.Runtime.Serialization.Formatter>pro čtení a a a potom dáte pokyn, aby modul pro formátování rekonstruoval objekt. Následující příklad kódu ukazuje, jak to lze provést.  
  
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
  
Výše <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> uvedené použité je velmi efektivní a vytváří kompaktní bajt ový proud. Všechny objekty serializované pomocí tohoto formátování lze deserializovat také s ním, díky čemuž je ideální nástroj pro serializaci objektů, které k deserializaci na rozhraní .NET Framework. Je důležité si všimnout, že konstruktory nejsou volána, když je objekt deserializován. Toto omezení je umístěn na deserializace z hlediska výkonu. Však to porušuje některé obvyklé smluv, které modul runtime provede pomocí objektu zapisovače a vývojáři se ujistěte, že znají důsledky při označení objektu jako serializovatelný.  
  
Pokud přenositelnost je požadavek, použijte <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> místo. Jednoduše nahradit **BinaryFormatter** ve výše uvedeném kódu **soapformatter** a volání **Serializovat** a **Deserializovat** jako dříve. Tento formátovací modul vytváří následující výstup například využité nad.  
  
```xml  
<SOAP-ENV:Envelope  
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"  
  xmlns:xsd="http://www.w3.org/2001/XMLSchema"
  xmlns:SOAP-ENC="http://schemas.xmlsoap.org/soap/encoding/"  
  xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/"  
  SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/"  
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
  
Je důležité si uvědomit, že [serializovatelný](xref:System.SerializableAttribute) atribut nelze zdědit. Je-li odvodit novou třídu z `MyObject`, musí být označen nové třídy s atributem také nebo nemůže být serializován. Například při pokusu o serializaci instance třídy níže, dostanete <xref:System.Runtime.Serialization.SerializationException> s informací, `MyStuff` že typ není označen jako serializovatelné.  
  
```csharp  
public class MyStuff : MyObject
{  
  public int n3;  
}  
```  
  
 Použití [Serializable](xref:System.SerializableAttribute) atribut je vhodné, ale má omezení, jak bylo dříve prokázáno. Informace o tom, kdy byste měli označit třídu pro serializaci, naleznete v pokynech pro [serializaci.](serialization-guidelines.md) Serializaci nelze přidat do třídy po kompilaci.  
  
## <a name="see-also"></a>Viz také

- [Binární serializace](binary-serialization.md)
- [Serializace XML a SOAP](xml-and-soap-serialization.md)
