---
title: 'Postupy: Ověření řetězců, které představují data nebo časy.'
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], validating
- String data type [Visual Basic], validation
ms.assetid: ae7d4b29-3436-4032-bdbf-4650eb1c8e19
ms.openlocfilehash: 5d153ac29039375386b3cd5f03609b1e4bd1d5bf
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410564"
---
# <a name="how-to-validate-strings-that-represent-dates-or-times-visual-basic"></a>Postupy: Ověření řetězců, které představují data nebo časy (Visual Basic).
Následující příklad kódu nastaví `Boolean` hodnotu, která označuje, zda řetězec představuje platné datum nebo čas.  
  
## <a name="example"></a>Příklad  
 [!code-vb[VbVbcnRegEx#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnRegEx/VB/Class1.vb#2)]  
  
## <a name="compile-the-code"></a>Kompilovat kód  
 Nahraďte `("01/01/03")` a `"9:30 PM"` datem a časem, který chcete ověřit. Řetězec lze nahradit jiným pevně zakódovaným řetězcem s `String` proměnnou nebo s metodou, která vrací řetězec, například `InputBox` .  
  
## <a name="robust-programming"></a>Robustní programování  
 Tuto metodu použijte k ověření řetězce před pokusem o převod na `String` `DateTime` proměnnou. Kontrolou prvního data nebo času se můžete vyhnout generování výjimky v době běhu.  
  
## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.Information.IsDate%2A>
- <xref:Microsoft.VisualBasic.Interaction.InputBox%2A>
- [Ověřování řetězců v jazyce Visual Basic](validating-strings.md)
