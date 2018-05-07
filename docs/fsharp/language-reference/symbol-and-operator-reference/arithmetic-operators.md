---
title: Aritmetické operátory (F#)
description: 'Další informace o aritmetické operátory, které jsou k dispozici v programovací jazyk F #.'
ms.date: 04/04/2018
ms.openlocfilehash: ead0bbd7fdad528b322f99eaf0f73638f060eb51
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="arithmetic-operators"></a>Aritmetické operátory

Toto téma popisuje aritmetické operátory, které jsou k dispozici v jazyce F #.

## <a name="summary-of-binary-arithmetic-operators"></a>Souhrn binární aritmetické operátory
Následující tabulka shrnuje binární aritmetické operátory, které jsou k dispozici pro nezabalený s plovoucí desetinnou čárkou a integrální typy.

|Binární operátor|Poznámky|
|---------------|-----|
|`+` (toho, plus)|Nezaškrtnuté. Podmínku možné přetečení při čísla se sčítají a součet překračuje maximální hodnotu absolutní podporovaného typu.|
|`-` (odčítání, minus)|Nezaškrtnuté. Možné podtečení podmínek, když jsou odečítat typy bez znaménka, nebo když hodnoty s plovoucí desetinnou čárkou jsou příliš malé a nelze podle typu.|
|`*` (násobení, časy)|Nezaškrtnuté. Možné přetečení podmínku, když se násobí čísla a produktu přesahuje maximální hodnotu absolutní podporovaného typu.|
|`/` (dělení dělený)|Dělení nulové příčiny <xref:System.DivideByZeroException> pro integrální typy. Pro typy s plovoucí desetinnou čárkou, dělení nulou vám dává speciální hodnoty s plovoucí desetinnou čárkou `+Infinity` nebo `-Infinity`. Je zde také možné podtečení podmínku po příliš malé a nelze podle typu číslo s plovoucí desetinnou čárkou.|
|`%` (zbývající, rem)|Vrátí zbytek operace dělení. Znaménko výsledek je stejný jako znaménko první operand.|
|`**` (exponentem umocnění)|Pokud výsledek překročí maximální absolutní hodnota pro typ možné přetečení podmínka.<br /><br />Exponenciální operátor funguje jenom s typy s plovoucí desetinnou čárkou.|

## <a name="summary-of-unary-arithmetic-operators"></a>Souhrn unární aritmetické operátory
Následující tabulka shrnuje unární aritmetické operátory, které jsou k dispozici pro typy integrální a s plovoucí desetinnou čárkou.


|Unární operátor|Poznámky|
|--------------|-----|
|`+` (kladné)|Můžete použít na jakýkoli aritmetické výraz. Nezmění přihlašovací hodnoty.|
|`-` (negace, záporné)|Můžete použít na jakýkoli aritmetické výraz. Změní přihlašovací hodnoty.|
Chování při přetečení nebo podtečení pro integrální typy je obtékat kolem. To způsobí, že nesprávný výsledek. Celé číslo přetečení je potenciálně vážný problém, který může přispívat k problémy se zabezpečením při softwaru zapisuje na účet pro ni. Pokud se jedná o problém pro vaši aplikaci, zvažte použití zaškrtnuté operátory v `Microsoft.FSharp.Core.Operators.Checked`.


## <a name="summary-of-binary-comparison-operators"></a>Souhrn operátorů binární porovnání
V následující tabulce jsou binární porovnání operátory, které jsou k dispozici pro typy integrální a s plovoucí desetinnou čárkou. Tyto operátory návratové hodnoty typu `bool`.

Čísla s plovoucí desetinnou čárkou nikdy se porovná přímo rovnosti, protože reprezentace plovoucí desetinné čárky IEEE nepodporuje operace přesný rovnosti. Dvě čísla, která můžete snadno ověřit si rovny zkontrolováním kód ve skutečnosti pravděpodobně různých bitových reprezentace.



|Operátor|Poznámky|
|--------|-----|
|`=` (rovnosti, rovná)|Toto není operátor přiřazení. Používá se pouze pro porovnání. Toto je obecná operátor.|
|`>` (větší než)|Toto je obecná operátor.|
|`<` (méně než)|Toto je obecná operátor.|
|`>=` (větší než nebo rovno)|Toto je obecná operátor.|
|`<=` (menší než nebo rovno)|Toto je obecná operátor.|
|`<>` (není rovno)|Toto je obecná operátor.|

## <a name="overloaded-and-generic-operators"></a>Operátory přetížené a obecná
Všechny operátory popsané v tomto tématu jsou definovány v **Microsoft.FSharp.Core.Operators** oboru názvů. Některé operátory jsou definované za použití parametry typu určené statisticky. To znamená, že jsou jednotlivé definice pro každý konkrétní typ, který funguje s Tento operátor. Všechny unární a binární aritmetické a bitové operátory jsou v této kategorii. Operátory porovnání obecné a proto fungovat s žádným typem aritmetické jenom primitivní typy. Rozlišovaná sjednocení a typy záznamů mají své vlastní vlastní implementací, které jsou generovány nástrojem kompilátor jazyka F #. Typy tříd, použijte metodu <xref:System.Object.Equals%2A>.

Obecné operátory lze přizpůsobit. Chcete-li přizpůsobit porovnání funkcí, přepište <xref:System.Object.Equals%2A> zadejte vlastní porovnání rovnosti vlastní, a potom implementovat <xref:System.IComparable>. <xref:System.IComparable?displayProperty=nameWithType> Rozhraní obsahuje jedinou metodu, <xref:System.IComparable.CompareTo%2A> metoda.


## <a name="operators-and-type-inference"></a>Operátory a odvození typu
Použití operátoru ve výrazu omezí odvození typu na tento operátor. Použití operátorů zabrání také, automatická generalizace, protože typ aritmetické znamená použití operátorů. Při absenci dalších informací, kompilátor jazyka F # odvodí `int` jako typ aritmetických výrazech. Toto chování můžete přepsat zadáním jiného typu. Proto typy argumentů a návratový typ `function1` v následujícím kódu jsou odvodit být `int`, ale typy pro `function2` jsou odvodit být `float`.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3501.fs)]
    
## <a name="see-also"></a>Viz také
[Referenční dokumentace symbolů a operátorů](index.md)

[Přetížení operátoru](../operator-overloading.md)

[Bitové operátory](bitwise-operators.md)

[Logické operátory](boolean-operators.md)
