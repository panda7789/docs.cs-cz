---
title: Výchozí (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Default
helpviewer_keywords:
- defaults, properties
- properties [Visual Basic], default
- default properties, in Visual Basic
- Default keyword [Visual Basic]
- default properties
ms.assetid: 45fce9b9-d212-4b2d-ab86-6e359b8b57af
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 18126a0a5b6254da0b43e806b3de1f5b2127e6a9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
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
  
 [Property – příkaz](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a>Viz také  
 [Postupy: deklarace a volání výchozí vlastnosti v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md)  
 [Klíčová slova](../../../visual-basic/language-reference/keywords/index.md)
