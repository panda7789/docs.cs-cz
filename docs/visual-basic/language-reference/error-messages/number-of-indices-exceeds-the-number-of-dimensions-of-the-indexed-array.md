---
title: Počet indexů překračuje počet rozměrů indexovaného pole.
ms.date: 07/20/2015
f1_keywords:
- bc30106
- vbc30106
helpviewer_keywords:
- BC30106
ms.assetid: 2c5363e1-62c2-4f5a-b675-c7337aeb363d
ms.openlocfilehash: 76cf0a997e9ad36ab4b5dfdc7c4bc29c57d309eb
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64665694"
---
# <a name="number-of-indices-exceeds-the-number-of-dimensions-of-the-indexed-array"></a>Počet indexů překračuje počet rozměrů indexovaného pole.
Počet indexů pro přístup k elementu pole musí být přesně stejné jako řád objektu array, to znamená, počet rozměrů deklarované pro něj.  
  
 **ID chyby:** BC30106  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Dokud celkový počet dolních indexů rovná řád objektu array, odeberte z odkazu na pole dolních indexů. Příklad:  
  
    ```vb  
    Dim gameBoard(3, 3) As String  
  
    ' Incorrect code. The array has two dimensions.  
    gameBoard(1, 1, 1) = "X"  
    gameBoard(2, 1, 1) = "O"  
  
    ' Correct code.  
    gameBoard(0, 0) = "X"  
    gameBoard(1, 0) = "O"  
    ```  
  
## <a name="see-also"></a>Viz také:

- [Pole](../../../visual-basic/programming-guide/language-features/arrays/index.md)
