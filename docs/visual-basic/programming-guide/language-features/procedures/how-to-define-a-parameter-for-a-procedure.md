---
title: 'Postupy: Definování parametru pro proceduru (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedure parameters [Visual Basic], defining data types for
- procedures [Visual Basic], parameters
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedure parameters [Visual Basic], defining
ms.assetid: 7962808d-407e-4e84-984e-43e9857c53c9
ms.openlocfilehash: 55925b0f007b1be2f5d46ffc0854601f483b2e2d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61863698"
---
# <a name="how-to-define-a-parameter-for-a-procedure-visual-basic"></a>Postupy: Definování parametru pro proceduru (Visual Basic)
A *parametr* umožňuje volající kód tak, předejte hodnotu k postupu při jeho volání. Stejným způsobem jako deklaraci proměnné, zadáte její název a datový typ deklarujete každý parametr pro proceduru. Zadáte také mechanismus předávání a určuje, zda se jedná o volitelný parametr.  
  
 Další informace najdete v tématu [parametry a argumenty procedury](./procedure-parameters-and-arguments.md).  
  
### <a name="to-define-a-procedure-parameter"></a>Chcete-li definovat parametr procedury  
  
1. V deklaraci procedury přidejte název parametru do seznamu parametrů podle postupu, oddělení od ostatních parametrů čárkami.  
  
2. Rozhodněte, datový typ parametru.  
  
3. Postupujte podle názvu parametru pomocí `As` klauzule k určení datového typu.  
  
4. Rozhodněte, předávání mechanismus, který chcete použít pro parametr. Obvykle můžete předat parametr podle hodnoty, pokud chcete postup nebude moct změnit jeho hodnotu ve volajícím kódu.  
  
5. Zadejte před název parametru [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) nebo [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) k určení mechanismus předávání. Další informace najdete v tématu [rozdíly mezi předáním argumentu podle hodnoty a podle Reference](./differences-between-passing-an-argument-by-value-and-by-reference.md).  
  
6. Pokud se jedná o volitelný parametr, předcházet mechanismus předávání s [volitelné](../../../../visual-basic/language-reference/modifiers/optional.md) a postupujte podle pokynů datový typ parametru znaménko rovná se (`=`) a výchozí hodnotu.  
  
     Následující příklad definuje obrys `Sub` postup se třemi parametry. První dvě jsou povinné a třetí je volitelné. Deklarace parametru se v seznamu parametrů oddělené čárkami.  
  
     [!code-vb[VbVbcnProcedures#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#33)]  
  
     První parametr `customer` objektu, a `updateCustomer` můžete přímo aktualizovat proměnnou předán `c` vzhledem k tomu, argument je předán [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md). Postup nelze změnit hodnoty poslední dva argumenty, protože jsou předávány [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).  
  
     Pokud volající kód neposkytne hodnotu `level` parametr, Visual Basic ji nastaví na výchozí hodnotu 0.  
  
     Pokud kontrola typu ([Option Strict – příkaz](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) je `Off`, `As` klauzule je volitelný při definování parametru. Ale pokud se používá jakékoli jeden parametr `As` klauzule, všechny z nich musí používat ho. Pokud je typ kontroly přepínač `On`, `As` klauzule se vyžaduje pro každou definici parametru.  
  
     Určení typů dat pro vaše programovací prvky se označuje jako *silné typování*. Pokud nastavíte `Option Strict On`, Visual Basic vynucuje silné typování. To je doporučeno, z následujících důvodů:  
  
    - Umožňuje podporu technologie IntelliSense pro proměnné a parametry. To umožňuje zobrazit jejich vlastnosti a ostatní členové průběžně zobrazovanými ve vašem kódu.  
  
    - To umožňuje kompilátoru provést kontrolu typu. To pomáhá zachytit příkazy, které může selhat v době běhu z důvodu chyby jako např. přetečení. Také zachytí volání metod na objekty, které je nepodporují.  
  
    - To má za následek rychlejší provádění kódu. Jedním z důvodů je, že pokud nezadáte datový typ pro programový element, kompilátor jazyka Visual Basic přiřadí ji `Object` typu. Zkompilovaný kód může být nutné převést vpřed a zpět mezi `Object` a ostatními datovými typy, což snižuje výkon.  
  
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
