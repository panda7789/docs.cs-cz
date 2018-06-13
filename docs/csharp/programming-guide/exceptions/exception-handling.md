---
title: Zpracování výjimek (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- exception handling [C#], about exception handling
- exceptions [C#], handling
ms.assetid: b4e4ecf2-b907-4e58-891f-2563762258e9
ms.openlocfilehash: bbe9db48ab5cc1313c18fce66312f4334b40b9c5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33337484"
---
# <a name="exception-handling-c-programming-guide"></a>Zpracování výjimek (Průvodce programováním v C#)
A [zkuste](../../../csharp/language-reference/keywords/try-catch.md) blok využívá C# programátorům oddílu kód, který může být ovlivněn výjimku. Související [catch](../../../csharp/language-reference/keywords/try-catch.md) bloky se používají pro zpracování všech výsledné výjimek. A [nakonec](../../../csharp/language-reference/keywords/try-finally.md) blok obsahuje kód, který se spustí bez ohledu na to, zda je vyvolána výjimka `try` bloku, například uvolnění prostředků, které jsou přiděleny v `try` bloku. A `try` bloku vyžaduje jeden nebo více přidružené `catch` bloky, nebo `finally` bloku nebo obojí.  
  
 Následující příklady zobrazují `try-catch` příkaz, `try-finally` příkaz a `try-catch-finally` příkaz.  
  
 [!code-csharp[csProgGuideExceptions#6](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/exception-handling_1.cs)]  
  
 [!code-csharp[csProgGuideExceptions#7](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/exception-handling_2.cs)]  
  
 [!code-csharp[csProgGuideExceptions#8](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/exception-handling_3.cs)]  
  
 A `try` blokovat bez `catch` nebo `finally` bloku způsobí chybu kompilátoru.  
  
## <a name="catch-blocks"></a>Catch – bloky  
 A `catch` bloku můžete zadat typ výjimky k zachycení. Specifikace typu je volána *filtru výjimek*. Typ výjimky by měl být odvozen od <xref:System.Exception>. Obecně platí, nezadávejte <xref:System.Exception> jako výjimka filtrovat Pokud buď víte, jak zpracovat všechny výjimky, které mohou být vyvolány v `try` bloku, nebo můžete mít zahrnuté [throw](../../../csharp/language-reference/keywords/throw.md) příkaz na konci vaše `catch`bloku.  
  
 Více `catch` bloky s filtry výjimek různých dají se propojit. `catch` Vyhodnocení bloků shora dolů v kódu, ale pouze jeden `catch` bloku je spouštěna každý výjimka, která je vyvolána výjimka. První `catch` spouští blok, který určuje typ přesný nebo základní třída vyvolaná výjimka. Pokud žádné `catch` bloku určuje odpovídající filtr výjimek, `catch` blok, který nemá filtr je vybraná, pokud je přítomen v příkazu. Je důležité na pozici `catch` bloky s největším výjimkou (který je nejvíce odvozené) konkrétní typy nejdřív.  
  
 Měli zachytávat výjimky, pokud jsou splněny následující podmínky:  
  
-   Je nutné dobrým porozumět tomu, proč může být vyvolána výjimka, a můžete implementovat konkrétní obnovení, například vyzvat uživatele k zadání nový název souboru, když jste catch <xref:System.IO.FileNotFoundException> objektu.  
  
-   Můžete vytvořit a nové, konkrétnější výjimku vyvolat.  
  
     [!code-csharp[csProgGuideExceptions#9](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/exception-handling_4.cs)]  
  
-   Chcete částečně zpracování výjimky před předáním pro další zpracování. V následujícím příkladu `catch` blokování se používá k přidání položky do protokolu chyb před znovu způsobující výjimku.  
  
     [!code-csharp[csProgGuideExceptions#10](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/exception-handling_5.cs)]  
  
## <a name="finally-blocks"></a>Finally – bloky  
 A `finally` bloku umožňuje vyčištění akce, které se provádějí v `try` bloku. Pokud je k dispozici, `finally` bloku spustí poslední, po `try` bloku a všechny shodná `catch` bloku. A `finally` blokovat vždycky spustí, bez ohledu na to je vyvolána výjimka, nebo `catch` je nalezen odpovídající typ výjimky bloku.  
  
 `finally` Bloku slouží k uvolnění prostředků, jako je například soubor datové proudy, připojení databáze a grafiky zpracovává bez čekání systém uvolňování paměti v modulu runtime pro dokončení objekty. V tématu [pomocí příkazu](../../../csharp/language-reference/keywords/using-statement.md) Další informace.  
  
 V následujícím příkladu `finally` bloku slouží k zavření souboru, který je otevřen v `try` bloku. Všimněte si, že stav popisovač souboru je zaškrtnuta možnost před soubor zavřený. Pokud `try` bloku nelze otevřít soubor, popisovač souboru stále má hodnotu `null` a `finally` bloku nepokouší zavřete ho. Případně pokud úspěšně v otevření souboru `try` bloku, `finally` bloku zavře, otevřete soubor.  
  
 [!code-csharp[csProgGuideExceptions#11](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/exception-handling_6.cs)]  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Výjimky a jejich zpracování](../../../csharp/programming-guide/exceptions/index.md)  
 [try-catch](../../../csharp/language-reference/keywords/try-catch.md)  
 [try-finally](../../../csharp/language-reference/keywords/try-finally.md)  
 [try-catch-finally](../../../csharp/language-reference/keywords/try-catch-finally.md)  
 [using – příkaz](../../../csharp/language-reference/keywords/using-statement.md)
