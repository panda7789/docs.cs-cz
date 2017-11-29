---
title: "Postupy: Změna hodnoty argumentu procedury (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- procedure arguments
- arguments [Visual Basic], passing by reference
- Visual Basic code, procedures
- arguments [Visual Basic], ByVal
- arguments [Visual Basic], passing by value
- procedure parameters
- arguments [Visual Basic], ByRef
- arguments [Visual Basic], changing value
ms.assetid: 6fad2368-5da7-4c07-8bf8-0f4e65a1be67
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ba23c8f0b4b0b6e751546019af902a6305b9ef53
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-change-the-value-of-a-procedure-argument-visual-basic"></a>Postupy: Změna hodnoty argumentu procedury (Visual Basic)
Při volání procedury, všechny argumenty, které zadáte odpovídá jednomu z parametry definované v postupu. V některých případech můžete kód postupu změňte hodnotu základní argument volající kód. V ostatních případech postupu můžete změnit pouze místní kopie argument.  
  
 Při volání procedury, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] vytvoří místní kopii každý argument, který je předán [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md). Pro každý argument předaný [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] poskytuje kód postup přímý odkaz na programovací element základní argument ve volání kódu.  
  
 Pokud základní element v volání kódu je upravitelnými a argument předaný `ByRef`, kód postup pomocí přímý odkaz můžete změnit hodnotu elementu v kódu volání.  
  
## <a name="changing-the-underlying-value"></a>Změna základní hodnoty  
  
#### <a name="to-change-the-underlying-value-of-a-procedure-argument-in-the-calling-code"></a>Ke změně základní hodnoty argumentu procedury v volání kódu  
  
1.  V deklaraci postupu zadejte [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) pro parametr odpovídající argument.  
  
2.  V kód volání předáte jako argument upravitelnými programovací element.  
  
3.  Ve volání kódu neuvádějte argumentem v závorkách v seznamu argumentů.  
  
4.  V postupu kódu použijte název parametru o přiřazení hodnoty k základní elementu v kódu volání.  
  
 Podívejte se na příklad další dolů pro předvedení.  
  
## <a name="changing-local-copies"></a>Změna místní kopie  
 Pokud základní element v volání kódu je neupravitelnými, nebo pokud je argument předaný `ByVal`, postup jeho hodnoty volající kód nelze změnit. Postup však můžete změnit jeho místní kopii takové argument.  
  
#### <a name="to-change-the-copy-of-a-procedure-argument-in-the-procedure-code"></a>Chcete-li změnit kopii argumentu procedury v postupu kódu  
  
1.  V deklaraci postupu zadejte [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) pro parametr odpovídající argument.  
  
     -nebo-  
  
     Ve volání kódu uzavřete jej v závorkách v seznamu argumentů. Vynutí se tak [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] k předání argumentu podle hodnoty, i v případě, že odpovídající parametr určuje `ByRef`.  
  
2.  V postupu kódu použijte název parametru o přiřazení hodnoty k místní kopii argument. Zadaná hodnota v volání kódu se nezmění.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje dva postupy, které provádějí proměnné pole a pracovat na jeho elementy. `increase` Postup jednoduše přidá jeden na každý element. `replace` Postup přiřadí nové pole do parametru `a()` a potom přidá jeden na každý element.  
  
 [!code-vb[VbVbcnProcedures#35](./codesnippet/VisualBasic/how-to-change-the-value-of-a-procedure-argument_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#36](./codesnippet/VisualBasic/how-to-change-the-value-of-a-procedure-argument_2.vb)]  
  
 [!code-vb[VbVbcnProcedures#37](./codesnippet/VisualBasic/how-to-change-the-value-of-a-procedure-argument_3.vb)]  
  
 První `MsgBox` volání zobrazí "po increase(n): 11, 21, 31, 41". Protože pole `n` je typu odkazu `replace` můžete změnit její členy, i když tento mechanismus předávání `ByVal`.  
  
 Druhý `MsgBox` volání zobrazí "po replace(n): 101, 201, 301". Protože `n` je předán `ByRef`, `replace` můžete upravit proměnnou `n` v kódu na volání a přiřazení nové pole do ní. Protože `n` je typu odkazu `replace` můžete také změnit její členy.  
  
 Můžete zabránit postup úpravy proměnné sám v volající kód. V tématu [postupy: ochrana argumentu procedury proti změnám hodnoty](./how-to-protect-a-procedure-argument-against-value-changes.md).  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Pokud předáte proměnné odkazem, je nutné použít `ByRef` – klíčové slovo zadat Tento mechanismus.  
  
 Výchozí hodnota v [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] je předání argumentů hodnotou. Ale je dobrým zvykem obsahovat buď programovacím [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) nebo [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) – klíčové slovo s každou deklarovaný parametr. To výrazně zjednodušuje kódu ke čtení.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Postup ke změně hodnoty základní argument volající kód, který umožňuje existuje vždy představuje potenciální riziko. Ujistěte se, že byste měli tuto hodnotu změnit, a zkontrolujte správnost před jeho použitím připravit.  
  
## <a name="see-also"></a>Viz také  
 [Postupy](./index.md)  
 [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)  
 [Postupy: předání argumentů proceduře](./how-to-pass-arguments-to-a-procedure.md)  
 [Předávání argumentů podle hodnoty a podle Reference](./passing-arguments-by-value-and-by-reference.md)  
 [Rozdíly mezi upravitelnými a Neupravitelnými argumenty](./differences-between-modifiable-and-nonmodifiable-arguments.md)  
 [Rozdíly mezi předáním argumentu podle hodnoty a podle Reference](./differences-between-passing-an-argument-by-value-and-by-reference.md)  
 [Postupy: ochrana argumentu procedury proti změnám hodnoty](./how-to-protect-a-procedure-argument-against-value-changes.md)  
 [Postupy: vynucení předání hodnotou argumentu](./how-to-force-an-argument-to-be-passed-by-value.md)  
 [Předávání argumentů podle pozice a názvu](./passing-arguments-by-position-and-by-name.md)  
 [Typy hodnot a odkazové typy](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
