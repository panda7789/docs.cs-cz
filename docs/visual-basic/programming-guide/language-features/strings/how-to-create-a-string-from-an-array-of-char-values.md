---
title: 'Postupy: Vytvoření řetězce z pole znakových hodnot'
ms.date: 07/20/2015
helpviewer_keywords:
- examples [Visual Basic], arrays
- examples [Visual Basic], Char data type
ms.assetid: 69f94e85-d57c-4ccc-a62a-426e829f5c5e
ms.openlocfilehash: d9ec897467f0caac0afc089a028516c0316a2bda
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410590"
---
# <a name="how-to-create-a-string-from-an-array-of-char-values-visual-basic"></a>Postupy: Vytvoření řetězce z pole znakových hodnot (Visual Basic)
Tento příklad vytvoří řetězec "abcd" z jednotlivých znaků.  
  
## <a name="example"></a>Příklad  
 [!code-vb[VbVbalrStrings#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#61)]  
  
## <a name="compile-the-code"></a>Kompilovat kód  
 Tato metoda nemá žádné zvláštní požadavky.  
  
 Syntaxe `"a"c` , kde jedna následuje za `c` jedním znakem v uvozovkách, se používá k vytvoření znakového literálu.  
  
## <a name="robust-programming"></a>Robustní programování  
 Znaky null (stejné jako `Chr(0)` ) v řetězci mají za následek neočekávané výsledky při použití řetězce. Znak null bude zahrnut spolu s řetězcem, ale v některých situacích se nezobrazí znaky, které následují za znakem null.  
  
## <a name="see-also"></a>Viz také

- <xref:System.String>
- [Char – datový typ](../../../language-reference/data-types/char-data-type.md)
- [Datové typy](../data-types/index.md)
