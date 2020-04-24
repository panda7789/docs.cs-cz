---
title: 'Postup: vytvoření řetězců pomocí StringBuilder'
ms.date: 07/20/2015
helpviewer_keywords:
- StringBuilder class
- strings [Visual Basic], using StringBuilder
ms.assetid: 9c042880-aa16-432e-9ccb-cd00abda9ae3
ms.openlocfilehash: c41db584df83782dab99b90043045aa2cabcb6ff
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645326"
---
# <a name="how-to-create-strings-using-a-stringbuilder-in-visual-basic"></a>Postup: vytvoření řetězců pomocí StringBuilder v jazyce Visual Basic

Tento příklad vytvoří dlouhý řetězec z mnoha <xref:System.Text.StringBuilder> menších řetězců pomocí třídy. Třída <xref:System.Text.StringBuilder> je efektivnější než `&=` operátor pro zřetězení mnoho řetězců.

## <a name="example"></a>Příklad

Následující příklad vytvoří instanci <xref:System.Text.StringBuilder> třídy, připojí k této instanci 1 000 řetězců a pak vrátí její řetězcovou reprezentaci:

 [!code-vb[VbVbalrStrings#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#70)]

## <a name="see-also"></a>Viz také

- [Používání třídy StringBuilder](../../../../standard/base-types/stringbuilder.md)
- [&= Operátor](../../../language-reference/operators/and-assignment-operator.md)
- [Řetězce](index.md)
- [Vytváření nových řetězců](../../../../standard/base-types/creating-new.md)
- [Práce s řetězci](../../../../standard/base-types/best-practices-strings.md)
