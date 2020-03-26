---
title: V tomto kontextu není podporováno odvození typu s povolenou hodnotu Null.
ms.date: 07/20/2015
f1_keywords:
- vbc36629
- bc36629
helpviewer_keywords:
- BC36629
ms.assetid: 0a1e2dbc-d9a4-433d-9306-c5540782b81d
ms.openlocfilehash: 42bde0b1843e52bbc16118bb056ade791591904e
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249497"
---
# <a name="nullable-type-inference-is-not-supported-in-this-context"></a><span data-ttu-id="a257c-102">V tomto kontextu není podporováno odvození typu s povolenou hodnotu Null.</span><span class="sxs-lookup"><span data-stu-id="a257c-102">Nullable type inference is not supported in this context</span></span>
<span data-ttu-id="a257c-103">Typy hodnot a struktury lze deklarovat s platností.</span><span class="sxs-lookup"><span data-stu-id="a257c-103">Value types and structures can be declared nullable.</span></span>  
  
```vb  
Dim a? As Integer  
Dim b As Integer?  
```  
  
 <span data-ttu-id="a257c-104">Však nelze použít deklaraci s možnou hodnotou null v kombinaci s odvozením typu.</span><span class="sxs-lookup"><span data-stu-id="a257c-104">However, you cannot use the nullable declaration in combination with type inference.</span></span> <span data-ttu-id="a257c-105">Následující příklady způsobit tuto chybu.</span><span class="sxs-lookup"><span data-stu-id="a257c-105">The following examples cause this error.</span></span>  
  
```vb  
' Not valid.  
' Dim c? = 10  
' Dim d? = a  
```  
  
 <span data-ttu-id="a257c-106">**ID chyby:** BC36629</span><span class="sxs-lookup"><span data-stu-id="a257c-106">**Error ID:** BC36629</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a257c-107">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="a257c-107">To correct this error</span></span>  
  
- <span data-ttu-id="a257c-108">Pomocí `As` klauzule deklarujte proměnnou jako typ hodnoty s možnou hodnotou s hodnotou, kterou lze použít.</span><span class="sxs-lookup"><span data-stu-id="a257c-108">Use an `As` clause to declare the variable as a nullable value type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a257c-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="a257c-109">See also</span></span>

- [<span data-ttu-id="a257c-110">Typy hodnot s povolenou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="a257c-110">Nullable Value Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [<span data-ttu-id="a257c-111">Odvození místního typu</span><span class="sxs-lookup"><span data-stu-id="a257c-111">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
