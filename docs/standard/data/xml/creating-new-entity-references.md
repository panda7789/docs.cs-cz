---
title: "Vytvoření nové odkazy na Entity"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a42f81b3-0403-4e34-b346-7d2129804e54
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 22e9b66f58275141cf9da154573ca43a0b90affc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="creating-new-entity-references"></a><span data-ttu-id="a188b-102">Vytvoření nové odkazy na Entity</span><span class="sxs-lookup"><span data-stu-id="a188b-102">Creating New Entity References</span></span>
<span data-ttu-id="a188b-103">**CreateEntityReference** metoda vytvoří novou **XmlEntityReference** uzlu.</span><span class="sxs-lookup"><span data-stu-id="a188b-103">The **CreateEntityReference** method creates a new **XmlEntityReference** node.</span></span> <span data-ttu-id="a188b-104">XML modelu DOM (Document Object) zjistí, pokud již byl deklarován název entity se na ně odkazovat.</span><span class="sxs-lookup"><span data-stu-id="a188b-104">The XML Document Object Model (DOM) looks to see if the entity name being referenced has already been declared.</span></span> <span data-ttu-id="a188b-105">Pokud ano, podřízené uzly **XmlEntityReference** uzlu se zkopírují z uzlu deklarace entity.</span><span class="sxs-lookup"><span data-stu-id="a188b-105">If it has, the child nodes of **XmlEntityReference** node are copied from the entity declaration node.</span></span> <span data-ttu-id="a188b-106">Pokud není k dispozici žádná deklarace entity, který odpovídá, je připojen prázdný textový uzel jako jediným podřízeným entity uzlu odkazu.</span><span class="sxs-lookup"><span data-stu-id="a188b-106">If there is no entity declaration that matches, an empty text node is attached as the only child of the entity reference node.</span></span> <span data-ttu-id="a188b-107">Protože podřízené uzly **XmlEntityReference** uzlu jsou kopie další uzly, tyto podřízené uzly jsou jen pro čtení a nelze jej změnit.</span><span class="sxs-lookup"><span data-stu-id="a188b-107">Because the child nodes of the **XmlEntityReference** node are copies of other nodes, these child nodes are read-only and cannot be modified.</span></span>  
  
 <span data-ttu-id="a188b-108">Pokud se zkopírují uzlů, může být obor názvů v oboru v místě odkaz na entitu.</span><span class="sxs-lookup"><span data-stu-id="a188b-108">When the nodes are copied, there may be a namespace in scope at the point of the entity reference.</span></span> <span data-ttu-id="a188b-109">Tento obor názvů ovlivňuje konfigurace elementu nebo atributu uzlů, která se generuje.</span><span class="sxs-lookup"><span data-stu-id="a188b-109">This namespace affects the configuration of any element or attribute nodes generated.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a188b-110">Přidá podřízené uzly modelu DOM **EntityReference** pouze při vložení **EntityReference** uzlu v dokumentu.</span><span class="sxs-lookup"><span data-stu-id="a188b-110">The DOM adds child nodes to the **EntityReference** only when you insert the **EntityReference** node to the document.</span></span> <span data-ttu-id="a188b-111">Nově vytvořený **EntityReference** uzly mít žádné podřízené uzly.</span><span class="sxs-lookup"><span data-stu-id="a188b-111">Newly created **EntityReference** nodes have no child nodes.</span></span>  
  
 <span data-ttu-id="a188b-112">I když **XmlDataDocument** je třída odvozená z **třídou XMLDocument nastavenou na**, **XmlDataDocument** nepodporuje vytvoření odkazy na entity.</span><span class="sxs-lookup"><span data-stu-id="a188b-112">Even though the **XmlDataDocument** is a derived class of the **XmlDocument**, the **XmlDataDocument** does not support the creation of entity references.</span></span> <span data-ttu-id="a188b-113">Důvodem je, že **EntityReference** podřízené objekty jsou jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="a188b-113">This is because **EntityReference** children are read-only.</span></span> <span data-ttu-id="a188b-114">Podřízené objekty daného **EntityReference** uzlu může zahrnovat více oblastí.</span><span class="sxs-lookup"><span data-stu-id="a188b-114">The children of an **EntityReference** node can span more than one region.</span></span> <span data-ttu-id="a188b-115">V takovém případě součástí řádek přidružené k oblasti, která obsahuje součást **EntityReference** budou jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="a188b-115">In this case, part of a row associated with the region that contains a part of an **EntityReference** will be read-only.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a188b-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="a188b-116">See Also</span></span>  
 [<span data-ttu-id="a188b-117">XML Document Object Model (DOM).</span><span class="sxs-lookup"><span data-stu-id="a188b-117">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
