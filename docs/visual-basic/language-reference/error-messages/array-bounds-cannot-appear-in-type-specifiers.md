---
title: Indexy pole nemohou být použity ve specifikátorech typu.
ms.date: 07/20/2015
f1_keywords:
- vbc30638
- bc30638
helpviewer_keywords:
- BC30638
ms.assetid: 93b654f4-70fa-4a48-baed-ffae42075550
ms.openlocfilehash: 45787db51de562f2266c587fd2bb15ef29ebefbe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="array-bounds-cannot-appear-in-type-specifiers"></a>Indexy pole nemohou být použity ve specifikátorech typu.
Velikosti pole nelze deklarovat jako součást specifikátor typu data.  
  
 **ID chyby:** BC30638  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Zadejte velikost pole hned za název proměnné namísto velikost pole po typu, jak je znázorněno v následujícím příkladu.  
  
    ```  
    Dim Array(8) As Integer   
    ```  
  
-   Zadejte pole a inicializace její požadovaný počet elementů, jak je znázorněno v následujícím příkladu.  
  
    ```  
    Dim Array2() As Integer = New Integer(8) {}  
    ```  
  
## <a name="see-also"></a>Viz také  
 [Pole](../../../visual-basic/programming-guide/language-features/arrays/index.md)
