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
ms.openlocfilehash: 4b7a5cce56dfdd2bdc7e068aadbc18b92bba269d
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581821"
---
# <a name="goto-statement"></a>GoTo – příkaz
Větve nepodmíněně na určený řádek v proceduře.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
GoTo line  
```  
  
## <a name="part"></a>Částí  
 `line`  
 Požadováno. Libovolný popisek čáry.  
  
## <a name="remarks"></a>Poznámky  
 Příkaz `GoTo` se může větvit jenom na řádky v proceduře, ve které se vyskytuje. Řádek musí mít popisek čáry, na který `GoTo` může odkazovat. Další informace naleznete v tématu [How to: Label Statements](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).  
  
> [!NOTE]
> příkazy `GoTo` mohou ztížit čtení a údržbu kódu. Kdykoli je to možné, použijte místo toho strukturu ovládacího prvku. Další informace najdete v tématu [tok řízení](../../../visual-basic/programming-guide/language-features/control-flow/index.md).  
  
 Příkaz `GoTo` nelze použít pro větev mimo `For`... `Next`, `For Each`... `Next`, `SyncLock`... `End SyncLock`, `Try`... `Catch`... `Finally`, 0... 1 nebo 2... 3 konstrukce na popisek uvnitř.  
  
## <a name="branching-and-try-constructions"></a>Větvení a vytváření try  
 V rámci `Try`... `Catch`... `Finally` konstrukce se následující pravidla vztahují na větvení pomocí příkazu `GoTo`.  
  
|Blok nebo oblast|Větvení z vnějšku|Vyskočení z vnitřku|  
|---------------------|-------------------------------|-------------------------------|  
|blok `Try`|Pouze z `Catch`ho bloku stejné konstrukce <sup>1</sup>|Jenom mimo celou konstrukci|  
|blok `Catch`|Nikdy Nepovoleno|Pouze mimo celou konstrukci nebo do `Try`ho bloku stejné konstrukce <sup>1</sup>|  
|blok `Finally`|Nikdy Nepovoleno|Nikdy Nepovoleno|  
  
 <sup>1</sup> , pokud jedna `Try`... `Catch`... `Finally` konstrukce je vnořená do jiného, `Catch` blok se může větvit do `Try` bloku na vlastní úrovni vnoření, ale ne do žádného jiného `Try` bloku. Vnořený `Try`... `Catch`... konstrukce `Finally` musí být zcela obsažena v bloku `Try` nebo `Catch` konstrukce, v rámci které je vnořena.  
  
 Následující ilustrace znázorňuje jeden `Try` konstrukce vnořené v rámci jiného. Různé větve mezi bloky dvou konstrukcí jsou označeny jako platné nebo neplatné.  
  
 ![Grafický diagram větvení v konstrukcích try](./media/goto-statement/try-construction-branching.gif)  
  
## <a name="example"></a>Příklad  
 Následující příklad používá příkaz `GoTo` pro větvení popiskům čáry v proceduře.  
  
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
