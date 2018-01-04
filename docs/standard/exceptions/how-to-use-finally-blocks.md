---
title: "Postupy: Používání bloků Finally"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 325be4836d661369326fbe3ea1f8b252bf251f3c
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-use-finally-blocks"></a>Postup používání bloků finally

Když dojde k výjimce, provádění zastaví a řízení dostane do obslužné rutiny příslušné výjimky. Často to znamená, že se vynechá řádků kódu, které chcete provést. Některé vyčištění prostředků, jako je například zavření souboru, je potřeba udělat i v případě, že je vyvolána výjimka. Chcete-li to provést, můžete použít `finally` bloku. A `finally` vždy provede bloku, bez ohledu na to, jestli je vyvolána výjimka.

Následující příklad kódu používá `try` / `catch` bloku k zachycení <xref:System.ArgumentOutOfRangeException>. `Main` Metoda vytvoří dvě pole a pokusí se zkopírovat jeden na druhý. Vytvoří akci <xref:System.ArgumentOutOfRangeException> a bude chyba zapsána do konzoly. `finally` Bloku spustí bez ohledu na to výsledek akce kopírování.

[!code-cpp[CodeTryCatchFinallyExample#3](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeTryCatchFinallyExample/CPP/source2.cpp#3)]
[!code-csharp[CodeTryCatchFinallyExample#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeTryCatchFinallyExample/CS/source2.cs#3)]
[!code-vb[CodeTryCatchFinallyExample#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeTryCatchFinallyExample/VB/source2.vb#3)]  

## <a name="see-also"></a>Viz také  
[Výjimky](index.md)   
