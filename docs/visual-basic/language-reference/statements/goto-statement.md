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
ms.openlocfilehash: d5cdcd214c9679e245645505fe11cb5d521ce085
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351088"
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
  
 Příkaz `GoTo` nemůžete použít k vytvoření větve mimo `For`...`Next`, `For Each`...`Next`, `SyncLock`...`End SyncLock`, `Try`...`Catch`...`Finally`, `With`...`End With`nebo `Using`...`End Using` konstrukce na návěští uvnitř.  
  
## <a name="branching-and-try-constructions"></a>Větvení a vytváření try  
 V rámci `Try`...`Catch`...`Finally` konstrukce se následující pravidla vztahují na větvení s příkazem `GoTo`.  
  
|Blok nebo oblast|Větvení z vnějšku|Vyskočení z vnitřku|  
|---------------------|-------------------------------|-------------------------------|  
|blok `Try`|Pouze z `Catch`ho bloku stejné konstrukce <sup>1</sup>|Jenom mimo celou konstrukci|  
|blok `Catch`|Nikdy Nepovoleno|Pouze mimo celou konstrukci nebo do `Try`ho bloku stejné konstrukce <sup>1</sup>|  
|blok `Finally`|Nikdy Nepovoleno|Nikdy Nepovoleno|  
  
 <sup>1</sup> Pokud je jedna `Try`...`Catch`...`Finally` konstrukce vnořená do jiného, `Catch` blok může větvit do bloku `Try` na vlastní úrovni vnoření, ale ne do žádného jiného `Try` bloku. Vnořená `Try`...`Catch`...`Finally` konstrukce musí být zcela obsažena v `Try` nebo `Catch` bloku konstrukce, v rámci které je vnořena.  
  
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
