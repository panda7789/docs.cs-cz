---
title: Použití objektů, které implementují IDisposable
description: Naučte se používat objekty, které implementují rozhraní IDisposable v .NET. Typy, které používají nespravované prostředky, implementují IDisposable, aby bylo možné prostředky znovu získat.
ms.date: 05/13/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Dispose method
- try/finally block
- garbage collection, encapsulating resources
ms.assetid: 81b2cdb5-c91a-4a31-9c83-eadc52da5cf0
ms.openlocfilehash: 7d5d4080f22aab6870a230d495b4a4b9ebcb3b96
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599851"
---
# <a name="using-objects-that-implement-idisposable"></a>Použití objektů, které implementují IDisposable

Systém uvolňování paměti modulu CLR (Common Language Runtime) uvolňuje paměť, kterou používají spravované objekty, ale typy, které používají nespravované prostředky, implementují <xref:System.IDisposable> rozhraní, které umožňuje, aby prostředky, které tyto nespravované prostředky potřebovaly, byly uvolněny. Po dokončení použití objektu, který implementuje <xref:System.IDisposable> , byste měli zavolat <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementaci objektu. Toto lze provést jedním ze dvou způsobů:

- Pomocí příkazu jazyka C# `using` ( `Using` v Visual Basic).
- Implementací `try/finally` bloku a voláním <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> v `finally` .

## <a name="the-using-statement"></a>Pomocí příkazu using

[ `using` Příkaz](../../csharp/language-reference/keywords/using-statement.md) v jazyce C# a [ `Using` příkaz](../../visual-basic/language-reference/statements/using-statement.md) v Visual Basic zjednoduší kód, který je nutné zapsat pro vyčištění objektu. `using`Příkaz získá jeden nebo více prostředků, spustí příkazy, které zadáte, a automaticky odstraní objekt. `using`Příkaz je však vhodný pouze pro objekty, které jsou používány v rámci rozsahu metody, ve které jsou vytvořeny.

Následující příklad používá `using` příkaz k vytvoření a uvolnění <xref:System.IO.StreamReader?displayProperty=nameWithType> objektu.

[!code-csharp[Conceptual.Disposable#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using1.cs#1)]
[!code-vb[Conceptual.Disposable#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using1.vb#1)]

I když <xref:System.IO.StreamReader> Třída implementuje <xref:System.IDisposable> rozhraní, což znamená, že používá nespravovaný prostředek, příklad explicitně nevolá <xref:System.IO.StreamReader.Dispose%2A?displayProperty=nameWithType> metodu. Když kompilátor jazyka C# nebo Visual Basic nalezne `using` příkaz, vygeneruje převodní jazyk (IL), který je ekvivalentní následujícímu kódu, který explicitně obsahuje `try/finally` blok.

[!code-csharp[Conceptual.Disposable#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using3.cs#3)]
[!code-vb[Conceptual.Disposable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using3.vb#3)]

Příkaz jazyka C# `using` také umožňuje získat více prostředků v jednom příkazu, který je interně ekvivalentní vnořeným `using` příkazům. Následující příklad vytvoří instanci dvou <xref:System.IO.StreamReader> objektů pro čtení obsahu dvou různých souborů.

[!code-csharp[Conceptual.Disposable#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using4.cs#4)]

## <a name="tryfinally-block"></a>Testovací blok / bezpodmínečný blok

Místo zabalení `try/finally` bloku v `using` příkazu můžete zvolit `try/finally` přímé implementace bloku. Může to být váš osobní styl kódování nebo to může být vhodné v jednom z následujících důvodů:

- Chcete-li zahrnout `catch` blok pro zpracování výjimek vyvolaných v `try` bloku. V opačném případě jakékoli výjimky vyvolané v rámci `using` příkazu nejsou ošetřeny.

- Pro vytvoření instance objektu, který implementuje, <xref:System.IDisposable> jehož obor není místní pro blok, ve kterém je deklarována.

Následující příklad je podobný předchozímu příkladu s tím rozdílem, že používá `try/catch/finally` blok pro vytvoření instance, použití a uvolnění <xref:System.IO.StreamReader> objektu a ke zpracování jakýchkoli výjimek vyvolaných <xref:System.IO.StreamReader> konstruktorem a jeho <xref:System.IO.StreamReader.ReadToEnd%2A> metodou. Kód v `finally` bloku kontroluje, zda objekt, který implementuje, <xref:System.IDisposable> není `null` před voláním <xref:System.IDisposable.Dispose%2A> metody. V takovém případě může dojít k <xref:System.NullReferenceException> výjimce za běhu.

[!code-csharp[Conceptual.Disposable#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using5.cs#6)]
[!code-vb[Conceptual.Disposable#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using5.vb#6)]

Můžete postupovat podle tohoto základního vzoru, pokud se rozhodnete implementovat nebo musíte implementovat `try/finally` blok, protože váš programovací jazyk nepodporuje `using` příkaz, ale umožňuje přímé volání <xref:System.IDisposable.Dispose%2A> metody.

## <a name="idisposable-instance-members"></a>Členové instance IDisposable

Pokud třída obsahuje <xref:System.IDisposable> implementaci jako člen instance, měla by být třída také implementovaná buď pole, nebo vlastnost <xref:System.IDisposable> . Další informace najdete v tématu [implementace kaskádové likvidace](implementing-dispose.md#cascade-dispose-calls).

## <a name="see-also"></a>Viz také

- [Čištění nespravovaných prostředků](unmanaged.md)
- [using – příkaz (Referenční dokumentace jazyka C#)](../../csharp/language-reference/keywords/using-statement.md)
- [Using – příkaz (Visual Basic)](../../visual-basic/language-reference/statements/using-statement.md)
