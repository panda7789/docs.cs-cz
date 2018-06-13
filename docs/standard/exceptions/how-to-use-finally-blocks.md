---
title: 'Postupy: Používání bloků Finally'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- exceptions, try/catch blocks
- exceptions, finally blocks
- try/catch blocks
- finally blocks
- ArgumentOutOfRangeException class
ms.assetid: 4b9c0137-04af-4468-91d1-b9014df8ddd2
author: mairaw
ms.author: mairaw
ms.openlocfilehash: dff1083256e24a35b7238ee5e8af6cb5743bc0ea
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33571518"
---
# <a name="how-to-use-finally-blocks"></a>Postup používání bloků finally

Když dojde k výjimce, provádění zastaví a řízení dostane do obslužné rutiny příslušné výjimky. Často to znamená, že se vynechá řádků kódu, které chcete provést. Některé vyčištění prostředků, jako je například zavření souboru, je potřeba udělat i v případě, že je vyvolána výjimka. Chcete-li to provést, můžete použít `finally` bloku. A `finally` vždy provede bloku, bez ohledu na to, jestli je vyvolána výjimka.

Následující příklad kódu používá `try` / `catch` bloku k zachycení <xref:System.ArgumentOutOfRangeException>. `Main` Metoda vytvoří dvě pole a pokusí se zkopírovat jeden na druhý. Vytvoří akci <xref:System.ArgumentOutOfRangeException> a bude chyba zapsána do konzoly. `finally` Bloku spustí bez ohledu na to výsledek akce kopírování.

[!code-cpp[CodeTryCatchFinallyExample#3](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeTryCatchFinallyExample/CPP/source2.cpp#3)]
[!code-csharp[CodeTryCatchFinallyExample#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeTryCatchFinallyExample/CS/source2.cs#3)]
[!code-vb[CodeTryCatchFinallyExample#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeTryCatchFinallyExample/VB/source2.vb#3)]  

## <a name="see-also"></a>Viz také  
[Výjimky](index.md)   
