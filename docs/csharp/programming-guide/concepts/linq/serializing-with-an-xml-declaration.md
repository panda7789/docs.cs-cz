---
title: Serializace pomocí deklarace XML (C#)
ms.date: 07/20/2015
ms.assetid: c237fa4a-a042-40fd-886f-17b54c66bb75
ms.openlocfilehash: 4f5dd9a7e392acff30814db4a483b297494b68b1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54702402"
---
# <a name="serializing-with-an-xml-declaration-c"></a><span data-ttu-id="a21b5-102">Serializace pomocí deklarace XML (C#)</span><span class="sxs-lookup"><span data-stu-id="a21b5-102">Serializing with an XML Declaration (C#)</span></span>
<span data-ttu-id="a21b5-103">Toto téma popisuje, jak řídit, jestli serializace generuje deklaraci XML.</span><span class="sxs-lookup"><span data-stu-id="a21b5-103">This topic describes how to control whether serialization generates an XML declaration.</span></span>  
  
## <a name="xml-declaration-generation"></a><span data-ttu-id="a21b5-104">Generování deklarace XML</span><span class="sxs-lookup"><span data-stu-id="a21b5-104">XML Declaration Generation</span></span>  
 <span data-ttu-id="a21b5-105">Serializace do <xref:System.IO.File> nebo <xref:System.IO.TextWriter> pomocí <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType> metoda nebo <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType> metoda generuje deklaraci XML.</span><span class="sxs-lookup"><span data-stu-id="a21b5-105">Serializing to a <xref:System.IO.File> or a <xref:System.IO.TextWriter> using the <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType> method or the <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType> method generates an XML declaration.</span></span> <span data-ttu-id="a21b5-106">Při serializaci do <xref:System.Xml.XmlWriter>, nastavení zapisovače (zadané v poli <xref:System.Xml.XmlWriterSettings> objektu) určuje, zda bude generovat deklarace XML, nebo ne.</span><span class="sxs-lookup"><span data-stu-id="a21b5-106">When you serialize to an <xref:System.Xml.XmlWriter>, the writer settings (specified in an <xref:System.Xml.XmlWriterSettings> object) determine whether an XML declaration is generated or not.</span></span>  
  
 <span data-ttu-id="a21b5-107">Pokud serializujete na řetězec pomocí `ToString` metoda výsledného kódu XML nebude obsahovat deklaraci XML.</span><span class="sxs-lookup"><span data-stu-id="a21b5-107">If you are serializing to a string using the `ToString` method, the resulting XML will not include an XML declaration.</span></span>  
  
### <a name="serializing-with-an-xml-declaration"></a><span data-ttu-id="a21b5-108">Serializace pomocí deklarace XML</span><span class="sxs-lookup"><span data-stu-id="a21b5-108">Serializing with an XML Declaration</span></span>  
 <span data-ttu-id="a21b5-109">Následující příklad vytvoří <xref:System.Xml.Linq.XElement>, uloží dokument k souboru a potom zobrazí soubor do konzoly:</span><span class="sxs-lookup"><span data-stu-id="a21b5-109">The following example creates an <xref:System.Xml.Linq.XElement>, saves the document to a file, and then prints the file to the console:</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("Child", "child content")  
);  
root.Save("Root.xml");  
string str = File.ReadAllText("Root.xml");  
Console.WriteLine(str);  
```  
  
 <span data-ttu-id="a21b5-110">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="a21b5-110">This example produces the following output:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<Root>  
  <Child>child content</Child>  
</Root>  
```  
  
### <a name="serializing-without-an-xml-declaration"></a><span data-ttu-id="a21b5-111">Serializace bez deklarace XML</span><span class="sxs-lookup"><span data-stu-id="a21b5-111">Serializing without an XML Declaration</span></span>  
 <span data-ttu-id="a21b5-112">Následující příklad ukazuje, jak uložit <xref:System.Xml.Linq.XElement> do <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="a21b5-112">The following example shows how to save an <xref:System.Xml.Linq.XElement> to an <xref:System.Xml.XmlWriter>.</span></span>  
  
```csharp  
StringBuilder sb = new StringBuilder();  
XmlWriterSettings xws = new XmlWriterSettings();  
xws.OmitXmlDeclaration = true;  
  
using (XmlWriter xw = XmlWriter.Create(sb, xws)) {  
    XElement root = new XElement("Root",  
        new XElement("Child", "child content")  
    );  
    root.Save(xw);  
}  
Console.WriteLine(sb.ToString());  
```  
  
 <span data-ttu-id="a21b5-113">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="a21b5-113">This example produces the following output:</span></span>  
  
```xml  
<Root><Child>child content</Child></Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a21b5-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a21b5-114">See also</span></span>

- [<span data-ttu-id="a21b5-115">Serializace stromů XML (C#)</span><span class="sxs-lookup"><span data-stu-id="a21b5-115">Serializing XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/serializing-xml-trees.md)
