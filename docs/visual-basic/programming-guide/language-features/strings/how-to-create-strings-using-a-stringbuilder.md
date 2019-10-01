---
title: 'Postupy: vytváření řetězců pomocí StringBuilder v Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- StringBuilder class
- strings [Visual Basic], using StringBuilder
ms.assetid: 9c042880-aa16-432e-9ccb-cd00abda9ae3
ms.openlocfilehash: 19e036abc9d25ec7fdfd6c33ebb420ec4f503cbc
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700106"
---
# <a name="how-to-create-strings-using-a-stringbuilder-in-visual-basic"></a>Postupy: vytváření řetězců pomocí StringBuilder v Visual Basic

Tento příklad vytvoří dlouhý řetězec z mnoha menších řetězců pomocí třídy <xref:System.Text.StringBuilder>. Třída <xref:System.Text.StringBuilder> je efektivnější než operátor `&=` pro zřetězení řady řetězců.

## <a name="example"></a>Příklad

Následující příklad vytvoří instanci třídy <xref:System.Text.StringBuilder>, připojí k této instanci řetězce 1 000 a potom vrátí jeho řetězcovou reprezentaci:

 [!code-vb[VbVbalrStrings#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#70)]

## <a name="see-also"></a>Viz také:

- [Používání třídy StringBuilder](../../../../standard/base-types/stringbuilder.md)
- [Operátor &=](../../../language-reference/operators/and-assignment-operator.md)
- [Řetězce](index.md)
- [Vytváření nových řetězců](../../../../standard/base-types/creating-new.md)
- [Práce s řetězci](../../../../standard/base-types/manipulating-strings.md)
