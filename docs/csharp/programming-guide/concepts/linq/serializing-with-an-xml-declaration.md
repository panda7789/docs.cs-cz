---
title: Serializace s deklarací XML (C#)
ms.date: 07/20/2015
ms.assetid: c237fa4a-a042-40fd-886f-17b54c66bb75
ms.openlocfilehash: 4533d69f2b0bee68b4adee6e18fe28dde18078ae
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "66483480"
---
# <a name="serializing-with-an-xml-declaration-c"></a><span data-ttu-id="d8bb2-102">Serializace s deklarací XML (C#)</span><span class="sxs-lookup"><span data-stu-id="d8bb2-102">Serializing with an XML Declaration (C#)</span></span>
<span data-ttu-id="d8bb2-103">Toto téma popisuje, jak řídit, zda serializace generuje deklaraci XML.</span><span class="sxs-lookup"><span data-stu-id="d8bb2-103">This topic describes how to control whether serialization generates an XML declaration.</span></span>  
  
## <a name="xml-declaration-generation"></a><span data-ttu-id="d8bb2-104">Generování deklarace XML</span><span class="sxs-lookup"><span data-stu-id="d8bb2-104">XML Declaration Generation</span></span>  
 <span data-ttu-id="d8bb2-105">Serializace na <xref:System.IO.File> nebo <xref:System.IO.TextWriter> pomocí <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType> metody <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType> nebo metody generuje deklaraci XML.</span><span class="sxs-lookup"><span data-stu-id="d8bb2-105">Serializing to a <xref:System.IO.File> or a <xref:System.IO.TextWriter> using the <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType> method or the <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType> method generates an XML declaration.</span></span> <span data-ttu-id="d8bb2-106">Při serializaci do <xref:System.Xml.XmlWriter>aplikace určují nastavení pro <xref:System.Xml.XmlWriterSettings> zápis (zadané v objektu), zda je deklarace XML generována či nikoli.</span><span class="sxs-lookup"><span data-stu-id="d8bb2-106">When you serialize to an <xref:System.Xml.XmlWriter>, the writer settings (specified in an <xref:System.Xml.XmlWriterSettings> object) determine whether an XML declaration is generated or not.</span></span>  
  
 <span data-ttu-id="d8bb2-107">Pokud serializujete řetězec pomocí `ToString` metody, výsledný kód XML nebude obsahovat deklaraci XML.</span><span class="sxs-lookup"><span data-stu-id="d8bb2-107">If you are serializing to a string using the `ToString` method, the resulting XML will not include an XML declaration.</span></span>  
  
### <a name="serializing-with-an-xml-declaration"></a><span data-ttu-id="d8bb2-108">Serializace pomocí deklarace XML</span><span class="sxs-lookup"><span data-stu-id="d8bb2-108">Serializing with an XML Declaration</span></span>  
 <span data-ttu-id="d8bb2-109">Následující příklad vytvoří <xref:System.Xml.Linq.XElement>soubor , uloží dokument do souboru a pak jej vytiskne do konzoly:</span><span class="sxs-lookup"><span data-stu-id="d8bb2-109">The following example creates an <xref:System.Xml.Linq.XElement>, saves the document to a file, and then prints the file to the console:</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("Child", "child content")  
);  
root.Save("Root.xml");  
string str = File.ReadAllText("Root.xml");  
Console.WriteLine(str);  
```  
  
 <span data-ttu-id="d8bb2-110">Tento příklad vytváří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="d8bb2-110">This example produces the following output:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<Root>  
  <Child>child content</Child>  
</Root>  
```  
  
### <a name="serializing-without-an-xml-declaration"></a><span data-ttu-id="d8bb2-111">Serializace bez deklarace XML</span><span class="sxs-lookup"><span data-stu-id="d8bb2-111">Serializing without an XML Declaration</span></span>  
 <span data-ttu-id="d8bb2-112">Následující příklad ukazuje, jak <xref:System.Xml.Linq.XElement> uložit <xref:System.Xml.XmlWriter>do .</span><span class="sxs-lookup"><span data-stu-id="d8bb2-112">The following example shows how to save an <xref:System.Xml.Linq.XElement> to an <xref:System.Xml.XmlWriter>.</span></span>  
  
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
  
 <span data-ttu-id="d8bb2-113">Tento příklad vytváří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="d8bb2-113">This example produces the following output:</span></span>  
  
```xml  
<Root><Child>child content</Child></Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d8bb2-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="d8bb2-114">See also</span></span>

- [<span data-ttu-id="d8bb2-115">Serializace stromů XML (C#)</span><span class="sxs-lookup"><span data-stu-id="d8bb2-115">Serializing XML Trees (C#)</span></span>](serializing-to-files-textwriters-and-xmlwriters.md)
