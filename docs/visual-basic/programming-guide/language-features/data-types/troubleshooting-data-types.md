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
ms.openlocfilehash: 5b2cb0d5270b7e14c3462aeaf54942f939511fd7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933236"
---
# <a name="troubleshooting-data-types-visual-basic"></a>Řešení potíží s datovými typy (Visual Basic)
Tato stránka obsahuje některé běžné problémy, které mohou nastat při provádění operací na vnitřních datových typech.  
  
## <a name="floating-point-expressions-do-not-compare-as-equal"></a>Výrazy s plovoucí desetinnou čárkou se nerovnávají stejně jako stejné  
 Když pracujete s čísly s plovoucí desetinnou čárkou ([datový typ s jedním datovým typem](../../../../visual-basic/language-reference/data-types/single-data-type.md) a [dvojitým datovým typem](../../../../visual-basic/language-reference/data-types/double-data-type.md)), pamatujte, že jsou uloženy jako binární zlomky. To znamená, že nemohou uchovávat přesnou reprezentaci žádného množství, které není binární zlomek (z formuláře k/(2 ^ n), kde k a n jsou celá čísla). Například 0,5 (= 1/2) a 0,3125 (= 5/16) lze uchovávat jako přesné hodnoty, zatímco 0,2 (= 1/5) a 0,3 (= 3/10) mohou být pouze aproximace.  
  
 Z důvodu této nepřesnosti nelze při provozování hodnot s plovoucí desetinnou čárkou spoléhat na přesné výsledky. Zejména dvě hodnoty, které jsou teoreticky stejné, mohou mít mírně odlišné reprezentace.  
  
