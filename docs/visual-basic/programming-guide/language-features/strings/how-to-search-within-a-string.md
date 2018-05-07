---
title: 'Postupy: Vyhledávání v řetězci (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], finding
- strings [Visual Basic], searching
- examples [Visual Basic], strings
ms.assetid: ae4c79e0-08ea-489f-bdb2-5eb6d355f284
ms.openlocfilehash: 08a005f2927a76c9b29c1ff0092ea8282188b2b2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-search-within-a-string-visual-basic"></a>Postupy: Vyhledávání v řetězci (Visual Basic)
Tento příklad volá <xref:System.String.IndexOf%2A> metodu <xref:System.String> objekt, který chcete nahlásit index prvního výskytu dílčí řetězec.  
  
## <a name="example"></a>Příklad  
 [!code-vb[VbVbalrStrings#71](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-search-within-a-string_1.vb)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   `Imports` Zadáním příkazu <xref:System> oboru názvů. Další informace najdete v tématu [příkaz Imports (Namespace .NET a typ)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
## <a name="robust-programming"></a>Robustní programování  
 <xref:System.String.IndexOf%2A> Metoda sestavy umístění první znak první výskyt dílčí řetězec. Index je založen na 0, což znamená, že první znak řetězec má index 0.  
  
 Pokud <xref:System.String.IndexOf%2A> nebyl nalezen dílčí řetězec, vrátí hodnotu -1.  
  
 <xref:System.String.IndexOf%2A> Metoda je malá a velká písmena a používá aktuální jazykovou verzi.  
  
 Pro optimální chyby řízení, můžete chtít uzavřete řetězec hledání v `Try` blokovat z [zkuste... Catch... Finally – příkaz](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) konstrukce.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.String.IndexOf%2A>  
 [Příkaz Try...Catch...Finally](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [Představení řetězců v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)  
 [Řetězce](../../../../visual-basic/programming-guide/language-features/strings/index.md)
