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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5183a854ee2b7462ecc27786a5fc0697565194c0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61970856"
---
# <a name="how-to-use-the-trycatch-block-to-catch-exceptions"></a>Postup používání bloku try/catch k zachycování výjimek

Umístěte všechny příkazy, které mohou vyvolat nebo vyvolat výjimku `try` bloku a používá ke zpracování výjimky nebo výjimky v jednom nebo více příkazů místo `catch` níže uvedených bloků `try` bloku. Každý `catch` blok obsahuje typ výjimky a může obsahovat další příkazy potřebné ke zpracování tohoto typu výjimky.

V následujícím příkladu <xref:System.IO.StreamReader> otevře soubor s názvem *data.txt* a načte řádek ze souboru. Protože kód může vyvolat výjimky tři, je umístěný v `try` bloku. Tři `catch` bloky catch výjimky a mohli je zpracovat zobrazením výsledků do konzoly.

[!code-csharp[CatchException#3](~/samples/snippets/csharp/VS_Snippets_CLR/CatchException/CS/catchexception2.cs#3)]
[!code-vb[CatchException#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/CatchException/VB/catchexception2.vb#3)]  

Common Language Runtime (CLR) zachytává výjimky není zpracována `catch` bloky. Pokud je výjimka zachycena platformou CLR, jednu z následujících výsledků může dojít v závislosti na vaší konfiguraci modulu CLR:

- A **ladění** zobrazí se dialogové okno.
- Program se zastaví provádění a zobrazí se dialogové okno s informací o výjimce.
- Chyba vytiskne na [standardní chybový proud výstup](xref:System.Console.Error).

> [!NOTE]
> Většinu kódu může vyvolat výjimku a výjimkami, jako je třeba <xref:System.OutOfMemoryException>, mohou být vyvolány pomocí modulu CLR, samotný kdykoli. Když aplikace není nutné zacházet s těmito výjimkami, mějte na paměti možnost při zápisu knihoven a využívat další uživatelé. Pro návrhy toho, kdy k nastavení kódu v `try` blokovat, najdete v článku [osvědčené postupy pro výjimky](best-practices-for-exceptions.md).

## <a name="see-also"></a>Viz také:

[Výjimky](index.md)  
[Zpracování chyb vstupně-výstupní operace v rozhraní .NET](../io/handling-io-errors.md)
