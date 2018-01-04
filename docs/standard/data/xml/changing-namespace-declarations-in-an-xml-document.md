---
title: "Změna Namespace – deklarace v dokumentu XML"
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
ms.assetid: a2758f40-e497-4964-8d8d-1bb68af14dcd
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 6db78e689b8529ef62a3b42c2cefb6a5b3d3f02f
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="changing-namespace-declarations-in-an-xml-document"></a><span data-ttu-id="5ce46-102">Změna Namespace – deklarace v dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="5ce46-102">Changing Namespace Declarations in an XML Document</span></span>
<span data-ttu-id="5ce46-103">**Třídou XMLDocument nastavenou na** vystavuje deklarace oboru názvů a **xmlns** atributy jako součást modelu objektu dokumentu.</span><span class="sxs-lookup"><span data-stu-id="5ce46-103">The **XmlDocument** exposes namespace declarations and **xmlns** attributes as part of the document object model.</span></span> <span data-ttu-id="5ce46-104">Tyto jsou uložené v **třídou XMLDocument nastavenou na**, takže při ukládání dokumentu, ho můžete zachovat umístění těchto atributů.</span><span class="sxs-lookup"><span data-stu-id="5ce46-104">These are stored in the **XmlDocument**, so when you save the document, it can preserve the location of those attributes.</span></span> <span data-ttu-id="5ce46-105">Změna těchto atributů nemá žádný vliv na **název**, **NamespaceURI**, a **předpony** vlastnosti dalších uzlů již ve stromové struktuře.</span><span class="sxs-lookup"><span data-stu-id="5ce46-105">Changing these attributes has no affect on the **Name**, **NamespaceURI**, and **Prefix** properties of other nodes already in the tree.</span></span> <span data-ttu-id="5ce46-106">Například, Pokud zavedete v následujících dokumentech pak se `test` má element **NamespaceURI**`123.`</span><span class="sxs-lookup"><span data-stu-id="5ce46-106">For example, if you load the following document, then the `test` element has **NamespaceURI** `123.`</span></span>  
  
```xml  
<test xmlns="123"/>  
```  
  
 <span data-ttu-id="5ce46-107">Pokud odeberete `xmlns` atribut následujícím způsobem, pak se `test` element má stále **NamespaceURI** z `123`.</span><span class="sxs-lookup"><span data-stu-id="5ce46-107">If you remove the `xmlns` attribute as follows, then the `test` element still has the **NamespaceURI** of `123`.</span></span>  
  
```vb  
doc.documentElement.RemoveAttribute("xmlns")  
```  
  
```csharp  
doc.documentElement.RemoveAttribute("xmlns");  
```  
  
 <span data-ttu-id="5ce46-108">Podobně pokud přidáte jinou `xmlns` atribut `doc` element následujícím způsobem, pak se `test` element má stále **NamespaceURI** `123`.</span><span class="sxs-lookup"><span data-stu-id="5ce46-108">Likewise, if you add a different `xmlns` attribute to the `doc` element as follows, then the `test` element still has **NamespaceURI** `123`.</span></span>  
  
```vb  
doc.documentElement.SetAttribute("xmlns","456");  
```  
  
```csharp  
doc.documentElement.SetAttribute("xmlns","456");  
```  
  
 <span data-ttu-id="5ce46-109">Proto změna `xmlns` atributy bude mít žádný účinek, dokud uložíte a znovu načtete **třídou XMLDocument nastavenou na** objektu.</span><span class="sxs-lookup"><span data-stu-id="5ce46-109">Therefore, changing `xmlns` attributes will have no affect until you save and reload the **XmlDocument** object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ce46-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="5ce46-110">See Also</span></span>  
 [<span data-ttu-id="5ce46-111">Model DOM (Document Object Model) dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="5ce46-111">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
