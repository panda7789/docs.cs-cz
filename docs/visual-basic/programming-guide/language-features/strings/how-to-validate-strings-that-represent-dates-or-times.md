---
title: 'Postupy: Ověření řetězců, které představují data nebo časy.'
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], validating
- String data type [Visual Basic], validation
ms.assetid: ae7d4b29-3436-4032-bdbf-4650eb1c8e19
ms.openlocfilehash: 34af6dffeb0d05eaeed38354f8007554b60e91b0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344344"
---
# <a name="how-to-validate-strings-that-represent-dates-or-times-visual-basic"></a>Postupy: Ověření řetězců, které představují data nebo časy (Visual Basic).
Následující příklad kódu nastaví `Boolean` hodnotu, která označuje, zda řetězec představuje platné datum nebo čas.  
  
## <a name="example"></a>Příklad  
 [!code-vb[VbVbcnRegEx#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnRegEx/VB/Class1.vb#2)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Nahraďte `("01/01/03")` a `"9:30 PM"` datem a časem, který chcete ověřit. Řetězec lze nahradit jiným pevně zakódovaným řetězcem s `String` proměnnou nebo metodou, která vrací řetězec, například `InputBox`.  
  
## <a name="robust-programming"></a>Robustní programování  
 Tuto metodu použijte, chcete-li před pokusem o převedení `String` na `DateTime` proměnnou ověřit řetězec. Kontrolou prvního data nebo času se můžete vyhnout generování výjimky v době běhu.  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.Information.IsDate%2A>
- <xref:Microsoft.VisualBasic.Interaction.InputBox%2A>
- [Ověřování řetězců v Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
