---
title: 'Postupy: Volání přetížené procedury'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], overloading
- procedures [Visual Basic], calling
- procedures [Visual Basic], multiple versions
- procedure calls [Visual Basic], overloaded
ms.assetid: 3bb331fb-f6bc-406f-9ca0-9609b497014c
ms.openlocfilehash: de101309fa1edaaddc3defc5759d9293fbef684c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84388540"
---
# <a name="how-to-call-an-overloaded-procedure-visual-basic"></a>Postupy: Volání přetížené procedury (Visual Basic)
Výhodou přetížení procedury je flexibilita volání. Volající kód může získat informace, které potřebuje předat proceduře, a pak zavolat jeden název procedury bez ohledu na to, co argumenty předává.  
  
### <a name="to-call-a-procedure-that-has-more-than-one-version-defined"></a>Volání procedury, která má definováno více než jednu verzi  
  
1. V kódu volání určete, která data mají být předána do postupu.  
  
2. Zapište volání procedury normálním způsobem a prezentujte data v seznamu argumentů. Ujistěte se, že argumenty odpovídají seznamu parametrů v jedné z verzí definovaných pro proceduru.  
  
3. Nemusíte určit, která verze procedury má být volána. Visual Basic předá řízení verzi, která odpovídá vašemu seznamu argumentů.  
  
     Následující příklad volá `post` proceduru deklarovanou v tématu [Postupy: definice více verzí procedury](./how-to-define-multiple-versions-of-a-procedure.md). Získá identifikaci zákazníka, určí, zda se jedná o `String` `Integer` , a pak v obou případech volá stejný postup.  
  
     [!code-vb[VbVbcnProcedures#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#56)]  
  
     [!code-vb[VbVbcnProcedures#57](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#57)]  
  
## <a name="see-also"></a>Viz také

- [Procedury](./index.md)
- [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)
- [Přetížení procedury](./procedure-overloading.md)
- [Řešení potíží s procedurami](./troubleshooting-procedures.md)
- [Postupy: Definice více verzí procedury](./how-to-define-multiple-versions-of-a-procedure.md)
- [Postupy: Přetížení procedury, která přebírá nepovinné parametry](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [Postupy: Přetížení procedury, která přebírá nekonečný počet parametrů.](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [Aspekty přetížení procedur](./considerations-in-overloading-procedures.md)
- [Rozlišení přetěžování](./overload-resolution.md)
- [Přetížení](../../../language-reference/modifiers/overloads.md)
