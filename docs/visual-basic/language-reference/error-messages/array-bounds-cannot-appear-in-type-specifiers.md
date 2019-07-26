---
title: Indexy pole nemohou být použity ve specifikátorech typu.
ms.date: 07/20/2015
f1_keywords:
- vbc30638
- bc30638
helpviewer_keywords:
- BC30638
ms.assetid: 93b654f4-70fa-4a48-baed-ffae42075550
ms.openlocfilehash: 951f710160ae1023671773c21c73946f5ae94c2b
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512765"
---
# <a name="array-bounds-cannot-appear-in-type-specifiers"></a><span data-ttu-id="eacbc-102">Indexy pole nemohou být použity ve specifikátorech typu.</span><span class="sxs-lookup"><span data-stu-id="eacbc-102">Array bounds cannot appear in type specifiers</span></span>

<span data-ttu-id="eacbc-103">Velikosti pole nelze deklarovat jako součást specifikátoru datového typu.</span><span class="sxs-lookup"><span data-stu-id="eacbc-103">Array sizes cannot be declared as part of a data type specifier.</span></span>

<span data-ttu-id="eacbc-104">**ID chyby:** BC30638</span><span class="sxs-lookup"><span data-stu-id="eacbc-104">**Error ID:** BC30638</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="eacbc-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="eacbc-105">To correct this error</span></span>

- <span data-ttu-id="eacbc-106">Určete velikost pole bezprostředně za názvem proměnné namísto umístění velikosti pole za typ, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="eacbc-106">Specify the size of the array immediately following the variable name instead of placing the array size after the type, as shown in the following example.</span></span>

  ```vb
  Dim Array(8) As Integer
  ```

- <span data-ttu-id="eacbc-107">Definujte pole a inicializujte ho s požadovaným počtem prvků, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="eacbc-107">Define an array and initialize it with the desired number of elements, as shown in the following example.</span></span>

  ```vb
  Dim Array2() As Integer = New Integer(8) {}
  ```

## <a name="see-also"></a><span data-ttu-id="eacbc-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="eacbc-108">See also</span></span>

- [<span data-ttu-id="eacbc-109">Pole</span><span class="sxs-lookup"><span data-stu-id="eacbc-109">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)
