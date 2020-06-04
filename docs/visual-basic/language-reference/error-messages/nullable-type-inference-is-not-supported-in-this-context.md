---
title: V tomto kontextu není podporováno odvození typu s povolenou hodnotu Null.
ms.date: 07/20/2015
f1_keywords:
- vbc36629
- bc36629
helpviewer_keywords:
- BC36629
ms.assetid: 0a1e2dbc-d9a4-433d-9306-c5540782b81d
ms.openlocfilehash: 52e5391fbcf30a4dada4d64a0e810c900ea85806
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409384"
---
# <a name="nullable-type-inference-is-not-supported-in-this-context"></a><span data-ttu-id="498c1-102">V tomto kontextu není podporováno odvození typu s povolenou hodnotu Null.</span><span class="sxs-lookup"><span data-stu-id="498c1-102">Nullable type inference is not supported in this context</span></span>
<span data-ttu-id="498c1-103">Typy hodnot a struktury lze deklarovat s možnou hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="498c1-103">Value types and structures can be declared nullable.</span></span>  
  
```vb  
Dim a? As Integer  
Dim b As Integer?  
```  
  
 <span data-ttu-id="498c1-104">Nemůžete však použít deklaraci Nullable v kombinaci s odvozením typu.</span><span class="sxs-lookup"><span data-stu-id="498c1-104">However, you cannot use the nullable declaration in combination with type inference.</span></span> <span data-ttu-id="498c1-105">Následující příklady způsobují tuto chybu.</span><span class="sxs-lookup"><span data-stu-id="498c1-105">The following examples cause this error.</span></span>  
  
```vb  
' Not valid.  
' Dim c? = 10  
' Dim d? = a  
```  
  
 <span data-ttu-id="498c1-106">**ID chyby:** BC36629</span><span class="sxs-lookup"><span data-stu-id="498c1-106">**Error ID:** BC36629</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="498c1-107">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="498c1-107">To correct this error</span></span>  
  
- <span data-ttu-id="498c1-108">Použijte `As` klauzuli pro deklaraci proměnné jako typ hodnoty s možnou hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="498c1-108">Use an `As` clause to declare the variable as a nullable value type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="498c1-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="498c1-109">See also</span></span>

- [<span data-ttu-id="498c1-110">Typy hodnot s možnou hodnotou null</span><span class="sxs-lookup"><span data-stu-id="498c1-110">Nullable Value Types</span></span>](../../programming-guide/language-features/data-types/nullable-value-types.md)
- [<span data-ttu-id="498c1-111">Odvození místního typu</span><span class="sxs-lookup"><span data-stu-id="498c1-111">Local Type Inference</span></span>](../../programming-guide/language-features/variables/local-type-inference.md)
