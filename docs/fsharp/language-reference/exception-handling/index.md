---
title: Zpracování výjimek
description: Naučte se základy zpracování výjimek v F# a hledání odkazů na výrazy a funkce zpracování výjimek.
ms.date: 05/16/2016
ms.openlocfilehash: e34a65dd7da9d706153254ac28e729de0745e4d0
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423062"
---
# <a name="exception-handling"></a>Zpracování výjimek

Tato část obsahuje informace o podpoře zpracování výjimek v F# jazyce.

## <a name="exception-handling-basics"></a>Základy zpracování výjimek

Zpracování výjimek je standardní způsob zpracování chybových podmínek v .NET Framework. Proto musí jakýkoli jazyk .NET podporovat tento mechanismus, včetně F#. *Výjimkou* je objekt, který zapouzdřuje informace o chybě. Pokud dojde k chybám, jsou vyvolány výjimky a pravidelné spouštění se zastaví. Místo toho modul runtime vyhledá odpovídající obslužnou rutinu pro výjimku. Hledání začne v aktuální funkci a pokračuje v zásobníku prostřednictvím vrstev volajících, dokud není nalezena vyhovující obslužná rutina. Pak se obslužná rutina spustí.

Vzhledem k tomu, že se zásobník odvíjí, modul runtime spustí jakýkoliv kód v `finally`ch blocích, aby bylo zaručeno, že se objekty během procesu odvíjení správně vyčistí.

## <a name="related-topics"></a>Související témata

|Název|Popis|
|-----|-----------|
|[Typy výjimek](exception-types.md)|Popisuje, jak deklarovat typ výjimky.|
|[Výjimky: výraz `try...with`](the-try-with-expression.md)|Popisuje jazykovou konstrukci, která podporuje zpracování výjimek.|
|[Výjimky: výraz `try...finally`](the-try-finally-expression.md)|Popisuje jazykovou konstrukci, která umožňuje spustit čistý kód v případě, že je vyvolána výjimka, když dojde k výjimce zásobníku.|
|[Výjimky: funkce `raise`](the-raise-Function.md)|Popisuje, jak vyvolat objekt výjimky.|
|[Výjimky: funkce `failwith`](the-failwith-function.md)|Popisuje, jak vygenerovat obecnou F# výjimku.|
|[Výjimky: funkce `invalidArg`](the-invalidArg-function.md)|Popisuje, jak vygenerovat výjimku neplatného argumentu.|
