---
title: Jak číst a psát kódovaný dokument (C#)
ms.date: 07/20/2015
ms.assetid: 84f64e71-39a6-42c6-ad68-f052bb158a03
ms.openlocfilehash: fa28c26845a0c6019943e0532ea0692a6dffd5a9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75347666"
---
# <a name="how-to-read-and-write-an-encoded-document-c"></a>Jak číst a psát kódovaný dokument (C#)
Chcete-li vytvořit kódovaný dokument XML, přidejte jej <xref:System.Xml.Linq.XDeclaration> do stromu XML a nastavíte kódování na požadovaný název znakové stránky.  
  
 Každá hodnota <xref:System.Text.Encoding.WebName%2A> vrácená je platná hodnota.  
  
 Pokud čtete kódovaný dokument, <xref:System.Xml.Linq.XDeclaration.Encoding%2A> vlastnost bude nastavena na název znakové stránky.  
  
 Pokud nastavíte <xref:System.Xml.Linq.XDeclaration.Encoding%2A> platný název [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] znakové stránky, serializuje se zadaným kódováním.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří dva dokumenty, jeden s kódováním UTF-8 a jeden s kódováním UTF-16. Potom načte dokumenty a vytiskne kódování do konzoly.  
  
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
  
 Tento příklad vytváří následující výstup:  
  
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
  
## <a name="see-also"></a>Viz také

- <xref:System.Xml.Linq.XDeclaration.Encoding%2A?displayProperty=nameWithType>
