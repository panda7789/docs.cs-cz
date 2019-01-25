---
title: Indexy pole nemohou být použity ve specifikátorech typu.
ms.date: 07/20/2015
f1_keywords:
- vbc30638
- bc30638
helpviewer_keywords:
- BC30638
ms.assetid: 93b654f4-70fa-4a48-baed-ffae42075550
ms.openlocfilehash: f31aea5a98233c8f262a77ba5c99eea389bc33ee
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54715436"
---
# <a name="array-bounds-cannot-appear-in-type-specifiers"></a>Indexy pole nemohou být použity ve specifikátorech typu.
Velikost pole nejde použít deklaraci jako součást v datovém specifikátoru typu.  
  
 **ID chyby:** BC30638  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Určete velikost pole, hned za název proměnné namísto velikost pole za typem, jak je znázorněno v následujícím příkladu.  
  
    ```  
    Dim Array(8) As Integer   
    ```  
  
-   Definování pole a inicializujte ji s požadovaný počtem elementů, jak je znázorněno v následujícím příkladu.  
  
    ```  
    Dim Array2() As Integer = New Integer(8) {}  
    ```  
  
## <a name="see-also"></a>Viz také:
- [Pole](../../../visual-basic/programming-guide/language-features/arrays/index.md)
