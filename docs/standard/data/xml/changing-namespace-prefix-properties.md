---
title: Změna vlastností předpony Namespace
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: d5c87cbe-4d69-429f-aad5-3103c2ca2770
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4a6597a3a57cd68c4dd17c4fbae882590f373709
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45526717"
---
# <a name="changing-namespace-prefix-properties"></a><span data-ttu-id="000b9-102">Změna vlastností předpony Namespace</span><span class="sxs-lookup"><span data-stu-id="000b9-102">Changing Namespace Prefix Properties</span></span>
<span data-ttu-id="000b9-103">**XmlNode** třída umožňuje změnit předponu oboru názvů, který je přidružený k daném uzlu.</span><span class="sxs-lookup"><span data-stu-id="000b9-103">The **XmlNode** class allows you to change the namespace prefix associated with a given node.</span></span> <span data-ttu-id="000b9-104">Například následující kód ukazuje předponu element mění.</span><span class="sxs-lookup"><span data-stu-id="000b9-104">For example, the following code shows the prefix of an element being changed.</span></span>  
  
```vb  
Dim doc as XmlDocument = new XmlDocument()  
doc.LoadXml("<a:test xmlns:a='123' xmlns:b='456'/>")  
Dim e as XmlElement = doc.DocumentElement  
e.Prefix = "b"  
Console.WriteLine(doc.InnerXml)  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
doc.LoadXml("<a:test xmlns:a='123' xmlns:b='456'/>");  
XmlElement e = doc.DocumentElement;         
e.Prefix = "b";  
Console.WriteLine(doc.InnerXml);  
```  
  
 <span data-ttu-id="000b9-105">**Output**</span><span class="sxs-lookup"><span data-stu-id="000b9-105">**Output**</span></span>  
  
```xml  
<b:test xmlns:a="123" xmlns:b="456" />  
```  
  
 <span data-ttu-id="000b9-106">Změna předponu uzel nezmění svůj obor názvů.</span><span class="sxs-lookup"><span data-stu-id="000b9-106">Changing the prefix of a node does not change its namespace.</span></span> <span data-ttu-id="000b9-107">Obor názvů lze nastavit pouze při vytvoření uzlu.</span><span class="sxs-lookup"><span data-stu-id="000b9-107">The namespace can only be set when the node is created.</span></span> <span data-ttu-id="000b9-108">Když vyskytovat i dál stromu, nové atributy oboru názvů může nastavit jako trvalý, si tím se uspokojí předpony, které nastavíte.</span><span class="sxs-lookup"><span data-stu-id="000b9-108">When you persist the tree, new namespace attributes may be persisted out to satisfy the prefix you set.</span></span> <span data-ttu-id="000b9-109">Pokud nelze vytvořit nový obor názvů, předpona, která se změní tak, že uzel zachová svůj místní název a obor názvů.</span><span class="sxs-lookup"><span data-stu-id="000b9-109">If the new namespace cannot be created, then the prefix is changed so the node preserves its local name and namespace.</span></span> <span data-ttu-id="000b9-110">Následující příklad ukazuje obor názvů atribut přidávaný.</span><span class="sxs-lookup"><span data-stu-id="000b9-110">The following example shows a namespace attribute being added.</span></span>  
  
```vb  
Dim doc as XmlDocument = new XmlDocument()  
doc.LoadXml("<test xmlns='123'/>")  
Dim e as XmlElement = doc.DocumentElement  
e.Prefix = "a"  
Console.WriteLine(doc.InnerXml)  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
doc.LoadXml("<test xmlns='123'/>");  
XmlElement e = doc.DocumentElement;         
e.Prefix = "a";  
Console.WriteLine(doc.InnerXml);  
```  
  
 <span data-ttu-id="000b9-111">**Output**</span><span class="sxs-lookup"><span data-stu-id="000b9-111">**Output**</span></span>  
  
```xml  
<a:test xmlns="123" xmlns:a="123" />  
```  
  
 <span data-ttu-id="000b9-112">Když stromu byl trvale uložen na řetězec v důsledku volání **dokumentu. InnerXml**, `xmlns:a='123'` atributu byl přidán k zachování obor názvů `test` elementu.</span><span class="sxs-lookup"><span data-stu-id="000b9-112">When the tree was persisted to a string as a result of the call to **doc.InnerXml**, the `xmlns:a='123'` attribute was added to preserve the namespace of the `test` element.</span></span> <span data-ttu-id="000b9-113">Bylo `'123'`, a zůstal `'123'`.</span><span class="sxs-lookup"><span data-stu-id="000b9-113">It was `'123'`, and it remained `'123'`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="000b9-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="000b9-114">See also</span></span>

- [<span data-ttu-id="000b9-115">Model DOM (Document Object Model) dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="000b9-115">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
