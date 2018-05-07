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
ms.openlocfilehash: b0ab186945b456d7fb4dde3f52724b08a99e2827
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="procedure-parameters-and-arguments-visual-basic"></a>Parametry a argumenty procedury (Visual Basic)
Ve většině případů musí procedury některé informace o v případech, ve kterých byla volána. Procedury, která provádí opakovaných nebo sdíleného úlohy používá různé informace pro každé volání. Tyto informace se skládá z proměnné, konstanty a výrazy, které se předávají k postupu při jeho volání.  
  
 A *parametr* představuje hodnotu, která procedura očekává, že můžete zadat při jeho volání. Deklarace procedury definuje jeho parametry.  
  
 Můžete definovat procedura se žádné parametry, parametr jeden nebo více než jeden. Se označuje jako součást definice procedury, která určuje parametry *seznam parametrů*.  
  
 *Argument* představuje hodnotu zadáte parametr postupu při voláním procedury. Volání kódu poskytuje argumenty, když se volá proceduru. Část volání procedury, která určuje argumenty, které se nazývá *seznam argumentů*.  
  
 Následující obrázek znázorňuje kód volání postup `safeSquareRoot` ze dvou různých míst. První volání předá hodnotu proměnné `x` (4.0) na parametr `number`a návratovou hodnotu v `root` (2.0) je přiřazen k proměnné `y`. Druhé volání předá hodnotu literálu 9.0 k `number`a přiřadí návratovou hodnotu (3.0) k proměnné `z`.  
  
 ![Grafický diagram předání argument na parametr](./media/parametersargue.gif "ParametersArgue")  
Předávání argument na parametr  
  
 Další informace najdete v tématu [rozdíly mezi parametry a argumenty](./differences-between-parameters-and-arguments.md).  
  
## <a name="parameter-data-type"></a>Typ dat parametru  
 Definovat datový typ pro parametr pomocí `As` klauzuli v jeho deklaraci. Například následující funkce přijme řetězce a celé číslo.  
  
 [!code-vb[VbVbcnProcedures#32](./codesnippet/VisualBasic/procedure-parameters-and-arguments_1.vb)]  
  
 Pokud kontrola typu přepínače ([Option Strict – příkaz](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) je `Off,` `As` klauzule je volitelné, s tím rozdílem, že pokud žádné jeden parametr používá ji, všechny parametry musí používat. Pokud kontrola typu `On`, `As` klauzule je vyžadována pro všechny parametry procedur.  
  
 Pokud kód volání očekává, zadejte argument s datovým typem, který se liší od odpovídajícího parametru, jako například `Byte` k `String` parametru, je nutné provést s některou z následujících:  
  
-   Zadejte pouze argumenty s typy dat, které rozšíří na datový typ parametru;  
  
-   Nastavit `Option Strict Off` umožňuje implicitní zužující převody; nebo  
  
-   Explicitně převést na datový typ pomocí klíčového slova převodu.  
  
### <a name="type-parameters"></a>Parametry typu  
 A *obecný postup* definuje také nejméně jeden *parametry typu* kromě jeho normální parametry. Obecný postup umožňuje kód volání předat různé datové typy pokaždé, když ho volá proceduru, takže ho můžete přizpůsobit datové typy požadavků na jednotlivých volání. V tématu [obecné procedury v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md).  
  
## <a name="see-also"></a>Viz také  
 [Procedury](./index.md)  
 [Procedury Sub](./sub-procedures.md)  
 [Procedury funkce](./function-procedures.md)  
 [Procedury vlastnosti](./property-procedures.md)  
 [Procedury operátoru](./operator-procedures.md)  
 [Postupy: Definování parametru pro proceduru](./how-to-define-a-parameter-for-a-procedure.md)  
 [Postupy: Předání argumentů proceduře](./how-to-pass-arguments-to-a-procedure.md)  
 [Předávání argumentů podle hodnoty a reference](./passing-arguments-by-value-and-by-reference.md)  
 [Přetížení procedury](./procedure-overloading.md)  
 [Převody typů v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
