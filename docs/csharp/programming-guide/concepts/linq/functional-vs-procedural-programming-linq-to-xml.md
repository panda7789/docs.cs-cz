---
title: Funkce vs. procedurální programování (LINQ to XML) (C#)
description: Pro zpracování XML LINQ to XML podporuje jak postupy, tak úpravy stromu XML v paměti a funkční konstrukci, která používá deklarativní přístup.
ms.date: 07/20/2015
ms.assetid: fc64e39c-a487-4882-9169-da4de97917d9
ms.openlocfilehash: e19f9311c56f4fe2c5e7e5f228aca6c03c6fe04d
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103656"
---
# <a name="functional-vs-procedural-programming-linq-to-xml-c"></a><span data-ttu-id="1c702-103">Funkce vs. procedurální programování (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="1c702-103">Functional vs. Procedural Programming (LINQ to XML) (C#)</span></span>
<span data-ttu-id="1c702-104">Existují různé typy aplikací XML:</span><span class="sxs-lookup"><span data-stu-id="1c702-104">There are various types of XML applications:</span></span>  
  
- <span data-ttu-id="1c702-105">Některé aplikace přijímají zdrojové dokumenty XML a vytvoří nové dokumenty XML, které se nacházejí v jiném tvaru než zdrojové dokumenty.</span><span class="sxs-lookup"><span data-stu-id="1c702-105">Some applications take source XML documents, and produce new XML documents that are in a different shape than the source documents.</span></span>  
  
- <span data-ttu-id="1c702-106">Některé aplikace přijímají zdrojové dokumenty XML a vytvářejí výsledné dokumenty v zcela jiném formuláři, například v HTML nebo v textových souborech CSV.</span><span class="sxs-lookup"><span data-stu-id="1c702-106">Some applications take source XML documents, and produce result documents in an entirely different form, such as HTML or CSV text files.</span></span>  
  
- <span data-ttu-id="1c702-107">Některé aplikace přijímají zdrojové dokumenty XML a vkládají záznamy do databáze.</span><span class="sxs-lookup"><span data-stu-id="1c702-107">Some applications take source XML documents, and insert records into a database.</span></span>  
  
- <span data-ttu-id="1c702-108">Některé aplikace přebírají data z jiného zdroje, jako je například databáze, a vytvářejí z nich dokumenty XML.</span><span class="sxs-lookup"><span data-stu-id="1c702-108">Some applications take data from another source, such as a database, and create XML documents from it.</span></span>  
  
 <span data-ttu-id="1c702-109">Nejedná se o všechny typy aplikací XML, ale jedná se o reprezentativní sadu typů funkcí, které musí programátor XML implementovat.</span><span class="sxs-lookup"><span data-stu-id="1c702-109">These are not all of the types of XML applications, but these are a representative set of the types of functionality that an XML programmer has to implement.</span></span>  
  
 <span data-ttu-id="1c702-110">U všech těchto typů aplikací existují dva způsoby kontrastu, které může vývojář provést:</span><span class="sxs-lookup"><span data-stu-id="1c702-110">With all of these types of applications, there are two contrasting approaches that a developer can take:</span></span>  
  
- <span data-ttu-id="1c702-111">Funkční konstrukce s použitím deklarativního přístupu.</span><span class="sxs-lookup"><span data-stu-id="1c702-111">Functional construction using a declarative approach.</span></span>  
  
- <span data-ttu-id="1c702-112">Úprava stromu XML v paměti pomocí procedurálního kódu.</span><span class="sxs-lookup"><span data-stu-id="1c702-112">In-memory XML tree modification using procedural code.</span></span>  
  
 <span data-ttu-id="1c702-113">LINQ to XML podporuje oba přístupy.</span><span class="sxs-lookup"><span data-stu-id="1c702-113">LINQ to XML supports both approaches.</span></span>  
  
 <span data-ttu-id="1c702-114">Při použití funkčního přístupu zapisujete transformace, které přijímají zdrojové dokumenty, a generují zcela nové dokumenty výsledků s požadovaným tvarem.</span><span class="sxs-lookup"><span data-stu-id="1c702-114">When using the functional approach, you write transformations that take the source documents and generate completely new result documents with the desired shape.</span></span>  
  
 <span data-ttu-id="1c702-115">Při úpravách stromu XML na místě napíšete kód, který přechází do uzlů ve stromu XML v paměti, vkládání, odstraňování a upravování uzlů podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="1c702-115">When modifying an XML tree in place, you write code that traverses and navigates through nodes in an in-memory XML tree, inserting, deleting, and modifying nodes as necessary.</span></span>  
  
 <span data-ttu-id="1c702-116">LINQ to XML můžete použít buď s přístupem.</span><span class="sxs-lookup"><span data-stu-id="1c702-116">You can use LINQ to XML with either approach.</span></span> <span data-ttu-id="1c702-117">Použijete stejné třídy, a v některých případech stejné metody.</span><span class="sxs-lookup"><span data-stu-id="1c702-117">You use the same classes, and in some cases the same methods.</span></span> <span data-ttu-id="1c702-118">Struktura a cíle těchto dvou přístupů se však velmi liší.</span><span class="sxs-lookup"><span data-stu-id="1c702-118">However, the structure and goals of the two approaches are very different.</span></span> <span data-ttu-id="1c702-119">Například v různých situacích bude mít jeden nebo druhý přístup často vyšší výkon a bude používat více nebo méně paměti.</span><span class="sxs-lookup"><span data-stu-id="1c702-119">For example, in different situations, one or the other approach will often have better performance, and use more or less memory.</span></span> <span data-ttu-id="1c702-120">Kromě toho bude jeden nebo druhý přístup snazší psát a vracet více udržovatelnější kód.</span><span class="sxs-lookup"><span data-stu-id="1c702-120">In addition, one or the other approach will be easier to write and yield more maintainable code.</span></span>  
  
 <span data-ttu-id="1c702-121">Chcete-li zobrazit tyto dva přístupy, přečtěte si část [Úprava stromu XML v paměti vs. konstrukce funkčnosti (LINQ to XML) (C#)](./in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="1c702-121">To see the two approaches contrasted, see [In-Memory XML Tree Modification vs. Functional Construction (LINQ to XML) (C#)](./in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="1c702-122">Kurz týkající se psaní funkčních transformací naleznete v tématu [čistě funkční transformace jazyka XML (C#)](./introduction-to-pure-functional-transformations.md).</span><span class="sxs-lookup"><span data-stu-id="1c702-122">For a tutorial on writing functional transformations, see [Pure Functional Transformations of XML (C#)](./introduction-to-pure-functional-transformations.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c702-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="1c702-123">See also</span></span>

- [<span data-ttu-id="1c702-124">Přehled programování LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="1c702-124">LINQ to XML Programming Overview (C#)</span></span>](./linq-to-xml-overview.md)
