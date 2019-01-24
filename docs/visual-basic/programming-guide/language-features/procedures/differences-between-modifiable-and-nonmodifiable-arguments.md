---
title: Rozdíly mezi upravitelnými a neupravitelnými argumenty (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedure arguments
- arguments [Visual Basic], nonmodifiable
- Visual Basic code, procedures
- arguments [Visual Basic], modifiable
ms.assetid: 87b2df69-e1f7-4657-9caf-b3f48d693428
ms.openlocfilehash: 06f3009d984f7a303a0ee6e8d529a3ff60900fbc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54498680"
---
# <a name="differences-between-modifiable-and-nonmodifiable-arguments-visual-basic"></a>Rozdíly mezi upravitelnými a neupravitelnými argumenty (Visual Basic)
Při volání procedury, typicky pass jeden nebo více argumentů do něj. Každý argument odpovídá základní programovací element. Základní elementy a argumenty, sami může být upravitelnými a neupravitelnými.  
  
## <a name="modifiable-and-nonmodifiable-elements"></a>Upravitelnými a Neupravitelnými elementy  
 Programovací element může být buď *upravitelná element*, svou hodnotu mění, která může mít nebo *neupravitelnými element*, který má pevnou hodnotu, po jejím vytvoření.  
  
 V následující tabulce jsou uvedeny upravitelnými a neupravitelnými programovací prvky.  
  
|Upravitelná elementy|Neupravitelnými elementy|  
|-------------------------|----------------------------|  
|Lokální proměnné (deklarované uvnitř procedury), včetně objektových proměnných, s výjimkou jen pro čtení|Proměnné určené jen pro čtení, polí a vlastností|  
|Pole (členské proměnné modulů, třídy a struktury), s výjimkou jen pro čtení|Konstanty a literály|  
|Vlastnosti, s výjimkou jen pro čtení|Členy výčtu|  
|Prvky pole|Výrazy (i když jsou jejich prvky upravitelná)|  
  
## <a name="modifiable-and-nonmodifiable-arguments"></a>Upravitelnými a Neupravitelnými argumenty  
 A *upravitelná argument* s upravitelná základního elementu. Volající kód může ukládat novou hodnotu v okamžiku, a pokud předat argument [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), kód v postupu můžete také upravit základní prvek ve volajícím kódu.  
  
 A *neupravitelnými argument* má element neupravitelnými základní nebo je předán [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md). Postup nelze upravovat základní prvek v volající kód, i v případě, že je lze měnit element. Pokud je element neupravitelnými, nelze jej upravovat volání samotný kód.  
  
 Volané procedury může upravovat jeho místní kopii neupravitelnými argument, ale tato změna nemá vliv na základní element ve volajícím kódu.  
  
## <a name="see-also"></a>Viz také:
- [Procedury](./index.md)
- [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)
- [Postupy: Předání argumentů proceduře](./how-to-pass-arguments-to-a-procedure.md)
- [Předávání argumentů podle hodnoty a reference](./passing-arguments-by-value-and-by-reference.md)
- [Rozdíly mezi předáním argumentu podle hodnoty a podle reference](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [Postupy: Změna hodnoty argumentu procedury](./how-to-change-the-value-of-a-procedure-argument.md)
- [Postupy: Ochrana argumentu procedury proti změnám hodnoty](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [Postupy: Vynucení argumentu být předána podle hodnoty](./how-to-force-an-argument-to-be-passed-by-value.md)
- [Předávání argumentů podle pozice a názvu](./passing-arguments-by-position-and-by-name.md)
- [Typy hodnot a odkazové typy](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
