---
title: Práce se soubory .resx programově
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- resource files, .resx files
- .resx files
ms.assetid: 168f941a-2b84-43f8-933f-cf4a8548d824
ms.openlocfilehash: 3b84d77e4ac9b9889d1bc2f08e5ead6b81deecb0
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243034"
---
# <a name="work-with-resx-files-programmatically"></a>Práce se soubory .resx programově

Vzhledem k tomu, že soubory prostředků XML (.resx) musí obsahovat dobře definovaný soubor XML, včetně záhlaví, které musí následovat za určitým schématem následovaným daty v párech název/hodnota, můžete zjistit, že ruční vytváření těchto souborů je náchylné k chybám. Jako alternativu můžete vytvářet soubory RESX programově pomocí typů a členů v knihovně tříd .NET. Knihovnu tříd .NET můžete také použít k načtení prostředků, které jsou uloženy v souborech .resx. Tento článek vysvětluje, jak můžete použít typy <xref:System.Resources> a členy v oboru názvů pro práci se soubory RESX.

Tento článek popisuje práci se soubory XML (.resx), které obsahují prostředky. Informace o práci s binárními soubory prostředků, které <xref:System.Resources.ResourceManager>byly vloženy do sestavení, naleznete v tématu .

> [!WARNING]
> Existují také způsoby, jak pracovat se soubory .resx jiné než programově. Když přidáte soubor prostředků do projektu [sady Visual Studio,](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) visual studio poskytuje rozhraní pro vytváření a údržbu souboru Resx a automaticky převede soubor .resx do souboru .resources v době kompilace. Textový editor můžete také použít k přímé manipulaci se souborem RESX. Chcete-li však zabránit poškození souboru, dávejte pozor, abyste neupravili žádné binární informace uložené v souboru.

## <a name="create-a-resx-file"></a>Vytvoření souboru Resx

Třídu <xref:System.Resources.ResXResourceWriter?displayProperty=nameWithType> můžete použít k programovému vytvoření souboru Resx následujícím postupem:

1. Vytvořte instanci <xref:System.Resources.ResXResourceWriter> objektu <xref:System.Resources.ResXResourceWriter.%23ctor%28System.String%29> voláním metody a zadáním názvu souboru Resx. Název souboru musí obsahovat příponu Resx. Pokud instance objektu <xref:System.Resources.ResXResourceWriter> v `using` bloku, není explicitně muset volat <xref:System.Resources.ResXResourceWriter.Close%2A?displayProperty=nameWithType> metodu v kroku 3.

2. Volání <xref:System.Resources.ResXResourceWriter.AddResource%2A?displayProperty=nameWithType> metody pro každý prostředek, který chcete přidat do souboru. Pomocí přetížení této metody přidejte řetězec, objekt a binární (bajtové pole) data. Pokud je prostředek objekt, musí být serializovatelný.

3. Volání <xref:System.Resources.ResXResourceWriter.Close%2A?displayProperty=nameWithType> metody generovat soubor prostředků a uvolnit všechny prostředky. Pokud <xref:System.Resources.ResXResourceWriter> byl objekt vytvořen `using` v rámci bloku, prostředky jsou zapsány do souboru .resx a prostředky používané <xref:System.Resources.ResXResourceWriter> objektem jsou uvolněny na konci `using` bloku.

Výsledný soubor Resx má příslušnou hlavičku `data` a značku pro <xref:System.Resources.ResXResourceWriter.AddResource%2A?displayProperty=nameWithType> každý prostředek přidaný metodou.

> [!WARNING]
> Nepoužívejte soubory prostředků k ukládání hesel, citlivých informací o zabezpečení nebo soukromých dat.

Následující příklad vytvoří soubor Resx s názvem CarResources.resx, který ukládá šest řetězců, ikonu `Automobile` a dva objekty definované aplikací (dva objekty). Třída, `Automobile` která je definována a vytvořena instance v příkladu, je označenatributem. <xref:System.SerializableAttribute>

