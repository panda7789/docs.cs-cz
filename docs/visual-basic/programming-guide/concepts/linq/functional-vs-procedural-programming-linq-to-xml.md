---
title: Funkce vs. procedurální programování (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: ea1015a5-d4c8-4d79-8e1e-ba17a40a4f39
ms.openlocfilehash: 3d1e3cf01b30454d29836f176afcd39cb2b55b73
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353414"
---
# <a name="functional-vs-procedural-programming-linq-to-xml-visual-basic"></a><span data-ttu-id="01d95-102">Funkce vs. procedurální programování (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="01d95-102">Functional vs. Procedural Programming (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="01d95-103">Existují různé typy aplikací XML:</span><span class="sxs-lookup"><span data-stu-id="01d95-103">There are various types of XML applications:</span></span>  
  
- <span data-ttu-id="01d95-104">Některé aplikace přijímají zdrojové dokumenty XML a vytvoří nové dokumenty XML, které se nacházejí v jiném tvaru než zdrojové dokumenty.</span><span class="sxs-lookup"><span data-stu-id="01d95-104">Some applications take source XML documents, and produce new XML documents that are in a different shape than the source documents.</span></span>  
  
- <span data-ttu-id="01d95-105">Některé aplikace přijímají zdrojové dokumenty XML a vytvářejí výsledné dokumenty v zcela jiném formuláři, například v HTML nebo v textových souborech CSV.</span><span class="sxs-lookup"><span data-stu-id="01d95-105">Some applications take source XML documents, and produce result documents in an entirely different form, such as HTML or CSV text files.</span></span>  
  
- <span data-ttu-id="01d95-106">Některé aplikace přijímají zdrojové dokumenty XML a vkládají záznamy do databáze.</span><span class="sxs-lookup"><span data-stu-id="01d95-106">Some applications take source XML documents, and insert records into a database.</span></span>  
  
- <span data-ttu-id="01d95-107">Některé aplikace přebírají data z jiného zdroje, jako je například databáze, a vytvářejí z nich dokumenty XML.</span><span class="sxs-lookup"><span data-stu-id="01d95-107">Some applications take data from another source, such as a database, and create XML documents from it.</span></span>  
  
 <span data-ttu-id="01d95-108">Nejedná se o všechny typy aplikací XML, ale jedná se o reprezentativní sadu typů funkcí, které musí programátor XML implementovat.</span><span class="sxs-lookup"><span data-stu-id="01d95-108">These are not all of the types of XML applications, but these are a representative set of the types of functionality that an XML programmer has to implement.</span></span>  
  
 <span data-ttu-id="01d95-109">U všech těchto typů aplikací existují dva způsoby kontrastu, které může vývojář provést:</span><span class="sxs-lookup"><span data-stu-id="01d95-109">With all of these types of applications, there are two contrasting approaches that a developer can take:</span></span>  
  
- <span data-ttu-id="01d95-110">Funkční konstrukce s použitím deklarativního přístupu.</span><span class="sxs-lookup"><span data-stu-id="01d95-110">Functional construction using a declarative approach.</span></span>  
  
- <span data-ttu-id="01d95-111">Úprava stromu XML v paměti pomocí procedurálního kódu.</span><span class="sxs-lookup"><span data-stu-id="01d95-111">In-memory XML tree modification using procedural code.</span></span>  
  
 <span data-ttu-id="01d95-112">LINQ to XML podporuje oba přístupy.</span><span class="sxs-lookup"><span data-stu-id="01d95-112">LINQ to XML supports both approaches.</span></span>  
  
 <span data-ttu-id="01d95-113">Při použití funkčního přístupu zapisujete transformace, které přijímají zdrojové dokumenty, a generují zcela nové dokumenty výsledků s požadovaným tvarem.</span><span class="sxs-lookup"><span data-stu-id="01d95-113">When using the functional approach, you write transformations that take the source documents and generate completely new result documents with the desired shape.</span></span>  
  
 <span data-ttu-id="01d95-114">Při úpravách stromu XML na místě napíšete kód, který přechází do uzlů ve stromu XML v paměti, vkládání, odstraňování a upravování uzlů podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="01d95-114">When modifying an XML tree in place, you write code that traverses and navigates through nodes in an in-memory XML tree, inserting, deleting, and modifying nodes as necessary.</span></span>  
  
 <span data-ttu-id="01d95-115">LINQ to XML můžete použít buď s přístupem.</span><span class="sxs-lookup"><span data-stu-id="01d95-115">You can use LINQ to XML with either approach.</span></span> <span data-ttu-id="01d95-116">Použijete stejné třídy, a v některých případech stejné metody.</span><span class="sxs-lookup"><span data-stu-id="01d95-116">You use the same classes, and in some cases the same methods.</span></span> <span data-ttu-id="01d95-117">Struktura a cíle těchto dvou přístupů se však velmi liší.</span><span class="sxs-lookup"><span data-stu-id="01d95-117">However, the structure and goals of the two approaches are very different.</span></span> <span data-ttu-id="01d95-118">Například v různých situacích bude mít jeden nebo druhý přístup často vyšší výkon a bude používat více nebo méně paměti.</span><span class="sxs-lookup"><span data-stu-id="01d95-118">For example, in different situations, one or the other approach will often have better performance, and use more or less memory.</span></span> <span data-ttu-id="01d95-119">Kromě toho bude jeden nebo druhý přístup snazší psát a vracet více udržovatelnější kód.</span><span class="sxs-lookup"><span data-stu-id="01d95-119">In addition, one or the other approach will be easier to write and yield more maintainable code.</span></span>  
  
 <span data-ttu-id="01d95-120">Chcete-li zobrazit tyto dva přístupy, přečtěte si část [Úprava stromu XML v paměti vs. konstrukce funkčnosti (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/in-memory-xml-tree-modification-vs-functional-construction.md).</span><span class="sxs-lookup"><span data-stu-id="01d95-120">To see the two approaches contrasted, see [In-Memory XML Tree Modification vs. Functional Construction (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/in-memory-xml-tree-modification-vs-functional-construction.md).</span></span>  
  
 <span data-ttu-id="01d95-121">Kurz týkající se psaní funkčních transformací najdete v tématu [čistě funkční transformace XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md).</span><span class="sxs-lookup"><span data-stu-id="01d95-121">For a tutorial on writing functional transformations, see [Pure Functional Transformations of XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01d95-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="01d95-122">See also</span></span>

- [<span data-ttu-id="01d95-123">Přehled programování LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="01d95-123">LINQ to XML Programming Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
