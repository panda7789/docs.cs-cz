---
title: Typy metod pro manipulaci s řetězci
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], manipulating [Visual Basic]
- string manipulation
ms.assetid: 905055cd-7f50-48fb-9eed-b0995af1dc1f
ms.openlocfilehash: aba9af9c699cf8d07862c5d2967902bec1623500
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84363756"
---
# <a name="types-of-string-manipulation-methods-in-visual-basic"></a>Typy metod manipulace s řetězci v jazyce Visual Basic
Existuje několik různých způsobů, jak analyzovat a manipulovat s řetězci. Některé metody jsou součástí jazyka Visual Basic a další jsou podstatou `String` třídy.  
  
## <a name="visual-basic-language-and-the-net-framework"></a>Visual Basic jazyk a .NET Framework  
 Metody Visual Basic jsou používány jako podstatné funkce jazyka. Je možné je použít bez kvalifikace ve vašem kódu. Následující příklad ukazuje typické použití Visual Basic příkazu pro manipulaci s řetězci:  
  
 [!code-vb[VbVbalrStrings#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#44)]  
  
 V tomto příkladu `Mid` funkce provede přímou operaci se zapnutou `aString` a přiřadí hodnotu `bString` .  
  
 Seznam metod manipulace s řetězci Visual Basic naleznete v tématu [Souhrn manipulace s řetězci](../../../language-reference/keywords/string-manipulation-summary.md).  
  
### <a name="shared-methods-and-instance-methods"></a>Sdílené metody a metody instance  
 Můžete také manipulovat s řetězci pomocí metod `String` třídy. Existují dva typy metod v `String` : *sdílené* metody a metody *instance* .  
  
#### <a name="shared-methods"></a>Sdílené metody  
 Sdílená metoda je metoda, která vychází z `String` samotné třídy a nevyžaduje, aby instance této třídy fungovala. Tyto metody mohou být kvalifikovány s názvem třídy ( `String` ) spíše než instancí `String` třídy. Příklad:  
  
 [!code-vb[VbVbalrStrings#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#45)]  
  
 V předchozím příkladu <xref:System.String.Copy%2A?displayProperty=nameWithType> je metoda statickou metodou, která funguje na výrazu, který je dán, a přiřazuje výslednou hodnotu k `bString` .  
  
#### <a name="instance-methods"></a>Metody instance  
 Metody instance, naproti tomu stonk z konkrétní instance `String` a musí být kvalifikovány názvem instance. Příklad:  
  
 [!code-vb[VbVbalrStrings#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#46)]  
  
 V tomto příkladu <xref:System.String.Substring%2A?displayProperty=nameWithType> je metoda metodou instance třídy `String` (to znamená, `aString` ). Provede operaci na `aString` a přiřadí tuto hodnotu k `bString` .  
  
 Další informace naleznete v dokumentaci pro <xref:System.String> třídu.  
  
## <a name="see-also"></a>Viz také

- [Představení řetězců v jazyce Visual Basic](introduction-to-strings.md)
