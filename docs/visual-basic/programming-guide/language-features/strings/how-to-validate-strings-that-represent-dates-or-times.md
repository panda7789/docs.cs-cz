---
title: 'Postupy: Ověření řetězců, které představují data nebo časy (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], validating
- String data type [Visual Basic], validation
ms.assetid: ae7d4b29-3436-4032-bdbf-4650eb1c8e19
ms.openlocfilehash: 1a838d9d156ad9c05a70a4d4d72db1a288731c9b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54685396"
---
# <a name="how-to-validate-strings-that-represent-dates-or-times-visual-basic"></a>Postupy: Ověření řetězců, které představují data nebo časy (Visual Basic)
Následující příklad kódu nastaví `Boolean` hodnotu, která určuje, zda řetězec reprezentuje platné datum nebo čas.  
  
## <a name="example"></a>Příklad  
 [!code-vb[VbVbcnRegEx#2](../../../../visual-basic/programming-guide/language-features/strings/codesnippet/VisualBasic/how-to-validate-strings-that-represent-dates-or-times_1.vb)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Nahraďte `("01/01/03")` a `"9:30 PM"` s datem a časem, kterou chcete ověřit. Můžete nahradit řetězce jiným řetězcem pevně zakódované `String` proměnných, nebo s metodou, která vrátí řetězec, například `InputBox`.  
  
## <a name="robust-programming"></a>Robustní programování  
 Tuto metodu použijte k ověření před pokusem o převod řetězce `String` k `DateTime` proměnné. Nejprve zkontrolovat datum nebo čas, byste se vyhnout generuje výjimku za běhu.  
  
## <a name="see-also"></a>Viz také:
- <xref:Microsoft.VisualBasic.Information.IsDate%2A>
- <xref:Microsoft.VisualBasic.Interaction.InputBox%2A>
- [Ověřování řetězců v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
