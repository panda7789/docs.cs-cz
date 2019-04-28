---
title: 'Postupy: Zpracování výjimky pomocí bloku try-catch - C# Průvodce programováním pro službu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- exception handling [C#], try/catch blocks
- exceptions [C#], try/catch blocks
- try/catch blocks [C#]
ms.assetid: ca8e3773-980e-4767-8633-7408540e9818
ms.openlocfilehash: 0524248a0b82ddc115e82108f774e894f1dc2f26
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61710833"
---
# <a name="how-to-handle-an-exception-using-trycatch-c-programming-guide"></a>Postupy: Zpracování výjimky pomocí bloku try/catch (C# Programming Guide)
Účel [bloku try-catch](../../../csharp/language-reference/keywords/try-catch.md) blok je k zachycení a zpracování výjimky generované funkční kód. Některé výjimky mohou být zpracovány v `catch` bloku a tento problém vyřešit bez výjimky je znovu vyvolána; však častěji pouze jednu, která vám pomůžou se ujistěte, že je vyvolána vhodná výjimka.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu <xref:System.IndexOutOfRangeException> není nejvhodnější výjimka: <xref:System.ArgumentOutOfRangeException> větší smysl metoda vzhledem k tomu, chyba je způsobená `index` argument předaná volající funkcí.  
  
 [!code-csharp[csProgGuideExceptions#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#5)]  
  
## <a name="comments"></a>Komentáře  
 Kód, který způsobí, že výjimka je ohraničen `try` bloku. A `catch` přidán příkaz ihned po zpracování `IndexOutOfRangeException`, pokud k němu dojde. `catch` Blokovat obslužné rutiny `IndexOutOfRangeException` a vyvolá více odpovídající `ArgumentOutOfRangeException` výjimka místo. Aby bylo možné poskytnout co nejvíce informací volajícího, zvažte zadání původní výjimku jako <xref:System.Exception.InnerException%2A> nové výjimky. Vzhledem k tomu, <xref:System.Exception.InnerException%2A> vlastnost je [jen pro čtení](../../../csharp/language-reference/keywords/readonly.md), je nutné přiřadit v konstruktoru novou výjimku.  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
- [Výjimky a jejich zpracování](../../../csharp/programming-guide/exceptions/index.md)
- [Zpracování výjimek](../../../csharp/programming-guide/exceptions/exception-handling.md)
