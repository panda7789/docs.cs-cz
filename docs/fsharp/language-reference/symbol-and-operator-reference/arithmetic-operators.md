---
title: Aritmetické operátory
description: Přečtěte si o aritmetických operátorech, které F# jsou k dispozici v programovacím jazyce.
ms.date: 04/04/2018
ms.openlocfilehash: b783a0134541f11f06dde83af97676699b797da1
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630778"
---
# <a name="arithmetic-operators"></a>Aritmetické operátory

Toto téma popisuje aritmetické operátory, které jsou k F# dispozici v jazyce.

## <a name="summary-of-binary-arithmetic-operators"></a>Souhrn binárních aritmetických operátorů

Následující tabulka shrnuje binární aritmetické operátory, které jsou k dispozici pro nezabalené celočíselné typy a typy s plovoucí desetinnou čárkou.

|Binární operátor|Poznámky|
|---------------|-----|
|`+`(sčítání a plus)|Není zaškrtnuto. Možná podmínka přetečení, když se přidají čísla společně a součet překračuje maximální absolutní hodnotu podporovanou typem.|
|`-`(odčítání, mínus)|Není zaškrtnuto. Možný stav podtečení při odečtení typu bez znaménka, nebo pokud hodnoty s plovoucí desetinnou čárkou jsou příliš malé pro reprezentaci typu.|
|`*`(násobení, časy)|Není zaškrtnuto. Možná podmínka přetečení při vynásobení čísel a součin překračuje maximální absolutní hodnotu podporovanou typem.|
|`/`(dělení, děleno)|Dělení nulou nezpůsobuje <xref:System.DivideByZeroException> pro celočíselné typy. V případě typů s plovoucí desetinnou čárkou dělení nulou poskytuje speciální hodnoty `+Infinity` s plovoucí desetinnou čárkou nebo. `-Infinity` Existuje také možný stav podtečení v případě, že číslo s plovoucí desetinnou čárkou je příliš malé pro reprezentaci typu.|
|`%`(zbytek, REM)|Vrátí zbytek operace dělení. Znaménko výsledku je stejné jako znaménko prvního operandu.|
|`**`(umocněno na mocninu)|Možná podmínka přetečení, pokud výsledek překračuje maximální absolutní hodnotu pro daný typ.<br /><br />Operátor umocnění funguje pouze s typy s plovoucí desetinnou čárkou.|

## <a name="summary-of-unary-arithmetic-operators"></a>Shrnutí unárních aritmetických operátorů

Následující tabulka shrnuje unární aritmetické operátory, které jsou k dispozici pro typy integrálních a plovoucích koncových bodů.

|Unární operátor|Poznámky|
|--------------|-----|
|`+`kladný|Lze použít na jakýkoli aritmetický výraz. Nemění znaménko hodnoty.|
|`-`(negace, negativní)|Lze použít na jakýkoli aritmetický výraz. Změní znaménko hodnoty.|

Chování při přetečení nebo podtečení u integrálních typů je obtékat kolem. To způsobuje nesprávný výsledek. Přetečení celého čísla představuje potenciálně vážný problém, který může přispět k problémům se zabezpečením, když se software do účtu nepíše. Pokud se to týká vaší aplikace, zvažte použití zkontrolovaných operátorů v `Microsoft.FSharp.Core.Operators.Checked`.

## <a name="summary-of-binary-comparison-operators"></a>Souhrn binárních relačních operátorů

Následující tabulka ukazuje binární relační operátory, které jsou k dispozici pro typy integrálních a plovoucích koncových bodů. Tyto operátory vracejí hodnoty typu `bool`.

Čísla s plovoucí desetinnou čárkou by nikdy neměla být porovnána s rovností, protože reprezentace s plovoucí desetinnou čárkou IEEE nepodporuje přesnou operaci rovnosti. Dvě čísla, která lze snadno ověřit tak, aby byla shodná s kontrolou kódu, mohou mít ve skutečnosti jiné bitové reprezentace.

|Operátor|Poznámky|
|--------|-----|
|`=`(rovnost, Equals)|Toto není operátor přiřazení. Používá se pouze pro porovnání. Toto je obecný operátor.|
|`>`(je větší než)|Toto je obecný operátor.|
|`<`(menší než)|Toto je obecný operátor.|
|`>=`(je větší než nebo rovno)|Toto je obecný operátor.|
|`<=`(je menší než nebo rovno)|Toto je obecný operátor.|
|`<>`(není rovno)|Toto je obecný operátor.|

## <a name="overloaded-and-generic-operators"></a>Přetížené a generické operátory

Všechny operátory popsané v tomto tématu jsou definovány v oboru názvů **Microsoft. FSharp. Core. Operators** . Některé operátory jsou definovány pomocí staticky vyřešených parametrů typu. To znamená, že pro každý konkrétní typ, který pracuje s operátorem, existují jednotlivé definice. Všechny unární a binární aritmetické a bitové operátory jsou v této kategorii. Operátory porovnání jsou obecné a proto pracují s jakýmkoli typem, nikoli pouze primitivními aritmetickými typy. Typy rozlišených sjednocení a typů záznamů mají vlastní implementace, které jsou generovány F# kompilátorem. Typy tříd používají metodu <xref:System.Object.Equals%2A>.

Obecné operátory jsou přizpůsobitelné. Chcete-li přizpůsobit funkce porovnání, <xref:System.Object.Equals%2A> přepište, abyste poskytovali vlastní porovnání rovnosti a <xref:System.IComparable>potom implementujte. Rozhraní má jedinou metodu <xref:System.IComparable.CompareTo%2A> , metodu. <xref:System.IComparable?displayProperty=nameWithType>

## <a name="operators-and-type-inference"></a>Odvození operátorů a typů

Použití operátoru ve výrazu omezuje odvození typu u tohoto operátoru. Použití operátorů také zabraňuje automatické generalizaci, protože použití operátorů implikuje aritmetický typ. Pokud neexistují žádné další informace, F# kompilátor odvodí `int` jako typ aritmetických výrazů. Toto chování můžete přepsat zadáním jiného typu. Proto jsou typy argumentů `function1` a návratový typ v následujícím kódu odvozeny, které mají být `int`, ale typy pro `function2` jsou odvozeny `float`.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3501.fs)]

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace symbolů a operátorů](index.md)
- [Přetížení operátoru](../operator-overloading.md)
- [Bitové operátory](bitwise-operators.md)
- [Logické operátory](boolean-operators.md)
