---
title: "Předávání argumentů podle pozice a názvu (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- arguments [Visual Basic], passing by name
- procedures [Visual Basic], arguments
- := passing arguments
- procedure arguments
- Visual Basic code, procedures
- named arguments [Visual Basic], passing arguments
- arguments [Visual Basic], passing by position
- Function procedures [Visual Basic], passing arguments
- named parameters [Visual Basic], passing arguments
- named arguments
- passing parameters [Visual Basic], named parameter arguments
- passing parameters [Visual Basic], by position
- procedures [Visual Basic], calling
- named parameters
- Sub procedures [Visual Basic], passing arguments
- argument passing
- passing parameters [Visual Basic], by name
- argument passing [Visual Basic], by position
- arguments [Visual Basic], listing by name
ms.assetid: 1ad7358f-1da9-48da-a95b-f3c7ed41eff3
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 164f69fcf23049441a0acbe05058c792d5363a03
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="passing-arguments-by-position-and-by-name-visual-basic"></a>Předávání argumentů podle pozice a názvu (Visual Basic)
Při volání `Sub` nebo `Function` postupu můžete předat argumenty *umístěním* – v pořadí, ve kterém se zobrazí v postupu pro definici – nebo můžete je předat *podle názvu*, bez ohledem na pozici.  
  
 Při předání argumentu podle názvu, zadáte argument je deklarovaný název následovaný dvojtečkou a symbolem rovná (`:=`), za nímž následují hodnota argumentu. Můžete zadat pojmenované argumenty v libovolném pořadí.  
  
 Například následující `Sub` procedura používá tři argumenty:  
  
 [!code-vb[VbVbcnProcedures#41](./codesnippet/VisualBasic/passing-arguments-by-position-and-by-name_1.vb)]  
  
 Při volání tohoto postupu můžete zadat argumentů podle pozice, podle názvu nebo pomocí kombinaci těchto dvou možností.  
  
## <a name="passing-arguments-by-position"></a>Předávání argumentů podle pozice  
 Postup můžete volat `studentInfo` s argumenty předaná pozice a oddělená čárkami, jak je znázorněno v následujícím příkladu:  
  
 [!code-vb[VbVbcnProcedures#42](./codesnippet/VisualBasic/passing-arguments-by-position-and-by-name_2.vb)]  
  
 Pokud vynecháte za volitelným argumentem v seznamu poziční argument, musí obsahovat příslušné místo oddělujte čárkami. Následující příklad volání `studentInfo` bez `age` argument:  
  
 [!code-vb[VbVbcnProcedures#43](./codesnippet/VisualBasic/passing-arguments-by-position-and-by-name_3.vb)]  
  
## <a name="passing-arguments-by-name"></a>Předávání argumentů podle názvu  
 Alternativně můžete volat `studentInfo` s argumentů předaných podle názvu, také oddělená čárkami, jak je znázorněno v následujícím příkladu:  
  
 [!code-vb[VbVbcnProcedures#44](./codesnippet/VisualBasic/passing-arguments-by-position-and-by-name_4.vb)]  
  
## <a name="mixing-arguments-by-position-and-by-name"></a>Kombinování argumentů podle pozice a názvu  
 Argumentů podle pozice a podle názvu ve volání jedinou proceduru, můžete zadat, jak je znázorněno v následujícím příkladu:  
  
 [!code-vb[VbVbcnProcedures#45](./codesnippet/VisualBasic/passing-arguments-by-position-and-by-name_5.vb)]  
  
 V předchozím příkladu, je potřeba k umístění na místo vynechání žádné další čárkami `age` argument, protože `birth` je předán podle názvu.  
  
 Když zadáte argumenty podle směs pozice a názvu, poziční argumenty musí všechny nejdřív se musí uvést. Jakmile zadáte argument podle názvu, musí všechny zbývající argumenty být podle názvu.  
  
## <a name="supplying-optional-arguments-by-name"></a>Poskytnutí volitelné argumenty podle názvu  
 Předávání argumentů podle názvu je obzvláště užitečná při volání procedury, která má více než jeden nepovinný argument. Pokud zadáte argumenty podle názvu, nemáte použít po sobě jdoucích čárkami k označení chybí poziční argumenty. Předávání argumentů podle názvu taky usnadní ke sledování které argumenty jsou předávání a ty, které jsou vynechá.  
  
## <a name="restrictions-on-supplying-arguments-by-name"></a>Omezení pro zadávání argumenty podle názvu  
 Nelze předat argumenty podle názvu, abyste nemuseli zadávat povinnými argumenty. Pouze volitelné argumenty, můžete vynechat.  
  
 Pole parametrů nelze předat podle názvu. Je to proto, že při volání postupu zadáte nekonečný počet textový soubor s oddělovači argumenty pro parametr pole a kompilátor nelze přidružit více než jeden argument s jedním názvem.  
  
## <a name="see-also"></a>Viz také  
 [Postupy](./index.md)  
 [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)  
 [Postupy: předání argumentů proceduře](./how-to-pass-arguments-to-a-procedure.md)  
 [Předávání argumentů podle hodnoty a podle Reference](./passing-arguments-by-value-and-by-reference.md)  
 [Volitelné parametry](./optional-parameters.md)  
 [Pole parametrů](./parameter-arrays.md)  
 [Volitelné](../../../../visual-basic/language-reference/modifiers/optional.md)  
 [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)
