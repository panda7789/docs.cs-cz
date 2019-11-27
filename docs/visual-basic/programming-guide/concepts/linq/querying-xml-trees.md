---
title: Dotazování na stromy XML
ms.date: 07/20/2015
ms.assetid: 2e35c1ab-08c8-4378-9ca8-8ff344756eda
ms.openlocfilehash: c8103820a231ba0fb5e8e7c15b7a2b9e7c996e65
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346567"
---
# <a name="querying-xml-trees-visual-basic"></a><span data-ttu-id="cb676-102">Dotazování na stromy XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cb676-102">Querying XML Trees (Visual Basic)</span></span>
<span data-ttu-id="cb676-103">V této části najdete příklady dotazů [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cb676-103">This section provides examples of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] queries.</span></span>  
  
 <span data-ttu-id="cb676-104">Další informace o psaní [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazů naleznete v tématu [Začínáme with LINQ in Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md).</span><span class="sxs-lookup"><span data-stu-id="cb676-104">For more information about writing [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries, see [Getting Started with LINQ in Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md).</span></span>  
  
 <span data-ttu-id="cb676-105">Po vytvoření instance stromu XML je zápis dotazů nejúčinnějším způsobem, jak extrahovat data ze stromu.</span><span class="sxs-lookup"><span data-stu-id="cb676-105">After you have instantiated an XML tree, writing queries is the most effective way to extract data from the tree.</span></span> <span data-ttu-id="cb676-106">Dotazování v kombinaci se strukturou funkční konstrukce vám také umožňuje vygenerovat nový dokument XML, který má jiný tvar z původního dokumentu.</span><span class="sxs-lookup"><span data-stu-id="cb676-106">Also, querying combined with functional construction enables you to generate a new XML document that has a different shape from the original document.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cb676-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="cb676-107">In This Section</span></span>  
  
|<span data-ttu-id="cb676-108">Téma</span><span class="sxs-lookup"><span data-stu-id="cb676-108">Topic</span></span>|<span data-ttu-id="cb676-109">Popis</span><span class="sxs-lookup"><span data-stu-id="cb676-109">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="cb676-110">Základní dotazy (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cb676-110">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)|<span data-ttu-id="cb676-111">Poskytuje běžné příklady pro dotazování stromů XML.</span><span class="sxs-lookup"><span data-stu-id="cb676-111">Provides common examples of querying XML trees.</span></span>|  
|[<span data-ttu-id="cb676-112">Projekce a transformace (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cb676-112">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)|<span data-ttu-id="cb676-113">Poskytuje běžné příklady pro projekci a transformaci stromů XML.</span><span class="sxs-lookup"><span data-stu-id="cb676-113">Provides common examples of projecting from and transforming XML trees.</span></span>|  
|[<span data-ttu-id="cb676-114">Pokročilé techniky dotazů (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cb676-114">Advanced Query Techniques (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)|<span data-ttu-id="cb676-115">Poskytuje techniky dotazů, které jsou užitečné v pokročilejších scénářích.</span><span class="sxs-lookup"><span data-stu-id="cb676-115">Provides query techniques that are useful in more advanced scenarios.</span></span>|  
|[<span data-ttu-id="cb676-116">LINQ to XML pro uživatele XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cb676-116">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)|<span data-ttu-id="cb676-117">Prezentuje počet výrazů XPath a jejich ekvivalenty [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cb676-117">Presents a number of XPath expressions and their [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] equivalents.</span></span>|  
|[<span data-ttu-id="cb676-118">Čistě funkční transformace jazyka XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cb676-118">Pure Functional Transformations of XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md)|<span data-ttu-id="cb676-119">Prezentuje malý kurz zápisu dotazů ve stylu funkčního programování.</span><span class="sxs-lookup"><span data-stu-id="cb676-119">Presents a small tutorial on writing queries in the style of functional programming.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cb676-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cb676-120">See also</span></span>

- [<span data-ttu-id="cb676-121">Průvodce programováním (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cb676-121">Programming Guide (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)
- [<span data-ttu-id="cb676-122">Začínáme pomocí LINQ v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cb676-122">Getting Started with LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
