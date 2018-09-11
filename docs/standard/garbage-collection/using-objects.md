---
title: Použití objektů implementujících rozhraní IDisposable
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 70955d496f5cf9e3bf44b9bc03a054d1c96efe98
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44260016"
---
# <a name="using-objects-that-implement-idisposable"></a>Použití objektů implementujících rozhraní IDisposable

Modul common language runtime systému uvolňování paměti uvolní paměť používanou spravovanými objekty, ale implementace typy, které používají nespravované prostředky <xref:System.IDisposable> rozhraní umožňující je paměť přidělená pro tyto nespravované prostředky, které mají být získány zpět. Jakmile ukončíte používání objektu, který implementuje <xref:System.IDisposable>, měli byste zavolat objekt <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementace. Toto lze provést jedním ze dvou způsobů:  
  
* V jazyce C# `using` příkazu nebo Visual Basic `Using` příkazu.  
  
* Implementací `try/finally` bloku.  

## <a name="the-using-statement"></a>Pomocí příkazu using

`using` Příkaz v jazyce C# a `Using` v sadě Visual Studio zjednodušuje kód, který je třeba zapsat k vytvoření a vyčištění objektu. `using` Příkaz získá jeden nebo více zdrojů, provede zadané příkazy a automaticky uvolní objekt. Ale `using` příkazu je platný pouze pro objekty, které se používají v rámci oboru metody, ve kterém jsou vytvořeny.  
  
V následujícím příkladu `using` příkazu k vytvoření a vydání <xref:System.IO.StreamReader?displayProperty=nameWithType> objektu.  
  
[!code-csharp[Conceptual.Disposable#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using1.cs#1)]
[!code-vb[Conceptual.Disposable#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using1.vb#1)]  
  
Všimněte si, že i když <xref:System.IO.StreamReader> implementuje třída <xref:System.IDisposable> rozhraní, což znamená, že používá nespravovaný prostředek, příklad nevolá explicitně <xref:System.IO.StreamReader.Dispose%2A?displayProperty=nameWithType> metody. Když kompilátor jazyka C# nebo Visual Basic narazí `using` prohlášení, vysílá zprostředkující jazyk (IL), který je ekvivalentní následujícímu kódu, který explicitně obsahuje `try/finally` bloku.  
  
[!code-csharp[Conceptual.Disposable#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using3.cs#3)]
[!code-vb[Conceptual.Disposable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using3.vb#3)]  
  
C# `using` příkaz také umožňuje získat více zdrojů v jediném příkazu, který je interním ekvivalentem vnořených `using` příkazy. Následující příklad vytvoří dvě <xref:System.IO.StreamReader> objekty ke čtení obsahu dvou různých souborech.  
  
[!code-csharp[Conceptual.Disposable#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using4.cs#4)]

## <a name="tryfinally-block"></a>Testovací blok / bezpodmínečný blok

Namísto obtékání `try/finally` blokovat `using` příkazu, můžete se rozhodnout k implementaci `try/finally` blokovat přímo. Může se jednat o váš vlastní styl psaní kódu nebo tak můžete činit z jednoho z následujících důvodů:  
  
* Zahrnout `catch` ke zpracování jakýchkoli výjimek v bloku `try` bloku. V opačném případě zůstanou veškeré výjimky vyvolané `using` nezpracované, stejně jako výjimky vyvolané v rámci `using` blokovat, pokud `try/catch` bloku není k dispozici.  
  
* Chcete-li vytvořit instanci objektu, který implementuje <xref:System.IDisposable> jehož rozsah není místním vyjádřením bloku, ve kterém je deklarována.  
  
Následující příklad je podobné jako v předchozím příkladu, s tím rozdílem, že používá `try/catch/finally` blok k vytváření instancí, použití a vyřadit <xref:System.IO.StreamReader> objektu a na zpracování jakékoli výjimky vyvolané <xref:System.IO.StreamReader> konstruktoru a jeho <xref:System.IO.StreamReader.ReadToEnd%2A> – metoda. Všimněte si, že kód v `finally` bloku kontroluje, zda objekt, který implementuje <xref:System.IDisposable> není `null` před voláním <xref:System.IDisposable.Dispose%2A> metody. K tomu může dojít <xref:System.NullReferenceException> výjimka za běhu.  
  
[!code-csharp[Conceptual.Disposable#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using5.cs#6)]
[!code-vb[Conceptual.Disposable#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using5.vb#6)]  
  
Tento základní princip lze použít v případě, že se rozhodnete implementovat nebo musí implementovat `try/finally` blokovat, protože váš programovací jazyk nepodporuje `using` příkaz ale umožňuje přímá volání <xref:System.IDisposable.Dispose%2A> metoda. 
  
## <a name="see-also"></a>Viz také:

* [Vymazání nespravovaných prostředků](../../../docs/standard/garbage-collection/unmanaged.md)   
* [Using – příkaz (referenční dokumentace jazyka C#)](~/docs/csharp/language-reference/keywords/using-statement.md)   
* [Using – příkaz (Visual Basic)](~/docs/visual-basic/language-reference/statements/using-statement.md)
