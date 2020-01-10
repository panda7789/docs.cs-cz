---
title: Změna deklarací oboru názvů v dokumentu XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: a2758f40-e497-4964-8d8d-1bb68af14dcd
ms.openlocfilehash: b8aa670764deb8e77cfb67fd16dbcf8b1cc9b4c0
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711126"
---
# <a name="changing-namespace-declarations-in-an-xml-document"></a><span data-ttu-id="517d1-102">Změna deklarací oboru názvů v dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="517d1-102">Changing Namespace Declarations in an XML Document</span></span>
<span data-ttu-id="517d1-103">**XmlDocument** zpřístupňuje deklarace oboru názvů a atributy **xmlns** jako součást modelu objektu dokumentu.</span><span class="sxs-lookup"><span data-stu-id="517d1-103">The **XmlDocument** exposes namespace declarations and **xmlns** attributes as part of the document object model.</span></span> <span data-ttu-id="517d1-104">Ty jsou uloženy v dokumentu **XmlDocument**, takže když dokument uložíte, může zachovat umístění těchto atributů.</span><span class="sxs-lookup"><span data-stu-id="517d1-104">These are stored in the **XmlDocument**, so when you save the document, it can preserve the location of those attributes.</span></span> <span data-ttu-id="517d1-105">Změna těchto atributů nemá žádný vliv na vlastnosti **Name**, **NamespaceURI**a **prefixu** dalších uzlů, které jsou již ve stromové struktuře.</span><span class="sxs-lookup"><span data-stu-id="517d1-105">Changing these attributes has no affect on the **Name**, **NamespaceURI**, and **Prefix** properties of other nodes already in the tree.</span></span> <span data-ttu-id="517d1-106">Například pokud načtete následující dokument, `test` element má **NamespaceURI** `123.`</span><span class="sxs-lookup"><span data-stu-id="517d1-106">For example, if you load the following document, then the `test` element has **NamespaceURI** `123.`</span></span>  
  
```xml  
<test xmlns="123"/>  
```  
  
 <span data-ttu-id="517d1-107">Odeberete-li atribut `xmlns` následujícím způsobem, má `test` prvek stále **NamespaceURI** `123`.</span><span class="sxs-lookup"><span data-stu-id="517d1-107">If you remove the `xmlns` attribute as follows, then the `test` element still has the **NamespaceURI** of `123`.</span></span>  
  
```vb  
doc.documentElement.RemoveAttribute("xmlns")  
```  
  
```csharp  
doc.documentElement.RemoveAttribute("xmlns");  
```  
  
 <span data-ttu-id="517d1-108">Podobně platí, že pokud přidáte jiný atribut `xmlns` do prvku `doc` následujícím způsobem, `test` element má nadále `123`**NamespaceURI** .</span><span class="sxs-lookup"><span data-stu-id="517d1-108">Likewise, if you add a different `xmlns` attribute to the `doc` element as follows, then the `test` element still has **NamespaceURI** `123`.</span></span>  
  
```vb  
doc.documentElement.SetAttribute("xmlns","456")
```  
  
```csharp  
doc.documentElement.SetAttribute("xmlns","456");  
```  
  
 <span data-ttu-id="517d1-109">Proto změna atributů `xmlns` nebude mít žádný vliv, dokud neuložíte a znovu načtete objekt **XmlDocument** .</span><span class="sxs-lookup"><span data-stu-id="517d1-109">Therefore, changing `xmlns` attributes will have no affect until you save and reload the **XmlDocument** object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="517d1-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="517d1-110">See also</span></span>

- [<span data-ttu-id="517d1-111">Model DOM (Document Object Model) dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="517d1-111">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
