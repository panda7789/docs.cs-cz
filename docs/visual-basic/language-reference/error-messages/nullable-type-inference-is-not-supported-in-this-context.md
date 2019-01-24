---
title: V tomto kontextu není podporováno odvození typu s povolenou hodnotu Null.
ms.date: 07/20/2015
f1_keywords:
- vbc36629
- bc36629
helpviewer_keywords:
- BC36629
ms.assetid: 0a1e2dbc-d9a4-433d-9306-c5540782b81d
ms.openlocfilehash: 7dffc5233656257cd892f573a2f8b9f91d781c21
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54611888"
---
# <a name="nullable-type-inference-is-not-supported-in-this-context"></a><span data-ttu-id="e1a2a-102">V tomto kontextu není podporováno odvození typu s povolenou hodnotu Null.</span><span class="sxs-lookup"><span data-stu-id="e1a2a-102">Nullable type inference is not supported in this context</span></span>
<span data-ttu-id="e1a2a-103">Hodnotové typy a struktury mohou být deklarovány s možnou hodnotou Null.</span><span class="sxs-lookup"><span data-stu-id="e1a2a-103">Value types and structures can be declared nullable.</span></span>  
  
```vb  
Dim a? As Integer  
Dim b As Integer?  
```  
  
 <span data-ttu-id="e1a2a-104">Však nelze použít deklaraci s možnou hodnotou Null v kombinaci s odvození typu proměnné.</span><span class="sxs-lookup"><span data-stu-id="e1a2a-104">However, you cannot use the nullable declaration in combination with type inference.</span></span> <span data-ttu-id="e1a2a-105">Následující příklady příčinou této chyby.</span><span class="sxs-lookup"><span data-stu-id="e1a2a-105">The following examples cause this error.</span></span>  
  
```vb  
' Not valid.  
' Dim c? = 10  
' Dim d? = a  
```  
  
 <span data-ttu-id="e1a2a-106">**ID chyby:** BC36629</span><span class="sxs-lookup"><span data-stu-id="e1a2a-106">**Error ID:** BC36629</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e1a2a-107">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="e1a2a-107">To correct this error</span></span>  
  
-   <span data-ttu-id="e1a2a-108">Použití `As` klauzule deklarovat proměnnou jako s možnou hodnotou Null.</span><span class="sxs-lookup"><span data-stu-id="e1a2a-108">Use an `As` clause to declare the variable as nullable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1a2a-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e1a2a-109">See also</span></span>
- [<span data-ttu-id="e1a2a-110">Typy hodnot s povolenou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="e1a2a-110">Nullable Value Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [<span data-ttu-id="e1a2a-111">Odvození místního typu</span><span class="sxs-lookup"><span data-stu-id="e1a2a-111">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
