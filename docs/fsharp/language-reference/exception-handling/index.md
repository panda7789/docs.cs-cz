---
title: Zpracování výjimek (F#)
description: 'Seznámíte se základy zpracování výjimek v F # a odkazy na výrazy a funkce pro zpracování výjimek.'
ms.date: 05/16/2016
ms.openlocfilehash: fc89feb0d21bc823cb105e435413f8309cd6174c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="exception-handling"></a>Zpracování výjimek

Tato část obsahuje informace o zpracování podpory v jazyce F # výjimek.


## <a name="exception-handling-basics"></a>Základy zpracování výjimek
Zpracovávání výjimek v jazyce je standardním způsobem zpracovávat chybové stavy v rozhraní .NET Framework. Proto kterémkoli jazyce platformy .NET musí podporovat tento mechanismus, včetně F #. *Výjimka* je objekt, který zapouzdří informace o chybě. Pokud dojde k chybám, výjimky jsou provádění pravidelných a nevyskytla se zastaví. Místo toho modul runtime vyhledá příslušnou obslužnou rutinu pro výjimku. Hledání se spustí v aktuální funkce a pokračuje až zásobníku prostřednictvím vrstvy volající, dokud nebude nalezen odpovídající obslužná rutina. Pak je spustit obslužnou rutinu.

Kromě toho je oddělen zásobníku, modul runtime provede žádný kód v `finally` bloky, chcete-li zaručit, že jsou objekty během procesu unwinding správně vyčištěna.


## <a name="related-topics"></a>Související témata

|Název|Popis|
|-----|-----------|
|[Typy výjimek](exception-types.md)|Popisuje, jak deklarovat typ výjimky.|
|[Výjimky: `try...with` výraz](the-try-with-expression.md)|Popisuje konstrukce jazyk, který podporuje zpracování výjimek.|
|[Výjimky: `try...finally` výraz](the-try-finally-expression.md)|Popisuje konstrukce jazyk, který umožňuje spuštění kódu čištění jako zásobníku unwinds, když je vyvolána výjimka.|
|[Výjimky: `raise` – funkce](the-raise-Function.md)|Popisuje, jak má být vyvolána výjimka objekt.|
|[Výjimky: `failwith` – funkce](the-failwith-function.md)|Popisuje, jak vygenerovat k obecné výjimce F #.|
|[Výjimky: `invalidArg` – funkce](the-invalidArg-function.md)|Popisuje, jak generovat výjimku neplatný argument.|
