---
title: Logické a bitové operátory v jazyce Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- short-circuiting
- Boolean expressions
- logical operators [Visual Basic], Boolean expressions
- operators [Visual Basic], logical
- AndAlso operator [Visual Basic]
- Not operator [Visual Basic], Boolean expressions
- Xor operator [Visual Basic], Boolean expressions
- And operator [Visual Basic], logical operators
- logical operators [Visual Basic]
- expressions [Visual Basic], Boolean
- Or operator [Visual Basic], logical operators
- Visual Basic code, operators
- short-circuiting [Visual Basic], logical operators
- logical operators [Visual Basic], short-circuiting
- Visual Basic code, expressions
- logical operators [Visual Basic], binary
- OrElse operator [Visual Basic]
- logical operators [Visual Basic], unary
ms.assetid: ca474e13-567d-4b1d-a18b-301433705e57
ms.openlocfilehash: 371d28629b39fb2808ca018ea69da3306a31f50c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33656149"
---
# <a name="logical-and-bitwise-operators-in-visual-basic"></a>Logické a bitové operátory v jazyce Visual Basic
Logické operátory porovnání `Boolean` výrazy a vraťte se `Boolean` výsledek. `And`, `Or`, `AndAlso`, `OrElse`, A `Xor` operátory jsou *binární* vzhledem k tomu, že jejich trvat dva operandy, při `Not` operátor je *unární* vzhledem k tomu, jak dlouho trvá jeden operand. Některé z těchto operátorů můžete také provést bitové logické operace na celočíselné hodnoty.  
  
