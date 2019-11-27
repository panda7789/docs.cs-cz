---
title: Typy metod pro manipulaci s řetězci
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], manipulating [Visual Basic]
- string manipulation
ms.assetid: 905055cd-7f50-48fb-9eed-b0995af1dc1f
ms.openlocfilehash: a02278abfb71efb2f31f239a89a22ad1c8ee7a18
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346274"
---
# <a name="types-of-string-manipulation-methods-in-visual-basic"></a>Typy metod manipulace s řetězci v jazyce Visual Basic
Existuje několik různých způsobů, jak analyzovat a manipulovat s řetězci. Některé metody jsou součástí jazyka Visual Basic a další jsou podstatou `String` třídy.  
  
## <a name="visual-basic-language-and-the-net-framework"></a>Visual Basic jazyk a .NET Framework  
 Metody Visual Basic jsou používány jako podstatné funkce jazyka. Je možné je použít bez kvalifikace ve vašem kódu. Následující příklad ukazuje typické použití Visual Basic příkazu pro manipulaci s řetězci:  
  
 [!code-vb[VbVbalrStrings#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#44)]  
  
 V tomto příkladu funkce `Mid` provede přímou operaci na `aString` a přiřadí hodnotu `bString`.  
  
 Seznam metod manipulace s řetězci Visual Basic naleznete v tématu [Souhrn manipulace s řetězci](../../../../visual-basic/language-reference/keywords/string-manipulation-summary.md).  
  
### <a name="shared-methods-and-instance-methods"></a>Sdílené metody a metody instance  
 Můžete také manipulovat s řetězci pomocí metod třídy `String`. Existují dva typy metod v `String`: *sdílené* metody a metody *instance* .  
  
#### <a name="shared-methods"></a>Sdílené metody  
 Sdílená metoda je metoda, která vychází z `String` samotné třídy a nevyžaduje, aby instance této třídy fungovala. Tyto metody mohou být kvalifikovány s názvem třídy (`String`) namísto instance `String` třídy. Příklad:  
  
 [!code-vb[VbVbalrStrings#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#45)]  
  
 V předchozím příkladu je metoda <xref:System.String.Copy%2A?displayProperty=nameWithType> statická metoda, která funguje na výrazu, který je dán, a přiřazuje výslednou hodnotu `bString`.  
  
#### <a name="instance-methods"></a>Metody instance  
 Metody instance naproti tomu vyplývají z konkrétní instance `String` a musí být kvalifikovány názvem instance. Příklad:  
  
 [!code-vb[VbVbalrStrings#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#46)]  
  
 V tomto příkladu je metoda <xref:System.String.Substring%2A?displayProperty=nameWithType> metodou instance `String` (to znamená `aString`). Provede operaci na `aString` a přiřadí tuto hodnotu `bString`.  
  
 Další informace naleznete v dokumentaci k třídě <xref:System.String>.  
  
## <a name="see-also"></a>Viz také:

- [Seznámení s řetězci v Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
