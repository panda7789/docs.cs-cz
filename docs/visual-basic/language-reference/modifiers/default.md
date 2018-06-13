---
title: Výchozí (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Default
helpviewer_keywords:
- defaults, properties
- properties [Visual Basic], default
- default properties, in Visual Basic
- Default keyword [Visual Basic]
- default properties
ms.assetid: 45fce9b9-d212-4b2d-ab86-6e359b8b57af
ms.openlocfilehash: 555e15110c7af501de05d1f395a72ca4b7800054
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33595137"
---
# <a name="default-visual-basic"></a>Výchozí (Visual Basic)
Identifikuje vlastnost jako vlastnost Výchozí třída, struktura, nebo rozhraní.  
  
## <a name="remarks"></a>Poznámky  
 Třída, struktura nebo rozhraní můžete určit jednu z jejích vlastností, jako *výchozí vlastnost*, za předpokladu, že má vlastnost minimálně jeden parametr. Pokud kód provede odkaz na třídu nebo strukturu bez zadání členem, Visual Basic řeší tento odkaz na výchozí vlastnost.  
  
 Výchozí vlastnosti může vést ke snížení malé znaky zdrojový kód, ale jejich byl váš kód obtížněji čitelný. Pokud volání kód není obeznámeni s třídě nebo struktuře, když má odkaz na název třídy nebo struktura nemůže být určité jestli přistupuje k tento odkaz, třídu nebo strukturu sám sebe nebo výchozí vlastnost. To může vést k chybám kompilátoru nebo jemně běhu logické chyby.  
  
 Poněkud může snížit pravděpodobnost chyby výchozí vlastnost vždy pomocí [Option Strict – příkaz](../../../visual-basic/language-reference/statements/option-strict-statement.md) nastavte typ kompilátoru kontrole `On`.  
  
 Pokud máte v úmyslu použít předdefinované třídu nebo strukturu ve vašem kódu, je třeba určit, jestli má výchozí vlastnost a pokud ano, jaké jeho název je.  
  
 Z důvodu tyto nevýhody měli byste zvážit není definování výchozí vlastnosti. Kód čitelnější měli také zvážit vždy odkazující na všechny vlastnosti explicitně, i výchozí vlastnosti.  
  
 `Default` Modifikátor můžete v tomto kontextu použít:  
  
 [Příkaz Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a>Viz také  
 [Postupy: deklarace a volání výchozí vlastnosti v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md)  
 [Klíčová slova](../../../visual-basic/language-reference/keywords/index.md)
