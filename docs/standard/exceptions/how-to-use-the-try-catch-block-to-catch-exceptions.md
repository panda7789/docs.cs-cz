---
title: 'Postupy: zachycení výjimek pomocí bloku try-catch'
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: eaa389f461e70aae41f2e09437fd725a3bcefa5e
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71696722"
---
# <a name="how-to-use-the-trycatch-block-to-catch-exceptions"></a>Jak zachytit výjimky pomocí bloku try/catch

Umístěte jakékoli příkazy kódu, které mohou vyvolat nebo vyvolat výjimku v bloku `try` a umístit příkazy používané pro zpracování výjimky nebo výjimek v jednom nebo více blocích `catch` pod blokem `try`. Každý blok `catch` zahrnuje typ výjimky a může obsahovat další příkazy potřebné ke zpracování tohoto typu výjimky.

V následujícím příkladu <xref:System.IO.StreamReader> otevře soubor s názvem *data. txt* a načte řádek ze souboru. Vzhledem k tomu, že kód může vyvolat některou ze tří výjimek, je umístěn v bloku `try`. Tři bloky `catch` zachycují výjimky a zpracovávají je zobrazením výsledků do konzoly.

[!code-csharp[CatchException#3](~/samples/snippets/csharp/VS_Snippets_CLR/CatchException/CS/catchexception2.cs#3)]
[!code-vb[CatchException#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/CatchException/VB/catchexception2.vb#3)]

Modul CLR (Common Language Runtime) zachytává výjimky, které nejsou zpracovány pomocí bloků `catch`. Pokud je výjimka zachycena modulem CLR, může dojít k jednomu z následujících výsledků v závislosti na konfiguraci CLR:

- Zobrazí se dialogové okno **ladění** .
- Program zastaví provádění a zobrazí se dialogové okno s informacemi o výjimce.
- Chyba se tiskne do [standardního výstupního datového proudu chyb](xref:System.Console.Error).

> [!NOTE]
> Většina kódu může vyvolat výjimku a některé výjimky, jako je například <xref:System.OutOfMemoryException>, mohou být vyvolány samotným modulem CLR kdykoli. I když se aplikace nevyžadují k tomu, aby se s těmito výjimkami musely zabývat, pamatujte na to, že při psaní knihoven, které budou používat ostatní Návrhy na to, kdy nastavit kód v bloku `try`, najdete v tématu [osvědčené postupy pro výjimky](best-practices-for-exceptions.md).

## <a name="see-also"></a>Viz také:

- [Výjimky](index.md)
- [Zpracování vstupně-výstupních chyb v .NET](../io/handling-io-errors.md)
