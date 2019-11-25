---
title: Postup porovnání řetězců – C# Průvodce
description: Přečtěte si, jak porovnat a seřadit řetězcové hodnoty s použitím nebo bez případu s použitím řazení konkrétní jazykové verze nebo bez něj.
ms.date: 10/03/2018
helpviewer_keywords:
- strings [C#], comparison
- comparing strings [C#]
ms.openlocfilehash: dda3ec8cb6a0131867e6ea3bb0cf7199d86058ff
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73973324"
---
# <a name="how-to-compare-strings-in-c"></a>Jak porovnat řetězce v jazyce C\#

Porovnáte řetězce, abyste odpověděli na jednu ze dvou otázek: "jsou tyto dva řetězce stejné?" nebo "v jakém pořadí mají být tyto řetězce umístěny při jejich řazení?"

Tyto dvě otázky jsou složité faktory, které ovlivňují porovnávání řetězců:

- Můžete zvolit ordinální nebo jazykové porovnání.
- Můžete si vybrat, jestli se jedná o případové věci.
- Můžete zvolit porovnání specifické pro jazykovou verzi.
- Jazykové porovnání představují jazykovou verzi a závislé na platformě.

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

Při porovnávání řetězců definujete mezi nimi objednávku. K řazení posloupnosti řetězců slouží porovnávání. Jakmile je sekvence ve známém pořadí, je snazší hledat jak pro software, tak pro lidi. Jiné porovnání mohou kontrolovat, zda jsou řetězce stejné. Tyto sameness kontroly jsou podobné rovnosti, ale některé rozdíly, například rozdíly v různých velikostech, mohou být ignorovány.

## <a name="default-ordinal-comparisons"></a>Výchozí ordinální porovnávání

Standardně nejběžnější operace:

- <xref:System.String.CompareTo%2A?displayProperty=nameWithType>
- <xref:System.String.Equals%2A?displayProperty=nameWithType>
- <xref:System.String.op_Equality%2A?displayProperty=nameWithType> a <xref:System.String.op_Inequality%2A?displayProperty=nameWithType>, to znamená, [operátory rovnosti `==` a `!=`](../language-reference/operators/equality-operators.md#string-equality), v uvedeném pořadí.

provede porovnávání v řádu rozlišující velká a malá písmena a v případě potřeby použije aktuální jazykovou verzi. Následující příklad ukazuje, že:

[!code-csharp-interactive[Comparing strings using an ordinal comparison](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#1)]

Výchozí ordinální porovnávání při porovnávání řetězců nebere v úvahu jazyková pravidla. Porovnává binární hodnotu každého objektu <xref:System.Char> ve dvou řetězcích. V důsledku toho výchozí ordinální porovnávání rozlišuje i velká a malá písmena.

Všimněte si, že test rovnosti s <xref:System.String.Equals%2A?displayProperty=nameWithType> a operátory `==` a `!=` se liší od porovnání řetězců pomocí metod <xref:System.String.CompareTo%2A?displayProperty=nameWithType> a <xref:System.String.Compare(System.String,System.String)?displayProperty=nameWithType)>. I když testy rovnosti provádějí ordinální porovnávání rozlišující velká a malá písmena, metody porovnání provádějí porovnání zohledňující velká a malá písmena s použitím aktuální jazykové verze. Vzhledem k tomu, že výchozí metody porovnání často provádějí různé typy porovnávání, doporučujeme, abyste vždy vymazali záměr kódu tím, že zavoláte přetížení, které explicitně určuje typ porovnání, které má být provedeno.

## <a name="case-insensitive-ordinal-comparisons"></a>Ordinální porovnávání bez rozlišení velkých a malých písmen

Metoda <xref:System.String.Equals(System.String,System.StringComparison)?displayProperty=nameWithType> umožňuje zadat hodnotu <xref:System.StringComparison> <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType>.
pro ordinální porovnávání bez rozlišování velkých a malých písmen. K dispozici je také statická metoda <xref:System.String.Compare(System.String,System.String,System.StringComparison)?displayProperty=nameWithType>, která provádí porovnávání bez rozlišení velkých a malých písmen, pokud zadáte hodnotu <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> pro argument <xref:System.StringComparison>. Jsou uvedeny v následujícím kódu:

[!code-csharp-interactive[Comparing strings ignoring case](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#2)]

Při porovnávání podle pořadového čísla bez rozlišení velkých a malých písmen tyto metody používají konvence pro používání velkých a malých písmen v [neutrální jazykové verzi](xref:System.Globalization.CultureInfo.InvariantCulture).

## <a name="linguistic-comparisons"></a>Jazyková porovnání

Řetězce lze také seřadit pomocí lingvistických pravidel pro aktuální jazykovou verzi.
Někdy se označuje jako "pořadí řazení slov". Pokud provedete jazykové porovnání, některé nealfanumerické znaky Unicode mohou mít přiřazeny zvláštní váhy. Například spojovník "-" může mít přiřazenu velmi malou váhu, aby se "Co-op" a "Coop" zobrazovaly vedle sebe v pořadí řazení. Kromě toho může být několik znaků Unicode ekvivalentní sekvenci <xref:System.Char> instancí. Následující příklad používá frázi "ty se roztancoval na ulici". v němčině s "SS" (U + 0073 U + 0073) v jednom řetězci a "ß" (U + 00DF) v jiném. V jazyku (ve Windows) se "SS" rovná Esszet německému znaku: "ß" v jazykových verzích "en-US" i "de-DE".

[!code-csharp-interactive[Comparing strings using linguistic rules](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#3)]

Tato ukázka demonstruje charakter jazykových porovnávání závislých na operačním systému. Hostitelem pro interaktivní okno je hostitel Linux. Jazykové a ordinální porovnávání vytváří stejné výsledky. Pokud jste spustili stejnou ukázku na hostiteli Windows, zobrazí se následující výstup:

```console
<coop> is less than <co-op> using invariant culture
<coop> is greater than <co-op> using ordinal comparison
<coop> is less than <cop> using invariant culture
<coop> is less than <cop> using ordinal comparison
<co-op> is less than <cop> using invariant culture
<co-op> is less than <cop> using ordinal comparison
```

V systému Windows se pořadí řazení "COP", "Coop" a "Co-op" mění při změně z lingvistového porovnání na ordinální porovnávání. Dvě německé věty také porovnávají odlišně pomocí různých typů porovnání.

## <a name="comparisons-using-specific-cultures"></a>Porovnání pomocí konkrétní jazykové verze

Tento příklad ukládá objekty <xref:System.Globalization.CultureInfo> pro kultury en-US a de-DE.
Porovnávání se provádí pomocí objektu <xref:System.Globalization.CultureInfo> k zajištění porovnání specifického pro jazykovou verzi.

Použitá jazyková verze má vliv na jazyková porovnání. Následující příklad ukazuje výsledky porovnání dvou německých vět pomocí jazykové verze "en-US" a jazykové verze de-DE ":

[!code-csharp-interactive[Comparing strings across cultures](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#4)]

Porovnávání závislé na jazykové verzi se obvykle používá k porovnání a řazení vstupu řetězců uživateli s jinými řetězci, které uživatelé používají. Tyto znaky a konvence řazení těchto řetězců se mohou lišit v závislosti na národním prostředí počítače uživatele. Dokonce i řetězce, které obsahují identické znaky, mohou být tříděny různě v závislosti na jazykové verzi aktuálního vlákna. Kromě toho vyzkoušejte tento ukázkový kód místně na počítači s Windows a zobrazí se vám následující výsledky:

```console
<coop> is less than <co-op> using en-US culture
<coop> is greater than <co-op> using ordinal comparison
<coop> is less than <cop> using en-US culture
<coop> is less than <cop> using ordinal comparison
<co-op> is less than <cop> using en-US culture
<co-op> is less than <cop> using ordinal comparison
```

Jazykové porovnání jsou závislé na aktuální jazykové verzi a jsou závislé na operačním systému. Musíte vzít v úvahu při práci s porovnáváním řetězců.

## <a name="linguistic-sorting-and-searching-strings-in-arrays"></a>Jazykové řazení a hledání řetězců v polích

Následující příklady ukazují, jak řadit a hledat řetězce v poli pomocí jazykového porovnání závislého na aktuální jazykové verzi. Použijete statické metody <xref:System.Array>, které přebírají parametr <xref:System.StringComparer?displayProperty=nameWithType>.

Tento příklad ukazuje, jak seřadit pole řetězců pomocí aktuální jazykové verze:

[!code-csharp-interactive[Sorting an array of strings](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#5)]

Po seřazení pole můžete vyhledat položky pomocí binárního vyhledávání. Binární vyhledávání začíná uprostřed kolekce, aby bylo možné zjistit, která polovina kolekce by obsahovala hledaný řetězec. Každé následné porovnání rozděluje zbývající část kolekce na polovinu.  Pole je řazeno pomocí <xref:System.StringComparer.CurrentCulture?displayProperty=nameWithType>. Místní funkce `ShowWhere` zobrazí informace o tom, kde byl řetězec nalezen. Pokud řetězec nebyl nalezen, vrácená hodnota označuje, kde by byla nalezena.

[!code-csharp-interactive[Searching in a sorted array](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#6)]

## <a name="ordinal-sorting-and-searching-in-collections"></a>Ordinální řazení a hledání v kolekcích

Následující kód používá třídu kolekce <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> k uložení řetězců. Řetězce jsou řazeny pomocí metody <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType>. Tato metoda vyžaduje delegáta, který porovnává a řadí dva řetězce. Metoda <xref:System.String.CompareTo%2A?displayProperty=nameWithType> poskytuje funkci porovnání. Spusťte ukázku a sledujte objednávku. Tato operace řazení používá řazení s rozlišujícími písmeny. Použijte metody statického <xref:System.String.Compare%2A?displayProperty=nameWithType> k určení různých pravidel porovnání.

[!code-csharp-interactive[Sorting a list of strings](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#7)]

Po seřazení lze seznam řetězců vyhledat pomocí binárního vyhledávání. Následující příklad ukazuje, jak vyhledat seřazený seznam pomocí stejné funkce porovnání. Místní funkce `ShowWhere` zobrazuje, kde je požadovaný text nebo by byl:

[!code-csharp-interactive[csProgGuideStrings#11](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#8)]

Vždy nezapomeňte použít stejný typ porovnání pro řazení a vyhledávání. Použití různých typů porovnání pro řazení a vyhledávání vytváří neočekávané výsledky.

Třídy kolekce, například <xref:System.Collections.Hashtable?displayProperty=nameWithType>, <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType>a <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> mají konstruktory, které přijímají parametr <xref:System.StringComparer?displayProperty=nameWithType>, když je typ prvků nebo klíčů `string`. Obecně byste měli používat tyto konstruktory, kdykoli je to možné, a zadat buď <xref:System.StringComparer.Ordinal?displayProperty=nameWithType> nebo <xref:System.StringComparer.OrdinalIgnoreCase?displayProperty=nameWithType>.

## <a name="reference-equality-and-string-interning"></a>Referenční rovnost a interning řetězců

Žádná z ukázek nepoužila <xref:System.Object.ReferenceEquals%2A>. Tato metoda určuje, zda jsou dva řetězce stejného objektu. To může vést k nekonzistentním výsledkům při porovnávání řetězců. Následující příklad ukazuje funkci pro *učně řetězců* v C#. Když program deklaruje dvě nebo více identických řetězcových proměnných, kompilátor je uloží do stejného umístění. Voláním metody <xref:System.Object.ReferenceEquals%2A> vidíte, že dva řetězce ve skutečnosti odkazují na stejný objekt v paměti. Použijte metodu <xref:System.String.Copy%2A?displayProperty=nameWithType>, abyste se vyhnuli interning. Po provedení kopie mají tyto dva řetězce různá umístění úložiště, a to i v případě, že mají stejnou hodnotu. Spusťte následující ukázku, aby se zobrazily řetězce `a` a `b` byly *interně* , což znamená, že sdílejí stejné úložiště. Řetězce `a` a `c` nejsou.

[!code-csharp-interactive[Demonstrating string interning](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#9)]

> [!NOTE]
> Při testování rovnosti řetězců byste měli použít metody, které explicitně určují, jaký druh porovnání máte v úmyslu provést. Váš kód je mnohem udržovatelnější a čitelný. Použijte přetížení metod třídy <xref:System.String?displayProperty=nameWithType> a <xref:System.Array?displayProperty=nameWithType>, které přebírají parametr výčtu <xref:System.StringComparison>. Určíte, který typ porovnání se má provést. Nepoužívejte operátory `==` a `!=` při testování rovnosti. Metody instance <xref:System.String.CompareTo%2A?displayProperty=nameWithType> vždy provádějí porovnání rozlišující velká a malá písmena. Jsou primárně vhodné pro řazení řetězců abecedně.

Můžete interně vytvořit řetězec nebo načíst odkaz na existující interně volaný řetězec voláním metody <xref:System.String.Intern%2A?displayProperty=nameWithType>. Chcete-li zjistit, zda je řetězec interně, zavolejte metodu <xref:System.String.IsInterned%2A?displayProperty=nameWithType>.

## <a name="see-also"></a>Viz také:

- <xref:System.Globalization.CultureInfo?displayProperty=nameWithType>
- <xref:System.StringComparer?displayProperty=nameWithType>
- [Řetězce](../programming-guide/strings/index.md)
- [Porovnávání řetězců](../../standard/base-types/comparing.md)
- [Globalizace a lokalizace aplikací](/visualstudio/ide/globalizing-and-localizing-applications)
