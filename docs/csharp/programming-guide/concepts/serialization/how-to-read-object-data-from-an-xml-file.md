---
title: Čtení dat objektu ze souboru XML (C#)
ms.date: 07/20/2015
ms.assetid: 6ad60d96-a4d9-48e6-a8b0-d7f6f803cafa
ms.openlocfilehash: 18428cbe2f2d3b9434a77ee4d063ceabbba6bcb8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79167815"
---
# <a name="how-to-read-object-data-from-an-xml-file-c"></a>Čtení dat objektu ze souboru XML (C#)
Tento příklad čte data objektu, která byla <xref:System.Xml.Serialization.XmlSerializer> dříve zapsána do souboru XML pomocí třídy.  
  
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
Nahraďte název souboru "c:\temp\SerializationOverview.xml" názvem souboru obsahujícího serializovaná data. Další informace o serializaci dat naleznete v tématu [Jak zapsat data objektů do souboru XML (C#).](./how-to-write-object-data-to-an-xml-file.md)
  
 Třída musí mít veřejný konstruktor bez parametrů.  
  
 Dekonstruovány jsou pouze veřejné vlastnosti a pole.  
  
## <a name="robust-programming"></a>Robustní programování  
 Následující podmínky mohou způsobit výjimku:  
  
- Třída serializované nemá veřejné, parametrless konstruktoru.  
  
- Data v souboru nepředstavují data z třídy, která má být rekonstruována.  
  
- Soubor neexistuje (<xref:System.IO.IOException>).  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Vždy ověřujte vstupy a nikdy nerekonstruujte data z nedůvěryhodného zdroje. Znovu vytvořený objekt je spuštěn v místním počítači s oprávněními kódu, který jej rekonstruoval. Před použitím dat ve své aplikaci ověřte všechny vstupy.  
  
## <a name="see-also"></a>Viz také

- <xref:System.IO.StreamWriter>
- [Jak zapisovat data objektů do souboru XML (C#)](./how-to-write-object-data-to-an-xml-file.md)
- [Serializace (C#)](./index.md)
- [Programovací příručka jazyka C#](../../index.md)
