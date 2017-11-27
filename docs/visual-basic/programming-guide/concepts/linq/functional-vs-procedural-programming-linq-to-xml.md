---
title: "Funkční vs. Procedurální programování (technologie LINQ to XML) (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ea1015a5-d4c8-4d79-8e1e-ba17a40a4f39
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7e47ff583146ab4258e219537cdc01821009e965
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="functional-vs-procedural-programming-linq-to-xml-visual-basic"></a><span data-ttu-id="a4317-102">Funkční vs. Procedurální programování (technologie LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a4317-102">Functional vs. Procedural Programming (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="a4317-103">Existují různé typy aplikací XML:</span><span class="sxs-lookup"><span data-stu-id="a4317-103">There are various types of XML applications:</span></span>  
  
-   <span data-ttu-id="a4317-104">Některé aplikace trvat zdroj XML – dokumenty a vytváření nových dokumentů XML, které se nacházejí v různých obrazce než dokumenty zdroje.</span><span class="sxs-lookup"><span data-stu-id="a4317-104">Some applications take source XML documents, and produce new XML documents that are in a different shape than the source documents.</span></span>  
  
-   <span data-ttu-id="a4317-105">Některé aplikace trvat zdroj XML – dokumenty a vytvořit výsledek dokumenty ve formuláři úplně jiné, jako jsou soubory HTML nebo CSV text.</span><span class="sxs-lookup"><span data-stu-id="a4317-105">Some applications take source XML documents, and produce result documents in an entirely different form, such as HTML or CSV text files.</span></span>  
  
-   <span data-ttu-id="a4317-106">Některé aplikace trvat zdroj XML – dokumenty a vložit záznamů do databáze.</span><span class="sxs-lookup"><span data-stu-id="a4317-106">Some applications take source XML documents, and insert records into a database.</span></span>  
  
-   <span data-ttu-id="a4317-107">Některé aplikace trvat data z jiného zdroje, jako je například databáze a vytvářet dokumenty XML z něj.</span><span class="sxs-lookup"><span data-stu-id="a4317-107">Some applications take data from another source, such as a database, and create XML documents from it.</span></span>  
  
 <span data-ttu-id="a4317-108">Tyto nejsou všechny typy aplikací, XML, ale toto jsou reprezentativní sadu typy funkcí, které programátory XML musí implementovat.</span><span class="sxs-lookup"><span data-stu-id="a4317-108">These are not all of the types of XML applications, but these are a representative set of the types of functionality that an XML programmer has to implement.</span></span>  
  
 <span data-ttu-id="a4317-109">Se všemi z těchto typů aplikací existují dva přístupy kontrastní, které může provádět vývojář:</span><span class="sxs-lookup"><span data-stu-id="a4317-109">With all of these types of applications, there are two contrasting approaches that a developer can take:</span></span>  
  
-   <span data-ttu-id="a4317-110">Funkční konstrukce deklarativní přístup.</span><span class="sxs-lookup"><span data-stu-id="a4317-110">Functional construction using a declarative approach.</span></span>  
  
-   <span data-ttu-id="a4317-111">Změna stromu XML v paměti pomocí procedurální kódu.</span><span class="sxs-lookup"><span data-stu-id="a4317-111">In-memory XML tree modification using procedural code.</span></span>  
  
 <span data-ttu-id="a4317-112">Technologie LINQ to XML podporuje obou přístupů.</span><span class="sxs-lookup"><span data-stu-id="a4317-112">LINQ to XML supports both approaches.</span></span>  
  
 <span data-ttu-id="a4317-113">Pokud používáte funkční přístup, napíšete transformace, které provádějí dokumenty zdroje a generovat úplně nové dokumenty výsledek s požadovaný tvar.</span><span class="sxs-lookup"><span data-stu-id="a4317-113">When using the functional approach, you write transformations that take the source documents and generate completely new result documents with the desired shape.</span></span>  
  
 <span data-ttu-id="a4317-114">Při úpravě strom XML na místě, můžete napsat kód, který prochází a přejde na uzly ve stromu XML v paměti, vkládání, odstraňování a změny uzly podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="a4317-114">When modifying an XML tree in place, you write code that traverses and navigates through nodes in an in-memory XML tree, inserting, deleting, and modifying nodes as necessary.</span></span>  
  
 <span data-ttu-id="a4317-115">Technologie LINQ to XML můžete použít s buď přístup.</span><span class="sxs-lookup"><span data-stu-id="a4317-115">You can use LINQ to XML with either approach.</span></span> <span data-ttu-id="a4317-116">Můžete použít stejné třídy a v některých případech stejné metody.</span><span class="sxs-lookup"><span data-stu-id="a4317-116">You use the same classes, and in some cases the same methods.</span></span> <span data-ttu-id="a4317-117">Struktura a cílů dva přístupy se však velmi liší.</span><span class="sxs-lookup"><span data-stu-id="a4317-117">However, the structure and goals of the two approaches are very different.</span></span> <span data-ttu-id="a4317-118">Například v různých situacích jedno nebo jiných přístup se často mají lepší výkon a použít více nebo méně paměti.</span><span class="sxs-lookup"><span data-stu-id="a4317-118">For example, in different situations, one or the other approach will often have better performance, and use more or less memory.</span></span> <span data-ttu-id="a4317-119">Kromě toho jeden nebo jiných přístupu bude jednodušší k zápisu a yield další udržovatelného kódu.</span><span class="sxs-lookup"><span data-stu-id="a4317-119">In addition, one or the other approach will be easier to write and yield more maintainable code.</span></span>  
  
 <span data-ttu-id="a4317-120">Tyto dva přístupy, na rozdíl od aktualizovaného najdete v sekci [vs úpravy stromu XML v paměti. Funkční konstrukce (technologie LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/in-memory-xml-tree-modification-vs-functional-construction.md).</span><span class="sxs-lookup"><span data-stu-id="a4317-120">To see the two approaches contrasted, see [In-Memory XML Tree Modification vs. Functional Construction (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/in-memory-xml-tree-modification-vs-functional-construction.md).</span></span>  
  
 <span data-ttu-id="a4317-121">Kurz týkající se funkční transformace zápis, najdete v části [čistý funkční transformace XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md).</span><span class="sxs-lookup"><span data-stu-id="a4317-121">For a tutorial on writing functional transformations, see [Pure Functional Transformations of XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4317-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="a4317-122">See Also</span></span>  
 [<span data-ttu-id="a4317-123">Technologie LINQ to přehled programování v XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a4317-123">LINQ to XML Programming Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
