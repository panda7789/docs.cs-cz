---
title: Logické a bitové operátory
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
ms.openlocfilehash: 55a246c0d56501a409ebbc7d0d0aa39ae9fa1770
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343597"
---
# <a name="logical-and-bitwise-operators-in-visual-basic"></a>Logické a bitové operátory v jazyce Visual Basic
Logické operátory porovnávají `Boolean` výrazy a vrátí výsledek `Boolean`. Operátory `And`, `Or`, `AndAlso`, `OrElse`a `Xor` jsou *binární* , protože berou dva operandy, zatímco operátor `Not` je *unární* , protože má jeden operand. Některé z těchto operátorů mohou také provádět bitové logické operace s celočíselnými hodnotami.  
  
## <a name="unary-logical-operator"></a>Unární logický operátor  
 [Operátor NOT](../../../../visual-basic/language-reference/operators/not-operator.md) provádí logickou *negaci* pro výraz `Boolean`. Vrací logický opak svého operandu. Pokud se výraz vyhodnotí jako `True`, vrátí `Not` `False`; Pokud je výraz vyhodnocen jako `False`, `Not` vrátí `True`. Toto dokládá následující příklad.  
  
 [!code-vb[VbVbalrOperators#77](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#77)]  
  
## <a name="binary-logical-operators"></a>Binární logické operátory  
 [Operátor and](../../../../visual-basic/language-reference/operators/and-operator.md) provádí logickou *kombinaci* na dvou `Boolean`ch výrazech. Pokud jsou oba výrazy vyhodnoceny jako `True`, `And` vrátí `True`. Pokud se alespoň jeden z výrazů vyhodnotí jako `False`, `And` vrátí `False`.  
  
 [Operátor OR](../../../../visual-basic/language-reference/operators/or-operator.md) provede logickou *disjunkci* nebo *zahrnutí* na dva `Boolean` výrazy. Pokud se jeden výraz vyhodnotí jako `True`nebo se vyhodnotí jako `True`, `Or` vrátí `True`. Pokud není žádný výraz vyhodnocen jako `True`, `Or` vrátí `False`.  
  
 [Operátor XOR](../../../../visual-basic/language-reference/operators/xor-operator.md) provádí logické *vyloučení* dvou `Boolean` výrazů. Pokud se přesně jeden výraz vyhodnotí jako `True`, ale ne obojí, `Xor` vrátí `True`. Pokud se oba výrazy vyhodnotí jako `True` nebo se vyhodnotí jako `False`, `Xor` vrátí `False`.  
  
 Následující příklad ukazuje operátory `And`, `Or`a `Xor`.  
  
 [!code-vb[VbVbalrOperators#78](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#78)]  
  
## <a name="short-circuiting-logical-operations"></a>Logické operace krátkodobého okruhu  
 [Operátor AndAlso –](../../../../visual-basic/language-reference/operators/andalso-operator.md) je velmi podobný operátoru `And`, v tom, že také provádí logické spojení na dvou `Boolean`ch výrazech. Hlavním rozdílem mezi nimi je to, že `AndAlso` vykazuje chování při *krátkém okruhu* . Pokud se první výraz ve výrazu `AndAlso` vyhodnocuje jako `False`, pak druhý výraz není vyhodnocen, protože nemůže změnit konečný výsledek a `AndAlso` vrátí `False`.  
  
 Podobně [operátor OrElse](../../../../visual-basic/language-reference/operators/orelse-operator.md) provádí zkrácenou logickou disjunkci dvou `Boolean` výrazů. Pokud se první výraz ve výrazu `OrElse` vyhodnocuje jako `True`, pak druhý výraz není vyhodnocen, protože nemůže změnit konečný výsledek a `OrElse` vrátí `True`.  
  
### <a name="short-circuiting-trade-offs"></a>Krátkodobé kompromisy  
 Krátkodobé okruhy mohou zvýšit výkon tím, že nevyhodnotí výraz, který nemůže změnit výsledek logické operace. Nicméně pokud tento výraz provede další akce, při krátkém okruhu se tyto akce přeskočí. Například pokud výraz obsahuje volání procedury `Function`, není tato procedura volána, pokud je výraz krátký, a jakýkoliv další kód obsažený v `Function` neběží. Proto může být funkce spuštěna pouze občas a nemusí být testována správně. Nebo logika programu může záviset na kódu v `Function`.  
  
 Následující příklad znázorňuje rozdíl mezi `And`, `Or`a jejich protějšky při jejich krátkodobém okruhu.  
  
 [!code-vb[VbVbalrOperators#81](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#81)]  
  
 [!code-vb[VbVbalrOperators#80](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#80)]  
  
 [!code-vb[VbVbalrOperators#79](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#79)]  
  
 V předchozím příkladu si všimněte, že některé důležité kódy v rámci `checkIfValid()` neběží, když je volání zkrácené. První příkaz `If` volá `checkIfValid()`, i když `12 > 45` vrátí `False`, protože `And` nemá krátký okruh. Druhý příkaz `If` nevolá `checkIfValid()`, protože když `12 > 45` vrátí `False`, `AndAlso` kratší okruh druhý výraz. Třetí příkaz `If` volá `checkIfValid()`, i když `12 < 45` vrátí `True`, protože `Or` nemá krátký okruh. Čtvrtý příkaz `If` nevolá `checkIfValid()`, protože když `12 < 45` vrátí `True`, `OrElse` krátkodobého okruhu druhý výraz.  
  
## <a name="bitwise-operations"></a>Bitové operace  
 Bitové operace vyhodnocují dvě integrální hodnoty v binárním formátu (2. základ). Porovná bity s odpovídajícími pozicemi a pak přiřadí hodnoty na základě porovnání. Následující příklad ilustruje operátor `And`.  
  
 [!code-vb[VbVbalrConcepts#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConcepts/VB/Class1.vb#2)]  
  
 Předchozí příklad nastaví hodnotu `x` na 1. K tomu dochází z následujících důvodů:  
  
- Hodnoty se považují za binární:  
  
     3 v binárním tvaru = 011  
  
     5 v binárním tvaru = 101  
  
- Operátor `And` porovnává binární reprezentace, jednu binární pozici (bitovou) v jednom okamžiku. Pokud jsou obě bity na dané pozici 1, pak je ve výsledku umístěna jedna pozice. Pokud má bit hodnotu 0, pak je na této pozici ve výsledku umístěný 0. V předchozím příkladu to funguje takto:  
  
     011 (3 v binárním formátu)  
  
     101 (5 v binárním formátu)  
  
     001 (výsledek, v binárním formátu)  
  
- Výsledek je považován za desetinný. Hodnota 001 je binární reprezentace 1, takže `x` = 1.  
  
 Bitová operace `Or` je podobná, s tím rozdílem, že 1 je přiřazena ke výslednému bitu, pokud je jedna nebo obě z porovnávaných bitů 1. `Xor` přiřadí ke výslednému bitu 1, pokud je přesně jedna z porovnávaných bitů (ne obojí) 1. `Not` bere jeden operand a Invertuje všechny bity, včetně znaku znaménka, a přiřadí tuto hodnotu k výsledku. To znamená, že u podepsaných kladných čísel `Not` vždycky vrací zápornou hodnotu a pro záporná čísla `Not` vždycky vrací kladnou nebo nulovou hodnotu.  
  
 Operátory `AndAlso` a `OrElse` nepodporují bitové operace.  
  
> [!NOTE]
> Bitové operace lze provádět pouze na integrálních typech. Hodnoty s plovoucí desetinnou čárkou musí být převedeny na integrální typy předtím, než může pokračovat bitová operace.  
  
## <a name="see-also"></a>Viz také:

- [Logické/bitové operátory (Visual Basic)](../../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Logické výrazy](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)
- [Aritmetické operátory v Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [Operátory porovnávání v Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Operátory zřetězení v Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
- [Účinná kombinace operátorů](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
