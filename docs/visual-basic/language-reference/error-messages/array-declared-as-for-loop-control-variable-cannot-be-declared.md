---
title: Pole deklarované jako řídicí proměnná cyklu typu for nelze deklarovat s počáteční velikostí.
ms.date: 07/20/2015
f1_keywords:
- vbc32039
- bc32039
helpviewer_keywords:
- BC32039
ms.assetid: 1d8b6560-c9eb-4b71-a038-24c6f5a5ce46
ms.openlocfilehash: bee3bcd3701945f5cf77f6761defc8be77acf49f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58843575"
---
# <a name="array-declared-as-for-loop-control-variable-cannot-be-declared-with-an-initial-size"></a><span data-ttu-id="c575c-102">Pole deklarované jako řídicí proměnná cyklu typu for nelze deklarovat s počáteční velikostí.</span><span class="sxs-lookup"><span data-stu-id="c575c-102">Array declared as for loop control variable cannot be declared with an initial size</span></span>
<span data-ttu-id="c575c-103">A `For Each` smyčky používá pole jako jeho *element* iterační proměnné ale inicializuje dané pole.</span><span class="sxs-lookup"><span data-stu-id="c575c-103">A `For Each` loop uses an array as its *element* iteration variable but initializes that array.</span></span>  
  
 <span data-ttu-id="c575c-104">Následující příkazy ukazují, jak můžete tuto chybu vygeneruje.</span><span class="sxs-lookup"><span data-stu-id="c575c-104">The following statements show how this error can be generated.</span></span>  
  
```  
Dim arrayList As New List(Of Integer())  
For Each listElement() As Integer In arrayList  
For Each listElement(1) As Integer In arrayList  
```  
  
 <span data-ttu-id="c575c-105">První `For Each` příkaz je správný způsob, jak přístup prvky `arrayList`.</span><span class="sxs-lookup"><span data-stu-id="c575c-105">The first `For Each` statement is the correct way to access elements of `arrayList`.</span></span> <span data-ttu-id="c575c-106">Druhá `For Each` příkaz vygeneruje tuto chybu.</span><span class="sxs-lookup"><span data-stu-id="c575c-106">The second `For Each` statement generates this error.</span></span>  
  
 <span data-ttu-id="c575c-107">**ID chyby:** BC32039</span><span class="sxs-lookup"><span data-stu-id="c575c-107">**Error ID:** BC32039</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c575c-108">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="c575c-108">To correct this error</span></span>  
  
-   <span data-ttu-id="c575c-109">Odebrání inicializace deklarace *element* proměnné iterace.</span><span class="sxs-lookup"><span data-stu-id="c575c-109">Remove the initialization from the declaration of the *element* iteration variable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c575c-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c575c-110">See also</span></span>

- [<span data-ttu-id="c575c-111">Příkaz For...Next</span><span class="sxs-lookup"><span data-stu-id="c575c-111">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="c575c-112">Pole</span><span class="sxs-lookup"><span data-stu-id="c575c-112">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="c575c-113">Kolekce</span><span class="sxs-lookup"><span data-stu-id="c575c-113">Collections</span></span>](../../../standard/collections/index.md)
