---
title: "GoTo – příkaz"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
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
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 22a6315e69cd6c797d462d0835e85bb1dde67dcc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
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
>  `GoTo`příkazy můžete nastavit kód obtížné číst a spravovat. Pokud je to možné, použijte místo toho řídicí struktury. Další informace najdete v tématu [tok řízení](../../../visual-basic/programming-guide/language-features/control-flow/index.md).  
  
 Nelze použít `GoTo` příkaz na větev z mimo `For`... `Next`, `For Each`... `Next`, `SyncLock`... `End SyncLock`, `Try`... `Catch`... `Finally`, `With`... `End With`, nebo `Using`... `End Using` konstrukce na štítek uvnitř.  
  
## <a name="branching-and-try-constructions"></a>Vytvoření větve a zkuste to konstrukce  
 V rámci `Try`... `Catch`... `Finally` konstrukce, platí následující pravidla pro vytvoření větve s `GoTo` příkaz.  
  
|Blokování nebo oblast|Větvení v z mimo|Větvení se z uvnitř|  
|---------------------|-------------------------------|-------------------------------|  
|`Try`blok|Pouze z `Catch` bloku stejné konstrukce <sup>1</sup>|Pouze mimo celou konstrukce|  
|`Catch`blok|Nikdy povoleno.|Pouze mimo celou konstrukce, nebo na `Try` bloku stejné konstrukce <sup>1</sup>|  
|`Finally`blok|Nikdy povoleno.|Nikdy povoleno.|  
  
 <sup>1</sup> Pokud `Try`... `Catch`... `Finally` konstrukce vnořen v rámci druhého, `Catch` bloku můžete větev do `Try` bloku na svůj vlastní úroveň vnoření, ale ne do žádné jiné `Try` bloku. Vnořený `Try`... `Catch`... `Finally` konstrukce musí být obsaženy v úplně `Try` nebo `Catch` konstrukce, ve kterém je vnořený blok.  
  
 Následující obrázek znázorňuje jednu `Try` konstrukce vnořené v rámci jiného. Různé větví mezi bloky dvě struktur, se označují jako platný nebo neplatný.  
  
 ![Grafický diagram větvení v konstrukce zkuste](../../../visual-basic/language-reference/statements/media/trybranching.gif "TryBranching")  
Platné a neplatné větve v zkuste konstrukce  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `GoTo` příkaz pro připojení popisků čáry v postupu.  
  
 [!code-vb[VbVbalrStatements#31](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/goto-statement_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Provést... Příkaz smyčky](../../../visual-basic/language-reference/statements/do-loop-statement.md)  
 [Pro... Next – příkaz](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [Pro každou... Next – příkaz](../../../visual-basic/language-reference/statements/for-each-next-statement.md)  
 [If... Potom... Else – příkaz](../../../visual-basic/language-reference/statements/if-then-else-statement.md)  
 [Vyberte... Case – příkaz](../../../visual-basic/language-reference/statements/select-case-statement.md)  
 [Try... Catch... Finally – příkaz](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [Chvíli... End While – příkaz](../../../visual-basic/language-reference/statements/while-end-while-statement.md)  
 [S... End With – příkaz](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
