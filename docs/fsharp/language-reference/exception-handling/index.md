---
title: Zpracování výjimek
description: Seznamte se se základy zpracování výjimek v F# a odkazy na výrazy a funkce pro zpracování výjimek.
ms.date: 05/16/2016
ms.openlocfilehash: 187236ca380c7de0b3714160f6c3703f8fb93d5a
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/19/2018
ms.locfileid: "53614438"
---
# <a name="exception-handling"></a>Zpracování výjimek

Tato část obsahuje informace o podpoře v zpracování výjimek F# jazyka.

## <a name="exception-handling-basics"></a>Základy zpracování výjimek
Zpracování výjimek je standardní způsob zpracování chyb v rozhraní .NET Framework. To znamená, libovolný jazyk .NET musí podporovat tento mechanismus, včetně F#. *Výjimka* je objekt, který zapouzdřuje informace o chybě. Když dojde k chybám, výjimky jsou provádění pravidelných a nevyskytla se zastaví. Místo toho modul runtime vyhledá odpovídající obslužná rutina výjimky. Hledání začne v aktuální funkci a zásobníkem prostřednictvím vrstev volající pokračuje, dokud není nalezena odpovídající obslužná rutina. Pak je provedena obslužné rutiny.

Kromě toho, jak je zásobník odvinut, modul runtime spustí libovolný kód v `finally` bloky, chcete-li zaručit, že se objekty během odvíjení správně vyčistí.

## <a name="related-topics"></a>Související témata

|Název|Popis|
|-----|-----------|
|[Typy výjimek](exception-types.md)|Popisuje, jak deklarovat typ výjimky.|
|[Výjimky: `try...with` Výraz](the-try-with-expression.md)|Popisuje konstrukce jazyka, který podporuje zpracování výjimek.|
|[Výjimky: `try...finally` Výraz](the-try-finally-expression.md)|Popisuje konstrukce jazyka, který můžete spustit kód pro vyčištění jako zásobník unwinds, když dojde k výjimce.|
|[Výjimky: `raise` – funkce](the-raise-Function.md)|Popisuje, jak vyvolat objektu výjimky.|
|[Výjimky: `failwith` – Funkce](the-failwith-function.md)|Popisuje, jak generovat Obecné F# výjimky.|
|[Výjimky: `invalidArg` – Funkce](the-invalidArg-function.md)|Popisuje, jak generovat výjimku neplatný argument.|