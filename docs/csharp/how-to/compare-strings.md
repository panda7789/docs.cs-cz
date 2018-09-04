---
title: 'Postupy: porovnávání řetězců – průvodce v C#'
description: Zjistěte, jak porovnat a pořadí řetězcové hodnoty, s nebo bez něj případu s nebo bez řazení konkrétní jazykovou verzi
ms.date: 03/20/2018
helpviewer_keywords:
- strings [C#], comparison
- comparing strings [C#]
ms.openlocfilehash: 3c841a1152613ec877bb6172dc8d053bf060b33b
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43515277"
---
# <a name="how-to-compare-strings-in-c"></a>Jak bude probíhat porovnávání řetězců v jazyce C\#

Porovnání řetězců k odpovědí mezi dva dotazy: "Jsou tyto dva řetězce stejné?" nebo "V jakém pořadí těchto řetězců, umístit při řazení je?"

Faktory ovlivňující porovnávání řetězců jsou složité tyto dvě otázky:

- Můžete použít pořadí nebo jazykové porovnání.
- Můžete použít, pokud to je případ.
- Jazyková verze můžete vybrat konkrétní porovnání.
- Lingvistická comparisions jsou jazykovou verzi a platformy, které jsou závislé.

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

Při porovnání řetězců můžete definovat pořadí mezi nimi. Porovnání se používají k seřazení posloupnost řetězců. Po známé postupně pořadí je snazší vyhledávat, k softwaru i pro lidi. Jiné porovnání může zkontrolujte, jestli řetězce jsou stejné. Tato míra shodnosti kontroly jsou podobné rovnosti, ale některé rozdíly, jako je například případu rozdíly, mohou být ignorovány.

## <a name="default-ordinal-comparisons"></a>Výchozí ordinální porovnání

Nejběžnější operace <xref:System.String.CompareTo%2A?displayProperty=nameWithType> a <xref:System.String.Equals%2A?displayProperty=nameWithType> nebo <xref:System.String.op_Equality%2A?displayProperty=nameWithType> použije pořadové porovnávání, porovnání velká a malá písmena a pomocí aktuální jazykové verze. Výsledky jsou zobrazeny v následujícím příkladu.

[!code-csharp-interactive[Comparing strings using an ordinal comparison](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#1)]

Ordinální porovnání nepřebírají jazyková pravidla v úvahu při porovnávání řetězců. Bude jejich porovnání znak po znaku řetězce. Porovnání velká a malá písmena pomocí malá a velká písmena v jejich porovnávání. Nejdůležitější bod týkající se těchto výchozí porovnávací metody je, protože používají aktuální jazykovou verzi, výsledek závisí na nastavení národního prostředí a jazyk daného počítače, kde běží. Tato porovnání jsou vhodná pro porovnání kde order by měl být konzistentní vzhledem k aplikacím napříč počítače nebo umístění.

## <a name="case-insensitive-ordinal-comparisons"></a>Ordinální porovnání velká a malá písmena

<xref:System.String.Equals%2A?displayProperty=nameWithType> Metoda vám umožňuje určit <xref:System.StringComparison> hodnotu <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType>
Chcete-li určit porovnání velká a malá písmena. Je také statické <xref:System.String.Compare%2A> metodu, která obsahuje logický argument, chcete-li určit porovnávání. Tyto aspekty znázorňuje následující kód:

[!code-csharp-interactive[Comparing strings ignoring case](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#2)]

## <a name="linguistic-comparisons"></a>Porovnání nezávislá na

Řetězce lze provést řazení také použití jazykových pravidel pro aktuální jazykovou verzi.
To se někdy označuje jako "pořadí řazení slov." Při provádění lingvistické srovnání některé nealfanumerické znaky Unicode mohou mít zvláštní váhu přiřazené. Například pomlčka "-" může mít velmi malou přiřazenou váhu, tak, aby "co-op" a "coop" zobrazily vedle sebe v pořadí řazení. Kromě toho může být některé znaky Unicode odpovídá sekvenci z alfanumerických znaků. Následující příklad používá frázi "Jejich taneček v ulici." v Německu "ss" a "ß". Lingvistických (ve Windows), "ss" je rovno Essetz Němčina: znak "ß" v "en US" a "de-DE" jazykové verze.

[!code-csharp-interactive[Comparing strings using linguistic rules](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#3)]

V této ukázce závislé povahy porovnání nezávislá na operační systém. Hostitel pro interaktivní okno je hostiteli se systémem Linux. Jazykové a ordinálního porovnání vytvářejí stejné výsledky. Pokud jste spustili tento stejný příklad na hostiteli Windows, zobrazí se následující výstup:

```console
<coop> is less than <co-op> using invariant culture
<coop> is greater than <co-op> using ordinal comparison
<coop> is less than <cop> using invariant culture
<coop> is less than <cop> using ordinal comparison
<co-op> is less than <cop> using invariant culture
<co-op> is less than <cop> using ordinal comparison
```

Na Windows, pořadí řazení "cop", změňte "coop" a "co-op" při změně jazykové porovnání ordinálního porovnání. Dvě věty německé také porovnat, jinak než pomocí jiné porovnání typů.

## <a name="comparisons-using-specific-cultures"></a>Porovnání pomocí konkrétní jazykové verze

Tato ukázka ukládá <xref:System.Globalization.CultureInfo> pro aktuální jazykovou verzi.
Původní jazykové verze můžete nastavit a načíst na aktuální objekt vlákna. Porovnání se provádí pomocí <xref:System.StringComparison.CurrentCulture> pro zajištění porovnání specifické pro jazykovou verzi.

Porovnání nezávislá na má vliv na použitou jazykovou verzi. Následující příklad ukazuje výsledky porovnání dvou německé vět s jazykovou verzi "en US" a "de-DE" jazykové verze:

[!code-csharp-interactive[Comparing strings across cultures](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#4)]

Porovnání zohledňující jazykovou verzi se obvykle používají porovnání a řazení řetězců vstup uživatelé s dalšími řetězci vstup uživatelem. Znaky a konvence řazení pro tyto řetězce můžou lišit v závislosti na národní prostředí uživatele počítače. Dokonce řetězce, které obsahují stejné znaky může seřadit odlišně v závislosti na jazykové verze aktuálního vlákna. Kromě toho vyzkoušejte tento kód ukázky místně na počítači s Windows a se následující výsledky:

```console
<coop> is less than <co-op> using en-US culture
<coop> is greater than <co-op> using ordinal comparison
<coop> is less than <cop> using en-US culture
<coop> is less than <cop> using ordinal comparison
<co-op> is less than <cop> using en-US culture
<co-op> is less than <cop> using ordinal comparison
```

Jazykové comparisions jsou závislé na aktuální jazykovou verzi a jsou závislé operačního systému. Je nutné provést, který v úvahu při práci s porovnávání řetězců.

## <a name="linguistic-sorting-and-searching-strings-in-arrays"></a>Jazyková řazení a hledání řetězců v polích

Následující příklady ukazují způsob řazení a hledání řetězce v poli pomocí jazykové porovnání závislé na aktuální jazykové verze. Použijete statickou <xref:System.Array> metod, které berou <xref:System.StringComparer?displayProperty=nameWithType> parametru.

Tento příklad ukazuje, jak seřadit pole řetězců pomocí aktuální jazykové verze:

[!code-csharp-interactive[Sorting an array of strings](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#5)]

Jakmile je pole seřazené, můžete vyhledat pomocí binárního vyhledávání položek. Binární vyhledávání začíná uprostřed kolekce, kterou chcete určit, které polovině kolekce by obsahovala hledané kombinaci řetězec. Každé následné porovnání rozděluje zbývajících součástí kolekce na polovinu.  Pole má řazení proběhnout pomocí <xref:System.StringComparer.CurrentCulture?displayProperty=nameWithType>. Lokální funkce `ShowWhere` zobrazí informace o nalezených řetězec. Pokud řetězec nebyl nalezen, vrácené hodnoty označuje, kde by se pokud nebyly nalezeny.

[!code-csharp-interactive[Searching in a sorted array](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#6)]

## <a name="ordinal-sorting-and-searching-in-collections"></a>Ordinální řazení a vyhledávání v kolekcích

Následující kód používá <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> třídy kolekce k uložení řetězců. Jsou řetězce seřazeny pomocí <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> metody. Tato metoda musí delegáta, který porovnává a objednává dva řetězce. <xref:System.String.CompareTo%2A?displayProperty=nameWithType> Metoda poskytuje tuto funkci porovnání. Spusťte ukázku a podívejte se pořadí. Tato operace řazení používá pořadové řazení malá a velká písmena. Můžete využít statické <xref:System.String.Compare%2A?displayProperty=nameWithType> metody lze určit pravidla, jiné porovnání.

[!code-csharp-interactive[Sorting a list of strings](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#7)]

Jakmile řazení, lze seznam řetězců, které prohledávat pomocí binárního vyhledávání. Následující příklad ukazuje, jak hledat seřazené uvedené pomocí stejné funkce porovnání. Lokální funkce `ShowWhere` ukazuje, kde je hledané kombinaci text nebo by být:

[!code-csharp-interactive[csProgGuideStrings#11](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#8)]

Vždy ujistěte se, že chcete použít stejný typ porovnání pro řazení a vyhledávání. Použití různých porovnání typů pro řazení a vyhledávání následek neočekávané výsledky.

Třídy kolekcí, jako <xref:System.Collections.Hashtable?displayProperty=nameWithType>, <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType>, a <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> konstruktorů, které mají <xref:System.StringComparer?displayProperty=nameWithType> parametr, když je typ prvky nebo klíče `string`. Obecně platí, by měl používat tyto konstruktory, kdykoli je to možné a zadat buď <xref:System.StringComparer.Ordinal?displayProperty=nameWithType> nebo <xref:System.StringComparer.OrdinalIgnoreCase?displayProperty=nameWithType>.

## <a name="reference-equality-and-string-interning"></a>Referenční rovnost a interning řetězce

Žádná z ukázky použili <xref:System.Object.ReferenceEquals%2A>. Tato metoda určuje, zda jsou dva řetězce stejný objekt. To může vést k nekonzistentním výsledkům při porovnávání řetězců. Následující příklad ukazuje, *interning řetězce* funkce jazyka C#. Když program deklaruje nejmíň dva identické řetězcové proměnné, kompilátor je uloží ve stejném umístění. Při volání <xref:System.Object.ReferenceEquals%2A> metoda, uvidíte, že dva řetězce ve skutečnosti odkazovat na stejný objekt v paměti. Použití <xref:System.String.Copy%2A?displayProperty=nameWithType> metody, aby se zabránilo interning. Po zkopírování, máte dva řetězce umístění jiného úložiště, i když mají stejnou hodnotu. Spusťte následující ukázku zobrazíte řetězce `a` a `b` jsou *internovány* to znamená, že sdílejí stejné úložiště. Řetězce `a` a `c` nejsou.

[!code-csharp-interactive[Demonstrating string interning](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#9)]

> [!NOTE]
> Při testování rovnosti řetězců, byste měli použít metody, které explicitně zadat, jaký druh porovnání máte v úmyslu provést. Váš kód je mnohem snadněji udržovatelné a čitelné. Použijte přetížení metody <xref:System.String?displayProperty=nameWithType> a <xref:System.Array?displayProperty=nameWithType> třídy, které přijímají <xref:System.StringComparison> parametr výčtu. Můžete určit typ porovnání k provedení. Vyhněte se použití `==` a `!=` operátory při testování rovnosti. <xref:System.String.CompareTo%2A?displayProperty=nameWithType> Metody instance provádět vždy pořadové porovnávání malá a velká písmena. Jsou primárně jsou vhodné pro řazení řetězců podle abecedy.

## <a name="see-also"></a>Viz také:

- <xref:System.Globalization.CultureInfo?displayProperty=nameWithType>  
- <xref:System.StringComparer?displayProperty=nameWithType>  
- [Řetězce](../programming-guide/strings/index.md)  
- [Porovnávání řetězců](../../standard/base-types/comparing.md)  
- [Globalizace a lokalizace aplikací](/visualstudio/ide/globalizing-and-localizing-applications)
