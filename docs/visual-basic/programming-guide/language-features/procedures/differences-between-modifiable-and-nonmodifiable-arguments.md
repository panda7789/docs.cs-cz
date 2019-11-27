---
title: Rozdíly mezi upravitelnými a neupravitelnými argumenty
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedure arguments
- arguments [Visual Basic], nonmodifiable
- Visual Basic code, procedures
- arguments [Visual Basic], modifiable
ms.assetid: 87b2df69-e1f7-4657-9caf-b3f48d693428
ms.openlocfilehash: 989795ee2cdd3a78b71bad4d95cf9b384c2719bd
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74341380"
---
# <a name="differences-between-modifiable-and-nonmodifiable-arguments-visual-basic"></a>Rozdíly mezi upravitelnými a neupravitelnými argumenty (Visual Basic)
Při volání procedury obvykle předáte jeden nebo více argumentů. Každý argument odpovídá základnímu programovacímu prvku. Základní prvky i samotné argumenty mohou být buď upravitelné, nebo neupravitelné.  
  
## <a name="modifiable-and-nonmodifiable-elements"></a>Upravitelné a neupravitelné elementy  
 Programovací element může být buď *upravitelný prvek*, který může mít změněnou hodnotu, nebo *neupravitelný prvek*, který má pevnou hodnotu po vytvoření.  
  
 V následující tabulce je uveden seznam upravitelných a neupravitelných programovacích prvků.  
  
|Upravitelné elementy|Neupravitelné elementy|  
|-------------------------|----------------------------|  
|Lokální proměnné (deklarované uvnitř procedur), včetně proměnných objektů, s výjimkou pouze pro čtení|Proměnné, pole a vlastnosti jen pro čtení|  
|Pole (členské proměnné modulů, tříd a struktur), s výjimkou jen pro čtení|Konstanty a literály|  
|Vlastnosti, s výjimkou pouze pro čtení|Členové výčtu|  
|Prvky pole|Výrazy (i když jejich prvky lze upravovat)|  
  
## <a name="modifiable-and-nonmodifiable-arguments"></a>Upravitelné a neupravitelné argumenty  
 *Upravitelný argument* je jeden s upravitelným podkladovým elementem. Volající kód může uložit novou hodnotu kdykoli, a Pokud předáte argument [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), kód v proceduře může také upravit podkladový prvek v kódu volajícího.  
  
 *Neupravitelný argument* má buď neupravitelný základní prvek, nebo je předán jako [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md). Procedura nemůže změnit podkladový prvek v kódu volání, i když se jedná o upravitelný prvek. Pokud se jedná o neupravitelný prvek, samotný volající kód ho nemůže změnit.  
  
 Volaná procedura může změnit svou místní kopii neupravitelného argumentu, ale tato změna nemá vliv na základní prvek v kódu volajícího.  
  
## <a name="see-also"></a>Viz také:

- [Procedury](./index.md)
- [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)
- [Postupy: Předání argumentů proceduře](./how-to-pass-arguments-to-a-procedure.md)
- [Předávání argumentů podle hodnoty a reference](./passing-arguments-by-value-and-by-reference.md)
- [Rozdíly mezi předáním argumentu podle hodnoty a podle reference](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [Postupy: Změna hodnoty argumentu procedury](./how-to-change-the-value-of-a-procedure-argument.md)
- [Postupy: Ochrana argumentu procedury před změnami hodnoty](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [Postupy: Vynucení předání argumentu podle hodnoty](./how-to-force-an-argument-to-be-passed-by-value.md)
- [Předávání argumentů podle pozice a názvu](./passing-arguments-by-position-and-by-name.md)
- [Typy hodnot a odkazové typy](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
