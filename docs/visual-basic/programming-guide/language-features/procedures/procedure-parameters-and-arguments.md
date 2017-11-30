---
title: Parametry a argumenty procedury (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 726667950cfb227a0359bd6238c202883561749c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
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
 [Postupy](./index.md)  
 [Sub – procedury](./sub-procedures.md)  
 [Function – procedury](./function-procedures.md)  
 [Procedury vlastností](./property-procedures.md)  
 [Procedury operátoru](./operator-procedures.md)  
 [Postupy: definování parametru pro proceduru](./how-to-define-a-parameter-for-a-procedure.md)  
 [Postupy: předání argumentů proceduře](./how-to-pass-arguments-to-a-procedure.md)  
 [Předávání argumentů podle hodnoty a podle Reference](./passing-arguments-by-value-and-by-reference.md)  
 [Přetížení procedury](./procedure-overloading.md)  
 [Převody typů v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
