---
title: Řešení potíží s datovými typy
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
ms.openlocfilehash: 239e1c2f908a9023aeca6e92aff4633b60f27b69
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84393400"
---
# <a name="troubleshooting-data-types-visual-basic"></a>Řešení potíží s datovými typy (Visual Basic)

Tato stránka obsahuje některé běžné problémy, které mohou nastat při provádění operací na vnitřních datových typech.

## <a name="floating-point-expressions-do-not-compare-as-equal"></a>Výrazy s plovoucí desetinnou čárkou se nerovnávají stejně jako stejné

Když pracujete s čísly s plovoucí desetinnou čárkou ([datový typ s jedním datovým typem](../../../language-reference/data-types/single-data-type.md) a [dvojitým datovým typem](../../../language-reference/data-types/double-data-type.md)), pamatujte, že jsou uloženy jako binární zlomky. To znamená, že nemohou uchovávat přesnou reprezentaci žádného množství, které není binární zlomek (z formuláře k/(2 ^ n), kde k a n jsou celá čísla). Například 0,5 (= 1/2) a 0,3125 (= 5/16) lze uchovávat jako přesné hodnoty, zatímco 0,2 (= 1/5) a 0,3 (= 3/10) mohou být pouze aproximace.

Z důvodu této nepřesnosti nelze při provozování hodnot s plovoucí desetinnou čárkou spoléhat na přesné výsledky. Zejména dvě hodnoty, které jsou teoreticky stejné, mohou mít mírně odlišné reprezentace.

| Porovnání množství s plovoucí desetinnou čárkou |
|---|
|1. Vypočítejte absolutní hodnotu jejich rozdílu pomocí <xref:System.Math.Abs%2A> metody <xref:System.Math> třídy v <xref:System> oboru názvů.<br />2. Určete přijatelný maximální rozdíl, aby bylo možné považovat dvě množství za praktické účely, pokud jejich rozdíl není větší.<br />3. Porovnejte absolutní hodnotu rozdílu s přijatelným rozdílem.|

Následující příklad ukazuje nesprávné a správné porovnání dvou `Double` hodnot.

