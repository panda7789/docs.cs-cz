---
title: Na výrazy typu <type> nelze zadávat dotazy.
ms.date: 07/20/2015
f1_keywords:
- bc36593
- vbc36593
helpviewer_keywords:
- BC36593
ms.assetid: 6f1f5860-bf97-4885-9ebb-bc87d028095c
ms.openlocfilehash: 121c0a95a3a6bb695d9c73347c733cba215a0de4
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59304152"
---
# <a name="expression-of-type-type-is-not-queryable"></a><span data-ttu-id="6b9ae-102">Výraz typu \<typ > není dotazovatelné</span><span class="sxs-lookup"><span data-stu-id="6b9ae-102">Expression of type \<type> is not queryable</span></span>
<span data-ttu-id="6b9ae-103">Výraz typu \<typ > není zadávat dotazy.</span><span class="sxs-lookup"><span data-stu-id="6b9ae-103">Expression of type \<type> is not queryable.</span></span> <span data-ttu-id="6b9ae-104">Ujistěte se, že nechybí sestavení odkazu nebo import oboru názvů pro zprostředkovatele LINQ.</span><span class="sxs-lookup"><span data-stu-id="6b9ae-104">Make sure you are not missing an assembly reference and/or namespace import for the LINQ provider.</span></span>  
  
 <span data-ttu-id="6b9ae-105">Dotazovatelné typy jsou definovány v <xref:System.Linq>, <xref:System.Data.Linq>, a <xref:System.Xml.Linq> obory názvů.</span><span class="sxs-lookup"><span data-stu-id="6b9ae-105">Queryable types are defined in the <xref:System.Linq>, <xref:System.Data.Linq>, and <xref:System.Xml.Linq> namespaces.</span></span> <span data-ttu-id="6b9ae-106">Je nutné importovat jeden nebo více z těchto oborů názvů k provádění dotazů LINQ.</span><span class="sxs-lookup"><span data-stu-id="6b9ae-106">You must import one or more of these namespaces to perform LINQ queries.</span></span>  
  
 <span data-ttu-id="6b9ae-107"><xref:System.Linq> Obor názvů umožňuje dotazu objekty, jako jsou kolekce a pole s využitím jazyka LINQ.</span><span class="sxs-lookup"><span data-stu-id="6b9ae-107">The <xref:System.Linq> namespace enables you to query objects such as collections and arrays by using LINQ.</span></span>  
  
 <span data-ttu-id="6b9ae-108"><xref:System.Data.Linq> Oborů názvů umožňuje dotazování datovými sadami ADO.NET a databáze systému SQL Server s využitím jazyka LINQ.</span><span class="sxs-lookup"><span data-stu-id="6b9ae-108">The <xref:System.Data.Linq> namespace enables you to query ADO.NET Datasets and SQL Server databases by using LINQ.</span></span>  
  
 <span data-ttu-id="6b9ae-109"><xref:System.Xml.Linq> Obor názvů umožňuje dotazu XML pomocí LINQ a pokud chcete používat funkce XML v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="6b9ae-109">The <xref:System.Xml.Linq> namespace enables you to query XML by using LINQ and to use XML features in Visual Basic.</span></span>  
  
 <span data-ttu-id="6b9ae-110">**ID chyby:** BC36593</span><span class="sxs-lookup"><span data-stu-id="6b9ae-110">**Error ID:** BC36593</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6b9ae-111">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="6b9ae-111">To correct this error</span></span>  
  
1. <span data-ttu-id="6b9ae-112">Přidat `Import` příkaz <xref:System.Linq>, <xref:System.Data.Linq>, nebo <xref:System.Xml.Linq> oboru názvů do souboru kódu.</span><span class="sxs-lookup"><span data-stu-id="6b9ae-112">Add an `Import` statement for the <xref:System.Linq>, <xref:System.Data.Linq>, or <xref:System.Xml.Linq> namespace to your code file.</span></span> <span data-ttu-id="6b9ae-113">Můžete také importovat obory názvů pro váš projekt s použitím **odkazy** stránky Návrháře projektu (**Můj projekt**).</span><span class="sxs-lookup"><span data-stu-id="6b9ae-113">You can also import namespaces for your project by using the **References** page of the Project Designer (**My Project**).</span></span>  
  
2. <span data-ttu-id="6b9ae-114">Ujistěte se, že typ, který jste našli jako dotazovatelný typ je zdroj dotazu.</span><span class="sxs-lookup"><span data-stu-id="6b9ae-114">Ensure that the type that you have identified as the source of your query is a queryable type.</span></span> <span data-ttu-id="6b9ae-115">To znamená typ, který implementuje <xref:System.Collections.Generic.IEnumerable%601> nebo <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="6b9ae-115">That is, a type that implements <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b9ae-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6b9ae-116">See also</span></span>

- <xref:System.Linq>
- <xref:System.Data.Linq>
- <xref:System.Xml.Linq>
- [<span data-ttu-id="6b9ae-117">Představení technologie LINQ v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6b9ae-117">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="6b9ae-118">LINQ</span><span class="sxs-lookup"><span data-stu-id="6b9ae-118">LINQ</span></span>](../../../visual-basic/programming-guide/language-features/linq/index.md)
- [<span data-ttu-id="6b9ae-119">XML</span><span class="sxs-lookup"><span data-stu-id="6b9ae-119">XML</span></span>](../../../visual-basic/programming-guide/language-features/xml/index.md)
- [<span data-ttu-id="6b9ae-120">Odkazy a příkaz Imports</span><span class="sxs-lookup"><span data-stu-id="6b9ae-120">References and the Imports Statement</span></span>](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)
- [<span data-ttu-id="6b9ae-121">Imports – příkaz (obor názvů a typ rozhraní .NET)</span><span class="sxs-lookup"><span data-stu-id="6b9ae-121">Imports Statement (.NET Namespace and Type)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="6b9ae-122">Stránka Odkazy, návrhář projektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6b9ae-122">References Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/references-page-project-designer-visual-basic)
