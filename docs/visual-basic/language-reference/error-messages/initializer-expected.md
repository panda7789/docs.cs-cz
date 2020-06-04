---
title: Byl očekáván inicializátor.
ms.date: 07/20/2015
f1_keywords:
- vbc30996
- bc30996
helpviewer_keywords:
- BC30996
ms.assetid: 6e183fe0-8888-43ed-a062-01571079455f
ms.openlocfilehash: 13fa8917f228661fc44f5e0920d91c596e250c38
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402834"
---
# <a name="initializer-expected"></a><span data-ttu-id="b0a10-102">Byl očekáván inicializátor.</span><span class="sxs-lookup"><span data-stu-id="b0a10-102">Initializer expected</span></span>
<span data-ttu-id="b0a10-103">Pokusili jste se deklarovat instanci třídy pomocí inicializátoru objektu, ve kterém je seznam inicializace prázdný, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="b0a10-103">You have tried to declare an instance of a class by using an object initializer in which the initialization list is empty, as shown in the following example.</span></span>  
  
 `' Not valid.`  
  
 `' Dim aStudent As New Student With {}`  
  
 <span data-ttu-id="b0a10-104">Alespoň jedno pole nebo vlastnost musí být inicializovány v seznamu inicializátorů, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="b0a10-104">At least one field or property must be initialized in the initializer list, as shown in the following example.</span></span>  
  
 `Dim aStudent As New Student With {.year = "Senior"}`  
  
 <span data-ttu-id="b0a10-105">**ID chyby:** BC30996</span><span class="sxs-lookup"><span data-stu-id="b0a10-105">**Error ID:** BC30996</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b0a10-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="b0a10-106">To correct this error</span></span>  
  
1. <span data-ttu-id="b0a10-107">Inicializujte alespoň jedno pole nebo vlastnost v inicializátoru, nebo nepoužívejte inicializátor objektu.</span><span class="sxs-lookup"><span data-stu-id="b0a10-107">Initialize at least one field or property in the initializer, or do not use an object initializer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0a10-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="b0a10-108">See also</span></span>

- [<span data-ttu-id="b0a10-109">Inicializátory objektů: pojmenované a anonymní typy</span><span class="sxs-lookup"><span data-stu-id="b0a10-109">Object Initializers: Named and Anonymous Types</span></span>](../../programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [<span data-ttu-id="b0a10-110">Postupy: Deklarace objektu pomocí inicializátoru objektu</span><span class="sxs-lookup"><span data-stu-id="b0a10-110">How to: Declare an Object by Using an Object Initializer</span></span>](../../programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)
