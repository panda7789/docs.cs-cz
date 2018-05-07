---
title: 'Postupy: porovnávání řetězců – průvodce v C#'
description: Zjistěte, jak porovnávání a řazení řetězcové hodnoty, s nebo bez případě s nebo bez řazení konkrétní jazykové verze
ms.date: 03/20/2018
helpviewer_keywords:
- strings [C#], comparison
- comparing strings [C#]
ms.openlocfilehash: e9f4216af6073a352bef1efb59eea0ddeda5fc4b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-compare-strings-in-c"></a>Postupy pro porovnání řetězců v jazyce C# #

Porovnávání řetězců do odpovědí mezi dva dotazy: "Jsou tyto dva řetězce stejné?" nebo "Pořadí, v jakém tyto řetězce má umístit při řazení je?"

Tyto dvě otázky jsou ztěžuje faktory ovlivňující porovnání řetězců: 
- Můžete použít porovnání pořadí nebo lingvistické.
- Můžete zvolit, pokud případ záleží.
- Jazykovou verzi můžete vybrat konkrétní porovnání.
- Lingvistické comparisions jsou jazykovou verzi a platformy, které jsou závislé.

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

Při porovnávání řetězců, můžete definovat pořadí mezi nimi. Porovnání se používají k řazení posloupnosti řetězců. Jakmile je pořadí v pořadí od známé, je snazší hledat, pro softwaru i pro člověka. Další porovnávání může zkontrolujte, zda řetězce jsou stejné. Tato míra shodnosti kontroly jsou podobná rovnosti, ale některé rozdíly, jako je například případu rozdílů, může být ignorován.

## <a name="default-ordinal-comparisons"></a>Výchozí pořadí porovnání

Většina běžných operací <xref:System.String.CompareTo%2A?displayProperty=nameWithType> a <xref:System.String.Equals%2A?displayProperty=nameWithType> nebo <xref:System.String.op_Equality%2A?displayProperty=nameWithType> pomocí porovnávání podle pořadového čísla, malá a velká písmena porovnání a použít aktuální jazykovou verzi. Výsledky se zobrazí v následujícím příkladu.

[!code-csharp-interactive[Comparing strings using an ordinal comparison](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#1)]

Ordinální porovnávání nepřebírají lingvistické pravidla v úvahu při porovnávání řetězců. Budou se porovná řetězce po znacích. Malá a velká písmena porovnání pomocí velkých písmen v jejich porovnání. Většina důležité o těchto metodách porovnání výchozí je, protože používají aktuální jazykovou verzi, výsledky závisí na nastavení národního prostředí a jazyk počítače kde poběží. Tato porovnání jsou není vhodný pro porovnání, kde pořadí by měl být konzistentní napříč počítače nebo umístění.

## <a name="case-insensitive-ordinal-comparisons"></a>Porovnávání bez pořadí

<xref:System.String.Equals%2A?displayProperty=nameWithType> Metoda umožňuje určit <xref:System.StringComparison> hodnotu <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> k určení porovnání velká a malá písmena. Je také statického <xref:System.String.Compare%2A> metoda, která zahrnuje logická hodnota argumentu zadat porovnávání. Tyto aspekty znázorňuje následující kód:

[!code-csharp-interactive[Comparing strings ignoring case](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#2)]

## <a name="linguistic-comparisons"></a>Lingvistické porovnání

Řetězce lze provést řazení také pomocí lingvistické pravidla pro aktuální jazykovou verzi.
To se někdy označuje jako "word pořadí řazení." Při provádění lingvistického srovnání některé nealfanumerické znaky kódování Unicode může mít speciální váhu přiřazen. Například pomlčka "-" může mít velmi malé váhu přiřazená, takže "ke spolupráci" a "coop" se zobrazí vedle sebe v pořadí řazení. Kromě toho může být některé znaky kódování Unicode ekvivalentní posloupnost alfanumerické characterss. Následující příklad používá fráze "Jejich tance v ulici." v němčině "ss" a 'ß'. Jazykově (v systému Windows), "ss" je rovno Essetz Němčina: znak "ß" v "en US" a "de-DE" jazykové verze. 

[!code-csharp-interactive[Comparing strings using linguistic rules](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#3)]

Tento příklad znázorňuje operačního systému závislé povaha lingvistické porovnání. Hostitel pro interaktivní okno je hostitele platformy Linux. Porovnání lingvistické a pořadí vytvořit stejné výsledky. Pokud jste spustili Tato ukázka stejné na hostitele Windows, zobrazí se následující výstup:

```console
<coop> is less than <co-op> using invariant culture
<coop> is greater than <co-op> using ordinal comparison
<coop> is less than <cop> using invariant culture
<coop> is less than <cop> using ordinal comparison
<co-op> is less than <cop> using invariant culture
<co-op> is less than <cop> using ordinal comparison
```

V systému Windows, pořadí řazení "cop", "coop" a "ke spolupráci" měnit při změně lingvistického srovnání na porovnávání podle pořadového čísla. Dvě věty němčině také porovnat, jinak použití různých porovnání typů.

## <a name="comparisons-using-specific-cultures"></a>Porovnání pomocí konkrétní jazykové verze

Tato ukázka ukládá <xref:System.Globalization.CultureInfo> pro aktuální jazykovou verzi.
Původní jazykovou verzi můžete nastavit a načíst na aktuální objekt přístup z více vláken. Porovnání se provádí pomocí <xref:System.StringComparison.CurrentCulture> hodnoty zajistit porovnání specifické pro jazykovou verzi.

Jazyková verze použitá ovlivňuje lingvistické porovnání. Následující příklad ukazuje výsledky porovnávání dvě němčině věty pomocí culture "en US" a "de-DE" jazyková verze:

[!code-csharp-interactive[Comparing strings across cultures](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#4)]

Jazykovou jsou obvykle používány k porovnání a řazení řetězců vstup uživatelé s jiných řetězců vstupní uživatelé. Znaky a řazení konvence tyto řetězce mohou lišit v závislosti na národního prostředí uživatele počítače. I řetězce, které obsahují stejné znaky může seřadit odlišně v závislosti na jazykové verze aktuálního vlákna. Kromě toho, opakujte tento ukázkový kód místně na počítači s Windows, a bude následující výsledky:

```console
<coop> is less than <co-op> using en-US culture
<coop> is greater than <co-op> using ordinal comparison
<coop> is less than <cop> using en-US culture
<coop> is less than <cop> using ordinal comparison
<co-op> is less than <cop> using en-US culture
<co-op> is less than <cop> using ordinal comparison
```

Lingvistické comparisions jsou závislé na aktuální jazykovou verzi a jsou závislé operačního systému. Musíte, v úvahu při práci s porovnání řetězců.

## <a name="linguistic-sorting-and-searching-strings-in-arrays"></a>Jazykové řazení a hledání řetězců v polích

Následující příklady ukazují, jak řadit a hledat řetězce v poli pomocí lingvistické porovnání závisí na aktuální jazykové verze. Použít statickou <xref:System.Array> metod, které berou <xref:System.StringComparer?displayProperty=nameWithType> parametr.

Tento příklad ukazuje, jak řadit pole řetězců pomocí aktuální jazykové verze: 

[!code-csharp-interactive[Sorting an array of strings](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#5)]

Jakmile je seřazen pole, můžete hledat položky pomocí binární vyhledávání. Binární vyhledávání spustí uprostřed kolekce k určení, které půl kolekce by obsahovat hledané kombinaci řetězec. Každý další porovnání dále dělí zbývající část kolekce v polovině.  Toto pole je seřazen pomocí <xref:System.StringComparer.CurrentCulture?displayProperty=nameWithType>. Místní funkce `ShowWhere` zobrazí informace o kterém byl nalezen řetězec. Pokud nebyl nalezen řetězec, vrácená hodnota určuje, kde je pokud nebyly nalezeny.

[!code-csharp-interactive[Searching in a sorted array](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#6)]

## <a name="ordinal-sorting-and-searching-in-collections"></a>Pořadí řazení a vyhledávání v kolekcích

Následující kód používá <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> třídu kolekce pro ukládání řetězců. Řetězce jsou seřazeny pomocí <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> metoda. Tato metoda musí delegáta, který porovnává a řadí dva řetězce. <xref:System.String.CompareTo%2A?displayProperty=nameWithType> Metoda poskytuje tuto funkci porovnání. Spustit ukázku a sledovat pořadí. Tato operace řazení používá pořadové řazení velká a malá písmena. Použijete statických <xref:System.String.Compare%2A?displayProperty=nameWithType> metody lze určit pravidla, jiné porovnání.

[!code-csharp-interactive[Sorting a list of strings](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#7)]

Jakmile seřadit, můžete seznam řetězců vyhledávat pomocí binární vyhledávání. Následující příklad ukazuje, jak hledat setříděné uvedené pomocí stejné funkce porovnání. Místní funkce `ShowWhere` ukazuje hledané kombinaci text nebo u kterých bude:

[!code-csharp-interactive[csProgGuideStrings#11](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#8)]

Vždy nezapomeňte použít stejný typ porovnání pro řazení a vyhledávání. Použití různých porovnání typů pro řazení a vyhledávání vytváří neočekávané výsledky. 

Kolekce tříd, například <xref:System.Collections.Hashtable?displayProperty=nameWithType>, <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType>, a <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> mít konstruktory, které provést <xref:System.StringComparer?displayProperty=nameWithType> parametr, pokud je typ elementy nebo klíčů `string`. Obecně platí, by měl používat tyto konstruktory, kdykoli je to možné a zadat buď <xref:System.StringComparer.Ordinal?displayProperty=nameWithType> nebo <xref:System.StringComparer.OrdinalIgnoreCase?displayProperty=nameWithType>.

## <a name="reference-equality-and-string-interning"></a>Referenční rovnosti a interning řetězec

Žádná z ukázky použili <xref:System.Object.ReferenceEquals%2A>. Tato metoda určuje, zda jsou dva řetězce na stejný objekt. To může vést k nekonzistentním výsledkům v porovnání řetězců. Následující příklad ukazuje *interning řetězec* funkce jazyka C#. Když program deklaruje minimálně dva identické řetězec proměnné, kompilátor je uloží všechny ve stejném umístění. Při volání <xref:System.Object.ReferenceEquals%2A> metoda, uvidíte, že dva řetězce ve skutečnosti odkazovat na stejný objekt v paměti. Použití <xref:System.String.Copy%2A?displayProperty=nameWithType> metoda zrušení interning. Po vytvoření kopie, mají dva řetězce umístění jiného úložiště, i když mají stejnou hodnotu. Spusťte následující ukázku zobrazíte řetězce `a` a `b` jsou *interned* znamená, že sdílejí stejné úložiště. Řetězce `a` a `c` nejsou.

[!code-csharp-interactive[Demonstrating string interning](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#9)]

> [!NOTE]
> Při testování rovnosti řetězců, byste měli použít metody, které explicitně zadat, jaký typ porovnání, který chcete provést. Váš kód je mnohem víc udržovatelný a čitelné. Použijte přetížení metody <xref:System.String?displayProperty=nameWithType> a <xref:System.Array?displayProperty=nameWithType> třídy trvají <xref:System.StringComparison> parametru výčtu. Můžete určit typ porovnání k provedení. Nepoužívejte `==` a `!=` operátory při testování rovnosti. <xref:System.String.CompareTo%2A?displayProperty=nameWithType> Instance metody vždy provádět porovnávání podle pořadového čísla malá a velká písmena. Mají především předpoklady pro řazení řetězců podle abecedy.

## <a name="see-also"></a>Viz také
 <xref:System.Globalization.CultureInfo?displayProperty=nameWithType>  
 <xref:System.StringComparer?displayProperty=nameWithType>  
 [Řetězce](../programming-guide/strings/index.md)  
 [Porovnávání řetězců](../../standard/base-types/comparing.md)  
 [Globalizace a lokalizace aplikací](/visualstudio/ide/globalizing-and-localizing-applications)