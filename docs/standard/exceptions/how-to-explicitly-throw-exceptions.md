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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a71cefc0a6483dbbe6513a64d8111a07a2e5af42
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71696731"
---
# <a name="how-to-explicitly-throw-exceptions"></a>Postup explicitního vyvolání výjimek

Výjimku můžete explicitně vyvolat pomocí C# [`throw`](../../csharp/language-reference/keywords/throw.md) nebo příkazu Visual Basic [`Throw`](../../visual-basic/language-reference/statements/throw-statement.md) . Zachycenou výjimku můžete také vyvolat znovu pomocí příkazu `throw`. Je vhodné postupovat při kódování pro přidání informací do výjimky, která se znovu vyvolala k poskytnutí dalších informací při ladění.

Následující příklad kódu používá blok `try` @ no__t-1 @ no__t-2 k zachycení možné <xref:System.IO.FileNotFoundException>. Po bloku `try` je blok `catch`, který zachytává <xref:System.IO.FileNotFoundException> a zapisuje zprávu do konzoly, pokud datový soubor nebyl nalezen. Další příkaz je příkaz `throw`, který vyvolá novou <xref:System.IO.FileNotFoundException> a do výjimky přidá textové informace.

[!code-csharp[Exception.Throwing#1](~/samples/snippets/csharp/VS_Snippets_CLR/Exception.Throwing/CS/throw.cs#1)]
[!code-vb[Exception.Throwing#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/Exception.Throwing/VB/throw.vb#1)]  

## <a name="see-also"></a>Viz také:

- [Výjimky](index.md)
