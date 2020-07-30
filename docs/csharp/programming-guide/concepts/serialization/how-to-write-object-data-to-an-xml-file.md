---
title: Zápis dat objektů do souboru XML (C#)
description: Tento příklad jazyka C# zapíše objekt z třídy do souboru XML pomocí třídy XmlSerializer. Přečtěte si, jak zkompilovat kód.
ms.date: 07/20/2015
ms.assetid: 7681eb98-703d-4005-a369-26a7bca0f894
ms.openlocfilehash: c88a85f8bc65a195f404dab6aa39675bac7e4f84
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303124"
---
# <a name="how-to-write-object-data-to-an-xml-file-c"></a>Zápis dat objektů do souboru XML (C#)
Tento příklad zapíše objekt z třídy do souboru XML pomocí <xref:System.Xml.Serialization.XmlSerializer> třídy.  
  
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
  
- Serializovaná třída nemá veřejný konstruktor bez parametrů.  
  
- Soubor existuje a je určen jen pro čtení ( <xref:System.IO.IOException> ).  
  
- Cesta je příliš dlouhá ( <xref:System.IO.PathTooLongException> ).  
  
- Disk je plný ( <xref:System.IO.IOException> ).  
  
## <a name="net-security"></a>Zabezpečení .NET  
 Tento příklad vytvoří nový soubor, pokud soubor ještě neexistuje. Pokud aplikace potřebuje vytvořit soubor, tato aplikace potřebuje `Create` ke složce přístup. Pokud soubor již existuje, aplikace potřebuje `Write` přístup pouze k menšímu oprávnění. Je-li to možné, je bezpečnější vytvořit soubor během nasazení a udělit `Read` přístup pouze k jedinému souboru, nikoli ke `Create` složce.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.IO.StreamWriter>
- [Čtení dat objektů ze souboru XML (C#)](./how-to-read-object-data-from-an-xml-file.md)
- [Serializace (C#)](./index.md)
