---
title: Zaškrtnuto a nezaškrtnuto - odkaz jazyka C#
ms.date: 05/15/2018
helpviewer_keywords:
- operators [C#], checked and unchecked
- exceptions [C#], overflow checking
- checked statement [C#]
- overflow checking [C#]
- unchecked statement [C#]
- statements [C#], checked and unchecked
ms.assetid: a84bc877-2c7f-4396-8735-1ce97c42f35e
ms.openlocfilehash: 8ee4c481a30dce30029fbe8cc26f4798b523a7ed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173637"
---
# <a name="checked-and-unchecked-c-reference"></a>Zaškrtnuto a nezaškrtnuto (Referenční dokumentace jazyka C#)
Příkazy jazyka C# lze spustit v zadávaného nebo nekontrolovaném kontextu. V kontrolovaném kontextu aritmetické přetečení vyvolá výjimku. V nekontrolovaném kontextu je aritmetické přetečení ignorováno a výsledek je zkrácen zahozením všech bitů vyššího řádu, které se nevejdou do cílového typu.  
  
- [zaškrtnuto](checked.md) Zadejte kontrolovaný kontext.  
  
- [nezaškrtnuté políčko](unchecked.md) Zadejte nezaškrtnutý kontext.  
  
 Kontrola přetečení ovlivňuje následující operace:  
  
- Výrazy používající následující předdefinované operátory na integrálních typech:  
  
     `++`, `--`, `-`unární `-` `*`, `+`, ,`/`  
  
- Explicitní číselné převody mezi `float` integrální typy nebo z nebo `double` integrální typu.  
  
 Pokud ani `checked` `unchecked` není zadán, výchozí kontext pro nekonstantní výrazy (výrazy, které jsou vyhodnocovány za běhu) je definován hodnotou [-checked](../compiler-options/checked-compiler-option.md) kompilátoru možnost. Ve výchozím nastavení je hodnota této možnosti unset a aritmetické operace jsou prováděny v nekontrolovaném kontextu.

 Pro konstantní výrazy (výrazy, které lze plně vyhodnotit v době kompilace), výchozí kontext je vždy kontrolována. Pokud konstantní výraz je explicitně umístěn v nekontrolovaném kontextu, přetečení, ke kterým dochází během vyhodnocení výrazu v době kompilace způsobit chyby kompilace.
  
## <a name="see-also"></a>Viz také

- [Odkaz jazyka C#](../index.md)
- [Programovací příručka jazyka C#](../../programming-guide/index.md)
- [C# Klíčová slova](index.md)
- [Klíčová slova příkazů](statement-keywords.md)
