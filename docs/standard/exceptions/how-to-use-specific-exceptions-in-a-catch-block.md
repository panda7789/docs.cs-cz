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
ms.openlocfilehash: 424db46c879974a9859637f9a2a5dfcd4494a3c5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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