[!code-csharp[Conceptual.Resources.ResX#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.resx/cs/create1.cs#1)]
[!code-vb[Conceptual.Resources.ResX#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.resx/vb/create1.vb#1)]

> [!TIP]
> Pomocí sady [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) můžete také vytvářet soubory Resx. V době kompilace visual studio používá [generátor souborů prostředků (Resgen.exe)](../tools/resgen-exe-resource-file-generator.md) převést soubor .resx do binárního souboru prostředků (.zdroje) a také vloží do sestavení aplikace nebo satelitní sestavení.

Soubor Resx nelze vložit do spustitelného souboru za běhu ani jej zkompilovat do satelitního sestavení. Soubor Resx je nutné převést na binární soubor prostředků (.resources) pomocí [generátoru souborů prostředků (Resgen.exe).](../tools/resgen-exe-resource-file-generator.md) Výsledný soubor .resources pak může být vložen do sestavení aplikace nebo satelitního sestavení. Další informace naleznete [v tématu Creating Resource Files](creating-resource-files-for-desktop-apps.md).

## <a name="enumerate-resources"></a>Výčet prostředků
 V některých případech můžete chtít načíst všechny prostředky, namísto konkrétního prostředku, ze souboru .resx. Chcete-li to provést, <xref:System.Resources.ResXResourceReader?displayProperty=nameWithType> můžete použít třídu, která poskytuje čítač pro všechny prostředky v souboru .resx. Třída <xref:System.Resources.ResXResourceReader?displayProperty=nameWithType> implementuje <xref:System.Collections.IDictionaryEnumerator>, <xref:System.Collections.DictionaryEntry> který vrací objekt, který představuje konkrétní prostředek pro každou iteraci smyčky. Jeho <xref:System.Collections.DictionaryEntry.Key%2A?displayProperty=nameWithType> vlastnost vrátí klíč prostředku a <xref:System.Collections.DictionaryEntry.Value%2A?displayProperty=nameWithType> jeho vlastnost vrátí hodnotu prostředku.

 Následující příklad vytvoří <xref:System.Resources.ResXResourceReader> objekt pro soubor CarResources.resx vytvořený v předchozím příkladu a itetuje prostřednictvím souboru prostředků. Přidá dva `Automobile` objekty, které jsou definovány <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> v souboru prostředků k objektu <xref:System.Collections.SortedList> a přidá pět ze šesti řetězců k objektu. Hodnoty v <xref:System.Collections.SortedList> objektu jsou převedeny na pole parametrů, které slouží k zobrazení záhlaví sloupců do konzoly. Hodnoty `Automobile` vlastností jsou také zobrazeny v konzole.

 [!code-csharp[Conceptual.Resources.ResX#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.resx/cs/enumerate1.cs#2)]
 [!code-vb[Conceptual.Resources.ResX#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.resx/vb/enumerate1.vb#2)]

## <a name="retrieve-a-specific-resource"></a>Načtení konkrétního prostředku
 Kromě výčtu položek v souboru RESX můžete pomocí <xref:System.Resources.ResXResourceSet?displayProperty=nameWithType> třídy načíst určitý prostředek podle názvu. Metoda <xref:System.Resources.ResourceSet.GetString%28System.String%29?displayProperty=nameWithType> načte hodnotu prostředku pojmenovaného řetězce. Metoda <xref:System.Resources.ResourceSet.GetObject%28System.String%29?displayProperty=nameWithType> načte hodnotu pojmenovaného objektu nebo binárnídata. Metoda vrátí objekt, který pak musí být přetypován (v jazyce C#) nebo převeden (v jazyce Visual Basic) na objekt příslušného typu.

 Následující příklad načte řetězec titulků formuláře a ikonu podle názvů prostředků. Také načte objekty `Automobile` definované aplikací použité v předchozím příkladu a zobrazí je v ovládacím <xref:System.Windows.Forms.DataGridView> prvku.

 [!code-csharp[Conceptual.Resources.ResX#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.resx/cs/retrieve1.cs#3)]
 [!code-vb[Conceptual.Resources.ResX#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.resx/vb/retrieve1.vb#3)]

## <a name="convert-resx-files-to-binary-resources-files"></a>Převod souborů RESX na binární soubory .resources
 Převod souborů RESX na vložené binární soubory prostředků (.resources) má významné výhody. Přestože soubory RESX jsou snadno čitelné a udržovatběhem vývoje aplikací, jsou zřídka součástí dokončené aplikace. Pokud jsou distribuovány s aplikací, existují jako samostatné soubory kromě spustitelného souboru aplikace a jeho doprovodných knihoven. Naproti tomu soubory .resources jsou vloženy do spustitelného souboru aplikace nebo jeho doprovodných sestavení. Kromě toho pro lokalizované aplikace, spoléhání se na soubory .resx za běhu umístí odpovědnost za zpracování prostředků záložní na vývojáře. Naproti tomu pokud byla vytvořena sada satelitních sestavení, která obsahují vložené soubory prostředků ., zpracovává záložní proces jazyka.

 Chcete-li převést soubor RESX na soubor .resources, použijte [generátor souborů prostředků (Resgen.exe),](../tools/resgen-exe-resource-file-generator.md)který má následující základní syntaxi:

 **Resgen.exe** *.resxNázev_souboru*

 Výsledkem je binární soubor prostředků, který má stejný kořenový název souboru jako soubor Resx a příponu .resources. Tento soubor pak může být kompilován do spustitelného souboru nebo knihovny v době kompilace. Pokud používáte kompilátor jazyka Visual Basic, použijte následující syntaxi k vložení souboru .resources do spustitelného souboru aplikace:

 **vbc** *název souboru* **.vb -resource:** *.resourcesNázev_a.*

 Pokud používáte C#, syntaxe je následující:

 **csc** *název souboru* **.cs -resource:** *.resourcesNázev_au*

 Soubor .resources lze také vložit do satelitního sestavení pomocí [linkeru sestavení (AL.exe),](../tools/al-exe-assembly-linker.md)který má následující základní syntaxi:

 **al** *resourcesNázev* **-out:** *assemblyFilename*

## <a name="see-also"></a>Viz také

- [Vytváření zdrojových souborů](creating-resource-files-for-desktop-apps.md)
- [Resgen.exe (generátor souborů zdrojů)](../tools/resgen-exe-resource-file-generator.md)
- [Al.exe (Propojovač sestavení)](../tools/al-exe-assembly-linker.md)
