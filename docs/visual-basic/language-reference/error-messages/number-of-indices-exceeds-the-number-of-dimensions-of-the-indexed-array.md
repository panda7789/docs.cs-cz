---
title: "Počet indexů překračuje počet rozměrů indexovaného pole."
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30106
- vbc30106
helpviewer_keywords: BC30106
ms.assetid: 2c5363e1-62c2-4f5a-b675-c7337aeb363d
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8fdf031734d441daca2073925f6d45d6ba9f1f52
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="number-of-indices-exceeds-the-number-of-dimensions-of-the-indexed-array"></a>Počet indexů překračuje počet rozměrů indexovaného pole.
Počet indexů použila k přístupu k elementu pole musí být přesně stejný jako pořadí pole, který je počet dimenzí deklarovaný pro něj.  
  
 **ID chyby:** BC30106  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Odeberte dolní indexy z odkaz na pole, dokud celkový počet dolní indexy rovná pořadí pole. Příklad:  
  
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
 [Pole](../../../visual-basic/programming-guide/language-features/arrays/index.md)
