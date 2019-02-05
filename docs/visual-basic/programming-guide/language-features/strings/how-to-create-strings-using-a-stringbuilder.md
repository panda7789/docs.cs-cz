---
title: 'Postupy: Vytváření řetězců pomocí StringBuilder v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- StringBuilder class
- strings [Visual Basic], using StringBuilder
ms.assetid: 9c042880-aa16-432e-9ccb-cd00abda9ae3
ms.openlocfilehash: dec1afdbd3ca6c0ba719a95906de8cf6fc7ba378
ms.sourcegitcommit: facefcacd7ae2e5645e463bc841df213c505ffd4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/05/2019
ms.locfileid: "55738796"
---
# <a name="how-to-create-strings-using-a-stringbuilder-in-visual-basic"></a>Postupy: Vytváření řetězců pomocí StringBuilder v jazyce Visual Basic
Tento příklad vytvoří dlouhý řetězec z mnoha menších řetězců pomocí <xref:System.Text.StringBuilder> třídy. <xref:System.Text.StringBuilder> Třída je efektivnější než `&=` operátoru pro zřetězení řetězců mnoho.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří instance <xref:System.Text.StringBuilder> připojí 1 000 řetězce do této instance třídy a vrátí řetězcové vyjádření.  
  
 [!code-vb[VbVbalrStrings#70](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-create-strings-using-a-stringbuilder_1.vb)]  
  
## <a name="see-also"></a>Viz také:
- [Používání třídy StringBuilder](../../../../standard/base-types/stringbuilder.md)
- [&= – operátor](../../../../visual-basic/language-reference/operators/and-assignment-operator.md)
- [Řetězce](../../../../visual-basic/programming-guide/language-features/strings/index.md)
- [Vytváření nových řetězců](../../../../standard/base-types/creating-new.md)
- [Práce s řetězci](../../../../standard/base-types/manipulating-strings.md)
