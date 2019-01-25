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
ms.openlocfilehash: ec7c92975bc056fd740033b602b15cd1611c44d1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54694032"
---
# <a name="differences-between-parameters-and-arguments-visual-basic"></a>Rozdíly mezi parametry a argumenty (Visual Basic)
Ve většině případů procedury musí mít některé informace o okolnostech, ve kterých byla volána. Postup, který provádí úlohy opakovaných nebo sdílené používá různé informace pro každé volání. Tyto informace se skládá z proměnné, konstanty a výrazy, které předáváte k postupu při jeho volání.  
  
 Sdělovat tyto informace k postupu podle postupu definuje *parametr*, a předá volající kód *argument* tomuto parametru. Si můžete představit jako parkovací místo parametru a argument jako automobilu. Stejně jako různých automobilů můžete park v prostoru parkovací v různých časech, volající kód lze předat jako argument jiné stejný parametr pokaždé, když se volá proceduru.  
  
## <a name="parameters"></a>Parametry  
 A *parametr* představuje hodnotu, která procedura očekává, že budete při jeho volání. Podle postupu prohlášení definuje jeho parametry.  
  
 Při definování `Function` nebo `Sub` postupu zadáte *seznam parametrů* v závorkách bezprostředně za název procedury. Pro každý parametr, můžete zadat název, datový typ a mechanismus pro předávání ([ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) nebo [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)). Můžete také určit, že parametr je volitelný. To znamená, že volající kód nemá předat hodnotu pro něj.  
  
 Název každého parametru slouží jako *lokální proměnná* v postupu. Název parametru použít stejným způsobem můžete použít jakoukoli jinou proměnnou.  
  
## <a name="arguments"></a>Arguments  
 *Argument* představuje hodnotu, kterou můžete předat parametr procedury při volání procedury. Volající kód poskytuje argumenty při volání postup.  
  
 Při volání `Function` nebo `Sub` postupu zahrnete *seznam argumentů* v závorkách bezprostředně za název procedury. Každý argument odpovídající parametru na stejné pozici v seznamu.  
  
 Na rozdíl od definice parametru argumenty nemají názvy. Každý argument je výraz, který může obsahovat nula nebo více proměnných, konstant a literály. Datový typ vyhodnocený výraz by měl odpovídat obvykle datového typu definovaného u odpovídajícího parametru a v každém případě musí být převoditelný na typ parametru.  
  
## <a name="see-also"></a>Viz také:
- [Procedury](./index.md)
- [Procedury Sub](./sub-procedures.md)
- [Procedury funkce](./function-procedures.md)
- [Procedury vlastnosti](./property-procedures.md)
- [Procedury operátoru](./operator-procedures.md)
- [Postupy: Definování parametru pro proceduru](./how-to-define-a-parameter-for-a-procedure.md)
- [Postupy: Předání argumentů proceduře](./how-to-pass-arguments-to-a-procedure.md)
- [Předávání argumentů podle hodnoty a reference](./passing-arguments-by-value-and-by-reference.md)
- [Rekurzivní procedury](./recursive-procedures.md)
- [Přetížení procedury](./procedure-overloading.md)
