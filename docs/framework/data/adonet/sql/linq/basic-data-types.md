---
title: "Základní datové typy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eca2c472-9548-4800-bd31-5d8d9f11752b
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: ae0bb07688cf1e9573d02826f186811cd7340c90
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="basic-data-types"></a><span data-ttu-id="aff92-102">Základní datové typy</span><span class="sxs-lookup"><span data-stu-id="aff92-102">Basic Data Types</span></span>
<span data-ttu-id="aff92-103">Protože dotazy LINQ to SQL převede Transact-SQL před byly spouštěny na serveru Microsoft SQL Server.</span><span class="sxs-lookup"><span data-stu-id="aff92-103">Because LINQ to SQL queries translate to Transact-SQL before they are executed on the Microsoft SQL Server.</span></span> <span data-ttu-id="aff92-104">Technologie LINQ to SQL podporuje většinu stejné vestavěné funkce systému SQL Server podporuje pro základní datové typy.</span><span class="sxs-lookup"><span data-stu-id="aff92-104">LINQ to SQL supports much of the same built-in functionality that SQL Server does for basic data types.</span></span>  
  
## <a name="casting"></a><span data-ttu-id="aff92-105">Přetypování</span><span class="sxs-lookup"><span data-stu-id="aff92-105">Casting</span></span>  
 <span data-ttu-id="aff92-106">Implicitním nebo explicitním přetypování jsou povolené ze zdroje typu CLR na cíl, typ CLR, pokud neexistuje podobné platný převod v rámci systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="aff92-106">Implicit or explicit casts are enabled from a source CLR type to a target CLR type if there is a similar valid conversion within SQL Server.</span></span> <span data-ttu-id="aff92-107">Další informace o přetypování CLR najdete v tématu [CType – funkce](~/docs/visual-basic/language-reference/functions/ctype-function.md) ([!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) a [jako](~/docs/csharp/language-reference/keywords/as.md).</span><span class="sxs-lookup"><span data-stu-id="aff92-107">For more information about CLR casting, see [CType Function](~/docs/visual-basic/language-reference/functions/ctype-function.md) ([!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) and [as](~/docs/csharp/language-reference/keywords/as.md).</span></span> <span data-ttu-id="aff92-108">Po převodu přetypování změnit chování operace provedené na CLR výraz tak, aby odpovídaly chování jiné CLR výrazů, které přirozeně mapovat na typ cíle.</span><span class="sxs-lookup"><span data-stu-id="aff92-108">After conversion, casts change the behavior of operations performed on a CLR expression to match the behavior of other CLR expressions that naturally map to the destination type.</span></span> <span data-ttu-id="aff92-109">Přetypování jsou také nepřeložitelná v rámci mapování dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="aff92-109">Casts are also translatable in the context of inheritance mapping.</span></span> <span data-ttu-id="aff92-110">Objekty lze převést na konkrétnější podtypů entity tak, aby jejich dílčí specifických dat je přístupný.</span><span class="sxs-lookup"><span data-stu-id="aff92-110">Objects can be cast to more specific entity subtypes so that their subtype-specific data can be accessed.</span></span>  
  
## <a name="equality-operators"></a><span data-ttu-id="aff92-111">Operátory rovnosti</span><span class="sxs-lookup"><span data-stu-id="aff92-111">Equality Operators</span></span>  
 <span data-ttu-id="aff92-112">Technologie LINQ to SQL podporuje následující operátory rovnosti na základní datové typy uvnitř LINQ dotazy SQL:</span><span class="sxs-lookup"><span data-stu-id="aff92-112">LINQ to SQL supports the following equality operators on basic data types inside LINQ to SQL queries:</span></span>  
  
-   <span data-ttu-id="aff92-113">Stejné a operátor nerovnosti: operátory rovnosti a nerovnosti jsou podporovány pro číselné <xref:System.Boolean>, <xref:System.DateTime>, a <xref:System.TimeSpan> typy.</span><span class="sxs-lookup"><span data-stu-id="aff92-113">Equal and Inequality Operator: Equality and inequality operators are supported for numeric <xref:System.Boolean>, <xref:System.DateTime>, and <xref:System.TimeSpan> types.</span></span> <span data-ttu-id="aff92-114">Další informace o [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] operátory `=` a `<>`, najdete v části [operátory porovnání](~/docs/visual-basic/language-reference/operators/comparison-operators.md).</span><span class="sxs-lookup"><span data-stu-id="aff92-114">For more about [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] operators `=` and `<>`, see [Comparison Operators](~/docs/visual-basic/language-reference/operators/comparison-operators.md).</span></span> <span data-ttu-id="aff92-115">Další informace o porovnání operátory jazyka C# `==` a `!=`, najdete v části [== – operátor](~/docs/csharp/language-reference/operators/equality-comparison-operator.md) a [! = – operátor](~/docs/csharp/language-reference/operators/not-equal-operator.md), v tomto pořadí</span><span class="sxs-lookup"><span data-stu-id="aff92-115">For more information about C# comparison operators `==` and `!=`, see [== Operator](~/docs/csharp/language-reference/operators/equality-comparison-operator.md) and [!= Operator](~/docs/csharp/language-reference/operators/not-equal-operator.md), respectively</span></span>  
  
-   <span data-ttu-id="aff92-116">Is – operátor: `IS` operátor má podporované překladu, pokud se používá mapování dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="aff92-116">Is operator: The `IS` operator has a supported translation when inheritance mapping is being used.</span></span> <span data-ttu-id="aff92-117">Můžete použít místo přímo testování sloupce diskriminátoru určit, zda objekt je určitý typ entity a převádějí na kontrolu na sloupce diskriminátoru.</span><span class="sxs-lookup"><span data-stu-id="aff92-117">It can be used instead of directly testing the discriminator column to determine whether an object is of a specific entity type, and is translated to a check on the discriminator column.</span></span> <span data-ttu-id="aff92-118">Další informace o operátory jazyka Visual Basic a C# je najdete v tématu [je operátor](~/docs/visual-basic/language-reference/operators/is-operator.md) a [je](~/docs/csharp/language-reference/keywords/is.md).</span><span class="sxs-lookup"><span data-stu-id="aff92-118">For more information about the Visual Basic and C# Is operators, see [Is Operator](~/docs/visual-basic/language-reference/operators/is-operator.md) and [is](~/docs/csharp/language-reference/keywords/is.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aff92-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="aff92-119">See Also</span></span>  
 [<span data-ttu-id="aff92-120">Mapování typů SQL a CLR</span><span class="sxs-lookup"><span data-stu-id="aff92-120">SQL-CLR Type Mapping</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)  
 [<span data-ttu-id="aff92-121">Datové typy a funkce</span><span class="sxs-lookup"><span data-stu-id="aff92-121">Data Types and Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
