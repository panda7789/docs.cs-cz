---
title: "'<typename>' je typ delegátu."
ms.date: 07/20/2015
f1_keywords:
- bc32008
- vbc32008
helpviewer_keywords:
- BC32008
ms.assetid: dc6abba0-a9ad-450f-8899-87265bc84abc
ms.openlocfilehash: 45dc0403468fa40888a6c5e6bdfe6ca782e98325
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64664171"
---
# <a name="typename-is-a-delegate-type"></a><span data-ttu-id="aa7c9-102">"\<typename >' je typ delegátu</span><span class="sxs-lookup"><span data-stu-id="aa7c9-102">'\<typename>' is a delegate type</span></span>
<span data-ttu-id="aa7c9-103">"\<typename >' je typ delegátu.</span><span class="sxs-lookup"><span data-stu-id="aa7c9-103">'\<typename>' is a delegate type.</span></span> <span data-ttu-id="aa7c9-104">Konstrukce delegáta povoluje pouze jeden výraz AddressOf jako seznam argumentů.</span><span class="sxs-lookup"><span data-stu-id="aa7c9-104">Delegate construction permits only a single AddressOf expression as an argument list.</span></span> <span data-ttu-id="aa7c9-105">Výraz AddressOf často lze použít místo vytváření delegátů.</span><span class="sxs-lookup"><span data-stu-id="aa7c9-105">Often an AddressOf expression can be used instead of a delegate construction.</span></span>  
  
 <span data-ttu-id="aa7c9-106">A `New` klauzule vytvoření instance třídy delegáta poskytuje seznam neplatný argumentů pro konstruktor delegate.</span><span class="sxs-lookup"><span data-stu-id="aa7c9-106">A `New` clause creating an instance of a delegate class supplies an invalid argument list to the delegate constructor.</span></span>  
  
 <span data-ttu-id="aa7c9-107">Můžete zadat pouze jeden `AddressOf` výraz při vytváření nové instance delegáta.</span><span class="sxs-lookup"><span data-stu-id="aa7c9-107">You can supply only a single `AddressOf` expression when creating a new delegate instance.</span></span>  
  
 <span data-ttu-id="aa7c9-108">K této chybě může dojít, pokud nepředáte žádné argumenty konstruktoru delegáta, Pokud předáváte více než jeden argument, nebo Pokud předáte jeden argument, který není platným `AddressOf` výrazu.</span><span class="sxs-lookup"><span data-stu-id="aa7c9-108">This error can result if you do not pass any arguments to the delegate constructor, if you pass more than one argument, or if you pass a single argument that is not a valid `AddressOf` expression.</span></span>  
  
 <span data-ttu-id="aa7c9-109">**ID chyby:** BC32008</span><span class="sxs-lookup"><span data-stu-id="aa7c9-109">**Error ID:** BC32008</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="aa7c9-110">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="aa7c9-110">To correct this error</span></span>  
  
- <span data-ttu-id="aa7c9-111">Pomocí jediné `AddressOf` výraz v seznamu argumentů pro třídu delegáta v `New` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="aa7c9-111">Use a single `AddressOf` expression in the argument list for the delegate class in the `New` clause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa7c9-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="aa7c9-112">See also</span></span>

- [<span data-ttu-id="aa7c9-113">Operátor New</span><span class="sxs-lookup"><span data-stu-id="aa7c9-113">New Operator</span></span>](../../../visual-basic/language-reference/operators/new-operator.md)
- [<span data-ttu-id="aa7c9-114">Operátor AddressOf</span><span class="sxs-lookup"><span data-stu-id="aa7c9-114">AddressOf Operator</span></span>](../../../visual-basic/language-reference/operators/addressof-operator.md)
- [<span data-ttu-id="aa7c9-115">Delegáti</span><span class="sxs-lookup"><span data-stu-id="aa7c9-115">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="aa7c9-116">Postupy: Volání metody delegáta</span><span class="sxs-lookup"><span data-stu-id="aa7c9-116">How to: Invoke a Delegate Method</span></span>](../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)
