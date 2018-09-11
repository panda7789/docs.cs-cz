---
title: 'Postupy: používání bloku Try-Catch k zachycování výjimek'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- exceptions, try/catch blocks
- try blocks
- try/catch blocks
- catch blocks
ms.assetid: a3ce6dfd-1f64-471b-8ad8-8cfaf406275d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 852df5cb3eeea2ee5fa44ddce2f97e9c4f8d8b5a
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2018
ms.locfileid: "44352372"
---
# <a name="how-to-use-the-trycatch-block-to-catch-exceptions"></a>Postup používání bloku try/catch k zachycování výjimek

Umístit na části kódu, který může vyvolat výjimky v `try` bloku a místo kód, který zpracovává výjimky v `catch` bloku. `catch` Blok je řada příkazů pomocí klíčového slova začínající `catch`následovaný typ výjimky a akce, jež mají být provedeny.

Následující příklad kódu používá `try` / `catch` bloku catch možnou výjimkou. `Main` Obsahuje metodu `try` blokovat s <xref:System.IO.StreamReader> volá příkaz, který otevře soubor dat `data.txt` a zapíše řetězec ze souboru. Následující `try` blok je `catch` blok, který zachytí jakoukoli výjimku, která je výsledkem `try` bloku.

 [!code-cpp[CatchException#3](../../../samples/snippets/cpp/VS_Snippets_CLR/CatchException/CPP/catchexception2.cpp#3)]
 [!code-csharp[CatchException#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CatchException/CS/catchexception2.cs#3)]
 [!code-vb[CatchException#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CatchException/VB/catchexception2.vb#3)]  

Modul common language runtime zachytí výjimky, které nejsou zachyceny v bloku catch. V závislosti na konfiguraci modulu runtime se zobrazí dialogové okno ladění, program se zastaví provádění a zobrazí se dialogové okno s informací o výjimce nebo chybu je tisknout do STDERR.

> [!NOTE] 
> Téměř libovolném řádku kódu může způsobit výjimku, zejména výjimky vyvolané modulem common language runtime, jako například <xref:System.OutOfMemoryException>. Většina aplikací nemusíte řešit tyto výjimky, ale byste měli vědět tuto možnost při zápisu knihoven a využívat další uživatelé. Návrhy toho, kdy k nastavení kódu v bloku Try, najdete v části [osvědčené postupy pro výjimky](best-practices-for-exceptions.md).

## <a name="see-also"></a>Viz také:

- [Výjimky](index.md)
