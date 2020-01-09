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
ms.openlocfilehash: 44fbb53437c4c8f19a424227a167e2e268b77057
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75708829"
---
# <a name="how-to-use-finally-blocks"></a>Jak používat bloky finally

Pokud dojde k výjimce, spuštění se zastaví a ovládací prvek se přestává příslušné obslužné rutině výjimky. To často znamená, že řádky kódu, které očekáváte, jsou vynechány. Některé vyčištění prostředků, jako je například zavření souboru, je nutné provést i v případě, že je vyvolána výjimka. K tomu můžete použít blok `finally`. `finally` blok se vždy spustí bez ohledu na to, zda je vyvolána výjimka.

Následující příklad kódu používá `try`/`catch` blok k zachycení <xref:System.ArgumentOutOfRangeException>. Metoda `Main` vytvoří dvě pole a pokusí se je zkopírovat do druhé. Akce vygeneruje <xref:System.ArgumentOutOfRangeException> a chyba se zapíše do konzoly. `finally` blok se provede bez ohledu na výsledek akce kopírování.

[!code-cpp[CodeTryCatchFinallyExample#3](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeTryCatchFinallyExample/CPP/source2.cpp#3)]
[!code-csharp[CodeTryCatchFinallyExample#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeTryCatchFinallyExample/CS/source2.cs#3)]
[!code-vb[CodeTryCatchFinallyExample#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeTryCatchFinallyExample/VB/source2.vb#3)]  

## <a name="see-also"></a>Viz také:

- [Výjimky](index.md)
