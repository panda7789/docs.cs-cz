---
title: Dynamické aktualizace pro NodeLists a NamedNodeMaps
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 76c511fd-6704-4ca4-8078-860a68d898ad
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9f56ba8711988f2f7d743dc4ff7b69272e2642a2
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44207405"
---
# <a name="dynamic-updates-to-nodelists-and-namednodemaps"></a><span data-ttu-id="a9bb0-102">Dynamické aktualizace pro NodeLists a NamedNodeMaps</span><span class="sxs-lookup"><span data-stu-id="a9bb0-102">Dynamic Updates to NodeLists and NamedNodeMaps</span></span>
<span data-ttu-id="a9bb0-103">Vzhledem k tomu, **XmlNodeList** a **XmlNamedNodeMap** obsahují sadu uzlů, ale dokument XML je načten do paměti a je upravována, World Wide Web Consortium (W3C) uvádí, že tyto objekty která obsahují sadu uzlů musí být dynamické.</span><span class="sxs-lookup"><span data-stu-id="a9bb0-103">Because the **XmlNodeList** and the **XmlNamedNodeMap** contain a set of nodes, yet the XML document is loaded into memory and is being modified, the World Wide Web Consortium (W3C) states that these objects that contain sets of nodes need to be dynamic.</span></span> <span data-ttu-id="a9bb0-104">To znamená pokud se změní podkladové dokument, pak data v těchto dvou objektů by měl změnit také.</span><span class="sxs-lookup"><span data-stu-id="a9bb0-104">That is, if the underlying document changes, then the data in these two objects should change also.</span></span> <span data-ttu-id="a9bb0-105">Proto pokud máte **XmlNodeList** , která obsahuje všechny podřízené prvky prvku konkrétní (například prvek X) a pak přidejte další prvek, Q, element v dokumentu v rámci elementu X. **XmlNodeList** musí být také tento nový prvek Q přidat do své kolekce.</span><span class="sxs-lookup"><span data-stu-id="a9bb0-105">Therefore, if you have an **XmlNodeList** that contains all the child elements of a particular element (for example, element X), then you add an additional element, element Q, to the document under element X. The **XmlNodeList** should also have that new element Q added to its collection.</span></span> <span data-ttu-id="a9bb0-106">Totéž platí v opačném pořadí.</span><span class="sxs-lookup"><span data-stu-id="a9bb0-106">The same is true in reverse.</span></span> <span data-ttu-id="a9bb0-107">Pokud uzel se přidá do **XmlNodeList**, je také aktualizovat zdrojový dokument.</span><span class="sxs-lookup"><span data-stu-id="a9bb0-107">If a node is added to the **XmlNodeList**, the underlying document is updated as well.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9bb0-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a9bb0-108">See also</span></span>

- [<span data-ttu-id="a9bb0-109">Model DOM (Document Object Model) dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="a9bb0-109">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
