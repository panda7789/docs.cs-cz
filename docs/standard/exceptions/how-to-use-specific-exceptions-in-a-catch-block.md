---
title: "Postupy: Používání specifických výjimek v bloku Catch"
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
- try/catch blocks
- catch blocks
ms.assetid: 12af9ff3-8587-4f31-90cf-6c2244e0fdae
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: ebc59035140ff0464cd959129fdf48a4e9a269f5
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-use-specific-exceptions-in-a-catch-block"></a>Postup používání specifických výjimek v bloku catch

Obecně platí, je dobrým zvykem zachytit specifický typ výjimky, místo použití základní programování `catch` příkaz.

Když dojde k výjimce, je předán do zásobníku a každý blok catch je zadána možnost se nezdařilo. Je důležité pořadí příkazů catch. Umístit bloky catch cílená na konkrétní výjimky před obecné výjimce bloku catch nebo kompilátor může vydat k chybě. Správný blok catch je určen podle odpovídající typ výjimky k názvu zadaná v bloku catch výjimky. Pokud není žádný konkrétní blok catch, je výjimka zachycena pomocí bloku catch Obecné, pokud existuje.

Následující příklad kódu používá `try` / `catch` bloku k zachycení <xref:System.InvalidCastException>. Ukázka vytvoří třídu s názvem `Employee` s jedinou vlastností, úroveň zaměstnance (`Emlevel`). A metoda `PromoteEmployee`, přebírá objekt a zvýší úroveň zaměstnance. <xref:System.InvalidCastException> Dojde při <xref:System.DateTime> instance předána `PromoteEmployee` metoda.

[!code-cpp[CatchException#2](../../../samples/snippets/cpp/VS_Snippets_CLR/CatchException/CPP/catchexception1.cpp#2)]
[!code-csharp[CatchException#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CatchException/CS/catchexception1.cs#2)]
[!code-vb[CatchException#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CatchException/VB/catchexception1.vb#2)] 

## <a name="see-also"></a>Viz také  
[Výjimky](index.md)
