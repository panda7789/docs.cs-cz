---
title: Na výrazy typu <type> nelze zadávat dotazy.
ms.date: 07/20/2015
f1_keywords:
- bc36593
- vbc36593
helpviewer_keywords:
- BC36593
ms.assetid: 6f1f5860-bf97-4885-9ebb-bc87d028095c
ms.openlocfilehash: e61b4dac109f714b5cf25226d1029237ca77032d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409475"
---
# <a name="expression-of-type-type-is-not-queryable"></a><span data-ttu-id="3163b-102">Na výrazy typu \<type> nelze zadávat dotazy.</span><span class="sxs-lookup"><span data-stu-id="3163b-102">Expression of type \<type> is not queryable</span></span>
<span data-ttu-id="3163b-103">Výraz typu není \<type> Queryable.</span><span class="sxs-lookup"><span data-stu-id="3163b-103">Expression of type \<type> is not queryable.</span></span> <span data-ttu-id="3163b-104">Ujistěte se, že nechybí odkaz na sestavení nebo import oboru názvů pro poskytovatele LINQ.</span><span class="sxs-lookup"><span data-stu-id="3163b-104">Make sure you are not missing an assembly reference and/or namespace import for the LINQ provider.</span></span>  
  
 <span data-ttu-id="3163b-105">Queryable typy jsou definovány v <xref:System.Linq> <xref:System.Data.Linq> <xref:System.Xml.Linq> oborech názvů, a.</span><span class="sxs-lookup"><span data-stu-id="3163b-105">Queryable types are defined in the <xref:System.Linq>, <xref:System.Data.Linq>, and <xref:System.Xml.Linq> namespaces.</span></span> <span data-ttu-id="3163b-106">Pro provádění dotazů LINQ musíte importovat jeden nebo více těchto oborů názvů.</span><span class="sxs-lookup"><span data-stu-id="3163b-106">You must import one or more of these namespaces to perform LINQ queries.</span></span>  
  
 <span data-ttu-id="3163b-107"><xref:System.Linq>Obor názvů umožňuje dotazování objektů, jako jsou kolekce a pole pomocí LINQ.</span><span class="sxs-lookup"><span data-stu-id="3163b-107">The <xref:System.Linq> namespace enables you to query objects such as collections and arrays by using LINQ.</span></span>  
  
 <span data-ttu-id="3163b-108"><xref:System.Data.Linq>Obor názvů umožňuje dotazování ADO.NET datových sad a SQL Server databází pomocí LINQ.</span><span class="sxs-lookup"><span data-stu-id="3163b-108">The <xref:System.Data.Linq> namespace enables you to query ADO.NET Datasets and SQL Server databases by using LINQ.</span></span>  
  
 <span data-ttu-id="3163b-109"><xref:System.Xml.Linq>Obor názvů vám umožňuje dotazovat se na XML pomocí LINQ a používat funkce XML v Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="3163b-109">The <xref:System.Xml.Linq> namespace enables you to query XML by using LINQ and to use XML features in Visual Basic.</span></span>  
  
 <span data-ttu-id="3163b-110">**ID chyby:** BC36593</span><span class="sxs-lookup"><span data-stu-id="3163b-110">**Error ID:** BC36593</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="3163b-111">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="3163b-111">To correct this error</span></span>  
  
1. <span data-ttu-id="3163b-112">Přidejte `Import` příkaz pro <xref:System.Linq> <xref:System.Data.Linq> <xref:System.Xml.Linq> obor názvů, nebo do souboru kódu.</span><span class="sxs-lookup"><span data-stu-id="3163b-112">Add an `Import` statement for the <xref:System.Linq>, <xref:System.Data.Linq>, or <xref:System.Xml.Linq> namespace to your code file.</span></span> <span data-ttu-id="3163b-113">Obory názvů pro svůj projekt můžete také importovat pomocí stránky **odkazy** Návrháře projektu (**můj projekt**).</span><span class="sxs-lookup"><span data-stu-id="3163b-113">You can also import namespaces for your project by using the **References** page of the Project Designer (**My Project**).</span></span>  
  
2. <span data-ttu-id="3163b-114">Ujistěte se, že typ, který jste identifikovali jako zdroj dotazu, je Queryable typ.</span><span class="sxs-lookup"><span data-stu-id="3163b-114">Ensure that the type that you have identified as the source of your query is a queryable type.</span></span> <span data-ttu-id="3163b-115">To znamená, že typ, který implementuje <xref:System.Collections.Generic.IEnumerable%601> nebo <xref:System.Linq.IQueryable%601> .</span><span class="sxs-lookup"><span data-stu-id="3163b-115">That is, a type that implements <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3163b-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="3163b-116">See also</span></span>

- <xref:System.Linq>
- <xref:System.Data.Linq>
- <xref:System.Xml.Linq>
- [<span data-ttu-id="3163b-117">Představení technologie LINQ v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3163b-117">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="3163b-118">LINQ</span><span class="sxs-lookup"><span data-stu-id="3163b-118">LINQ</span></span>](../../programming-guide/language-features/linq/index.md)
- [<span data-ttu-id="3163b-119">XML</span><span class="sxs-lookup"><span data-stu-id="3163b-119">XML</span></span>](../../programming-guide/language-features/xml/index.md)
- [<span data-ttu-id="3163b-120">Odkazy a příkaz Imports</span><span class="sxs-lookup"><span data-stu-id="3163b-120">References and the Imports Statement</span></span>](../../programming-guide/program-structure/references-and-the-imports-statement.md)
- [<span data-ttu-id="3163b-121">Imports – příkaz (obor názvů a typ rozhraní .NET)</span><span class="sxs-lookup"><span data-stu-id="3163b-121">Imports Statement (.NET Namespace and Type)</span></span>](../statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="3163b-122">Stránka Odkazy, návrhář projektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3163b-122">References Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/references-page-project-designer-visual-basic)
