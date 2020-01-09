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
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75708859"
---
# <a name="how-to-explicitly-throw-exceptions"></a>Postup explicitního vyvolání výjimek

Výjimku lze explicitně vyvolat pomocí C# [`throw`](../../csharp/language-reference/keywords/throw.md) nebo příkazu Visual Basic [`Throw`](../../visual-basic/language-reference/statements/throw-statement.md) . Zachycenou výjimku můžete také vyvolat znovu pomocí příkazu `throw`. Je vhodné postupovat při kódování pro přidání informací do výjimky, která se znovu vyvolala k poskytnutí dalších informací při ladění.

Následující příklad kódu používá `try`/`catch` blok k zachycení možného <xref:System.IO.FileNotFoundException>. Následující blok `try` je `catch` blok, který zachytává <xref:System.IO.FileNotFoundException> a zapisuje zprávu do konzoly, pokud datový soubor nebyl nalezen. Další příkaz je příkaz `throw`, který vyvolá nový <xref:System.IO.FileNotFoundException> a přidá do výjimky textové informace.

[!code-csharp[Exception.Throwing#1](~/samples/snippets/csharp/VS_Snippets_CLR/Exception.Throwing/CS/throw.cs#1)]
[!code-vb[Exception.Throwing#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/Exception.Throwing/VB/throw.vb#1)]  

## <a name="see-also"></a>Viz také:

- [Výjimky](index.md)
