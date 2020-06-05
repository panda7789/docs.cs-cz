---
title: Return – příkaz
ms.date: 07/20/2015
f1_keywords:
- vb.Return
helpviewer_keywords:
- Return statement [Visual Basic], syntax
- control flow [Visual Basic], returning control to expressions
- Return statement [Visual Basic]
- expressions [Visual Basic], returning control to
ms.assetid: ac86e7f0-5a67-42c3-9834-0e0381efa3ec
ms.openlocfilehash: cdb58e32c30c8e6c1662fb698ac5576c3f71258c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404197"
---
# <a name="return-statement-visual-basic"></a>Return – příkaz (Visual Basic)
Vrátí řízení kódu, který se nazývá `Function` procedura,,, `Sub` `Get` `Set` nebo `Operator` .  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Return  
' -or-  
Return expression  
```  
  
## <a name="part"></a>Část  
 `expression`  
 Vyžadováno v `Function` proceduře, `Get` nebo `Operator` . Výraz, který představuje hodnotu, která má být vrácena volajícímu kódu.  
  
## <a name="remarks"></a>Poznámky  
 V `Sub` proceduře nebo `Set` `Return` je příkaz ekvivalentní `Exit Sub` `Exit Property` příkazu nebo a `expression` nesmí být dodán.  
  
 V `Function` proceduře, `Get` nebo `Operator` `Return` musí příkaz obsahovat `expression` a `expression` musí vyhodnotit na datový typ, který lze převést na návratový typ procedury. V `Function` proceduře nebo máte `Get` také alternativu k názvu procedury, která má sloužit jako návratová hodnota, a poté provedení `Exit Function` `Exit Property` příkazu nebo. V `Operator` proceduře je nutné použít `Return expression` .  
  
 Stejný postup můžete použít jako `Return` vhodný počet příkazů.  
  
> [!NOTE]
> Kód v bloku se `Finally` spustí po `Return` zjištění příkazu v `Try` `Catch` bloku nebo, ale před spuštěním tohoto `Return` příkazu. `Return`Příkaz nelze zahrnout do `Finally` bloku.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `Return` příkaz několikrát pro návrat na volající kód v případě, že procedura nemusí dělat cokoli jiného.  
  
 [!code-vb[VbVbalrStatements#53](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#53)]  
  
## <a name="see-also"></a>Viz také

- [Function – příkaz](function-statement.md)
- [Sub – příkaz](sub-statement.md)
- [Get – příkaz](get-statement.md)
- [Set – příkaz](set-statement.md)
- [Operator – příkaz](operator-statement.md)
- [Property – příkaz](property-statement.md)
- [Exit – příkaz](exit-statement.md)
- [Try...Catch....Finally – příkaz](try-catch-finally-statement.md)
