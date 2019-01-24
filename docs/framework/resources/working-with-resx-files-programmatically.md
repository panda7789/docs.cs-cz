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
ms.openlocfilehash: 0c13a00ddad974ebba8eea4fceddd6a9fe3ed942
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54597577"
---
# <a name="working-with-resx-files-programmatically"></a>Práce se soubory .resx programově
Vzhledem k tomu, že soubory XML prostředky (RESX) se musí skládat z dobře definovaných XML, včetně záhlaví, které musí dodržovat konkrétní schéma a data v dvojice název/hodnota, můžete zjistit, že je náchylný ruční vytvoření těchto souborů. Jako alternativu můžete vytvořit soubory .resx programově pomocí typy a členy v knihovně tříd rozhraní .NET Framework. Můžete také použít knihovny tříd rozhraní .NET Framework pro načtení prostředků, které jsou uloženy v souborech .resx. Toto téma vysvětluje, jak můžete použít typy a členy v <xref:System.Resources> obor názvů pro práci se soubory .resx.  
  
 Všimněte si, že tento článek popisuje práci s XML (.resx) soubory, které obsahují prostředky. Informace o práci se soubory binárních prostředků, které byly vloženy do sestavení, najdete v článku <xref:System.Resources.ResourceManager> tématu.  
  
> [!WARNING]
>  Existují také způsoby, jak pracovat se soubory .resx jiné než prostřednictvím kódu programu. Když přidáte soubor prostředků do projektu sady Visual Studio, Visual Studio poskytuje rozhraní pro vytvoření a údržbu soubor .resx a automaticky převádí soubory .resx na soubor .resources v době kompilace. Textového editoru můžete použít také k manipulaci s soubor .resx přímo. Nicméně aby nedošlo k poškození souboru, dejte pozor, abyste upravte libovolné binární informace, která je uložena v souboru.  
  
## <a name="creating-a-resx-file"></a>Vytvoření souboru .resx  
 Můžete použít <xref:System.Resources.ResXResourceWriter?displayProperty=nameWithType> třídy za účelem vytvoření souboru .resx programově, pomocí následujících kroků:  
  
1.  Vytvořit instanci <xref:System.Resources.ResXResourceWriter> objektu voláním <xref:System.Resources.ResXResourceWriter.%23ctor%28System.String%29?displayProperty=nameWithType> metoda a zadáním názvu souboru .resx. Název souboru musí obsahovat příponou .resx. Pokud vytvoříte instanci <xref:System.Resources.ResXResourceWriter> objekt `using` bloku, není nutné explicitně volat <xref:System.Resources.ResXResourceWriter.Close%2A?displayProperty=nameWithType> metoda v kroku 3.  
  
2.  Volání <xref:System.Resources.ResXResourceWriter.AddResource%2A?displayProperty=nameWithType> metodu pro jednotlivé prostředky, které chcete přidat do souboru. Použijte přetížení této metody přidat řetězec, objekt a data binárního souboru (pole bajtů). Pokud prostředek je objekt, musí být serializovatelný.  
  
3.  Volání <xref:System.Resources.ResXResourceWriter.Close%2A?displayProperty=nameWithType> metoda ke generování souboru prostředků a uvolnit všechny prostředky. Pokud <xref:System.Resources.ResXResourceWriter> objekt byl vytvořen v rámci `using` bloku, prostředky se zapisují do souboru .resx a prostředky využívané třídou <xref:System.Resources.ResXResourceWriter> jsou na konci uvolnění objektu `using` bloku.  
  
 Výsledný soubor .resx obsahuje odpovídající hlavičku a `data` značky pro každý prostředek přidal <xref:System.Resources.ResXResourceWriter.AddResource%2A?displayProperty=nameWithType> metody.  
  
