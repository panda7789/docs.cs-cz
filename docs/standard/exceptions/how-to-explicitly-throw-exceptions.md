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
ms.openlocfilehash: 4eeb70c10d71a7c96136039342bcdcc7bc8ece20
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-explicitly-throw-exceptions"></a>Postupy: explicitní generování výjimek

Můžete explicitně vyvolat výjimku pomocí `throw` příkaz. Můžete také vyvolat Zachycenou výjimku znovu s použitím `throw` příkaz. Je dobrým zvykem přidat informace o výjimku, která je znovu vyvolána při ladění poskytnout další informace.

Následující příklad kódu používá `try` / `catch` blok k zachycení možné <xref:System.IO.FileNotFoundException>. Následující `try` blok je `catch` blok, který zachytí <xref:System.IO.FileNotFoundException> a zapíše zprávu do konzoly, pokud nebyl nalezen datový soubor. Další je `throw` příkaz, který vyvolá novou <xref:System.IO.FileNotFoundException> a přidá textových informací k výjimce.

[!code-csharp[Exception.Throwing#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Exception.Throwing/CS/throw.cs#1)]
[!code-vb[Exception.Throwing#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Exception.Throwing/VB/throw.vb#1)]  

## <a name="see-also"></a>Viz také  
[Výjimky](index.md)
