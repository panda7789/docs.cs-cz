---
title: Postup zpracování výjimky pomocí Průvodce programováním try-catch-C#
description: Naučte se, jak zpracovat výjimku pomocí bloku try-catch. Podívejte se na příklad kódu a zobrazte další dostupné prostředky.
ms.date: 07/20/2015
helpviewer_keywords:
- exception handling [C#], try/catch blocks
- exceptions [C#], try/catch blocks
- try/catch blocks [C#]
ms.assetid: ca8e3773-980e-4767-8633-7408540e9818
ms.openlocfilehash: 357aebe042bc5b6e761b3c1bad258021441de22c
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301993"
---
# <a name="how-to-handle-an-exception-using-trycatch-c-programming-guide"></a>Postup zpracování výjimky pomocí try/catch (Průvodce programováním v C#)
Účelem bloku [try-catch](../../language-reference/keywords/try-catch.md) je zachycení a zpracování výjimky generované pracovním kódem. Některé výjimky lze zpracovat v `catch` bloku a problém je vyřešen, aniž by došlo k opakovanému vyvolání výjimky, ale častěji stačí pouze to, abyste se ujistili, že je vyvolána příslušná výjimka.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu není <xref:System.IndexOutOfRangeException> nejvhodnější výjimka: <xref:System.ArgumentOutOfRangeException> dává pro metodu větší smysl, protože chyba je způsobena `index` argumentem předaným volajícím.  
  
 [!code-csharp[csProgGuideExceptions#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#5)]  
  
## <a name="comments"></a>Komentáře  
 Kód, který způsobuje výjimku, je uzavřen v `try` bloku. `catch`Příkaz se přidá hned po zpracování `IndexOutOfRangeException` , pokud k němu dojde. `catch`Blok zpracovává `IndexOutOfRangeException` a `ArgumentOutOfRangeException` namísto toho vyvolává vhodnější výjimku. Aby bylo možné poskytnout volající co nejvíc informací, zvažte zadání původní výjimky jako <xref:System.Exception.InnerException%2A> nové výjimky. Vzhledem k tomu <xref:System.Exception.InnerException%2A> , že je vlastnost [jen pro čtení](../../properties.md#read-only), je nutné ji přiřadit v konstruktoru nové výjimky.  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v C#](../index.md)
- [Výjimky a zpracování výjimek](./index.md)
- [Zpracování výjimek](./exception-handling.md)
