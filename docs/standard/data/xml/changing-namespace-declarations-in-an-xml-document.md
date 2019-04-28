---
title: Změna deklarací oboru názvů v dokumentu XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: a2758f40-e497-4964-8d8d-1bb68af14dcd
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4a6b80a885f43facf4b3d4dd1dcb56d937d4f8de
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61669157"
---
# <a name="changing-namespace-declarations-in-an-xml-document"></a><span data-ttu-id="cd697-102">Změna deklarací oboru názvů v dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="cd697-102">Changing Namespace Declarations in an XML Document</span></span>
<span data-ttu-id="cd697-103">**XmlDocument** vystavuje deklarace oboru názvů a **xmlns** atributy jako součást modelu objektu dokumentu.</span><span class="sxs-lookup"><span data-stu-id="cd697-103">The **XmlDocument** exposes namespace declarations and **xmlns** attributes as part of the document object model.</span></span> <span data-ttu-id="cd697-104">Tyto jsou uložené v **XmlDocument**, takže při ukládání dokumentu, můžete zachovat umístění těchto atributů.</span><span class="sxs-lookup"><span data-stu-id="cd697-104">These are stored in the **XmlDocument**, so when you save the document, it can preserve the location of those attributes.</span></span> <span data-ttu-id="cd697-105">Změna těchto atributů nemá žádný vliv na **název**, **NamespaceURI**, a **předpony** vlastnosti ostatní uzly již ve stromové struktuře.</span><span class="sxs-lookup"><span data-stu-id="cd697-105">Changing these attributes has no affect on the **Name**, **NamespaceURI**, and **Prefix** properties of other nodes already in the tree.</span></span> <span data-ttu-id="cd697-106">Například pokud načítáte následující dokument pak bude `test` element má **NamespaceURI** `123.`</span><span class="sxs-lookup"><span data-stu-id="cd697-106">For example, if you load the following document, then the `test` element has **NamespaceURI** `123.`</span></span>  
  
```xml  
<test xmlns="123"/>  
```  
  
 <span data-ttu-id="cd697-107">Pokud odeberete `xmlns` atribut následujícím způsobem, pak bude `test` element má stále **NamespaceURI** z `123`.</span><span class="sxs-lookup"><span data-stu-id="cd697-107">If you remove the `xmlns` attribute as follows, then the `test` element still has the **NamespaceURI** of `123`.</span></span>  
  
```vb  
doc.documentElement.RemoveAttribute("xmlns")  
```  
  
```csharp  
doc.documentElement.RemoveAttribute("xmlns");  
```  
  
 <span data-ttu-id="cd697-108">Podobně pokud chcete přidat jiný `xmlns` atribut `doc` element následujícím způsobem, pak bude `test` element má stále **NamespaceURI** `123`.</span><span class="sxs-lookup"><span data-stu-id="cd697-108">Likewise, if you add a different `xmlns` attribute to the `doc` element as follows, then the `test` element still has **NamespaceURI** `123`.</span></span>  
  
```vb  
doc.documentElement.SetAttribute("xmlns","456");  
```  
  
```csharp  
doc.documentElement.SetAttribute("xmlns","456");  
```  
  
 <span data-ttu-id="cd697-109">Proto se mění `xmlns` atributy se nemají žádný vliv, dokud uložit a znovu načíst **XmlDocument** objektu.</span><span class="sxs-lookup"><span data-stu-id="cd697-109">Therefore, changing `xmlns` attributes will have no affect until you save and reload the **XmlDocument** object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd697-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cd697-110">See also</span></span>

- [<span data-ttu-id="cd697-111">Model DOM (Document Object Model) dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="cd697-111">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
