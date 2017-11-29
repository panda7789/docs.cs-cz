---
title: "Rozdíly mezi parametry a argumenty (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- parameters [Visual Basic], and arguments
- procedure arguments
- Visual Basic code, procedures
- arguments [Visual Basic], and parameters
- procedure parameters
- parameters [Visual Basic], definition
ms.assetid: c237c056-74f4-4749-9f2c-15864f139a31
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b6613c64a24ef18239422b69f8b5320eadc95b92
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="differences-between-parameters-and-arguments-visual-basic"></a>Rozdíly mezi parametry a argumenty (Visual Basic)
Ve většině případů musí mít procedury některé informace o v případech, ve kterých byla volána. Procedury, která provádí opakovaných nebo sdíleného úlohy používá různé informace pro každé volání. Tyto informace se skládá z proměnné, konstanty a výrazy, které se předávají k postupu při jeho volání.  
  
 Tyto informace k postupu komunikovat, postup definuje *parametr*, a předává volání kód *argument* tohoto parametru. Si můžete představit jako prostor parkovací parametr a argument jako automobilu. Stejně jako různých automobilů tedy vůbec v prostoru parkovací v různou dobu, volající kód lze předat jiné argument stejný parametr pokaždé, když to volá proceduru.  
  
## <a name="parameters"></a>Parametry  
 A *parametr* představuje hodnotu, která procedura očekává, že vám při volání ho. Deklarace procedury definuje jeho parametry.  
  
 Když definujete `Function` nebo `Sub` postupu zadáte *seznam parametrů* v závorkách bezprostředně za název procedury. Pro každý parametr zadejte název, datový typ a mechanismus předávání ([ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) nebo [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)). Můžete také určit, že je volitelný parametr. To znamená, že volající kód nemá předat hodnotu pro ni.  
  
 Název každého parametru slouží jako *místní proměnné* v postupu. Název parametru použít stejným způsobem jako použijete jakoukoli jinou proměnnou.  
  
## <a name="arguments"></a>Arguments  
 *Argument* představuje hodnotu, kterou předáte parametr postupu při voláním procedury. Volání kódu poskytuje argumenty, když se volá proceduru.  
  
 Při volání `Function` nebo `Sub` postupu zahrnete *seznam argumentů* v závorkách bezprostředně za název procedury. Každý argument odpovídá parametru ve stejné pozici v seznamu.  
  
 Na rozdíl od definici parametru argumenty nemají názvy. Každý argument je výraz, který může obsahovat nula nebo více proměnných, konstanty a literály. Datový typ vyhodnocený výraz by měl odpovídat obvykle datového typu definovaného pro odpovídající parametr a v každém případě musí být převoditelná na typ parametru.  
  
## <a name="see-also"></a>Viz také  
 [Postupy](./index.md)  
 [Sub – procedury](./sub-procedures.md)  
 [Function – procedury](./function-procedures.md)  
 [Procedury vlastností](./property-procedures.md)  
 [Procedury operátoru](./operator-procedures.md)  
 [Postupy: definování parametru pro proceduru](./how-to-define-a-parameter-for-a-procedure.md)  
 [Postupy: předání argumentů proceduře](./how-to-pass-arguments-to-a-procedure.md)  
 [Předávání argumentů podle hodnoty a podle Reference](./passing-arguments-by-value-and-by-reference.md)  
 [Rekurzivní procedury](./recursive-procedures.md)  
 [Přetížení procedury](./procedure-overloading.md)
