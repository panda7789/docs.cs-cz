---
title: Aritmetické operátory (F#)
description: Další informace o aritmetických operátorů, které jsou k dispozici v F# programovací jazyk.
ms.date: 04/04/2018
ms.openlocfilehash: 2c0e2e25a4f79d00455d978e235e4bef16b52586
ms.sourcegitcommit: 6ae7cdd0437a32884556dd4826ca90e957b7a4e3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/06/2018
ms.locfileid: "45597424"
---
# <a name="arithmetic-operators"></a>Aritmetické operátory

Toto téma popisuje aritmetických operátorů, které jsou k dispozici v F# jazyka.

## <a name="summary-of-binary-arithmetic-operators"></a>Souhrn binární aritmetické operátory

Následující tabulka shrnuje binární aritmetických operátorů, které jsou dostupné pro instance nezabalená s plovoucí desetinnou čárkou a celočíselné typy.

|Binární operátor|Poznámky|
|---------------|-----|
|`+` (přidání, plus)|Není zaškrtnuto. Je to možné přetečení při čísla jsou navzájem sečteny a součet překračuje maximální hodnotu absolutní podporována typem.|
|`-` (odčítání, minus)|Není zaškrtnuto. Je to možné podtečení podmínka po odečtení typů bez znaménka, nebo když hodnoty s plovoucí desetinnou čárkou jsou příliš malé a nelze je reprezentovat podle typu.|
|`*` (násobení, čas)|Není zaškrtnuto. Je to možné přetečení, když jsou čísla vynásobena a produktu překračuje maximální hodnotu absolutní podporována typem.|
|`/` (dělení, dělený)|Dělení nulovou příčiny <xref:System.DivideByZeroException> pro integrální typy. U typů s plovoucí desetinnou čárkou dělení nulou nabízí zvláštní hodnoty s plovoucí desetinnou čárkou `+Infinity` nebo `-Infinity`. Je také možné podtečení podmínka když číslo s plovoucí desetinnou čárkou je příliš malá, a nelze je reprezentovat podle typu.|
|`%` (zbytek, o)|Vrátí zbytek operace dělení. Znaménko výsledku je stejný jako znaménko prvního operandu.|
|`**` (k elektrické energie z umocnění)|Je to možné přetečení při výsledek přesáhl maximální absolutní hodnota pro typ.<br /><br />Operátor umocňování funguje pouze s typy s plovoucí desetinnou čárkou.|

## <a name="summary-of-unary-arithmetic-operators"></a>Souhrn unární aritmetické operátory

Následující tabulka shrnuje unární aritmetické operátory, které jsou k dispozici pro typy s plovoucí desetinnou čárkou a integrální.

|Unární operátor|Poznámky|
|--------------|-----|
|`+` (pozitivní)|Můžete použít pro jakékoli aritmetický výraz. Znaménko hodnoty nezmění.|
|`-` (negace, negativní)|Můžete použít pro jakékoli aritmetický výraz. Změní znaménku hodnoty.|

Obtékání je chování při přetečení nebo podtečení pro integrální typy. To způsobí, že nesprávný výsledek. Přetečení celého čísla je potenciálně vážný problém, který může přispět k problémy se zabezpečením při softwaru není zapsána do účtu pro něj. Pokud je to důležité pro vaši aplikaci, zvažte použití kontrolované operátory v `Microsoft.FSharp.Core.Operators.Checked`.

## <a name="summary-of-binary-comparison-operators"></a>Souhrn binární relační operátory

V následující tabulce jsou uvedeny binární relační operátory, které jsou k dispozici pro typy s plovoucí desetinnou čárkou a integrální. Tyto operátory návratové hodnoty typu `bool`.

Čísla s plovoucí desetinnou čárkou by nikdy porovnat přímo rovnost, protože reprezentace plovoucí desetinné čárky IEEE nepodporuje operace přesné rovnosti. Dvě čísla, která se rovná zkontrolováním kódu můžete snadno ověřit ve skutečnosti může mít různé bitové reprezentace.

|Operátor|Poznámky|
|--------|-----|
|`=` (operátory rovnosti, rovná se)|Toto není operátor přiřazení. Používá se pouze pro porovnání. Toto je obecný operátor.|
|`>` (větší než)|Toto je obecný operátor.|
|`<` (méně než)|Toto je obecný operátor.|
|`>=` (větší než nebo rovno)|Toto je obecný operátor.|
|`<=` (menší než nebo rovno)|Toto je obecný operátor.|
|`<>` (není rovno)|Toto je obecný operátor.|

## <a name="overloaded-and-generic-operators"></a>Obecné a přetížené operátory

Všechny operátory jsou popsané v tomto tématu jsou definovány v **Microsoft.FSharp.Core.Operators** oboru názvů. Některé operátory jsou definovány pomocí staticky rozpoznávané parametry typu. To znamená, že jsou jednotlivé definice pro každý konkrétní typ, který funguje s operátor. Všechny jednočlenné a binární aritmetické a bitové operátory jsou v této kategorii. Operátory porovnání jsou obecné a proto fungovat s jakýmkoli typem aritmetické pouze primitivní typy. Rozlišovaná sjednocení a typy záznamů mají své vlastní vlastní implementace, které se vygenerovaly F# kompilátoru. Typy tříd pomocí metody <xref:System.Object.Equals%2A>.

Obecný operátory jsou přizpůsobitelné. Chcete-li přizpůsobit funkce porovnání, přepište <xref:System.Object.Equals%2A> poskytnout vlastní porovnání rovnosti vlastní, a potom implementovat <xref:System.IComparable>. <xref:System.IComparable?displayProperty=nameWithType> Rozhraní obsahuje jedinou metodu, <xref:System.IComparable.CompareTo%2A> metody.

## <a name="operators-and-type-inference"></a>Operátory a odvození typu

Použití operátoru ve výrazu omezí odvození typu na tento operátor. Použití operátorů zabrání také, automatická generalizace, protože použití operátorů znamená aritmetického typu. Chybí nějakých jiných informací F# kompilátor odvodí `int` jako typ aritmetických výrazech. Toto chování můžete přepsat zadáním jiného typu. Proto typy argumentů a návratový typ `function1` v následujícím kódu, které jsou odvozeny bude `int`, ale typy pro `function2` jsou odvozena jako `float`.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3501.fs)]

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace symbolů a operátorů](index.md)
- [Přetížení operátoru](../operator-overloading.md)
- [Bitové operátory](bitwise-operators.md)
- [Logické operátory](boolean-operators.md)
