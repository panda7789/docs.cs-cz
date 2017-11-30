---
title: "Postupy: Řazení pole v jazyce Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: Array.Sort
helpviewer_keywords:
- arrays [Visual Basic], sorting
- examples [Visual Basic], arrays
ms.assetid: 9289aeaa-9626-4698-94a7-1d1fd3702b87
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 310c2dacb384de49c80073840c6c58d37f3937d9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-sort-an-array-in-visual-basic"></a>Postupy: Řazení pole v jazyce Visual Basic
Tento příklad deklaruje pole `String` objektů s názvem `zooAnimals`, naplní jej a abecedně seřadí.  
  
## <a name="example"></a>Příklad  
  
```  
Private Sub sortAnimals()  
    Dim zooAnimals(2) As String  
    zooAnimals(0) = "lion"  
    zooAnimals(1) = "turtle"  
    zooAnimals(2) = "ostrich"  
    Array.Sort(zooAnimals)  
End Sub  
```  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Přístup k Mscorlib.dll a <xref:System> oboru názvů.  
  
## <a name="robust-programming"></a>Robustní programování  
 Následující podmínky mohou způsobit výjimku:  
  
-   Pole je prázdné (<xref:System.ArgumentNullException> třídy)  
  
-   Pole je multidimenzionální (<xref:System.RankException> třídy)  
  
-   Jeden či více elementů pole neimplementují <xref:System.IComparable> rozhraní (<xref:System.InvalidOperationException> třídy)  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Array.Sort%2A?displayProperty=nameWithType>  
 [Pole](../../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [Řešení potíží s poli](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)  
 [Kolekce](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b)  
 [Pro každou... Next – příkaz](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)
