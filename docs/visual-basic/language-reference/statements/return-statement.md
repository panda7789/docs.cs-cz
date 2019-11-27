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
ms.openlocfilehash: efc85a3a844898345aa2d16926ba0e35d7346d1b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74333018"
---
# <a name="return-statement-visual-basic"></a>Return – příkaz (Visual Basic)
Vrátí řízení kódu, který se nazývá `Function`, `Sub`, `Get`, `Set`nebo `Operator` procedury.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Return  
' -or-  
Return expression  
```  
  
## <a name="part"></a>Částí  
 `expression`  
 Vyžaduje se v `Function`, `Get`nebo `Operator` postupu. Výraz, který představuje hodnotu, která má být vrácena volajícímu kódu.  
  
## <a name="remarks"></a>Poznámky  
 V proceduře `Sub` nebo `Set` je příkaz `Return` ekvivalentem `Exit Sub` nebo příkazu `Exit Property` a `expression` nesmí být dodán.  
  
 V `Function`, `Get`nebo `Operator`, musí příkaz `Return` zahrnovat `expression`a `expression` musí vyhodnotit na datový typ, který lze převést na návratový typ procedury. V proceduře `Function` nebo `Get` máte také alternativu k názvu procedury, která bude sloužit jako návratová hodnota, a následným spuštěním příkazu `Exit Function` nebo `Exit Property`. V `Operator` proceduře je nutné použít `Return expression`.  
  
 Stejným postupem můžete zahrnout tolik `Return` příkazů.  
  
> [!NOTE]
> Kód v `Finally`ovém bloku se spustí po zjištění `Return` v `Try` nebo `Catch` bloku, ale před tím, než se spustí příkaz `Return`. Příkaz `Return` nelze zahrnout do bloku `Finally`.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá příkaz `Return` několikrát pro návrat k volajícímu kódu, když procedura nemusí dělat něco jiného.  
  
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
