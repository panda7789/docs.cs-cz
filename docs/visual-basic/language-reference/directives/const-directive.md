---
title: '#Const – direktiva'
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
ms.openlocfilehash: 278219edb1bb5d1c0bb015611d69cbe4ae70014b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343848"
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

 Podmíněné konstanty kompilátoru jsou vždy soukromé k souboru, ve kterém jsou uvedeny. Pomocí direktivy `#Const` nemůžete vytvářet veřejné konstanty kompilátoru. můžete je vytvořit pouze v uživatelském rozhraní nebo pomocí možnosti kompilátoru `/define`.  
  
 V `expression`lze použít pouze podmíněné konstanty kompilátoru a literály. Při použití standardní konstanty definované v `Const` dojde k chybě. Naopak můžete použít konstanty definované s klíčovým slovem `#Const` pouze pro podmíněnou kompilaci. Konstanty mohou být také nedefinovány. v takovém případě mají hodnotu `Nothing`.  
  
## <a name="example"></a>Příklad  

 V tomto příkladu se používá direktiva `#Const`.  
  
 [!code-vb[VbVbalrConditionalComp#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#3)]  
  
## <a name="see-also"></a>Viz také:

- [-define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md)
- [Direktivy #If...Then...#Else](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [Příkaz Const](../../../visual-basic/language-reference/statements/const-statement.md)
- [Podmíněná kompilace](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- [Příkaz If...Then...Else](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
