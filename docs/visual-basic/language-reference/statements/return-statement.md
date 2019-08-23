---
title: Return – příkaz (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Return
helpviewer_keywords:
- Return statement [Visual Basic], syntax
- control flow [Visual Basic], returning control to expressions
- Return statement [Visual Basic]
- expressions [Visual Basic], returning control to
ms.assetid: ac86e7f0-5a67-42c3-9834-0e0381efa3ec
ms.openlocfilehash: af49ea95d7f9d01072190ac3ccf6ba2f1041347e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957675"
---
# <a name="return-statement-visual-basic"></a>Return – příkaz (Visual Basic)
Vrátí řízení kódu `Function`, který se nazývá procedura `Get`, `Sub` `Set`,, nebo `Operator` .  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Return  
-or-  
Return expression  
```  
  
## <a name="part"></a>Částí  
 `expression`  
 Vyžadováno v `Function`proceduře, `Get`nebo. `Operator` Výraz, který představuje hodnotu, která má být vrácena volajícímu kódu.  
  
## <a name="remarks"></a>Poznámky  
 `Sub` V proceduře `Set`neboje příkazekvivalentní`Exit Sub` příkazu nebo`Exit Property` a`expression`nesmíbýtdodán. `Return`  
  
 `Get` Vproceduře`Return` ,nebo`expression`musí příkaz obsahovat a`expression` musí vyhodnotit na datový typ, který lze převést na návratový typ procedury. `Operator` `Function` V proceduře `Get` `Exit Function` nebo máte také alternativu k názvu procedury, která má sloužit jako návratová hodnota, a poté provedení příkazu nebo `Exit Property`. `Function` V proceduře je nutné použít `Return expression`. `Operator`  
  
 Stejný postup můžete použít jako `Return` vhodný počet příkazů.  
  
> [!NOTE]
> Kód `Finally` v bloku se spustí `Try` `Return` po zjištění příkazu v bloku nebo `Catch` , ale před spuštěním tohoto `Return` příkazu. Příkaz nelze zahrnout `Finally` do bloku. `Return`  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `Return` příkaz několikrát pro návrat na volající kód v případě, že procedura nemusí dělat cokoli jiného.  
  
 [!code-vb[VbVbalrStatements#53](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#53)]  
  
## <a name="see-also"></a>Viz také:

- [Příkaz Function](../../../visual-basic/language-reference/statements/function-statement.md)
- [Příkaz Sub](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Příkaz Get](../../../visual-basic/language-reference/statements/get-statement.md)
- [Příkaz Set](../../../visual-basic/language-reference/statements/set-statement.md)
- [Příkaz Operator](../../../visual-basic/language-reference/statements/operator-statement.md)
- [Příkaz Property](../../../visual-basic/language-reference/statements/property-statement.md)
- [Příkaz Exit](../../../visual-basic/language-reference/statements/exit-statement.md)
- [Příkaz Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
