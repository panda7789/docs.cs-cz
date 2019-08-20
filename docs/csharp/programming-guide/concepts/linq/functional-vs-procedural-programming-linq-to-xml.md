---
title: Funkční vs. Procedurální programování (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: fc64e39c-a487-4882-9169-da4de97917d9
ms.openlocfilehash: e87114d2edcda4b2df14eb2d84f62ebe9638b5eb
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69594258"
---
# <a name="functional-vs-procedural-programming-linq-to-xml-c"></a><span data-ttu-id="12eef-102">Funkční vs. Procedurální programování (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="12eef-102">Functional vs. Procedural Programming (LINQ to XML) (C#)</span></span>
<span data-ttu-id="12eef-103">Existují různé typy aplikací XML:</span><span class="sxs-lookup"><span data-stu-id="12eef-103">There are various types of XML applications:</span></span>  
  
- <span data-ttu-id="12eef-104">Některé aplikace přijímají zdrojové dokumenty XML a vytvoří nové dokumenty XML, které se nacházejí v jiném tvaru než zdrojové dokumenty.</span><span class="sxs-lookup"><span data-stu-id="12eef-104">Some applications take source XML documents, and produce new XML documents that are in a different shape than the source documents.</span></span>  
  
- <span data-ttu-id="12eef-105">Některé aplikace přijímají zdrojové dokumenty XML a vytvářejí výsledné dokumenty v zcela jiném formuláři, například v HTML nebo v textových souborech CSV.</span><span class="sxs-lookup"><span data-stu-id="12eef-105">Some applications take source XML documents, and produce result documents in an entirely different form, such as HTML or CSV text files.</span></span>  
  
- <span data-ttu-id="12eef-106">Některé aplikace přijímají zdrojové dokumenty XML a vkládají záznamy do databáze.</span><span class="sxs-lookup"><span data-stu-id="12eef-106">Some applications take source XML documents, and insert records into a database.</span></span>  
  
- <span data-ttu-id="12eef-107">Některé aplikace přebírají data z jiného zdroje, jako je například databáze, a vytvářejí z nich dokumenty XML.</span><span class="sxs-lookup"><span data-stu-id="12eef-107">Some applications take data from another source, such as a database, and create XML documents from it.</span></span>  
  
 <span data-ttu-id="12eef-108">Nejedná se o všechny typy aplikací XML, ale jedná se o reprezentativní sadu typů funkcí, které musí programátor XML implementovat.</span><span class="sxs-lookup"><span data-stu-id="12eef-108">These are not all of the types of XML applications, but these are a representative set of the types of functionality that an XML programmer has to implement.</span></span>  
  
 <span data-ttu-id="12eef-109">U všech těchto typů aplikací existují dva způsoby kontrastu, které může vývojář provést:</span><span class="sxs-lookup"><span data-stu-id="12eef-109">With all of these types of applications, there are two contrasting approaches that a developer can take:</span></span>  
  
- <span data-ttu-id="12eef-110">Funkční konstrukce s použitím deklarativního přístupu.</span><span class="sxs-lookup"><span data-stu-id="12eef-110">Functional construction using a declarative approach.</span></span>  
  
- <span data-ttu-id="12eef-111">Úprava stromu XML v paměti pomocí procedurálního kódu.</span><span class="sxs-lookup"><span data-stu-id="12eef-111">In-memory XML tree modification using procedural code.</span></span>  
  
 <span data-ttu-id="12eef-112">LINQ to XML podporuje oba přístupy.</span><span class="sxs-lookup"><span data-stu-id="12eef-112">LINQ to XML supports both approaches.</span></span>  
  
 <span data-ttu-id="12eef-113">Při použití funkčního přístupu zapisujete transformace, které přijímají zdrojové dokumenty, a generují zcela nové dokumenty výsledků s požadovaným tvarem.</span><span class="sxs-lookup"><span data-stu-id="12eef-113">When using the functional approach, you write transformations that take the source documents and generate completely new result documents with the desired shape.</span></span>  
  
 <span data-ttu-id="12eef-114">Při úpravách stromu XML na místě napíšete kód, který přechází do uzlů ve stromu XML v paměti, vkládání, odstraňování a upravování uzlů podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="12eef-114">When modifying an XML tree in place, you write code that traverses and navigates through nodes in an in-memory XML tree, inserting, deleting, and modifying nodes as necessary.</span></span>  
  
 <span data-ttu-id="12eef-115">LINQ to XML můžete použít buď s přístupem.</span><span class="sxs-lookup"><span data-stu-id="12eef-115">You can use LINQ to XML with either approach.</span></span> <span data-ttu-id="12eef-116">Použijete stejné třídy, a v některých případech stejné metody.</span><span class="sxs-lookup"><span data-stu-id="12eef-116">You use the same classes, and in some cases the same methods.</span></span> <span data-ttu-id="12eef-117">Struktura a cíle těchto dvou přístupů se však velmi liší.</span><span class="sxs-lookup"><span data-stu-id="12eef-117">However, the structure and goals of the two approaches are very different.</span></span> <span data-ttu-id="12eef-118">Například v různých situacích bude mít jeden nebo druhý přístup často vyšší výkon a bude používat více nebo méně paměti.</span><span class="sxs-lookup"><span data-stu-id="12eef-118">For example, in different situations, one or the other approach will often have better performance, and use more or less memory.</span></span> <span data-ttu-id="12eef-119">Kromě toho bude jeden nebo druhý přístup snazší psát a vracet více udržovatelnější kód.</span><span class="sxs-lookup"><span data-stu-id="12eef-119">In addition, one or the other approach will be easier to write and yield more maintainable code.</span></span>  
  
 <span data-ttu-id="12eef-120">Chcete-li zobrazit kontrast dvou přístupů, přečtěte si část [úprava stromu XML v paměti vs. Funkční konstrukce (LINQ to XML) (C#)](./in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="12eef-120">To see the two approaches contrasted, see [In-Memory XML Tree Modification vs. Functional Construction (LINQ to XML) (C#)](./in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="12eef-121">Kurz týkající se psaní funkčních transformací naleznete v tématu [čistě funkční transformace jazyka XMLC#()](./introduction-to-pure-functional-transformations.md).</span><span class="sxs-lookup"><span data-stu-id="12eef-121">For a tutorial on writing functional transformations, see [Pure Functional Transformations of XML (C#)](./introduction-to-pure-functional-transformations.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12eef-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="12eef-122">See also</span></span>

- [<span data-ttu-id="12eef-123">Přehled programování LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="12eef-123">LINQ to XML Programming Overview (C#)</span></span>](./linq-to-xml-overview.md)
