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
ms.openlocfilehash: e703346113348556b8a3ea41a7934a55a8008522
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84388073"
---
# <a name="how-to-define-a-parameter-for-a-procedure-visual-basic"></a>Postupy: Definování parametru pro proceduru (Visual Basic)
*Parametr* umožňuje volajícímu kódu předat hodnotu proceduře při jeho volání. Každý parametr pro proceduru deklarujete stejným způsobem jako proměnnou, a to zadáním jejího názvu a datového typu. Zadáte také mechanismus předávání a zda je parametr volitelný.  
  
 Další informace najdete v tématu [parametry a argumenty procedury](./procedure-parameters-and-arguments.md).  
  
### <a name="to-define-a-procedure-parameter"></a>Definování parametru procedury  
  
1. V deklaraci procedury přidejte název parametru do seznamu parametrů procedury a oddělte jej od ostatních parametrů čárkami.  
  
2. Určete datový typ parametru.  
  
3. Podle názvu parametru s `As` klauzulí zadejte datový typ.  
  
4. Určete mechanismus předávání, který chcete pro parametr. Obvykle předáte parametr podle hodnoty, pokud nechcete, aby procedura mohla měnit jeho hodnotu v volajícím kódu.  
  
5. Před názvem parametru s klíčovým slovem [ByVal](../../../language-reference/modifiers/byval.md) nebo [ByRef](../../../language-reference/modifiers/byref.md) zadejte mechanismus předávání. Další informace naleznete v tématu [rozdíly mezi předáním argumentu podle hodnoty a podle reference](./differences-between-passing-an-argument-by-value-and-by-reference.md).  
  
6. Pokud je parametr volitelný, předchází mechanismus předání s [volitelným](../../../language-reference/modifiers/optional.md) a následuje datový typ parametru se symbolem rovná se ( `=` ) a výchozí hodnotou.  
  
     Následující příklad definuje osnovu `Sub` procedury se třemi parametry. První dvě jsou povinná a třetí je volitelná. Deklarace parametrů jsou v seznamu parametrů odděleny čárkami.  
  
     [!code-vb[VbVbcnProcedures#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#33)]  
  
     První parametr přijímá `customer` objekt a `updateCustomer` může přímo aktualizovat proměnnou předanou do, `c` protože argument je předán jako typ [ByRef](../../../language-reference/modifiers/byref.md). Procedura nemůže změnit hodnoty posledních dvou argumentů, protože jsou předány metodě [ByVal](../../../language-reference/modifiers/byval.md).  
  
     Pokud volající kód nezadá hodnotu pro `level` parametr, Visual Basic nastaví na výchozí hodnotu 0.  
  
     Pokud je přepínač pro kontrolu typu ([příkaz Option Strict](../../../language-reference/statements/option-strict-statement.md)) `Off` , je `As` klauzule při definování parametru volitelná. Nicméně, pokud některý z parametrů používá `As` klauzuli, všechny je musí použít. Pokud je přepínač pro kontrolu typu `On` , `As` je klauzule požadována pro každou definici parametru.  
  
     Zadání datových typů pro všechny vaše programovací prvky se nazývá *silného psaní*. Když nastavíte `Option Strict On` , Visual Basic vynutila silné psaní. Tento postup se doporučuje z následujících důvodů:  
  
    - Umožňuje podporu technologie IntelliSense pro vaše proměnné a parametry. To vám umožní zobrazit jejich vlastnosti a další členy při psaní do kódu.  
  
    - Umožňuje kompilátoru provést kontrolu typu. To pomáhá zachytit příkazy, které mohou selhat za běhu z důvodu chyb, jako je například přetečení. Také zachytí volání metod pro objekty, které je nepodporují.  
  
    - Výsledkem je rychlejší provádění kódu. Jedním z důvodů je, že pokud neurčíte datový typ pro programovací prvek, Visual Basic kompilátor přiřadí `Object` typ. Zkompilovaný kód může být nutné převádět mezi `Object` a jinými datovými typy, což snižuje výkon.  
  
## <a name="see-also"></a>Viz také

- [Procedury](./index.md)
- [Procedury Sub](./sub-procedures.md)
- [Procedury funkcí](./function-procedures.md)
- [Postupy: Předání argumentů proceduře](./how-to-pass-arguments-to-a-procedure.md)
- [Předávání argumentů podle hodnoty a reference](./passing-arguments-by-value-and-by-reference.md)
- [Rekurzivní procedury](./recursive-procedures.md)
- [Přetížení procedury](./procedure-overloading.md)
- [Objekty a třídy](../objects-and-classes/index.md)
- [Objektově orientované programování (Visual Basic)](../../concepts/object-oriented-programming.md)
