---
title: Výraz typu &lt;typ&gt; není dotazovatelné
ms.date: 07/20/2015
f1_keywords:
- bc36593
- vbc36593
helpviewer_keywords:
- BC36593
ms.assetid: 6f1f5860-bf97-4885-9ebb-bc87d028095c
ms.openlocfilehash: ce0831e0770e5733759c072b8d7c6f20b56f771b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54521488"
---
# <a name="expression-of-type-lttypegt-is-not-queryable"></a><span data-ttu-id="2ecaf-102">Výraz typu &lt;typ&gt; není dotazovatelné</span><span class="sxs-lookup"><span data-stu-id="2ecaf-102">Expression of type &lt;type&gt; is not queryable</span></span>
<span data-ttu-id="2ecaf-103">Výraz typu \<typ > není zadávat dotazy.</span><span class="sxs-lookup"><span data-stu-id="2ecaf-103">Expression of type \<type> is not queryable.</span></span> <span data-ttu-id="2ecaf-104">Ujistěte se, že nechybí sestavení odkazu nebo import oboru názvů pro zprostředkovatele LINQ.</span><span class="sxs-lookup"><span data-stu-id="2ecaf-104">Make sure you are not missing an assembly reference and/or namespace import for the LINQ provider.</span></span>  
  
 <span data-ttu-id="2ecaf-105">Dotazovatelné typy jsou definovány v <xref:System.Linq>, <xref:System.Data.Linq>, a <xref:System.Xml.Linq> obory názvů.</span><span class="sxs-lookup"><span data-stu-id="2ecaf-105">Queryable types are defined in the <xref:System.Linq>, <xref:System.Data.Linq>, and <xref:System.Xml.Linq> namespaces.</span></span> <span data-ttu-id="2ecaf-106">Je nutné importovat jeden nebo více z těchto oborů názvů k provádění dotazů LINQ.</span><span class="sxs-lookup"><span data-stu-id="2ecaf-106">You must import one or more of these namespaces to perform LINQ queries.</span></span>  
  
 <span data-ttu-id="2ecaf-107"><xref:System.Linq> Obor názvů umožňuje dotazu objekty, jako jsou kolekce a pole s využitím jazyka LINQ.</span><span class="sxs-lookup"><span data-stu-id="2ecaf-107">The <xref:System.Linq> namespace enables you to query objects such as collections and arrays by using LINQ.</span></span>  
  
 <span data-ttu-id="2ecaf-108"><xref:System.Data.Linq> Oborů názvů umožňuje dotazování datovými sadami ADO.NET a databáze systému SQL Server s využitím jazyka LINQ.</span><span class="sxs-lookup"><span data-stu-id="2ecaf-108">The <xref:System.Data.Linq> namespace enables you to query ADO.NET Datasets and SQL Server databases by using LINQ.</span></span>  
  
 <span data-ttu-id="2ecaf-109"><xref:System.Xml.Linq> Obor názvů umožňuje dotazu XML pomocí LINQ a pokud chcete používat funkce XML v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="2ecaf-109">The <xref:System.Xml.Linq> namespace enables you to query XML by using LINQ and to use XML features in Visual Basic.</span></span>  
  
 <span data-ttu-id="2ecaf-110">**ID chyby:** BC36593</span><span class="sxs-lookup"><span data-stu-id="2ecaf-110">**Error ID:** BC36593</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2ecaf-111">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="2ecaf-111">To correct this error</span></span>  
  
1.  <span data-ttu-id="2ecaf-112">Přidat `Import` příkaz <xref:System.Linq>, <xref:System.Data.Linq>, nebo <xref:System.Xml.Linq> oboru názvů do souboru kódu.</span><span class="sxs-lookup"><span data-stu-id="2ecaf-112">Add an `Import` statement for the <xref:System.Linq>, <xref:System.Data.Linq>, or <xref:System.Xml.Linq> namespace to your code file.</span></span> <span data-ttu-id="2ecaf-113">Můžete také importovat obory názvů pro váš projekt s použitím **odkazy** stránky Návrháře projektu (**Můj projekt**).</span><span class="sxs-lookup"><span data-stu-id="2ecaf-113">You can also import namespaces for your project by using the **References** page of the Project Designer (**My Project**).</span></span>  
  
2.  <span data-ttu-id="2ecaf-114">Ujistěte se, že typ, který jste našli jako dotazovatelný typ je zdroj dotazu.</span><span class="sxs-lookup"><span data-stu-id="2ecaf-114">Ensure that the type that you have identified as the source of your query is a queryable type.</span></span> <span data-ttu-id="2ecaf-115">To znamená typ, který implementuje <xref:System.Collections.Generic.IEnumerable%601> nebo <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="2ecaf-115">That is, a type that implements <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ecaf-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2ecaf-116">See also</span></span>
- <xref:System.Linq>
- <xref:System.Data.Linq>
- <xref:System.Xml.Linq>
- [<span data-ttu-id="2ecaf-117">Úvod do LINQ v JAZYKU Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2ecaf-117">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="2ecaf-118">LINQ</span><span class="sxs-lookup"><span data-stu-id="2ecaf-118">LINQ</span></span>](../../../visual-basic/programming-guide/language-features/linq/index.md)
- [<span data-ttu-id="2ecaf-119">XML</span><span class="sxs-lookup"><span data-stu-id="2ecaf-119">XML</span></span>](../../../visual-basic/programming-guide/language-features/xml/index.md)
- [<span data-ttu-id="2ecaf-120">Odkazy a příkaz Imports</span><span class="sxs-lookup"><span data-stu-id="2ecaf-120">References and the Imports Statement</span></span>](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)
- [<span data-ttu-id="2ecaf-121">Příkaz Imports (obor názvů a typ .NET)</span><span class="sxs-lookup"><span data-stu-id="2ecaf-121">Imports Statement (.NET Namespace and Type)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="2ecaf-122">Stránka Odkazy, Návrhář projektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2ecaf-122">References Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/references-page-project-designer-visual-basic)
