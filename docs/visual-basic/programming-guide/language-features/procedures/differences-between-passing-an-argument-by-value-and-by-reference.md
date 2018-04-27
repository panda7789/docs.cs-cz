---
title: Rozdíly mezi předáním argumentu podle hodnoty a podle reference (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- ByRef keyword [Visual Basic], passing arguments by reference
- Visual Basic code, procedures
- procedures [Visual Basic], passing arguments
- ByVal keyword [Visual Basic], passing arguments by value
- arguments [Visual Basic], passing by value or by reference
ms.assetid: 5f5c38fe-3e2d-494c-8fff-f4025b55ec93
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8f733b4fd50612292c0c4ac7195304d99ae2dbea
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="differences-between-passing-an-argument-by-value-and-by-reference-visual-basic"></a>Rozdíly mezi předáním argumentu podle hodnoty a podle reference (Visual Basic)
Pokud předáte jeden nebo více argumentů proceduře, každý argument odpovídá základní programovací element v volání kódu. Můžete předat hodnotu tento základní element nebo na něj odkaz. To se označuje jako *předávání mechanismus*.  
  
## <a name="passing-by-value"></a>Předání hodnotou  
 Předat argument *hodnotou* zadáním [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) – klíčové slovo pro odpovídající parametr v definici postupu. Pokud použijete tento mechanismus předávání, Visual Basic hodnotu základní programovací element zkopíruje do místní proměnné v postupu. Kód postup nemá přístup k podkladové element v volající kód.  
  
## <a name="passing-by-reference"></a>Předávání odkazem  
 Předat argument *odkazem* zadáním [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) – klíčové slovo pro odpovídající parametr v definici postupu. Pokud použijete tento mechanismus předávání, Visual Basic vám poskytuje postup přímý odkaz na základní programovací element volající kód.  
  
## <a name="passing-mechanism-and-element-type"></a>Mechanismus předávání a typ elementu  
 Volba předávání mechanismus není stejný jako klasifikaci základní typ elementu. Předávání hodnotou nebo odkazem odkazuje na Visual Basic poskytuje postup kódu. Typ hodnoty nebo typ odkazu odkazuje na tom, jak je programovací element uložené v paměti.  
  
 Ale mechanismus předávání a typ elementu spolu souvisejí. Hodnota typu odkaz je ukazatel na data jinde v paměti. To znamená, že při předání typu odkazu hodnotou, kód postupu má ukazatel na základní element data, i když nemá přístup k podkladové elementu samotného. Pokud element je proměnná typu pole, například kód postup nemá přístup k proměnné sám sebe, ale má přístup k poli členy.  
  
## <a name="ability-to-modify"></a>Možnost upravit  
 Při předání neupravitelnými element jako argument, postup nikdy ho upravit, v volání kódu, zda je předán `ByVal` nebo `ByRef`.  
  
 Pro element upravitelnými následující tabulka shrnuje interakce mezi mechanismus předávání a typ elementu.  
  
|Typ elementu|Předaný `ByVal`|Předaný `ByRef`|  
|------------------|--------------------|--------------------|  
|Typ hodnoty (obsahuje pouze hodnota)|Postup nelze změnit, proměnné nebo kterýkoli z jejích členů.|Postup, můžete změnit proměnnou a její členy.|  
|Typ odkazu (obsahuje ukazatel na třídu nebo strukturu instance)|Postup proměnné nelze změnit, ale můžete změnit členy instance, na kterou odkazuje.|Postup můžete změnit proměnné a členů instance, na kterou odkazuje.|  
  
## <a name="see-also"></a>Viz také  
 [Procedury](./index.md)  
 [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)  
 [Postupy: Předání argumentů proceduře](./how-to-pass-arguments-to-a-procedure.md)  
 [Předávání argumentů podle hodnoty a reference](./passing-arguments-by-value-and-by-reference.md)  
 [Rozdíly mezi upravitelnými a neupravitelnými argumenty](./differences-between-modifiable-and-nonmodifiable-arguments.md)  
 [Postupy: Změna hodnoty argumentu procedury](./how-to-change-the-value-of-a-procedure-argument.md)  
 [Postupy: Ochrana argumentu procedury před změnami hodnoty](./how-to-protect-a-procedure-argument-against-value-changes.md)  
 [Postupy: Vynucení předání argumentu podle hodnoty](./how-to-force-an-argument-to-be-passed-by-value.md)  
 [Předávání argumentů podle pozice a názvu](./passing-arguments-by-position-and-by-name.md)  
 [Typy hodnot a odkazové typy](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
