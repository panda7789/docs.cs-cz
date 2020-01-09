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
ms.openlocfilehash: 6f0956c6418d894a5768463861151f86a1948850
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75708578"
---
# <a name="how-to-use-specific-exceptions-in-a-catch-block"></a>Používání specifických výjimek v bloku catch

Obecně je dobrým programovacím postupem zachytit konkrétní typ výjimky namísto použití základního příkazu `catch`.

Pokud dojde k výjimce, je předán zásobníku a každý blok catch je dána příležitostí k jejímu zpracování. Pořadí příkazů catch je důležité. Umístěte bloky catch cílené na konkrétní výjimky před obecným blokem catch výjimky nebo kompilátor může vystavit chybu. Správný blok catch je určen porovnáním typu výjimky s názvem výjimky zadané v bloku catch. Pokud není k dispozici žádný konkrétní blok catch, je výjimka zachycena obecným blokem catch, pokud nějaká existuje.

Následující příklad kódu používá `try`/`catch` blok k zachycení <xref:System.InvalidCastException>. Ukázka vytvoří třídu s názvem `Employee` s jedinou vlastností, úrovní zaměstnance (`Emlevel`). Metoda, `PromoteEmployee`, přebírá objekt a zvyšuje úroveň zaměstnance. K <xref:System.InvalidCastException> dojde, když je instance <xref:System.DateTime> předána metodě `PromoteEmployee`.

[!code-cpp[CatchException#2](../../../samples/snippets/cpp/VS_Snippets_CLR/CatchException/CPP/catchexception1.cpp#2)]
[!code-csharp[CatchException#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CatchException/CS/catchexception1.cs#2)]
[!code-vb[CatchException#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CatchException/VB/catchexception1.vb#2)] 

## <a name="see-also"></a>Viz také:

- [Výjimky](index.md)
