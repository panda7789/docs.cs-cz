---
title: 'Postupy: Ověření řetězců, které představují data nebo časy (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], validating
- String data type [Visual Basic], validation
ms.assetid: ae7d4b29-3436-4032-bdbf-4650eb1c8e19
ms.openlocfilehash: c1a3f14354e36dec91aca3afbe8470eff7146318
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56970400"
---
# <a name="how-to-validate-strings-that-represent-dates-or-times-visual-basic"></a>Postupy: Ověření řetězců, které představují data nebo časy (Visual Basic)
Následující příklad kódu nastaví `Boolean` hodnotu, která určuje, zda řetězec reprezentuje platné datum nebo čas.  
  
## <a name="example"></a>Příklad  
 [!code-vb[VbVbcnRegEx#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnRegEx/VB/Class1.vb#2)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Nahraďte `("01/01/03")` a `"9:30 PM"` s datem a časem, kterou chcete ověřit. Můžete nahradit řetězce jiným řetězcem pevně zakódované `String` proměnných, nebo s metodou, která vrátí řetězec, například `InputBox`.  
  
## <a name="robust-programming"></a>Robustní programování  
 Tuto metodu použijte k ověření před pokusem o převod řetězce `String` k `DateTime` proměnné. Nejprve zkontrolovat datum nebo čas, byste se vyhnout generuje výjimku za běhu.  
  
## <a name="see-also"></a>Viz také:
- <xref:Microsoft.VisualBasic.Information.IsDate%2A>
- <xref:Microsoft.VisualBasic.Interaction.InputBox%2A>
- [Ověřování řetězců v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
