---
title: GoTo – příkaz
ms.date: 07/20/2015
f1_keywords:
- vb.GoTo
helpviewer_keywords:
- GoTo statement [Visual Basic]
- control flow [Visual Basic], branching
- unconditional branching [Visual Basic]
- branching [Visual Basic]
- branching [Visual Basic], unconditional
- branching [Visual Basic], conditional
- conditional statements [Visual Basic], GoTo statement
- GoTo statement [Visual Basic], syntax
ms.assetid: 313274c2-8ab3-4b9c-9ba3-0fd6798e4f6d
ms.openlocfilehash: 27ebc677bab8b7f61a02408fddb30a6ec21c43cc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="goto-statement"></a>GoTo – příkaz
Větvích bezpodmínečně zadaný řádek v postupu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
GoTo line  
```  
  
## <a name="part"></a>Část  
 `line`  
 Požadováno. Žádné čáry popisku.  
  
## <a name="remarks"></a>Poznámky  
 `GoTo` Příkaz můžete větev jenom na řádky v postupu, ve kterém se zobrazí. Na řádku musí mít čáry popisku, který `GoTo` mohou odkazovat na. Další informace najdete v tématu [postup: příkazy popisek](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).  
  
> [!NOTE]
>  `GoTo` příkazy můžete nastavit kód obtížné číst a spravovat. Pokud je to možné, použijte místo toho řídicí struktury. Další informace najdete v tématu [tok řízení](../../../visual-basic/programming-guide/language-features/control-flow/index.md).  
  
 Nelze použít `GoTo` příkaz na větev z mimo `For`... `Next`, `For Each`... `Next`, `SyncLock`... `End SyncLock`, `Try`... `Catch`... `Finally`, `With`... `End With`, nebo `Using`... `End Using` konstrukce na štítek uvnitř.  
  
## <a name="branching-and-try-constructions"></a>Vytvoření větve a zkuste to konstrukce  
 V rámci `Try`... `Catch`... `Finally` konstrukce, platí následující pravidla pro vytvoření větve s `GoTo` příkaz.  
  
|Blokování nebo oblast|Větvení v z mimo|Větvení se z uvnitř|  
|---------------------|-------------------------------|-------------------------------|  
|`Try` Blok|Pouze z `Catch` bloku stejné konstrukce <sup>1</sup>|Pouze mimo celou konstrukce|  
|`Catch` Blok|Nikdy povoleno.|Pouze mimo celou konstrukce, nebo na `Try` bloku stejné konstrukce <sup>1</sup>|  
|`Finally` Blok|Nikdy povoleno.|Nikdy povoleno.|  
  
 <sup>1</sup> Pokud `Try`... `Catch`... `Finally` konstrukce vnořen v rámci druhého, `Catch` bloku můžete větev do `Try` bloku na svůj vlastní úroveň vnoření, ale ne do žádné jiné `Try` bloku. Vnořený `Try`... `Catch`... `Finally` konstrukce musí být obsaženy v úplně `Try` nebo `Catch` konstrukce, ve kterém je vnořený blok.  
  
 Následující obrázek znázorňuje jednu `Try` konstrukce vnořené v rámci jiného. Různé větví mezi bloky dvě struktur, se označují jako platný nebo neplatný.  
  
 ![Grafický diagram větvení v konstrukce zkuste](../../../visual-basic/language-reference/statements/media/trybranching.gif "TryBranching")  
Platné a neplatné větve v zkuste konstrukce  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `GoTo` příkaz pro připojení popisků čáry v postupu.  
  
 [!code-vb[VbVbalrStatements#31](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/goto-statement_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Příkaz Do...Loop](../../../visual-basic/language-reference/statements/do-loop-statement.md)  
 [Příkaz For...Next](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [Příkaz For Each...Next](../../../visual-basic/language-reference/statements/for-each-next-statement.md)  
 [Příkaz If...Then...Else](../../../visual-basic/language-reference/statements/if-then-else-statement.md)  
 [Příkaz Select...Case](../../../visual-basic/language-reference/statements/select-case-statement.md)  
 [Příkaz Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [Příkaz While...End While](../../../visual-basic/language-reference/statements/while-end-while-statement.md)  
 [Příkaz With...End With](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
