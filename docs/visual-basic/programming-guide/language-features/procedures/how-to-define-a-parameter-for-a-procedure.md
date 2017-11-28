---
title: "Postupy: Definování parametru pro proceduru (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedure parameters [Visual Basic], defining data types for
- procedures [Visual Basic], parameters
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedure parameters [Visual Basic], defining
ms.assetid: 7962808d-407e-4e84-984e-43e9857c53c9
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3c909cfe1b45a42aae91948917f310474575f225
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-define-a-parameter-for-a-procedure-visual-basic"></a>Postupy: Definování parametru pro proceduru (Visual Basic)
A *parametr* umožňuje volací kód, který předat hodnotu k postupu při jeho volání. Každý parametr pro proceduru deklarovat stejným způsobem jako deklarovat proměnnou, zadat jeho název a datový typ. Můžete také zadat mechanismus předávání, a zda se jedná o volitelný parametr.  
  
 Další informace najdete v tématu [parametry a argumenty procedury](./procedure-parameters-and-arguments.md).  
  
### <a name="to-define-a-procedure-parameter"></a>Chcete-li definovat parametru procedury  
  
1.  V deklaraci postup přidejte název parametru do seznamu parametrů postupu, oddělení z dalších parametrů čárkami.  
  
2.  Rozhodněte, datový typ parametru.  
  
3.  Postupujte podle názvu parametru s `As` klauzule k určení datového typu.  
  
4.  Rozhodněte, které chcete pro parametr mechanismus předávání. Za normálních okolností předání parametru podle hodnoty, pokud chcete, aby postup nebudete moct změnit jeho hodnota v volání kódu.  
  
5.  Zadejte před název parametru [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) nebo [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) k určení mechanismus předávání. Další informace najdete v tématu [rozdíly mezi předáním argumentu podle hodnoty a podle Reference](./differences-between-passing-an-argument-by-value-and-by-reference.md).  
  
6.  Pokud se jedná o volitelný parametr, předcházet mechanismus předávání s [volitelné](../../../../visual-basic/language-reference/modifiers/optional.md) a postupujte podle pokynů datový typ parametru symbol rovná se (`=`) a výchozí hodnotu.  
  
     V následujícím příkladu definuje obrys `Sub` postupu se třemi parametry. První dvě jsou povinné a třetí je volitelné. Deklarace parametru se v seznamu parametrů oddělených čárkami.  
  
     [!code-vb[VbVbcnProcedures#33](./codesnippet/VisualBasic/how-to-define-a-parameter-for-a-procedure_1.vb)]  
  
     První parametr přijme `customer` objekt, a `updateCustomer` můžete přímo aktualizovat proměnnou předaný `c` protože argument předaný [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md). Postup nejde změnit hodnoty poslední dva argumenty, protože jsou předávány [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).  
  
     Pokud kód volání neposkytuje hodnotu `level` parametr [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] nastaví na výchozí hodnotu 0.  
  
     Pokud kontrola typu přepínače ([Option Strict – příkaz](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) je `Off`, `As` klauzule je volitelný, když definujete parametr. Ale pokud žádné jeden parametr se používá `As` klauzule, všechny z nich musí používat ho. Pokud je typ kontroly přepínač `On`, `As` je vyžadována pro každý parametr definice klauzule.  
  
     Určení typů dat pro všechny programovací elementy se označuje jako *silného typování*. Když nastavíte `Option Strict On`, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] vynucuje silného typování. Toto nastavení se důrazně doporučuje, z následujících důvodů:  
  
    -   Umožňuje podporu technologie IntelliSense pro proměnné a parametry. To umožňuje zobrazit jejich vlastnosti a ostatní členové při psaní do vašeho kódu.  
  
    -   To umožňuje kompilátoru provést kontrola typu. To pomáhá catch příkazy, které může selhat v době běhu z důvodu chyby jako např. přetečení. Volání metody také zachytávalo na objekty, které je nepodporují.  
  
    -   Výsledkem rychlejší provádění kódu. Jedním z důvodů je, že pokud nezadáte datový typ pro element programování [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] kompilátoru přiřadí ji `Object` typu. Zkompilovaný kód možná muset převést přepínat mezi `Object` a dalších typů dat, které sníží výkon.  
  
## <a name="see-also"></a>Viz také  
 [Postupy](./index.md)  
 [Sub – procedury](./sub-procedures.md)  
 [Function – procedury](./function-procedures.md)  
 [Postupy: předání argumentů proceduře](./how-to-pass-arguments-to-a-procedure.md)  
 [Předávání argumentů podle hodnoty a podle Reference](./passing-arguments-by-value-and-by-reference.md)  
 [Rekurzivní procedury](./recursive-procedures.md)  
 [Přetížení procedury](./procedure-overloading.md)  
 [Objekty a třídy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [Objektově orientované programování](http://msdn.microsoft.com/library/1cf6e655-3f30-45f1-9a5d-4a88ca24a1c2)
