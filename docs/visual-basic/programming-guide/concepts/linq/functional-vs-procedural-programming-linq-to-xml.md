---
title: Funkční vs. Procedurální programování (LINQ to XML) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: ea1015a5-d4c8-4d79-8e1e-ba17a40a4f39
ms.openlocfilehash: 892c6b7113fe1efdb8e855749c86ac5f9da8cbe4
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58813455"
---
# <a name="functional-vs-procedural-programming-linq-to-xml-visual-basic"></a><span data-ttu-id="10514-102">Funkční vs. Procedurální programování (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="10514-102">Functional vs. Procedural Programming (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="10514-103">Existují různé typy aplikací XML:</span><span class="sxs-lookup"><span data-stu-id="10514-103">There are various types of XML applications:</span></span>  
  
-   <span data-ttu-id="10514-104">Některé aplikace trvat zdroje dokumentů XML a vytvářet nové dokumenty XML, které jsou v odlišném tvaru než dokumenty zdroje.</span><span class="sxs-lookup"><span data-stu-id="10514-104">Some applications take source XML documents, and produce new XML documents that are in a different shape than the source documents.</span></span>  
  
-   <span data-ttu-id="10514-105">Některé aplikace trvat zdroje dokumentů XML a vytvoří výsledek dokumenty v úplně jiném formuláře, jako je HTML nebo text souborů CSV.</span><span class="sxs-lookup"><span data-stu-id="10514-105">Some applications take source XML documents, and produce result documents in an entirely different form, such as HTML or CSV text files.</span></span>  
  
-   <span data-ttu-id="10514-106">Některé aplikace trvat zdroje dokumentů XML a vkládání záznamů do databáze.</span><span class="sxs-lookup"><span data-stu-id="10514-106">Some applications take source XML documents, and insert records into a database.</span></span>  
  
-   <span data-ttu-id="10514-107">Některé aplikace vzít data z jiného zdroje, jako je například databáze a vytvářet dokumenty XML z něj.</span><span class="sxs-lookup"><span data-stu-id="10514-107">Some applications take data from another source, such as a database, and create XML documents from it.</span></span>  
  
 <span data-ttu-id="10514-108">Nejsou to všechny typy aplikací XML, ale toto jsou reprezentativní sadu typů funkcí, které má programátor XML k implementaci.</span><span class="sxs-lookup"><span data-stu-id="10514-108">These are not all of the types of XML applications, but these are a representative set of the types of functionality that an XML programmer has to implement.</span></span>  
  
 <span data-ttu-id="10514-109">Se všemi typy aplikací se používají dva přístupy kontrastní, které vývojář může trvat:</span><span class="sxs-lookup"><span data-stu-id="10514-109">With all of these types of applications, there are two contrasting approaches that a developer can take:</span></span>  
  
-   <span data-ttu-id="10514-110">Funkční konstrukce pomocí deklarativního přístupu.</span><span class="sxs-lookup"><span data-stu-id="10514-110">Functional construction using a declarative approach.</span></span>  
  
-   <span data-ttu-id="10514-111">Změna stromu XML v paměti pomocí kódu procedury.</span><span class="sxs-lookup"><span data-stu-id="10514-111">In-memory XML tree modification using procedural code.</span></span>  
  
 <span data-ttu-id="10514-112">Technologie LINQ to XML podporuje oba přístupy.</span><span class="sxs-lookup"><span data-stu-id="10514-112">LINQ to XML supports both approaches.</span></span>  
  
 <span data-ttu-id="10514-113">Při použití funkční přístup, můžete napsat transformace, které používat zdroje dokumentů a generovat zcela nové dokumenty výsledek s požadovaný tvar.</span><span class="sxs-lookup"><span data-stu-id="10514-113">When using the functional approach, you write transformations that take the source documents and generate completely new result documents with the desired shape.</span></span>  
  
 <span data-ttu-id="10514-114">Při úpravě stromu XML v místě, píšete kód, který prochází skrz a prochází uzly ve stromu XML v paměti, vkládání, odstraňování a úpravy uzlů podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="10514-114">When modifying an XML tree in place, you write code that traverses and navigates through nodes in an in-memory XML tree, inserting, deleting, and modifying nodes as necessary.</span></span>  
  
 <span data-ttu-id="10514-115">LINQ to XML můžete použít s oběma.</span><span class="sxs-lookup"><span data-stu-id="10514-115">You can use LINQ to XML with either approach.</span></span> <span data-ttu-id="10514-116">Použít stejné třídy a v některých případech stejné metody.</span><span class="sxs-lookup"><span data-stu-id="10514-116">You use the same classes, and in some cases the same methods.</span></span> <span data-ttu-id="10514-117">Struktura a cíle tyto dvě metody jsou však velmi odlišné.</span><span class="sxs-lookup"><span data-stu-id="10514-117">However, the structure and goals of the two approaches are very different.</span></span> <span data-ttu-id="10514-118">Například v různých situacích, jeden nebo jiný přístup se často mají lepší výkon a použijte více nebo méně paměti.</span><span class="sxs-lookup"><span data-stu-id="10514-118">For example, in different situations, one or the other approach will often have better performance, and use more or less memory.</span></span> <span data-ttu-id="10514-119">Kromě toho jeden nebo jiný přístup bude jednodušší zápis a poskytovat další udržovatelného kódu.</span><span class="sxs-lookup"><span data-stu-id="10514-119">In addition, one or the other approach will be easier to write and yield more maintainable code.</span></span>  
  
 <span data-ttu-id="10514-120">Tyto dva přístupy rozdíly najdete v tématu [změna stromu XML v paměti vs. Funkční konstrukce (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/in-memory-xml-tree-modification-vs-functional-construction.md).</span><span class="sxs-lookup"><span data-stu-id="10514-120">To see the two approaches contrasted, see [In-Memory XML Tree Modification vs. Functional Construction (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/in-memory-xml-tree-modification-vs-functional-construction.md).</span></span>  
  
 <span data-ttu-id="10514-121">Kurz týkající se zápisu funkční transformace, najdete v části [čistě funkční transformace XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md).</span><span class="sxs-lookup"><span data-stu-id="10514-121">For a tutorial on writing functional transformations, see [Pure Functional Transformations of XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10514-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="10514-122">See also</span></span>

- [<span data-ttu-id="10514-123">Přehled LINQ to XML programování (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="10514-123">LINQ to XML Programming Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
