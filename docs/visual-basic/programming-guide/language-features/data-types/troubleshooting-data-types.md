---
title: Řešení potíží s datovými typy (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Char data type [Visual Basic], converting
- Decimal data type [Visual Basic], conversions
- data types [Visual Basic], troubleshooting
- literals [Visual Basic], default types
- type characters [Visual Basic], literal
- Mod operator [Visual Basic], in floating-point operations
- troubleshooting Visual Basic, data types
- troubleshooting data types [Visual Basic]
- floating-point numbers [Visual Basic], precision
- Boolean data type [Visual Basic], converting
- literal types [Visual Basic]
- literal type characters [Visual Basic]
- floating-point numbers [Visual Basic], imprecision
- String data type [Visual Basic], converting
- floating-point numbers [Visual Basic], comparison
- floating-point numbers
ms.assetid: 90040d67-b630-4125-a6ae-37195b079042
caps.latest.revision: 29
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f34e7bc50a51032387cf01db3fae17ef44b8b4d9
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="troubleshooting-data-types-visual-basic"></a>Řešení potíží s datovými typy (Visual Basic)
Tato stránka obsahuje některé běžné problémy, ke kterým dochází při provádění operací na vnitřní datové typy.  
  
## <a name="floating-point-expressions-do-not-compare-as-equal"></a>Výrazy s plovoucí desetinnou čárkou není porovnat jako rovná  
 Při práci s plovoucí desetinnou čárkou ([jeden datový typ](../../../../visual-basic/language-reference/data-types/single-data-type.md) a [dvojitý datový typ](../../../../visual-basic/language-reference/data-types/double-data-type.md)), mějte na paměti, že jsou uloženy jako binární zlomků. To znamená, že se nemůže přidržet přesná reprezentace jakékoli množství, který není binární zlomek (ve formátu tisíc nebo (2 ^ n), kde tisíc a n jsou celá čísla). Například 0,5 (= 1/2) a 0.3125 (= 5/16) můžete uchovávat jako přesné hodnoty, zatímco (= 1/5) 0.2 a 0.3 (= 3/10) může být pouze aproximace.  
  
 Z tohoto důvodu nepřesnosti, nemůžete spoléhat na přesné výsledky při pracovat na hodnoty s plovoucí desetinnou čárkou. Konkrétně dvě hodnoty, které jsou teoreticky stejné pravděpodobně reprezentace mírně lišit.  
  
| K porovnání s plovoucí desetinnou čárkou počty | 
|---| 
|1.  Výpočet absolutní hodnotu jejich rozdíl pomocí <xref:System.Math.Abs%2A> metodu <xref:System.Math> třídy v <xref:System> oboru názvů.<br />2.  Určení přijatelné maximální rozdíl, tak, že můžete zvážit dva množství, která mají být stejné pro praktické účely, pokud jejich rozdílem je, není větší.<br />3.  Porovnejte absolutní hodnota rozdílu přijatelné rozdílu.|  
  
 Následující příklad ukazuje nesprávný a správnou porovnání dva `Double` hodnoty.  
  
 [!code-vb[VbVbalrDataTypes#10](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/troubleshooting-data-types_1.vb)]  
  
 Předchozí příklad používá <xref:System.Double.ToString%2A> metodu <xref:System.Double> struktury tak, aby ji můžete zadat lepší přesnosti než `CStr` používá – klíčové slovo. Výchozí hodnota je 15 číslic, ale ve formátu "G17" ji rozšiřuje na 17 číslic.  
  
## <a name="mod-operator-does-not-return-accurate-result"></a>Mod – operátor nevrátí přesné výsledky  
 Z důvodu nepřesnosti s plovoucí desetinnou čárkou úložiště [Mod operátor](../../../../visual-basic/language-reference/operators/mod-operator.md) neočekávaný výsledek může vrátit, pokud je alespoň jedna z operandy s plovoucí desetinnou čárkou.  
  
 [Decimal – datový typ](../../../../visual-basic/language-reference/data-types/decimal-data-type.md) nepoužívá reprezentace plovoucí desetinné čárky. Mnoho čísla, které jsou nepřesné v `Single` a `Double` jsou přesně v `Decimal` (například 0.2 a 0.3). I když aritmetické je pomalejší v `Decimal` než v s plovoucí desetinnou čárkou, může být vhodné ke snížení výkonu zajistit lepší přesnosti.  
  
|Najít zbytek celé číslo s plovoucí desetinnou čárkou počty|  
|---|  
|1.  Deklarujte proměnné jako `Decimal`.<br />2.  Použít znak typu literálu `D` vynutit literály k `Decimal`, v případě, že jejich hodnoty jsou příliš velké vzhledem k `Long` datového typu.|  
  
 Následující příklad ukazuje potenciální nepřesnosti operandů s plovoucí desetinnou čárkou.  
  
 [!code-vb[VbVbalrDataTypes#11](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/troubleshooting-data-types_2.vb)]  
  
 Předchozí příklad používá <xref:System.Double.ToString%2A> metodu <xref:System.Double> struktury tak, aby ji můžete zadat lepší přesnosti než `CStr` používá – klíčové slovo. Výchozí hodnota je 15 číslic, ale ve formátu "G17" ji rozšiřuje na 17 číslic.  
  
 Protože `zeroPointTwo` je `Double`, jeho hodnota 0,2 je nekonečnou opakovaný binární zlomek s hodnotou uloženou 0.20000000000000001. Dělení 2.0 toto množství vypočítá 9.9999999999999995 s zbytek 0.19999999999999991.  
  
 Ve výrazu pro `decimalRemainder`, znak typu literálu `D` vynutí oba operandy k `Decimal`, a 0,2 má znázornění přesné. Proto `Mod` operátor vypočítá zbytek 0,0 očekávané.  
  
 Všimněte si, že není dostatečná pro deklarovat `decimalRemainder` jako `Decimal`. Musíte také vynutit literály k `Decimal`, nebo používají `Double` ve výchozím nastavení a `decimalRemainder` obdrží nesprávné stejnou hodnotu jako `doubleRemainder`.  
  
## <a name="boolean-type-does-not-convert-to-numeric-type-accurately"></a>Typem logická hodnota není převod na číselný typ přesně  
 [Datový typ Boolean](../../../../visual-basic/language-reference/data-types/boolean-data-type.md) hodnoty nejsou uložené jako čísla a uložené hodnoty nejsou určeny jako ekvivalentní na čísla. Pro kompatibilitu s předchozími verzemi jazyka Visual Basic poskytuje klíčová slova převodu ([CType – funkce](../../../../visual-basic/language-reference/functions/ctype-function.md), `CBool`, `CInt`a tak dále) pro převod mezi `Boolean` a číselnými typy. Ale jiné jazyky někdy provést tyto převody odlišně, stejně jako [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] metody.  
  
 Nikdy byste měli zapsat kód, který závisí na ekvivalentní číselné hodnoty pro `True` a `False`. Kdykoli je to možné, měli byste omezit využití `Boolean` proměnné logické hodnoty, pro které jsou navrženy. Pokud musíte kombinovat `Boolean` a číselné hodnoty, ujistěte se, že rozumíte převod metoda, kterou jste vybrali.  
  
### <a name="conversion-in-visual-basic"></a>Převod v jazyce Visual Basic  
 Při použití `CType` nebo `CBool` klíčová slova převodu převod číselných datových typů pro `Boolean`, stane 0 `False` a všechny ostatní hodnoty přestat `True`. Při převodu `Boolean` hodnot na číselné typy pomocí klíčová slova převodu, `False` se změní na 0 a `True` se změní na hodnotu -1.  
  
### <a name="conversion-in-the-framework"></a>Převod v rozhraní Framework  
 <xref:System.Convert.ToInt32%2A> Metodu <xref:System.Convert> třídy v <xref:System> převede obor názvů `True` až + 1.  
  
 Pokud je nutné převést `Boolean` hodnoty na číselný datový typ, dávejte pozor, o jakou metodu převodu použijete.  
  
## <a name="character-literal-generates-compiler-error"></a>Znakový literál vygeneruje Chyba kompilátoru  
 Neexistují žádné znaky typu předpokládá Visual Basic výchozí datové typy pro literály. Výchozí typ znaku literálu – uzavřena v uvozovkách (`" "`) – je `String`.  
  
 `String` Datový typ není rozšíří do [Char – datový typ](../../../../visual-basic/language-reference/data-types/char-data-type.md). To znamená, že pokud chcete přiřadit k literál `Char` proměnné, musíte provést zužující převod nebo vynutit literál k `Char` typu.  

|K vytvoření znakový literál přiřadí proměnné nebo konstanta|
|---|  
|1.  Deklarovat proměnnou nebo konstanta jako `Char`.<br />2.  Hodnota znaku uzavřít do uvozovek (`" "`).<br />3.  Postupujte podle uzavírací dvojité uvozovky s znak typu literálu `C` vynutit literál k `Char`. To je nezbytné, pokud kontrola typu přepínače ([Option Strict – příkaz](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) je `On`, a je v každém případě žádoucí.|  
  
 Následující příklad ukazuje úspěšné i neúspěšné přiřazení literálu k `Char` proměnné.  
  
 [!code-vb[VbVbalrDataTypes#12](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/troubleshooting-data-types_3.vb)]  
  
 Existuje vždy riziko pomocí zužující převody, protože můžou selhat v době běhu. Například převod z `String` k `Char` může selhat, pokud `String` hodnota obsahuje více než jeden znak. Proto je lepší programování používat `C` zadávat znaky.  
  
## <a name="string-conversion-fails-at-run-time"></a>Převod řetězce selže v době běhu  
 [String – datový typ](../../../../visual-basic/language-reference/data-types/string-data-type.md) účastní velmi málo rozšiřující převody. `String` rozšiřuje pouze na sebe sama a `Object`a pouze `Char` a `Char()` ( `Char` pole) rozšíří do `String`. Důvodem je, že `String` proměnných a konstant může obsahovat hodnoty, které nemůže obsahovat jiné datové typy.  
  
 Když je kontrola typu přepínače ([Option Strict – příkaz](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) je `On`, kompilátor zakazuje všechny implicitní zužující převod. To zahrnuje ty zahrnující `String`. Váš kód můžete dál používat klíčová slova převodu, jako `CStr` a [CType – funkce](../../../../visual-basic/language-reference/functions/ctype-function.md), které přímo [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] k pokusu o převod.  
  
> [!NOTE]
>  Chyba zužující převod je potlačen pro převody z elementů v `For Each…Next` kolekce řídicí proměnná smyčky. Další informace a příklady naleznete v části "Zužující převody" v [For Each... Další příkaz](../../../../visual-basic/language-reference/statements/for-each-next-statement.md).  
  
### <a name="narrowing-conversion-protection"></a>Zužující převod ochrany  
 Zužující převody nevýhodou je, že může selhat v době běhu. Například pokud `String` proměnná obsahuje nic jiného, než "hodnotu True" nebo "Nepravda", nelze převést na `Boolean`. Pokud obsahuje znaky interpunkce, převod na číselný typ. se nezdaří. Pokud víte, že vaše `String` proměnné vždy obsahuje hodnoty, které může přijmout typ cílového, by neměl zkuste převod.  
  
 Pokud je nutné převést z `String` na jiný datový typ, má-li uzavřete pokusu o převod v nejbezpečnější postup [zkuste... Catch... Finally – příkaz](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md). To vám umožňuje řešit selhání spuštění.  
  
### <a name="character-arrays"></a>Znaková pole  
 Jediný `Char` a pole `Char` elementy obě rozšíří do `String`. Ale `String` není rozšíří do `Char()`. Převést `String` hodnotu `Char` pole, které můžete použít <xref:System.String.ToCharArray%2A> metodu <xref:System.String?displayProperty=nameWithType> třída.  
  
### <a name="meaningless-values"></a>Smysl hodnoty  
 Obecně platí `String` hodnoty nejsou smysluplný v jiné datové typy a převod je vysoce umělé a nebezpečné. Kdykoli je to možné, měli byste omezit využití `String` proměnné sekvence znaků, pro které jsou navrženy. By nikdy napsat kód, který závisí na ekvivalentní hodnoty v jiných typech.  
  
## <a name="see-also"></a>Viz také  
 [Datové typy](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [Znaky typu](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)  
 [Typy hodnot a odkazové typy](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [Převody typů v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [Datové typy](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Funkce pro převod typů](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Účinné používání datových typů](../../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
