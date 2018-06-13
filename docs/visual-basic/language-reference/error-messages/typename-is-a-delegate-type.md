---
title: '&#39;&lt;TypeName&gt; &#39; je typem delegáta'
ms.date: 07/20/2015
f1_keywords:
- bc32008
- vbc32008
helpviewer_keywords:
- BC32008
ms.assetid: dc6abba0-a9ad-450f-8899-87265bc84abc
ms.openlocfilehash: c6d4244ce72dedee50b65ba19978149ce86b9e87
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33595645"
---
# <a name="39lttypenamegt39-is-a-delegate-type"></a><span data-ttu-id="29506-102">&#39;&lt;TypeName&gt; &#39; je typem delegáta</span><span class="sxs-lookup"><span data-stu-id="29506-102">&#39;&lt;typename&gt;&#39; is a delegate type</span></span>
<span data-ttu-id="29506-103">'\<typename >' je typ delegáta.</span><span class="sxs-lookup"><span data-stu-id="29506-103">'\<typename>' is a delegate type.</span></span> <span data-ttu-id="29506-104">Delegát konstrukce umožňuje jenom jeden výraz AddressOf jako seznam argumentů.</span><span class="sxs-lookup"><span data-stu-id="29506-104">Delegate construction permits only a single AddressOf expression as an argument list.</span></span> <span data-ttu-id="29506-105">Často Výraz AddressOf lze namísto vytváření delegáta.</span><span class="sxs-lookup"><span data-stu-id="29506-105">Often an AddressOf expression can be used instead of a delegate construction.</span></span>  
  
 <span data-ttu-id="29506-106">A `New` klauzule vytvoření instance třídy delegáta poskytuje seznam neplatný argumentů pro konstruktor delegáta.</span><span class="sxs-lookup"><span data-stu-id="29506-106">A `New` clause creating an instance of a delegate class supplies an invalid argument list to the delegate constructor.</span></span>  
  
 <span data-ttu-id="29506-107">Můžete zadat jenom jeden `AddressOf` výraz při vytvoření nové instance delegáta.</span><span class="sxs-lookup"><span data-stu-id="29506-107">You can supply only a single `AddressOf` expression when creating a new delegate instance.</span></span>  
  
 <span data-ttu-id="29506-108">K této chybě může dojít, pokud neproběhne úspěšně všechny argumenty pro konstruktor delegáta, pokud předáte více než jeden argument, nebo Pokud předáte jeden argument, který není platným `AddressOf` výraz.</span><span class="sxs-lookup"><span data-stu-id="29506-108">This error can result if you do not pass any arguments to the delegate constructor, if you pass more than one argument, or if you pass a single argument that is not a valid `AddressOf` expression.</span></span>  
  
 <span data-ttu-id="29506-109">**ID chyby:** BC32008</span><span class="sxs-lookup"><span data-stu-id="29506-109">**Error ID:** BC32008</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="29506-110">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="29506-110">To correct this error</span></span>  
  
-   <span data-ttu-id="29506-111">Použití jedné `AddressOf` výraz v seznamu argumentů pro třídu delegáta v `New` klauzule.</span><span class="sxs-lookup"><span data-stu-id="29506-111">Use a single `AddressOf` expression in the argument list for the delegate class in the `New` clause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29506-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="29506-112">See Also</span></span>  
 [<span data-ttu-id="29506-113">Operátor New</span><span class="sxs-lookup"><span data-stu-id="29506-113">New Operator</span></span>](../../../visual-basic/language-reference/operators/new-operator.md)  
 [<span data-ttu-id="29506-114">Operátor AddressOf</span><span class="sxs-lookup"><span data-stu-id="29506-114">AddressOf Operator</span></span>](../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [<span data-ttu-id="29506-115">Delegáti</span><span class="sxs-lookup"><span data-stu-id="29506-115">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [<span data-ttu-id="29506-116">Postupy: Volání metody delegáta</span><span class="sxs-lookup"><span data-stu-id="29506-116">How to: Invoke a Delegate Method</span></span>](../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)
