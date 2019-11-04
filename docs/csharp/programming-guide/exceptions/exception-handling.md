---
title: Zpracování výjimek – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- exception handling [C#], about exception handling
- exceptions [C#], handling
ms.assetid: b4e4ecf2-b907-4e58-891f-2563762258e9
ms.openlocfilehash: 895f561c15941d851980ea9b392d2e86db2462f3
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423288"
---
# <a name="exception-handling-c-programming-guide"></a>Zpracování výjimek (Průvodce programováním v C#)
Blok [Try](../../language-reference/keywords/try-catch.md) je používán C# programátory k rozdělení kódu, který může být ovlivněn výjimkou. Přidružené bloky [catch](../../language-reference/keywords/try-catch.md) se používají ke zpracování všech výsledných výjimek. Blok [finally](../../language-reference/keywords/try-finally.md) obsahuje kód, který je spuštěn bez ohledu na to, zda je vyvolána výjimka v bloku `try`, jako je například uvolnění prostředků, které jsou přiděleny v bloku `try`. `try` blok vyžaduje jeden nebo více přidružených bloků `catch` nebo blok `finally` nebo obojí.  
  
 Následující příklady znázorňují příkaz `try-catch`, příkaz `try-finally` a příkaz `try-catch-finally`.  
  
 [!code-csharp[csProgGuideExceptions#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#6)]  
  
 [!code-csharp[csProgGuideExceptions#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#7)]  
  
 [!code-csharp[csProgGuideExceptions#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#8)]  
  
 Blok `try` bez bloku `catch` nebo `finally` způsobí chybu kompilátoru.  
  
## <a name="catch-blocks"></a>Bloky catch  
 Blok `catch` může určovat typ výjimky, která se má zachytit. Specifikace typu se nazývá *filtr výjimek*. Typ výjimky by měl být odvozen z <xref:System.Exception>. Obecně nespecifikujte <xref:System.Exception> jako filtr výjimek, Pokud nevíte, jak zpracovat všechny výjimky, které mohou být vyvolány v bloku `try` nebo zda jste na konci bloku `catch` zahrnuli příkaz [throw](../../language-reference/keywords/throw.md) .  
  
 Několik bloků `catch` s různými filtry výjimek lze zřetězit dohromady. `catch` bloky jsou vyhodnocovány shora dolů ve vašem kódu, ale pro každou vyvolanou výjimku je spuštěn pouze jeden blok `catch`. Je proveden první blok `catch`, který určuje přesný typ nebo základní třídu vyvolané výjimky. Pokud žádný `catch` blok neurčuje odpovídající filtr výjimek, je vybrán `catch` blok, který nemá filtr, pokud je v příkazu přítomen. Je důležité umístit `catch` bloky s nejpřesnější typy výjimek (tj. nejvíce odvozené).  
  
 Výjimky byste měli zachytit, pokud jsou splněné následující podmínky:  
  
- Máte dobrý přehled o tom, proč může být výjimka vyvolána, a můžete implementovat konkrétní obnovení, jako je například zobrazení výzvy uživateli při zachytávání objektu <xref:System.IO.FileNotFoundException> k zadání nového názvu souboru.  
  
- Můžete vytvořit a vyvolat novou, konkrétnější výjimku.  
  
     [!code-csharp[csProgGuideExceptions#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#9)]  
  
- Chcete výjimku částečně zpracovat před tím, než ji předáte pro další zpracování. V následujícím příkladu se `catch` blok používá k přidání položky do protokolu chyb před opakovanou vyvolání výjimky.  
  
     [!code-csharp[csProgGuideExceptions#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#10)]  
  
## <a name="finally-blocks"></a>Bloky finally  
 `finally` blok umožňuje vyčistit akce, které se provádí v bloku `try`. Je-li k dispozici, `finally` blok spuštěn jako poslední, po bloku `try` a jakémkoli odpovídajícím bloku `catch`. `finally` blok vždy běží bez ohledu na to, zda je vyvolána výjimka, nebo je nalezena `catch` blok, který odpovídá typu výjimky.  
  
 `finally` blok lze použít k uvolnění prostředků, například datových proudů, připojení k databázi a grafických popisovačů, aniž byste čekali na uvolňování paměti v modulu runtime k finalizaci objektů. Další informace najdete v tématu [použití příkazu Using](../../language-reference/keywords/using-statement.md) .  
  
 V následujícím příkladu je `finally` blok použit k zavření souboru, který je otevřen v bloku `try`. Všimněte si, že před zavřením souboru je zkontrolován stav popisovače souboru. Pokud `try` blok nemůže soubor otevřít, má popisovač souboru stále hodnotu `null` a blok `finally` se nepokusí zavřít. Případně, pokud je soubor otevřen úspěšně v bloku `try`, blok `finally` zavře otevřený soubor.  
  
 [!code-csharp[csProgGuideExceptions#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#11)]  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  

Další informace naleznete v tématu [výjimky](~/_csharplang/spec/exceptions.md) a [příkaz try](~/_csharplang/spec/statements.md#the-try-statement) ve [ C# specifikaci jazyka](/dotnet/csharp/language-reference/language-specification/introduction). Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.
  
## <a name="see-also"></a>Viz také:

- [C#Odkaz](../../language-reference/index.md)
- [Průvodce programováním v jazyce C#](../index.md)
- [Výjimky a jejich zpracování](./index.md)
- [try-catch](../../language-reference/keywords/try-catch.md)
- [try-finally](../../language-reference/keywords/try-finally.md)
- [try-catch-finally](../../language-reference/keywords/try-catch-finally.md)
- [using – příkaz](../../language-reference/keywords/using-statement.md)
