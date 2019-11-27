---
title: 'Postupy: Definování parametru pro proceduru'
ms.date: 07/20/2015
helpviewer_keywords:
- procedure parameters [Visual Basic], defining data types for
- procedures [Visual Basic], parameters
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedure parameters [Visual Basic], defining
ms.assetid: 7962808d-407e-4e84-984e-43e9857c53c9
ms.openlocfilehash: 411959a7be92ea49a59558b508e992bfba8eff95
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344887"
---
# <a name="how-to-define-a-parameter-for-a-procedure-visual-basic"></a>Postupy: Definování parametru pro proceduru (Visual Basic)
*Parametr* umožňuje volajícímu kódu předat hodnotu proceduře při jeho volání. Každý parametr pro proceduru deklarujete stejným způsobem jako proměnnou, a to zadáním jejího názvu a datového typu. Zadáte také mechanismus předávání a zda je parametr volitelný.  
  
 Další informace najdete v tématu [parametry a argumenty procedury](./procedure-parameters-and-arguments.md).  
  
### <a name="to-define-a-procedure-parameter"></a>Definování parametru procedury  
  
1. V deklaraci procedury přidejte název parametru do seznamu parametrů procedury a oddělte jej od ostatních parametrů čárkami.  
  
2. Určete datový typ parametru.  
  
3. Použijte název parametru s klauzulí `As` a určete datový typ.  
  
4. Určete mechanismus předávání, který chcete pro parametr. Obvykle předáte parametr podle hodnoty, pokud nechcete, aby procedura mohla měnit jeho hodnotu v volajícím kódu.  
  
5. Před názvem parametru s klíčovým slovem [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) nebo [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) zadejte mechanismus předávání. Další informace naleznete v tématu [rozdíly mezi předáním argumentu podle hodnoty a podle reference](./differences-between-passing-an-argument-by-value-and-by-reference.md).  
  
6. Pokud je parametr nepovinný, předchází mechanismus předání s [volitelným](../../../../visual-basic/language-reference/modifiers/optional.md) a následuje datový typ parametru se symbolem rovná se (`=`) a výchozí hodnotou.  
  
     Následující příklad definuje osnovu `Sub` proceduře se třemi parametry. První dvě jsou povinná a třetí je volitelná. Deklarace parametrů jsou v seznamu parametrů odděleny čárkami.  
  
     [!code-vb[VbVbcnProcedures#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#33)]  
  
     První parametr přijímá objekt `customer` a `updateCustomer` může přímo aktualizovat proměnnou předanou `c`, protože argument je předán jako typ [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md). Procedura nemůže změnit hodnoty posledních dvou argumentů, protože jsou předány metodě [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).  
  
     Pokud volající kód neposkytuje hodnotu parametru `level`, Visual Basic jej nastaví na výchozí hodnotu 0.  
  
     Pokud je přepínač pro kontrolu typu ([příkaz Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) `Off`, klauzule `As` je při definování parametru volitelná. Nicméně, pokud některý z parametrů používá klauzuli `As`, všechny je musí použít. Pokud je přepínač pro kontrolu typu `On`, je klauzule `As` požadována pro každou definici parametru.  
  
     Zadání datových typů pro všechny vaše programovací prvky se nazývá *silného psaní*. Když nastavíte `Option Strict On`, Visual Basic vynutilo silné psaní. Tento postup se doporučuje z následujících důvodů:  
  
    - Umožňuje podporu technologie IntelliSense pro vaše proměnné a parametry. To vám umožní zobrazit jejich vlastnosti a další členy při psaní do kódu.  
  
    - Umožňuje kompilátoru provést kontrolu typu. To pomáhá zachytit příkazy, které mohou selhat za běhu z důvodu chyb, jako je například přetečení. Také zachytí volání metod pro objekty, které je nepodporují.  
  
    - Výsledkem je rychlejší provádění kódu. Jedním z důvodů je, že pokud neurčíte datový typ pro programovací prvek, Visual Basic kompilátor přiřadí typ `Object`. Zkompilovaný kód může být nutné převést mezi `Object` a jinými datovými typy, což snižuje výkon.  
  
## <a name="see-also"></a>Viz také:

- [Procedury](./index.md)
- [Procedury Sub](./sub-procedures.md)
- [Procedury funkce](./function-procedures.md)
- [Postupy: Předání argumentů proceduře](./how-to-pass-arguments-to-a-procedure.md)
- [Předávání argumentů podle hodnoty a reference](./passing-arguments-by-value-and-by-reference.md)
- [Rekurzivní procedury](./recursive-procedures.md)
- [Přetížení procedury](./procedure-overloading.md)
- [Objekty a třídy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [Objektově orientované programování (Visual Basic)](../../concepts/object-oriented-programming.md)
