---
title: Zaškrtnuto a nezaškrtnuto (Referenční dokumentace jazyka C#)
ms.date: 05/15/2018
helpviewer_keywords:
- operators [C#], checked and unchecked
- exceptions [C#], overflow checking
- checked statement [C#]
- overflow checking [C#]
- unchecked statement [C#]
- statements [C#], checked and unchecked
ms.assetid: a84bc877-2c7f-4396-8735-1ce97c42f35e
ms.openlocfilehash: f8e292a67fab49b5fc3616e438d063eca2617274
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/17/2018
ms.locfileid: "34234370"
---
# <a name="checked-and-unchecked-c-reference"></a>Zaškrtnuto a nezaškrtnuto (Referenční dokumentace jazyka C#)
Příkazy jazyka C# můžete spustit v kontextu zaškrtnuté nebo nezaškrtnuté. V kontextu zaškrtnuté Přetečení aritmetické funkce vyvolá výjimku. V kontextu nezaškrtnuté aritmetického přetečení je ignorován a výsledek je rozdělená do zahození žádné nejvyšších bitů, které se nehodí typu cílového.  
  
-   [zaškrtnutí](checked.md) zadejte zaškrtnutí kontextu.  
  
-   [nezaškrtnuté](unchecked.md) zadejte nezaškrtnuté kontextu.  
  
 Kontrola přetečení se týká následující operace:  
  
-   Pomocí následující předdefinované operátory na integrální typy výrazů:  
  
     `++`, `--`, unární `-`, `+`, `-`, `*`, `/`  
  
-   Explicitní číselné převody mezi celočíselných typů, nebo z `float` nebo `double` integrální typu.  
  
 Pokud ani `checked` ani `unchecked` je zadána výchozí kontext není konstantní výrazy (výrazy, které jsou vyhodnocovány v době běhu) je definován hodnotou [-zaškrtnutí](../compiler-options/checked-compiler-option.md) – možnost kompilátoru. Ve výchozím nastavení je hodnota tuto možnost nastavení a aritmetické operace jsou spouštěny v kontextu není zaškrtnuto.
 
 Pro konstantní výrazy (výrazy, které se dají posoudit plně v době kompilace) je vždy zaškrtnuto výchozí kontext. Pokud konstantní výraz je explicitně umístěn v kontextu není zaškrtnuto, některé, ke kterým došlo během kompilace vyhodnocování výrazu způsobit chyby při kompilaci.
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../index.md)  
 [Průvodce programováním v jazyce C#](../../programming-guide/index.md)  
 [Klíčová slova jazyka C#](index.md)  
 [Klíčová slova příkazů](statement-keywords.md)
