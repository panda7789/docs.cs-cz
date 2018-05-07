---
title: 'Postupy: Ověření řetězců, které představují data nebo časy (Visual Basic).'
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], validating
- String data type [Visual Basic], validation
ms.assetid: ae7d4b29-3436-4032-bdbf-4650eb1c8e19
ms.openlocfilehash: 411c8517783421b2472c3e4aa77287f8252f179b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-validate-strings-that-represent-dates-or-times-visual-basic"></a>Postupy: Ověření řetězců, které představují data nebo časy (Visual Basic).
Následující příklad kódu nastaví `Boolean` hodnotu, která určuje, zda řetězec reprezentuje platné datum nebo čas.  
  
## <a name="example"></a>Příklad  
 [!code-vb[VbVbcnRegEx#2](../../../../visual-basic/programming-guide/language-features/strings/codesnippet/VisualBasic/how-to-validate-strings-that-represent-dates-or-times_1.vb)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Nahraďte `("01/01/03")` a `"9:30 PM"` s datum a čas, kterou chcete ověřit. Je řetězec s jiným řetězcem pevně nahradit `String` proměnnou, nebo pomocí metody, vrátí řetězec, například `InputBox`.  
  
## <a name="robust-programming"></a>Robustní programování  
 Použít tuto metodu ověření než se pokusíte převést řetězec `String` k `DateTime` proměnné. Nejdřív kontrolou datum nebo čas, se můžete vyhnout generování výjimku za běhu.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.Information.IsDate%2A>  
 <xref:Microsoft.VisualBasic.Interaction.InputBox%2A>  
 [Ověřování řetězců v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
