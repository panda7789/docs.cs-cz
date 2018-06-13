---
title: Serializace s deklarace XML (C#)
ms.date: 07/20/2015
ms.assetid: c237fa4a-a042-40fd-886f-17b54c66bb75
ms.openlocfilehash: 3f331f1226e7e5a905471f4a793f9a415bdd858a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33329784"
---
# <a name="serializing-with-an-xml-declaration-c"></a><span data-ttu-id="82a88-102">Serializace s deklarace XML (C#)</span><span class="sxs-lookup"><span data-stu-id="82a88-102">Serializing with an XML Declaration (C#)</span></span>
<span data-ttu-id="82a88-103">Toto téma popisuje, jak řídit, jestli serializace generuje deklarace XML.</span><span class="sxs-lookup"><span data-stu-id="82a88-103">This topic describes how to control whether serialization generates an XML declaration.</span></span>  
  
## <a name="xml-declaration-generation"></a><span data-ttu-id="82a88-104">Generování deklarace XML</span><span class="sxs-lookup"><span data-stu-id="82a88-104">XML Declaration Generation</span></span>  
 <span data-ttu-id="82a88-105">K serializaci <xref:System.IO.File> nebo <xref:System.IO.TextWriter> pomocí <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType> metoda nebo <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType> metoda generuje deklarace XML.</span><span class="sxs-lookup"><span data-stu-id="82a88-105">Serializing to a <xref:System.IO.File> or a <xref:System.IO.TextWriter> using the <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType> method or the <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType> method generates an XML declaration.</span></span> <span data-ttu-id="82a88-106">Při serializaci do <xref:System.Xml.XmlWriter>, nastavení zapisovače (zadaný v <xref:System.Xml.XmlWriterSettings> objektu) určete, zda se vygeneruje deklarace XML, nebo ne.</span><span class="sxs-lookup"><span data-stu-id="82a88-106">When you serialize to an <xref:System.Xml.XmlWriter>, the writer settings (specified in an <xref:System.Xml.XmlWriterSettings> object) determine whether an XML declaration is generated or not.</span></span>  
  
 <span data-ttu-id="82a88-107">Pokud je serializována na řetězec pomocí `ToString` metoda, výsledná XML nebude obsahovat deklarace XML.</span><span class="sxs-lookup"><span data-stu-id="82a88-107">If you are serializing to a string using the `ToString` method, the resulting XML will not include an XML declaration.</span></span>  
  
### <a name="serializing-with-an-xml-declaration"></a><span data-ttu-id="82a88-108">Serializace s deklarace XML</span><span class="sxs-lookup"><span data-stu-id="82a88-108">Serializing with an XML Declaration</span></span>  
 <span data-ttu-id="82a88-109">Následující příklad vytvoří <xref:System.Xml.Linq.XElement>dokument uloží do souboru a potom zobrazí soubor do konzoly:</span><span class="sxs-lookup"><span data-stu-id="82a88-109">The following example creates an <xref:System.Xml.Linq.XElement>, saves the document to a file, and then prints the file to the console:</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("Child", "child content")  
);  
root.Save("Root.xml");  
string str = File.ReadAllText("Root.xml");  
Console.WriteLine(str);  
```  
  
 <span data-ttu-id="82a88-110">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="82a88-110">This example produces the following output:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<Root>  
  <Child>child content</Child>  
</Root>  
```  
  
### <a name="serializing-without-an-xml-declaration"></a><span data-ttu-id="82a88-111">Serializace bez deklarace XML</span><span class="sxs-lookup"><span data-stu-id="82a88-111">Serializing without an XML Declaration</span></span>  
 <span data-ttu-id="82a88-112">Následující příklad ukazuje, jak uložit <xref:System.Xml.Linq.XElement> k <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="82a88-112">The following example shows how to save an <xref:System.Xml.Linq.XElement> to an <xref:System.Xml.XmlWriter>.</span></span>  
  
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
  
 <span data-ttu-id="82a88-113">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="82a88-113">This example produces the following output:</span></span>  
  
```xml  
<Root><Child>child content</Child></Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="82a88-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="82a88-114">See Also</span></span>  
 [<span data-ttu-id="82a88-115">Serializace XML stromů (C#)</span><span class="sxs-lookup"><span data-stu-id="82a88-115">Serializing XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/serializing-xml-trees.md)
