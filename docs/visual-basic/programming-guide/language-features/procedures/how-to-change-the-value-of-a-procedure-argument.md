---
title: 'Postupy: Změna hodnoty argumentu procedury (Visual Basic)'
ms.date: 07/20/2015
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
ms.openlocfilehash: 6aee795fefe36c2ad19390c0ac6d1613b2199415
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58837483"
---
# <a name="how-to-change-the-value-of-a-procedure-argument-visual-basic"></a>Postupy: Změna hodnoty argumentu procedury (Visual Basic)
Při volání procedury, každý argument, který zadáte odpovídá jednomu z parametrů definovaných v postupu. V některých případech můžete změnit kód procedury hodnotu základní argumentu ve volajícím kódu. V ostatních případech procedura může změnit pouze místní kopie argumentu.  
  
 Při volání postupu Visual Basic vytvoří místní kopii každý argument, který je předán [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md). Každý argument předaný [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), Visual Basic poskytuje kód procedury přímý odkaz na programovací prvek základní argumentu ve volajícím kódu.  
  
 Pokud základní prvek ve volajícím kódu je upravitelná prvek a argument je předán `ByRef`, kód procedury můžete použít přímý odkaz ke změně hodnoty prvku ve volajícím kódu.  
  
## <a name="changing-the-underlying-value"></a>Změna zdrojové hodnoty  
  
#### <a name="to-change-the-underlying-value-of-a-procedure-argument-in-the-calling-code"></a>Chcete-li změnit nadřazenou hodnotu argumentu ve volajícím kódu procedury  
  
1.  V deklaraci procedury zadejte [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) parametru odpovídající argument.  
  
2.  Ve volajícím kódu předáte jako argument upravitelná programovací element.  
  
3.  Ve volajícím kódu neuvádějte argument v závorkách v seznamu argumentů.  
  
4.  V kódu procedury používejte název parametru pro přiřazení hodnoty na základní element ve volajícím kódu.  
  
 Podívejte se na příklad dále dolů ukázku.  
  
## <a name="changing-local-copies"></a>Změna místní kopie  
 Pokud základní prvek ve volajícím kódu je neupravitelnými prvek, nebo pokud je argument předaný `ByVal`, postup nelze změnit jeho hodnotu ve volajícím kódu. Postup však můžete změnit jeho místní kopii těchto argument.  
  
#### <a name="to-change-the-copy-of-a-procedure-argument-in-the-procedure-code"></a>Chcete-li změnit kopie argumentu procedury v kódu procedury  
  
1.  V deklaraci procedury zadejte [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) parametru odpovídající argument.  
  
     -nebo-  
  
     Ve volajícím kódu uzavřete jej do v závorkách v seznamu argumentů. To vynutí jazyka Visual Basic k předání argumentu podle hodnoty, i v případě, že odpovídající parametr určuje `ByRef`.  
  
2.  V kódu procedury používejte název parametru pro přiřazení hodnoty k místní kopie argumentu. Základní hodnota ve volajícím kódu se nezmění.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje dva postupy, které trvat proměnnou pole a provozují na jeho prvků. `increase` Procedura přidá pouze jednu na každý prvek. `replace` Postup přiřadí nové pole parametru `a()` a pak přidá jednu na každý prvek.  
  
 [!code-vb[VbVbcnProcedures#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#35)]  
  
 [!code-vb[VbVbcnProcedures#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#36)]  
  
 [!code-vb[VbVbcnProcedures#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#37)]  
  
 První `MsgBox` volání zobrazí "po increase(n): 11, 21, 31, 41". Protože pole `n` je typem odkazu `replace` lze měnit její členy, i když je mechanismus předávání `ByVal`.  
  
 Druhá `MsgBox` volání zobrazí "po replace(n): 101, 201, 301". Protože `n` je předán `ByRef`, `replace` můžete upravit proměnnou `n` v volající kód a přiřaďte nové pole do něj. Protože `n` je typem odkazu `replace` můžete také změnit jeho členů.  
  
 Postup lze zabránit ve změně samotného proměnné ve volajícím kódu. Zobrazit [jak: Ochrana argumentu procedury proti změnám hodnoty](./how-to-protect-a-procedure-argument-against-value-changes.md).  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Při předání proměnné podle odkazu, je nutné použít `ByRef` – klíčové slovo k určení tento mechanismus.  
  
 Ve výchozím nastavení v jazyce Visual Basic je předání argumentů podle hodnoty. Ale při programování je dobrým zvykem zahrnout buď [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) nebo [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) – klíčové slovo s každou deklarovaný parametr. Díky tomu váš kód lépe čitelný.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Je vždycky představuje potenciální riziko postup, chcete-li změnit hodnotu argumentu ve volajícím kódu základní, kterému je povoleno. Ujistěte se, že očekáváte, že tuto hodnotu změnit a připravit tak zkontrolovat, že platnost před jeho použitím.  
  
## <a name="see-also"></a>Viz také:

- [Procedury](./index.md)
- [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)
- [Postupy: Předání argumentů proceduře](./how-to-pass-arguments-to-a-procedure.md)
- [Předávání argumentů podle hodnoty a reference](./passing-arguments-by-value-and-by-reference.md)
- [Rozdíly mezi upravitelnými a neupravitelnými argumenty](./differences-between-modifiable-and-nonmodifiable-arguments.md)
- [Rozdíly mezi předáním argumentu podle hodnoty a podle reference](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [Postupy: Ochrana argumentu procedury proti změnám hodnoty](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [Postupy: Vynucení argumentu být předána podle hodnoty](./how-to-force-an-argument-to-be-passed-by-value.md)
- [Předávání argumentů podle pozice a názvu](./passing-arguments-by-position-and-by-name.md)
- [Typy hodnot a odkazové typy](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
