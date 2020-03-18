---
title: Jak zapisovat data objektů do souboru XML (C#)
ms.date: 07/20/2015
ms.assetid: 7681eb98-703d-4005-a369-26a7bca0f894
ms.openlocfilehash: f7ffb47a22d3cd94cd7cb6f702b64180a8790eb4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79167505"
---
# <a name="how-to-write-object-data-to-an-xml-file-c"></a>Jak zapisovat data objektů do souboru XML (C#)
Tento příklad zapíše objekt z třídy <xref:System.Xml.Serialization.XmlSerializer> do souboru XML pomocí třídy.  
  
## <a name="example"></a>Příklad  
  
```csharp  
public class XMLWrite  
{  
  
   static void Main(string[] args)  
    {  
        WriteXML();  
    }  
  
    public class Book  
    {  
        public String title;
    }  
  
    public static void WriteXML()  
    {  
        Book overview = new Book();  
        overview.title = "Serialization Overview";  
        System.Xml.Serialization.XmlSerializer writer =
            new System.Xml.Serialization.XmlSerializer(typeof(Book));  
  
        var path = Environment.GetFolderPath(Environment.SpecialFolder.MyDocuments) + "//SerializationOverview.xml";  
        System.IO.FileStream file = System.IO.File.Create(path);  
  
        writer.Serialize(file, overview);  
        file.Close();  
    }  
}  
```  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Serializovaná třída musí mít veřejný konstruktor bez parametrů.  
  
## <a name="robust-programming"></a>Robustní programování  
 Následující podmínky mohou způsobit výjimku:  
  
- Třída serializované nemá veřejné, parametrless konstruktoru.  
  
- Soubor existuje a je jen<xref:System.IO.IOException>pro čtení ( ).  
  
- Cesta je příliš<xref:System.IO.PathTooLongException>dlouhá ( ).  
  
- Disk je plný<xref:System.IO.IOException>( ).  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Tento příklad vytvoří nový soubor, pokud soubor ještě neexistuje. Pokud aplikace potřebuje vytvořit soubor, tato `Create` aplikace potřebuje přístup pro složku. Pokud soubor již existuje, aplikace `Write` potřebuje pouze přístup, menší oprávnění. Pokud je to možné, je bezpečnější vytvořit soubor `Read` během nasazení a udělit `Create` přístup pouze k jednomu souboru, nikoli přístup u složky.  
  
## <a name="see-also"></a>Viz také

- <xref:System.IO.StreamWriter>
- [Čtení dat objektu ze souboru XML (C#)](./how-to-read-object-data-from-an-xml-file.md)
- [Serializace (C#)](./index.md)
