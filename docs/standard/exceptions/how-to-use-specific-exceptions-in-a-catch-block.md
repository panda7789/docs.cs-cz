---
title: 'Postupy: Používání specifických výjimek v bloku Catch'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- exceptions, try/catch blocks
- try/catch blocks
- catch blocks
ms.assetid: 12af9ff3-8587-4f31-90cf-6c2244e0fdae
ms.openlocfilehash: 48b450e579263876725f96e0adfc4c16aac1d869
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160154"
---
# <a name="how-to-use-specific-exceptions-in-a-catch-block"></a>Použití konkrétních výjimek v bloku catch

Obecně je vhodné programovací praxe zachytit konkrétní typ výjimky spíše `catch` než použít základní příkaz.

Když dojde k výjimce, je předán do zásobníku a každý blok catch je dána možnost jej zpracovat. Pořadí catch příkazy je důležité. Umístit catch bloky cílené na konkrétní výjimky před obecný blok catch výjimky nebo kompilátor může vydat chybu. Správný blok catch je určen porovnáním typu výjimky s názvem výjimky určené v bloku catch. Pokud neexistuje žádný konkrétní blok catch, výjimka je zachycena obecným blokem catch, pokud existuje.

Následující příklad kódu `try` / `catch` používá blok <xref:System.InvalidCastException>k zachycení . Ukázka vytvoří třídu volanou `Employee` s`Emlevel`jedinou vlastností, úrovní zaměstnance ( ). Metoda , `PromoteEmployee`přebírá objekt a narůstá úroveň zaměstnance. Dojde <xref:System.InvalidCastException> k při <xref:System.DateTime> instanci `PromoteEmployee` je předán a metoda.

[!code-cpp[CatchException#2](../../../samples/snippets/cpp/VS_Snippets_CLR/CatchException/CPP/catchexception1.cpp#2)]
[!code-csharp[CatchException#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CatchException/CS/catchexception1.cs#2)]
[!code-vb[CatchException#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CatchException/VB/catchexception1.vb#2)]

## <a name="see-also"></a>Viz také

- [Výjimky](index.md)
