---
title: Čtení a zápis kódovaného dokumentu (C#)
ms.date: 07/20/2015
ms.assetid: 84f64e71-39a6-42c6-ad68-f052bb158a03
ms.openlocfilehash: fa28c26845a0c6019943e0532ea0692a6dffd5a9
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347666"
---
# <a name="how-to-read-and-write-an-encoded-document-c"></a>Čtení a zápis kódovaného dokumentu (C#)
Chcete-li vytvořit kódovaný dokument XML, přidejte <xref:System.Xml.Linq.XDeclaration> do stromu XML a nastavte kódování na požadovaný název kódové stránky.  
  
 Jakákoli hodnota vrácená <xref:System.Text.Encoding.WebName%2A> je platná hodnota.  
  
 Při čtení kódovaného dokumentu bude vlastnost <xref:System.Xml.Linq.XDeclaration.Encoding%2A> nastavena na název kódové stránky.  
  
 Nastavíte-li <xref:System.Xml.Linq.XDeclaration.Encoding%2A> na platný název kódové stránky, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] bude serializován se zadaným kódováním.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří dva dokumenty, jednu s kódováním UTF-8 a jednu s kódováním UTF-16. Poté načte dokumenty a vytiskne kódování do konzoly.  
  
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
  
```output  
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.Xml.Linq.XDeclaration.Encoding%2A?displayProperty=nameWithType>
