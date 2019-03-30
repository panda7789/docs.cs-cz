---
title: Parametry a argumenty procedury (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], argument lists
- values [Visual Basic], passing to procedures
- arguments [Visual Basic], passing
- procedures [Visual Basic], parameters
- Visual Basic code, argument lists
- Visual Basic code, procedures
- parameters [Visual Basic], Visual Basic procedures
- parameters [Visual Basic], lists
- arguments [Visual Basic], Visual Basic procedures
- arguments [Visual Basic], procedures
- parameter lists [Visual Basic]
- Visual Basic code, parameter lists
- argument lists [Visual Basic]
- procedures [Visual Basic], parameter lists
ms.assetid: ff275aff-aa13-40df-bd4c-63486db8c1e9
ms.openlocfilehash: 4b62e4b752074bb8d1a660e51ab230a87ff21db4
ms.sourcegitcommit: 15ab532fd5e1f8073a4b678922d93b68b521bfa0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/29/2019
ms.locfileid: "58654234"
---
# <a name="procedure-parameters-and-arguments-visual-basic"></a>Parametry a argumenty procedury (Visual Basic)
Ve většině případů postup potřebuje určité informace o okolnostech, ve kterých byla volána. Postup, který provádí úlohy opakovaných nebo sdílené používá různé informace pro každé volání. Tyto informace se skládá z proměnné, konstanty a výrazy, které předáváte k postupu při jeho volání.  
  
 A *parametr* představuje hodnotu, která procedura očekává, že můžete zadat při jeho volání. Podle postupu prohlášení definuje jeho parametry.  
  
 Můžete definovat postup s žádné parametry, jeden parametr nebo více než jeden. Je volána část definice procedury, která určuje parametry *seznam parametrů*.  
  
 *Argument* představuje hodnotu zadáte parametr procedury při volání procedury. Volající kód poskytuje argumenty při volání postup. Část volání procedury, která určuje argumenty se nazývá *seznam argumentů*.  
  
 Následující obrázek znázorňuje kódu volající proces `safeSquareRoot` ze dvou různých míst. První volání předá hodnotu proměnné `x` (4.0) k parametru `number`a návratová hodnota v `root` (2.0) je přiřazená k proměnné `y`. Druhé volání předá hodnotu literálu 9.0 na `number`a přiřadí proměnné návratovou hodnotu (3.0) `z`.  
  
 ![Diagram zobrazující průběh předání argumentu pro parametr](./media/procedure-parameters-and-arguments/pass-argument-parameter.gif)  
  
 Další informace najdete v tématu [rozdíly mezi parametry a argumenty](./differences-between-parameters-and-arguments.md).  
  
## <a name="parameter-data-type"></a>Datový typ parametru  
 Definovat datový typ pro parametr pomocí `As` klauzule v jeho deklaraci. Například následující funkce přijímá řetězec a celé číslo.  
  
 [!code-vb[VbVbcnProcedures#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#32)]  
  
 Pokud kontrola typu ([Option Strict – příkaz](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) je `Off,` `As` klauzule je volitelné, s tím rozdílem, že pokud ho používáte jakékoli jeden parametr, musíte použít všechny parametry, ho. Pokud je kontrola typu `On`, `As` klauzule se vyžaduje pro všechny parametry procedury.  
  
 Pokud volající kód očekává, že chcete zadat argument s datovým typem, který se liší od odpovídajícího parametru, například `Byte` k `String` parametr, musíte udělat jednu z následujících:  
  
-   Zadejte pouze argumenty s datovými typy, které rozšířit na datový typ parametru;  
  
-   Nastavte `Option Strict Off` povolit implicitní zužující převody; nebo  
  
-   Použijte klíčové slovo převodu k explicitnímu převodu datového typu.  
  
### <a name="type-parameters"></a>Parametry typu  
 A *obecný postup* také definuje jeden nebo více *parametry typu* kromě své normální parametry. Obecný postup umožňuje volajícímu kódu k předání různých typů dat pokaždé, když volá proceduru, takže ho můžete přizpůsobit datové typy s požadavky každého jednotlivého volání. Zobrazit [obecné procedury v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md).  
  
## <a name="see-also"></a>Viz také:
- [Procedury](./index.md)
- [Procedury Sub](./sub-procedures.md)
- [Procedury funkce](./function-procedures.md)
- [Procedury vlastnosti](./property-procedures.md)
- [Procedury operátoru](./operator-procedures.md)
- [Postupy: Definování parametru pro proceduru](./how-to-define-a-parameter-for-a-procedure.md)
- [Postupy: Předání argumentů proceduře](./how-to-pass-arguments-to-a-procedure.md)
- [Předávání argumentů podle hodnoty a reference](./passing-arguments-by-value-and-by-reference.md)
- [Přetížení procedury](./procedure-overloading.md)
- [Převody typů v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
