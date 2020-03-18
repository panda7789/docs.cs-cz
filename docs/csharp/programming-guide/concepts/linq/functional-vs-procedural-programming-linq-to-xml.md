---
title: Funkční vs. procedurální programování (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: fc64e39c-a487-4882-9169-da4de97917d9
ms.openlocfilehash: e87114d2edcda4b2df14eb2d84f62ebe9638b5eb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "69594258"
---
# <a name="functional-vs-procedural-programming-linq-to-xml-c"></a><span data-ttu-id="a4966-102">Funkční vs. procedurální programování (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="a4966-102">Functional vs. Procedural Programming (LINQ to XML) (C#)</span></span>
<span data-ttu-id="a4966-103">Existují různé typy xml aplikací:</span><span class="sxs-lookup"><span data-stu-id="a4966-103">There are various types of XML applications:</span></span>  
  
- <span data-ttu-id="a4966-104">Některé aplikace přebírají zdrojové dokumenty XML a vytvářejí nové dokumenty XML, které mají jiný tvar než zdrojové dokumenty.</span><span class="sxs-lookup"><span data-stu-id="a4966-104">Some applications take source XML documents, and produce new XML documents that are in a different shape than the source documents.</span></span>  
  
- <span data-ttu-id="a4966-105">Některé aplikace přebírají zdrojové dokumenty XML a vytvářejí výsledné dokumenty ve zcela jiné podobě, například textové soubory HTML nebo CSV.</span><span class="sxs-lookup"><span data-stu-id="a4966-105">Some applications take source XML documents, and produce result documents in an entirely different form, such as HTML or CSV text files.</span></span>  
  
- <span data-ttu-id="a4966-106">Některé aplikace přebírají zdrojové dokumenty XML a vkládají záznamy do databáze.</span><span class="sxs-lookup"><span data-stu-id="a4966-106">Some applications take source XML documents, and insert records into a database.</span></span>  
  
- <span data-ttu-id="a4966-107">Některé aplikace přebírají data z jiného zdroje, například z databáze, a vytvářejí z ní dokumenty XML.</span><span class="sxs-lookup"><span data-stu-id="a4966-107">Some applications take data from another source, such as a database, and create XML documents from it.</span></span>  
  
 <span data-ttu-id="a4966-108">Nejedná se o všechny typy aplikací XML, ale jedná se o reprezentativní sadu typů funkcí, které musí programátor XML implementovat.</span><span class="sxs-lookup"><span data-stu-id="a4966-108">These are not all of the types of XML applications, but these are a representative set of the types of functionality that an XML programmer has to implement.</span></span>  
  
 <span data-ttu-id="a4966-109">U všech těchto typů aplikací existují dva kontrastní přístupy, které může vývojář použít:</span><span class="sxs-lookup"><span data-stu-id="a4966-109">With all of these types of applications, there are two contrasting approaches that a developer can take:</span></span>  
  
- <span data-ttu-id="a4966-110">Funkční konstrukce s použitím deklarativního přístupu.</span><span class="sxs-lookup"><span data-stu-id="a4966-110">Functional construction using a declarative approach.</span></span>  
  
- <span data-ttu-id="a4966-111">Úprava stromu XML v paměti pomocí procedurálního kódu.</span><span class="sxs-lookup"><span data-stu-id="a4966-111">In-memory XML tree modification using procedural code.</span></span>  
  
 <span data-ttu-id="a4966-112">LINQ na XML podporuje oba přístupy.</span><span class="sxs-lookup"><span data-stu-id="a4966-112">LINQ to XML supports both approaches.</span></span>  
  
 <span data-ttu-id="a4966-113">Při použití funkčního přístupu píšete transformace, které berou zdrojové dokumenty a generují zcela nové výsledné dokumenty s požadovaným tvarem.</span><span class="sxs-lookup"><span data-stu-id="a4966-113">When using the functional approach, you write transformations that take the source documents and generate completely new result documents with the desired shape.</span></span>  
  
 <span data-ttu-id="a4966-114">Při úpravách stromu XML na místě napíšete kód, který prochází a prochází uzly ve stromu XML v paměti, vkládání, odstranění a úpravy uzlů podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="a4966-114">When modifying an XML tree in place, you write code that traverses and navigates through nodes in an in-memory XML tree, inserting, deleting, and modifying nodes as necessary.</span></span>  
  
 <span data-ttu-id="a4966-115">LinQ můžete použít xml s oběma přístupy.</span><span class="sxs-lookup"><span data-stu-id="a4966-115">You can use LINQ to XML with either approach.</span></span> <span data-ttu-id="a4966-116">Používáte stejné třídy a v některých případech stejné metody.</span><span class="sxs-lookup"><span data-stu-id="a4966-116">You use the same classes, and in some cases the same methods.</span></span> <span data-ttu-id="a4966-117">Struktura a cíle obou přístupů jsou však velmi odlišné.</span><span class="sxs-lookup"><span data-stu-id="a4966-117">However, the structure and goals of the two approaches are very different.</span></span> <span data-ttu-id="a4966-118">Například v různých situacích jeden nebo druhý přístup bude mít často lepší výkon a používat více či méně paměti.</span><span class="sxs-lookup"><span data-stu-id="a4966-118">For example, in different situations, one or the other approach will often have better performance, and use more or less memory.</span></span> <span data-ttu-id="a4966-119">Kromě toho jeden nebo druhý přístup bude snazší psát a výnos více udržovatelný kód.</span><span class="sxs-lookup"><span data-stu-id="a4966-119">In addition, one or the other approach will be easier to write and yield more maintainable code.</span></span>  
  
 <span data-ttu-id="a4966-120">Chcete-li zobrazit dva přístupy v kontrastu, naleznete [v tématu Modifikace stromu XML v paměti vs funkční konstrukce (LINQ na XML) (C#)](./in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="a4966-120">To see the two approaches contrasted, see [In-Memory XML Tree Modification vs. Functional Construction (LINQ to XML) (C#)](./in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="a4966-121">Pro výuku psaní funkční transformace, naleznete v části [Čisté funkční transformace XML (C#)](./introduction-to-pure-functional-transformations.md).</span><span class="sxs-lookup"><span data-stu-id="a4966-121">For a tutorial on writing functional transformations, see [Pure Functional Transformations of XML (C#)](./introduction-to-pure-functional-transformations.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4966-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="a4966-122">See also</span></span>

- [<span data-ttu-id="a4966-123">Přehled programování LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="a4966-123">LINQ to XML Programming Overview (C#)</span></span>](./linq-to-xml-overview.md)
