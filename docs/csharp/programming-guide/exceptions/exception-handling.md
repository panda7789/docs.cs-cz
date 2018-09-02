---
title: Zpracování výjimek (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- exception handling [C#], about exception handling
- exceptions [C#], handling
ms.assetid: b4e4ecf2-b907-4e58-891f-2563762258e9
ms.openlocfilehash: bbe9db48ab5cc1313c18fce66312f4334b40b9c5
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43402792"
---
# <a name="exception-handling-c-programming-guide"></a>Zpracování výjimek (Průvodce programováním v C#)
A [zkuste](../../../csharp/language-reference/keywords/try-catch.md) blokem programátory C# pro oddíl kódu, které by mohly mít dopad výjimky. Související [catch](../../../csharp/language-reference/keywords/try-catch.md) bloky se používají ke zpracování všech výsledný výjimek. A [nakonec](../../../csharp/language-reference/keywords/try-finally.md) obsahuje kód, který se spustí bez ohledu na to, zda je výjimka vyvolána bloku `try` bloku, jako je například uvolnění prostředků, které jsou přiděleny v `try` bloku. A `try` blok vyžaduje jeden nebo více přidružené `catch` bloky, nebo `finally` bloku nebo obojí.  
  
 Následující příklady ukazují `try-catch` příkaz, `try-finally` příkaz a `try-catch-finally` příkazu.  
  
 [!code-csharp[csProgGuideExceptions#6](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/exception-handling_1.cs)]  
  
 [!code-csharp[csProgGuideExceptions#7](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/exception-handling_2.cs)]  
  
 [!code-csharp[csProgGuideExceptions#8](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/exception-handling_3.cs)]  
  
 A `try` blokovat bez `catch` nebo `finally` blok způsobí chybu kompilátoru.  
  
## <a name="catch-blocks"></a>Bloky catch  
 A `catch` blok můžete zadat typ výjimky pro zachycení. Specifikace typu je volána *filtr výjimek*. Typ výjimky musí být odvozen od <xref:System.Exception>. Obecně platí, nezadávejte <xref:System.Exception> jako filtr výjimku, pokud buď nevíte, jak zpracovávat všechny výjimky, které mohou být vyvolány v `try` bloku nebo jste zahrnuli [throw](../../../csharp/language-reference/keywords/throw.md) příkaz na konci vaší `catch`bloku.  
  
 Více `catch` bloky s jinou výjimku filtry je možné zřetězit. `catch` Vyhodnocení bloků shora dolů v kódu, ale pouze jeden `catch` bloku je prováděna pro jednotlivé výjimky, která je vyvolána. První `catch` je proveden blok, který určuje přesný typ nebo základní třídu vyvolané výjimky. Pokud ne `catch` bloku určuje odpovídající filtr výjimek, `catch` blok, který nemá filtr je vybraná, pokud je k dispozici v příkazu. Je důležité, pokud chcete umístit `catch` nejprve typy bloků s nejvíce výjimkou konkrétní (to znamená, nejvíce odvozená).  
  
 Byste zachytit výjimky, pokud jsou splněny následující podmínky:  
  
-   Je nutné dobrým porozumět tomu, proč může být vyvolána výjimka, a vy můžete implementovat konkrétní obnovení, například vyzvat uživatele k zadání nový název souboru, když při zachycení <xref:System.IO.FileNotFoundException> objektu.  
  
-   Můžete vytvořit a vyvolat výjimku nové a konkrétnější.  
  
     [!code-csharp[csProgGuideExceptions#9](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/exception-handling_4.cs)]  
  
-   Chcete částečně zpracování výjimky před předáním pro další zpracování. V následujícím příkladu `catch` blokování se používá k přidání položky do protokolu chyb před opětném vyvolávání výjimky.  
  
     [!code-csharp[csProgGuideExceptions#10](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/exception-handling_5.cs)]  
  
## <a name="finally-blocks"></a>Bloky finally  
 A `finally` bloku umožňuje vyčistit akce, které se provádějí v `try` bloku. Pokud jsou k dispozici, `finally` blok se spustí po poslední, `try` blok a všechny odpovídající `catch` bloku. A `finally` blok vždy, bez ohledu na to, zda dojde k výjimce nebo `catch` najít odpovídající typ výjimky bloku.  
  
 `finally` Bloku slouží k uvolnění prostředků, jako jsou datové proudy souborů, připojení k databázi, a zpracovává grafiky bez čekání na dokončení objekty systému uvolňování paměti v modulu runtime. Zobrazit [příkaz using](../../../csharp/language-reference/keywords/using-statement.md) Další informace.  
  
 V následujícím příkladu `finally` blokem zavřete soubor, který je otevřen v `try` bloku. Všimněte si, že před zavřením souboru kontroly stavu popisovače souboru. Pokud `try` block nemůžou soubor otevřít, popisovač souboru stále má hodnotu `null` a `finally` bloku nepokusí se jej zavřete. Případně pokud je soubor úspěšně otevřen `try` bloku `finally` bloku zavře otevřený soubor.  
  
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
