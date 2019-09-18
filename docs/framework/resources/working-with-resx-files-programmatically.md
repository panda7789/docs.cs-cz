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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7e5a57664c5d86ebf394ce026608be9a55872eb8
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71045538"
---
# <a name="working-with-resx-files-programmatically"></a>Práce se soubory. resx prostřednictvím kódu programu
Vzhledem k tomu, že soubory prostředků XML (. resx) se musí skládat z dobře definovaného kódu XML, včetně záhlaví, které musí následovat po určitém schématu následovaným daty v dvojice název/hodnota, můžete zjistit, že ruční vytváření těchto souborů je náchylné k chybám. Alternativně můžete vytvořit soubory. resx programově pomocí typů a členů v knihovně tříd .NET. Můžete také použít knihovnu tříd .NET k načtení prostředků, které jsou uloženy v souborech. resx. Toto téma vysvětluje, jak lze použít typy a členy v <xref:System.Resources> oboru názvů pro práci se soubory. resx.

 Všimněte si, že tento článek popisuje práci se soubory XML (. resx), které obsahují prostředky. Informace o práci s binárními soubory prostředků, které byly vloženy do sestavení, naleznete <xref:System.Resources.ResourceManager> v tématu.

> [!WARNING]
> Existují také způsoby, jak pracovat se soubory. resx jinými než programově. Když přidáte soubor prostředků do projektu sady [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) , Visual Studio poskytuje rozhraní pro vytvoření a údržbu souboru. resx a automaticky převede soubor. resx na soubor. Resources v době kompilace. Textový editor lze také použít k manipulaci s souborem. resx přímo. Chcete-li však zabránit poškození souboru, buďte opatrní, abyste nemuseli upravovat žádné binární informace, které jsou uloženy v souboru.

## <a name="create-a-resx-file"></a>Vytvoření souboru. resx

<xref:System.Resources.ResXResourceWriter?displayProperty=nameWithType> Třídu můžete použít k programovému vytvoření souboru. resx pomocí následujících kroků:

1. Vytvořte instanci <xref:System.Resources.ResXResourceWriter.%23ctor%28System.String%29?displayProperty=nameWithType> objektu voláním metody a zadáním názvu souboru. resx. <xref:System.Resources.ResXResourceWriter> Název souboru musí obsahovat příponu. resx. Pokud vytváříte instanci <xref:System.Resources.ResXResourceWriter> objektu `using` v bloku, nemusíte <xref:System.Resources.ResXResourceWriter.Close%2A?displayProperty=nameWithType> explicitně volat metodu v kroku 3.

2. <xref:System.Resources.ResXResourceWriter.AddResource%2A?displayProperty=nameWithType> Zavolejte metodu pro každý prostředek, který chcete přidat do souboru. Pomocí přetížení této metody můžete přidat data typu String, Object a Binary (bajtové pole). Pokud je prostředek objekt, musí být serializovatelný.

3. <xref:System.Resources.ResXResourceWriter.Close%2A?displayProperty=nameWithType> Zavolejte metodu pro vytvoření souboru prostředků a uvolnění všech prostředků. Pokud byl `using` <xref:System.Resources.ResXResourceWriter> objekt vytvořen v rámci bloku, prostředky jsou zapsány do souboru. resx a prostředky používané `using` objektem jsou uvolněny na konci bloku. <xref:System.Resources.ResXResourceWriter>

Výsledný soubor. resx má odpovídající hlavičku a `data` značku pro každý prostředek přidaný <xref:System.Resources.ResXResourceWriter.AddResource%2A?displayProperty=nameWithType> metodou.

> [!WARNING]
> Nepoužívejte soubory prostředků k ukládání hesel, informací citlivých na zabezpečení nebo soukromých dat.

Následující příklad vytvoří soubor. resx s názvem CarResources. resx, který ukládá šest řetězců, ikonu a dva objekty definované aplikací (dva `Automobile` objekty). Všimněte si, `Automobile` že třída, která je definována a vytvořena v příkladu, je označena <xref:System.SerializableAttribute> atributem.

