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
ms.openlocfilehash: c4dd249620ba1bf445642ce4600498f6beb30461
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58827767"
---
# <a name="goto-statement"></a>GoTo – příkaz
Rozvětví se nepodmíněně na určený řádek v proceduře.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
GoTo line  
```  
  
## <a name="part"></a>Část  
 `line`  
 Povinný parametr. Žádné čáry popisku.  
  
## <a name="remarks"></a>Poznámky  
 `GoTo` Příkaz větvit pouze pro řádky v postupu, ve kterém se zobrazí. Na řádku musí mít popisek, který řádek `GoTo` mohou odkazovat na. Další informace najdete v tématu [jak: Vytváření popisků příkazů](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).  
  
> [!NOTE]
>  `GoTo` příkazy může ztěžovat kód ke čtení a udržovat. Kdykoli je to možné, použijte řídicí struktura. Další informace najdete v tématu [tok řízení](../../../visual-basic/programming-guide/language-features/control-flow/index.md).  
  
 Nelze použít `GoTo` příkaz do větve z mimo `For`... `Next`, `For Each`... `Next`, `SyncLock`... `End SyncLock`, `Try`... `Catch`... `Finally`, `With`... `End With`, nebo `Using`... `End Using` konstrukce na popisek uvnitř.  
  
## <a name="branching-and-try-constructions"></a>Větvení a konstrukce akci  
 V rámci `Try`... `Catch`... `Finally` konstrukce, platí následující pravidla pro větvení s `GoTo` příkazu.  
  
|Blokování nebo oblasti|Větvení v z mimo|Větvení navýšení kapacity v rámci|  
|---------------------|-------------------------------|-------------------------------|  
|`Try` Blok|Pouze z `Catch` bloku stejné konstrukce <sup>1</sup>|Pouze mimo celý konstrukce|  
|`Catch` Blok|Nikdy povoleno|Pouze mimo celého procesu vytváření, nebo do adresáře `Try` bloku stejné konstrukce <sup>1</sup>|  
|`Finally` Blok|Nikdy povoleno|Nikdy povoleno|  
  
 <sup>1</sup> Pokud `Try`... `Catch`... `Finally` konstrukce je vnořená v jiném, `Catch` větvit do bloku `Try` bloku na vlastní úroveň vnoření, ale ne do jiného `Try` bloku. Vnořený `Try`... `Catch`... `Finally` konstrukce musí být obsažena v úplně `Try` nebo `Catch` bloku konstrukce, ve kterém je vnořená.  
  
 Následující obrázek znázorňuje jeden `Try` konstrukce vnořit do jiného. Různými větvemi mezi bloky dvě konstrukce jsou označeny jako platný nebo neplatný.  
  
 ![Grafický diagram větvení v konstrukcích Try](./media/goto-statement/try-construction-branching.gif)  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `GoTo` příkaz vzorce pro větvení popisků čáry v postupu.  
  
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
