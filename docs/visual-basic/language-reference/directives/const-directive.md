---
title: '#Const – direktiva (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.#Const
- '#vb.Const'
- '#Const'
helpviewer_keywords:
- '#Const directive'
- conditional compilation [Visual Basic], directives
- Const directive (#Const)
- Visual Basic compiler, compiler directives
- constants [Visual Basic], Const directive
- constants [Visual Basic], declaring
- Const statement [Visual Basic], directive (#Const)
- 'declaring constants [Visual Basic], #const directive'
ms.assetid: 707669e5-23f9-4f17-8622-a0d534429386
ms.openlocfilehash: 9b8d2da2158a8244b4533eb6ef49049949417216
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71696855"
---
# <a name="const-directive"></a>#Const – direktiva
Definuje podmíněné konstanty kompilátoru pro Visual Basic.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
#Const constname = expression  
```  
  
## <a name="parts"></a>Součásti  
 `constname`  
 Požadováno. Název konstanty, která je definována.  
  
 `expression`  
 Požadováno. Literál, jiné podmíněné konstanty kompilátoru nebo libovolná kombinace, která obsahuje všechny nebo všechny aritmetické nebo logické operátory s výjimkou `Is`.  
  
## <a name="remarks"></a>Poznámky  
 Podmíněné konstanty kompilátoru jsou vždy soukromé k souboru, ve kterém jsou uvedeny. Nemůžete vytvořit konstanty veřejného kompilátoru pomocí direktivy `#Const`; můžete je vytvořit pouze v uživatelském rozhraní nebo pomocí možnosti kompilátoru `/define`.  
  
 V `expression` lze použít pouze podmíněné konstanty a literály kompilátoru. Použití standardní konstanty definované s `Const` způsobí chybu. Naopak můžete použít konstanty definované s klíčovým slovem `#Const` pouze pro podmíněnou kompilaci. Konstanty mohou být také nedefinovány. v takovém případě mají hodnotu `Nothing`.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu se používá direktiva `#Const`.  
  
 [!code-vb[VbVbalrConditionalComp#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#3)]  
  
## <a name="see-also"></a>Viz také:

- [/define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md)
- [Direktivy #If...Then...#Else](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [Příkaz Const](../../../visual-basic/language-reference/statements/const-statement.md)
- [Podmíněná kompilace](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- [Příkaz If...Then...Else](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
