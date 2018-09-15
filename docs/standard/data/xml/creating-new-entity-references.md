---
title: Vytváření nových odkazů na Entity
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: a42f81b3-0403-4e34-b346-7d2129804e54
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 67fdbcdbff64bcd91c80fbeaec0c41982b68d98f
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/15/2018
ms.locfileid: "45646139"
---
# <a name="creating-new-entity-references"></a><span data-ttu-id="f4005-102">Vytváření nových odkazů na Entity</span><span class="sxs-lookup"><span data-stu-id="f4005-102">Creating New Entity References</span></span>
<span data-ttu-id="f4005-103">**CreateEntityReference** metoda vytvoří nový **XmlEntityReference** uzlu.</span><span class="sxs-lookup"><span data-stu-id="f4005-103">The **CreateEntityReference** method creates a new **XmlEntityReference** node.</span></span> <span data-ttu-id="f4005-104">Pokud chcete zobrazit, pokud je už deklarovaný název entity, na kterou se odkazuje vypadá XML Document Object Model (DOM).</span><span class="sxs-lookup"><span data-stu-id="f4005-104">The XML Document Object Model (DOM) looks to see if the entity name being referenced has already been declared.</span></span> <span data-ttu-id="f4005-105">Pokud ano, podřízené uzly **XmlEntityReference** uzlu jsou zkopírovány z uzlu entity prohlášení.</span><span class="sxs-lookup"><span data-stu-id="f4005-105">If it has, the child nodes of **XmlEntityReference** node are copied from the entity declaration node.</span></span> <span data-ttu-id="f4005-106">Pokud neexistuje žádná deklarace entity, který odpovídá, prázdný textový uzel je připojen jako jediný podřízený uzel odkazu entity.</span><span class="sxs-lookup"><span data-stu-id="f4005-106">If there is no entity declaration that matches, an empty text node is attached as the only child of the entity reference node.</span></span> <span data-ttu-id="f4005-107">Protože podřízené uzly **XmlEntityReference** uzlu jsou kopie jiných uzlech, tyto podřízené uzly jsou jen pro čtení a nelze ji změnit.</span><span class="sxs-lookup"><span data-stu-id="f4005-107">Because the child nodes of the **XmlEntityReference** node are copies of other nodes, these child nodes are read-only and cannot be modified.</span></span>  
  
 <span data-ttu-id="f4005-108">Když se zkopírují uzly, může být oboru názvů v oboru místě odkaz na entitu.</span><span class="sxs-lookup"><span data-stu-id="f4005-108">When the nodes are copied, there may be a namespace in scope at the point of the entity reference.</span></span> <span data-ttu-id="f4005-109">Tento obor názvů má vliv na konfiguraci jakéhokoli uzlu elementu nebo atributu vygenerována.</span><span class="sxs-lookup"><span data-stu-id="f4005-109">This namespace affects the configuration of any element or attribute nodes generated.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f4005-110">Přidá podřízené uzly modelu DOM **EntityReference** pouze při vložení **EntityReference** uzel v dokumentu.</span><span class="sxs-lookup"><span data-stu-id="f4005-110">The DOM adds child nodes to the **EntityReference** only when you insert the **EntityReference** node to the document.</span></span> <span data-ttu-id="f4005-111">Nově vytvořené **EntityReference** uzly obsahovat podřízené uzly.</span><span class="sxs-lookup"><span data-stu-id="f4005-111">Newly created **EntityReference** nodes have no child nodes.</span></span>  
  
 <span data-ttu-id="f4005-112">I když **XmlDataDocument** je odvozenou třídu **třídou XMLDocument nastavenou na**, **objektu XmlDataDocument** nepodporuje vytváření odkazů na entity.</span><span class="sxs-lookup"><span data-stu-id="f4005-112">Even though the **XmlDataDocument** is a derived class of the **XmlDocument**, the **XmlDataDocument** does not support the creation of entity references.</span></span> <span data-ttu-id="f4005-113">Důvodem je, že **EntityReference** podřízené objekty jsou jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="f4005-113">This is because **EntityReference** children are read-only.</span></span> <span data-ttu-id="f4005-114">Podřízené objekty daného **EntityReference** uzel může zahrnovat více než jedné oblasti.</span><span class="sxs-lookup"><span data-stu-id="f4005-114">The children of an **EntityReference** node can span more than one region.</span></span> <span data-ttu-id="f4005-115">V takovém případě část řádku přidružené k oblasti, která obsahuje součást **EntityReference** budou jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="f4005-115">In this case, part of a row associated with the region that contains a part of an **EntityReference** will be read-only.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4005-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f4005-116">See also</span></span>

- [<span data-ttu-id="f4005-117">Model DOM (Document Object Model) dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="f4005-117">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
