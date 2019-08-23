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
ms.openlocfilehash: 40076b2ad6606b4c565bcd39dbeea9e55da47211
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963308"
---
# <a name="logical-and-bitwise-operators-in-visual-basic"></a>Logické a bitové operátory v jazyce Visual Basic
Logické operátory porovnávají `Boolean` výrazy a `Boolean` vracejí výsledek. `And` `Not` Operátory, `Or`, `AndAlso`, ajsoubinární,protožepřebírajídvaoperandy,zatímcooperátorjeunární,protožepoužívájedenoperand.`OrElse` `Xor` Některé z těchto operátorů mohou také provádět bitové logické operace s celočíselnými hodnotami.  
  
## <a name="unary-logical-operator"></a>Unární logický operátor  
 [Operátor NOT](../../../../visual-basic/language-reference/operators/not-operator.md) provádí logickou *negaci* `Boolean` výrazu. Vrací logický opak svého operandu. Pokud se výraz vyhodnotí `True`jako, `Not` pak `False`vrátí hodnotu; Pokud se výraz vyhodnotí `Not` `False`jako `True`, pak vrátí. Toto dokládá následující příklad.  
  
 [!code-vb[VbVbalrOperators#77](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#77)]  
  
## <a name="binary-logical-operators"></a>Binární logické operátory  
 [Operátor and](../../../../visual-basic/language-reference/operators/and-operator.md) provádí logickou *kombinaci* dvou `Boolean` výrazů. Pokud se oba výrazy vyhodnotí `True`, `True`pak `And` vrátí. Pokud se alespoň jeden z výrazů vyhodnotí `False`jako, pak `And` vrátí. `False`  
  
 [Operátor OR](../../../../visual-basic/language-reference/operators/or-operator.md) provádí logickou disjunkci nebo *zahrnutí* ve `Boolean` dvou výrazech. Pokud se jeden `True`výraz vyhodnotí jako, nebo vyhodnotí na `True` `True`, a pak `Or` vrátí. Pokud není žádný výraz vyhodnocen `True`jako `Or` , `False`vrátí.  
  
 [Operátor XOR](../../../../visual-basic/language-reference/operators/xor-operator.md) provádí logické *vyloučení* dvou `Boolean` výrazů. Pokud se přesně jeden výraz vyhodnotí `True`jako, ale ne obojí, `Xor` vrátí `True`. Pokud `True` `False`jsou oba výrazy vyhodnoceny nebo vyhodnoceny `False`jako, `Xor` vrátí.  
  
 Následující příklad ukazuje `And`operátory, `Or`a `Xor` .  
  
 [!code-vb[VbVbalrOperators#78](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#78)]  
  
## <a name="short-circuiting-logical-operations"></a>Logické operace krátkodobého okruhu  
 [Operátor AndAlso –](../../../../visual-basic/language-reference/operators/andalso-operator.md) je velmi podobný `And` operátoru, v tom, že také provádí logické spojení dvou `Boolean` výrazů. Klíčový rozdíl mezi těmito dvěma prvky je, `AndAlso` který vykazuje chování při *krátkém okruhu* . Pokud se `AndAlso` první výraz ve výrazu vyhodnocuje `False`jako, pak druhý výraz není vyhodnocen, protože nemůže změnit konečný výsledek a `AndAlso` vrátí `False`.  
  
 Podobně [operátor OrElse](../../../../visual-basic/language-reference/operators/orelse-operator.md) provádí zkrácenou logickou disjunkci dvou `Boolean` výrazů. Pokud se `OrElse` první výraz ve výrazu vyhodnocuje `True`jako, pak druhý výraz není vyhodnocen, protože nemůže změnit konečný výsledek a `OrElse` vrátí `True`.  
  
### <a name="short-circuiting-trade-offs"></a>Krátkodobé kompromisy  
 Krátkodobé okruhy mohou zvýšit výkon tím, že nevyhodnotí výraz, který nemůže změnit výsledek logické operace. Nicméně pokud tento výraz provede další akce, při krátkém okruhu se tyto akce přeskočí. Například pokud výraz obsahuje volání `Function` procedury, tato procedura není volána, pokud je výraz zkrácen a jakýkoliv další kód obsažený `Function` v nespustí. Proto může být funkce spuštěna pouze občas a nemusí být testována správně. Nebo je možné, že logika programu může záviset na `Function`kódu v.  
  
 Následující příklad znázorňuje rozdíl mezi `And`, `Or`a jejich protějšky na jejich krátkodobé okruhy.  
  
 [!code-vb[VbVbalrOperators#81](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#81)]  
  
 [!code-vb[VbVbalrOperators#80](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#80)]  
  
 [!code-vb[VbVbalrOperators#79](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#79)]  
  
 V předchozím příkladu si všimněte, že některé důležité kódy uvnitř `checkIfValid()` nejsou spouštěny, když je volání zkráceno. `If` První příkaz volá `checkIfValid()` i když `12 > 45` vrátí `False`, protože`And` není krátký okruh. Druhý `If` příkaz nevolá `checkIfValid()`, protože když `12 > 45` vrátí `False`, `AndAlso` je pro něj druhý výraz. `If` Třetí příkaz volá `checkIfValid()` i když `12 < 45` vrátí `True`, protože`Or` není krátký okruh. Čtvrtý `If` příkaz nevolá `checkIfValid()`, protože když `12 < 45` vrátí `True`, `OrElse` je pro něj druhý výraz.  
  
## <a name="bitwise-operations"></a>Bitové operace  
 Bitové operace vyhodnocují dvě integrální hodnoty v binárním formátu (2. základ). Porovná bity s odpovídajícími pozicemi a pak přiřadí hodnoty na základě porovnání. Následující příklad znázorňuje `And` operátor.  
  
 [!code-vb[VbVbalrConcepts#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConcepts/VB/Class1.vb#2)]  
  
 Předchozí příklad nastaví hodnotu `x` na 1. K tomu dochází z následujících důvodů:  
  
- Hodnoty se považují za binární:  
  
     3 v binárním tvaru = 011  
  
     5 v binárním tvaru = 101  
  
- `And` Operátor porovnává binární reprezentace, jednu binární pozici (bitovou) v jednom okamžiku. Pokud jsou obě bity na dané pozici 1, pak je ve výsledku umístěna jedna pozice. Pokud má bit hodnotu 0, pak je na této pozici ve výsledku umístěný 0. V předchozím příkladu to funguje takto:  
  
     011 (3 v binárním formátu)  
  
     101 (5 v binárním formátu)  
  
     001 (výsledek, v binárním formátu)  
  
- Výsledek je považován za desetinný. Hodnota 001 je binární reprezentace 1, takže `x` = 1.  
  
 Bitová `Or` operace je podobná, s tím rozdílem, že k výslednému bitu je přiřazena 1, pokud je jedna nebo obě z porovnávaných bitů 1. `Xor`přiřadí ke výslednému bitu 1, pokud je přesně jedna z porovnávaných bitů (ne obojí) 1. `Not`provede jeden operand a Invertuje všechny bity, včetně znaku znaménka, a přiřadí tuto hodnotu k výsledku. To znamená, že u podepsaných kladných čísel `Not` vždycky vrátí zápornou hodnotu a pro záporná `Not` čísla vždycky Vrátí kladnou nebo nulovou hodnotu.  
  
 Operátory `AndAlso` a`OrElse` nepodporují bitové operace.  
  
> [!NOTE]
> Bitové operace lze provádět pouze na integrálních typech. Hodnoty s plovoucí desetinnou čárkou musí být převedeny na integrální typy předtím, než může pokračovat bitová operace.  
  
## <a name="see-also"></a>Viz také:

- [Logické/bitové operátory (Visual Basic)](../../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Logické výrazy](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)
- [Aritmetické operátory v Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [Operátory porovnávání v Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Operátory zřetězení v Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
- [Účinná kombinace operátorů](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
