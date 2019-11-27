---
title: 'Postupy: čtení a zápis kódovaného dokumentu'
ms.date: 07/20/2015
ms.assetid: 159d868f-5ac8-40f2-95ca-07dd925f35c6
ms.openlocfilehash: 913b08d91b8d4886bc74cbe538df8e27826a6cca
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347621"
---
# <a name="how-to-read-and-write-an-encoded-document-visual-basic"></a>Postupy: čtení a zápis kódovaného dokumentu (Visual Basic)

Chcete-li vytvořit kódovaný dokument XML, přidejte <xref:System.Xml.Linq.XDeclaration> do stromu XML a nastavte kódování na požadovaný název kódové stránky.

Jakákoli hodnota vrácená <xref:System.Text.Encoding.WebName%2A> je platná hodnota.

Při čtení kódovaného dokumentu bude vlastnost <xref:System.Xml.Linq.XDeclaration.Encoding%2A> nastavena na název kódové stránky.

Nastavíte-li <xref:System.Xml.Linq.XDeclaration.Encoding%2A> na platný název kódové stránky, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] bude serializován se zadaným kódováním.

## <a name="example"></a>Příklad

Následující příklad vytvoří dva dokumenty, jednu s kódováním UTF-8 a jednu s kódováním UTF-16. Poté načte dokumenty a vytiskne kódování do konzoly.

```vb
Console.WriteLine("Creating a document with utf-8 encoding")
Dim encodedDoc8 As XDocument = _
        <?xml version='1.0' encoding='utf-8' standalone='yes'?>
        <Root>Content</Root>

encodedDoc8.Save("EncodedUtf8.xml")
Console.WriteLine("Encoding is:{0}", encodedDoc8.Declaration.Encoding)
Console.WriteLine()

Console.WriteLine("Creating a document with utf-16 encoding")
Dim encodedDoc16 As XDocument = _
        <?xml version='1.0' encoding='utf-16' standalone='yes'?>
        <Root>Content</Root>

encodedDoc16.Save("EncodedUtf16.xml")
Console.WriteLine("Encoding is:{0}", encodedDoc16.Declaration.Encoding)
Console.WriteLine()

Dim newDoc8 As XDocument = XDocument.Load("EncodedUtf8.xml")
Console.WriteLine("Encoded document:")
Console.WriteLine(File.ReadAllText("EncodedUtf8.xml"))
Console.WriteLine()
Console.WriteLine("Encoding of loaded document is:{0}", newDoc8.Declaration.Encoding)
Console.WriteLine()

Dim newDoc16 As XDocument = XDocument.Load("EncodedUtf16.xml")
Console.WriteLine("Encoded document:")
Console.WriteLine(File.ReadAllText("EncodedUtf16.xml"))
Console.WriteLine()
Console.WriteLine("Encoding of loaded document is:{0}", newDoc16.Declaration.Encoding)
```

Tento příklad vytvoří následující výstup:

```console
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
- [Rozšířené programování LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
