---
title: 'Postupy: Používání bloku Try/Catch k zachycování výjimek'
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
ms.openlocfilehash: 5a9218d394b76e897f4263708a10f1bc895ad4e1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75708463"
---
# <a name="how-to-use-the-trycatch-block-to-catch-exceptions"></a>Jak použít blok try/catch k zachycení výjimek

Umístěte všechny příkazy kódu, které mohou `try` vyvolat nebo vyvolat výjimku v bloku a umístit `catch` příkazy `try` používané ke zpracování výjimky nebo výjimky v jednom nebo více bloků pod blok. Každý `catch` blok obsahuje typ výjimky a může obsahovat další příkazy potřebné ke zpracování tohoto typu výjimky.

V následujícím příkladu <xref:System.IO.StreamReader> otevře soubor s názvem *data.txt* a načte řádek ze souboru. Vzhledem k tomu, že kód může vyvolat některou ze tří výjimek, je umístěn v `try` bloku. Tři `catch` bloky zachytit výjimky a zpracovat je zobrazením výsledky do konzoly.

[!code-csharp[CatchException#3](~/samples/snippets/csharp/VS_Snippets_CLR/CatchException/CS/catchexception2.cs#3)]
[!code-vb[CatchException#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/CatchException/VB/catchexception2.vb#3)]

Common Language Runtime (CLR) zachytí `catch` výjimky, které nejsou zpracovány bloky. Pokud je výjimka zachycena CLR, může dojít k jednomu z následujících výsledků v závislosti na konfiguraci CLR:

- Zobrazí se dialogové okno **Ladění.**
- Program zastaví provádění a zobrazí se dialogové okno s informacemi o výjimce.
- Chyba se vytiskne do [výstupního datového proudu standardní chyby](xref:System.Console.Error).

> [!NOTE]
> Většina kódu může vyvolat výjimku a <xref:System.OutOfMemoryException>některé výjimky, jako je , může být vyvolána CLR sám kdykoli. Zatímco aplikace nejsou nutné k řešení těchto výjimek, být vědomi možnosti při psaní knihoven, které mají být použity jinými uživateli. Návrhy, kdy nastavit kód `try` v bloku, najdete v [tématu Doporučené postupy pro výjimky](best-practices-for-exceptions.md).

## <a name="see-also"></a>Viz také

- [Výjimky](index.md)
- [Zpracování vstupně-v.I chyb v rozhraní .NET](../io/handling-io-errors.md)
