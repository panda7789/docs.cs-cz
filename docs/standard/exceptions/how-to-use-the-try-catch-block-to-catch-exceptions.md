---
title: "Postupy: zachycení výjimky pomocí bloku Try-Catch"
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
- try blocks
- try/catch blocks
- catch blocks
ms.assetid: a3ce6dfd-1f64-471b-8ad8-8cfaf406275d
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 192f762872b112ea261d22251175db6867229437
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-use-the-trycatch-block-to-catch-exceptions"></a>Jak zachytit výjimky pomocí bloku try/catch

Umístit na části kódu, který může vyvolat výjimky v `try` bloku a umístěte kód, který zpracovává výjimky v `catch` bloku. `catch` Blok je řada příkazů počínaje klíčové slovo `catch`, za nímž následují typ výjimky a akce, které mají být provedeny.

Následující příklad kódu používá `try` / `catch` blok k zachycení možné výjimky. `Main` Metoda obsahuje `try` blokovat s <xref:System.IO.StreamReader> příkaz, který otevře datový soubor s názvem `data.txt` a zapisuje řetězec ze souboru. Následující `try` blok je `catch` blok, který zachytí jakoukoli výjimku, která je výsledkem `try` bloku.

 [!code-cpp[CatchException#3](../../../samples/snippets/cpp/VS_Snippets_CLR/CatchException/CPP/catchexception2.cpp#3)]
 [!code-csharp[CatchException#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CatchException/CS/catchexception2.cs#3)]
 [!code-vb[CatchException#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CatchException/VB/catchexception2.vb#3)]  

Modul common language runtime zachytí výjimky, které nejsou zachytila bloku catch. V závislosti na konfiguraci modulu runtime zobrazí se dialogové okno ladění, nebo program zastaví, provádění a zobrazí se dialogové okno s informací o výjimce nebo chybu se vytiskne na STDERR.

> [!NOTE] 
> Téměř každý řádek kódu může způsobit výjimku, zejména výjimky, které jsou vyvolány common language runtime samostatně, jako například <xref:System.OutOfMemoryException>. Většina aplikací nemusí zabývat těmito výjimkami, ale byste měli vědět tuto možnost při zápisu knihoven pro použití jinými uživateli. Návrhy, když chcete nastavit kód do bloku Try, najdete v části [osvědčené postupy pro výjimky](best-practices-for-exceptions.md).

## <a name="see-also"></a>Viz také  
[Výjimky](index.md)
