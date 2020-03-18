---
title: 'Postupy: Explicitní generování výjimek'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- exceptions, try/catch blocks
- FileNotFoundException class
- try/catch blocks
- exceptions, throwing
- implicitly throwing exceptions
ms.assetid: 72bdd157-caa9-4478-9ee3-cb4500b84528
ms.openlocfilehash: 750da20b8c1c40901cc363ac0eff8af888821ce9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75708859"
---
# <a name="how-to-explicitly-throw-exceptions"></a>Jak explicitně vyvolat výjimky

Můžete explicitně vyvolat výjimku [`throw`](../../csharp/language-reference/keywords/throw.md) pomocí C# [`Throw`](../../visual-basic/language-reference/statements/throw-statement.md) nebo Visual Basic prohlášení. Můžete také vyvolat zachycené výjimky znovu pomocí příkazu. `throw` Je vhodné kódování praxe přidat informace o výjimce, která je znovu vyvolána poskytnout další informace při ladění.

Následující příklad kódu `try` / `catch` používá blok zachytit <xref:System.IO.FileNotFoundException>možné . Následující `try` blok je `catch` blok, <xref:System.IO.FileNotFoundException> který zachytí a zapíše zprávu do konzoly, pokud datový soubor nebyl nalezen. Dalším příkazem `throw` je příkaz, který <xref:System.IO.FileNotFoundException> vyvolá nový a přidá textové informace k výjimce.

[!code-csharp[Exception.Throwing#1](~/samples/snippets/csharp/VS_Snippets_CLR/Exception.Throwing/CS/throw.cs#1)]
[!code-vb[Exception.Throwing#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/Exception.Throwing/VB/throw.vb#1)]  

## <a name="see-also"></a>Viz také

- [Výjimky](index.md)
