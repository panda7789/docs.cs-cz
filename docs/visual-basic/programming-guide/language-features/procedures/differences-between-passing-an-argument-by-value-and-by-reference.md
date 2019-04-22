---
title: Rozdíly mezi předáním argumentu podle hodnoty a podle reference (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- ByRef keyword [Visual Basic], passing arguments by reference
- Visual Basic code, procedures
- procedures [Visual Basic], passing arguments
- ByVal keyword [Visual Basic], passing arguments by value
- arguments [Visual Basic], passing by value or by reference
ms.assetid: 5f5c38fe-3e2d-494c-8fff-f4025b55ec93
ms.openlocfilehash: 1b85941c14721280a5025db442c4793930244ec8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58837489"
---
# <a name="differences-between-passing-an-argument-by-value-and-by-reference-visual-basic"></a>Rozdíly mezi předáním argumentu podle hodnoty a podle reference (Visual Basic)
Pokud předáte jeden nebo více argumentů proceduře, každý argument odpovídá základní programovací element ve volajícím kódu. Můžete předat hodnotu tohoto základního elementu nebo na ni odkaz. To se označuje jako *předávání mechanismus*.  
  
## <a name="passing-by-value"></a>Předání hodnotou  
 Předat argument *podle hodnoty* zadáním [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) – klíčové slovo pro odpovídající parametr v definici procedury. Při použití tohoto mechanismu předávání jazyka Visual Basic kopíruje hodnotu základní programovací element do místní proměnné v postupu. Kód procedury nemá přístup k podkladové element ve volajícím kódu.  
  
## <a name="passing-by-reference"></a>Předávání odkazem.  
 Předat argument *odkazem* zadáním [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) – klíčové slovo pro odpovídající parametr v definici procedury. Pokud použijete tento mechanismus pro předávání, Visual Basic poskytuje postup přímý odkaz na základní programovací element volající kód.  
  
## <a name="passing-mechanism-and-element-type"></a>Mechanismus pro předávání a typ prvku  
 Volba předávání mechanismus není stejný jako klasifikace základní typ elementu. Předání hodnotou nebo odkazem odkazuje na Visual Basic poskytuje kód procedury. Typ hodnoty nebo typ odkazu odkazuje na způsob uložení programovací element v paměti.  
  
 Nicméně mechanismus předávání a typ prvku spolu souvisejí. Hodnota typu odkazu je ukazatel na data jinde v paměti. To znamená, že pokud předáte typ odkazu podle hodnoty, kód procedury má ukazatel na základní element data, i když nemá přístup k podkladové elementu samotného. Pokud element je proměnná typu pole, například kód procedury nemá přístup k proměnné samotné, ale může přistupovat k členy pole.  
  
## <a name="ability-to-modify"></a>Schopnost upravovat  
 Po úspěšných neupravitelnými element jako argument postup nikdy upravit volající kód, zda je jí předán `ByVal` nebo `ByRef`.  
  
 Následující tabulka shrnuje pro prvek upravitelná interakce mezi typem elementu a předávání mechanismus.  
  
|Typ elementu|Předaný `ByVal`|Předaný `ByRef`|  
|------------------|--------------------|--------------------|  
|Typ hodnoty (obsahuje pouze hodnotu)|Postup nelze změnit proměnné nebo kterýkoli z jejích členů.|Podle postupu můžete změnit proměnné a její členy.|  
|Typ odkazu (obsahuje ukazatel na instanci třídy nebo struktury)|Postup proměnné nelze změnit, ale můžete změnit členy instance, na kterou odkazuje.|Podle postupu můžete změnit proměnné a členy instance, na kterou odkazuje.|  
  
## <a name="see-also"></a>Viz také:

- [Procedury](./index.md)
- [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)
- [Postupy: Předání argumentů proceduře](./how-to-pass-arguments-to-a-procedure.md)
- [Předávání argumentů podle hodnoty a reference](./passing-arguments-by-value-and-by-reference.md)
- [Rozdíly mezi upravitelnými a neupravitelnými argumenty](./differences-between-modifiable-and-nonmodifiable-arguments.md)
- [Postupy: Změna hodnoty argumentu procedury](./how-to-change-the-value-of-a-procedure-argument.md)
- [Postupy: Ochrana argumentu procedury proti změnám hodnoty](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [Postupy: Vynucení argumentu být předána podle hodnoty](./how-to-force-an-argument-to-be-passed-by-value.md)
- [Předávání argumentů podle pozice a názvu](./passing-arguments-by-position-and-by-name.md)
- [Typy hodnot a odkazové typy](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
