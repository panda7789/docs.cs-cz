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
ms.openlocfilehash: 91152771a4ef5ec74a7408511ccc2afe28dd442e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415463"
---
# <a name="const-directive"></a>#Const – direktiva

Definuje podmíněné konstanty kompilátoru pro Visual Basic.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
#Const constname = expression  
```  
  
## <a name="parts"></a>Součásti  

 `constname`  
 Povinná hodnota. Název konstanty, která je definována.  
  
 `expression`  
 Povinná hodnota. Literál, jiné podmíněné konstanty kompilátoru nebo libovolná kombinace obsahující všechny nebo všechny aritmetické nebo logické operátory s výjimkou `Is` .  
  
## <a name="remarks"></a>Poznámky  

 Podmíněné konstanty kompilátoru jsou vždy soukromé k souboru, ve kterém jsou uvedeny. Nemůžete vytvořit konstanty veřejného kompilátoru pomocí `#Const` direktivy. můžete je vytvořit pouze v uživatelském rozhraní nebo pomocí `/define` Možnosti kompilátoru.  
  
 V můžete použít pouze podmíněné konstanty kompilátoru a literály `expression` . Použití standardní konstanty definované s `Const` způsobí chybu. Naopak můžete použít konstanty definované s `#Const` klíčovým slovem pouze pro podmíněnou kompilaci. Konstanty mohou být také nedefinovány, v takovém případě mají hodnotu `Nothing` .  
  
## <a name="example"></a>Příklad  

 V tomto příkladu se používá `#Const` direktiva.  
  
 [!code-vb[VbVbalrConditionalComp#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#3)]  
  
## <a name="see-also"></a>Viz také

- [-define (Visual Basic)](../../reference/command-line-compiler/define.md)
- [#If... Then... #Else – direktivy](if-then-else-directives.md)
- [Const – příkaz](../statements/const-statement.md)
- [Podmíněná kompilace](../../programming-guide/program-structure/conditional-compilation.md)
- [If...Then...Else – příkaz](../statements/if-then-else-statement.md)
