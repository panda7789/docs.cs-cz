---
title: Funkční vs. procedurální programování (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: ea1015a5-d4c8-4d79-8e1e-ba17a40a4f39
ms.openlocfilehash: 0b525f13298e7402369b890516434cec47e01542
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84398432"
---
# <a name="functional-vs-procedural-programming-linq-to-xml-visual-basic"></a><span data-ttu-id="715d2-102">Funkce vs. procedurální programování (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="715d2-102">Functional vs. Procedural Programming (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="715d2-103">Existují různé typy aplikací XML:</span><span class="sxs-lookup"><span data-stu-id="715d2-103">There are various types of XML applications:</span></span>  
  
- <span data-ttu-id="715d2-104">Některé aplikace přijímají zdrojové dokumenty XML a vytvoří nové dokumenty XML, které se nacházejí v jiném tvaru než zdrojové dokumenty.</span><span class="sxs-lookup"><span data-stu-id="715d2-104">Some applications take source XML documents, and produce new XML documents that are in a different shape than the source documents.</span></span>  
  
- <span data-ttu-id="715d2-105">Některé aplikace přijímají zdrojové dokumenty XML a vytvářejí výsledné dokumenty v zcela jiném formuláři, například v HTML nebo v textových souborech CSV.</span><span class="sxs-lookup"><span data-stu-id="715d2-105">Some applications take source XML documents, and produce result documents in an entirely different form, such as HTML or CSV text files.</span></span>  
  
- <span data-ttu-id="715d2-106">Některé aplikace přijímají zdrojové dokumenty XML a vkládají záznamy do databáze.</span><span class="sxs-lookup"><span data-stu-id="715d2-106">Some applications take source XML documents, and insert records into a database.</span></span>  
  
- <span data-ttu-id="715d2-107">Některé aplikace přebírají data z jiného zdroje, jako je například databáze, a vytvářejí z nich dokumenty XML.</span><span class="sxs-lookup"><span data-stu-id="715d2-107">Some applications take data from another source, such as a database, and create XML documents from it.</span></span>  
  
 <span data-ttu-id="715d2-108">Nejedná se o všechny typy aplikací XML, ale jedná se o reprezentativní sadu typů funkcí, které musí programátor XML implementovat.</span><span class="sxs-lookup"><span data-stu-id="715d2-108">These are not all of the types of XML applications, but these are a representative set of the types of functionality that an XML programmer has to implement.</span></span>  
  
 <span data-ttu-id="715d2-109">U všech těchto typů aplikací existují dva způsoby kontrastu, které může vývojář provést:</span><span class="sxs-lookup"><span data-stu-id="715d2-109">With all of these types of applications, there are two contrasting approaches that a developer can take:</span></span>  
  
- <span data-ttu-id="715d2-110">Funkční konstrukce s použitím deklarativního přístupu.</span><span class="sxs-lookup"><span data-stu-id="715d2-110">Functional construction using a declarative approach.</span></span>  
  
- <span data-ttu-id="715d2-111">Úprava stromu XML v paměti pomocí procedurálního kódu.</span><span class="sxs-lookup"><span data-stu-id="715d2-111">In-memory XML tree modification using procedural code.</span></span>  
  
 <span data-ttu-id="715d2-112">LINQ to XML podporuje oba přístupy.</span><span class="sxs-lookup"><span data-stu-id="715d2-112">LINQ to XML supports both approaches.</span></span>  
  
 <span data-ttu-id="715d2-113">Při použití funkčního přístupu zapisujete transformace, které přijímají zdrojové dokumenty, a generují zcela nové dokumenty výsledků s požadovaným tvarem.</span><span class="sxs-lookup"><span data-stu-id="715d2-113">When using the functional approach, you write transformations that take the source documents and generate completely new result documents with the desired shape.</span></span>  
  
 <span data-ttu-id="715d2-114">Při úpravách stromu XML na místě napíšete kód, který přechází do uzlů ve stromu XML v paměti, vkládání, odstraňování a upravování uzlů podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="715d2-114">When modifying an XML tree in place, you write code that traverses and navigates through nodes in an in-memory XML tree, inserting, deleting, and modifying nodes as necessary.</span></span>  
  
 <span data-ttu-id="715d2-115">LINQ to XML můžete použít buď s přístupem.</span><span class="sxs-lookup"><span data-stu-id="715d2-115">You can use LINQ to XML with either approach.</span></span> <span data-ttu-id="715d2-116">Použijete stejné třídy, a v některých případech stejné metody.</span><span class="sxs-lookup"><span data-stu-id="715d2-116">You use the same classes, and in some cases the same methods.</span></span> <span data-ttu-id="715d2-117">Struktura a cíle těchto dvou přístupů se však velmi liší.</span><span class="sxs-lookup"><span data-stu-id="715d2-117">However, the structure and goals of the two approaches are very different.</span></span> <span data-ttu-id="715d2-118">Například v různých situacích bude mít jeden nebo druhý přístup často vyšší výkon a bude používat více nebo méně paměti.</span><span class="sxs-lookup"><span data-stu-id="715d2-118">For example, in different situations, one or the other approach will often have better performance, and use more or less memory.</span></span> <span data-ttu-id="715d2-119">Kromě toho bude jeden nebo druhý přístup snazší psát a vracet více udržovatelnější kód.</span><span class="sxs-lookup"><span data-stu-id="715d2-119">In addition, one or the other approach will be easier to write and yield more maintainable code.</span></span>  
  
 <span data-ttu-id="715d2-120">Chcete-li zobrazit tyto dva přístupy, přečtěte si část [Úprava stromu XML v paměti vs. konstrukce funkčnosti (LINQ to XML) (Visual Basic)](in-memory-xml-tree-modification-vs-functional-construction.md).</span><span class="sxs-lookup"><span data-stu-id="715d2-120">To see the two approaches contrasted, see [In-Memory XML Tree Modification vs. Functional Construction (LINQ to XML) (Visual Basic)](in-memory-xml-tree-modification-vs-functional-construction.md).</span></span>  
  
 <span data-ttu-id="715d2-121">Kurz týkající se psaní funkčních transformací najdete v tématu [čistě funkční transformace XML (Visual Basic)](pure-functional-transformations-of-xml.md).</span><span class="sxs-lookup"><span data-stu-id="715d2-121">For a tutorial on writing functional transformations, see [Pure Functional Transformations of XML (Visual Basic)](pure-functional-transformations-of-xml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="715d2-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="715d2-122">See also</span></span>

- [<span data-ttu-id="715d2-123">Přehled programování LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="715d2-123">LINQ to XML Programming Overview (Visual Basic)</span></span>](linq-to-xml-programming-overview.md)
