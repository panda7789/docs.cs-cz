---
title: GoTo – příkaz (Visual Basic)
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
ms.openlocfilehash: 3034c84684e94dfe8c334107a16df8cbd227c4d4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912451"
---
# <a name="goto-statement"></a>GoTo – příkaz
Větve nepodmíněně na určený řádek v proceduře.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
GoTo line  
```  
  
## <a name="part"></a>Částí  
 `line`  
 Povinný parametr. Libovolný popisek čáry.  
  
## <a name="remarks"></a>Poznámky  
 `GoTo` Příkaz může být větví pouze na řádky v proceduře, ve které se vyskytuje. Řádek musí mít popisek řádku, na který `GoTo` může odkazovat. Další informace najdete v tématu [jak: Příkazy](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md)Label.  
  
> [!NOTE]
> `GoTo`příkazy mohou ztížit čtení a údržbu kódu. Kdykoli je to možné, použijte místo toho strukturu ovládacího prvku. Další informace najdete v tématu [tok řízení](../../../visual-basic/programming-guide/language-features/control-flow/index.md).  
  
 Nemůžete použít `GoTo` příkaz k vytvoření `For`větve mimo... `Next`, `For Each`... `Next`, `SyncLock`... `End SyncLock`, `Try`... `Catch`... `Finally`, `With`... `End With`, nebo`Using`... `End Using` konstrukce na návěští uvnitř.  
  
## <a name="branching-and-try-constructions"></a>Větvení a vytváření try  
 V rámci `Try`... `Catch`... konstrukce: následující pravidla platí pro větvení `GoTo` s příkazem. `Finally`  
  
|Blok nebo oblast|Větvení z vnějšku|Vyskočení z vnitřku|  
|---------------------|-------------------------------|-------------------------------|  
|`Try`Blokované|Pouze z `Catch` bloku stejné konstrukce <sup>1</sup>|Jenom mimo celou konstrukci|  
|`Catch`Blokované|Nikdy Nepovoleno|Pouze vně celé konstrukce nebo do `Try` bloku stejné konstrukce <sup>1</sup>|  
|`Finally`Blokované|Nikdy Nepovoleno|Nikdy Nepovoleno|  
  
 <sup>1</sup> , pokud `Try`jedna... `Catch`... konstrukce je vnořena do jiného, `Catch` `Try` blok může být větví do bloku na vlastní úrovni vnoření, ale ne do žádného jiného `Try` bloku. `Finally` Vnořený `Try`... `Catch`... konstrukce musí být zcela obsažena `Try` v bloku `Catch` nebo konstrukce, v rámci které je vnořena. `Finally`  
  
 Následující ilustrace znázorňuje jeden `Try` konstrukcí vnořený do jiného. Různé větve mezi bloky dvou konstrukcí jsou označeny jako platné nebo neplatné.  
  
 ![Grafický diagram větvení v konstrukcích try](./media/goto-statement/try-construction-branching.gif)  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `GoTo` příkaz pro větvení popiskům čáry v proceduře.  
  
 [!code-vb[VbVbalrStatements#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#31)]  
  
## <a name="see-also"></a>Viz také:

- [Příkaz Do...Loop](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [Příkaz For...Next](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Příkaz For Each...Next](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [Příkaz If...Then...Else](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [Příkaz Select...Case](../../../visual-basic/language-reference/statements/select-case-statement.md)
- [Příkaz Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [Příkaz While...End While](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [Příkaz With...End With](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
