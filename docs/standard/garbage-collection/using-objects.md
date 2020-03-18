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
ms.openlocfilehash: c5232aa89064c514e71f3a18bc754159e9c9b15b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160275"
---
# <a name="using-objects-that-implement-idisposable"></a>Použití objektů, které implementují IDisposable

Uvolňování paměti modulu COMMON Jazyka runtime uvolňuje paměť používanou spravovanými <xref:System.IDisposable> objekty, ale typy, které používají nespravované prostředky, implementují rozhraní tak, aby paměť přidělená těmto nespravovaným prostředkům byla uvolněna. Po dokončení pomocí objektu, <xref:System.IDisposable>který implementuje , <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> měli byste volat implementaci objektu. Toto lze provést jedním ze dvou způsobů:  
  
- S c# `using` příkaz nebo `Using` visual basic prohlášení.  
  
- Implementací `try/finally` bloku.  

## <a name="the-using-statement"></a>Pomocí příkazu using

Příkaz `using` v jazyce `Using` C# a příkaz v jazyce Visual Basic zjednodušit kód, který je nutné napsat k vytvoření a vyčištění objektu. Příkaz `using` získá jeden nebo více prostředků, provede příkazy, které zadáte, a automaticky nakládá s objektem. `using` Příkaz je však užitečné pouze pro objekty, které se používají v rámci rozsahu metody, ve kterém jsou vytvořeny.  
  
Následující příklad používá `using` příkaz k vytvoření <xref:System.IO.StreamReader?displayProperty=nameWithType> a uvolnění objektu.  
  
[!code-csharp[Conceptual.Disposable#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using1.cs#1)]
[!code-vb[Conceptual.Disposable#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using1.vb#1)]  
  
Všimněte si, že i když <xref:System.IO.StreamReader> třída implementuje <xref:System.IDisposable> rozhraní, což znamená, že <xref:System.IO.StreamReader.Dispose%2A?displayProperty=nameWithType> používá nespravovaný prostředek, příklad není explicitně volat metodu. Když kompilátor jazyka C# nebo `using` Visual Basic narazí na příkaz, vydává zprostředkující jazyk (IL), který je ekvivalentní následující kód, který explicitně obsahuje `try/finally` blok.  
  
[!code-csharp[Conceptual.Disposable#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using3.cs#3)]
[!code-vb[Conceptual.Disposable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using3.vb#3)]  
  
Příkaz C# `using` také umožňuje získat více prostředků v jednom příkazu, který `using` je vnitřně ekvivalentní vnořené příkazy. Následující příklad inkonfikuje dva <xref:System.IO.StreamReader> objekty ke čtení obsahu dvou různých souborů.  
  
[!code-csharp[Conceptual.Disposable#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using4.cs#4)]

## <a name="tryfinally-block"></a>Testovací blok / bezpodmínečný blok

Namísto zabalení `try/finally` bloku `using` v příkazu, můžete `try/finally` provést blok přímo. Může se jednat o váš vlastní styl psaní kódu nebo tak můžete činit z jednoho z následujících důvodů:  
  
- Chcete-li `catch` zahrnout blok pro zpracování všech `try` výjimek vyzdvižených v bloku. V opačném případě jsou všechny `using` výjimky vyzdvižené příkazem neošetřené, stejně jako všechny výjimky vyzývané v `using` rámci bloku, pokud `try/catch` blok není k dispozici.  
  
- K vytvoření instance objektu, <xref:System.IDisposable> který implementuje, jehož obor není místní bloku, ve kterém je deklarován.  
  
Následující příklad je podobný předchozímu příkladu, `try/catch/finally` s tím rozdílem, že používá blok <xref:System.IO.StreamReader> k vytvoření instance, použití a <xref:System.IO.StreamReader> vyřazení objektu a ke zpracování všech výjimek vystrutekovaných konstruktorem a jeho <xref:System.IO.StreamReader.ReadToEnd%2A> metodou. Všimněte si, `finally` že kód v bloku <xref:System.IDisposable> kontroluje, `null` že objekt, <xref:System.IDisposable.Dispose%2A> který implementuje není před voláním metody. Pokud tak neučiníte, <xref:System.NullReferenceException> může dojít k výjimce za běhu.  
  
[!code-csharp[Conceptual.Disposable#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using5.cs#6)]
[!code-vb[Conceptual.Disposable#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using5.vb#6)]  
  
Tento základní vzor můžete sledovat, pokud se `try/finally` rozhodnete implementovat nebo musíte implementovat `using` blok, protože váš <xref:System.IDisposable.Dispose%2A> programovací jazyk nepodporuje příkaz, ale umožňuje přímé volání metody.
  
## <a name="see-also"></a>Viz také

- [Vymazání nespravovaných prostředků](../../../docs/standard/garbage-collection/unmanaged.md)
- [using – příkaz (Referenční dokumentace jazyka C#)](../../csharp/language-reference/keywords/using-statement.md)
- [Using – příkaz (Visual Basic)](../../visual-basic/language-reference/statements/using-statement.md)
