---
title: Výchozí
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
ms.openlocfilehash: ad4c9528f208cc2c31f07b0506d1b049a7568c86
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351572"
---
# <a name="default-visual-basic"></a>Výchozí (Visual Basic)
Identifikuje vlastnost jako výchozí vlastnost své třídy, struktury nebo rozhraní.  
  
## <a name="remarks"></a>Poznámky  
 Třída, struktura nebo rozhraní mohou jako *výchozí vlastnost*označovat nejvíce jednu z jejích vlastností, za předpokladu, že vlastnost přebírá alespoň jeden parametr. Pokud kód vytvoří odkaz na třídu nebo strukturu bez určení člena, Visual Basic tento odkaz přeloží na výchozí vlastnost.  
  
 Výchozí vlastnosti můžou mít za následek malé snížení počtu znaků zdrojového kódu, ale můžou ztížit čtení kódu. Pokud volající kód není obeznámen s vaší třídou nebo strukturou, při odkazování na název třídy nebo struktury nemůže být jisté, zda tento odkaz přistupuje k třídě nebo struktuře samotné nebo výchozí vlastnosti. To může vést k chybám kompilátoru nebo k drobným chybám logiky run-time.  
  
 Můžete trochu snížit šanci na chyby výchozích vlastností – vždy pomocí [příkazu Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md) nastavit kontrolu typu kompilátoru na `On`.  
  
 Pokud plánujete použít předdefinovanou třídu nebo strukturu v kódu, je nutné určit, zda má výchozí vlastnost, a pokud ano, jaký je její název.  
  
 Z důvodu těchto nevýhody byste měli zvážit, že nedefinujete výchozí vlastnosti. V případě čitelnosti kódu byste měli také zvážit možnost vždy odkazovat na všechny vlastnosti, a to i na výchozí vlastnosti.  
  
 V tomto kontextu lze použít modifikátor `Default`:  
  
 [Příkaz Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a>Viz také:

- [Postupy: deklarace a volání výchozí vlastnosti v Visual Basic](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md)
- [Klíčová slova](../../../visual-basic/language-reference/keywords/index.md)
