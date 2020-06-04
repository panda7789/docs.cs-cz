---
title: Počet indexů překračuje počet rozměrů indexovaného pole.
ms.date: 07/20/2015
f1_keywords:
- bc30106
- vbc30106
helpviewer_keywords:
- BC30106
ms.assetid: 2c5363e1-62c2-4f5a-b675-c7337aeb363d
ms.openlocfilehash: 4d8ffd2c4ad0a386053ced0f98503969723c7168
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409371"
---
# <a name="number-of-indices-exceeds-the-number-of-dimensions-of-the-indexed-array"></a>Počet indexů překračuje počet rozměrů indexovaného pole.
Počet indexů použitých pro přístup k prvku pole musí být přesně stejný jako rozměr pole, tj. počet dimenzí, které jsou pro něj deklarovány.  
  
 **ID chyby:** BC30106  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Odeberte dolní indexy z odkazu na pole, dokud celkový počet dolních indexů nerovná rozměru pole. Příklad:  
  
    ```vb  
    Dim gameBoard(3, 3) As String  
  
    ' Incorrect code. The array has two dimensions.  
    gameBoard(1, 1, 1) = "X"  
    gameBoard(2, 1, 1) = "O"  
  
    ' Correct code.  
    gameBoard(0, 0) = "X"  
    gameBoard(1, 0) = "O"  
    ```  
  
## <a name="see-also"></a>Viz také

- [Pole](../../programming-guide/language-features/arrays/index.md)
