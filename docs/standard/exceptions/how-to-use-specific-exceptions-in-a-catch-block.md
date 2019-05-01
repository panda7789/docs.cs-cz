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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3da35dae374018f0695f79022e83ad397e98cb88
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61970882"
---
# <a name="how-to-use-specific-exceptions-in-a-catch-block"></a>Postup používání specifických výjimek v bloku catch

Obecně je programování je dobrým zvykem catch konkrétní typ výjimky, a nemuseli používat základní `catch` příkazu.

Když dojde k výjimce, jsou předány do zásobníku a každý blok catch dostane příležitost, aby to zvládnul. Je důležité pořadí příkazů catch. Umístit bloky catch cílené na specifické výjimky než blok catch výjimky nebo kompilátor zahlásí chybu. Určuje blok catch správné odpovídající typ výjimky k názvu na výjimku zadanou v bloku catch. Pokud neexistuje žádný konkrétní blok catch, výjimku zachycuje se prostřednictvím obecný zachytávací blok, pokud existuje.

Následující příklad kódu používá `try` / `catch` bloku catch <xref:System.InvalidCastException>. Ukázka vytvoří třídu s názvem `Employee` s jedinou vlastností, úroveň zaměstnance (`Emlevel`). Je metoda `PromoteEmployee`, přebírá objekt a zvýší úroveň zaměstnance. <xref:System.InvalidCastException> Dojde k při <xref:System.DateTime> instance předána `PromoteEmployee` metody.

[!code-cpp[CatchException#2](../../../samples/snippets/cpp/VS_Snippets_CLR/CatchException/CPP/catchexception1.cpp#2)]
[!code-csharp[CatchException#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CatchException/CS/catchexception1.cs#2)]
[!code-vb[CatchException#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CatchException/VB/catchexception1.vb#2)] 

## <a name="see-also"></a>Viz také:

- [Výjimky](index.md)
