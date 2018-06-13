---
title: Pole deklarované jako řídicí proměnná cyklu typu for nelze deklarovat s počáteční velikostí.
ms.date: 07/20/2015
f1_keywords:
- vbc32039
- bc32039
helpviewer_keywords:
- BC32039
ms.assetid: 1d8b6560-c9eb-4b71-a038-24c6f5a5ce46
ms.openlocfilehash: f6cf397b1e76313ab399d5e39a43ae0263df619c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33587981"
---
# <a name="array-declared-as-for-loop-control-variable-cannot-be-declared-with-an-initial-size"></a><span data-ttu-id="8a1a2-102">Pole deklarované jako řídicí proměnná cyklu typu for nelze deklarovat s počáteční velikostí.</span><span class="sxs-lookup"><span data-stu-id="8a1a2-102">Array declared as for loop control variable cannot be declared with an initial size</span></span>
<span data-ttu-id="8a1a2-103">A `For Each` smyčky používá pole jako jeho *element* proměnné iterace ale inicializuje tohoto pole.</span><span class="sxs-lookup"><span data-stu-id="8a1a2-103">A `For Each` loop uses an array as its *element* iteration variable but initializes that array.</span></span>  
  
 <span data-ttu-id="8a1a2-104">Následující příkazy ukazují, jak může být generována této chybě.</span><span class="sxs-lookup"><span data-stu-id="8a1a2-104">The following statements show how this error can be generated.</span></span>  
  
```  
Dim arrayList As New List(Of Integer())  
For Each listElement() As Integer In arrayList  
For Each listElement(1) As Integer In arrayList  
```  
  
 <span data-ttu-id="8a1a2-105">První `For Each` příkaz je správný způsob, jak přístup prvky `arrayList`.</span><span class="sxs-lookup"><span data-stu-id="8a1a2-105">The first `For Each` statement is the correct way to access elements of `arrayList`.</span></span> <span data-ttu-id="8a1a2-106">Druhý `For Each` příkaz vygeneruje tuto chybu.</span><span class="sxs-lookup"><span data-stu-id="8a1a2-106">The second `For Each` statement generates this error.</span></span>  
  
 <span data-ttu-id="8a1a2-107">**ID chyby:** BC32039</span><span class="sxs-lookup"><span data-stu-id="8a1a2-107">**Error ID:** BC32039</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="8a1a2-108">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="8a1a2-108">To correct this error</span></span>  
  
-   <span data-ttu-id="8a1a2-109">Inicializace odebrání deklaraci *element* proměnné iterace.</span><span class="sxs-lookup"><span data-stu-id="8a1a2-109">Remove the initialization from the declaration of the *element* iteration variable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a1a2-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="8a1a2-110">See Also</span></span>  
 [<span data-ttu-id="8a1a2-111">Příkaz For...Next</span><span class="sxs-lookup"><span data-stu-id="8a1a2-111">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [<span data-ttu-id="8a1a2-112">Pole</span><span class="sxs-lookup"><span data-stu-id="8a1a2-112">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [<span data-ttu-id="8a1a2-113">Kolekce</span><span class="sxs-lookup"><span data-stu-id="8a1a2-113">Collections</span></span>](../../../standard/collections/index.md)
