---
title: 'Postupy: čtení a zápis kódovaného dokumentu (C#)'
ms.date: 07/20/2015
ms.assetid: 84f64e71-39a6-42c6-ad68-f052bb158a03
ms.openlocfilehash: 9fc6a7beaa4a7b9de21961e1095dd41fe2e407dd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-read-and-write-an-encoded-document-c"></a>Postupy: čtení a zápis kódovaného dokumentu (C#)
Chcete-li vytvořit dokument XML kódovaného, je přidat <xref:System.Xml.Linq.XDeclaration> do stromu XML nastavení kódování, které má název požadované kódu stránky.  
  
 Všechny hodnoty vrácené <xref:System.Text.Encoding.WebName%2A> platná hodnota.  
  
 Pokud si přečíst dokument kódovaného <xref:System.Xml.Linq.XDeclaration.Encoding%2A> vlastnost bude nastavena na název stránky kód.  
  
 Pokud nastavíte <xref:System.Xml.Linq.XDeclaration.Encoding%2A> k názvu stránky platný kód [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] bude serializovat s zadanému kódování.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří dva dokumenty, jeden s kódováním utf-8 a jednu s kódování utf-16. Potom načte dokumenty a vytiskne kódování ke konzole.  
  
```csharp  
Console.WriteLine("Creating a document with utf-8 encoding");  
XDocument encodedDoc8 = new XDocument(  
    new XDeclaration("1.0", "utf-8", "yes"),  
    new XElement("Root", "Content")  
);  
encodedDoc8.Save("EncodedUtf8.xml");  
Console.WriteLine("Encoding is:{0}", encodedDoc8.Declaration.Encoding);  
Console.WriteLine();  
  
Console.WriteLine("Creating a document with utf-16 encoding");  
XDocument encodedDoc16 = new XDocument(  
    new XDeclaration("1.0", "utf-16", "yes"),  
    new XElement("Root", "Content")  
);  
encodedDoc16.Save("EncodedUtf16.xml");  
Console.WriteLine("Encoding is:{0}", encodedDoc16.Declaration.Encoding);  
Console.WriteLine();  
  
XDocument newDoc8 = XDocument.Load("EncodedUtf8.xml");  
Console.WriteLine("Encoded document:");  
Console.WriteLine(File.ReadAllText("EncodedUtf8.xml"));  
Console.WriteLine();  
Console.WriteLine("Encoding of loaded document is:{0}", newDoc8.Declaration.Encoding);  
Console.WriteLine();  
  
XDocument newDoc16 = XDocument.Load("EncodedUtf16.xml");  
Console.WriteLine("Encoded document:");  
Console.WriteLine(File.ReadAllText("EncodedUtf16.xml"));  
Console.WriteLine();  
Console.WriteLine("Encoding of loaded document is:{0}", newDoc16.Declaration.Encoding);  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```  
Creating a document with utf-8 encoding  
Encoding is:utf-8  
  
Creating a document with utf-16 encoding  
Encoding is:utf-16  
  
Encoded document:  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<Root>Content</Root>  
  
Encoding of loaded document is:utf-8  
  
Encoded document:  
<?xml version="1.0" encoding="utf-16" standalone="yes"?>  
<Root>Content</Root>  
  
Encoding of loaded document is:utf-16  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Xml.Linq.XDeclaration.Encoding%2A?displayProperty=nameWithType>  
 [Pokročilé technologie LINQ to XML programování (C#)](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
