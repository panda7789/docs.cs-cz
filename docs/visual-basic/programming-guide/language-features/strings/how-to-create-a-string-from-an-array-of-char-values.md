---
title: "Postupy: Vytvoření řetězce z pole znakových hodnot (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- examples [Visual Basic], arrays
- examples [Visual Basic], Char data type
ms.assetid: 69f94e85-d57c-4ccc-a62a-426e829f5c5e
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 06e5c6923c26f3cb84b38475d6680523853d727d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
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
 [Char – datový typ](../../../../visual-basic/language-reference/data-types/char-data-type.md)  
 [Datové typy](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
