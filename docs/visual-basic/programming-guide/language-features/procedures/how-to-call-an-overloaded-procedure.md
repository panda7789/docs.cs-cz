---
title: 'Postupy: Volání přetížené procedury (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], overloading
- procedures [Visual Basic], calling
- procedures [Visual Basic], multiple versions
- procedure calls [Visual Basic], overloaded
ms.assetid: 3bb331fb-f6bc-406f-9ca0-9609b497014c
ms.openlocfilehash: 9dda0fbc0cffe8904ab97c46cea40d5cf00c91e9
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58843783"
---
# <a name="how-to-call-an-overloaded-procedure-visual-basic"></a>Postupy: Volání přetížené procedury (Visual Basic)
Výhodou přetížení procedury je flexibilitu volání. Volající kód může získat informace, které je potřeba předat do procedury a poté zavolejte jedinou proceduru název, bez ohledu na to, jaké argumentů je předání.  
  
### <a name="to-call-a-procedure-that-has-more-than-one-version-defined"></a>Volání procedury, která má více než jednu verzi definovány  
  
1.  Ve volajícím kódu zjistěte, jaká data budou předány procesu.  
  
2.  Zápis protokolu TDS běžným způsobem, prezentování dat. v seznamu argumentů. Ujistěte se, že argumenty odpovídat seznamu parametrů. v jednu z verzí definované pro proceduru.  
  
3.  Není nutné určit, která verze procedury pro volání. Visual Basic předá řízení verzi, která odpovídá seznamu argumentů.  
  
     Následující příklad volá `post` postup deklarované v [jak: Definice více verzí procedury](./how-to-define-multiple-versions-of-a-procedure.md). Získá Identifikace zákazníka, určuje, zda je `String` nebo `Integer`a poté v obou případech volá stejný postup.  
  
     [!code-vb[VbVbcnProcedures#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#56)]  
  
     [!code-vb[VbVbcnProcedures#57](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#57)]  
  
## <a name="see-also"></a>Viz také:

- [Procedury](./index.md)
- [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)
- [Přetížení procedury](./procedure-overloading.md)
- [Řešení potíží s procedurami](./troubleshooting-procedures.md)
- [Postupy: Definice více verzí procedury](./how-to-define-multiple-versions-of-a-procedure.md)
- [Postupy: Přetížení procedury, která přebírá volitelné parametry](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [Postupy: Přetížení procedury, která přebírá nekonečný počet parametrů](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [Aspekty přetížení procedur](./considerations-in-overloading-procedures.md)
- [Řešení přetížení](./overload-resolution.md)
- [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md)
