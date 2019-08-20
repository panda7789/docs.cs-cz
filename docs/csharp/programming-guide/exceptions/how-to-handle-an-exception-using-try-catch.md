---
title: 'Postupy: Zpracování výjimky pomocí Průvodce Try-Catch- C# Programming'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- exception handling [C#], try/catch blocks
- exceptions [C#], try/catch blocks
- try/catch blocks [C#]
ms.assetid: ca8e3773-980e-4767-8633-7408540e9818
ms.openlocfilehash: 5378de09962055fe7d2e100484ad69662c803e0f
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590232"
---
# <a name="how-to-handle-an-exception-using-trycatch-c-programming-guide"></a>Postupy: Zpracování výjimky pomocí try/catch (C# Průvodce programováním)
Účelem bloku [try-catch](../../language-reference/keywords/try-catch.md) je zachycení a zpracování výjimky generované pracovním kódem. Některé výjimky lze zpracovat v `catch` bloku a problém je vyřešen, aniž by došlo k opakovanému vyvolání výjimky, ale častěji stačí pouze to, abyste se ujistili, že je vyvolána příslušná výjimka.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu <xref:System.IndexOutOfRangeException> není nejvhodnější výjimka: <xref:System.ArgumentOutOfRangeException> dává pro metodu větší smysl, protože `index` chyba je způsobena argumentem předaným volajícím.  
  
 [!code-csharp[csProgGuideExceptions#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#5)]  
  
## <a name="comments"></a>Komentáře  
 Kód, který způsobuje výjimku, je uzavřen v `try` bloku. Příkaz se přidá hned po zpracování `IndexOutOfRangeException`, pokud k němu dojde. `catch` `catch` Blok zpracovává`IndexOutOfRangeException` a namísto toho vyvolává vhodnější výjimku.`ArgumentOutOfRangeException` Aby bylo možné poskytnout volající co nejvíc informací, zvažte zadání původní výjimky jako <xref:System.Exception.InnerException%2A> nové výjimky. Vzhledem k <xref:System.Exception.InnerException%2A> tomu, že vlastnost je [jen pro čtení](../../language-reference/keywords/readonly.md), je nutné ji přiřadit v konstruktoru nové výjimky.  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Výjimky a jejich zpracování](./index.md)
- [Zpracování výjimek](./exception-handling.md)
