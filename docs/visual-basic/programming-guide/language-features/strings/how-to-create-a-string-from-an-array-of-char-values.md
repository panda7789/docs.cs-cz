---
title: 'Postupy: Vytvoření řetězce z pole znakových hodnot'
ms.date: 07/20/2015
helpviewer_keywords:
- examples [Visual Basic], arrays
- examples [Visual Basic], Char data type
ms.assetid: 69f94e85-d57c-4ccc-a62a-426e829f5c5e
ms.openlocfilehash: 03138a851afc55f735cc66edeb345817428a0452
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344389"
---
# <a name="how-to-create-a-string-from-an-array-of-char-values-visual-basic"></a>Postupy: Vytvoření řetězce z pole znakových hodnot (Visual Basic)
Tento příklad vytvoří řetězec "abcd" z jednotlivých znaků.  
  
## <a name="example"></a>Příklad  
 [!code-vb[VbVbalrStrings#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#61)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tato metoda nemá žádné zvláštní požadavky.  
  
 Syntaxe `"a"c`, kde jedna `c` sleduje jeden znak v uvozovkách, slouží k vytvoření znakového literálu.  
  
## <a name="robust-programming"></a>Robustní programování  
 Znaky null (ekvivalentní `Chr(0)`) v řetězci mají za následek neočekávané výsledky při použití řetězce. Znak null bude zahrnut spolu s řetězcem, ale v některých situacích se nezobrazí znaky, které následují za znakem null.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.String>
- [Datový typ Char](../../../../visual-basic/language-reference/data-types/char-data-type.md)
- [Datové typy](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
