---
title: Změna vlastností předpony oboru názvů
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: d5c87cbe-4d69-429f-aad5-3103c2ca2770
ms.openlocfilehash: b1df520d00d3a98b2e518092d4eff51b5d0b7741
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78158022"
---
# <a name="changing-namespace-prefix-properties"></a><span data-ttu-id="ce658-102">Změna vlastností předpony oboru názvů</span><span class="sxs-lookup"><span data-stu-id="ce658-102">Changing Namespace Prefix Properties</span></span>
<span data-ttu-id="ce658-103">Třída **XmlNode** umožňuje změnit předponu oboru názvů přidružené k danému uzlu.</span><span class="sxs-lookup"><span data-stu-id="ce658-103">The **XmlNode** class allows you to change the namespace prefix associated with a given node.</span></span> <span data-ttu-id="ce658-104">Například následující kód ukazuje předponu měněného prvku.</span><span class="sxs-lookup"><span data-stu-id="ce658-104">For example, the following code shows the prefix of an element being changed.</span></span>  
  
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
  
 <span data-ttu-id="ce658-105">**Výstup**</span><span class="sxs-lookup"><span data-stu-id="ce658-105">**Output**</span></span>  
  
```xml  
<b:test xmlns:a="123" xmlns:b="456" />  
```  
  
 <span data-ttu-id="ce658-106">Změna předpony uzlu nemění jeho obor názvů.</span><span class="sxs-lookup"><span data-stu-id="ce658-106">Changing the prefix of a node does not change its namespace.</span></span> <span data-ttu-id="ce658-107">Obor názvů lze nastavit pouze v případě, že je uzel vytvořen.</span><span class="sxs-lookup"><span data-stu-id="ce658-107">The namespace can only be set when the node is created.</span></span> <span data-ttu-id="ce658-108">Když zachová strom, mohou být nové atributy oboru názvů trvale nastaveny pro splnění nastavené předpony.</span><span class="sxs-lookup"><span data-stu-id="ce658-108">When you persist the tree, new namespace attributes may be persisted out to satisfy the prefix you set.</span></span> <span data-ttu-id="ce658-109">Pokud nový obor názvů nelze vytvořit, předpona je změněna, takže uzel zachovává svůj místní název a obor názvů.</span><span class="sxs-lookup"><span data-stu-id="ce658-109">If the new namespace cannot be created, then the prefix is changed so the node preserves its local name and namespace.</span></span> <span data-ttu-id="ce658-110">Následující příklad ukazuje přidávaného atributu oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="ce658-110">The following example shows a namespace attribute being added.</span></span>  
  
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
  
 <span data-ttu-id="ce658-111">**Výstup**</span><span class="sxs-lookup"><span data-stu-id="ce658-111">**Output**</span></span>  
  
```xml  
<a:test xmlns="123" xmlns:a="123" />  
```  
  
 <span data-ttu-id="ce658-112">V případě, že byl strom uložen do řetězce v důsledku volání metody **doc. InnerXml**, byl `xmlns:a='123'` přidán atribut pro zachování oboru názvů `test` elementu.</span><span class="sxs-lookup"><span data-stu-id="ce658-112">When the tree was persisted to a string as a result of the call to **doc.InnerXml**, the `xmlns:a='123'` attribute was added to preserve the namespace of the `test` element.</span></span> <span data-ttu-id="ce658-113">Bylo `'123'`to a zůstalo `'123'`.</span><span class="sxs-lookup"><span data-stu-id="ce658-113">It was `'123'`, and it remained `'123'`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce658-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="ce658-114">See also</span></span>

- [<span data-ttu-id="ce658-115">model DOM (Document Object Model) dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="ce658-115">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
