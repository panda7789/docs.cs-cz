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
ms.openlocfilehash: a1a8658999f08d295e76afc9df6ec8acd146abe2
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43863223"
---
# <a name="how-to-explicitly-throw-exceptions"></a>Jak explicitní generování výjimek

Můžete explicitně vyvolat výjimku pomocí `throw` příkazu. Můžete také vyvolá Zachycenou výjimku znovu pomocí `throw` příkazu. Je dobrým zvykem přidejte informace o výjimce, která je znovu vyvolána k poskytnutí dalších informací při ladění.

Následující příklad kódu používá `try` / `catch` bloku catch možný výskyt <xref:System.IO.FileNotFoundException>. Následující `try` blok je `catch` blok, který zachytává <xref:System.IO.FileNotFoundException> a zapíše zprávu do konzoly, pokud datový soubor nebyl nalezen. Další příkaz je `throw` příkaz, který vyvolá novou <xref:System.IO.FileNotFoundException> a přidá informace o textu k výjimce.

[!code-csharp[Exception.Throwing#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Exception.Throwing/CS/throw.cs#1)]
[!code-vb[Exception.Throwing#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Exception.Throwing/VB/throw.vb#1)]  

## <a name="see-also"></a>Viz také:

- [Výjimky](index.md)
