---
title: Indexy pole nemohou být použity ve specifikátorech typu.
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30638
- bc30638
helpviewer_keywords:
- BC30638
ms.assetid: 93b654f4-70fa-4a48-baed-ffae42075550
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 770f86ca960110965b6917a22d284678ff8b6f8c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="array-bounds-cannot-appear-in-type-specifiers"></a><span data-ttu-id="d20ae-102">Indexy pole nemohou být použity ve specifikátorech typu.</span><span class="sxs-lookup"><span data-stu-id="d20ae-102">Array bounds cannot appear in type specifiers</span></span>
<span data-ttu-id="d20ae-103">Velikosti pole nelze deklarovat jako součást specifikátor typu data.</span><span class="sxs-lookup"><span data-stu-id="d20ae-103">Array sizes cannot be declared as part of a data type specifier.</span></span>  
  
 <span data-ttu-id="d20ae-104">**ID chyby:** BC30638</span><span class="sxs-lookup"><span data-stu-id="d20ae-104">**Error ID:** BC30638</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d20ae-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="d20ae-105">To correct this error</span></span>  
  
-   <span data-ttu-id="d20ae-106">Zadejte velikost pole hned za název proměnné namísto velikost pole po typu, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="d20ae-106">Specify the size of the array immediately following the variable name instead of placing the array size after the type, as shown in the following example.</span></span>  
  
    ```  
    Dim Array(8) As Integer   
    ```  
  
-   <span data-ttu-id="d20ae-107">Zadejte pole a inicializace její požadovaný počet elementů, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="d20ae-107">Define an array and initialize it with the desired number of elements, as shown in the following example.</span></span>  
  
    ```  
    Dim Array2() As Integer = New Integer(8) {}  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="d20ae-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="d20ae-108">See Also</span></span>  
 [<span data-ttu-id="d20ae-109">Pole</span><span class="sxs-lookup"><span data-stu-id="d20ae-109">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)
