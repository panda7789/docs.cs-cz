---
title: Řešení potíží s datovými typy (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: 9bbc7f51de9899354184d051d8f1a584651dd030
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44213936"
---
# <a name="troubleshooting-data-types-visual-basic"></a>Řešení potíží s datovými typy (Visual Basic)
Tato stránka obsahuje některé běžné problémy, které se mohou vyskytnout při provádění operací ve vnitřních datových typů.  
  
## <a name="floating-point-expressions-do-not-compare-as-equal"></a>Jako rovnocenné Neporovnávejte výrazů s plovoucí desetinnou čárkou  
 Při práci s čísly s plovoucí desetinnou čárkou ([jeden datový typ](../../../../visual-basic/language-reference/data-types/single-data-type.md) a [datový typ Double](../../../../visual-basic/language-reference/data-types/double-data-type.md)), mějte na paměti, že se ukládají jako binární zlomků. To znamená, že se nemůže obsahovat přesnou reprezentací libovolné množství, který není binární zlomek (formuláře k nebo (2 ^ n), kde k a n jsou celá čísla). Například 0,5 (= 1/2) a 0.3125 (tzn. 5/16) se můžou uchovávat jako přesné hodnoty, zatímco se (= 1/5) 0.2 a 0.3 (= 3/10) může být pouze rovin útoku.  
  
 Z tohoto důvodu nepřesnosti, nelze spoléhat na přesné výsledky při pracovat na hodnoty s plovoucí desetinnou čárkou. Konkrétně se dvě hodnoty, které jsou si rovny teoreticky může mít mírně odlišné reprezentace.  
  
| K porovnání s plovoucí desetinnou čárkou množství | 
|---| 
|1.  Vypočítá absolutní hodnotu jejich rozdíl pomocí <xref:System.Math.Abs%2A> metodu <xref:System.Math> třídy v <xref:System> oboru názvů.<br />2.  Určení přijatelné maximální rozdíl, tak, aby měli zvážit dva množství musí rovnat pro praktické účely, pokud je jejich rozdíl větší.<br />3.  Porovnejte absolutní hodnota rozdílu na přijatelné rozdíl.|  
  
 Následující příklad ukazuje správná i nesprávná porovnání dvou `Double` hodnoty.  
  
 [!code-vb[VbVbalrDataTypes#10](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/troubleshooting-data-types_1.vb)]  
  
 V předchozím příkladu se používá <xref:System.Double.ToString%2A> metodu <xref:System.Double> struktury tak, aby ho můžete zadat vyšší přesností než `CStr` používá klíčové slovo. Výchozí hodnota je 15 číslic, ale to formát "G17" rozšiřuje na 17 číslic.  
  
## <a name="mod-operator-does-not-return-accurate-result"></a>Mod – operátor nevrátí přesné výsledky  
 Z důvodu nepřesnosti úložiště, s plovoucí desetinnou čárkou [Mod operátor](../../../../visual-basic/language-reference/operators/mod-operator.md) může vrátit neočekávaný výsledek v případě alespoň jeden z operandů s plovoucí desetinnou čárkou.  
  
 [Datový typ Decimal](../../../../visual-basic/language-reference/data-types/decimal-data-type.md) nepoužívá reprezentace plovoucí desetinné čárky. Mnoha čísla, která jsou nepřesné v `Single` a `Double` jsou přesné v `Decimal` (například 0.2 a 0.3). I když aritmetické je pomalejší v `Decimal` než v plovoucí desetinné čárky, může být vhodné ke snížení výkonu, abyste dosáhli vyšší přesnost.  
  
|Chcete-li najít zbytek celé číslo s plovoucí desetinnou čárkou množství|  
|---|  
|1.  Deklarujte proměnné jako `Decimal`.<br />2.  Použít znak typu literálu `D` přinutit se `Decimal`, v případě, že jejich hodnoty jsou příliš velké `Long` datového typu.|  
  
 Následující příklad ukazuje potenciál nepřesnost operandů s plovoucí desetinnou čárkou.  
  
 [!code-vb[VbVbalrDataTypes#11](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/troubleshooting-data-types_2.vb)]  
  
 V předchozím příkladu se používá <xref:System.Double.ToString%2A> metodu <xref:System.Double> struktury tak, aby ho můžete zadat vyšší přesností než `CStr` používá klíčové slovo. Výchozí hodnota je 15 číslic, ale to formát "G17" rozšiřuje na 17 číslic.  
  
 Protože `zeroPointTwo` je `Double`, 0.2 jeho hodnotu neomezeně opakovaný binární zlomek s hodnotou uloženou v 0.20000000000000001. Vydělí toto množství 2.0 poskytuje 9.9999999999999995 s zbytek 0.19999999999999991.  
  
 Ve výrazu pro `decimalRemainder`, znak typu literálu `D` vynutí oba operandy `Decimal`, a 0.2 má přesné reprezentaci. Proto `Mod` operátor dává očekávaný zbývající 0,0.  
  
 Všimněte si, že není dostatečná k deklarování `decimalRemainder` jako `Decimal`. Také je nutné donutit literály do `Decimal`, nebo používají `Double` ve výchozím nastavení a `decimalRemainder` obdrží nepřesné stejnou hodnotu jako `doubleRemainder`.  
  
## <a name="boolean-type-does-not-convert-to-numeric-type-accurately"></a>Typ Boolean není numerický typ. přesně převádět  
 [Datový typ Boolean](../../../../visual-basic/language-reference/data-types/boolean-data-type.md) nejsou uložené hodnoty jako čísla a uložené hodnoty nejsou určeny jako ekvivalentní čísla. Z důvodu kompatibility se staršími verzemi Visual Basic poskytuje klíčová slova převodu ([funkce CType](../../../../visual-basic/language-reference/functions/ctype-function.md), `CBool`, `CInt`, a tak dále) pro převod mezi `Boolean` a číselné typy. Ale jiných jazycích někdy provádění těchto převodů odlišně, stejně jako [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] metody.  
  
 Nikdy by měl napsat kód, který závisí na ekvivalentní číselné hodnoty pro `True` a `False`. Kdykoli je to možné, byste měli omezit využití `Boolean` proměnné logické hodnoty, které jsou určeny. Jestliže musíte kombinovat `Boolean` a číselné hodnoty, ujistěte se, že rozumíte metodu převodu, který jste vybrali.  
  
### <a name="conversion-in-visual-basic"></a>Převod v jazyce Visual Basic  
 Při použití `CType` nebo `CBool` klíčová slova převodu chcete převést číselné datové typy k `Boolean`, stane 0 `False` a Staňte se všechny ostatní hodnoty `True`. Při převodu `Boolean` hodnoty pro číselné typy s použitím klíčová slova převodu `False` stane 0 a `True` stane hodnota -1.  
  
### <a name="conversion-in-the-framework"></a>V rámci převodu  
 <xref:System.Convert.ToInt32%2A> Metodu <xref:System.Convert> třídy v <xref:System> obor názvů převede `True` až + 1.  
  
 Pokud je nutné převést `Boolean` hodnota, která se číselný datový typ, buďte opatrní o způsobu převodu použijete.  
  
## <a name="character-literal-generates-compiler-error"></a>Znakový literál vygeneruje Chyba kompilátoru  
 Neexistují žádné znaky typu předpokládá Visual Basic výchozí datové typy pro literály. Výchozí typ pro literální znak – uzavřena v uvozovkách (`" "`) – je `String`.  
  
 `String` Datový typ nelze rozšířit na [Char – datový typ](../../../../visual-basic/language-reference/data-types/char-data-type.md). To znamená, že pokud chcete přiřadit literál na `Char` proměnné, musíte provést zužující převod nebo literál k vynucení `Char` typu.  

|K vytvoření znak literálu přiřadit k proměnné nebo – konstanta|
|---|  
|1.  Deklarujte proměnnou nebo konstantu jako `Char`.<br />2.  Hodnota znaku uzavřete do uvozovek (`" "`).<br />3.  Postupujte podle uzavírací dvojité uvozovky se znak typu literálu `C` přinutit literal na `Char`. To je nezbytné, pokud kontrola typu ([Option Strict – příkaz](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) je `On`, a je v každém případě žádoucí.|  
  
 Následující příklad ukazuje neúspěšných a úspěšných přiřazení literál na `Char` proměnné.  
  
 [!code-vb[VbVbalrDataTypes#12](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/troubleshooting-data-types_3.vb)]  
  
 Je vždycky riziko pomocí zužující převody, protože může selhat v době běhu. Například převod z `String` k `Char` může selhat, pokud `String` hodnota obsahuje více než jeden znak. Proto je lépe programování používat `C` znak.  
  
## <a name="string-conversion-fails-at-run-time"></a>Převod řetězce selže v době běhu  
 [Datový typ String](../../../../visual-basic/language-reference/data-types/string-data-type.md) podílí na velmi málo rozšiřující převody. `String` rozšiřuje pouze sám na sebe a `Object`a pouze `Char` a `Char()` ( `Char` pole) rozšířit na `String`. Důvodem je, že `String` proměnné a konstanty může obsahovat hodnoty, které nesmí obsahovat jiné datové typy.  
  
 Při přepnutí kontrola typu ([Option Strict – příkaz](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) je `On`, zakáže všechny implicitní zužující převody kompilátor. Jedná se o těch zahrnující `String`. Kód můžete stále použít klíčová slova převodu například `CStr` a [CType – funkce](../../../../visual-basic/language-reference/functions/ctype-function.md), které přímo [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] pokusu o převod.  
  
> [!NOTE]
>  Chyba zúžit převodu je potlačeno pro převod z prvků v `For Each…Next` kolekce řídicí proměnná smyčky for. Další informace a příklady najdete v tématu v části "Zužující převody" [For Each... Další příkaz](../../../../visual-basic/language-reference/statements/for-each-next-statement.md).  
  
### <a name="narrowing-conversion-protection"></a>Zužující převod ochrany  
 Zužující převody nevýhodou je, že může selhat v době běhu. Například pokud `String` proměnná obsahuje všechno, jiné než "True" nebo "Nepravda", nelze převést na `Boolean`. Pokud obsahuje interpunkční znaménka, převod na libovolného číselného typu se nezdaří. Pokud si nejste jisti, který vaše `String` proměnná vždy obsahuje hodnoty, které může přijmout typ cíle, by neměla zkuste převod.  
  
 Pokud je nutné převést z `String` na jiný datový typ, je nejbezpečnější postup uzavření pokus o převod [zkuste... Catch... Příkaz finally](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md). Díky tomu můžete řešit selhání za běhu.  
  
### <a name="character-arrays"></a>Znakových polí  
 Jediný `Char` a pole `Char` prvky obou rozšířit na `String`. Ale `String` nelze rozšířit na `Char()`. Převést `String` hodnota, která se `Char` pole, můžete použít <xref:System.String.ToCharArray%2A> metodu <xref:System.String?displayProperty=nameWithType> třídy.  
  
### <a name="meaningless-values"></a>Význam hodnoty  
 Obecně platí `String` hodnoty nejsou smysl v jiných datových typů a převod je vysoce umělý a nebezpečné. Kdykoli je to možné, byste měli omezit využití `String` proměnné sekvence znaků, pro které jsou určeny. By nikdy Nepsat kód, který závisí na odpovídající hodnoty v jiných typech.  
  
## <a name="see-also"></a>Viz také  
 [Datové typy](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [Znaky typu](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)  
 [Typy hodnot a odkazové typy](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [Převody typů v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [Datové typy](../../../../visual-basic/language-reference/data-types/index.md)  
 [Funkce pro převod typů](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Účinné používání datových typů](../../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
