---
title: Zpracování výjimek – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- exception handling [C#], about exception handling
- exceptions [C#], handling
ms.assetid: b4e4ecf2-b907-4e58-891f-2563762258e9
ms.openlocfilehash: 5013738e74aaa260ab6f5bcd4d73904cfbdcc3c8
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590276"
---
# <a name="exception-handling-c-programming-guide"></a>Zpracování výjimek (Průvodce programováním v C#)
Blok [Try](../../language-reference/keywords/try-catch.md) je používán C# programátory k rozdělení kódu, který může být ovlivněn výjimkou. Přidružené bloky [catch](../../language-reference/keywords/try-catch.md) se používají ke zpracování všech výsledných výjimek. Blok [finally](../../language-reference/keywords/try-finally.md) obsahuje kód, který je spuštěn bez ohledu na to, zda je výjimka vyvolána v `try` bloku, například uvolnění prostředků, které `try` jsou přiděleny v bloku. Blok vyžaduje jeden nebo více přidružených `catch` bloků, `finally` nebo blok nebo obojí. `try`  
  
 Následující příklady znázorňují `try-catch` příkaz `try-finally` , příkaz a `try-catch-finally` příkaz.  
  
 [!code-csharp[csProgGuideExceptions#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#6)]  
  
 [!code-csharp[csProgGuideExceptions#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#7)]  
  
 [!code-csharp[csProgGuideExceptions#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#8)]  
  
 Blok bez bloku`finally` nebo způsobí chybu kompilátoru. `catch` `try`  
  
## <a name="catch-blocks"></a>Bloky catch  
 `catch` Blok může určovat typ výjimky, která má být zachycena. Specifikace typu se nazývá *filtr výjimek*. Typ výjimky by měl být odvozen z <xref:System.Exception>. Obecně <xref:System.Exception> nedávejte jako filtr výjimek, Pokud nevíte, jak zpracovat všechny výjimky, které mohou být vyvolány `try` v bloku nebo jste na konci `catch` bloku zahrnuli příkaz [throw](../../language-reference/keywords/throw.md) .  
  
 Několik `catch` bloků s různými filtry výjimek lze zřetězit dohromady. Bloky jsou vyhodnocovány shora dolů ve vašem kódu, ale pro každou vyvolanou výjimku je spuštěn pouze jeden `catch` blok. `catch` Je proveden `catch` první blok, který určuje přesný typ nebo základní třídu vyvolané výjimky. Pokud žádný `catch` blok neurčuje odpovídající filtr výjimek `catch` , je vybrán blok, který nemá filtr, pokud je přítomný v příkazu. Je důležité umístit `catch` bloky s nejpřesnější (tj. nejvíce odvozené) typy výjimek.  
  
 Výjimky byste měli zachytit, pokud jsou splněné následující podmínky:  
  
- Máte dobrý přehled o tom, proč může být výjimka vyvolána, a můžete implementovat konkrétní obnovení, jako je například zobrazení výzvy uživateli při zachycení <xref:System.IO.FileNotFoundException> objektu zadání nového názvu souboru.  
  
- Můžete vytvořit a vyvolat novou, konkrétnější výjimku.  
  
     [!code-csharp[csProgGuideExceptions#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#9)]  
  
- Chcete výjimku částečně zpracovat před tím, než ji předáte pro další zpracování. V následujícím příkladu `catch` je blok použit k přidání položky do protokolu chyb před opakovanou vyvolání výjimky.  
  
     [!code-csharp[csProgGuideExceptions#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#10)]  
  
## <a name="finally-blocks"></a>Bloky finally  
 Blok umožňuje vyčistit akce, které se provádí `try` v bloku. `finally` Je-li k `finally` dispozici, blok se spustí `try` jako poslední, za `catch` blok a libovolným odpovídajícím blokem. Vždy se spustí `catch` blokbezohledunato,zdajevyvolánavýjimka,nebojenalezenblok,který`finally` odpovídá typu výjimky.  
  
 `finally` Blok lze použít k uvolnění prostředků, například datových proudů, připojení k databázi a grafických popisovačů, aniž byste čekali na uvolňování paměti v modulu runtime k finalizaci objektů. Další informace najdete v tématu [použití příkazu Using](../../language-reference/keywords/using-statement.md) .  
  
 V následujícím příkladu `finally` je blok použit k zavření souboru, který je otevřen `try` v bloku. Všimněte si, že před zavřením souboru je zkontrolován stav popisovače souboru. Pokud blok nemůže otevřít soubor, popisovač souboru má stále hodnotu `null` a `finally` blok se nepokusí zavřít. `try` Případně, pokud je soubor v `try` bloku otevřený úspěšně `finally` , blok zavře otevřený soubor.  
  
 [!code-csharp[csProgGuideExceptions#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#11)]  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  

Další informace naleznete v tématu [výjimky](~/_csharplang/spec/exceptions.md) a [příkaz try](~/_csharplang/spec/statements.md#the-try-statement) ve [ C# specifikaci jazyka](../../language-reference/language-specification/index.md). Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.
  
## <a name="see-also"></a>Viz také:

- [C#Odkaz](../../language-reference/index.md)
- [Průvodce programováním v jazyce C#](../index.md)
- [Výjimky a jejich zpracování](./index.md)
- [try-catch](../../language-reference/keywords/try-catch.md)
- [try-finally](../../language-reference/keywords/try-finally.md)
- [try-catch-finally](../../language-reference/keywords/try-catch-finally.md)
- [using – příkaz](../../language-reference/keywords/using-statement.md)
