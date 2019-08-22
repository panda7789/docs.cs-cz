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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 074b97f29946390170abe3c40d71d2ee2cb214ce
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666481"
---
# <a name="using-objects-that-implement-idisposable"></a>Použití objektů, které implementují IDisposable

Systém uvolňování paměti modulu CLR (Common Language Runtime) uvolňuje paměť využívané spravovanými objekty, ale typy, které <xref:System.IDisposable> používají nespravované prostředky, implementují rozhraní, aby bylo možné uvolnit paměť přidělené těmto nespravovaným prostředkům. Po dokončení použití objektu, který implementuje <xref:System.IDisposable>, byste měli zavolat <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementaci objektu. Toto lze provést jedním ze dvou způsobů:  
  
* C# Pomocí příkazu nebo příkazu Visual Basic `Using` `using` .  
  
* Implementací `try/finally` bloku.  

## <a name="the-using-statement"></a>Pomocí příkazu using

Příkaz v C# a`Using` příkaz v Visual Basic zjednoduší kód, který je nutné zapsat pro vytvoření a vyčištění objektu. `using` `using` Příkaz získá jeden nebo více prostředků, spustí příkazy, které zadáte, a automaticky odstraní objekt. `using` Příkaz je však vhodný pouze pro objekty, které jsou používány v rámci rozsahu metody, ve které jsou vytvořeny.  
  
Následující příklad používá `using` příkaz k vytvoření a <xref:System.IO.StreamReader?displayProperty=nameWithType> uvolnění objektu.  
  
[!code-csharp[Conceptual.Disposable#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using1.cs#1)]
[!code-vb[Conceptual.Disposable#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using1.vb#1)]  
  
Všimněte si, že <xref:System.IO.StreamReader> i když třída <xref:System.IDisposable> implementuje rozhraní, což znamená, že používá nespravovaný prostředek, <xref:System.IO.StreamReader.Dispose%2A?displayProperty=nameWithType> příklad explicitně nevolá metodu. Když kompilátor C# nebo Visual Basic nalezne `using` příkaz, vygeneruje převodní jazyk (IL), který je ekvivalentní následujícímu kódu `try/finally` , který explicitně obsahuje blok.  
  
[!code-csharp[Conceptual.Disposable#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using3.cs#3)]
[!code-vb[Conceptual.Disposable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using3.vb#3)]  
  
Příkaz také umožňuje získat více prostředků v jednom příkazu, který je interně ekvivalentní vnořeným `using` příkazům. C# `using` Následující příklad vytvoří instanci dvou <xref:System.IO.StreamReader> objektů pro čtení obsahu dvou různých souborů.  
  
[!code-csharp[Conceptual.Disposable#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using4.cs#4)]

## <a name="tryfinally-block"></a>Testovací blok / bezpodmínečný blok

Místo zabalení `try/finally` bloku `using` v příkazu můžete zvolit přímé implementace `try/finally` bloku. Může se jednat o váš vlastní styl psaní kódu nebo tak můžete činit z jednoho z následujících důvodů:  
  
* Chcete-li `catch` zahrnout blok pro zpracování jakýchkoli výjimek vyvolaných `try` v bloku. V opačném případě jakékoli výjimky vyvolané `using` příkazem nejsou ošetřeny, stejně jako jakékoli výjimky vyvolané `using` v rámci bloku, `try/catch` Pokud není přítomen blok.  
  
* Pro vytvoření instance objektu, který implementuje <xref:System.IDisposable> , jehož obor není místní pro blok, ve kterém je deklarována.  
  
Následující příklad je `try/catch/finally` podobný předchozímu příkladu s tím rozdílem, že používá blok pro vytvoření instance, použití a uvolnění <xref:System.IO.StreamReader> objektu a ke zpracování <xref:System.IO.StreamReader> jakýchkoli výjimek vyvolaných konstruktorem a jeho <xref:System.IO.StreamReader.ReadToEnd%2A> metodou. Všimněte si, že kód v `finally` bloku kontroluje, zda objekt, který <xref:System.IDisposable> implementuje `null` , <xref:System.IDisposable.Dispose%2A> není před voláním metody. V takovém případě může dojít k <xref:System.NullReferenceException> výjimce za běhu.  
  
[!code-csharp[Conceptual.Disposable#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using5.cs#6)]
[!code-vb[Conceptual.Disposable#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using5.vb#6)]  
  
Můžete postupovat podle tohoto základního vzoru, pokud se rozhodnete implementovat nebo musíte `try/finally` implementovat blok, protože váš programovací jazyk `using` nepodporuje příkaz, ale <xref:System.IDisposable.Dispose%2A> umožňuje přímé volání metody. 
  
## <a name="see-also"></a>Viz také:

- [Vymazání nespravovaných prostředků](../../../docs/standard/garbage-collection/unmanaged.md)
- [using – příkazC# (Referenční dokumentace)](../../csharp/language-reference/keywords/using-statement.md)
- [Using – příkaz (Visual Basic)](../../visual-basic/language-reference/statements/using-statement.md)
