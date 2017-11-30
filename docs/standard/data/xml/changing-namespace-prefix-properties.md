---
title: "Změna vlastností Namespace předpony"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: d5c87cbe-4d69-429f-aad5-3103c2ca2770
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 7ce6e4b705188b9c1d0949703991633e3f450689
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="changing-namespace-prefix-properties"></a><span data-ttu-id="77c98-102">Změna vlastností Namespace předpony</span><span class="sxs-lookup"><span data-stu-id="77c98-102">Changing Namespace Prefix Properties</span></span>
<span data-ttu-id="77c98-103">**XmlNode** třída umožňuje změnit Předpona oboru názvů, které jsou přidružené k danému uzlu.</span><span class="sxs-lookup"><span data-stu-id="77c98-103">The **XmlNode** class allows you to change the namespace prefix associated with a given node.</span></span> <span data-ttu-id="77c98-104">Například následující kód ukazuje předponu elementu mění.</span><span class="sxs-lookup"><span data-stu-id="77c98-104">For example, the following code shows the prefix of an element being changed.</span></span>  
  
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
  
 <span data-ttu-id="77c98-105">**Výstup**</span><span class="sxs-lookup"><span data-stu-id="77c98-105">**Output**</span></span>  
  
```xml  
<b:test xmlns:a="123" xmlns:b="456" />  
```  
  
 <span data-ttu-id="77c98-106">Změna předponu uzlu nedojde ke změně jeho obor názvů.</span><span class="sxs-lookup"><span data-stu-id="77c98-106">Changing the prefix of a node does not change its namespace.</span></span> <span data-ttu-id="77c98-107">Obor názvů lze nastavit pouze při vytváření uzlu.</span><span class="sxs-lookup"><span data-stu-id="77c98-107">The namespace can only be set when the node is created.</span></span> <span data-ttu-id="77c98-108">Při můžete zachovat stromu, může se vyhovět předponu, která nastavíte nové atributy oboru názvů trvalé.</span><span class="sxs-lookup"><span data-stu-id="77c98-108">When you persist the tree, new namespace attributes may be persisted out to satisfy the prefix you set.</span></span> <span data-ttu-id="77c98-109">Pokud nelze vytvořit nový obor názvů, se změní předponu, takže uzlu zachovává svůj místní názvem a oborem názvů.</span><span class="sxs-lookup"><span data-stu-id="77c98-109">If the new namespace cannot be created, then the prefix is changed so the node preserves its local name and namespace.</span></span> <span data-ttu-id="77c98-110">Následující příklad ukazuje, obor názvů atribut, který chcete přidat.</span><span class="sxs-lookup"><span data-stu-id="77c98-110">The following example shows a namespace attribute being added.</span></span>  
  
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
  
 <span data-ttu-id="77c98-111">**Výstup**</span><span class="sxs-lookup"><span data-stu-id="77c98-111">**Output**</span></span>  
  
```xml  
<a:test xmlns="123" xmlns:a="123" />  
```  
  
 <span data-ttu-id="77c98-112">Pokud byl stromu trvalé na řetězec v důsledku volání **dokumentů. InnerXml**, `xmlns:a='123'` atribut byla přidána do zachovat obor názvů `test` elementu.</span><span class="sxs-lookup"><span data-stu-id="77c98-112">When the tree was persisted to a string as a result of the call to **doc.InnerXml**, the `xmlns:a='123'` attribute was added to preserve the namespace of the `test` element.</span></span> <span data-ttu-id="77c98-113">Byl `'123'`, a přesto zůstala `'123'`.</span><span class="sxs-lookup"><span data-stu-id="77c98-113">It was `'123'`, and it remained `'123'`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77c98-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="77c98-114">See Also</span></span>  
 [<span data-ttu-id="77c98-115">XML Document Object Model (DOM).</span><span class="sxs-lookup"><span data-stu-id="77c98-115">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
