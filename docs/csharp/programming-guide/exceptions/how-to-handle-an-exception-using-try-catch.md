---
title: Jak zpracovat výjimku pomocí try-catch - C# Programovací průvodce
ms.date: 07/20/2015
helpviewer_keywords:
- exception handling [C#], try/catch blocks
- exceptions [C#], try/catch blocks
- try/catch blocks [C#]
ms.assetid: ca8e3773-980e-4767-8633-7408540e9818
ms.openlocfilehash: adfc53cbe4fd603ac3a6de6b9a0162320d5a2e19
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712283"
---
# <a name="how-to-handle-an-exception-using-trycatch-c-programming-guide"></a>Jak zpracovat výjimku pomocí try/catch (Průvodce programováním jazyka C#)
Účelem bloku [try-catch](../../language-reference/keywords/try-catch.md) je zachytit a zpracovat výjimku generovanou pracovním kódem. Některé výjimky mohou být `catch` zpracovány v bloku a problém vyřešen bez výjimky je znovu vyvolána; však častěji jediná věc, kterou můžete udělat, je ujistěte se, že je vyvolána příslušná výjimka.  
  
## <a name="example"></a>Příklad  
 V tomto <xref:System.IndexOutOfRangeException> příkladu není nejvhodnější <xref:System.ArgumentOutOfRangeException> výjimkou: dává větší smysl pro metodu, protože chyba je způsobena `index` argumentem předaný volajícím.  
  
 [!code-csharp[csProgGuideExceptions#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#5)]  
  
## <a name="comments"></a>Komentáře  
 Kód, který způsobuje výjimku je `try` uzavřen v bloku. Příkaz `catch` je přidán ihned `IndexOutOfRangeException`po zpracování , pokud k němu dojde. Blok `catch` zpracovává `IndexOutOfRangeException` a vyvolá vhodnější `ArgumentOutOfRangeException` výjimku místo. Chcete-li volajícímu poskytnout co nejvíce informací, zvažte zadání <xref:System.Exception.InnerException%2A> původní výjimky jako nové výjimky. Vzhledem <xref:System.Exception.InnerException%2A> k tomu, že vlastnost je [jen pro čtení](../../language-reference/keywords/readonly.md), musíte ji přiřadit v konstruktoru nové výjimky.  
  
## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../index.md)
- [Výjimky a zpracování výjimek](./index.md)
- [Zpracování výjimek](./exception-handling.md)
