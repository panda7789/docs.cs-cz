---
title: "#<a name=\"const-directive\"></a>#Const – direktiva"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a6e162b01dc5c99fb7708337d259f9e66ddd6b64
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
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
 [#If... Then... #Else – direktivy](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
 [Const – příkaz](../../../visual-basic/language-reference/statements/const-statement.md)  
 [Podmíněná kompilace](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 [If... Potom... Else – příkaz](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
