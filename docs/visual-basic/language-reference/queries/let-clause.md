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
ms.openlocfilehash: 88166a040823cfefe623f672e556c364d652a7fc
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004726"
---
# <a name="let-clause-visual-basic"></a><span data-ttu-id="8e008-102">Let – klauzule (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8e008-102">Let Clause (Visual Basic)</span></span>
<span data-ttu-id="8e008-103">Vypočítá hodnotu a přiřadí ji k nové proměnné v rámci dotazu.</span><span class="sxs-lookup"><span data-stu-id="8e008-103">Computes a value and assigns it to a new variable within the query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e008-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8e008-104">Syntax</span></span>  
  
```vb  
Let variable = expression [, ...]  
```  
  
## <a name="parts"></a><span data-ttu-id="8e008-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="8e008-105">Parts</span></span>  
  
|<span data-ttu-id="8e008-106">Termín</span><span class="sxs-lookup"><span data-stu-id="8e008-106">Term</span></span>|<span data-ttu-id="8e008-107">Definice</span><span class="sxs-lookup"><span data-stu-id="8e008-107">Definition</span></span>|  
|---|---|  
|`variable`|<span data-ttu-id="8e008-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="8e008-108">Required.</span></span> <span data-ttu-id="8e008-109">Alias, který lze použít k odkazování na výsledky poskytnutého výrazu.</span><span class="sxs-lookup"><span data-stu-id="8e008-109">An alias that can be used to reference the results of the supplied expression.</span></span>|  
|`expression`|<span data-ttu-id="8e008-110">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="8e008-110">Required.</span></span> <span data-ttu-id="8e008-111">Výraz, který bude vyhodnocen a přiřazen k zadané proměnné.</span><span class="sxs-lookup"><span data-stu-id="8e008-111">An expression that will be evaluated and assigned to the specified variable.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8e008-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8e008-112">Remarks</span></span>  
 <span data-ttu-id="8e008-113">Klauzule `Let` umožňuje vypočítat hodnoty pro každý výsledek dotazu a odkazovat na ně pomocí aliasu.</span><span class="sxs-lookup"><span data-stu-id="8e008-113">The `Let` clause enables you to compute values for each query result and reference them by using an alias.</span></span> <span data-ttu-id="8e008-114">Alias lze použít v jiných klauzulích, například v klauzuli `Where`.</span><span class="sxs-lookup"><span data-stu-id="8e008-114">The alias can be used in other clauses, such as the `Where` clause.</span></span> <span data-ttu-id="8e008-115">Klauzule `Let` umožňuje vytvořit příkaz dotazu, který je snazší číst, protože můžete zadat alias pro klauzuli Expression, který je součástí dotazu, a nahradit alias pokaždé, když se použije klauzule Expression.</span><span class="sxs-lookup"><span data-stu-id="8e008-115">The `Let` clause enables you to create a query statement that is easier to read because you can specify an alias for an expression clause included in the query and substitute the alias each time the expression clause is used.</span></span>  
  
 <span data-ttu-id="8e008-116">V klauzuli `Let` můžete zahrnout libovolný počet přiřazení `variable` a `expression`.</span><span class="sxs-lookup"><span data-stu-id="8e008-116">You can include any number of `variable` and `expression` assignments in the `Let` clause.</span></span> <span data-ttu-id="8e008-117">Jednotlivá přiřazení oddělte čárkou (,).</span><span class="sxs-lookup"><span data-stu-id="8e008-117">Separate each assignment with a comma (,).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8e008-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="8e008-118">Example</span></span>  
 <span data-ttu-id="8e008-119">Následující příklad kódu používá klauzuli `Let` pro výpočet 10% slevy na produkty.</span><span class="sxs-lookup"><span data-stu-id="8e008-119">The following code example uses the `Let` clause to compute a 10 percent discount on products.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#16)]  
  
## <a name="see-also"></a><span data-ttu-id="8e008-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8e008-120">See also</span></span>

- [<span data-ttu-id="8e008-121">Úvod do jazyka LINQ v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8e008-121">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="8e008-122">Dotazy</span><span class="sxs-lookup"><span data-stu-id="8e008-122">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="8e008-123">Klauzule Select</span><span class="sxs-lookup"><span data-stu-id="8e008-123">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="8e008-124">Klauzule From</span><span class="sxs-lookup"><span data-stu-id="8e008-124">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="8e008-125">Klauzule Where</span><span class="sxs-lookup"><span data-stu-id="8e008-125">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
