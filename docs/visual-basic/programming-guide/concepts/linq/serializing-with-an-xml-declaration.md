---
title: Serializace pomocí deklarace XML (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 8726f79e-2bb0-4ba0-969d-197cca591647
ms.openlocfilehash: f51dacb0f89e1042ba9875bec10a0cb1fe25f889
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61786435"
---
# <a name="serializing-with-an-xml-declaration-visual-basic"></a><span data-ttu-id="f2d41-102">Serializace pomocí deklarace XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f2d41-102">Serializing with an XML Declaration (Visual Basic)</span></span>
<span data-ttu-id="f2d41-103">Toto téma popisuje, jak řídit, jestli serializace generuje deklaraci XML.</span><span class="sxs-lookup"><span data-stu-id="f2d41-103">This topic describes how to control whether serialization generates an XML declaration.</span></span>  
  
## <a name="xml-declaration-generation"></a><span data-ttu-id="f2d41-104">Generování deklarace XML</span><span class="sxs-lookup"><span data-stu-id="f2d41-104">XML Declaration Generation</span></span>  
 <span data-ttu-id="f2d41-105">Serializace do <xref:System.IO.File> nebo <xref:System.IO.TextWriter> pomocí <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType> metoda nebo <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType> metoda generuje deklaraci XML.</span><span class="sxs-lookup"><span data-stu-id="f2d41-105">Serializing to a <xref:System.IO.File> or a <xref:System.IO.TextWriter> using the <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType> method or the <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType> method generates an XML declaration.</span></span> <span data-ttu-id="f2d41-106">Při serializaci do <xref:System.Xml.XmlWriter>, nastavení zapisovače (zadané v poli <xref:System.Xml.XmlWriterSettings> objektu) určuje, zda bude generovat deklarace XML, nebo ne.</span><span class="sxs-lookup"><span data-stu-id="f2d41-106">When you serialize to an <xref:System.Xml.XmlWriter>, the writer settings (specified in an <xref:System.Xml.XmlWriterSettings> object) determine whether an XML declaration is generated or not.</span></span>  
  
 <span data-ttu-id="f2d41-107">Pokud serializujete na řetězec pomocí `ToString` metoda výsledného kódu XML nebude obsahovat deklaraci XML.</span><span class="sxs-lookup"><span data-stu-id="f2d41-107">If you are serializing to a string using the `ToString` method, the resulting XML will not include an XML declaration.</span></span>  
  
### <a name="serializing-with-an-xml-declaration"></a><span data-ttu-id="f2d41-108">Serializace pomocí deklarace XML</span><span class="sxs-lookup"><span data-stu-id="f2d41-108">Serializing with an XML Declaration</span></span>  
 <span data-ttu-id="f2d41-109">Následující příklad vytvoří <xref:System.Xml.Linq.XElement>, uloží dokument k souboru a potom zobrazí soubor do konzoly:</span><span class="sxs-lookup"><span data-stu-id="f2d41-109">The following example creates an <xref:System.Xml.Linq.XElement>, saves the document to a file, and then prints the file to the console:</span></span>  
  
```vb  
Dim root As XElement = <Root>  
                           <Child>child content</Child>  
                       </Root>  
root.Save("Root.xml")  
Dim str As String = File.ReadAllText("Root.xml")  
Console.WriteLine(str)  
```  
  
 <span data-ttu-id="f2d41-110">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="f2d41-110">This example produces the following output:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<Root>  
  <Child>child content</Child>  
</Root>  
```  
  
### <a name="serializing-without-an-xml-declaration"></a><span data-ttu-id="f2d41-111">Serializace bez deklarace XML</span><span class="sxs-lookup"><span data-stu-id="f2d41-111">Serializing without an XML Declaration</span></span>  
 <span data-ttu-id="f2d41-112">Následující příklad ukazuje, jak uložit <xref:System.Xml.Linq.XElement> do <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="f2d41-112">The following example shows how to save an <xref:System.Xml.Linq.XElement> to an <xref:System.Xml.XmlWriter>.</span></span>  
  
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
  
 <span data-ttu-id="f2d41-113">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="f2d41-113">This example produces the following output:</span></span>  
  
```xml  
<Root><Child>child content</Child></Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f2d41-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f2d41-114">See also</span></span>

- [<span data-ttu-id="f2d41-115">Serializace stromů XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f2d41-115">Serializing XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md)
