---
title: Byl očekáván inicializátor.
ms.date: 07/20/2015
f1_keywords:
- vbc30996
- bc30996
helpviewer_keywords:
- BC30996
ms.assetid: 6e183fe0-8888-43ed-a062-01571079455f
ms.openlocfilehash: 77cfeb57bc313ded2d2c4d5a0c59041c5c19f515
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58826077"
---
# <a name="initializer-expected"></a><span data-ttu-id="0c3f4-102">Byl očekáván inicializátor.</span><span class="sxs-lookup"><span data-stu-id="0c3f4-102">Initializer expected</span></span>
<span data-ttu-id="0c3f4-103">Pokusili jste se instanci třídy deklarovat pomocí inicializátoru objektu, ve kterém je prázdný, inicializační seznam, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="0c3f4-103">You have tried to declare an instance of a class by using an object initializer in which the initialization list is empty, as shown in the following example.</span></span>  
  
 `' Not valid.`  
  
 `' Dim aStudent As New Student With {}`  
  
 <span data-ttu-id="0c3f4-104">Aspoň jedno pole nebo vlastnost musí být inicializována v seznamu inicializátorů, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="0c3f4-104">At least one field or property must be initialized in the initializer list, as shown in the following example.</span></span>  
  
 `Dim aStudent As New Student With {.year = "Senior"}`  
  
 <span data-ttu-id="0c3f4-105">**ID chyby:** BC30996</span><span class="sxs-lookup"><span data-stu-id="0c3f4-105">**Error ID:** BC30996</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0c3f4-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="0c3f4-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="0c3f4-107">Inicializovat aspoň jedno pole nebo vlastnost v inicializátoru, nebo nepoužívejte inicializátoru objektu.</span><span class="sxs-lookup"><span data-stu-id="0c3f4-107">Initialize at least one field or property in the initializer, or do not use an object initializer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c3f4-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0c3f4-108">See also</span></span>

- [<span data-ttu-id="0c3f4-109">Inicializátory objektů: Pojmenované a anonymní typy</span><span class="sxs-lookup"><span data-stu-id="0c3f4-109">Object Initializers: Named and Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [<span data-ttu-id="0c3f4-110">Postupy: Deklarace objektu pomocí inicializátoru objektů</span><span class="sxs-lookup"><span data-stu-id="0c3f4-110">How to: Declare an Object by Using an Object Initializer</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)
