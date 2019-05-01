---
title: Let – klauzule (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryLet
helpviewer_keywords:
- queries [Visual Basic], Let
- Let clause [Visual Basic]
- Let statement [Visual Basic]
ms.assetid: 981aa516-16eb-4c53-b1f1-5aa3e82f316e
ms.openlocfilehash: ff298f001a2d865446436e8099a2fbbef593a00a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62054195"
---
# <a name="let-clause-visual-basic"></a><span data-ttu-id="7dd9b-102">Let – klauzule (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7dd9b-102">Let Clause (Visual Basic)</span></span>
<span data-ttu-id="7dd9b-103">Vypočítá hodnotu a přiřadí ji nové proměnné v rámci dotazu.</span><span class="sxs-lookup"><span data-stu-id="7dd9b-103">Computes a value and assigns it to a new variable within the query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7dd9b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7dd9b-104">Syntax</span></span>  
  
```  
Let variable = expression [, ...]  
```  
  
## <a name="parts"></a><span data-ttu-id="7dd9b-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="7dd9b-105">Parts</span></span>  
  
|<span data-ttu-id="7dd9b-106">Termín</span><span class="sxs-lookup"><span data-stu-id="7dd9b-106">Term</span></span>|<span data-ttu-id="7dd9b-107">Definice</span><span class="sxs-lookup"><span data-stu-id="7dd9b-107">Definition</span></span>|  
|---|---|  
|`variable`|<span data-ttu-id="7dd9b-108">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="7dd9b-108">Required.</span></span> <span data-ttu-id="7dd9b-109">Alias, který slouží k odkazování výsledky poskytnutý výraz.</span><span class="sxs-lookup"><span data-stu-id="7dd9b-109">An alias that can be used to reference the results of the supplied expression.</span></span>|  
|`expression`|<span data-ttu-id="7dd9b-110">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="7dd9b-110">Required.</span></span> <span data-ttu-id="7dd9b-111">Výraz, který bude vyhodnocen a přiřazen k zadané proměnné.</span><span class="sxs-lookup"><span data-stu-id="7dd9b-111">An expression that will be evaluated and assigned to the specified variable.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7dd9b-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7dd9b-112">Remarks</span></span>  
 <span data-ttu-id="7dd9b-113">`Let` Klauzule můžete k výpočtu hodnoty pro každý výsledek dotazu a na ně odkazovat pomocí alias.</span><span class="sxs-lookup"><span data-stu-id="7dd9b-113">The `Let` clause enables you to compute values for each query result and reference them by using an alias.</span></span> <span data-ttu-id="7dd9b-114">Alias je možné v jiných klauzulích, jako `Where` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="7dd9b-114">The alias can be used in other clauses, such as the `Where` clause.</span></span> <span data-ttu-id="7dd9b-115">`Let` Klauzule vám umožní vytvořit příkaz dotazu, který je snazší přečíst, protože můžete zadat jako alias pro klauzuli výraz obsažena v dotazu a nahraďte aliasem, který se pokaždé, když se používá v klauzuli výrazu.</span><span class="sxs-lookup"><span data-stu-id="7dd9b-115">The `Let` clause enables you to create a query statement that is easier to read because you can specify an alias for an expression clause included in the query and substitute the alias each time the expression clause is used.</span></span>  
  
 <span data-ttu-id="7dd9b-116">Může obsahovat libovolný počet `variable` a `expression` přiřazení v `Let` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="7dd9b-116">You can include any number of `variable` and `expression` assignments in the `Let` clause.</span></span> <span data-ttu-id="7dd9b-117">Každé přiřazení oddělte čárkou (,).</span><span class="sxs-lookup"><span data-stu-id="7dd9b-117">Separate each assignment with a comma (,).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7dd9b-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="7dd9b-118">Example</span></span>  
 <span data-ttu-id="7dd9b-119">Následující příklad kódu používá `Let` klauzule compute 10 % slevu na produkty.</span><span class="sxs-lookup"><span data-stu-id="7dd9b-119">The following code example uses the `Let` clause to compute a 10 percent discount on products.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#16)]  
  
## <a name="see-also"></a><span data-ttu-id="7dd9b-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7dd9b-120">See also</span></span>

- [<span data-ttu-id="7dd9b-121">Úvod do LINQ v JAZYKU Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7dd9b-121">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="7dd9b-122">Dotazy</span><span class="sxs-lookup"><span data-stu-id="7dd9b-122">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="7dd9b-123">Klauzule Select</span><span class="sxs-lookup"><span data-stu-id="7dd9b-123">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="7dd9b-124">Klauzule From</span><span class="sxs-lookup"><span data-stu-id="7dd9b-124">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="7dd9b-125">Klauzule Where</span><span class="sxs-lookup"><span data-stu-id="7dd9b-125">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
