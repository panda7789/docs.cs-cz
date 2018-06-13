---
title: Dynamické aktualizace NodeLists a NamedNodeMaps
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 76c511fd-6704-4ca4-8078-860a68d898ad
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1de133d0208f1b86ad3240cdc00d8016af0a160c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33568963"
---
# <a name="dynamic-updates-to-nodelists-and-namednodemaps"></a><span data-ttu-id="5f941-102">Dynamické aktualizace NodeLists a NamedNodeMaps</span><span class="sxs-lookup"><span data-stu-id="5f941-102">Dynamic Updates to NodeLists and NamedNodeMaps</span></span>
<span data-ttu-id="5f941-103">Protože **XmlNodeList** a **XmlNamedNodeMap** obsahují sadu uzlů, ještě v dokumentu XML je načten do paměti a tento proces je upravována, stavů World Wide Web Consortium (W3C), které tyto objekty obsahující sadu uzlů musí být dynamické.</span><span class="sxs-lookup"><span data-stu-id="5f941-103">Because the **XmlNodeList** and the **XmlNamedNodeMap** contain a set of nodes, yet the XML document is loaded into memory and is being modified, the World Wide Web Consortium (W3C) states that these objects that contain sets of nodes need to be dynamic.</span></span> <span data-ttu-id="5f941-104">To znamená pokud se změní zdrojový dokument, pak data v těchto dvou objektů měli změnit také.</span><span class="sxs-lookup"><span data-stu-id="5f941-104">That is, if the underlying document changes, then the data in these two objects should change also.</span></span> <span data-ttu-id="5f941-105">Proto pokud máte **XmlNodeList** obsahující všechny podřízené elementy určitý element (například element X) a pak přidejte další elementu, element Q, v dokumentu v části element X. **XmlNodeList** by měly mít také tohoto nového elementu Q jeho kolekce přidat.</span><span class="sxs-lookup"><span data-stu-id="5f941-105">Therefore, if you have an **XmlNodeList** that contains all the child elements of a particular element (for example, element X), then you add an additional element, element Q, to the document under element X. The **XmlNodeList** should also have that new element Q added to its collection.</span></span> <span data-ttu-id="5f941-106">Platí to pozpátku.</span><span class="sxs-lookup"><span data-stu-id="5f941-106">The same is true in reverse.</span></span> <span data-ttu-id="5f941-107">Pokud uzel je přidán do **XmlNodeList**, se rovněž aktualizuje zdrojový dokument.</span><span class="sxs-lookup"><span data-stu-id="5f941-107">If a node is added to the **XmlNodeList**, the underlying document is updated as well.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f941-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="5f941-108">See Also</span></span>  
 [<span data-ttu-id="5f941-109">Model DOM (Document Object Model) dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="5f941-109">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
