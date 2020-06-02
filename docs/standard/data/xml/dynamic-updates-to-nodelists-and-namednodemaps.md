---
title: Dynamické aktualizace pro NodeLists a NamedNodeMaps
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 76c511fd-6704-4ca4-8078-860a68d898ad
ms.openlocfilehash: 0199f24e9ef8dd28f91976edd50f78399dc893ef
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84292082"
---
# <a name="dynamic-updates-to-nodelists-and-namednodemaps"></a><span data-ttu-id="41214-102">Dynamické aktualizace pro NodeLists a NamedNodeMaps</span><span class="sxs-lookup"><span data-stu-id="41214-102">Dynamic Updates to NodeLists and NamedNodeMaps</span></span>
<span data-ttu-id="41214-103">Vzhledem k tomu, že **XmlNodeList** a **XmlNamedNodeMap** obsahují sadu uzlů, ale dokument XML je načten do paměti a je upravován, konsorcium World Wide Web (W3C) uvádí, že tyto objekty, které obsahují sady uzlů, musí být dynamické.</span><span class="sxs-lookup"><span data-stu-id="41214-103">Because the **XmlNodeList** and the **XmlNamedNodeMap** contain a set of nodes, yet the XML document is loaded into memory and is being modified, the World Wide Web Consortium (W3C) states that these objects that contain sets of nodes need to be dynamic.</span></span> <span data-ttu-id="41214-104">To znamená, že pokud se změní podkladové dokumenty, data v těchto dvou objektech by se měla změnit také.</span><span class="sxs-lookup"><span data-stu-id="41214-104">That is, if the underlying document changes, then the data in these two objects should change also.</span></span> <span data-ttu-id="41214-105">Proto pokud máte **XmlNodeList** , který obsahuje všechny podřízené prvky určitého prvku (například element X), pak přidáte další prvek, element Q, do dokumentu pod prvkem x. **XmlNodeList** by měl také mít přidán nový element Q do své kolekce.</span><span class="sxs-lookup"><span data-stu-id="41214-105">Therefore, if you have an **XmlNodeList** that contains all the child elements of a particular element (for example, element X), then you add an additional element, element Q, to the document under element X. The **XmlNodeList** should also have that new element Q added to its collection.</span></span> <span data-ttu-id="41214-106">Totéž platí v obráceném pořadí.</span><span class="sxs-lookup"><span data-stu-id="41214-106">The same is true in reverse.</span></span> <span data-ttu-id="41214-107">Pokud se do **XmlNodeList**přidá uzel, bude aktualizován i příslušný dokument.</span><span class="sxs-lookup"><span data-stu-id="41214-107">If a node is added to the **XmlNodeList**, the underlying document is updated as well.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41214-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="41214-108">See also</span></span>

- [<span data-ttu-id="41214-109">model DOM (Document Object Model) dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="41214-109">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
