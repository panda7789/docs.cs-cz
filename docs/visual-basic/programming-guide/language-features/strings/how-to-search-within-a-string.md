---
title: 'Postupy: Vyhledávání v řetězci (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], finding
- strings [Visual Basic], searching
- examples [Visual Basic], strings
ms.assetid: ae4c79e0-08ea-489f-bdb2-5eb6d355f284
ms.openlocfilehash: 57a3d9650ad78e1c8580fd46839c9a1cbc7794c9
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64665344"
---
# <a name="how-to-search-within-a-string-visual-basic"></a>Postupy: Vyhledávání v řetězci (Visual Basic)
Tento příklad příkladu volá <xref:System.String.IndexOf%2A> metoda <xref:System.String> objektu oznámit index prvního výskytu podřetězce.  
  
## <a name="example"></a>Příklad  
 [!code-vb[VbVbalrStrings#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#71)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- `Imports` Zadáním příkazu <xref:System> oboru názvů. Další informace najdete v tématu [příkaz Imports (Namespace .NET a typ)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
## <a name="robust-programming"></a>Robustní programování  
 <xref:System.String.IndexOf%2A> Metoda umístění prvního znaku prvního výskytu podřetězce sestav. Index je založen na 0, což znamená, že první znak řetězce má index 0.  
  
 Pokud <xref:System.String.IndexOf%2A> nebyl nalezen dílčí řetězec, vrátí hodnotu -1.  
  
 <xref:System.String.IndexOf%2A> Metoda velká a malá písmena a použije aktuální jazykové verze.  
  
 Pro řízení optimální chyb, můžete chtít uzavřít řetězec hledání v `Try` bloku [zkuste... Catch... Příkaz finally](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) konstrukce.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.String.IndexOf%2A>
- [Příkaz Try...Catch...Finally](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [Úvod do řetězců v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
- [Řetězce](../../../../visual-basic/programming-guide/language-features/strings/index.md)
