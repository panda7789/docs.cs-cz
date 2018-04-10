---
title: Zpracování výjimek (F#)
description: 'Seznámíte se základy zpracování výjimek v F # a odkazy na výrazy a funkce pro zpracování výjimek.'
keywords: 'Visual f #, f #, funkční programování'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: ad475c4a-d94e-47d9-b27b-3ff000b65f8e
ms.openlocfilehash: b61af66e0a70fdf9b86df37418c0284957d1f99e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
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
