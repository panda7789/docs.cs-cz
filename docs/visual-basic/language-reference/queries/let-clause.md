---
title: Let – klauzule
ms.date: 07/20/2015
f1_keywords:
- vb.QueryLet
helpviewer_keywords:
- queries [Visual Basic], Let
- Let clause [Visual Basic]
- Let statement [Visual Basic]
ms.assetid: 981aa516-16eb-4c53-b1f1-5aa3e82f316e
ms.openlocfilehash: 4bf832651d9753c41ee5a02defec4adc55af1ff1
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84359758"
---
# <a name="let-clause-visual-basic"></a><span data-ttu-id="71e81-102">Let – klauzule (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="71e81-102">Let Clause (Visual Basic)</span></span>
<span data-ttu-id="71e81-103">Vypočítá hodnotu a přiřadí ji k nové proměnné v rámci dotazu.</span><span class="sxs-lookup"><span data-stu-id="71e81-103">Computes a value and assigns it to a new variable within the query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71e81-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="71e81-104">Syntax</span></span>  
  
```vb  
Let variable = expression [, ...]  
```  
  
## <a name="parts"></a><span data-ttu-id="71e81-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="71e81-105">Parts</span></span>  
  
|<span data-ttu-id="71e81-106">Pojem</span><span class="sxs-lookup"><span data-stu-id="71e81-106">Term</span></span>|<span data-ttu-id="71e81-107">Definice</span><span class="sxs-lookup"><span data-stu-id="71e81-107">Definition</span></span>|  
|---|---|  
|`variable`|<span data-ttu-id="71e81-108">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="71e81-108">Required.</span></span> <span data-ttu-id="71e81-109">Alias, který lze použít k odkazování na výsledky poskytnutého výrazu.</span><span class="sxs-lookup"><span data-stu-id="71e81-109">An alias that can be used to reference the results of the supplied expression.</span></span>|  
|`expression`|<span data-ttu-id="71e81-110">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="71e81-110">Required.</span></span> <span data-ttu-id="71e81-111">Výraz, který bude vyhodnocen a přiřazen k zadané proměnné.</span><span class="sxs-lookup"><span data-stu-id="71e81-111">An expression that will be evaluated and assigned to the specified variable.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="71e81-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="71e81-112">Remarks</span></span>  
 <span data-ttu-id="71e81-113">`Let`Klauzule umožňuje vypočítat hodnoty pro každý výsledek dotazu a odkazovat na ně pomocí aliasu.</span><span class="sxs-lookup"><span data-stu-id="71e81-113">The `Let` clause enables you to compute values for each query result and reference them by using an alias.</span></span> <span data-ttu-id="71e81-114">Alias lze použít v jiných klauzulích, jako je například `Where` klauzule.</span><span class="sxs-lookup"><span data-stu-id="71e81-114">The alias can be used in other clauses, such as the `Where` clause.</span></span> <span data-ttu-id="71e81-115">`Let`Klauzule umožňuje vytvořit příkaz dotazu, který je snazší číst, protože můžete zadat alias klauzule Expression, který je součástí dotazu, a nahradit alias pokaždé, když se použije klauzule Expression.</span><span class="sxs-lookup"><span data-stu-id="71e81-115">The `Let` clause enables you to create a query statement that is easier to read because you can specify an alias for an expression clause included in the query and substitute the alias each time the expression clause is used.</span></span>  
  
 <span data-ttu-id="71e81-116">V klauzuli můžete zadat libovolný počet `variable` a `expression` přiřazení `Let` .</span><span class="sxs-lookup"><span data-stu-id="71e81-116">You can include any number of `variable` and `expression` assignments in the `Let` clause.</span></span> <span data-ttu-id="71e81-117">Jednotlivá přiřazení oddělte čárkou (,).</span><span class="sxs-lookup"><span data-stu-id="71e81-117">Separate each assignment with a comma (,).</span></span>  
  
## <a name="example"></a><span data-ttu-id="71e81-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="71e81-118">Example</span></span>  
 <span data-ttu-id="71e81-119">Následující příklad kódu používá `Let` klauzuli pro výpočet 10% slevy na produkty.</span><span class="sxs-lookup"><span data-stu-id="71e81-119">The following code example uses the `Let` clause to compute a 10 percent discount on products.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#16)]  
  
## <a name="see-also"></a><span data-ttu-id="71e81-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="71e81-120">See also</span></span>

- [<span data-ttu-id="71e81-121">Představení technologie LINQ v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="71e81-121">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="71e81-122">Dotazy</span><span class="sxs-lookup"><span data-stu-id="71e81-122">Queries</span></span>](index.md)
- [<span data-ttu-id="71e81-123">Klauzule SELECT</span><span class="sxs-lookup"><span data-stu-id="71e81-123">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="71e81-124">Klauzule FROM</span><span class="sxs-lookup"><span data-stu-id="71e81-124">From Clause</span></span>](from-clause.md)
- [<span data-ttu-id="71e81-125">Klauzule WHERE</span><span class="sxs-lookup"><span data-stu-id="71e81-125">Where Clause</span></span>](where-clause.md)
