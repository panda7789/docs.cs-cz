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
ms.openlocfilehash: f24c0625058dbd960411d5981b4e98e0e9422b99
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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
 [Kolekce](../../concepts/collections.md)  
 [Příkaz For Each...Next](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)
