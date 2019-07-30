---
title: Typy chyb (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions, types
- errors [Visual Basic], types
- errors [Visual Basic], logic
- errors [Visual Basic], syntax
- logic errors [Visual Basic], Visual Basic
- run-time errors [Visual Basic], types of errors
- syntax errors [Visual Basic], Visual Basic
ms.assetid: 3048aabf-8c97-4e13-9150-853769cb5f6f
ms.openlocfilehash: 030986111a50ab59c605a1d683fedc118d10b260
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68626609"
---
# <a name="error-types-visual-basic"></a>Typy chyb (Visual Basic)
V Visual Basic chyby spadají do jedné ze tří kategorií: syntaktické chyby, běhové chyby a logické chyby.

## <a name="syntax-errors"></a>Chyby syntaxe
 *Chyby syntaxe* jsou ty, které se zobrazí při psaní kódu. Pokud používáte aplikaci Visual Studio, Visual Basic zkontroluje kód při jeho psaní v okně **editoru kódu** a upozorní vás, pokud uděláte chybu, jako je například chybné zadání slova nebo použití nesprávně používaného prvku jazyka. Pokud kompilujete z příkazového řádku, Visual Basic zobrazí chybu kompilátoru s informacemi o chybě syntaxe. Nejběžnějším typem chyb jsou chyby syntaxe. Můžete je snadno opravit v prostředí kódování ihned po jejich výskytu.

> [!NOTE]
>  `Option Explicit` Příkaz je jedním ze způsobů, jak zabránit chybám syntaxe. Vynutí vám deklarovat předem všechny proměnné, které mají být použity v aplikaci. Proto pokud jsou tyto proměnné použity v kódu, jakékoli typografické chyby jsou okamžitě zachyceny a lze je opravit.

## <a name="run-time-errors"></a>Běhové chyby
 *Běhové chyby* jsou ty, které se zobrazí až po zkompilování a spuštění kódu. Ty zahrnují kód, který může být v tom, že neobsahuje žádné chyby syntaxe, ale který nebude proveden. Například můžete správně napsat řádek kódu pro otevření souboru. Pokud však soubor neexistuje, aplikace nemůže soubor otevřít a vyvolá výjimku. Většinu chyb za běhu můžete opravit přepsáním chybného kódu nebo pomocí [zpracování výjimek](../../language-reference/statements/try-catch-finally-statement.md)a pak ho znovu zkompilovat a znovu spustit.
  
## <a name="logic-errors"></a>Logické chyby
 *Logické chyby* jsou ty, které se zobrazí, jakmile se aplikace používá. Jsou to nejčastěji vadné předpoklady, které vývojář udělal, nebo nechtěné nebo neočekávané výsledky v reakci na akce uživatele. Například nesprávně natypový klíč může poskytnout nesprávné informace metodě nebo můžete předpokládat, že platná hodnota je vždy dodána metodě, pokud to není případ. I když mohou být logické chyby zpracovávány pomocí [zpracování výjimek](../../language-reference/statements/try-catch-finally-statement.md) (například otestováním, zda je `Nothing` argument a vyvolání <xref:System.ArgumentNullException>), nejčastěji by měly být řešeny opravou chyby v logice a opětovnou kompilací použití.

## <a name="see-also"></a>Viz také:

- [Příkaz Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [Základy ladicího programu](/visualstudio/debugger/debugger-basics)
