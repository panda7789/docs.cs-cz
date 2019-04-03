---
title: Typy metod manipulace s řetězci v jazyce Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], manipulating [Visual Basic]
- string manipulation
ms.assetid: 905055cd-7f50-48fb-9eed-b0995af1dc1f
ms.openlocfilehash: 44eb101ebdfeb316958a659107190ef1fc84df44
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58821150"
---
# <a name="types-of-string-manipulation-methods-in-visual-basic"></a>Typy metod manipulace s řetězci v jazyce Visual Basic
Existuje několik různých způsobů, jak analyzovat a manipulaci s řetězci. Některé metody jsou součástí jazyka Visual Basic a jiné jsou spojené `String` třídy.  
  
## <a name="visual-basic-language-and-the-net-framework"></a>Jazyk Visual Basic a rozhraní .NET Framework  
 Metody jazyka Visual Basic se používají jako vlastní funkce jazyka. Může být použít bez kvalifikace v kódu. Následující příklad ukazuje typické použití příkazu zacházení s řetězci jazyka Visual Basic:  
  
 [!code-vb[VbVbalrStrings#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#44)]  
  
 V tomto příkladu `Mid` funkce provede operaci s přímým přístupem na `aString` a přiřadí hodnotu k `bString`.  
  
 Seznam metod manipulace s řetězci jazyka Visual Basic najdete v tématu [souhrn manipulace s řetězci](../../../../visual-basic/language-reference/keywords/string-manipulation-summary.md).  
  
### <a name="shared-methods-and-instance-methods"></a>Sdílené metody a Instance metody  
 Můžete také manipulaci s řetězci s metodami `String` třídy. Existují dva typy metod v `String`: *sdílené* metody a *instance* metody.  
  
#### <a name="shared-methods"></a>Sdílené metody  
 Sdílené metody je metoda, která vyplývá ze `String` třídu a nevyžaduje, aby instance této třídy pro práci. Tyto metody mohou být kvalifikovány názvem třídy (`String`), nikoli s instancí `String` třídy. Příklad:  
  
 [!code-vb[VbVbalrStrings#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#45)]  
  
 V předchozím příkladu <xref:System.String.Copy%2A?displayProperty=nameWithType> metoda je statická metoda, která funguje na výraz ho dostane a přiřadí výslednou hodnotu pro `bString`.  
  
#### <a name="instance-methods"></a>Instance metody  
 Metody instance, naopak vyplývají z konkrétní instanci `String` a musí být kvalifikován s názvem instance. Příklad:  
  
 [!code-vb[VbVbalrStrings#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#46)]  
  
 V tomto příkladu <xref:System.String.Substring%2A?displayProperty=nameWithType> je metoda metodou instance `String` (to znamená `aString`). Provádí operaci na `aString` a přiřadí tuto hodnotu `bString`.  
  
 Další informace najdete v tématu v dokumentaci <xref:System.String> třídy.  
  
## <a name="see-also"></a>Viz také:

- [Úvod do řetězců v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
