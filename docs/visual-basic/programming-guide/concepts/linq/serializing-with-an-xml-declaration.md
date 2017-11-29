---
title: Serializace s deklarace XML (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8726f79e-2bb0-4ba0-969d-197cca591647
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e8544157104b202a36f2ef75b069bcdd297b9158
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="serializing-with-an-xml-declaration-visual-basic"></a><span data-ttu-id="c0fc6-102">Serializace s deklarace XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c0fc6-102">Serializing with an XML Declaration (Visual Basic)</span></span>
<span data-ttu-id="c0fc6-103">Toto téma popisuje, jak řídit, jestli serializace generuje deklarace XML.</span><span class="sxs-lookup"><span data-stu-id="c0fc6-103">This topic describes how to control whether serialization generates an XML declaration.</span></span>  
  
## <a name="xml-declaration-generation"></a><span data-ttu-id="c0fc6-104">Generování deklarace XML</span><span class="sxs-lookup"><span data-stu-id="c0fc6-104">XML Declaration Generation</span></span>  
 <span data-ttu-id="c0fc6-105">K serializaci <xref:System.IO.File> nebo <xref:System.IO.TextWriter> pomocí <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType> metoda nebo <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType> metoda generuje deklarace XML.</span><span class="sxs-lookup"><span data-stu-id="c0fc6-105">Serializing to a <xref:System.IO.File> or a <xref:System.IO.TextWriter> using the <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType> method or the <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType> method generates an XML declaration.</span></span> <span data-ttu-id="c0fc6-106">Při serializaci do <xref:System.Xml.XmlWriter>, nastavení zapisovače (zadaný v <xref:System.Xml.XmlWriterSettings> objektu) určete, zda se vygeneruje deklarace XML, nebo ne.</span><span class="sxs-lookup"><span data-stu-id="c0fc6-106">When you serialize to an <xref:System.Xml.XmlWriter>, the writer settings (specified in an <xref:System.Xml.XmlWriterSettings> object) determine whether an XML declaration is generated or not.</span></span>  
  
 <span data-ttu-id="c0fc6-107">Pokud je serializována na řetězec pomocí `ToString` metoda, výsledná XML nebude obsahovat deklarace XML.</span><span class="sxs-lookup"><span data-stu-id="c0fc6-107">If you are serializing to a string using the `ToString` method, the resulting XML will not include an XML declaration.</span></span>  
  
### <a name="serializing-with-an-xml-declaration"></a><span data-ttu-id="c0fc6-108">Serializace s deklarace XML</span><span class="sxs-lookup"><span data-stu-id="c0fc6-108">Serializing with an XML Declaration</span></span>  
 <span data-ttu-id="c0fc6-109">Následující příklad vytvoří <xref:System.Xml.Linq.XElement>dokument uloží do souboru a potom zobrazí soubor do konzoly:</span><span class="sxs-lookup"><span data-stu-id="c0fc6-109">The following example creates an <xref:System.Xml.Linq.XElement>, saves the document to a file, and then prints the file to the console:</span></span>  
  
```vb  
Dim root As XElement = <Root>  
                           <Child>child content</Child>  
                       </Root>  
root.Save("Root.xml")  
Dim str As String = File.ReadAllText("Root.xml")  
Console.WriteLine(str)  
```  
  
 <span data-ttu-id="c0fc6-110">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="c0fc6-110">This example produces the following output:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<Root>  
  <Child>child content</Child>  
</Root>  
```  
  
### <a name="serializing-without-an-xml-declaration"></a><span data-ttu-id="c0fc6-111">Serializace bez deklarace XML</span><span class="sxs-lookup"><span data-stu-id="c0fc6-111">Serializing without an XML Declaration</span></span>  
 <span data-ttu-id="c0fc6-112">Následující příklad ukazuje, jak uložit <xref:System.Xml.Linq.XElement> k <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="c0fc6-112">The following example shows how to save an <xref:System.Xml.Linq.XElement> to an <xref:System.Xml.XmlWriter>.</span></span>  
  
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
  
 <span data-ttu-id="c0fc6-113">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="c0fc6-113">This example produces the following output:</span></span>  
  
```xml  
<Root><Child>child content</Child></Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c0fc6-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="c0fc6-114">See Also</span></span>  
 [<span data-ttu-id="c0fc6-115">Serializace XML stromů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c0fc6-115">Serializing XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md)
