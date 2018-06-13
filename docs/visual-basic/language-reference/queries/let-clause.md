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
ms.openlocfilehash: 6484da5329c8240735b7c35f506637dd01cbeda4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604468"
---
# <a name="let-clause-visual-basic"></a><span data-ttu-id="25e00-102">Let – klauzule (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="25e00-102">Let Clause (Visual Basic)</span></span>
<span data-ttu-id="25e00-103">Vypočítá hodnotu a přiřadí ji k nové proměnné v dotazu.</span><span class="sxs-lookup"><span data-stu-id="25e00-103">Computes a value and assigns it to a new variable within the query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25e00-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="25e00-104">Syntax</span></span>  
  
```  
Let variable = expression [, ...]  
```  
  
## <a name="parts"></a><span data-ttu-id="25e00-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="25e00-105">Parts</span></span>  
  
|<span data-ttu-id="25e00-106">Termín</span><span class="sxs-lookup"><span data-stu-id="25e00-106">Term</span></span>|<span data-ttu-id="25e00-107">Definice</span><span class="sxs-lookup"><span data-stu-id="25e00-107">Definition</span></span>|  
|---|---|  
|`variable`|<span data-ttu-id="25e00-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="25e00-108">Required.</span></span> <span data-ttu-id="25e00-109">Alias, který slouží k odkazování výsledky zadaný výraz.</span><span class="sxs-lookup"><span data-stu-id="25e00-109">An alias that can be used to reference the results of the supplied expression.</span></span>|  
|`expression`|<span data-ttu-id="25e00-110">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="25e00-110">Required.</span></span> <span data-ttu-id="25e00-111">Výraz, který bude vyhodnocen a přiřazené k zadané proměnné.</span><span class="sxs-lookup"><span data-stu-id="25e00-111">An expression that will be evaluated and assigned to the specified variable.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="25e00-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="25e00-112">Remarks</span></span>  
 <span data-ttu-id="25e00-113">`Let` Klauzule umožňuje výpočetní hodnoty pro každý výsledek dotazu a odkazujte na ně pomocí alias.</span><span class="sxs-lookup"><span data-stu-id="25e00-113">The `Let` clause enables you to compute values for each query result and reference them by using an alias.</span></span> <span data-ttu-id="25e00-114">Alias lze použít v jiných klauzulích, jako `Where` klauzule.</span><span class="sxs-lookup"><span data-stu-id="25e00-114">The alias can be used in other clauses, such as the `Where` clause.</span></span> <span data-ttu-id="25e00-115">`Let` Klauzule umožňuje vytvářet příkaz dotazu, který lze snadněji přečíst, protože můžete zadat alias pro klauzuli výraz, který je zahrnutý v dotazu a nahraďte alias pokaždé, když se používá v klauzuli výraz.</span><span class="sxs-lookup"><span data-stu-id="25e00-115">The `Let` clause enables you to create a query statement that is easier to read because you can specify an alias for an expression clause included in the query and substitute the alias each time the expression clause is used.</span></span>  
  
 <span data-ttu-id="25e00-116">Může obsahovat libovolný počet `variable` a `expression` přiřazení v `Let` klauzule.</span><span class="sxs-lookup"><span data-stu-id="25e00-116">You can include any number of `variable` and `expression` assignments in the `Let` clause.</span></span> <span data-ttu-id="25e00-117">Každé přiřazení oddělte čárkou (,).</span><span class="sxs-lookup"><span data-stu-id="25e00-117">Separate each assignment with a comma (,).</span></span>  
  
## <a name="example"></a><span data-ttu-id="25e00-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="25e00-118">Example</span></span>  
 <span data-ttu-id="25e00-119">Následující příklad kódu používá `Let` klauzule k výpočtu 10 procent slevy na produkty.</span><span class="sxs-lookup"><span data-stu-id="25e00-119">The following code example uses the `Let` clause to compute a 10 percent discount on products.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#16](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/let-clause_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="25e00-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="25e00-120">See Also</span></span>  
 [<span data-ttu-id="25e00-121">Úvod do LINQ v jazyku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="25e00-121">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="25e00-122">Dotazy</span><span class="sxs-lookup"><span data-stu-id="25e00-122">Queries</span></span>](../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="25e00-123">Klauzule Select</span><span class="sxs-lookup"><span data-stu-id="25e00-123">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)  
 [<span data-ttu-id="25e00-124">Klauzule From</span><span class="sxs-lookup"><span data-stu-id="25e00-124">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)  
 [<span data-ttu-id="25e00-125">Klauzule Where</span><span class="sxs-lookup"><span data-stu-id="25e00-125">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
