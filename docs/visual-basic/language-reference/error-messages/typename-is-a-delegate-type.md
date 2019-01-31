---
title: "'<typename>' je typ delegátu."
ms.date: 07/20/2015
f1_keywords:
- bc32008
- vbc32008
helpviewer_keywords:
- BC32008
ms.assetid: dc6abba0-a9ad-450f-8899-87265bc84abc
ms.openlocfilehash: 4278ea0fc6a8dc2c6a90b720d2da70b1c26f2a17
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55283449"
---
# <a name="typename-is-a-delegate-type"></a><span data-ttu-id="7dadc-102">"\<typename >' je typ delegátu</span><span class="sxs-lookup"><span data-stu-id="7dadc-102">'\<typename>' is a delegate type</span></span>
<span data-ttu-id="7dadc-103">"\<typename >' je typ delegátu.</span><span class="sxs-lookup"><span data-stu-id="7dadc-103">'\<typename>' is a delegate type.</span></span> <span data-ttu-id="7dadc-104">Konstrukce delegáta povoluje pouze jeden výraz AddressOf jako seznam argumentů.</span><span class="sxs-lookup"><span data-stu-id="7dadc-104">Delegate construction permits only a single AddressOf expression as an argument list.</span></span> <span data-ttu-id="7dadc-105">Výraz AddressOf často lze použít místo vytváření delegátů.</span><span class="sxs-lookup"><span data-stu-id="7dadc-105">Often an AddressOf expression can be used instead of a delegate construction.</span></span>  
  
 <span data-ttu-id="7dadc-106">A `New` klauzule vytvoření instance třídy delegáta poskytuje seznam neplatný argumentů pro konstruktor delegate.</span><span class="sxs-lookup"><span data-stu-id="7dadc-106">A `New` clause creating an instance of a delegate class supplies an invalid argument list to the delegate constructor.</span></span>  
  
 <span data-ttu-id="7dadc-107">Můžete zadat pouze jeden `AddressOf` výraz při vytváření nové instance delegáta.</span><span class="sxs-lookup"><span data-stu-id="7dadc-107">You can supply only a single `AddressOf` expression when creating a new delegate instance.</span></span>  
  
 <span data-ttu-id="7dadc-108">K této chybě může dojít, pokud nepředáte žádné argumenty konstruktoru delegáta, Pokud předáváte více než jeden argument, nebo Pokud předáte jeden argument, který není platným `AddressOf` výrazu.</span><span class="sxs-lookup"><span data-stu-id="7dadc-108">This error can result if you do not pass any arguments to the delegate constructor, if you pass more than one argument, or if you pass a single argument that is not a valid `AddressOf` expression.</span></span>  
  
 <span data-ttu-id="7dadc-109">**ID chyby:** BC32008</span><span class="sxs-lookup"><span data-stu-id="7dadc-109">**Error ID:** BC32008</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7dadc-110">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="7dadc-110">To correct this error</span></span>  
  
-   <span data-ttu-id="7dadc-111">Pomocí jediné `AddressOf` výraz v seznamu argumentů pro třídu delegáta v `New` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="7dadc-111">Use a single `AddressOf` expression in the argument list for the delegate class in the `New` clause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7dadc-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7dadc-112">See also</span></span>
- [<span data-ttu-id="7dadc-113">Operátor New</span><span class="sxs-lookup"><span data-stu-id="7dadc-113">New Operator</span></span>](../../../visual-basic/language-reference/operators/new-operator.md)
- [<span data-ttu-id="7dadc-114">Operátor AddressOf</span><span class="sxs-lookup"><span data-stu-id="7dadc-114">AddressOf Operator</span></span>](../../../visual-basic/language-reference/operators/addressof-operator.md)
- [<span data-ttu-id="7dadc-115">Delegáti</span><span class="sxs-lookup"><span data-stu-id="7dadc-115">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="7dadc-116">Postupy: Volání metody delegáta</span><span class="sxs-lookup"><span data-stu-id="7dadc-116">How to: Invoke a Delegate Method</span></span>](../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)
