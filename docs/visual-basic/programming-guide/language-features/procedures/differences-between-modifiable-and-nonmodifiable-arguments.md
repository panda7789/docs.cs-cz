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
ms.openlocfilehash: 2b60d732b260ad0477946e41ece4cd182de541ce
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="differences-between-modifiable-and-nonmodifiable-arguments-visual-basic"></a>Rozdíly mezi upravitelnými a neupravitelnými argumenty (Visual Basic)
Při volání procedury, obvykle předání jeden nebo více argumentů do ní. Každý argument odpovídá základní programovací element. Základní elementy a argumenty sami může být upravitelnými a neupravitelnými.  
  
## <a name="modifiable-and-nonmodifiable-elements"></a>Upravitelnými a Neupravitelnými elementy  
 Programovací element může být buď *upravitelnými element*, která může mít jeho hodnota změněna, nebo *neupravitelnými element*, který má pevnou hodnotu, po vytvoření.  
  
 Následující tabulka uvádí upravitelnými a neupravitelnými elementům programování.  
  
|Upravitelnými elementy|Neupravitelnými elementy|  
|-------------------------|----------------------------|  
|Lokální proměnné (deklarované uvnitř procedury), včetně objektové proměnné, s výjimkou jen pro čtení|Proměnné jen pro čtení, polí a vlastností|  
|Pole (členské proměnné modulů, třídy a struktury), s výjimkou jen pro čtení|Konstanty a literály|  
|Vlastnosti, s výjimkou jen pro čtení|Členové výčtu|  
|Elementy pole|Výrazy (i když jsou jejich elementů upravitelnými)|  
  
## <a name="modifiable-and-nonmodifiable-arguments"></a>Upravitelnými a Neupravitelnými argumenty  
 A *upravitelnými argument* je jedním s upravitelnými základní elementem. Volání kódu můžete uložit novou hodnotu kdykoli, a Pokud předáte argument [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), kód v postupu můžete také upravit základní elementu v kódu volání.  
  
 A *neupravitelnými argument* má neupravitelnými základní element nebo je předán [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md). Postup nelze upravit základní element v kód volání, i když je upravitelnými element. Pokud je element neupravitelnými, nelze jej upravovat volání samotný kód.  
  
 Volané procedury může změnit jeho místní kopii neupravitelnými argument, ale tato změna nemá vliv na základní elementu v kódu volání.  
  
## <a name="see-also"></a>Viz také  
 [Procedury](./index.md)  
 [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)  
 [Postupy: Předání argumentů proceduře](./how-to-pass-arguments-to-a-procedure.md)  
 [Předávání argumentů podle hodnoty a reference](./passing-arguments-by-value-and-by-reference.md)  
 [Rozdíly mezi předáním argumentu podle hodnoty a podle reference](./differences-between-passing-an-argument-by-value-and-by-reference.md)  
 [Postupy: Změna hodnoty argumentu procedury](./how-to-change-the-value-of-a-procedure-argument.md)  
 [Postupy: Ochrana argumentu procedury před změnami hodnoty](./how-to-protect-a-procedure-argument-against-value-changes.md)  
 [Postupy: Vynucení předání argumentu podle hodnoty](./how-to-force-an-argument-to-be-passed-by-value.md)  
 [Předávání argumentů podle pozice a názvu](./passing-arguments-by-position-and-by-name.md)  
 [Typy hodnot a odkazové typy](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
