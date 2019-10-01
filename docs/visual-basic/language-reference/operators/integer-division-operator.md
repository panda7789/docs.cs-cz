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
ms.openlocfilehash: d1a46f99c21be007d33361ba095a3f0c52fe906c
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701149"
---
# <a name="-operator-visual-basic"></a>\ – operátor (Visual Basic)
Vydělí dvě čísla a vrátí celočíselný výsledek.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
expression1 \ expression2  
```  
  
## <a name="parts"></a>Součásti  
 `expression1`  
 Požadováno. Libovolný číselný výraz.  
  
 `expression2`  
 Požadováno. Libovolný číselný výraz.  
  
## <a name="supported-types"></a>Podporované typy  
 Všechny číselné typy, včetně typů unsigned a float-Point a `Decimal`.  
  
## <a name="result"></a>Výsledek  
 Výsledkem je celočíselná hodnota `expression1` dělená `expression2`, která zahodí všechny zbývající a uchová pouze celočíselnou část. Toto se říká *zkrácení*.  
  
 Výsledný datový typ je číselný typ, který je vhodný pro datové typy `expression1` a `expression2`. Podívejte se na tabulky "celočíselné aritmetické" v [datových typech výsledků operátoru](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).  
  
 [Operátor/(Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) vrátí úplný podíl, který zachová zbytek ve zlomkové části.  
  
## <a name="remarks"></a>Poznámky  
 Před provedením dělení Visual Basic pokusí převést libovolný číselný výraz s plovoucí desetinnou čárkou na `Long`. Pokud je `Option Strict` `On`, dojde k chybě kompilátoru. Pokud je `Option Strict` `Off`, je <xref:System.OverflowException> možné, pokud je hodnota mimo rozsah [dlouhého datového typu](../../../visual-basic/language-reference/data-types/long-data-type.md). Převod na `Long` je také předmětem *zaokrouhlování bank*. Další informace naleznete v části "zlomkové části" v tématu [funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md).  
  
 Pokud je hodnota `expression1` nebo `expression2` vyhodnocena jako [žádná](../../../visual-basic/language-reference/nothing.md), bude považována za nulu.  
  
## <a name="attempted-division-by-zero"></a>Došlo k pokusu o dělení nulou.  
 Pokud je hodnota `expression2` vyhodnocena jako nula, operátor `\` vyvolá výjimku <xref:System.DivideByZeroException>. To platí pro všechny číselné datové typy operandů.  
  
> [!NOTE]
> Operátor `\` lze přetížit, což znamená, že třída nebo struktura může předefinovat *chování, pokud*operand má typ této třídy nebo struktury. Pokud váš kód používá tento operátor na takové třídě nebo struktuře, ujistěte se, že rozumíte jeho předefinovanému chování. Další informace naleznete v tématu [procedury operátorů](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá operátor `\` k provedení dělení celého čísla. Výsledkem je celé číslo, které představuje celočíselný podíl dvou operandů a zbytek byl zahozen.  
  
 [!code-vb[VbVbalrOperators#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#18)]  
  
 Výrazy v předchozím příkladu vrací hodnoty 2, 3, 33 a-22 v uvedeném pořadí.  
  
## <a name="see-also"></a>Viz také:

- [\\ = – operátor](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)
- [/– Operátor (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)
- [Příkaz Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [Aritmetické operátory](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Priorita operátorů v Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Aritmetické operátory v Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
