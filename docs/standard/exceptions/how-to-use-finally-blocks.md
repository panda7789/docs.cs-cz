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
ms.openlocfilehash: 213ab53c68a37ac0ba5f337a1d6fc32bfe6f8989
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43883676"
---
# <a name="how-to-use-finally-blocks"></a>Postup použití bloku finally.

Když dojde k výjimce, zastaví provádění a ovládací prvek dostane k obslužné rutině příslušné výjimky. To často znamená, že se přeskočí řádky kódu, který očekáváte, že má být proveden. Některé vyčištění prostředků, jako je například zavření souboru, je nutné provést i v případě, že dojde k výjimce. K tomuto účelu můžete použít `finally` bloku. A `finally` vždy provede blok, bez ohledu na to, zda je vyvolána výjimka.

Následující příklad kódu používá `try` / `catch` bloku catch <xref:System.ArgumentOutOfRangeException>. `Main` Metoda vytvoří dvě pole a pokusí se zkopírujte jeden na druhý. Vytvoří akci <xref:System.ArgumentOutOfRangeException> a bude chyba zapsána do konzoly. `finally` Blok se spustí bez ohledu na to výsledek akce kopírování.

[!code-cpp[CodeTryCatchFinallyExample#3](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeTryCatchFinallyExample/CPP/source2.cpp#3)]
[!code-csharp[CodeTryCatchFinallyExample#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeTryCatchFinallyExample/CS/source2.cs#3)]
[!code-vb[CodeTryCatchFinallyExample#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeTryCatchFinallyExample/VB/source2.vb#3)]  

## <a name="see-also"></a>Viz také:

- [Výjimky](index.md)
