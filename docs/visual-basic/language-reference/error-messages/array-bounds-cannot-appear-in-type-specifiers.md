---
title: Indexy pole nemohou být použity ve specifikátorech typu.
ms.date: 07/20/2015
f1_keywords:
- vbc30638
- bc30638
helpviewer_keywords:
- BC30638
ms.assetid: 93b654f4-70fa-4a48-baed-ffae42075550
ms.openlocfilehash: f20ed883005641082eb89e2effa5221594910ffe
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58838778"
---
# <a name="array-bounds-cannot-appear-in-type-specifiers"></a><span data-ttu-id="4c0e6-102">Indexy pole nemohou být použity ve specifikátorech typu.</span><span class="sxs-lookup"><span data-stu-id="4c0e6-102">Array bounds cannot appear in type specifiers</span></span>
<span data-ttu-id="4c0e6-103">Velikost pole nejde použít deklaraci jako součást v datovém specifikátoru typu.</span><span class="sxs-lookup"><span data-stu-id="4c0e6-103">Array sizes cannot be declared as part of a data type specifier.</span></span>  
  
 <span data-ttu-id="4c0e6-104">**ID chyby:** BC30638</span><span class="sxs-lookup"><span data-stu-id="4c0e6-104">**Error ID:** BC30638</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="4c0e6-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="4c0e6-105">To correct this error</span></span>  
  
-   <span data-ttu-id="4c0e6-106">Určete velikost pole, hned za název proměnné namísto velikost pole za typem, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="4c0e6-106">Specify the size of the array immediately following the variable name instead of placing the array size after the type, as shown in the following example.</span></span>  
  
    ```  
    Dim Array(8) As Integer   
    ```  
  
-   <span data-ttu-id="4c0e6-107">Definování pole a inicializujte ji s požadovaný počtem elementů, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="4c0e6-107">Define an array and initialize it with the desired number of elements, as shown in the following example.</span></span>  
  
    ```  
    Dim Array2() As Integer = New Integer(8) {}  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="4c0e6-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4c0e6-108">See also</span></span>

- [<span data-ttu-id="4c0e6-109">Pole</span><span class="sxs-lookup"><span data-stu-id="4c0e6-109">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)
