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
ms.openlocfilehash: 0c2808795d6fcbad7892369fd7f460ebf0406093
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84372969"
---
# <a name="default-visual-basic"></a>Výchozí (Visual Basic)
Identifikuje vlastnost jako výchozí vlastnost své třídy, struktury nebo rozhraní.  
  
## <a name="remarks"></a>Poznámky  
 Třída, struktura nebo rozhraní mohou jako *výchozí vlastnost*označovat nejvíce jednu z jejích vlastností, za předpokladu, že vlastnost přebírá alespoň jeden parametr. Pokud kód vytvoří odkaz na třídu nebo strukturu bez určení člena, Visual Basic tento odkaz přeloží na výchozí vlastnost.  
  
 Výchozí vlastnosti můžou mít za následek malé snížení počtu znaků zdrojového kódu, ale můžou ztížit čtení kódu. Pokud volající kód není obeznámen s vaší třídou nebo strukturou, při odkazování na název třídy nebo struktury nemůže být jisté, zda tento odkaz přistupuje k třídě nebo struktuře samotné nebo výchozí vlastnosti. To může vést k chybám kompilátoru nebo k drobným chybám logiky run-time.  
  
 Můžete trochu snížit pravděpodobnost chyb výchozích vlastností – vždy pomocí [příkazu Option Strict](../statements/option-strict-statement.md) nastavit kontrolu typu kompilátoru na `On` .  
  
 Pokud plánujete použít předdefinovanou třídu nebo strukturu v kódu, je nutné určit, zda má výchozí vlastnost, a pokud ano, jaký je její název.  
  
 Z důvodu těchto nevýhody byste měli zvážit, že nedefinujete výchozí vlastnosti. V případě čitelnosti kódu byste měli také zvážit možnost vždy odkazovat na všechny vlastnosti, a to i na výchozí vlastnosti.  
  
 `Default`V tomto kontextu lze použít modifikátor:  
  
 [Property – příkaz](../statements/property-statement.md)  
  
## <a name="see-also"></a>Viz také

- [Postupy: Deklarace a volání výchozí vlastnosti v jazyce Visual Basic](../../programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md)
- [Klíčová slova](../keywords/index.md)
