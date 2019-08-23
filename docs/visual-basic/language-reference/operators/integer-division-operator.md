---
title: '\ – operátor (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.\
- '\'
helpviewer_keywords:
- division operator [Visual Basic], integer
- integer division operator [Visual Basic]
- zero, division by zero
- arithmetic operators [Visual Basic], division
- division [Visual Basic], by zero
- backslash (\) [Visual Basic]
- '\ operator [Visual Basic]'
- integer quotient
- math operators [Visual Basic]
- quotients, integer
- truncation [Visual Basic], integer division
ms.assetid: 4b0ee347-950c-45c9-8e23-54bc85df208e
ms.openlocfilehash: 276071fef3632d1a617f177b6fe18026b290103a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917242"
---
# <a name="-operator-visual-basic"></a>\ – operátor (Visual Basic)
Vydělí dvě čísla a vrátí celočíselný výsledek.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
expression1 \ expression2  
```  
  
## <a name="parts"></a>Součásti  
 `expression1`  
 Povinný parametr. Libovolný číselný výraz.  
  
 `expression2`  
 Povinný parametr. Libovolný číselný výraz.  
  
## <a name="supported-types"></a>Podporované typy  
 Všechny číselné typy, včetně typů unsigned a float-Point a `Decimal`.  
  
## <a name="result"></a>Výsledek  
 Výsledkem je celočíselný podíl `expression1` dělený pomocí `expression2`, který zahodí všechny zbývající a uchová pouze celočíselnou část. Toto se říká *zkrácení*.  
  
 Výsledný datový typ je číselný typ odpovídající datovým typům `expression1` a. `expression2` Podívejte se na tabulky "celočíselné aritmetické" v [datových typech výsledků operátoru](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).  
  
 [Operátor/(Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) vrátí úplný podíl, který zachová zbytek ve zlomkové části.  
  
## <a name="remarks"></a>Poznámky  
 Před provedením dělení Visual Basic pokusy o převod libovolného číselného výrazu s plovoucí desetinnou čárkou na `Long`. V takovém případě `Option Strict` dojde k chybě kompilátoru. `On` Pokud `Option Strict` <xref:System.OverflowException> je `Off`, je možné, že je hodnota mimo rozsah [dlouhého datového typu](../../../visual-basic/language-reference/data-types/long-data-type.md). Převod na `Long` je také předmětem *zaokrouhlování bank*. Další informace naleznete v části "zlomkové části" v tématu [funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md).  
  
 Pokud `expression1` je `expression2` nebo se vyhodnotí jako [Nothing](../../../visual-basic/language-reference/nothing.md), bude se zacházet jako nula.  
  
## <a name="attempted-division-by-zero"></a>Došlo k pokusu o dělení nulou.  
 Pokud `expression2` je hodnota vyhodnocena jako `\` nula, operátor <xref:System.DivideByZeroException> vyvolá výjimku. To platí pro všechny číselné datové typy operandů.  
  
> [!NOTE]
> Operátor může být přetížen, což znamená, že třída nebo struktura může předefinovat své chování, pokud má operand typ této třídy nebo struktury. `\` Pokud váš kód používá tento operátor na takové třídě nebo struktuře, ujistěte se, že rozumíte jeho předefinovanému chování. Další informace naleznete v tématu [procedury operátorů](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `\` operátor k provedení dělení celého čísla. Výsledkem je celé číslo, které představuje celočíselný podíl dvou operandů a zbytek byl zahozen.  
  
 [!code-vb[VbVbalrOperators#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#18)]  
  
 Výrazy v předchozím příkladu vrací hodnoty 2, 3, 33 a-22 v uvedeném pořadí.  
  
## <a name="see-also"></a>Viz také:

- [\\= – Operátor](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)
- [/– Operátor (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)
- [Příkaz Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [Aritmetické operátory](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Priorita operátorů v Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Aritmetické operátory v Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
