---
title: Zpracování výjimek – průvodce programováním jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- exception handling [C#], about exception handling
- exceptions [C#], handling
ms.assetid: b4e4ecf2-b907-4e58-891f-2563762258e9
ms.openlocfilehash: ee1e5bd15183dad9ffe97824f9b194668e9d3b17
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705298"
---
# <a name="exception-handling-c-programming-guide"></a>Zpracování výjimek (Průvodce programováním v C#)
Try [try](../../language-reference/keywords/try-catch.md) blok je používán programátory Jazyka C# k oddílu kódu, který může být ovlivněn výjimkou. Přidružené [catch](../../language-reference/keywords/try-catch.md) bloky se používají ke zpracování všech výsledných výjimek. Finally [finally](../../language-reference/keywords/try-finally.md) blok obsahuje kód, který je spuštěn bez ohledu na `try` to, zda je vyvolána výjimka `try` v bloku, jako je například uvolnění prostředků, které jsou přiděleny v bloku. Blok `try` vyžaduje jeden nebo `catch` více přidružených bloků, `finally` blok nebo obojí.  
  
 Následující příklady ukazují `try-catch` příkaz, `try-finally` příkaz a `try-catch-finally` příkaz.  
  
 [!code-csharp[csProgGuideExceptions#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#6)]  
  
 [!code-csharp[csProgGuideExceptions#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#7)]  
  
 [!code-csharp[csProgGuideExceptions#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#8)]  
  
 Blok `try` bez `catch` nebo `finally` bloku způsobí chybu kompilátoru.  
  
## <a name="catch-blocks"></a>Úlovek bloky  
 Blok `catch` může určit typ výjimky catch. Specifikace typu se nazývá *filtr výjimek*. Typ výjimky by měl <xref:System.Exception>být odvozen z . Obecně <xref:System.Exception> nezadávejte jako filtr výjimek, pokud nevíte, jak zpracovat všechny `try` výjimky, které mohou být vyvolány v `catch` bloku, nebo jste zahrnuli příkaz [throw](../../language-reference/keywords/throw.md) na konci bloku.  
  
 Více `catch` bloků s různými filtry výjimek lze zřetězit dohromady. Bloky `catch` jsou vyhodnocovány shora dolů `catch` v kódu, ale pouze jeden blok je spuštěn pro každou výjimku, která je vyvolána. První `catch` blok, který určuje přesný typ nebo základní třídu vyvolání výjimky je proveden. Pokud `catch` žádný blok určuje odpovídající filtr `catch` výjimek, je vybrán blok, který nemá filtr, pokud je v příkazu přítomen. Je důležité nejprve umístit `catch` bloky s nejkonkrétnějšími (to znamená nejvíce odvozenými) typy výjimek.  
  
 Výjimky byste měli zachytit, pokud jsou splněny následující podmínky:  
  
- Máte dobré znalosti o tom, proč může být vyvolána výjimka a můžete implementovat konkrétní obnovení, jako <xref:System.IO.FileNotFoundException> je například výzva uživateli zadat nový název souboru při zachycení objektu.  
  
- Můžete vytvořit a vyvolat novou, konkrétnější výjimku.  
  
     [!code-csharp[csProgGuideExceptions#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#9)]  
  
- Chcete částečně zpracovat výjimku před předáním pro další zpracování. V následujícím příkladu `catch` se blok používá k přidání položky do protokolu chyb před opětovným vyvoláním výjimky.  
  
     [!code-csharp[csProgGuideExceptions#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#10)]  
  
## <a name="finally-blocks"></a>Konečně bloky  
 Blok `finally` umožňuje vyčistit akce, které jsou `try` prováděny v bloku. Pokud je `finally` k dispozici, blok `try` provede poslední, `catch` po bloku a všechny odpovídající bloku. Blok `finally` vždy spustí, bez ohledu na to, `catch` zda je vyvolána výjimka nebo blok odpovídající typu výjimky je nalezen.  
  
 Blok `finally` lze uvolnit prostředky, jako jsou datové proudy souborů, připojení k databázi a grafické popisovače bez čekání na uvolňování paměti v době runtime k dokončení objektů. Další informace najdete [v tématu použití příkazu.](../../language-reference/keywords/using-statement.md)  
  
 V následujícím příkladu `finally` se blok používá k zavření `try` souboru, který je otevřen v bloku. Všimněte si, že stav popisovače souboru je zaškrtnuta před zavřením souboru. Pokud `try` blok nemůže otevřít soubor, popisovač souboru má stále hodnotu `null` a `finally` blok se nepokouší jej zavřít. Případně pokud je soubor úspěšně otevřen `try` v bloku, `finally` blok zavře otevřený soubor.  
  
 [!code-csharp[csProgGuideExceptions#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#11)]  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  

Další informace naleznete v [tématu](~/_csharplang/spec/statements.md#the-try-statement) [Exceptions](~/_csharplang/spec/exceptions.md) and The try statement in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction). Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.
  
## <a name="see-also"></a>Viz také

- [Odkaz jazyka C#](../../language-reference/index.md)
- [Programovací příručka jazyka C#](../index.md)
- [Výjimky a zpracování výjimek](./index.md)
- [try-catch](../../language-reference/keywords/try-catch.md)
- [try-finally](../../language-reference/keywords/try-finally.md)
- [try-catch-finally](../../language-reference/keywords/try-catch-finally.md)
- [using – příkaz](../../language-reference/keywords/using-statement.md)
