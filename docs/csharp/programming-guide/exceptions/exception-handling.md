---
title: Zpracování výjimek – Průvodce programováním v C#
description: Přečtěte si o zpracování výjimek. Podívejte se na příklady příkazů try-catch, try-finally a try-catch-finally.
ms.date: 07/20/2015
helpviewer_keywords:
- exception handling [C#], about exception handling
- exceptions [C#], handling
ms.assetid: b4e4ecf2-b907-4e58-891f-2563762258e9
ms.openlocfilehash: 8e55b44573c40f594e567fc5a4501689e66c7af4
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302032"
---
# <a name="exception-handling-c-programming-guide"></a>Zpracování výjimek (Průvodce programováním v C#)
Blok [Try](../../language-reference/keywords/try-catch.md) je používán programátory v jazyce C# k rozdělení kódu, který může být ovlivněn výjimkou. Přidružené bloky [catch](../../language-reference/keywords/try-catch.md) se používají ke zpracování všech výsledných výjimek. Blok [finally](../../language-reference/keywords/try-finally.md) obsahuje kód, který je spuštěn bez ohledu na to, zda je výjimka vyvolána v `try` bloku, například uvolnění prostředků, které jsou přiděleny v `try` bloku. `try`Blok vyžaduje jeden nebo více přidružených `catch` bloků, nebo `finally` blok nebo obojí.  
  
 Následující příklady znázorňují `try-catch` příkaz, `try-finally` příkaz a `try-catch-finally` příkaz.  
  
 [!code-csharp[csProgGuideExceptions#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#6)]  
  
 [!code-csharp[csProgGuideExceptions#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#7)]  
  
 [!code-csharp[csProgGuideExceptions#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#8)]  
  
 `try`Blok bez `catch` `finally` bloku nebo způsobí chybu kompilátoru.  
  
## <a name="catch-blocks"></a>Bloky catch  
 `catch`Blok může určovat typ výjimky, která má být zachycena. Specifikace typu se nazývá *filtr výjimek*. Typ výjimky by měl být odvozen z <xref:System.Exception> . Obecně nedávejte <xref:System.Exception> jako filtr výjimek, Pokud nevíte, jak zpracovat všechny výjimky, které mohou být vyvolány v `try` bloku nebo jste na konci bloku zahrnuli příkaz [throw](../../language-reference/keywords/throw.md) `catch` .  
  
 Několik `catch` bloků s různými filtry výjimek lze zřetězit dohromady. `catch`Bloky jsou vyhodnocovány shora dolů ve vašem kódu, ale `catch` pro každou vyvolanou výjimku je spuštěn pouze jeden blok. `catch`Je proveden první blok, který určuje přesný typ nebo základní třídu vyvolané výjimky. Pokud žádný `catch` blok neurčuje odpovídající filtr výjimek, `catch` je vybrán blok, který nemá filtr, pokud je přítomný v příkazu. Je důležité umístit bloky s nejpřesnější `catch` (tj. nejvíce odvozené) typy výjimek.  
  
 Výjimky byste měli zachytit, pokud jsou splněné následující podmínky:  
  
- Máte dobrý přehled o tom, proč může být výjimka vyvolána, a můžete implementovat konkrétní obnovení, jako je například zobrazení výzvy uživateli při zachycení objektu zadání nového názvu souboru <xref:System.IO.FileNotFoundException> .  
  
- Můžete vytvořit a vyvolat novou, konkrétnější výjimku.  
  
     [!code-csharp[csProgGuideExceptions#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#9)]  
  
- Chcete výjimku částečně zpracovat před tím, než ji předáte pro další zpracování. V následujícím příkladu `catch` je blok použit k přidání položky do protokolu chyb před opakovanou vyvolání výjimky.  
  
     [!code-csharp[csProgGuideExceptions#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#10)]  
  
## <a name="finally-blocks"></a>Bloky finally  
 `finally`Blok umožňuje vyčistit akce, které se provádí v `try` bloku. Je-li k dispozici, `finally` blok se spustí jako poslední, za `try` blok a libovolným odpovídajícím `catch` blokem. `finally`Vždy se spustí blok bez ohledu na to, zda je vyvolána výjimka, nebo `catch` je nalezen blok, který odpovídá typu výjimky.  
  
 `finally`Blok lze použít k uvolnění prostředků, například datových proudů, připojení k databázi a grafických popisovačů, aniž byste čekali na uvolňování paměti v modulu runtime k finalizaci objektů. Další informace najdete v tématu [použití příkazu Using](../../language-reference/keywords/using-statement.md) .  
  
 V následujícím příkladu `finally` je blok použit k zavření souboru, který je otevřen v `try` bloku. Všimněte si, že před zavřením souboru je zkontrolován stav popisovače souboru. Pokud `try` blok nemůže otevřít soubor, popisovač souboru má stále hodnotu `null` a `finally` blok se nepokusí zavřít. Případně, pokud je soubor v bloku otevřený úspěšně `try` , `finally` blok zavře otevřený soubor.  
  
 [!code-csharp[csProgGuideExceptions#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#11)]  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  

Další informace naleznete v tématu [výjimky](~/_csharplang/spec/exceptions.md) a [příkaz try](~/_csharplang/spec/statements.md#the-try-statement) ve [specifikaci jazyka C#](/dotnet/csharp/language-reference/language-specification/introduction). Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.
  
## <a name="see-also"></a>Viz také:

- [Reference jazyka C#](../../language-reference/index.md)
- [Průvodce programováním v C#](../index.md)
- [Výjimky a zpracování výjimek](./index.md)
- [try-catch](../../language-reference/keywords/try-catch.md)
- [try-finally](../../language-reference/keywords/try-finally.md)
- [try-catch-finally](../../language-reference/keywords/try-catch-finally.md)
- [using – příkaz](../../language-reference/keywords/using-statement.md)
