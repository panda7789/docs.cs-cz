---
title: "Výraz typu &lt;typ&gt; není dotazovatelné"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc36593
- vbc36593
helpviewer_keywords: BC36593
ms.assetid: 6f1f5860-bf97-4885-9ebb-bc87d028095c
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3f2b98bf48f0b3965929f9211c2944ff97754f23
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="expression-of-type-lttypegt-is-not-queryable"></a><span data-ttu-id="9da54-102">Výraz typu &lt;typ&gt; není dotazovatelné</span><span class="sxs-lookup"><span data-stu-id="9da54-102">Expression of type &lt;type&gt; is not queryable</span></span>
<span data-ttu-id="9da54-103">Výraz typu \<typ > není dotazovatelnosti.</span><span class="sxs-lookup"><span data-stu-id="9da54-103">Expression of type \<type> is not queryable.</span></span> <span data-ttu-id="9da54-104">Ujistěte se, že nejsou pro zprostředkovatele LINQ chybí sestavení odkaz nebo obor názvů importu.</span><span class="sxs-lookup"><span data-stu-id="9da54-104">Make sure you are not missing an assembly reference and/or namespace import for the LINQ provider.</span></span>  
  
 <span data-ttu-id="9da54-105">Dotazovatelný typy jsou definované v <xref:System.Linq>, <xref:System.Data.Linq>, a <xref:System.Xml.Linq> obory názvů.</span><span class="sxs-lookup"><span data-stu-id="9da54-105">Queryable types are defined in the <xref:System.Linq>, <xref:System.Data.Linq>, and <xref:System.Xml.Linq> namespaces.</span></span> <span data-ttu-id="9da54-106">Je nutné naimportovat minimálně jeden z těchto oborů názvů provádět dotazy LINQ.</span><span class="sxs-lookup"><span data-stu-id="9da54-106">You must import one or more of these namespaces to perform LINQ queries.</span></span>  
  
 <span data-ttu-id="9da54-107"><xref:System.Linq> Obor názvů umožňuje objekty dotazu, jako jsou kolekce a pole pomocí LINQ.</span><span class="sxs-lookup"><span data-stu-id="9da54-107">The <xref:System.Linq> namespace enables you to query objects such as collections and arrays by using LINQ.</span></span>  
  
 <span data-ttu-id="9da54-108"><xref:System.Data.Linq> Obor názvů umožňuje ADO.NET datové sady a databáze systému SQL Server pomocí LINQ dotazů.</span><span class="sxs-lookup"><span data-stu-id="9da54-108">The <xref:System.Data.Linq> namespace enables you to query ADO.NET Datasets and SQL Server databases by using LINQ.</span></span>  
  
 <span data-ttu-id="9da54-109"><xref:System.Xml.Linq> Obor názvů umožňuje dotazu XML pomocí LINQ a chcete používat funkce XML v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="9da54-109">The <xref:System.Xml.Linq> namespace enables you to query XML by using LINQ and to use XML features in Visual Basic.</span></span>  
  
 <span data-ttu-id="9da54-110">**ID chyby:** BC36593</span><span class="sxs-lookup"><span data-stu-id="9da54-110">**Error ID:** BC36593</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9da54-111">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="9da54-111">To correct this error</span></span>  
  
1.  <span data-ttu-id="9da54-112">Přidat `Import` údajů <xref:System.Linq>, <xref:System.Data.Linq>, nebo <xref:System.Xml.Linq> oboru názvů do souboru kódu.</span><span class="sxs-lookup"><span data-stu-id="9da54-112">Add an `Import` statement for the <xref:System.Linq>, <xref:System.Data.Linq>, or <xref:System.Xml.Linq> namespace to your code file.</span></span> <span data-ttu-id="9da54-113">Můžete také importovat obory názvů pro váš projekt pomocí **odkazy** stránky v Návrháři projektu (**Můj projekt**).</span><span class="sxs-lookup"><span data-stu-id="9da54-113">You can also import namespaces for your project by using the **References** page of the Project Designer (**My Project**).</span></span>  
  
2.  <span data-ttu-id="9da54-114">Zajistěte, aby typ, který jste našli jako zdroj dotazu je typu dotazovatelnosti.</span><span class="sxs-lookup"><span data-stu-id="9da54-114">Ensure that the type that you have identified as the source of your query is a queryable type.</span></span> <span data-ttu-id="9da54-115">To znamená, typ, který implementuje <xref:System.Collections.Generic.IEnumerable%601> nebo <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="9da54-115">That is, a type that implements <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9da54-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="9da54-116">See Also</span></span>  
 <xref:System.Linq>  
 <xref:System.Data.Linq>  
 <xref:System.Xml.Linq>  
 [<span data-ttu-id="9da54-117">Úvod do LINQ v jazyku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9da54-117">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="9da54-118">LINQ</span><span class="sxs-lookup"><span data-stu-id="9da54-118">LINQ</span></span>](../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [<span data-ttu-id="9da54-119">XML</span><span class="sxs-lookup"><span data-stu-id="9da54-119">XML</span></span>](../../../visual-basic/programming-guide/language-features/xml/index.md)  
 [<span data-ttu-id="9da54-120">Odkazy a příkaz Imports</span><span class="sxs-lookup"><span data-stu-id="9da54-120">References and the Imports Statement</span></span>](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)  
 [<span data-ttu-id="9da54-121">Imports – příkaz (Namespace .NET a typ)</span><span class="sxs-lookup"><span data-stu-id="9da54-121">Imports Statement (.NET Namespace and Type)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [<span data-ttu-id="9da54-122">Stránka odkazy, Návrhář projektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9da54-122">References Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/references-page-project-designer-visual-basic)
