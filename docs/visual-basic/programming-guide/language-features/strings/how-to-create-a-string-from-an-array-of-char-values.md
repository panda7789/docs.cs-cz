---
title: 'Postupy: Vytvoření řetězce z pole znakových hodnot (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- examples [Visual Basic], arrays
- examples [Visual Basic], Char data type
ms.assetid: 69f94e85-d57c-4ccc-a62a-426e829f5c5e
ms.openlocfilehash: 1f72cb86ffa38dc929062fab2f5592a781f2de27
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62054052"
---
# <a name="how-to-create-a-string-from-an-array-of-char-values-visual-basic"></a>Postupy: Vytvoření řetězce z pole znakových hodnot (Visual Basic)
Tento příklad vytvoří řetězec "abcd" z jednotlivých znaků.  
  
## <a name="example"></a>Příklad  
 [!code-vb[VbVbalrStrings#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#61)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tato metoda nemá žádné zvláštní požadavky.  
  
 Syntaxe `"a"c`, kde jeden `c` následující jeden znak do uvozovek, je použít k vytvoření znak literálu.  
  
## <a name="robust-programming"></a>Robustní programování  
 Znaky s hodnotou Null (ekvivalentní `Chr(0)`) v řetězci vést k neočekávaným výsledkům při použití řetězce. Znak null bude součástí řetězce, ale v některých situacích se nezobrazí znaky následující po znaku null.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.String>
- [Datový typ Char](../../../../visual-basic/language-reference/data-types/char-data-type.md)
- [Datové typy](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
