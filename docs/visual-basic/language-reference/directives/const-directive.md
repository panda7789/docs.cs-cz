---
title: '##Const – direktiva'
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
ms.openlocfilehash: a3b3318f6b44f7d1798e08195be5aeb920b61c0c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33588064"
---
# <a name="const-directive"></a>#Const – direktiva
Definuje konstanty podmíněného kompilátoru jazyka Visual Basic.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#Const constname = expression  
```  
  
## <a name="parts"></a>Součásti  
 `constname`  
 Požadováno. Název konstanta definovaný.  
  
 `expression`  
 Požadováno. Literál, ostatní konstanta podmíněného kompilátoru nebo libovolnou kombinaci, která zahrnuje některé nebo všechny aritmetické nebo logické operátory s výjimkou `Is`.  
  
## <a name="remarks"></a>Poznámky  
 Konstanty podmíněného kompilátoru jsou vždy privátní do souboru, ve kterém se zobrazí. Nelze vytvořit veřejný kompilátoru konstanty pomocí `#Const` direktivy; můžete vytvořit pouze v uživatelském rozhraní nebo pomocí `/define` – možnost kompilátoru.  
  
 Můžete použít pouze konstanty podmíněného kompilátoru a literály v `expression`. Pomocí standardní konstanta definovaný s `Const` dojde k chybě. Naopak můžete použít konstanty definovaný s `#Const` – klíčové slovo pouze pro Podmíněná kompilace. Konstanty můžete také být undefined, v takovém případě budou mít hodnotu `Nothing`.  
  
## <a name="example"></a>Příklad  
 Tento příklad používá `#Const` – direktiva.  
  
 [!code-vb[VbVbalrConditionalComp#3](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/const-directive_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 [/ define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md)  
 [Direktivy #If...Then...#Else](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
 [Příkaz Const](../../../visual-basic/language-reference/statements/const-statement.md)  
 [Podmíněná kompilace](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 [Příkaz If...Then...Else](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
