---
title: Jak porovnat řetězce - Průvodce C#
description: Naučte se, jak porovnat a seřadit hodnoty řetězce, s nebo bez případu, s nebo bez pořadí specifické pro jazykovou verzi
ms.date: 10/03/2018
helpviewer_keywords:
- strings [C#], comparison
- comparing strings [C#]
ms.openlocfilehash: dda3ec8cb6a0131867e6ea3bb0cf7199d86058ff
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "73973324"
---
# <a name="how-to-compare-strings-in-c"></a>Jak porovnat řetězce v C\#

Porovnáte řetězce odpovědět na jednu ze dvou otázek: "Jsou tyto dva řetězce stejné?" nebo "V jakém pořadí by měly být tyto řetězce umístěny při jejich třídění?"

Tyto dvě otázky jsou komplikovány faktory, které ovlivňují porovnání řetězců:

- Můžete zvolit posuzované nebo jazykové srovnání.
- Můžete si vybrat, jestli záleží na případu.
- Můžete zvolit porovnání specifické pro jazykovou verzi.
- Jazykové porovnání jsou závislé na jazykové verzi a platformě.

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

Při porovnávání řetězců, definujete pořadí mezi nimi. Porovnání se používají k řazení posloupnosti řetězců. Jakmile je sekvence ve známém pořadí, je snazší vyhledávat, a to jak pro software, tak pro člověka. Jiné porovnání může zkontrolovat, zda řetězce jsou stejné. Tyto kontroly stejnosti jsou podobné rovnosti, ale některé rozdíly, jako jsou rozdíly v případech, mohou být ignorovány.

## <a name="default-ordinal-comparisons"></a>Výchozí číselné porovnání

Ve výchozím nastavení nejběžnější operace:

- <xref:System.String.CompareTo%2A?displayProperty=nameWithType>
- <xref:System.String.Equals%2A?displayProperty=nameWithType>
- <xref:System.String.op_Equality%2A?displayProperty=nameWithType>a <xref:System.String.op_Inequality%2A?displayProperty=nameWithType>, to [znamená, `==` `!=`že provozovatelé rovnosti a ](../language-reference/operators/equality-operators.md#string-equality), resp.

proveďte řadové porovnání rozlišující malá a velká písmena a v případě potřeby použijte aktuální jazykovou verzi. Následující příklad ukazuje, že:

[!code-csharp-interactive[Comparing strings using an ordinal comparison](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#1)]

Výchozí řadové porovnání nebere v úvahu jazyková pravidla při porovnávání řetězců. Porovnává binární hodnotu každého <xref:System.Char> objektu ve dvou řetězcích. V důsledku toho je výchozí řadové porovnání také rozlišování velkých a malých písmen.

Všimněte si, že <xref:System.String.Equals%2A?displayProperty=nameWithType> test `==` rovnosti s a a `!=` <xref:System.String.CompareTo%2A?displayProperty=nameWithType> operátory se liší od porovnání řetězců pomocí metody a. <xref:System.String.Compare(System.String,System.String)?displayProperty=nameWithType)> Zatímco testy rovnosti provést případ rozlišování ordinální porovnání, metody porovnání provést případ rozlišování, jazyková verze citlivé porovnání pomocí aktuální jazykové verze. Vzhledem k tomu, že výchozí metody porovnání často provádět různé typy porovnání, doporučujeme vždy provést záměr kódu jasné voláním přetížení, které explicitně určuje typ porovnání provést.

## <a name="case-insensitive-ordinal-comparisons"></a>Ordinální porovnání bez rozlišování velkých a malých písmen

Tato <xref:System.String.Equals(System.String,System.StringComparison)?displayProperty=nameWithType> metoda umožňuje zadat <xref:System.StringComparison> hodnotu<xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType>
pro poslané číslovky bez rozlišování velkých a malých písmen. Existuje také statická <xref:System.String.Compare(System.String,System.String,System.StringComparison)?displayProperty=nameWithType> metoda, která provádí porovnání ordinal bez rozlišování velkých a malých písmen, pokud zadáte hodnotu <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> argumentu. <xref:System.StringComparison> Ty jsou uvedeny v následujícím kódu:

[!code-csharp-interactive[Comparing strings ignoring case](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#2)]

Při provádění rozlišování velkých a malých písmen řadové porovnání, tyto metody používají konvencí skříně [invariantní jazykové verze](xref:System.Globalization.CultureInfo.InvariantCulture).

## <a name="linguistic-comparisons"></a>Jazyková srovnání

Řetězce lze také objednat pomocí jazykových pravidel pro aktuální jazykovou verzi.
To se někdy označuje jako "pořadí řazení slov". Při provádění jazykového porovnání mohou mít některé nealfanumerické znaky unicode přiřazeny speciální váhy. Například pomlčka "-" může mít velmi malou váhu přiřazenou tak, aby se vedle sebe vedle sebe zobrazovaly "co-op" a "coop" v pořadí řazení. Kromě toho některé znaky Unicode může být <xref:System.Char> ekvivalentní posloupnost instancí. Následující příklad používá frázi "Tančí na ulici". v němčině s "ss" (U+0073 U+0073) v jednom řetězci a "ß" (U+00DF) v jiném. Lingvisticky (v systému Windows), "ss" se rovná německé Esszet: 'ß' znak v obou "en-US" a "de-DE" kultury.

[!code-csharp-interactive[Comparing strings using linguistic rules](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#3)]

Tato ukázka ukazuje povahu jazykového porovnání závislé na operačním systému. Hostitelem interaktivního okna je hostitel Linuxu. Jazykové a posvěcené porovnání dosáhnout stejných výsledků. Pokud jste spustili stejnou ukázku na hostiteli systému Windows, zobrazí se následující výstup:

```console
<coop> is less than <co-op> using invariant culture
<coop> is greater than <co-op> using ordinal comparison
<coop> is less than <cop> using invariant culture
<coop> is less than <cop> using ordinal comparison
<co-op> is less than <cop> using invariant culture
<co-op> is less than <cop> using ordinal comparison
```

V systému Windows se pořadí řazení "cop", "coop" a "co-op" změní, když změníte z jazykového porovnání na řadové porovnání. Dvě německé věty také porovnávají odlišně pomocí různých typů porovnání.

## <a name="comparisons-using-specific-cultures"></a>Porovnání pomocí specifických kultur

Tato ukázka ukládá <xref:System.Globalization.CultureInfo> objekty pro jazykové verze en US a de-DE.
Porovnání se provádí pomocí <xref:System.Globalization.CultureInfo> objektu k zajištění porovnání specifické pro jazykovou verzi.

Použitá jazyková verze ovlivňuje jazykové porovnání. Následující příklad ukazuje výsledky porovnání dvou německých vět pomocí jazykové verze "en US" a jazykové verze "de-DE":

[!code-csharp-interactive[Comparing strings across cultures](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#4)]

Porovnání zkoumaná jazykovou verzi se obvykle používají k porovnání a řazení řetězců vstup uživatelů s jinými řetězci vstup uživatelů. Znaky a konvence řazení těchto řetězců se mohou lišit v závislosti na národním prostředí počítače uživatele. Dokonce i řetězce, které obsahují identické znaky mohou řadit odlišně v závislosti na jazykové verzi aktuálního vlákna. Kromě toho zkuste tento ukázkový kód místně na počítači se systémem Windows a budete mít následující výsledky:

```console
<coop> is less than <co-op> using en-US culture
<coop> is greater than <co-op> using ordinal comparison
<coop> is less than <cop> using en-US culture
<coop> is less than <cop> using ordinal comparison
<co-op> is less than <cop> using en-US culture
<co-op> is less than <cop> using ordinal comparison
```

Jazykové porovnání jsou závislé na aktuální jazykové verzi a jsou závislé na os. Musíte vzít v úvahu, že při práci s porovnání řetězců.

## <a name="linguistic-sorting-and-searching-strings-in-arrays"></a>Jazykové řazení a hledání řetězců v polích

Následující příklady ukazují, jak řadit a vyhledávat řetězce v poli pomocí jazykového porovnání závislého na aktuální jazykové verzi. Použijete statické <xref:System.Array> metody, <xref:System.StringComparer?displayProperty=nameWithType> které trvat parametr.

Tento příklad ukazuje, jak seřadit pole řetězců pomocí aktuální jazykové verze:

[!code-csharp-interactive[Sorting an array of strings](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#5)]

Po seřazení pole můžete vyhledávat položky pomocí binárního vyhledávání. Binární hledání začíná uprostřed kolekce k určení, která polovina kolekce bude obsahovat požadovaný řetězec. Každé následné porovnání rozdělí zbývající část kolekce na polovinu.  Pole je seřazeno pomocí . <xref:System.StringComparer.CurrentCulture?displayProperty=nameWithType> Místní funkce `ShowWhere` zobrazuje informace o tom, kde byl řetězec nalezen. Pokud řetězec nebyl nalezen, vrácená hodnota označuje, kde by byl, kdyby byl nalezen.

[!code-csharp-interactive[Searching in a sorted array](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#6)]

## <a name="ordinal-sorting-and-searching-in-collections"></a>Řadové třídění a vyhledávání ve sbírkách

Následující kód používá <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> třídu kolekce k ukládání řetězců. Řetězce jsou seřazeny <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> pomocí metody. Tato metoda potřebuje delegáta, který porovnává a objednávky dva řetězce. Metoda <xref:System.String.CompareTo%2A?displayProperty=nameWithType> poskytuje tuto funkci porovnání. Spusťte ukázku a dodržujte pořadí. Tato operace řazení používá řadové řazení rozlišující malá a velká písmena. Statické <xref:System.String.Compare%2A?displayProperty=nameWithType> metody byste použili k určení různých pravidel porovnání.

[!code-csharp-interactive[Sorting a list of strings](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#7)]

Po seřazení lze seznam řetězců prohledávat pomocí binárního vyhledávání. Následující ukázka ukazuje, jak prohledávat seřazené uvedené pomocí stejné funkce porovnání. Místní funkce `ShowWhere` ukazuje, kde je nebo by byl hledaný text:

[!code-csharp-interactive[csProgGuideStrings#11](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#8)]

Při řazení a vyhledávání vždy používejte stejný typ porovnání. Použití různých typů porovnání pro řazení a vyhledávání přináší neočekávané výsledky.

Kolekce <xref:System.Collections.Hashtable?displayProperty=nameWithType>třídy, jako <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> je například , <xref:System.StringComparer?displayProperty=nameWithType> <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType>a mají konstruktory, `string`které berou parametr, když je typ prvků nebo klíčů . Obecně byste měli použít tyto konstruktory, kdykoli <xref:System.StringComparer.Ordinal?displayProperty=nameWithType> <xref:System.StringComparer.OrdinalIgnoreCase?displayProperty=nameWithType>je to možné, a určit buď nebo .

## <a name="reference-equality-and-string-interning"></a>Referenční rovnost a interning řetězců

Žádný ze vzorků <xref:System.Object.ReferenceEquals%2A>nepoužil . Tato metoda určuje, pokud dva řetězce jsou stejný objekt. To může vést k nekonzistentní výsledky v porovnání řetězců. Následující příklad ukazuje *funkci interning řetězce* jazyka C#. Když program deklaruje dvě nebo více identických proměnných řetězce, kompilátor je všechny uloží do stejného umístění. Voláním <xref:System.Object.ReferenceEquals%2A> metody uvidíte, že dva řetězce skutečně odkazují na stejný objekt v paměti. Použijte <xref:System.String.Copy%2A?displayProperty=nameWithType> metodu, aby se zabránilo interning. Po nastolování kopie mají dva řetězce různá umístění úložiště, i když mají stejnou hodnotu. Spusťte následující ukázku, `a` `b` která ukazuje, že řetězce a jsou *internovány,* což znamená, že sdílejí stejné úložiště. Struny `a` a `c` nejsou.

[!code-csharp-interactive[Demonstrating string interning](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#9)]

> [!NOTE]
> Při testování rovnosti řetězců, měli byste použít metody, které explicitně určit, jaký druh porovnání máte v úmyslu provést. Váš kód je mnohem více udržovatelný a čitelný. Použijte přetížení metody <xref:System.String?displayProperty=nameWithType> a <xref:System.Array?displayProperty=nameWithType> třídy, které <xref:System.StringComparison> mají parametr výčtu. Můžete zadat, jaký typ porovnání provést. Vyhněte `==` `!=` se použití a operátory při testování rovnosti. Metody <xref:System.String.CompareTo%2A?displayProperty=nameWithType> instance vždy provádět řadové porovnání rozlišování velkých a malých písmen. Jsou primárně vhodné pro řazení řetězců abecedně.

Můžete intern řetězec nebo načíst odkaz na existující internovaný řetězec voláním <xref:System.String.Intern%2A?displayProperty=nameWithType> metody. Chcete-li zjistit, zda je <xref:System.String.IsInterned%2A?displayProperty=nameWithType> řetězec internován, zavolejte metodu.

## <a name="see-also"></a>Viz také

- <xref:System.Globalization.CultureInfo?displayProperty=nameWithType>
- <xref:System.StringComparer?displayProperty=nameWithType>
- [Řetězce](../programming-guide/strings/index.md)
- [Porovnávání řetězců](../../standard/base-types/comparing.md)
- [Globalizace a lokalizace aplikací](/visualstudio/ide/globalizing-and-localizing-applications)
