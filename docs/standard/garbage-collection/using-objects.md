---
title: Použití objektů, které implementují IDisposable
ms.date: 04/07/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Dispose method
- try/finally block
- garbage collection, encapsulating resources
ms.assetid: 81b2cdb5-c91a-4a31-9c83-eadc52da5cf0
ms.openlocfilehash: 979cd782e5ab094b6dea010fc7a0b27caa390e67
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141342"
---
# <a name="using-objects-that-implement-idisposable"></a>Použití objektů, které implementují IDisposable

Systém uvolňování paměti modulu CLR (Common Language Runtime) uvolňuje paměť využívané spravovanými objekty, ale typy, které používají nespravované prostředky, implementují rozhraní <xref:System.IDisposable>, aby mohla být uvolněna paměť přidělená těmto nespravovaným prostředkům. Po dokončení použití objektu, který implementuje <xref:System.IDisposable>, byste měli zavolat implementaci <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> objektu. Toto lze provést jedním ze dvou způsobů:  
  
- Pomocí příkazu C# `using` nebo příkazu Visual Basic `Using`.  
  
- Implementací bloku `try/finally`.  

## <a name="the-using-statement"></a>Pomocí příkazu using

Příkaz `using` v C# a příkaz `Using` v Visual Basic zjednodušuje kód, který je nutné zapsat pro vytvoření a vyčištění objektu. Příkaz `using` získá jeden nebo více prostředků, spustí příkazy, které zadáte, a automaticky odstraní objekt. Příkaz `using` je vhodný pouze pro objekty, které jsou používány v rámci rozsahu metody, ve které jsou vytvořeny.  
  
Následující příklad používá příkaz `using` k vytvoření a uvolnění objektu <xref:System.IO.StreamReader?displayProperty=nameWithType>.  
  
[!code-csharp[Conceptual.Disposable#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using1.cs#1)]
[!code-vb[Conceptual.Disposable#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using1.vb#1)]  
  
Všimněte si, že i když třída <xref:System.IO.StreamReader> implementuje rozhraní <xref:System.IDisposable>, což znamená, že používá nespravovaný prostředek, příklad explicitně nevolá metodu <xref:System.IO.StreamReader.Dispose%2A?displayProperty=nameWithType>. Když kompilátor C# nebo Visual Basic nalezne příkaz `using`, vygeneruje převodní jazyk (IL), který je ekvivalentní následujícímu kódu, který explicitně obsahuje blok `try/finally`.  
  
[!code-csharp[Conceptual.Disposable#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using3.cs#3)]
[!code-vb[Conceptual.Disposable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using3.vb#3)]  
  
Příkaz C# `using` také umožňuje získat více prostředků v jednom příkazu, který je interně ekvivalentní vnořeným `using`m příkazům. Následující příklad vytvoří instanci dvou objektů <xref:System.IO.StreamReader> pro čtení obsahu dvou různých souborů.  
  
[!code-csharp[Conceptual.Disposable#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using4.cs#4)]

## <a name="tryfinally-block"></a>Testovací blok / bezpodmínečný blok

Namísto zabalení `try/finally` bloku v příkazu `using`, můžete zvolit přímé implementace `try/finally` bloku. Může se jednat o váš vlastní styl psaní kódu nebo tak můžete činit z jednoho z následujících důvodů:  
  
- Chcete-li zahrnout blok `catch` pro zpracování jakýchkoli výjimek vyvolaných v bloku `try`. V opačném případě jakékoli výjimky vyvolané příkazem `using` nejsou ošetřeny, stejně jako jakékoli výjimky vyvolané v rámci `using` bloku, pokud není přítomen blok `try/catch`.  
  
- Chcete-li vytvořit instanci objektu, který implementuje <xref:System.IDisposable>, jehož obor není místní pro blok, ve kterém je deklarována.  
  
Následující příklad je podobný předchozímu příkladu s tím rozdílem, že používá `try/catch/finally` blok pro vytvoření instance, použití a Dispose objektu <xref:System.IO.StreamReader> a ke zpracování jakýchkoli výjimek vyvolaných konstruktorem <xref:System.IO.StreamReader> a její <xref:System.IO.StreamReader.ReadToEnd%2A>ou metodou. Všimněte si, že kód v bloku `finally` kontroluje, zda objekt, který implementuje <xref:System.IDisposable> není `null` před voláním metody <xref:System.IDisposable.Dispose%2A>. V takovém případě může dojít k výjimce <xref:System.NullReferenceException> v době běhu.  
  
[!code-csharp[Conceptual.Disposable#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using5.cs#6)]
[!code-vb[Conceptual.Disposable#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using5.vb#6)]  
  
Můžete postupovat podle tohoto základního vzoru, pokud se rozhodnete implementovat nebo musíte implementovat blok `try/finally`, protože váš programovací jazyk nepodporuje příkaz `using`, ale umožňuje přímé volání metody <xref:System.IDisposable.Dispose%2A>. 
  
## <a name="see-also"></a>Viz také:

- [Vymazání nespravovaných prostředků](../../../docs/standard/garbage-collection/unmanaged.md)
- [using – příkazC# (Referenční dokumentace)](../../csharp/language-reference/keywords/using-statement.md)
- [Using – příkaz (Visual Basic)](../../visual-basic/language-reference/statements/using-statement.md)