> [!WARNING]
>  Nepoužívejte soubory prostředků pro uložení hesel, zabezpečené informace nebo soukromá data.  
  
 Následující příklad vytvoří soubor .resx CarResources.resx, který ukládá šesti řetězce, ikona a dva objekty definované aplikací (dvě `Automobile` objekty). Všimněte si, že `Automobile` třídu, která je definována a instance v příkladu, je označené <xref:System.SerializableAttribute> atribut.  
  
 [!code-csharp[Conceptual.Resources.ResX#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.resx/cs/create1.cs#1)]
 [!code-vb[Conceptual.Resources.ResX#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.resx/vb/create1.vb#1)]  
  
> [!IMPORTANT]
>  Visual Studio můžete také vytvořit soubory .resx. V době kompilace, použije sada Visual Studio [Resource File Generator (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) převést soubor .resx na binární prostředek (.resources) souboru a také vloží sestavení aplikace nebo satelitního sestavení.  
  
 Nelze vložit do spustitelného souboru .resx nebo kompiloval do satelitního sestavení. Je nutné převést soubor RESX do souboru binárního prostředku (.resources) s použitím [Resource File Generator (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md). Výsledný soubor .resources by pak může být vložen do sestavení aplikace nebo satelitního sestavení. Další informace najdete v tématu [Creating Resource Files](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md).  
  
## <a name="enumerating-resources"></a>Vytváření výčtu zdroje  
 V některých případech můžete chtít načíst všechny prostředky, místo konkrétního prostředku, ze souboru RESX. K tomuto účelu můžete použít <xref:System.Resources.ResXResourceReader?displayProperty=nameWithType> třídu, která poskytuje enumerátor pro všechny prostředky v souboru .resx. <xref:System.Resources.ResXResourceReader?displayProperty=nameWithType> Implementuje třída <xref:System.Collections.IDictionaryEnumerator>, který vrátí hodnotu <xref:System.Collections.DictionaryEntry> objekt, který představuje určitý prostředek pro každou iteraci smyčky. Jeho <xref:System.Collections.DictionaryEntry.Key%2A?displayProperty=nameWithType> vrátí vlastnost prostředku klíč a jeho <xref:System.Collections.DictionaryEntry.Value%2A?displayProperty=nameWithType> vlastnost vrací hodnotu zdroje.  
  
 Následující příklad vytvoří <xref:System.Resources.ResXResourceReader> objekt pro CarResources.resx soubor vytvořený v předchozím příkladu a iteruje souboru prostředků. Sečte dva `Automobile` objekty, které jsou definovány v souboru prostředků na <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> objektu a přidá pět šest řetězců <xref:System.Collections.SortedList> objektu. Hodnoty <xref:System.Collections.SortedList> objekt je převést na pole parametrů, které slouží k zobrazení záhlaví sloupců do konzoly. `Automobile` Hodnoty vlastností se také zobrazí v konzole.  
  
 [!code-csharp[Conceptual.Resources.ResX#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.resx/cs/enumerate1.cs#2)]
 [!code-vb[Conceptual.Resources.ResX#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.resx/vb/enumerate1.vb#2)]  
  
## <a name="retrieving-a-specific-resource"></a>Načítání konkrétního prostředku  
 Kromě spočítání položek v souboru .resx, můžete konkrétní prostředek načíst podle názvu pomocí <xref:System.Resources.ResXResourceSet?displayProperty=nameWithType> třídy. <xref:System.Resources.ResourceSet.GetString%28System.String%29?displayProperty=nameWithType> Metoda načte hodnotu řetězce s názvem prostředku. <xref:System.Resources.ResourceSet.GetObject%28System.String%29?displayProperty=nameWithType> Metoda načte hodnotu pojmenovaný objekt nebo binární data. Metoda vrátí objekt, který pak musí být přetypovat (v C#) nebo (v jazyce Visual Basic) převést na objekt příslušného typu.  
  
 Následující příklad načte formuláře titulek řetězec a ikonu podle svých názvů prostředků. Také načte definovaného aplikací `Automobile` objekty použité v předchozím příkladu a zobrazí je v <xref:System.Windows.Forms.DataGridView> ovládacího prvku.  
  
 [!code-csharp[Conceptual.Resources.ResX#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.resx/cs/retrieve1.cs#3)]
 [!code-vb[Conceptual.Resources.ResX#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.resx/vb/retrieve1.vb#3)]  
  
## <a name="converting-resx-files-to-binary-resources-files"></a>Převod souborů .resx na binárních souborů .resources  
 Převod souborů .resx na soubory vložené binární prostředek (.resources) má významné výhody. Přestože jsou soubory .resx snadno číst a spravovat během vývoje aplikace, jsou zřídka součástí hotové aplikace. Pokud jsou distribuovány do aplikace, existují jako samostatné soubory kromě spustitelný soubor aplikace a její související knihovny. Soubory .resources naproti tomu jsou vloženy do spustitelného souboru aplikace nebo jeho související sestavení. Kromě toho v případě lokalizovaných aplikací spoléhá na soubory .resx na místa v době běhu zodpovědnost za zpracování prostředků záložní na vývojáře. Naopak pokud vytvořil sadu satelitní sestavení, které obsahují soubory .resources vložený modul common language runtime zpracovává proces získávání náhradních prostředků.  
  
 Chcete-li převést soubory .resx na soubor .resources, je použít [Resource File Generator (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md), který má následující základní syntaxe:  
  
 **Resgen.exe** *.resxFilename*  
  
 Výsledkem je na binární soubor prostředků, který má stejný název souboru kořenový soubor RESX a příponu souboru .resources. Tento soubor může být poté zkompilován do spustitelného souboru nebo knihovny v době kompilace. Pokud používáte kompilátor jazyka Visual Basic, vložíte soubor .resources na spustitelný soubor aplikace použijte následující syntaxi:  
  
 **Vbc –** *filename* **.vb-resource:** *.resourcesFilename*  
  
 Pokud používáte C#, syntaxe vypadá takto:  
  
 **CSC** *filename* **.cs-resource:** *.resourcesFilename*  
  
 Soubor .resources můžete také vložit do satelitního sestavení s použitím [Assembly Linker (AL.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md), který má následující základní syntaxe:  
  
 **Al** *resourcesFilename* **-out:** *assemblyFilename*  
  
## <a name="see-also"></a>Viz také:
- [Vytváření zdrojových souborů](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md)
- [Resgen.exe (generátor zdrojových souborů)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md)
- [Al.exe (linker sestavení)](../../../docs/framework/tools/al-exe-assembly-linker.md)