| Porovnání množství s plovoucí desetinnou čárkou | 
|---| 
|1.  Vypočítá absolutní hodnotu jejich rozdílu pomocí <xref:System.Math.Abs%2A> metody <xref:System.Math> třídy v <xref:System> oboru názvů.<br />2.  Určete přijatelný maximální rozdíl, aby bylo možné považovat dvě množství za praktické účely, pokud jejich rozdíl není větší.<br />3.  Porovná absolutní hodnotu rozdílu s přijatelným rozdílem.|  
  
 Následující příklad ukazuje nesprávné a správné porovnání dvou `Double` hodnot.  
  
 [!code-vb[VbVbalrDataTypes#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#10)]  
  
 Předchozí příklad používá <xref:System.Double.ToString%2A> metodu <xref:System.Double> struktury tak, aby mohla `CStr` určovat lepší přesnost, než klíčové slovo používá. Výchozí hodnota je 15 číslic, ale formát "G17" ho rozšiřuje na 17 číslic.  
  
## <a name="mod-operator-does-not-return-accurate-result"></a>Operátor mod nevrací přesný výsledek.  
 Z důvodu nepřesnosti úložiště s plovoucí desetinnou čárkou může [operátor mod](../../../../visual-basic/language-reference/operators/mod-operator.md) vracet neočekávaný výsledek, pokud je alespoň jeden z operandů plovoucí desetinné čárky.  
  
 [Datový typ Decimal](../../../../visual-basic/language-reference/data-types/decimal-data-type.md) nepoužívá reprezentaci s plovoucí desetinnou čárkou. Mnoho čísel, která jsou nepřesné `Double` v `Single` a jsou `Decimal` přesně v nástroji (například 0,2 a 0,3). I když aritmetická operace `Decimal` je pomalejší než v pohyblivé řádové čárce, může to znamenat snížení výkonu za účelem dosažení lepší přesnosti.  
  
|Vyhledání celého čísla zbytku množství s plovoucí desetinnou čárkou|  
|---|  
|1.  Deklarujte proměnné `Decimal`jako.<br />2.  Použijte znak `D` literálového typu k vynucení literálů `Decimal`pro, pro případ, že jejich hodnoty `Long` jsou pro datový typ příliš velké.|  
  
 Následující příklad ukazuje potenciální nepřesnost operandů s plovoucí desetinnou čárkou.  
  
 [!code-vb[VbVbalrDataTypes#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#11)]  
  
 Předchozí příklad používá <xref:System.Double.ToString%2A> metodu <xref:System.Double> struktury tak, aby mohla `CStr` určovat lepší přesnost, než klíčové slovo používá. Výchozí hodnota je 15 číslic, ale formát "G17" ho rozšiřuje na 17 číslic.  
  
 Vzhledem k tomu `zeroPointTwo`,že jeho hodnota pro 0,2 je nekonečně opakující se binární zlomek s uloženou hodnotou 0.20000000000000001. `Double` Rozdělení 2,0 tímto množstvím vrátí 9.9999999999999995 se zbytkem 0.19999999999999991.  
  
 Ve výrazu pro `decimalRemainder`, literální znak `D` typu `Decimal`vynutí oba operandy, a 0,2 má přesnou reprezentaci. `Mod` Proto operátor vypočítá očekávanou zbývající část 0,0.  
  
 Všimněte si, že není dostačující deklarovat `decimalRemainder` jako. `Decimal` `Decimal`Musíte taky vynutit literály nebo použít `Double` ve výchozím nastavení a `decimalRemainder` stejnou nepřesnou hodnotu jako `doubleRemainder`.  
  
## <a name="boolean-type-does-not-convert-to-numeric-type-accurately"></a>Typ Boolean se přesně nepřevádí na číselný typ.  
 [Logické hodnoty datového typu](../../../../visual-basic/language-reference/data-types/boolean-data-type.md) nejsou uloženy jako čísla a uložené hodnoty nejsou určeny pro ekvivalent čísel. Pro zajištění kompatibility se staršími verzemi Visual Basic poskytuje klíčová slova převodu ( `CBool`[funkce CType](../../../../visual-basic/language-reference/functions/ctype-function.md), `CInt`, a tak dále) pro `Boolean` převod mezi a číselnými typy. Nicméně jiné jazyky někdy provádějí tyto převody odlišně, stejně jako .NET Framework metody.  
  
 Nikdy byste neměli psát kód, který spoléhá na ekvivalentní číselné hodnoty `True` pro `False`a. Kdykoli je to možné, měli byste omezit `Boolean` použití proměnných na logické hodnoty, pro které jsou navrženy. Pokud musíte kombinovat `Boolean` a číselné hodnoty, ujistěte se, že rozumíte metodě převodu, kterou jste vybrali.  
  
### <a name="conversion-in-visual-basic"></a>Převod v Visual Basic  
 `CType` Když použijete klíčová `CBool` slova pro převod nebo k převodu číselných `Boolean`datových typů na `False` hodnotu `True`, 0 se stane a zobrazí se všechny ostatní hodnoty. Při převodu `Boolean` hodnot na číselné typy pomocí `False` klíčových slov převodu se hodnota 0 a `True` nastanou na 1.  
  
### <a name="conversion-in-the-framework"></a>Převod v rozhraní .NET Framework  
 Metoda třídy v `True` oboru názvů se převede na + 1. <xref:System> <xref:System.Convert> <xref:System.Convert.ToInt32%2A>  
  
 Pokud je nutné převést `Boolean` hodnotu na číselný datový typ, buďte opatrní na to, kterou metodu převodu používáte.  
  
## <a name="character-literal-generates-compiler-error"></a>Znakový literál generuje chybu kompilátoru.  
 Při absenci žádných typů znaků Visual Basic předpokládá výchozí datové typy pro literály. Výchozí typ pro znakový literál – uzavřený v uvozovkách (`" "`) – je. `String`  
  
 Datový typ nerozšiřuje [datový typ char.](../../../../visual-basic/language-reference/data-types/char-data-type.md) `String` To znamená, že pokud chcete `Char` proměnné přiřadit literál, musíte buď provést zužující převod, nebo vynutit literál `Char` pro typ.  

|Vytvoření literálu znaku pro přiřazení proměnné nebo konstantě|
|---|  
|1.  Deklarujte proměnnou nebo konstantu `Char`jako.<br />2.  Uzavřete hodnotu znaku do uvozovek (`" "`).<br />3.  Použijte uzavírací dvojitou uvozovku pomocí znaku `C` literálového typu k vynucení `Char`literálu. To je nezbytné v případě, že přepínač pro kontrolu typu ([Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) je `On`a je v každém případě žádoucí.|  
  
 Následující příklad ukazuje neúspěšná a úspěšná přiřazení literálu `Char` proměnné.  
  
 [!code-vb[VbVbalrDataTypes#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#12)]  
  
 Použití zužujících převodů vždy představuje riziko, protože v době běhu může selhat. Například převod z `String` na na `Char` může selhat, pokud `String` hodnota obsahuje více než jeden znak. Proto je lepší programování pro použití `C` znaku typu.  
  
## <a name="string-conversion-fails-at-run-time"></a>Převod řetězce v době běhu se nezdařil.  
 [Datový typ String](../../../../visual-basic/language-reference/data-types/string-data-type.md) se účastní několika rozšiřujících převodů. `String`rozšiřuje se pouze na sebe sama `Object`a `Char` `Char()` a a ( `Char` pole) rozšiřuje na `String`. Důvodem je `String` , že proměnné a konstanty mohou obsahovat hodnoty, které nemohou obsahovat jiné datové typy.  
  
 Když je `On`přepínač pro kontrolu typu ([Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)), kompilátor zakáže všechny implicitní zužující převody. To zahrnuje i ty `String`, které se týkají. Váš kód může stále používat klíčová slova pro `CStr` převod, jako je [funkce a CType](../../../../visual-basic/language-reference/functions/ctype-function.md), které nasměrují .NET Framework k pokusu o převod.  
  
> [!NOTE]
> Chyba zužujícího převodu je potlačena pro převody z prvků v `For Each…Next` kolekci na řídicí proměnnou smyčky. Další informace a příklady najdete v části "zužující převody" v tématu.. [. Další příkaz](../../../../visual-basic/language-reference/statements/for-each-next-statement.md).  
  
### <a name="narrowing-conversion-protection"></a>Zúžení ochrany před převodem  
 Nevýhodou zužujících převodů je, že v době běhu mohou selhat. Například pokud `String` proměnná obsahuje cokoli jiného než "true" nebo "false", nelze ji převést na `Boolean`. Pokud obsahuje interpunkční znaménka, převod na libovolný číselný typ se nezdařil. Pokud si nejste jisti `String` , že proměnná vždy obsahuje hodnoty, které může cílový typ přijmout, neměli byste zkoušet převod.  
  
 Pokud je nutné převést z `String` na jiný datový typ, nejbezpečnější postup je uzavřít pokus o převod do [Try... Zachytit... Finally – příkaz](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md). To vám umožní pracovat s chybou za běhu.  
  
### <a name="character-arrays"></a>Pole znaků  
 Jedno `Char` a `String`pole prvků se rozšíří na. `Char` Nerozšiřuje se však na `Char()`. `String` Chcete-li `String` převést hodnotu `Char` na pole <xref:System.String.ToCharArray%2A> , můžete <xref:System.String?displayProperty=nameWithType> použít metodu třídy.  
  
### <a name="meaningless-values"></a>Nevýznamové hodnoty  
 Obecně platí, `String` že hodnoty nejsou smysluplné v jiných datových typech a převod je vysoce umělý a nebezpečný. Kdykoli je to možné, měli byste omezit `String` použití proměnných na sekvence znaků, pro které jsou navrženy. Nikdy byste neměli psát kód, který závisí na ekvivalentních hodnotách v jiných typech.  
  
## <a name="see-also"></a>Viz také:

- [Datové typy](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Znaky typu](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
- [Typy hodnot a odkazové typy](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [Převody typu v Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [Datové typy](../../../../visual-basic/language-reference/data-types/index.md)
- [Funkce pro převod typů](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Účinné používání datových typů](../../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
