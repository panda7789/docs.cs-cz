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
ms.openlocfilehash: 569f2d59bb2abf013a87bdaa694a7fcf36c70042
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33398830"
---
# <a name="working-with-resx-files-programmatically"></a>Práce se soubory .resx programově
Protože soubory XML prostředků (RESX) musí obsahovat přesně vymezené XML, včetně hlavičku, která musí odpovídat určitému schématu následuje data v dvojice název/hodnota, můžete zjistit, že ruční vytvoření těchto souborů je k chybám. Jako alternativu můžete vytvořit soubory .resx programově pomocí typy a členy v knihovně tříd rozhraní .NET Framework. Knihovna tříd rozhraní .NET Framework můžete použít také k načtení prostředků, které jsou uložené v soubory RESX. Toto téma vysvětluje, jak můžete použít typy a členy v <xref:System.Resources> obor názvů pro práci se soubory .resx.  
  
 Všimněte si, že tento článek popisuje práce s XML (RESX) soubory, které obsahují prostředky. Informace o práci se soubory binárního prostředku, které byly vloženy do sestavení najdete v tématu <xref:System.Resources.ResourceManager> tématu.  
  
> [!WARNING]
>  Existují také způsoby, jak pracovat se soubory .resx jiné než prostřednictvím kódu programu. Když přidáte souboru prostředků pro projekt sady Visual Studio, Visual Studio poskytuje rozhraní pro vytváření a údržbu soubor .resx a automaticky převede soubor .resx do souboru .resources v době kompilace. Můžete také textového editoru k manipulaci s souboru RESX přímo. Pokud ale pokud chcete vyhnout poškození souboru, buďte pozor, abyste všechny binární informace, které je uložený v souboru.  
  
## <a name="creating-a-resx-file"></a>Vytvoření souboru RESX  
 Můžete použít <xref:System.Resources.ResXResourceWriter?displayProperty=nameWithType> třídy za účelem vytvoření soubor .resx programově pomocí následujících kroků:  
  
1.  Vytváření instancí <xref:System.Resources.ResXResourceWriter> objekt voláním <xref:System.Resources.ResXResourceWriter.%23ctor%28System.String%29?displayProperty=nameWithType> metoda a zadáním názvu souboru RESX. Název souboru musí obsahovat rozšíření resx. Pokud vytvoříte instanci <xref:System.Resources.ResXResourceWriter> objekt v `using` bloku, není nutné explicitně k volání <xref:System.Resources.ResXResourceWriter.Close%2A?displayProperty=nameWithType> metoda v kroku 3.  
  
2.  Volání <xref:System.Resources.ResXResourceWriter.AddResource%2A?displayProperty=nameWithType> metodu pro každý prostředek, který chcete přidat do souboru. Použijte přetížení této metody přidat řetězec, objekt a data binárního souboru (pole bajtů). Pokud je objekt, musí být serializovatelný.  
  
3.  Volání <xref:System.Resources.ResXResourceWriter.Close%2A?displayProperty=nameWithType> metoda generování souboru prostředků a uvolní všechny prostředky. Pokud <xref:System.Resources.ResXResourceWriter> objekt byl vytvořen v rámci `using` bloku, prostředky se zapisují do souboru RESX a prostředky používané <xref:System.Resources.ResXResourceWriter> objekt vydávají na konci `using` bloku.  
  
 Výsledný soubor .resx má vhodné záhlaví a `data` značky pro každý prostředek přidaný <xref:System.Resources.ResXResourceWriter.AddResource%2A?displayProperty=nameWithType> metoda.  
  
