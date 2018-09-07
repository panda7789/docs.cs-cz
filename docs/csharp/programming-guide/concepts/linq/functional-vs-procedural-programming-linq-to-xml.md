---
title: Funkční vs. Procedurální programování (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: fc64e39c-a487-4882-9169-da4de97917d9
ms.openlocfilehash: 888c360e1b868c79d378f2fc46a26c152121300f
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44071762"
---
# <a name="functional-vs-procedural-programming-linq-to-xml-c"></a><span data-ttu-id="672ab-102">Funkční vs. Procedurální programování (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="672ab-102">Functional vs. Procedural Programming (LINQ to XML) (C#)</span></span>
<span data-ttu-id="672ab-103">Existují různé typy aplikací XML:</span><span class="sxs-lookup"><span data-stu-id="672ab-103">There are various types of XML applications:</span></span>  
  
-   <span data-ttu-id="672ab-104">Některé aplikace trvat zdroje dokumentů XML a vytvářet nové dokumenty XML, které jsou v odlišném tvaru než dokumenty zdroje.</span><span class="sxs-lookup"><span data-stu-id="672ab-104">Some applications take source XML documents, and produce new XML documents that are in a different shape than the source documents.</span></span>  
  
-   <span data-ttu-id="672ab-105">Některé aplikace trvat zdroje dokumentů XML a vytvoří výsledek dokumenty v úplně jiném formuláře, jako je HTML nebo text souborů CSV.</span><span class="sxs-lookup"><span data-stu-id="672ab-105">Some applications take source XML documents, and produce result documents in an entirely different form, such as HTML or CSV text files.</span></span>  
  
-   <span data-ttu-id="672ab-106">Některé aplikace trvat zdroje dokumentů XML a vkládání záznamů do databáze.</span><span class="sxs-lookup"><span data-stu-id="672ab-106">Some applications take source XML documents, and insert records into a database.</span></span>  
  
-   <span data-ttu-id="672ab-107">Některé aplikace vzít data z jiného zdroje, jako je například databáze a vytvářet dokumenty XML z něj.</span><span class="sxs-lookup"><span data-stu-id="672ab-107">Some applications take data from another source, such as a database, and create XML documents from it.</span></span>  
  
 <span data-ttu-id="672ab-108">Nejsou to všechny typy aplikací XML, ale toto jsou reprezentativní sadu typů funkcí, které má programátor XML k implementaci.</span><span class="sxs-lookup"><span data-stu-id="672ab-108">These are not all of the types of XML applications, but these are a representative set of the types of functionality that an XML programmer has to implement.</span></span>  
  
 <span data-ttu-id="672ab-109">Se všemi typy aplikací se používají dva přístupy kontrastní, které vývojář může trvat:</span><span class="sxs-lookup"><span data-stu-id="672ab-109">With all of these types of applications, there are two contrasting approaches that a developer can take:</span></span>  
  
-   <span data-ttu-id="672ab-110">Funkční konstrukce pomocí deklarativního přístupu.</span><span class="sxs-lookup"><span data-stu-id="672ab-110">Functional construction using a declarative approach.</span></span>  
  
-   <span data-ttu-id="672ab-111">Změna stromu XML v paměti pomocí kódu procedury.</span><span class="sxs-lookup"><span data-stu-id="672ab-111">In-memory XML tree modification using procedural code.</span></span>  
  
 <span data-ttu-id="672ab-112">Technologie LINQ to XML podporuje oba přístupy.</span><span class="sxs-lookup"><span data-stu-id="672ab-112">LINQ to XML supports both approaches.</span></span>  
  
 <span data-ttu-id="672ab-113">Při použití funkční přístup, můžete napsat transformace, které používat zdroje dokumentů a generovat zcela nové dokumenty výsledek s požadovaný tvar.</span><span class="sxs-lookup"><span data-stu-id="672ab-113">When using the functional approach, you write transformations that take the source documents and generate completely new result documents with the desired shape.</span></span>  
  
 <span data-ttu-id="672ab-114">Při úpravě stromu XML v místě, píšete kód, který prochází skrz a prochází uzly ve stromu XML v paměti, vkládání, odstraňování a úpravy uzlů podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="672ab-114">When modifying an XML tree in place, you write code that traverses and navigates through nodes in an in-memory XML tree, inserting, deleting, and modifying nodes as necessary.</span></span>  
  
 <span data-ttu-id="672ab-115">LINQ to XML můžete použít s oběma.</span><span class="sxs-lookup"><span data-stu-id="672ab-115">You can use LINQ to XML with either approach.</span></span> <span data-ttu-id="672ab-116">Použít stejné třídy a v některých případech stejné metody.</span><span class="sxs-lookup"><span data-stu-id="672ab-116">You use the same classes, and in some cases the same methods.</span></span> <span data-ttu-id="672ab-117">Struktura a cíle tyto dvě metody jsou však velmi odlišné.</span><span class="sxs-lookup"><span data-stu-id="672ab-117">However, the structure and goals of the two approaches are very different.</span></span> <span data-ttu-id="672ab-118">Například v různých situacích, jeden nebo jiný přístup se často mají lepší výkon a použijte více nebo méně paměti.</span><span class="sxs-lookup"><span data-stu-id="672ab-118">For example, in different situations, one or the other approach will often have better performance, and use more or less memory.</span></span> <span data-ttu-id="672ab-119">Kromě toho jeden nebo jiný přístup bude jednodušší zápis a poskytovat další udržovatelného kódu.</span><span class="sxs-lookup"><span data-stu-id="672ab-119">In addition, one or the other approach will be easier to write and yield more maintainable code.</span></span>  
  
 <span data-ttu-id="672ab-120">Tyto dva přístupy rozdíly najdete v tématu [změna stromu XML v paměti vs. Funkční konstrukce (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="672ab-120">To see the two approaches contrasted, see [In-Memory XML Tree Modification vs. Functional Construction (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="672ab-121">Kurz týkající se zápisu funkční transformace, najdete v části [čistě funkční transformace XML (C#)](../../../../csharp/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md).</span><span class="sxs-lookup"><span data-stu-id="672ab-121">For a tutorial on writing functional transformations, see [Pure Functional Transformations of XML (C#)](../../../../csharp/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="672ab-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="672ab-122">See Also</span></span>

- [<span data-ttu-id="672ab-123">Přehled LINQ to XML programování (C#)</span><span class="sxs-lookup"><span data-stu-id="672ab-123">LINQ to XML Programming Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
