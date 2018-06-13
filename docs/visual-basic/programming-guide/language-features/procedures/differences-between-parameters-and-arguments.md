---
title: Rozdíly mezi parametry a argumenty (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: a5075c218371b754ac883b97475ab941811966b5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33650683"
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
 [Procedury](./index.md)  
 [Procedury Sub](./sub-procedures.md)  
 [Procedury funkce](./function-procedures.md)  
 [Procedury vlastnosti](./property-procedures.md)  
 [Procedury operátoru](./operator-procedures.md)  
 [Postupy: Definování parametru pro proceduru](./how-to-define-a-parameter-for-a-procedure.md)  
 [Postupy: Předání argumentů proceduře](./how-to-pass-arguments-to-a-procedure.md)  
 [Předávání argumentů podle hodnoty a reference](./passing-arguments-by-value-and-by-reference.md)  
 [Rekurzivní procedury](./recursive-procedures.md)  
 [Přetížení procedury](./procedure-overloading.md)
