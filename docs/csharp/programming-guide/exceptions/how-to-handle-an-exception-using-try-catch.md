---
title: 'Postupy: zpracování výjimky pomocí try-try catch (C# Průvodce programováním)'
ms.date: 07/20/2015
helpviewer_keywords:
- exception handling [C#], try/catch blocks
- exceptions [C#], try/catch blocks
- try/catch blocks [C#]
ms.assetid: ca8e3773-980e-4767-8633-7408540e9818
ms.openlocfilehash: b67a3d7b6d2e10519363a273b7dd1d8b61317d1c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33338068"
---
# <a name="how-to-handle-an-exception-using-trycatch-c-programming-guide"></a>Postupy: Zpracování výjimky pomocí bloku try/catch (Průvodce programováním v C#)
Účel [try-catch –](../../../csharp/language-reference/keywords/try-catch.md) je blok catch a zpracování výjimky generované funkční kód. Některé výjimky lze zpracovat v `catch` bloku a problém vyřešit, bez výjimky se znovu; častěji jediné, co musíte se ale ujistěte se, že je vyvolána příslušné výjimky.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu <xref:System.IndexOutOfRangeException> není nejvhodnější výjimka: <xref:System.ArgumentOutOfRangeException> větší smysl pro metodu vzhledem k tomu, že je chyba způsobená pomocí `index` argument předaná volající funkcí.  
  
 [!code-csharp[csProgGuideExceptions#5](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/how-to-handle-an-exception-using-try-catch_1.cs)]  
  
## <a name="comments"></a>Komentáře  
 Kód, který způsobí výjimku ohraničeno `try` bloku. A `catch` je přidán příkaz ihned po zpracování `IndexOutOfRangeException`, pokud k němu dojde. `catch` Blokovat obslužné rutiny `IndexOutOfRangeException` a vyvolá vhodnější `ArgumentOutOfRangeException` výjimka místo. Aby bylo možné poskytnout volající co nejvíce informací, zvažte zadání původní výjimka jako <xref:System.Exception.InnerException%2A> nové výjimky. Protože <xref:System.Exception.InnerException%2A> vlastnost je [jen pro čtení](../../../csharp/language-reference/keywords/readonly.md), je nutné přiřadit v konstruktoru novou výjimku.  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Výjimky a jejich zpracování](../../../csharp/programming-guide/exceptions/index.md)  
 [Zpracování výjimek](../../../csharp/programming-guide/exceptions/exception-handling.md)
