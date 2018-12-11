---
title: Zaškrtnuto a nezaškrtnuto - C# odkaz
ms.custom: seodec18
ms.date: 05/15/2018
helpviewer_keywords:
- operators [C#], checked and unchecked
- exceptions [C#], overflow checking
- checked statement [C#]
- overflow checking [C#]
- unchecked statement [C#]
- statements [C#], checked and unchecked
ms.assetid: a84bc877-2c7f-4396-8735-1ce97c42f35e
ms.openlocfilehash: ba4ddd7fa87eb200de0de3aea6f0bc056a40f0e5
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53235800"
---
# <a name="checked-and-unchecked-c-reference"></a>Zaškrtnuto a nezaškrtnuto (Referenční dokumentace jazyka C#)
Příkazy jazyka C# lze spustit v kontextu zaškrtnuté nebo nezaškrtnuté. Aritmetické přetečení ve zkontrolovaném kontextu, vyvolá výjimku. V nekontrolovaném kontextu je ignorován Přetečení aritmetické operace a výsledek je rozdělená do se zahodí všechny bity nejvyšším, které se nehodí do cílového typu.  
  
-   [checked](checked.md) kontextu zadejte zaškrtnuto.  
  
-   [unchecked](unchecked.md) zadejte nezkontrolovaném kontextu.  
  
 Tyto operace jsou ovlivněny kontrola přetečení:  
  
-   Pomocí následující předdefinované operátory na integrální typy výrazů:  
  
     `++`, `--`, unární `-`, `+`, `-`, `*`, `/`  
  
-   Explicitní číselné převody mezi celočíselnými typy nebo z `float` nebo `double` na celočíselný typ.  
  
 Pokud ani `checked` ani `unchecked` není zadán, výchozí kontext pro výrazy nekonstantní (výrazy, které jsou vyhodnocovány v době běhu) je definován hodnotou [-checked](../compiler-options/checked-compiler-option.md) – možnost kompilátoru. Ve výchozím nastavení má tato možnost hodnotu unset a aritmetické operace jsou provedeny v nekontrolovaném kontextu.
 
 Pro konstantní výrazy (výrazy, které může být plně vyhodnocen v době kompilace) je vždy zaškrtnuto výchozí kontext. Pokud není konstantní výraz je explicitně umístěné v nekontrolovaném kontextu, přetečení, ke kterým dochází při vyhodnocení za kompilace výrazu způsobit chyby kompilace.
  
## <a name="see-also"></a>Viz také  

- [Referenční dokumentace jazyka C#](../index.md)  
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)  
- [Klíčová slova jazyka C#](index.md)  
- [Klíčová slova příkazů](statement-keywords.md)
