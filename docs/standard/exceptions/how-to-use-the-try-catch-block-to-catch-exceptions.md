---
title: 'Postupy: Používání bloku Try/Catch k zachycování výjimek'
description: Použijte blok try k zahrnutí příkazů, které mohou vyvolat nebo vyvolat výjimku. Umístěte příkazy pro zpracování výjimek v jednom nebo více blocích catch.
ms.date: 02/06/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- exceptions, try/catch blocks
- try blocks
- try/catch blocks
- catch blocks
ms.assetid: a3ce6dfd-1f64-471b-8ad8-8cfaf406275d
ms.openlocfilehash: 60ed213ea777fe35873fd1e67555b7506e3ca587
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/15/2020
ms.locfileid: "84768908"
---
# <a name="how-to-use-the-trycatch-block-to-catch-exceptions"></a>Jak zachytit výjimky pomocí bloku try/catch

Umístěte jakékoli příkazy kódu, které mohou vyvolat nebo vyvolat výjimku v `try` bloku a umístit příkazy používané pro zpracování výjimky nebo výjimek v jednom nebo více `catch` blocích pod `try` blokem. Každý `catch` blok zahrnuje typ výjimky a může obsahovat další příkazy potřebné ke zpracování tohoto typu výjimky.

V následujícím příkladu <xref:System.IO.StreamReader> otevře soubor s názvem *data.txt* a načte řádek ze souboru. Vzhledem k tomu, že kód může vyvolat některou ze tří výjimek, je umístěn v `try` bloku. Tři `catch` bloky zachytí výjimky a zpracovávají je zobrazením výsledků do konzoly.

[!code-csharp[CatchException#3](~/samples/snippets/csharp/VS_Snippets_CLR/CatchException/CS/catchexception2.cs#3)]
[!code-vb[CatchException#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/CatchException/VB/catchexception2.vb#3)]

Modul CLR (Common Language Runtime) zachytává výjimky, které nejsou zpracovávány `catch` bloky. Pokud je výjimka zachycena modulem CLR, může dojít k jednomu z následujících výsledků v závislosti na konfiguraci CLR:

- Zobrazí se dialogové okno **ladění** .
- Program zastaví provádění a zobrazí se dialogové okno s informacemi o výjimce.
- Chyba se tiskne do [standardního výstupního datového proudu chyb](xref:System.Console.Error).

> [!NOTE]
> Většina kódu může vyvolat výjimku a některé výjimky, například <xref:System.OutOfMemoryException> , mohou být vyvolány samotným modulem CLR kdykoli. I když se aplikace nevyžadují k tomu, aby se s těmito výjimkami musely zabývat, pamatujte na to, že při psaní knihoven, které budou používat ostatní Návrhy na to, kdy nastavit kód v `try` bloku, najdete v tématu [osvědčené postupy pro výjimky](best-practices-for-exceptions.md).

## <a name="see-also"></a>Viz také

- [Výjimky](index.md)
- [Zpracování vstupně-výstupních chyb v .NET](../io/handling-io-errors.md)
