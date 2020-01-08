---
title: Čtení dat objektů ze souboru XML (C#)
ms.date: 07/20/2015
ms.assetid: 6ad60d96-a4d9-48e6-a8b0-d7f6f803cafa
ms.openlocfilehash: 2da5919c11ed2d6e43f4f9fc406f43e3ed48060f
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346434"
---
# <a name="how-to-read-object-data-from-an-xml-file-c"></a>Čtení dat objektů ze souboru XML (C#)
Tento příklad načte data objektů, která byla dříve zapsána do souboru XML pomocí třídy <xref:System.Xml.Serialization.XmlSerializer>.  
  
## <a name="example"></a>Příklad  
  
```csharp  
public class Book  
{  
    public String title;  
}         
  
public void ReadXML()  
{  
    // First write something so that there is something to read ...  
    var b = new Book { title = "Serialization Overview" };  
    var writer = new System.Xml.Serialization.XmlSerializer(typeof(Book));  
    var wfile = new System.IO.StreamWriter(@"c:\temp\SerializationOverview.xml");  
    writer.Serialize(wfile, b);  
    wfile.Close();  
  
    // Now we can read the serialized book ...  
    System.Xml.Serialization.XmlSerializer reader =   
        new System.Xml.Serialization.XmlSerializer(typeof(Book));  
    System.IO.StreamReader file = new System.IO.StreamReader(  
        @"c:\temp\SerializationOverview.xml");  
    Book overview =  (Book)reader.Deserialize(file);  
    file.Close();  
  
    Console.WriteLine(overview.title);  
  
}  
```  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
Nahraďte název souboru "c:\temp\SerializationOverview.xml" názvem souboru, který obsahuje Serializovaná data. Další informace o serializaci dat naleznete v tématu [jak zapisovat data objektů do souboru XML (C#)](./how-to-write-object-data-to-an-xml-file.md).
  
 Třída musí mít veřejný konstruktor bez parametrů.  
  
 Pouze veřejné vlastnosti a pole jsou deserializovány.  
  
## <a name="robust-programming"></a>Robustní programování  
 Následující podmínky mohou způsobit výjimku:  
  
- Serializovaná třída nemá veřejný konstruktor bez parametrů.  
  
- Data v souboru reprezentují data z třídy, která se má deserializovat.  
  
- Soubor neexistuje (<xref:System.IO.IOException>).  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Vždy ověřte vstupy a nikdy neserializovat data z nedůvěryhodného zdroje. Nově vytvořený objekt je spuštěn v místním počítači s oprávněním kódu, který jej deserializovat. Před použitím dat ve své aplikaci ověřte všechny vstupy.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.IO.StreamWriter>
- [Zápis dat objektů do souboru XML (C#)](./how-to-write-object-data-to-an-xml-file.md)
- [SerializaceC#()](./index.md)
- [Průvodce programováním v jazyce C#](../../index.md)
