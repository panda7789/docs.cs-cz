---
title: Indexy pole nemohou být použity ve specifikátorech typu.
ms.date: 07/20/2015
f1_keywords:
- vbc30638
- bc30638
helpviewer_keywords:
- BC30638
ms.assetid: 93b654f4-70fa-4a48-baed-ffae42075550
ms.openlocfilehash: 50e1cd0e41da467a9e816c8e5d64d09a36923d65
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64665739"
---
# <a name="array-bounds-cannot-appear-in-type-specifiers"></a><span data-ttu-id="61595-102">Indexy pole nemohou být použity ve specifikátorech typu.</span><span class="sxs-lookup"><span data-stu-id="61595-102">Array bounds cannot appear in type specifiers</span></span>
<span data-ttu-id="61595-103">Velikost pole nejde použít deklaraci jako součást v datovém specifikátoru typu.</span><span class="sxs-lookup"><span data-stu-id="61595-103">Array sizes cannot be declared as part of a data type specifier.</span></span>  
  
 <span data-ttu-id="61595-104">**ID chyby:** BC30638</span><span class="sxs-lookup"><span data-stu-id="61595-104">**Error ID:** BC30638</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="61595-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="61595-105">To correct this error</span></span>  
  
- <span data-ttu-id="61595-106">Určete velikost pole, hned za název proměnné namísto velikost pole za typem, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="61595-106">Specify the size of the array immediately following the variable name instead of placing the array size after the type, as shown in the following example.</span></span>  
  
    ```  
    Dim Array(8) As Integer   
    ```  
  
- <span data-ttu-id="61595-107">Definování pole a inicializujte ji s požadovaný počtem elementů, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="61595-107">Define an array and initialize it with the desired number of elements, as shown in the following example.</span></span>  
  
    ```  
    Dim Array2() As Integer = New Integer(8) {}  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="61595-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="61595-108">See also</span></span>

- [<span data-ttu-id="61595-109">Pole</span><span class="sxs-lookup"><span data-stu-id="61595-109">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)
