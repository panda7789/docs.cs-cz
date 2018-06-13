---
title: V tomto kontextu není podporováno odvození typu s povolenou hodnotu Null.
ms.date: 07/20/2015
f1_keywords:
- vbc36629
- bc36629
helpviewer_keywords:
- BC36629
ms.assetid: 0a1e2dbc-d9a4-433d-9306-c5540782b81d
ms.openlocfilehash: ea531c7be676e940a263b019a66cc80cf280a772
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33593188"
---
# <a name="nullable-type-inference-is-not-supported-in-this-context"></a><span data-ttu-id="feb03-102">V tomto kontextu není podporováno odvození typu s povolenou hodnotu Null.</span><span class="sxs-lookup"><span data-stu-id="feb03-102">Nullable type inference is not supported in this context</span></span>
<span data-ttu-id="feb03-103">Typy hodnot a struktury lze deklarovat s možnou hodnotou Null.</span><span class="sxs-lookup"><span data-stu-id="feb03-103">Value types and structures can be declared nullable.</span></span>  
  
```vb  
Dim a? As Integer  
Dim b As Integer?  
```  
  
 <span data-ttu-id="feb03-104">S možnou hodnotou Null deklarace však nelze použít v kombinaci s odvození typu.</span><span class="sxs-lookup"><span data-stu-id="feb03-104">However, you cannot use the nullable declaration in combination with type inference.</span></span> <span data-ttu-id="feb03-105">Následující příklady příčinou této chyby.</span><span class="sxs-lookup"><span data-stu-id="feb03-105">The following examples cause this error.</span></span>  
  
```vb  
' Not valid.  
' Dim c? = 10  
' Dim d? = a  
```  
  
 <span data-ttu-id="feb03-106">**ID chyby:** BC36629</span><span class="sxs-lookup"><span data-stu-id="feb03-106">**Error ID:** BC36629</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="feb03-107">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="feb03-107">To correct this error</span></span>  
  
-   <span data-ttu-id="feb03-108">Použijte `As` klauzule deklarovat proměnnou jako s možnou hodnotou Null.</span><span class="sxs-lookup"><span data-stu-id="feb03-108">Use an `As` clause to declare the variable as nullable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="feb03-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="feb03-109">See Also</span></span>  
 [<span data-ttu-id="feb03-110">Typy hodnot s povolenou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="feb03-110">Nullable Value Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)  
 [<span data-ttu-id="feb03-111">Odvození místního typu</span><span class="sxs-lookup"><span data-stu-id="feb03-111">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
