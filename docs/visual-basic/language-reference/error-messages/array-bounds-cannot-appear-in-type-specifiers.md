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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61935353"
---
# <a name="array-bounds-cannot-appear-in-type-specifiers"></a>Indexy pole nemohou být použity ve specifikátorech typu.
Velikost pole nejde použít deklaraci jako součást v datovém specifikátoru typu.  
  
 **ID chyby:** BC30638  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Určete velikost pole, hned za název proměnné namísto velikost pole za typem, jak je znázorněno v následujícím příkladu.  
  
    ```  
    Dim Array(8) As Integer   
    ```  
  
- Definování pole a inicializujte ji s požadovaný počtem elementů, jak je znázorněno v následujícím příkladu.  
  
    ```  
    Dim Array2() As Integer = New Integer(8) {}  
    ```  
  
## <a name="see-also"></a>Viz také:

- [Pole](../../../visual-basic/programming-guide/language-features/arrays/index.md)
