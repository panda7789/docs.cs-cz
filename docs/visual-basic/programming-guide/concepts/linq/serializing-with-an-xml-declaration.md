---
title: Serializace pomocí deklarace XML
ms.date: 07/20/2015
ms.assetid: 8726f79e-2bb0-4ba0-969d-197cca591647
ms.openlocfilehash: cd303a800efe42d3fa99d601f25d54320570bed3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411792"
---
# <a name="serializing-with-an-xml-declaration-visual-basic"></a><span data-ttu-id="618aa-102">Serializace s deklarací XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="618aa-102">Serializing with an XML Declaration (Visual Basic)</span></span>
<span data-ttu-id="618aa-103">Toto téma popisuje, jak určit, zda serializace generuje deklaraci XML.</span><span class="sxs-lookup"><span data-stu-id="618aa-103">This topic describes how to control whether serialization generates an XML declaration.</span></span>  
  
## <a name="xml-declaration-generation"></a><span data-ttu-id="618aa-104">Generování deklarace XML</span><span class="sxs-lookup"><span data-stu-id="618aa-104">XML Declaration Generation</span></span>  
 <span data-ttu-id="618aa-105">Serializace do <xref:System.IO.File> nebo <xref:System.IO.TextWriter> pomocí <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType> metody nebo <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType> metody generuje deklaraci XML.</span><span class="sxs-lookup"><span data-stu-id="618aa-105">Serializing to a <xref:System.IO.File> or a <xref:System.IO.TextWriter> using the <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType> method or the <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType> method generates an XML declaration.</span></span> <span data-ttu-id="618aa-106">Při serializaci do <xref:System.Xml.XmlWriter> , nastavení zapisovače (určené v <xref:System.Xml.XmlWriterSettings> objektu) určuje, zda je generována deklarace XML.</span><span class="sxs-lookup"><span data-stu-id="618aa-106">When you serialize to an <xref:System.Xml.XmlWriter>, the writer settings (specified in an <xref:System.Xml.XmlWriterSettings> object) determine whether an XML declaration is generated or not.</span></span>  
  
 <span data-ttu-id="618aa-107">Pokud provádíte serializaci do řetězce pomocí `ToString` metody, výsledný kód XML nebude obsahovat deklaraci XML.</span><span class="sxs-lookup"><span data-stu-id="618aa-107">If you are serializing to a string using the `ToString` method, the resulting XML will not include an XML declaration.</span></span>  
  
### <a name="serializing-with-an-xml-declaration"></a><span data-ttu-id="618aa-108">Serializace pomocí deklarace XML</span><span class="sxs-lookup"><span data-stu-id="618aa-108">Serializing with an XML Declaration</span></span>  
 <span data-ttu-id="618aa-109">Následující příklad vytvoří <xref:System.Xml.Linq.XElement> , uloží dokument do souboru a pak vytiskne soubor do konzoly:</span><span class="sxs-lookup"><span data-stu-id="618aa-109">The following example creates an <xref:System.Xml.Linq.XElement>, saves the document to a file, and then prints the file to the console:</span></span>  
  
```vb  
Dim root As XElement = <Root>  
                           <Child>child content</Child>  
                       </Root>  
root.Save("Root.xml")  
Dim str As String = File.ReadAllText("Root.xml")  
Console.WriteLine(str)  
```  
  
 <span data-ttu-id="618aa-110">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="618aa-110">This example produces the following output:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<Root>  
  <Child>child content</Child>  
</Root>  
```  
  
### <a name="serializing-without-an-xml-declaration"></a><span data-ttu-id="618aa-111">Serializace bez deklarace XML</span><span class="sxs-lookup"><span data-stu-id="618aa-111">Serializing without an XML Declaration</span></span>  
 <span data-ttu-id="618aa-112">Následující příklad ukazuje, jak uložit <xref:System.Xml.Linq.XElement> do <xref:System.Xml.XmlWriter> .</span><span class="sxs-lookup"><span data-stu-id="618aa-112">The following example shows how to save an <xref:System.Xml.Linq.XElement> to an <xref:System.Xml.XmlWriter>.</span></span>  
  
```vb  
Dim sb As StringBuilder = New StringBuilder()  
Dim xws As XmlWriterSettings = New XmlWriterSettings()  
xws.OmitXmlDeclaration = True  
  
Using xw As XmlWriter = XmlWriter.Create(sb, xws)  
    Dim root = <Root>  
                   <Child>child content</Child>  
               </Root>  
    root.Save(xw)  
End Using  
Console.WriteLine(sb.ToString())  
```  
  
 <span data-ttu-id="618aa-113">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="618aa-113">This example produces the following output:</span></span>  
  
```xml  
<Root><Child>child content</Child></Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="618aa-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="618aa-114">See also</span></span>

- [<span data-ttu-id="618aa-115">Serializace stromů XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="618aa-115">Serializing XML Trees (Visual Basic)</span></span>](serializing-xml-trees.md)
