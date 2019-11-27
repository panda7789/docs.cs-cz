---
title: 'Postupy: vytváření řetězců pomocí StringBuilder'
ms.date: 07/20/2015
helpviewer_keywords:
- StringBuilder class
- strings [Visual Basic], using StringBuilder
ms.assetid: 9c042880-aa16-432e-9ccb-cd00abda9ae3
ms.openlocfilehash: 9295b9d0cdcfdb05dfc75f75f48c16c2354b09b0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344371"
---
# <a name="how-to-create-strings-using-a-stringbuilder-in-visual-basic"></a>Postupy: vytváření řetězců pomocí StringBuilder v Visual Basic

Tento příklad vytvoří dlouhý řetězec z mnoha menších řetězců pomocí třídy <xref:System.Text.StringBuilder>. Třída <xref:System.Text.StringBuilder> je efektivnější než `&=` operátor pro zřetězení řady řetězců.

## <a name="example"></a>Příklad

Následující příklad vytvoří instanci třídy <xref:System.Text.StringBuilder>, připojí k této instanci řetězce 1 000 a potom vrátí jeho řetězcovou reprezentaci:

 [!code-vb[VbVbalrStrings#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#70)]

## <a name="see-also"></a>Viz také:

- [Používání třídy StringBuilder](../../../../standard/base-types/stringbuilder.md)
- [&= – operátor](../../../language-reference/operators/and-assignment-operator.md)
- [Řetězce](index.md)
- [Vytváření nových řetězců](../../../../standard/base-types/creating-new.md)
- [Práce s řetězci](../../../../standard/base-types/manipulating-strings.md)
