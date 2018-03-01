---
title: "& č. 39; &lt;typename&gt;& č. 39; je typem delegáta"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc32008
- vbc32008
helpviewer_keywords:
- BC32008
ms.assetid: dc6abba0-a9ad-450f-8899-87265bc84abc
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9428f0ac321b90e36d4d987381ed69b6c968894c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="39lttypenamegt39-is-a-delegate-type"></a><span data-ttu-id="72aa5-102">& č. 39; &lt;typename&gt;& č. 39; je typem delegáta</span><span class="sxs-lookup"><span data-stu-id="72aa5-102">&#39;&lt;typename&gt;&#39; is a delegate type</span></span>
<span data-ttu-id="72aa5-103">'\<typename >' je typ delegáta.</span><span class="sxs-lookup"><span data-stu-id="72aa5-103">'\<typename>' is a delegate type.</span></span> <span data-ttu-id="72aa5-104">Delegát konstrukce umožňuje jenom jeden výraz AddressOf jako seznam argumentů.</span><span class="sxs-lookup"><span data-stu-id="72aa5-104">Delegate construction permits only a single AddressOf expression as an argument list.</span></span> <span data-ttu-id="72aa5-105">Často Výraz AddressOf lze namísto vytváření delegáta.</span><span class="sxs-lookup"><span data-stu-id="72aa5-105">Often an AddressOf expression can be used instead of a delegate construction.</span></span>  
  
 <span data-ttu-id="72aa5-106">A `New` klauzule vytvoření instance třídy delegáta poskytuje seznam neplatný argumentů pro konstruktor delegáta.</span><span class="sxs-lookup"><span data-stu-id="72aa5-106">A `New` clause creating an instance of a delegate class supplies an invalid argument list to the delegate constructor.</span></span>  
  
 <span data-ttu-id="72aa5-107">Můžete zadat jenom jeden `AddressOf` výraz při vytvoření nové instance delegáta.</span><span class="sxs-lookup"><span data-stu-id="72aa5-107">You can supply only a single `AddressOf` expression when creating a new delegate instance.</span></span>  
  
 <span data-ttu-id="72aa5-108">K této chybě může dojít, pokud neproběhne úspěšně všechny argumenty pro konstruktor delegáta, pokud předáte více než jeden argument, nebo Pokud předáte jeden argument, který není platným `AddressOf` výraz.</span><span class="sxs-lookup"><span data-stu-id="72aa5-108">This error can result if you do not pass any arguments to the delegate constructor, if you pass more than one argument, or if you pass a single argument that is not a valid `AddressOf` expression.</span></span>  
  
 <span data-ttu-id="72aa5-109">**ID chyby:** BC32008</span><span class="sxs-lookup"><span data-stu-id="72aa5-109">**Error ID:** BC32008</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="72aa5-110">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="72aa5-110">To correct this error</span></span>  
  
-   <span data-ttu-id="72aa5-111">Použití jedné `AddressOf` výraz v seznamu argumentů pro třídu delegáta v `New` klauzule.</span><span class="sxs-lookup"><span data-stu-id="72aa5-111">Use a single `AddressOf` expression in the argument list for the delegate class in the `New` clause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72aa5-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="72aa5-112">See Also</span></span>  
 [<span data-ttu-id="72aa5-113">New – operátor</span><span class="sxs-lookup"><span data-stu-id="72aa5-113">New Operator</span></span>](../../../visual-basic/language-reference/operators/new-operator.md)  
 [<span data-ttu-id="72aa5-114">AddressOf – operátor</span><span class="sxs-lookup"><span data-stu-id="72aa5-114">AddressOf Operator</span></span>](../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [<span data-ttu-id="72aa5-115">Delegáti</span><span class="sxs-lookup"><span data-stu-id="72aa5-115">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [<span data-ttu-id="72aa5-116">Postupy: volání metody delegáta</span><span class="sxs-lookup"><span data-stu-id="72aa5-116">How to: Invoke a Delegate Method</span></span>](../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)
