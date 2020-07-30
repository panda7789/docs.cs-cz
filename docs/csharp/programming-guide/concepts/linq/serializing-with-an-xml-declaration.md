---
title: Serializace s deklarací XML (C#)
description: Přečtěte si o konfiguracích, ve kterých serializace v jazyce C# generuje deklaraci XML, včetně serializace do souboru, TextWriter a XmlWriter.
ms.date: 07/20/2015
ms.assetid: c237fa4a-a042-40fd-886f-17b54c66bb75
ms.openlocfilehash: 7e91b61f037d28149f7c2355f4233dc319b54627
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302357"
---
# <a name="serializing-with-an-xml-declaration-c"></a><span data-ttu-id="4f904-103">Serializace s deklarací XML (C#)</span><span class="sxs-lookup"><span data-stu-id="4f904-103">Serializing with an XML Declaration (C#)</span></span>
<span data-ttu-id="4f904-104">Toto téma popisuje, jak určit, zda serializace generuje deklaraci XML.</span><span class="sxs-lookup"><span data-stu-id="4f904-104">This topic describes how to control whether serialization generates an XML declaration.</span></span>  
  
## <a name="xml-declaration-generation"></a><span data-ttu-id="4f904-105">Generování deklarace XML</span><span class="sxs-lookup"><span data-stu-id="4f904-105">XML Declaration Generation</span></span>  
 <span data-ttu-id="4f904-106">Serializace do <xref:System.IO.File> nebo <xref:System.IO.TextWriter> pomocí <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType> metody nebo <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType> metody generuje deklaraci XML.</span><span class="sxs-lookup"><span data-stu-id="4f904-106">Serializing to a <xref:System.IO.File> or a <xref:System.IO.TextWriter> using the <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType> method or the <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType> method generates an XML declaration.</span></span> <span data-ttu-id="4f904-107">Při serializaci do <xref:System.Xml.XmlWriter> , nastavení zapisovače (určené v <xref:System.Xml.XmlWriterSettings> objektu) určuje, zda je generována deklarace XML.</span><span class="sxs-lookup"><span data-stu-id="4f904-107">When you serialize to an <xref:System.Xml.XmlWriter>, the writer settings (specified in an <xref:System.Xml.XmlWriterSettings> object) determine whether an XML declaration is generated or not.</span></span>  
  
 <span data-ttu-id="4f904-108">Pokud provádíte serializaci do řetězce pomocí `ToString` metody, výsledný kód XML nebude obsahovat deklaraci XML.</span><span class="sxs-lookup"><span data-stu-id="4f904-108">If you are serializing to a string using the `ToString` method, the resulting XML will not include an XML declaration.</span></span>  
  
### <a name="serializing-with-an-xml-declaration"></a><span data-ttu-id="4f904-109">Serializace pomocí deklarace XML</span><span class="sxs-lookup"><span data-stu-id="4f904-109">Serializing with an XML Declaration</span></span>  
 <span data-ttu-id="4f904-110">Následující příklad vytvoří <xref:System.Xml.Linq.XElement> , uloží dokument do souboru a pak vytiskne soubor do konzoly:</span><span class="sxs-lookup"><span data-stu-id="4f904-110">The following example creates an <xref:System.Xml.Linq.XElement>, saves the document to a file, and then prints the file to the console:</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("Child", "child content")  
);  
root.Save("Root.xml");  
string str = File.ReadAllText("Root.xml");  
Console.WriteLine(str);  
```  
  
 <span data-ttu-id="4f904-111">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="4f904-111">This example produces the following output:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<Root>  
  <Child>child content</Child>  
</Root>  
```  
  
### <a name="serializing-without-an-xml-declaration"></a><span data-ttu-id="4f904-112">Serializace bez deklarace XML</span><span class="sxs-lookup"><span data-stu-id="4f904-112">Serializing without an XML Declaration</span></span>  
 <span data-ttu-id="4f904-113">Následující příklad ukazuje, jak uložit <xref:System.Xml.Linq.XElement> do <xref:System.Xml.XmlWriter> .</span><span class="sxs-lookup"><span data-stu-id="4f904-113">The following example shows how to save an <xref:System.Xml.Linq.XElement> to an <xref:System.Xml.XmlWriter>.</span></span>  
  
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
  
 <span data-ttu-id="4f904-114">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="4f904-114">This example produces the following output:</span></span>  
  
```xml  
<Root><Child>child content</Child></Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4f904-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4f904-115">See also</span></span>

- [<span data-ttu-id="4f904-116">Serializace stromů XML (C#)</span><span class="sxs-lookup"><span data-stu-id="4f904-116">Serializing XML Trees (C#)</span></span>](serializing-to-files-textwriters-and-xmlwriters.md)
