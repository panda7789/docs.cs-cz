---
title: TryCast – operátor
ms.date: 07/20/2015
f1_keywords:
- vb.trycast
- trycast
helpviewer_keywords:
- TryCast keyword [Visual Basic]
ms.assetid: d1ef5d47-fef4-491e-b014-1d910628f65c
ms.openlocfilehash: 8f0d4f612cd5a96e0b0ab7305c41e00790613cc8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406372"
---
# <a name="trycast-operator-visual-basic"></a><span data-ttu-id="03d1c-102">TryCast – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="03d1c-102">TryCast Operator (Visual Basic)</span></span>
<span data-ttu-id="03d1c-103">Zavádí operaci převodu typu, která nevyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="03d1c-103">Introduces a type conversion operation that does not throw an exception.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="03d1c-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="03d1c-104">Remarks</span></span>  
 <span data-ttu-id="03d1c-105">Pokud pokus o převod neproběhne úspěšně `CType` , `DirectCast` vyvolejte <xref:System.InvalidCastException> chybu.</span><span class="sxs-lookup"><span data-stu-id="03d1c-105">If an attempted conversion fails, `CType` and `DirectCast` both throw an <xref:System.InvalidCastException> error.</span></span> <span data-ttu-id="03d1c-106">To může mít nepříznivý vliv na výkon aplikace.</span><span class="sxs-lookup"><span data-stu-id="03d1c-106">This can adversely affect the performance of your application.</span></span> <span data-ttu-id="03d1c-107">`TryCast`nevrátí [žádnou](../nothing.md)hodnotu, takže namísto nutnosti zpracovat možnou výjimku budete potřebovat pouze test vráceného výsledku `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="03d1c-107">`TryCast` returns [Nothing](../nothing.md), so that instead of having to handle a possible exception, you need only test the returned result against `Nothing`.</span></span>  
  
 <span data-ttu-id="03d1c-108">`TryCast`Klíčové slovo se používá stejným způsobem jako [funkce CType](../functions/ctype-function.md) a klíčové slovo [operátoru DirectCast](directcast-operator.md) .</span><span class="sxs-lookup"><span data-stu-id="03d1c-108">You use the `TryCast` keyword the same way you use the [CType Function](../functions/ctype-function.md) and the [DirectCast Operator](directcast-operator.md) keyword.</span></span> <span data-ttu-id="03d1c-109">Výraz zadejte jako první argument a typ, který jej převede jako druhý argument.</span><span class="sxs-lookup"><span data-stu-id="03d1c-109">You supply an expression as the first argument and a type to convert it to as the second argument.</span></span> <span data-ttu-id="03d1c-110">`TryCast`funguje pouze na odkazových typech, jako jsou třídy a rozhraní.</span><span class="sxs-lookup"><span data-stu-id="03d1c-110">`TryCast` operates only on reference types, such as classes and interfaces.</span></span> <span data-ttu-id="03d1c-111">Vyžaduje vztah dědičnosti nebo implementace mezi těmito dvěma typy.</span><span class="sxs-lookup"><span data-stu-id="03d1c-111">It requires an inheritance or implementation relationship between the two types.</span></span> <span data-ttu-id="03d1c-112">To znamená, že jeden typ musí dědit z nebo implementovat druhý.</span><span class="sxs-lookup"><span data-stu-id="03d1c-112">This means that one type must inherit from or implement the other.</span></span>  
  
## <a name="errors-and-failures"></a><span data-ttu-id="03d1c-113">Chyby a selhání</span><span class="sxs-lookup"><span data-stu-id="03d1c-113">Errors and Failures</span></span>  
 <span data-ttu-id="03d1c-114">`TryCast`vygeneruje chybu kompilátoru, pokud zjistí, že neexistuje vztah dědičnosti nebo implementace.</span><span class="sxs-lookup"><span data-stu-id="03d1c-114">`TryCast` generates a compiler error if it detects that no inheritance or implementation relationship exists.</span></span> <span data-ttu-id="03d1c-115">Chybějící Chyba kompilátoru ale nezaručuje úspěšný převod.</span><span class="sxs-lookup"><span data-stu-id="03d1c-115">But the lack of a compiler error does not guarantee a successful conversion.</span></span> <span data-ttu-id="03d1c-116">Pokud je požadovaný převod zúžený, může v době běhu selhat.</span><span class="sxs-lookup"><span data-stu-id="03d1c-116">If the desired conversion is narrowing, it could fail at run time.</span></span> <span data-ttu-id="03d1c-117">V takovém případě `TryCast` vrátí hodnotu [Nothing](../nothing.md).</span><span class="sxs-lookup"><span data-stu-id="03d1c-117">If this happens, `TryCast` returns [Nothing](../nothing.md).</span></span>  
  
## <a name="conversion-keywords"></a><span data-ttu-id="03d1c-118">Klíčová slova převodu</span><span class="sxs-lookup"><span data-stu-id="03d1c-118">Conversion Keywords</span></span>  
 <span data-ttu-id="03d1c-119">Porovnání klíčových slov převodu typů je následující.</span><span class="sxs-lookup"><span data-stu-id="03d1c-119">A comparison of the type conversion keywords is as follows.</span></span>  
  
|<span data-ttu-id="03d1c-120">Klíčové slovo</span><span class="sxs-lookup"><span data-stu-id="03d1c-120">Keyword</span></span>|<span data-ttu-id="03d1c-121">Datové typy</span><span class="sxs-lookup"><span data-stu-id="03d1c-121">Data types</span></span>|<span data-ttu-id="03d1c-122">Relace argumentu</span><span class="sxs-lookup"><span data-stu-id="03d1c-122">Argument relationship</span></span>|<span data-ttu-id="03d1c-123">Selhání za běhu</span><span class="sxs-lookup"><span data-stu-id="03d1c-123">Run-time failure</span></span>|  
|---|---|---|---|  
|[<span data-ttu-id="03d1c-124">CType – funkce</span><span class="sxs-lookup"><span data-stu-id="03d1c-124">CType Function</span></span>](../functions/ctype-function.md)|<span data-ttu-id="03d1c-125">Všechny typy dat</span><span class="sxs-lookup"><span data-stu-id="03d1c-125">Any data types</span></span>|<span data-ttu-id="03d1c-126">Mezi dvěma datovými typy musí být definovaný rozšiřující nebo zužující převod.</span><span class="sxs-lookup"><span data-stu-id="03d1c-126">Widening or narrowing conversion must be defined between the two data types</span></span>|<span data-ttu-id="03d1c-127">Vyvolá<xref:System.InvalidCastException></span><span class="sxs-lookup"><span data-stu-id="03d1c-127">Throws <xref:System.InvalidCastException></span></span>|  
|[<span data-ttu-id="03d1c-128">DirectCast – operátor</span><span class="sxs-lookup"><span data-stu-id="03d1c-128">DirectCast Operator</span></span>](directcast-operator.md)|<span data-ttu-id="03d1c-129">Všechny typy dat</span><span class="sxs-lookup"><span data-stu-id="03d1c-129">Any data types</span></span>|<span data-ttu-id="03d1c-130">Jeden typ musí dědit z nebo implementovat jiný typ.</span><span class="sxs-lookup"><span data-stu-id="03d1c-130">One type must inherit from or implement the other type</span></span>|<span data-ttu-id="03d1c-131">Vyvolá<xref:System.InvalidCastException></span><span class="sxs-lookup"><span data-stu-id="03d1c-131">Throws <xref:System.InvalidCastException></span></span>|  
|`TryCast`|<span data-ttu-id="03d1c-132">Pouze odkazované typy</span><span class="sxs-lookup"><span data-stu-id="03d1c-132">Reference types only</span></span>|<span data-ttu-id="03d1c-133">Jeden typ musí dědit z nebo implementovat jiný typ.</span><span class="sxs-lookup"><span data-stu-id="03d1c-133">One type must inherit from or implement the other type</span></span>|<span data-ttu-id="03d1c-134">Vrátí hodnotu [Nothing](../nothing.md) .</span><span class="sxs-lookup"><span data-stu-id="03d1c-134">Returns [Nothing](../nothing.md)</span></span>|  
  
## <a name="example"></a><span data-ttu-id="03d1c-135">Příklad</span><span class="sxs-lookup"><span data-stu-id="03d1c-135">Example</span></span>  
 <span data-ttu-id="03d1c-136">Následující příklad ukazuje, jak použít `TryCast` .</span><span class="sxs-lookup"><span data-stu-id="03d1c-136">The following example shows how to use `TryCast`.</span></span>  
  
 [!code-vb[VbVbalrKeywords#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="03d1c-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="03d1c-137">See also</span></span>

- [<span data-ttu-id="03d1c-138">Rozšíření a zúžení převodů</span><span class="sxs-lookup"><span data-stu-id="03d1c-138">Widening and Narrowing Conversions</span></span>](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="03d1c-139">Implicitní a explicitní převody</span><span class="sxs-lookup"><span data-stu-id="03d1c-139">Implicit and Explicit Conversions</span></span>](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
