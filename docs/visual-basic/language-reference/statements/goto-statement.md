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
ms.openlocfilehash: eb6f48d04b7d14591003e340464451da7df45cd6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404612"
---
# <a name="goto-statement"></a>GoTo – příkaz
Větve nepodmíněně na určený řádek v proceduře.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
GoTo line  
```  
  
## <a name="part"></a>Část  
 `line`  
 Povinná hodnota. Libovolný popisek čáry.  
  
## <a name="remarks"></a>Poznámky  
 `GoTo`Příkaz může být větví pouze na řádky v proceduře, ve které se vyskytuje. Řádek musí mít popisek řádku, na který `GoTo` může odkazovat. Další informace naleznete v tématu [How to: Label Statements](../../programming-guide/program-structure/how-to-label-statements.md).  
  
> [!NOTE]
> `GoTo`příkazy mohou ztížit čtení a údržbu kódu. Kdykoli je to možné, použijte místo toho strukturu ovládacího prvku. Další informace najdete v tématu [tok řízení](../../programming-guide/language-features/control-flow/index.md).  
  
 Nemůžete použít `GoTo` příkaz k vytvoření větve mimo `For` ... `Next` , `For Each` ..., `Next` `SyncLock` `End SyncLock` `Try` ...,. `Catch` .. ... `Finally` , `With` ...,... `End With` , nebo `Using` ... `End Using` konstrukce na návěští uvnitř.  
  
## <a name="branching-and-try-constructions"></a>Větvení a vytváření try  
 V rámci `Try` ... `Catch` ...`Finally` konstrukce: následující pravidla platí pro větvení s `GoTo` příkazem.  
  
|Blok nebo oblast|Větvení z vnějšku|Vyskočení z vnitřku|  
|---------------------|-------------------------------|-------------------------------|  
|Blok `Try`|Pouze z `Catch` bloku stejné konstrukce <sup>1</sup>|Jenom mimo celou konstrukci|  
|Blok `Catch`|Nikdy Nepovoleno|Pouze vně celé konstrukce nebo do `Try` bloku stejné konstrukce <sup>1</sup>|  
|Blok `Finally`|Nikdy Nepovoleno|Nikdy Nepovoleno|  
  
 <sup>1</sup> , pokud jedna `Try` ... `Catch` ...`Finally` konstrukce je vnořena do jiného, `Catch` blok může být větví do `Try` bloku na vlastní úrovni vnoření, ale ne do žádného jiného `Try` bloku. Vnořený `Try` ... `Catch` ...`Finally` konstrukce musí být zcela obsažena v `Try` `Catch` bloku nebo konstrukce, v rámci které je vnořena.  
  
 Následující ilustrace znázorňuje jeden `Try` konstrukcí vnořený do jiného. Různé větve mezi bloky dvou konstrukcí jsou označeny jako platné nebo neplatné.  
  
 ![Grafický diagram větvení v konstrukcích try](./media/goto-statement/try-construction-branching.gif)  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `GoTo` příkaz pro větvení popiskům čáry v proceduře.  
  
 [!code-vb[VbVbalrStatements#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#31)]  
  
## <a name="see-also"></a>Viz také

- [Do...Loop – příkaz](do-loop-statement.md)
- [For...Next – příkaz](for-next-statement.md)
- [For Each...Next – příkaz](for-each-next-statement.md)
- [If...Then...Else – příkaz](if-then-else-statement.md)
- [Select...Case – příkaz](select-case-statement.md)
- [Try...Catch....Finally – příkaz](try-catch-finally-statement.md)
- [While...End While – příkaz](while-end-while-statement.md)
- [With...End With – příkaz](with-end-with-statement.md)
