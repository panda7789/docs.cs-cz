---
title: Postup zpracování výjimky pomocí Průvodce Try-Catch- C# Programming
ms.date: 07/20/2015
helpviewer_keywords:
- exception handling [C#], try/catch blocks
- exceptions [C#], try/catch blocks
- try/catch blocks [C#]
ms.assetid: ca8e3773-980e-4767-8633-7408540e9818
ms.openlocfilehash: adfc53cbe4fd603ac3a6de6b9a0162320d5a2e19
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712283"
---
# <a name="how-to-handle-an-exception-using-trycatch-c-programming-guide"></a>Postup zpracování výjimky pomocí try/catch (C# Průvodce programováním)
Účelem bloku [try-catch](../../language-reference/keywords/try-catch.md) je zachycení a zpracování výjimky generované pracovním kódem. Některé výjimky lze zpracovat v `catch` bloku a problém je vyřešen, aniž by došlo k opakovanému vyvolání výjimky; častěji jen to, co můžete udělat, je však zajistěte, aby byla vyvolána příslušná výjimka.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu <xref:System.IndexOutOfRangeException> není nejvhodnější výjimkou: <xref:System.ArgumentOutOfRangeException> dává pro metodu větší smysl, protože chyba je způsobena argumentem `index` předaným volajícím.  
  
 [!code-csharp[csProgGuideExceptions#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#5)]  
  
## <a name="comments"></a>Komentáře  
 Kód, který způsobuje výjimku, je uzavřen v bloku `try`. Příkaz `catch` je přidán ihned po zpracování `IndexOutOfRangeException`, pokud k němu dojde. Blok `catch` zpracovává `IndexOutOfRangeException` a místo toho vyvolá vhodnější výjimku `ArgumentOutOfRangeException`. Aby bylo možné poskytnout volající co nejvíc informací, zvažte určení původní výjimky jako <xref:System.Exception.InnerException%2A> nové výjimky. Vzhledem k tomu, že vlastnost <xref:System.Exception.InnerException%2A> je [jen pro čtení](../../language-reference/keywords/readonly.md), je nutné ji přiřadit v konstruktoru nové výjimky.  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Výjimky a jejich zpracování](./index.md)
- [Zpracování výjimek](./exception-handling.md)
