---
title: 'Postupy: Ověření řetězců, které představují data nebo časy.'
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], validating
- String data type [Visual Basic], validation
ms.assetid: ae7d4b29-3436-4032-bdbf-4650eb1c8e19
ms.openlocfilehash: 5321e7a85c45ddb6ce17433bd25ce9ca2165f0a3
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75348405"
---
# <a name="how-to-validate-strings-that-represent-dates-or-times-visual-basic"></a>Postupy: Ověření řetězců, které představují data nebo časy (Visual Basic).
Následující příklad kódu nastaví `Boolean` hodnotu, která označuje, zda řetězec představuje platné datum nebo čas.  
  
## <a name="example"></a>Příklad  
 [!code-vb[VbVbcnRegEx#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnRegEx/VB/Class1.vb#2)]  
  
## <a name="compile-the-code"></a>Kompilace kódu  
 Nahraďte `("01/01/03")` a `"9:30 PM"` datem a časem, který chcete ověřit. Řetězec lze nahradit jiným pevně zakódovaným řetězcem s `String` proměnnou nebo metodou, která vrací řetězec, například `InputBox`.  
  
## <a name="robust-programming"></a>Robustní programování  
 Tuto metodu použijte, chcete-li před pokusem o převedení `String` na `DateTime` proměnnou ověřit řetězec. Kontrolou prvního data nebo času se můžete vyhnout generování výjimky v době běhu.  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.Information.IsDate%2A>
- <xref:Microsoft.VisualBasic.Interaction.InputBox%2A>
- [Ověřování řetězců v Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
