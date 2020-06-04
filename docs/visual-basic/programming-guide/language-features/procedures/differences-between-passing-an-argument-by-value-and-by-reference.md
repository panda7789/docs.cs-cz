---
title: Rozdíly mezi předáváním argumentů hodnotou a referencí
ms.date: 07/20/2015
helpviewer_keywords:
- ByRef keyword [Visual Basic], passing arguments by reference
- Visual Basic code, procedures
- procedures [Visual Basic], passing arguments
- ByVal keyword [Visual Basic], passing arguments by value
- arguments [Visual Basic], passing by value or by reference
ms.assetid: 5f5c38fe-3e2d-494c-8fff-f4025b55ec93
ms.openlocfilehash: bd316ae2239ad85e4ef6dadbb8a634d5fe7ecf02
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403327"
---
# <a name="differences-between-passing-an-argument-by-value-and-by-reference-visual-basic"></a>Rozdíly mezi předáním argumentu podle hodnoty a podle reference (Visual Basic)
Pokud předáte jeden nebo více argumentů procedury, každý argument odpovídá základnímu programovacímu prvku v kódu volajícího. Můžete předat buď hodnotu tohoto podkladového prvku, nebo odkaz na něj. Tato metoda se označuje jako *mechanismus předávání*.  
  
## <a name="passing-by-value"></a>Předávání hodnotou  
 Argument můžete předat *hodnotou* zadáním klíčového slova [ByVal](../../../language-reference/modifiers/byval.md) pro odpovídající parametr v definici procedury. Při použití tohoto mechanismu předávání Visual Basic kopíruje hodnotu základního programovacího prvku do místní proměnné v proceduře. Kód procedury nemá žádný přístup k podkladovému prvku v kódu volajícího.  
  
## <a name="passing-by-reference"></a>Předávání odkazem  
 Argument předáte *odkazem* zadáním klíčového slova [ByRef](../../../language-reference/modifiers/byref.md) pro odpovídající parametr v definici procedury. Při použití tohoto mechanismu předávání Visual Basic poskytuje proceduru přímý odkaz na základní programovací prvek v kódu volajícího.  
  
## <a name="passing-mechanism-and-element-type"></a>Předání mechanismu a typu elementu  
 Výběr mechanismu předávání není stejný jako klasifikace základního typu elementu. Předání hodnotou nebo odkazem odkazuje na to, co Visual Basic poskytování kódu procedury. Typ hodnoty nebo odkazový typ odkazuje na způsob ukládání programovacího prvku v paměti.  
  
 Mechanismus předání a typ elementu však jsou vzájemně propojené. Hodnota typu odkazu je ukazatel na data jinde v paměti. To znamená, že když předáte typ odkazu podle hodnoty, kód procedury má ukazatel na data základního elementu, i když nemá přístup k základnímu elementu samotnému. Například pokud je prvek proměnnou pole, kód procedury nemá přístup k proměnné samotné, ale má přístup k členům pole.  
  
## <a name="ability-to-modify"></a>Možnost úpravy  
 Pokud předáte neupravitelný prvek jako argument, procedura jej nikdy neupraví v volajícím kódu, zda je předán `ByVal` nebo `ByRef` .  
  
 V případě upravitelného prvku shrnuje následující tabulka interakci mezi typem prvku a mechanismem předávání.  
  
|Typ elementu|Předaný`ByVal`|Předaný`ByRef`|  
|------------------|--------------------|--------------------|  
|Typ hodnoty (obsahuje pouze hodnotu)|Procedura nemůže změnit proměnnou ani žádný z jejích členů.|Procedura může změnit proměnnou a její členy.|  
|Odkazový typ (obsahuje ukazatel na instanci třídy nebo struktury)|Procedura nemůže změnit proměnnou, ale může změnit členy instance, na kterou odkazuje.|Procedura může změnit proměnnou a členy instance, na kterou odkazuje.|  
  
## <a name="see-also"></a>Viz také

- [Procedury](./index.md)
- [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)
- [Postupy: Předání argumentů proceduře](./how-to-pass-arguments-to-a-procedure.md)
- [Předávání argumentů podle hodnoty a reference](./passing-arguments-by-value-and-by-reference.md)
- [Rozdíly mezi upravitelnými a neupravitelnými argumenty](./differences-between-modifiable-and-nonmodifiable-arguments.md)
- [Postupy: Změna hodnoty argumentu procedury](./how-to-change-the-value-of-a-procedure-argument.md)
- [Postupy: Ochrana argumentu procedury před změnami hodnoty](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [Postupy: Vynucení předání argumentu podle hodnoty](./how-to-force-an-argument-to-be-passed-by-value.md)
- [Předávání argumentů podle pozice a názvu](./passing-arguments-by-position-and-by-name.md)
- [Typy hodnot a typy odkazu](../data-types/value-types-and-reference-types.md)
