---
title: 'Postupy: Čtení a zápis kódovaného dokumentu'
ms.date: 07/20/2015
ms.assetid: 159d868f-5ac8-40f2-95ca-07dd925f35c6
ms.openlocfilehash: f66737429950e04f447dfbd58cf47b6434a22976
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397905"
---
# <a name="how-to-read-and-write-an-encoded-document-visual-basic"></a><span data-ttu-id="7c9b8-102">Postupy: čtení a zápis kódovaného dokumentu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7c9b8-102">How to: Read and Write an Encoded Document (Visual Basic)</span></span>

<span data-ttu-id="7c9b8-103">Chcete-li vytvořit kódovaný dokument XML, přidejte <xref:System.Xml.Linq.XDeclaration> do stromu XML a nastavte kódování na požadovaný název kódové stránky.</span><span class="sxs-lookup"><span data-stu-id="7c9b8-103">To create an encoded XML document, you add an <xref:System.Xml.Linq.XDeclaration> to the XML tree, setting the encoding to the desired code page name.</span></span>

<span data-ttu-id="7c9b8-104">Libovolná hodnota vrácená hodnotou <xref:System.Text.Encoding.WebName%2A> je platná hodnota.</span><span class="sxs-lookup"><span data-stu-id="7c9b8-104">Any value returned by <xref:System.Text.Encoding.WebName%2A> is a valid value.</span></span>

<span data-ttu-id="7c9b8-105">Při čtení kódovaného dokumentu <xref:System.Xml.Linq.XDeclaration.Encoding%2A> bude vlastnost nastavena na název kódové stránky.</span><span class="sxs-lookup"><span data-stu-id="7c9b8-105">If you read an encoded document, the <xref:System.Xml.Linq.XDeclaration.Encoding%2A> property will be set to the code page name.</span></span>

<span data-ttu-id="7c9b8-106">Nastavíte <xref:System.Xml.Linq.XDeclaration.Encoding%2A> -li na platný název kódové stránky, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] bude serializace se zadaným kódováním.</span><span class="sxs-lookup"><span data-stu-id="7c9b8-106">If you set <xref:System.Xml.Linq.XDeclaration.Encoding%2A> to a valid code page name, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] will serialize with the specified encoding.</span></span>

## <a name="example"></a><span data-ttu-id="7c9b8-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="7c9b8-107">Example</span></span>

<span data-ttu-id="7c9b8-108">Následující příklad vytvoří dva dokumenty, jednu s kódováním UTF-8 a jednu s kódováním UTF-16.</span><span class="sxs-lookup"><span data-stu-id="7c9b8-108">The following example creates two documents, one with utf-8 encoding, and one with utf-16 encoding.</span></span> <span data-ttu-id="7c9b8-109">Poté načte dokumenty a vytiskne kódování do konzoly.</span><span class="sxs-lookup"><span data-stu-id="7c9b8-109">It then loads the documents and prints the encoding to the console.</span></span>

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

<span data-ttu-id="7c9b8-110">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="7c9b8-110">This example produces the following output:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="7c9b8-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="7c9b8-111">See also</span></span>

- <xref:System.Xml.Linq.XDeclaration.Encoding%2A?displayProperty=nameWithType>
- [<span data-ttu-id="7c9b8-112">Rozšířené programování LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7c9b8-112">Advanced LINQ to XML Programming (Visual Basic)</span></span>](advanced-linq-to-xml-programming.md)