## <a name="unary-logical-operator"></a>Unární logický operátor  
 [Operátor Not](../../../../visual-basic/language-reference/operators/not-operator.md) provede logické *negace* na `Boolean` výraz. Vrací logickou opak jeho operand. Pokud je výsledkem výrazu `True`, pak `Not` vrátí `False`; Pokud je výsledkem výrazu `False`, pak `Not` vrátí `True`. Toto dokládá následující příklad.  
  
 [!code-vb[VbVbalrOperators#77](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/logical-and-bitwise-operators_1.vb)]  
  
## <a name="binary-logical-operators"></a>Binární logické operátory  
 [a operátor](../../../../visual-basic/language-reference/operators/and-operator.md) provede logické *spojení* na dva `Boolean` výrazy. Pokud jsou oba výrazy vyhodnoceny `True`, pak `And` vrátí `True`. Pokud je alespoň jeden z výrazů výsledkem `False`, pak `And` vrátí `False`.  
  
 [Operátor nebo](../../../../visual-basic/language-reference/operators/or-operator.md) provede logické *disjunkce* nebo *zahrnutí* na dva `Boolean` výrazy. Pokud výraz vyhodnocen jako `True`, nebo obě vyhodnocení `True`, pak `Or` vrátí `True`. Pokud ani výraz vyhodnocen `True`, `Or` vrátí `False`.  
  
 [Xor Operátor](../../../../visual-basic/language-reference/operators/xor-operator.md) provede logické *vyloučení* na dva `Boolean` výrazy. Pokud je výsledkem přesně jeden výraz `True`, ale ne obojí `Xor` vrátí `True`. Pokud jsou oba výrazy vyhodnoceny `True` nebo obě vyhodnocení `False`, `Xor` vrátí `False`.  
  
 Následující příklad ukazuje `And`, `Or`, a `Xor` operátory.  
  
 [!code-vb[VbVbalrOperators#78](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/logical-and-bitwise-operators_2.vb)]  
  
## <a name="short-circuiting-logical-operations"></a>Krátká smyčka logických operací  
 [AndAlso – operátor](../../../../visual-basic/language-reference/operators/andalso-operator.md) je velmi podobné `And` operátor, v tom, že provádí taky logické spojení na dva `Boolean` výrazy. Klíčovým rozdílem mezi těmito dvěma je, že `AndAlso` jádro vykazuje *krátká smyčka* chování. Pokud k prvnímu výrazu v `AndAlso` výraz vyhodnocen jako `False`, pak je výraz druhé není vyhodnotit, protože jej nelze změnit konečný výsledek a `AndAlso` vrátí `False`.  
  
 Podobně [orelse – operátor](../../../../visual-basic/language-reference/operators/orelse-operator.md) provede zkrácenou logickou disjunkci dvou `Boolean` výrazy. Pokud k prvnímu výrazu v `OrElse` výraz vyhodnocen jako `True`, pak je výraz druhé není vyhodnotit, protože jej nelze změnit konečný výsledek a `OrElse` vrátí `True`.  
  
### <a name="short-circuiting-trade-offs"></a>Krátká smyčka kompromis  
 Krátká smyčka může zlepšit výkon není vyhodnocením výraz, který nelze změnit výsledek logické operace. Pokud tento výraz provede další akce, ale krátká smyčka přeskočí tyto akce. Například, pokud výraz obsahuje volání `Function` postupu, že není procedura volána, pokud je výraz zkratována a všechny další kód obsažené v `Function` není spuštěna. Proto funkce může spustit pouze občas a nemusí být testována správně. Nebo program logiku může záviset na kód `Function`.  
  
 Následující příklad ukazuje rozdíl mezi `And`, `Or`a jejich short-circuiting protějšky.  
  
 [!code-vb[VbVbalrOperators#81](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/logical-and-bitwise-operators_3.vb)]  
  
 [!code-vb[VbVbalrOperators#80](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/logical-and-bitwise-operators_4.vb)]  
  
 [!code-vb[VbVbalrOperators#79](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/logical-and-bitwise-operators_5.vb)]  
  
 V předchozím příkladu, Všimněte si, že některé důležité kód uvnitř `checkIfValid()` nejde spustit po zkratována volání. První `If` příkaz volání `checkIfValid()` i když `12 > 45` vrátí `False`, protože `And` není krátká smyčka. Druhý `If` příkaz nevyvolá `checkIfValid()`, protože při `12 > 45` vrátí `False`, `AndAlso` zkratům druhý výraz. Třetí `If` příkaz volání `checkIfValid()` i když `12 < 45` vrátí `True`, protože `Or` není krátká smyčka. Čtvrtý `If` příkaz nevyvolá `checkIfValid()`, protože při `12 < 45` vrátí `True`, `OrElse` zkratům druhý výraz.  
  
## <a name="bitwise-operations"></a>Bitové operace  
 Bitové operace vyhodnotit dvě celočíselné hodnoty v podobě binárního souboru (se základem 2). Tyto porovnat bits na odpovídající pozic a přiřadit hodnoty, které jsou založeny na porovnávání. Následující příklad ukazuje `And` operátor.  
  
 [!code-vb[VbVbalrConcepts#2](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/codesnippet/VisualBasic/logical-and-bitwise-operators_6.vb)]  
  
 V předchozím příkladu nastaví hodnotu `x` na 1. To se stane z následujících důvodů:  
  
-   Hodnoty jsou považovány za binární:  
  
     3 v binárním formátu = 011  
  
     5 v binárním formátu = 101  
  
-   `And` Operátor porovná binární reprezentace jednu binární pozici (verze) v čase. Pokud jsou obě služby bits na dané pozici 1, 1 umístit na této pozici v výsledek. Pokud je buď bit 0, 0 je umístěn na této pozici v výsledek. V předchozím příkladu toto funguje takto:  
  
     011 (3 v binárním formátu)  
  
     101 (5 v binárním formátu)  
  
     001 (výsledek v binárním formátu)  
  
-   Výsledkem je považována za decimal. Hodnota 001 je binární reprezentace 1, takže `x` = 1.  
  
 Bitové hodnotě `Or` operace je podobné, s tím rozdílem, že 1 je přiřazen k bit výsledek, pokud jedné nebo obou porovnání bits je 1. `Xor` přiřadí bit výsledek 1, pokud právě jeden z porovnání služby bits (ne obojí) je 1. `Not` má jeden operand Invertuje výběr všech bitů, včetně bit přihlášení a přiřadí tuto hodnotu na výsledek. To znamená, že pro přihlášení kladná čísla `Not` vždy vrátí hodnotu záporná a záporná čísla `Not` vždy vrátí hodnotu u kladné číslo nebo nula.  
  
 `AndAlso` a `OrElse` operátory nepodporují bitové operace.  
  
> [!NOTE]
>  Bitové operace můžete provádět na pouze pro integrální typy. Hodnoty s plovoucí desetinnou čárkou musí před pokračováním bitové operace převést na integrální typy.  
  
## <a name="see-also"></a>Viz také  
 [Logické/bitové operátory (Visual Basic)](../../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)  
 [Logické výrazy](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)  
 [Aritmetické operátory v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)  
 [Operátory porovnání v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)  
 [Operátory řetězení v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)  
 [Účinná kombinace operátorů](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
