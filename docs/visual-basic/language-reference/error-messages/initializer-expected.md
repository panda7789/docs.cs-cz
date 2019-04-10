---
title: Byl očekáván inicializátor.
ms.date: 07/20/2015
f1_keywords:
- vbc30996
- bc30996
helpviewer_keywords:
- BC30996
ms.assetid: 6e183fe0-8888-43ed-a062-01571079455f
ms.openlocfilehash: 0795fdc1c4b177e13979d7555cd7588217b8cb4c
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59334962"
---
# <a name="initializer-expected"></a><span data-ttu-id="ad59b-102">Byl očekáván inicializátor.</span><span class="sxs-lookup"><span data-stu-id="ad59b-102">Initializer expected</span></span>
<span data-ttu-id="ad59b-103">Pokusili jste se instanci třídy deklarovat pomocí inicializátoru objektu, ve kterém je prázdný, inicializační seznam, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="ad59b-103">You have tried to declare an instance of a class by using an object initializer in which the initialization list is empty, as shown in the following example.</span></span>  
  
 `' Not valid.`  
  
 `' Dim aStudent As New Student With {}`  
  
 <span data-ttu-id="ad59b-104">Aspoň jedno pole nebo vlastnost musí být inicializována v seznamu inicializátorů, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="ad59b-104">At least one field or property must be initialized in the initializer list, as shown in the following example.</span></span>  
  
 `Dim aStudent As New Student With {.year = "Senior"}`  
  
 <span data-ttu-id="ad59b-105">**ID chyby:** BC30996</span><span class="sxs-lookup"><span data-stu-id="ad59b-105">**Error ID:** BC30996</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ad59b-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="ad59b-106">To correct this error</span></span>  
  
1. <span data-ttu-id="ad59b-107">Inicializovat aspoň jedno pole nebo vlastnost v inicializátoru, nebo nepoužívejte inicializátoru objektu.</span><span class="sxs-lookup"><span data-stu-id="ad59b-107">Initialize at least one field or property in the initializer, or do not use an object initializer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad59b-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ad59b-108">See also</span></span>

- [<span data-ttu-id="ad59b-109">Inicializátory objektů: Pojmenované a anonymní typy</span><span class="sxs-lookup"><span data-stu-id="ad59b-109">Object Initializers: Named and Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [<span data-ttu-id="ad59b-110">Postupy: Deklarace objektu pomocí inicializátoru objektu</span><span class="sxs-lookup"><span data-stu-id="ad59b-110">How to: Declare an Object by Using an Object Initializer</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)
