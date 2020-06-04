---
title: Výrazy logických hodnot
ms.date: 07/20/2015
helpviewer_keywords:
- short-circuiting
- Boolean expressions
- logical operators [Visual Basic], Boolean expressions
- expressions [Visual Basic], Boolean
- expression evaluation [Visual Basic], Boolean expressions
- operators [Visual Basic], short-circuiting
- Visual Basic code, operators
- short-circuit evaluation
- logical operators [Visual Basic], short-circuiting
- operators [Visual Basic], Boolean
- Visual Basic code, expressions
ms.assetid: d3d90406-55c8-4404-8143-50fd7f0d0d1a
ms.openlocfilehash: 8d34eb4c8b14bb4754f2a3cf5b6f9a7601aa4662
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84388955"
---
# <a name="boolean-expressions-visual-basic"></a>Výrazy logických hodnot (Visual Basic)
*Logický výraz* je výraz, který je vyhodnocen jako hodnota [logického datového typu](../../../language-reference/data-types/boolean-data-type.md): `True` nebo `False` . `Boolean`výrazy mohou mít několik forem. Nejjednodušší je přímé porovnání hodnoty `Boolean` proměnné s `Boolean` literálem, jak je znázorněno v následujícím příkladu.  
  
 [!code-vb[VbVbalrOperators#87](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#87)]  
  
## <a name="two-meanings-of-the--operator"></a>Dva významy operátoru =  
 Všimněte si, že příkaz přiřazení `newCustomer = True` vypadá stejně jako výraz v předchozím příkladu, ale provádí jinou funkci a je použit odlišně. V předchozím příkladu výraz `newCustomer = True` představuje logickou hodnotu a `=` znaménko je interpretováno jako operátor porovnání. V samostatném příkazu `=` je znaménko interpretováno jako operátor přiřazení a přiřadí hodnotu na pravé straně k proměnné na levé straně. Toto dokládá následující příklad.  
  
 [!code-vb[VbVbalrOperators#88](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#88)]  
  
 Další informace naleznete v tématu [porovnání hodnot](value-comparisons.md) a [příkazy](../../../language-reference/statements/index.md).  
  
## <a name="comparison-operators"></a>Operátory porovnání  
 Relační operátory, jako `=` například,,, `<` `>` `<>` , `<=` a `>=` poskytují logické výrazy porovnáním výrazu na levé straně operátoru k výrazu na pravé straně operátoru a vyhodnocení výsledku jako `True` nebo `False` . Toto dokládá následující příklad.  
  
 `42 < 81`  
  
 Vzhledem k tomu, že 42 je menší než 81, logický výraz v předchozím příkladu je vyhodnocen jako `True` . Další informace o tomto typu výrazu naleznete v tématu [porovnání hodnot](value-comparisons.md).  
  
### <a name="comparison-operators-combined-with-logical-operators"></a>Operátory porovnání kombinované s logickými operátory  
 Výrazy porovnání lze kombinovat pomocí logických operátorů k tvorbě složitějších logických výrazů. Následující příklad ukazuje použití relačních operátorů ve spojení s logickým operátorem.  
  
 `x > y And x < 1000`  
  
 V předchozím příkladu hodnota celkového výrazu závisí na hodnotách výrazů na každé straně `And` operátoru. Pokud jsou oba výrazy `True` , pak se celkový výraz vyhodnotí jako `True` . Pokud je některý z těchto výrazů `False` , pak se celý výraz vyhodnotí jako `False` .  
  
## <a name="short-circuiting-operators"></a>Operátory krátkodobého okruhu  
 Logické operátory `AndAlso` a `OrElse` chování se projevují jako *krátkodobé okruhy*. Operátor krátkého okruhu nejprve vyhodnocuje levý operand. Pokud levý operand určí hodnotu celého výrazu, pak spuštění programu pokračuje bez vyhodnocení správného výrazu. Toto dokládá následující příklad.  
  
 [!code-vb[VbVbalrOperators#89](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#89)]  
  
 V předchozím příkladu operátor vyhodnocuje levý výraz, `45 < 12` . Vzhledem k tomu, že se levý výraz vyhodnotí jako `False` , musí se celý logický výraz vyhodnotit na `False` . Provádění programu proto přeskočí provádění kódu v rámci `If` bloku bez vyhodnocení pravého výrazu, `testFunction(3)` . Tento příklad nevolá, `testFunction()` protože levý výraz padělaný celý výraz.  
  
 Podobně platí, že pokud se na levém výrazu v logickém výrazu používá `OrElse` vyhodnocení `True` , provádění pokračuje na další řádek kódu bez vyhodnocení pravého výrazu, protože levý výraz již ověřil celý výraz.  
  
### <a name="comparison-with-non-short-circuiting-operators"></a>Porovnání s operátory bez krátkých okruhů  
 Naopak obě strany logického operátoru jsou vyhodnocovány při použití logických operátorů `And` a `Or` . Toto dokládá následující příklad.  
  
 [!code-vb[VbVbalrOperators#90](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#90)]  
  
 Předchozí příklad volá `testFunction()` i v případě, že se levý výraz vyhodnotí jako `False` .  
  
## <a name="parenthetical-expressions"></a>Výrazy kulatého závorky  
 Můžete použít kulaté závorky k řízení pořadí vyhodnocení logických výrazů. Nejprve se vyhodnocují výrazy, které jsou uzavřeny v závorkách. Pro více úrovní vnoření je přednost udělena nejhlouběji vnořeným výrazům. V závorkách hodnocení pokračuje podle pravidel přednosti operátoru. Další informace najdete v tématu [Priorita operátorů v Visual Basic](../../../language-reference/operators/operator-precedence.md).  
  
## <a name="see-also"></a>Viz také

- [Logické a bitové operátory v jazyce Visual Basic](logical-and-bitwise-operators.md)
- [Porovnání hodnot](value-comparisons.md)
- [Příkazy](../statements.md)
- [Operátory porovnání](../../../language-reference/operators/comparison-operators.md)
- [Účinná kombinace operátorů](efficient-combination-of-operators.md)
- [Priorita operátorů v jazyce Visual Basic](../../../language-reference/operators/operator-precedence.md)
- [Boolean – datový typ](../../../language-reference/data-types/boolean-data-type.md)
