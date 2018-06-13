---
title: 'Postupy: Vytvoření řetězce z pole znakových hodnot (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- examples [Visual Basic], arrays
- examples [Visual Basic], Char data type
ms.assetid: 69f94e85-d57c-4ccc-a62a-426e829f5c5e
ms.openlocfilehash: 104b329011d69e10a2926f31ce5d296759a3cce8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33647164"
---
# <a name="how-to-create-a-string-from-an-array-of-char-values-visual-basic"></a>Postupy: Vytvoření řetězce z pole znakových hodnot (Visual Basic)
Tento příklad vytvoří řetězec "abcd" z jednotlivých znaků.  
  
## <a name="example"></a>Příklad  
 [!code-vb[VbVbalrStrings#61](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-create-a-string-from-an-array-of-char-values_1.vb)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tato metoda nemá žádné zvláštní požadavky.  
  
 Syntaxe `"a"c`, kde jeden `c` následuje jednoho znaku v uvozovkách, se používá k vytvoření znak literálu.  
  
## <a name="robust-programming"></a>Robustní programování  
 Znaky Null (ekvivalentní `Chr(0)`) v řetězci vést k neočekávaným výsledkům při použití řetězec. Znak hodnoty null budou zahrnuty s řetězcem, ale v některých situacích se nezobrazí znaky následující znak hodnoty null.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.String>  
 [Datový typ Char](../../../../visual-basic/language-reference/data-types/char-data-type.md)  
 [Datové typy](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
