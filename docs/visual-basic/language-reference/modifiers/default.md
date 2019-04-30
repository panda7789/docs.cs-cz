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
ms.openlocfilehash: f78ffe42a9d618d44da2a50c0de831396576430c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61800929"
---
# <a name="default-visual-basic"></a>Výchozí (Visual Basic)
Identifikuje vlastnost jako výchozí vlastnost své třídy, struktury nebo rozhraní.  
  
## <a name="remarks"></a>Poznámky  
 Třídy, struktury nebo rozhraní můžete určit jenom jedna z jeho vlastnosti, jako *výchozí vlastnost*za předpokladu, že vlastnost používá nejméně jeden parametr. Pokud kód provede odkaz na třídy nebo struktury bez zadání členem, Visual Basic přeloží tento odkaz na výchozí vlastnost.  
  
 Výchozí vlastnosti může vést k malé snížení zdrojového kódu – znaků, ale váš kód mohl provést obtížněji čitelný. Pokud volající kód není znáte třídy nebo struktury, když se vytváří odkaz na název třídy nebo struktury nemůže být určité Určuje, zda přistupuje k této referenční třídy nebo struktury samotné nebo výchozí vlastnost. To může vést k chybám kompilátoru nebo běhové logiky drobné chyby.  
  
 Můžete poněkud snížit pravděpodobnost vzniku chyby výchozí vlastnost vždy používat [Option Strict – příkaz](../../../visual-basic/language-reference/statements/option-strict-statement.md) nastavení kompilátoru kontroly typů pro `On`.  
  
 Pokud máte v úmyslu použít předdefinované třídy nebo struktury v kódu, musíte určit, zda má výchozí vlastnosti a pokud ano, co její název je.  
  
 Z důvodu tyto nevýhody měli byste zvážit, není definování výchozí vlastnosti. Pro lepší čitelnost kódu byste také vzít v úvahu vždy odkazuje na všechny vlastnosti explicitně, dokonce i výchozí vlastnosti.  
  
 `Default` Modifikátor lze použít v tomto kontextu:  
  
 [Příkaz Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Deklarace a volání výchozí vlastnosti v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md)
- [Klíčová slova](../../../visual-basic/language-reference/keywords/index.md)
