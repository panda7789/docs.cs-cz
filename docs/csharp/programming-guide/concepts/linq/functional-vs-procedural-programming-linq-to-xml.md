---
title: Funkční vs. Procedurální programování (technologie LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: fc64e39c-a487-4882-9169-da4de97917d9
ms.openlocfilehash: 16d78e967fd5379940ac93c82e3bb59c60941e58
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33328211"
---
# <a name="functional-vs-procedural-programming-linq-to-xml-c"></a><span data-ttu-id="b6c45-102">Funkční vs. Procedurální programování (technologie LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="b6c45-102">Functional vs. Procedural Programming (LINQ to XML) (C#)</span></span>
<span data-ttu-id="b6c45-103">Existují různé typy aplikací XML:</span><span class="sxs-lookup"><span data-stu-id="b6c45-103">There are various types of XML applications:</span></span>  
  
-   <span data-ttu-id="b6c45-104">Některé aplikace trvat zdroj XML – dokumenty a vytváření nových dokumentů XML, které se nacházejí v různých obrazce než dokumenty zdroje.</span><span class="sxs-lookup"><span data-stu-id="b6c45-104">Some applications take source XML documents, and produce new XML documents that are in a different shape than the source documents.</span></span>  
  
-   <span data-ttu-id="b6c45-105">Některé aplikace trvat zdroj XML – dokumenty a vytvořit výsledek dokumenty ve formuláři úplně jiné, jako jsou soubory HTML nebo CSV text.</span><span class="sxs-lookup"><span data-stu-id="b6c45-105">Some applications take source XML documents, and produce result documents in an entirely different form, such as HTML or CSV text files.</span></span>  
  
-   <span data-ttu-id="b6c45-106">Některé aplikace trvat zdroj XML – dokumenty a vložit záznamů do databáze.</span><span class="sxs-lookup"><span data-stu-id="b6c45-106">Some applications take source XML documents, and insert records into a database.</span></span>  
  
-   <span data-ttu-id="b6c45-107">Některé aplikace trvat data z jiného zdroje, jako je například databáze a vytvářet dokumenty XML z něj.</span><span class="sxs-lookup"><span data-stu-id="b6c45-107">Some applications take data from another source, such as a database, and create XML documents from it.</span></span>  
  
 <span data-ttu-id="b6c45-108">Tyto nejsou všechny typy aplikací, XML, ale toto jsou reprezentativní sadu typy funkcí, které programátory XML musí implementovat.</span><span class="sxs-lookup"><span data-stu-id="b6c45-108">These are not all of the types of XML applications, but these are a representative set of the types of functionality that an XML programmer has to implement.</span></span>  
  
 <span data-ttu-id="b6c45-109">Se všemi z těchto typů aplikací existují dva přístupy kontrastní, které může provádět vývojář:</span><span class="sxs-lookup"><span data-stu-id="b6c45-109">With all of these types of applications, there are two contrasting approaches that a developer can take:</span></span>  
  
-   <span data-ttu-id="b6c45-110">Funkční konstrukce deklarativní přístup.</span><span class="sxs-lookup"><span data-stu-id="b6c45-110">Functional construction using a declarative approach.</span></span>  
  
-   <span data-ttu-id="b6c45-111">Změna stromu XML v paměti pomocí procedurální kódu.</span><span class="sxs-lookup"><span data-stu-id="b6c45-111">In-memory XML tree modification using procedural code.</span></span>  
  
 <span data-ttu-id="b6c45-112">Technologie LINQ to XML podporuje obou přístupů.</span><span class="sxs-lookup"><span data-stu-id="b6c45-112">LINQ to XML supports both approaches.</span></span>  
  
 <span data-ttu-id="b6c45-113">Pokud používáte funkční přístup, napíšete transformace, které provádějí dokumenty zdroje a generovat úplně nové dokumenty výsledek s požadovaný tvar.</span><span class="sxs-lookup"><span data-stu-id="b6c45-113">When using the functional approach, you write transformations that take the source documents and generate completely new result documents with the desired shape.</span></span>  
  
 <span data-ttu-id="b6c45-114">Při úpravě strom XML na místě, můžete napsat kód, který prochází a přejde na uzly ve stromu XML v paměti, vkládání, odstraňování a změny uzly podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="b6c45-114">When modifying an XML tree in place, you write code that traverses and navigates through nodes in an in-memory XML tree, inserting, deleting, and modifying nodes as necessary.</span></span>  
  
 <span data-ttu-id="b6c45-115">Technologie LINQ to XML můžete použít s buď přístup.</span><span class="sxs-lookup"><span data-stu-id="b6c45-115">You can use LINQ to XML with either approach.</span></span> <span data-ttu-id="b6c45-116">Můžete použít stejné třídy a v některých případech stejné metody.</span><span class="sxs-lookup"><span data-stu-id="b6c45-116">You use the same classes, and in some cases the same methods.</span></span> <span data-ttu-id="b6c45-117">Struktura a cílů dva přístupy se však velmi liší.</span><span class="sxs-lookup"><span data-stu-id="b6c45-117">However, the structure and goals of the two approaches are very different.</span></span> <span data-ttu-id="b6c45-118">Například v různých situacích jedno nebo jiných přístup se často mají lepší výkon a použít více nebo méně paměti.</span><span class="sxs-lookup"><span data-stu-id="b6c45-118">For example, in different situations, one or the other approach will often have better performance, and use more or less memory.</span></span> <span data-ttu-id="b6c45-119">Kromě toho jeden nebo jiných přístupu bude jednodušší k zápisu a yield další udržovatelného kódu.</span><span class="sxs-lookup"><span data-stu-id="b6c45-119">In addition, one or the other approach will be easier to write and yield more maintainable code.</span></span>  
  
 <span data-ttu-id="b6c45-120">Tyto dva přístupy, na rozdíl od aktualizovaného najdete v sekci [vs úpravy stromu XML v paměti. Funkční konstrukce (technologie LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="b6c45-120">To see the two approaches contrasted, see [In-Memory XML Tree Modification vs. Functional Construction (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="b6c45-121">Kurz týkající se funkční transformace zápis, najdete v části [čistý funkční transformace XML (C#)](../../../../csharp/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md).</span><span class="sxs-lookup"><span data-stu-id="b6c45-121">For a tutorial on writing functional transformations, see [Pure Functional Transformations of XML (C#)](../../../../csharp/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6c45-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="b6c45-122">See Also</span></span>  
 [<span data-ttu-id="b6c45-123">Technologie LINQ to XML přehled programování (C#)</span><span class="sxs-lookup"><span data-stu-id="b6c45-123">LINQ to XML Programming Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