> [!WARNING]
>  Nepoužívejte soubory prostředků pro uložení hesla, informace citlivé na zabezpečení nebo osobní data.  
  
 Následující příklad vytvoří soubor .resx s názvem CarResources.resx, který ukládá šest řetězců, ikonu a dva objekty definované aplikací (dva `Automobile` objektů). Všimněte si, že `Automobile` třída, která je definována a vytvoření instance v příkladu, je označené <xref:System.SerializableAttribute> atribut.  
  
 [!code-csharp[Conceptual.Resources.ResX#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.resx/cs/create1.cs#1)]
 [!code-vb[Conceptual.Resources.ResX#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.resx/vb/create1.vb#1)]  
  
> [!IMPORTANT]
>  Visual Studio můžete také vytvořit soubory RESX. Při kompilaci, Visual Studio použije [Generátor zdrojových souborů (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) převést soubor .resx binárního prostředku (.resources) souboru a také se vloží do sestavení aplikace nebo satelitní sestavení.  
  
 Nelze vložit spustitelného souboru RESX nebo kompilována satelitní sestavení. Je nutné převést svůj soubor .resx do souboru binárního prostředku (.resources) pomocí [Generátor zdrojových souborů (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md). Výsledný soubor .resources můžete pak vložit do sestavení aplikace nebo sestavu satelitu. Další informace najdete v tématu [vytváření souborů prostředků](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md).  
  
## <a name="enumerating-resources"></a>Vytváření výčtů prostředků  
 V některých případech můžete načíst všechny prostředky, místo konkrétního prostředku ze souboru RESX. Chcete-li to provést, můžete použít <xref:System.Resources.ResXResourceReader?displayProperty=nameWithType> třídy, která poskytuje enumerátor pro všechny prostředky v souboru RESX. <xref:System.Resources.ResXResourceReader?displayProperty=nameWithType> Třída implementuje <xref:System.Collections.IDictionaryEnumerator>, která vrátí <xref:System.Collections.DictionaryEntry> objekt, který reprezentuje určitý prostředek pro každou iteraci smyčky. Jeho <xref:System.Collections.DictionaryEntry.Key%2A?displayProperty=nameWithType> vlastnost vrací klíč zdroje a jeho <xref:System.Collections.DictionaryEntry.Value%2A?displayProperty=nameWithType> vlastnost vrací hodnotu zdroje.  
  
 Následující příklad vytvoří <xref:System.Resources.ResXResourceReader> objekt pro soubor CarResources.resx vytvořený v předchozím příkladu a iteruje souboru prostředků. Přidá dva `Automobile` objekty, které jsou definovány v souboru prostředků pro <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> objektu a přidá pět šesti řetězců do <xref:System.Collections.SortedList> objektu. Hodnoty <xref:System.Collections.SortedList> objekt se převedou na pole parametrů, které se používá k zobrazení záhlaví sloupců do konzoly. `Automobile` Hodnot vlastností se také zobrazí konzole.  
  
 [!code-csharp[Conceptual.Resources.ResX#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.resx/cs/enumerate1.cs#2)]
 [!code-vb[Conceptual.Resources.ResX#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.resx/vb/enumerate1.vb#2)]  
  
## <a name="retrieving-a-specific-resource"></a>Načítání určitého zdroje  
 Kromě vytváření výčtu položek v souboru RESX, můžete načíst konkrétní prostředek podle názvu pomocí <xref:System.Resources.ResXResourceSet?displayProperty=nameWithType> třídy. <xref:System.Resources.ResourceSet.GetString%28System.String%29?displayProperty=nameWithType> Metoda načte hodnotu prostředek s názvem řetězce. <xref:System.Resources.ResourceSet.GetObject%28System.String%29?displayProperty=nameWithType> Metoda načítá hodnotu s názvem objektu nebo binární data. Metoda vrátí objekt, který musí být pak přetypování (v C#) nebo (v jazyce Visual Basic) převést na objekt příslušného typu.  
  
 Následující příklad načte řetězec titulku formuláře a ikona podle jejich názvy prostředků. Také načte definované aplikací `Automobile` objekty použít v předchozím příkladu a zobrazí je v <xref:System.Windows.Forms.DataGridView> ovládacího prvku.  
  
 [!code-csharp[Conceptual.Resources.ResX#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.resx/cs/retrieve1.cs#3)]
 [!code-vb[Conceptual.Resources.ResX#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.resx/vb/retrieve1.vb#3)]  
  
## <a name="converting-resx-files-to-binary-resources-files"></a>Převod souborů RESX na binární soubory RESOURCES  
 Převod souborů RESX na soubory embedded binárního prostředku (.resources) má významné výhody. I když jsou soubory RESX snadno přečíst a udržovat během vývoje aplikace, jsou zřídka součástí dokončení aplikací. Pokud jsou distribuovány s aplikací, které jsou jako samostatné soubory kromě spustitelný soubor aplikace a jeho doprovodných knihoven. Soubory .resources jsou naopak součástí spustitelný soubor aplikace nebo jeho doprovodných sestavení. Kromě toho pro lokalizované aplikace spoléhat na soubory RESX náhradních za zpracování prostředků zodpovědný vývojář. Naproti tomu pokud vytvořil sadu satelitní sestavení, které obsahují soubory embedded .resources modul common language runtime zpracovává nouzového procesu prostředků.  
  
 Chcete-li převést soubor .resx do souboru .resources, použijte [Generátor zdrojových souborů (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md), který má základní syntaxi:  
  
 **Resgen.exe** *.resxFilename*  
  
 Výsledkem je soubor binárního prostředku, který má stejný název kořenové jako soubor .resx a příponu souboru .resources. Tento soubor můžete poté zkompilovány do spustitelného souboru nebo knihovny v době kompilace. Pokud používáte Visual Basic – kompilátor, použijte následující syntaxi souboru .resources vložit do aplikace spustitelný soubor:  
  
 **Vbc –** *filename* **VB-prostředků:** *.resourcesFilename*  
  
 Pokud používáte C#, syntaxe vypadá takto:  
  
 **CSC** *filename* **.cs-prostředků:** *.resourcesFilename*  
  
 Souboru .resources lze také vložit v satelitní sestavení pomocí [Linker sestavení (AL.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md), který má základní syntaxi:  
  
 **Al** *resourcesFilename* **-out:** *assemblyFilename*  
  
## <a name="see-also"></a>Viz také  
 [Vytváření zdrojových souborů](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md)  
 [Resgen.exe (generátor zdrojových souborů)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md)  
 [Al.exe (linker sestavení)](../../../docs/framework/tools/al-exe-assembly-linker.md)
