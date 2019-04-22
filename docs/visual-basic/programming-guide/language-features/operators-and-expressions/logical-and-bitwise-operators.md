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
ms.openlocfilehash: ac47b6d7fa4861d18646a23f442caccc4062852f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58819304"
---
# <a name="logical-and-bitwise-operators-in-visual-basic"></a>Logické a bitové operátory v jazyce Visual Basic
Logické operátory porovnávají `Boolean` výrazy a vraťte se `Boolean` výsledek. `And`, `Or`, `AndAlso`, `OrElse`, A `Xor` operátory jsou *binární* protože přijímají dva operandy, zatímco `Not` operátor je *unární* protože trvá jeden operand. Některé z těchto operátorů lze provést také bitové logické operace na integrální hodnoty.  
  
## <a name="unary-logical-operator"></a>Unární logický operátor  
 [Operátor Not](../../../../visual-basic/language-reference/operators/not-operator.md) provádí logické *negace* na `Boolean` výrazu. Bude vrácen na logický protějšek svého operandu. Pokud je výraz vyhodnocen `True`, pak `Not` vrátí `False`; Pokud je výraz vyhodnocen `False`, pak `Not` vrátí `True`. Toto dokládá následující příklad.  
  
 [!code-vb[VbVbalrOperators#77](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#77)]  
  
## <a name="binary-logical-operators"></a>Binární logické operátory  
 [Operátoru](../../../../visual-basic/language-reference/operators/and-operator.md) provádí logické *spojení* na dvou `Boolean` výrazy. Pokud mají oba výrazy `True`, pak `And` vrátí `True`. Pokud se alespoň jeden z výrazů vyhodnotí jako `False`, pak `And` vrátí `False`.  
  
 [Nebo operátor](../../../../visual-basic/language-reference/operators/or-operator.md) provádí logické *disjunkce* nebo *zahrnutí* na dvou `Boolean` výrazy. Pokud je výraz vyhodnocen jako `True`, nebo obojí vyhodnotit `True`, pak `Or` vrátí `True`. Pokud ani výraz nevyhodnotí jako `True`, `Or` vrátí `False`.  
  
 [Xor Operátor](../../../../visual-basic/language-reference/operators/xor-operator.md) provádí logické *vyloučení* na dvou `Boolean` výrazy. Pokud se přesně jeden výraz vyhodnotí jako `True`, ale ne obojí `Xor` vrátí `True`. Pokud mají oba výrazy `True` nebo obojí vyhodnotit `False`, `Xor` vrátí `False`.  
  
 Následující příklad ukazuje, `And`, `Or`, a `Xor` operátory.  
  
 [!code-vb[VbVbalrOperators#78](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#78)]  
  
## <a name="short-circuiting-logical-operations"></a>Zkrácení logické operace  
 [AndAlso – operátor](../../../../visual-basic/language-reference/operators/andalso-operator.md) je velmi podobný `And` operátor v tom, že také provede logickou konjunkci na dvou `Boolean` výrazy. Klíčovým rozdílem mezi těmito dvěma je, že `AndAlso` vykazuje *zkrácenou* chování. Pokud k prvnímu výrazu v `AndAlso` výraz vyhodnocen jako `False`, a druhý výraz není vyhodnocen, protože ji nelze změnit na konečný výsledek a `AndAlso` vrátí `False`.  
  
 Podobně platí [OrElse – operátor](../../../../visual-basic/language-reference/operators/orelse-operator.md) provede zkrácenou logickou disjunkci dvou `Boolean` výrazy. Pokud k prvnímu výrazu v `OrElse` výraz vyhodnocen jako `True`, a druhý výraz není vyhodnocen, protože ji nelze změnit na konečný výsledek a `OrElse` vrátí `True`.  
  
### <a name="short-circuiting-trade-offs"></a>Krátký cyklus kompromisy  
 Krátký cyklus lze vylepšit výkon není vyhodnocení výrazu, který nejde změnit výsledek logické operace. Pokud tento výraz provede další akce, ale zkrácenou přeskočí těchto akcí. Například, pokud výraz obsahuje volání `Function` postupu, že postup není volána, pokud má výraz hodnotu zkratována a žádný další kód obsažený v `Function` se nespustí. Proto funkce může spustit jenom občas a nemusí být správně testována. Nebo aplikaci logiky může záviset na kód v `Function`.  
  
 Následující příklad ukazuje rozdíl mezi `And`, `Or`a jejich protějšky short-circuiting.  
  
 [!code-vb[VbVbalrOperators#81](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#81)]  
  
 [!code-vb[VbVbalrOperators#80](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#80)]  
  
 [!code-vb[VbVbalrOperators#79](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#79)]  
  
 V předchozím příkladu, Všimněte si, že některé důležité kód uvnitř `checkIfValid()` při volání je zkratována nespustí. První `If` příkaz volá `checkIfValid()` Přestože `12 > 45` vrátí `False`, protože `And` není zkrácenou. Druhá `If` příkaz nevolá `checkIfValid()`, protože při `12 > 45` vrátí `False`, `AndAlso` zkratům druhý výraz. Třetí `If` příkaz volá `checkIfValid()` Přestože `12 < 45` vrátí `True`, protože `Or` není zkrácenou. Čtvrtý `If` příkaz nevolá `checkIfValid()`, protože při `12 < 45` vrátí `True`, `OrElse` zkratům druhý výraz.  
  
## <a name="bitwise-operations"></a>Bitové operace  
 Bitové operace vyhodnotit dvě celočíselné hodnoty ve formuláři binární soubor (základní 2). Jejich porovnání bity na odpovídající pozice a pak přiřaďte hodnoty založené na porovnání. Následující příklad ukazuje, `And` operátor.  
  
 [!code-vb[VbVbalrConcepts#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConcepts/VB/Class1.vb#2)]  
  
 Předchozí příklad nastaví hodnotu `x` na hodnotu 1. V takovém z následujících důvodů:  
  
-   Hodnoty jsou považovány za binární soubor:  
  
     3 v binárním formátu = 011  
  
     5 v binárním formátu = 101  
  
-   `And` Operátor porovnání vícebinární reprezentace jednu binární pozici (verze) v čase. Pokud i službu bits na dané pozici 1, 1 je umístěn na této pozici ve výsledku. Pokud buď bit na hodnotu 0, 0 je umístěn na této pozici ve výsledku. V předchozím příkladu toto funguje takto:  
  
     011 (3 v binárním formátu)  
  
     101 (5 v binárním formátu)  
  
     001 (výsledek, v binárním formátu)  
  
-   Výsledkem je považováno za desítkové. Hodnota 001 je binární reprezentace 1, takže `x` = 1.  
  
 Bitový `Or` operace je podobný s tím rozdílem, že 1 je přiřazena k bitu výsledku, pokud jeden nebo oba z porovnání bitů je 1. `Xor` přiřadí k bitu výsledku 1, v případě, že právě jeden z porovnání bity (ne oba) je 1. `Not` přijímá jeden operand obrátí všechny bity, včetně bitu a přiřadí tuto hodnotu na výsledek. To znamená, že pro podepsané kladná čísla `Not` vždy vrátí zápornou hodnotu a záporných čísel `Not` vždy vrátí hodnotu pozitivní nebo nulovou hodnotu.  
  
 `AndAlso` a `OrElse` operátory nepodporuje bitové operace.  
  
> [!NOTE]
>  Bitová operace lze provádět na pouze pro integrální typy. Hodnoty s plovoucí desetinnou čárkou musí převést na integrální typy než bitová operace můžete pokračovat.  
  
## <a name="see-also"></a>Viz také:

- [Logické/bitové operátory (Visual Basic)](../../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Logické výrazy](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)
- [Aritmetické operátory v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [Operátory porovnání v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Operátory řetězení v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
- [Účinná kombinace operátorů](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
