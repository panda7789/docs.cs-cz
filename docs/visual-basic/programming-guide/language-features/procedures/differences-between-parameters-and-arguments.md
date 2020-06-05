---
title: Rozdíly mezi parametry a argumenty
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
ms.openlocfilehash: dd0a62b6567f3e74763b7f2e9b96803c193c7976
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403353"
---
# <a name="differences-between-parameters-and-arguments-visual-basic"></a>Rozdíly mezi parametry a argumenty (Visual Basic)
Ve většině případů musí mít procedura nějaké informace o okolnostech, ve kterých byla volána. Postup, který provádí opakované nebo sdílené úkoly, používá pro každé volání jiné informace. Tyto informace se skládají z proměnných, konstant a výrazů, které procedury předáte při volání.  
  
 Chcete-li sdělit tyto informace proceduře, procedura definuje *parametr*a volající kód předá *argument* tomuto parametru. Parametr si můžete představit jako místo pro parkování a argument jako automobil. Stejně jako různé Automobiles mohou být v parkovacím prostoru v různých časech, volající kód může předat jiný argument stejnému parametru pokaždé, když volá proceduru.  
  
## <a name="parameters"></a>Parametry  
 *Parametr* představuje hodnotu, kterou procedura očekává, že bude při volání předána. Deklarace procedury definuje její parametry.  
  
 Při definování `Function` `Sub` procedury nebo zadejte *seznam parametrů* v závorkách hned za názvem procedury. Pro každý parametr určíte název, datový typ a mechanismus předávání ([ByVal](../../../language-reference/modifiers/byval.md) nebo [ByRef](../../../language-reference/modifiers/byref.md)). Můžete také indikovat, že parametr je nepovinný. To znamená, že volající kód nemusí pro něj předat hodnotu.  
  
 Název každého parametru slouží jako *místní proměnná* v proceduře. Název parametru použijete stejným způsobem jako jakoukoli jinou proměnnou.  
  
## <a name="arguments"></a>Arguments  
 *Argument* představuje hodnotu, která je předána parametru procedury při volání procedury. Volající kód dodává argumenty při volání procedury.  
  
 Při volání `Function` `Sub` procedury nebo můžete do závorek zahrnout *seznam argumentů* hned za názvem procedury. Každý argument odpovídá parametru ve stejné pozici v seznamu.  
  
 Na rozdíl od definice parametru argumenty nemají názvy. Každý argument je výraz, který může obsahovat nula nebo více proměnných, konstant a literálů. Datový typ vyhodnoceného výrazu by měl obvykle odpovídat datovému typu definovanému pro příslušný parametr a v každém případě musí být převoditelné na typ parametru.  
  
## <a name="see-also"></a>Viz také

- [Procedury](./index.md)
- [Procedury Sub](./sub-procedures.md)
- [Procedury funkcí](./function-procedures.md)
- [Procedury vlastnosti](./property-procedures.md)
- [Procedury operátoru](./operator-procedures.md)
- [Postupy: Definování parametru pro proceduru](./how-to-define-a-parameter-for-a-procedure.md)
- [Postupy: Předání argumentů proceduře](./how-to-pass-arguments-to-a-procedure.md)
- [Předávání argumentů podle hodnoty a reference](./passing-arguments-by-value-and-by-reference.md)
- [Rekurzivní procedury](./recursive-procedures.md)
- [Přetížení procedury](./procedure-overloading.md)
