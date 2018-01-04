---
title: "Použití objektů implementujících rozhraní IDisposable"
ms.custom: 
ms.date: 04/07/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Dispose method
- try/finally block
- garbage collection, encapsulating resources
ms.assetid: 81b2cdb5-c91a-4a31-9c83-eadc52da5cf0
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 47ff64cab098425c5369773f792d586b65658d0f
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="using-objects-that-implement-idisposable"></a>Použití objektů implementujících rozhraní IDisposable

Modul common language runtime systém uvolňování paměti získá množství paměti používané spravovaných objektů, ale implementace typů, které používají nespravované prostředky <xref:System.IDisposable> rozhraní umožňující je paměť přidělená pro tyto nespravované prostředky, které mají být získány zpět. Po dokončení pomocí objektu, který implementuje <xref:System.IDisposable>, by měly volat objektu <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementace. Toto lze provést jedním ze dvou způsobů:  
  
* Pomocí jazyka C# `using` příkaz nebo Visual Basic `Using` příkaz.  
  
* Implementací `try/finally` bloku.  

## <a name="the-using-statement"></a>Pomocí příkazu using

`using` Příkaz v jazyce C# a `Using` kód, který musí zapsat do vytvoření a vyčištění objekt zjednodušení příkaz v jazyce Visual Basic. `using` Příkaz získá jeden nebo více prostředků, provede příkazy, které můžete zadat a automaticky uvolní objekt. Ale `using` příkaz je vhodné pouze pro objekty, které se používají v rámci oboru metody, ve kterém se vytvářejí.  
  
Následující příklad používá `using` příkazu k vytvoření a vydání <xref:System.IO.StreamReader?displayProperty=nameWithType> objektu.  
  
[!code-csharp[Conceptual.Disposable#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using1.cs#1)]
[!code-vb[Conceptual.Disposable#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using1.vb#1)]  
  
Všimněte si, že i když <xref:System.IO.StreamReader> třída implementuje <xref:System.IDisposable> rozhraní, které označuje, že používá nespravovaný prostředek v příkladu není explicitně volání <xref:System.IO.StreamReader.Dispose%2A?displayProperty=nameWithType> metoda. Když kompilátor jazyka C# nebo Visual Basic narazí `using` příkaz vysílá převodní jazyk (IL), který je ekvivalentní pro následující kód, který obsahuje explicitně `try/finally` bloku.  
  
[!code-csharp[Conceptual.Disposable#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using3.cs#3)]
[!code-vb[Conceptual.Disposable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using3.vb#3)]  
  
C# `using` příkaz také umožňuje získat víc zdrojů v jediném příkazu, která je ekvivalentní interně vnořené `using` příkazy. Následující příklad vytvoří dvě instance <xref:System.IO.StreamReader> objekty, které se přečíst obsah dva různé soubory.  
  
[!code-csharp[Conceptual.Disposable#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using4.cs#4)]

## <a name="tryfinally-block"></a>Testovací blok / bezpodmínečný blok

Místo zabalení `try/finally` blokovat `using` prohlášení, můžete se rozhodnout k implementaci `try/finally` blokovat přímo. Může se jednat o váš vlastní styl psaní kódu nebo tak můžete činit z jednoho z následujících důvodů:  
  
* Zahrnout `catch` bloku pro zpracování všech výjimek vyvolaných v `try` bloku. Jinak, jakékoli výjimky vyvolané `using` příkaz nejsou zpracovány, jako jsou všechny výjimky vydané v rámci `using` blokovat Pokud `try/catch` blok není přítomen.  
  
* K vytvoření instance objektu, který implementuje <xref:System.IDisposable> jehož obor není místní vzhledem k bloku, ve kterém je deklarovaná.  
  
V následujícím příkladu je podobně jako v předchozím příkladu s tím rozdílem, že používá `try/catch/finally` blok k vytváření instancí, použití a odstranění <xref:System.IO.StreamReader> objekt a ke zpracování jakékoli výjimky vyvolané <xref:System.IO.StreamReader> konstruktor a jeho <xref:System.IO.StreamReader.ReadToEnd%2A> metoda. Všimněte si, že kód `finally` bloku kontroluje, zda objekt, který implementuje <xref:System.IDisposable> není `null` zavolá <xref:System.IDisposable.Dispose%2A> metoda. K tomu může dojít <xref:System.NullReferenceException> výjimky za běhu.  
  
[!code-csharp[Conceptual.Disposable#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using5.cs#6)]
[!code-vb[Conceptual.Disposable#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using5.vb#6)]  
  
Tento základní vzor můžete provést, pokud se rozhodnete implementovat nebo musí implementovat `try/finally` blokovat, protože nepodporuje programovacího jazyka `using` příkaz ale umožňuje přímé volání <xref:System.IDisposable.Dispose%2A> metoda. 
  
## <a name="see-also"></a>Viz také

[Vymazání nespravovaných prostředků](../../../docs/standard/garbage-collection/unmanaged.md)   
[Using – příkaz (referenční dokumentace jazyka C#)](~/docs/csharp/language-reference/keywords/using-statement.md)   
[Using – příkaz (Visual Basic)](~/docs/visual-basic/language-reference/statements/using-statement.md)
