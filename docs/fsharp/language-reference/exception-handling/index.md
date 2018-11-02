---
title: Zpracování výjimek (F#)
description: Seznamte se se základy zpracování výjimek v F# a odkazy na výrazy a funkce pro zpracování výjimek.
ms.date: 05/16/2016
ms.openlocfilehash: fc89feb0d21bc823cb105e435413f8309cd6174c
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/02/2018
ms.locfileid: "33564323"
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
|[Výjimky: `try...with` výraz](the-try-with-expression.md)|Popisuje konstrukce jazyka, který podporuje zpracování výjimek.|
|[Výjimky: `try...finally` výraz](the-try-finally-expression.md)|Popisuje konstrukce jazyka, který můžete spustit kód pro vyčištění jako zásobník unwinds, když dojde k výjimce.|
|[Výjimky: `raise` – funkce](the-raise-Function.md)|Popisuje, jak vyvolat objektu výjimky.|
|[Výjimky: `failwith` – funkce](the-failwith-function.md)|Popisuje, jak generovat Obecné F# výjimky.|
|[Výjimky: `invalidArg` – funkce](the-invalidArg-function.md)|Popisuje, jak generovat výjimku neplatný argument.|
