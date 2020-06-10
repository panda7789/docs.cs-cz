---
title: 'Postupy: Explicitní generování výjimek'
description: Zjistěte, jak v rozhraní .NET vyvolat výjimku explicitně pomocí příkazu throw jazyka C# nebo příkazu Visual Basic throw.
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
ms.openlocfilehash: 2dd939f9edd58ba91ea74df5d6930087849f0560
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/10/2020
ms.locfileid: "84662781"
---
# <a name="how-to-explicitly-throw-exceptions"></a>Postup explicitního vyvolání výjimek

Výjimku lze explicitně vyvolat pomocí jazyka C# [`throw`](../../csharp/language-reference/keywords/throw.md) nebo [`Throw`](../../visual-basic/language-reference/statements/throw-statement.md) příkazu Visual Basic. Zachycenou výjimku můžete také vyvolat znovu pomocí `throw` příkazu. Je vhodné postupovat při kódování pro přidání informací do výjimky, která se znovu vyvolala k poskytnutí dalších informací při ladění.

Následující příklad kódu používá `try` / `catch` blok k zachycení možného <xref:System.IO.FileNotFoundException> . Po `try` bloku je `catch` blok, který zachytává <xref:System.IO.FileNotFoundException> a zapisuje zprávu do konzoly, pokud datový soubor nebyl nalezen. Další příkaz je `throw` příkaz, který vyvolá novou <xref:System.IO.FileNotFoundException> a přidá do výjimky textové informace.

[!code-csharp[Exception.Throwing#1](~/samples/snippets/csharp/VS_Snippets_CLR/Exception.Throwing/CS/throw.cs#1)]
[!code-vb[Exception.Throwing#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/Exception.Throwing/VB/throw.vb#1)]  

## <a name="see-also"></a>Viz také

- [Výjimky](index.md)