[!code-vb[VbVbalrDataTypes#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#10)]

Předchozí příklad používá <xref:System.Double.ToString%2A> metodu <xref:System.Double> struktury tak, aby mohla určovat lepší přesnost, než `CStr` klíčové slovo používá. Výchozí hodnota je 15 číslic, ale formát "G17" ho rozšiřuje na 17 číslic.

## <a name="mod-operator-does-not-return-accurate-result"></a>Operátor mod nevrací přesný výsledek.

Z důvodu nepřesnosti úložiště s plovoucí desetinnou čárkou může [operátor mod](../../../language-reference/operators/mod-operator.md) vracet neočekávaný výsledek, pokud je alespoň jeden z operandů plovoucí desetinné čárky.

[Datový typ Decimal](../../../language-reference/data-types/decimal-data-type.md) nepoužívá reprezentaci s plovoucí desetinnou čárkou. Mnoho čísel, která jsou nepřesné v `Single` a `Double` jsou přesně v nástroji `Decimal` (například 0,2 a 0,3). I když aritmetická operace je pomalejší `Decimal` než v pohyblivé řádové čárce, může to znamenat snížení výkonu za účelem dosažení lepší přesnosti.

|Vyhledání celého čísla zbytku množství s plovoucí desetinnou čárkou|
|---|
|1. deklarujte proměnné jako `Decimal` .<br />2. pomocí znaku literálového typu `D` vynutíte literály pro `Decimal` případ, že jejich hodnoty jsou pro `Long` datový typ příliš velké.|

Následující příklad ukazuje potenciální nepřesnost operandů s plovoucí desetinnou čárkou.

[!code-vb[VbVbalrDataTypes#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#11)]

Předchozí příklad používá <xref:System.Double.ToString%2A> metodu <xref:System.Double> struktury tak, aby mohla určovat lepší přesnost, než `CStr` klíčové slovo používá. Výchozí hodnota je 15 číslic, ale formát "G17" ho rozšiřuje na 17 číslic.

Vzhledem k tomu `zeroPointTwo` `Double` , že jeho hodnota pro 0,2 je nekonečně opakující se binární zlomek s uloženou hodnotou 0.20000000000000001. Rozdělení 2,0 tímto množstvím vrátí 9.9999999999999995 se zbytkem 0.19999999999999991.

Ve výrazu pro `decimalRemainder` , literální znak typu `D` vynutí oba operandy `Decimal` , a 0,2 má přesnou reprezentaci. Proto `Mod` operátor vypočítá očekávanou zbývající část 0,0.

Všimněte si, že není dostačující deklarovat `decimalRemainder` jako `Decimal` . Musíte taky vynutit literály `Decimal` nebo použít `Double` ve výchozím nastavení a `decimalRemainder` stejnou nepřesnou hodnotu jako `doubleRemainder` .

## <a name="boolean-type-does-not-convert-to-numeric-type-accurately"></a>Typ Boolean se přesně nepřevádí na číselný typ.

[Logické hodnoty datového typu](../../../language-reference/data-types/boolean-data-type.md) nejsou uloženy jako čísla a uložené hodnoty nejsou určeny pro ekvivalent čísel. Pro zajištění kompatibility se staršími verzemi Visual Basic poskytuje klíčová slova převodu ([funkce CType](../../../language-reference/functions/ctype-function.md),, `CBool` `CInt` a tak dále) pro převod mezi `Boolean` a číselnými typy. Nicméně jiné jazyky někdy provádějí tyto převody odlišně, stejně jako .NET Framework metody.

Nikdy byste neměli psát kód, který spoléhá na ekvivalentní číselné hodnoty pro `True` a `False` . Kdykoli je to možné, měli byste omezit použití `Boolean` proměnných na logické hodnoty, pro které jsou navrženy. Pokud musíte kombinovat `Boolean` a číselné hodnoty, ujistěte se, že rozumíte metodě převodu, kterou jste vybrali.

### <a name="conversion-in-visual-basic"></a>Převod v Visual Basic

Když použijete `CType` `CBool` klíčová slova pro převod nebo k převodu číselných datových typů na `Boolean` hodnotu, 0 se stane a zobrazí se `False` všechny ostatní hodnoty `True` . Při převodu `Boolean` hodnot na číselné typy pomocí klíčových slov převodu se hodnota `False` 0 a `True` nastanou na 1.

### <a name="conversion-in-the-framework"></a>Převod v rozhraní .NET Framework

<xref:System.Convert.ToInt32%2A>Metoda <xref:System.Convert> třídy v <xref:System> oboru názvů se převede `True` na + 1.

Pokud je nutné převést `Boolean` hodnotu na číselný datový typ, buďte opatrní na to, kterou metodu převodu používáte.

## <a name="character-literal-generates-compiler-error"></a>Znakový literál generuje chybu kompilátoru.

Při absenci žádných typů znaků Visual Basic předpokládá výchozí datové typy pro literály. Výchozí typ pro znakový literál – uzavřený v uvozovkách ( `" "` ) – je `String` .

`String`Datový typ nerozšiřuje [datový typ char](../../../language-reference/data-types/char-data-type.md). To znamená, že pokud chcete proměnné přiřadit literál `Char` , musíte buď provést zužující převod, nebo vynutit literál pro `Char` typ.

|Vytvoření literálu znaku pro přiřazení proměnné nebo konstantě|
|---|
|1. deklarujte proměnnou nebo konstantu jako `Char` .<br />2. Uzavřete hodnotu znaku do uvozovek ( `" "` ).<br />3. postupujte podle uzavírací dvojité uvozovky znakem literálového typu `C` k vynucení literálu `Char` . To je nezbytné v případě, že přepínač pro kontrolu typu ([Option Strict](../../../language-reference/statements/option-strict-statement.md)) je `On` a je v každém případě žádoucí.|

Následující příklad ukazuje neúspěšná a úspěšná přiřazení literálu `Char` proměnné.

[!code-vb[VbVbalrDataTypes#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#12)]

Použití zužujících převodů vždy představuje riziko, protože v době běhu může selhat. Například převod z `String` na na `Char` může selhat, pokud `String` hodnota obsahuje více než jeden znak. Proto je lepší programování pro použití `C` znaku typu.

## <a name="string-conversion-fails-at-run-time"></a>Převod řetězce v době běhu se nezdařil.

[Datový typ String](../../../language-reference/data-types/string-data-type.md) se účastní několika rozšiřujících převodů. `String`rozšiřuje se pouze na sebe sama a a a `Object` `Char` `Char()` ( `Char` pole) rozšiřuje na `String` . Důvodem je `String` , že proměnné a konstanty mohou obsahovat hodnoty, které nemohou obsahovat jiné datové typy.

Když je přepínač pro kontrolu typu ([Option Strict](../../../language-reference/statements/option-strict-statement.md)) `On` , kompilátor zakáže všechny implicitní zužující převody. To zahrnuje i ty, které se týkají `String` . Váš kód může stále používat klíčová slova pro převod, jako je `CStr` [funkce a CType](../../../language-reference/functions/ctype-function.md), které nasměrují .NET Framework k pokusu o převod.

> [!NOTE]
> Chyba zužujícího převodu je potlačena pro převody z prvků v `For Each…Next` kolekci na řídicí proměnnou smyčky. Další informace a příklady najdete v části "zužující převody" v tématu.. [. Další příkaz](../../../language-reference/statements/for-each-next-statement.md).

### <a name="narrowing-conversion-protection"></a>Zúžení ochrany před převodem

Nevýhodou zužujících převodů je, že v době běhu mohou selhat. Například pokud `String` proměnná obsahuje cokoli jiného než "true" nebo "false", nelze ji převést na `Boolean` . Pokud obsahuje interpunkční znaménka, převod na libovolný číselný typ se nezdařil. Pokud si nejste jisti, že `String` Proměnná vždy obsahuje hodnoty, které může cílový typ přijmout, neměli byste zkoušet převod.

Pokud je nutné převést z `String` na jiný datový typ, nejbezpečnější postup je uzavřít pokus o převod do [Try... Zachytit... Finally – příkaz](../../../language-reference/statements/try-catch-finally-statement.md). To vám umožní pracovat s chybou za běhu.

### <a name="character-arrays"></a>Pole znaků

Jedno `Char` a pole `Char` prvků se rozšíří na `String` . Nerozšiřuje `String` se však na `Char()` . Chcete-li převést `String` hodnotu na `Char` pole, můžete použít <xref:System.String.ToCharArray%2A> metodu <xref:System.String?displayProperty=nameWithType> třídy.

### <a name="meaningless-values"></a>Nevýznamové hodnoty

Obecně platí, že `String` hodnoty nejsou smysluplné v jiných datových typech a převod je vysoce umělý a nebezpečný. Kdykoli je to možné, měli byste omezit použití `String` proměnných na sekvence znaků, pro které jsou navrženy. Nikdy byste neměli psát kód, který závisí na ekvivalentních hodnotách v jiných typech.

## <a name="see-also"></a>Viz také

- [Datové typy](index.md)
- [Znaky typu](type-characters.md)
- [Typy hodnot a typy odkazu](value-types-and-reference-types.md)
- [Převody typů v jazyce Visual Basic](type-conversions.md)
- [Datové typy](../../../language-reference/data-types/index.md)
- [Funkce pro převod typů](../../../language-reference/functions/type-conversion-functions.md)
- [Účinné používání datových typů](efficient-use-of-data-types.md)