[!code-csharp[Conceptual.Resources.ResX#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.resx/cs/create1.cs#1)]
[!code-vb[Conceptual.Resources.ResX#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.resx/vb/create1.vb#1)]

> [!TIP]
> Můžete také použít [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) k vytvoření souborů. resx. V době kompilace používá Visual Studio [generátor souboru prostředků (Resgen. exe)](../tools/resgen-exe-resource-file-generator.md) k převodu souboru. resx na binární soubor prostředků (. Resources) a také jej vloží do sestavení aplikace nebo satelitního sestavení.

Soubor. resx nelze vložit do spustitelného souboru modulu runtime nebo jej zkompilujte do satelitního sestavení. Soubor. resx je nutné převést na binární soubor prostředků (. Resources) pomocí [generátoru souboru prostředků (Resgen. exe)](../tools/resgen-exe-resource-file-generator.md). Výsledný soubor. Resources může být vložen do sestavení aplikace nebo satelitního sestavení. Další informace najdete v tématu [vytváření souborů prostředků](creating-resource-files-for-desktop-apps.md).

## <a name="enumerate-resources"></a>Zobrazení výčtu prostředků
 V některých případech můžete chtít načíst všechny prostředky namísto konkrétního prostředku ze souboru. resx. K tomu můžete použít <xref:System.Resources.ResXResourceReader?displayProperty=nameWithType> třídu, která poskytuje enumerátor pro všechny prostředky v souboru. resx. Třída implementuje <xref:System.Collections.IDictionaryEnumerator>, která vrací <xref:System.Collections.DictionaryEntry> objekt, který představuje konkrétní prostředek pro každou iteraci smyčky. <xref:System.Resources.ResXResourceReader?displayProperty=nameWithType> Jeho <xref:System.Collections.DictionaryEntry.Key%2A?displayProperty=nameWithType> vlastnost vrátí klíč prostředku a jeho <xref:System.Collections.DictionaryEntry.Value%2A?displayProperty=nameWithType> vlastnost vrátí hodnotu prostředku.

 Následující příklad vytvoří <xref:System.Resources.ResXResourceReader> objekt pro soubor CarResources. resx vytvořený v předchozím příkladu a provede iteraci v souboru prostředků. Přidá dva `Automobile` objekty, které jsou definovány v souboru <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> prostředků objektu, a přidá pět z šesti řetězců do <xref:System.Collections.SortedList> objektu. Hodnoty v <xref:System.Collections.SortedList> objektu jsou převedeny na pole parametrů, které se používá k zobrazení záhlaví sloupců v konzole. Hodnoty `Automobile` vlastností se zobrazí také v konzole nástroje.

 [!code-csharp[Conceptual.Resources.ResX#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.resx/cs/enumerate1.cs#2)]
 [!code-vb[Conceptual.Resources.ResX#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.resx/vb/enumerate1.vb#2)]

## <a name="retrieve-a-specific-resource"></a>Načtení konkrétního prostředku
 Kromě vytváření výčtu položek v souboru. resx můžete načíst konkrétní prostředek podle názvu pomocí <xref:System.Resources.ResXResourceSet?displayProperty=nameWithType> třídy. <xref:System.Resources.ResourceSet.GetString%28System.String%29?displayProperty=nameWithType> Metoda načte hodnotu prostředku pojmenovaného řetězce. <xref:System.Resources.ResourceSet.GetObject%28System.String%29?displayProperty=nameWithType> Metoda načte hodnotu pojmenovaného objektu nebo binárních dat. Metoda vrátí objekt, který musí být poté převeden (in C#) nebo převeden (v Visual Basic) na objekt příslušného typu.

 V následujícím příkladu je načten řetězec a ikona v podobě titulků formuláře podle jejich názvů prostředků. Také načte objekty definované `Automobile` aplikací, které jsou použity v předchozím příkladu, a zobrazí je <xref:System.Windows.Forms.DataGridView> v ovládacím prvku.

 [!code-csharp[Conceptual.Resources.ResX#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.resx/cs/retrieve1.cs#3)]
 [!code-vb[Conceptual.Resources.ResX#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.resx/vb/retrieve1.vb#3)]

## <a name="convert-resx-files-to-binary-resources-files"></a>Převod souborů. resx do binárních souborů. Resources
 Převod souborů. resx na vložené soubory binárních prostředků (. Resources) má významné výhody. I když se soubory. resx snadno čtou a udržují během vývoje aplikací, jsou v rámci dokončených aplikací zřídka zahrnuty. Pokud jsou distribuovány s aplikací, existují jako samostatné soubory kromě spustitelného souboru aplikace a jeho doprovodných knihoven. Naproti tomu soubory. Resources jsou vloženy do spustitelného souboru aplikace nebo do jeho doprovodných sestavení. Kromě toho pro lokalizované aplikace, které se spoléhají na soubory. resx za běhu, umístí zodpovědnost za zpracování záložního prostředku na vývojáře. Naproti tomu, pokud byla vytvořena sada satelitních sestavení, která obsahují vložené soubory. Resources, modul CLR zpracuje proces záložního prostředku.

 Chcete-li převést soubor. resx na soubor. Resources, použijte nástroj [Resource File Generator (Resgen. exe)](../tools/resgen-exe-resource-file-generator.md), který má následující základní syntaxi:

 **Resgen.exe** *.resxFilename*

 Výsledkem je binární soubor prostředků, který má stejný název kořenového souboru jako soubor. resx a příponu souboru. Resources. Tento soubor lze následně zkompilovat do spustitelného souboru nebo knihovny v době kompilace. Pokud používáte kompilátor Visual Basic, použijte následující syntaxi pro vložení souboru. Resources do spustitelného souboru aplikace:

 **Vbc** *název souboru* **. vb – prostředek:** *. resourcesFilename*

 Pokud používáte C#, syntaxe je následující:

 **CSC** *název souboru* **. cs – prostředek:** *. resourcesFilename*

 Soubor. Resources může být také vložen do satelitního sestavení pomocí [linkeru sestavení (Al. exe)](../tools/al-exe-assembly-linker.md), který má následující základní syntaxi:

 **Al** *resourcesFilename* **-out:** *assemblyFilename*

## <a name="see-also"></a>Viz také:

- [Vytváření zdrojových souborů](creating-resource-files-for-desktop-apps.md)
- [Resgen.exe (generátor zdrojových souborů)](../tools/resgen-exe-resource-file-generator.md)
- [Al.exe (linker sestavení)](../tools/al-exe-assembly-linker.md)
