---
title: V tomto kontextu není podporováno odvození typu s povolenou hodnotu Null.
ms.date: 07/20/2015
f1_keywords:
- vbc36629
- bc36629
helpviewer_keywords:
- BC36629
ms.assetid: 0a1e2dbc-d9a4-433d-9306-c5540782b81d
ms.openlocfilehash: 9f7f878649d8b96f050b56d5b878eb3d67e027ff
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58819239"
---
# <a name="nullable-type-inference-is-not-supported-in-this-context"></a><span data-ttu-id="cea86-102">V tomto kontextu není podporováno odvození typu s povolenou hodnotu Null.</span><span class="sxs-lookup"><span data-stu-id="cea86-102">Nullable type inference is not supported in this context</span></span>
<span data-ttu-id="cea86-103">Hodnotové typy a struktury mohou být deklarovány s možnou hodnotou Null.</span><span class="sxs-lookup"><span data-stu-id="cea86-103">Value types and structures can be declared nullable.</span></span>  
  
```vb  
Dim a? As Integer  
Dim b As Integer?  
```  
  
 <span data-ttu-id="cea86-104">Však nelze použít deklaraci s možnou hodnotou Null v kombinaci s odvození typu proměnné.</span><span class="sxs-lookup"><span data-stu-id="cea86-104">However, you cannot use the nullable declaration in combination with type inference.</span></span> <span data-ttu-id="cea86-105">Následující příklady příčinou této chyby.</span><span class="sxs-lookup"><span data-stu-id="cea86-105">The following examples cause this error.</span></span>  
  
```vb  
' Not valid.  
' Dim c? = 10  
' Dim d? = a  
```  
  
 <span data-ttu-id="cea86-106">**ID chyby:** BC36629</span><span class="sxs-lookup"><span data-stu-id="cea86-106">**Error ID:** BC36629</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="cea86-107">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="cea86-107">To correct this error</span></span>  
  
-   <span data-ttu-id="cea86-108">Použití `As` klauzule deklarovat proměnnou jako s možnou hodnotou Null.</span><span class="sxs-lookup"><span data-stu-id="cea86-108">Use an `As` clause to declare the variable as nullable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cea86-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cea86-109">See also</span></span>

- [<span data-ttu-id="cea86-110">Typy hodnot s povolenou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="cea86-110">Nullable Value Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [<span data-ttu-id="cea86-111">Odvození místního typu</span><span class="sxs-lookup"><span data-stu-id="cea86-111">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
