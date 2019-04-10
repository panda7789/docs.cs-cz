---
title: Vytvořit soubor prostředků pro aplikace .NET
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- resource files, .resources files
- .resources files
- application resources, creating files
- resource files, creating
ms.assetid: 6c5ad891-66a0-4e7a-adcf-f41863ba6d8d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c7ff34285220fd1e3c17503a8387104e91ec08b1
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59313655"
---
# <a name="create-resource-files-for-net-apps"></a>Vytvořit soubor prostředků pro aplikace .NET

Prostředky, jako jsou řetězce, obrázky nebo dat objektů, můžete zahrnout soubory prostředků, aby se daly snadno k dispozici pro vaši aplikaci. Rozhraní .NET Framework nabízí pět způsoby, jak vytvořit prostředky soubory:

- Vytvořte textový soubor obsahující řetězcové prostředky. Můžete použít [Resource File Generator (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) textový soubor převést na binární prostředek (.resources) souboru. Potom můžete vložit soubor binárního prostředku v spustitelný soubor aplikace nebo do knihovny aplikace pomocí kompilátoru jazyka nebo můžete vložit ho do satelitního sestavení s použitím [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md). Další informace najdete v tématu [prostředky v textových souborech](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md#TextFiles) oddílu.

- Vytvoření souboru XML prostředky (RESX), která obsahuje řetězce, image nebo data objektu. Můžete použít [Resource File Generator (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) převést soubor .resx na soubor binární prostředek (.resources). Potom můžete vložit soubor binárního prostředku v spustitelný soubor aplikace nebo do knihovny aplikace pomocí kompilátoru jazyka nebo můžete vložit ho do satelitního sestavení s použitím [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md). Další informace najdete v tématu [prostředky v souborech .resx](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md#ResxFiles) oddílu.

- Vytvoření souboru XML prostředky (RESX) prostřednictvím kódu programu pomocí typů v <xref:System.Resources> oboru názvů. Můžete vytvořit soubor .resx, výčet jeho prostředků a načíst konkrétní prostředky podle názvu. Další informace naleznete v tématu [práce s programové soubory .resx](../../../docs/framework/resources/working-with-resx-files-programmatically.md).

- Vytvořte soubor binární prostředek (.resources) prostřednictvím kódu programu. Poté můžete vložit soubor spustitelný soubor aplikace nebo do knihovny aplikace pomocí kompilátoru jazyka nebo můžete vložit ho do satelitního sestavení s použitím [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md). Další informace najdete v tématu [prostředky v souborech .resources](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md#ResourcesFiles) oddílu.

- Použití [sady Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) k vytvoření souboru prostředků a zahrnout do projektu. Visual Studio poskytuje editor prostředků, která umožňuje přidávat, odstraňovat a upravovat prostředky. V době kompilace je soubor prostředků automaticky převést na binární soubor .resources a součástí aplikace sestavení nebo satelitního sestavení. Další informace najdete v tématu [soubory prostředků v sadě Visual Studio](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md#VSResFiles) oddílu.

<a name="TextFiles"></a>
## <a name="resources-in-text-files"></a>Prostředky v textových souborech

Textové soubory (.txt nebo .restext) můžete použít k uložení pouze řetězcové prostředky. Neřetězcové prostředky použijte soubory .resx nebo je programově vytvořit. Textové soubory obsahující řetězcové prostředky mají tento formát:

```text
# This is an optional comment.
name = value

; This is another optional comment.
name = value

; The following supports conditional compilation if X is defined.
#ifdef X
name1=value1
name2=value2
#endif

# The following supports conditional compilation if Y is undefined.
#if !Y
name1=value1
name2=value2
#endif
```

 Je stejný jako formát souboru prostředku soubory .txt a .restext. Přípona souboru .restext slouží jenom k bylo okamžitě identifikovat textových souborů jako prostředek založený na textové soubory.

 Prostředky řetězců se zobrazí jako *název/hodnota* dvojice, ve kterém *název* je řetězec, který identifikuje prostředek, a *hodnotu* je řetězec prostředku, který je vrácen při předávání *název* do metody načítání zdrojů, jako <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType>. *název* a *hodnotu* musí být odděleny znaménkem rovná se (=). Příklad:

```text
FileMenuName=File
EditMenuName=Edit
ViewMenuName=View
HelpMenuName=Help
```

> [!CAUTION]
> Nepoužívejte soubory prostředků pro uložení hesel, zabezpečené informace nebo soukromá data.

 Prázdné řetězce (tedy prostředek, jehož hodnota je <xref:System.String.Empty?displayProperty=nameWithType>) jsou povolené v textových souborech. Příklad:

```
EmptyString=
```

 Spouští se s rozhraním .NET Framework 4.5 a ve všech verzích .NET Core, podporují textové soubory podmíněnou kompilaci pomocí konstrukce `#ifdef` *symbol*... `#endif` a `#if !` *symbol*... `#endif` vytvoří. Pak můžete použít `/define` přepínači s [Resource File Generator (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) definovat symboly. Jednotlivé prostředky vyžadují vlastní `#ifdef` *symbol*... `#endif` nebo `#if !` *symbol*... `#endif` vytvořit. Pokud používáte `#ifdef` příkazu a *symbol* je definován, přidružený prostředek zahrnut do souboru .resources; v opačném případě začleněn není. Pokud používáte `#if !` příkazu a *symbol* není definován, přidružený prostředek zahrnut do souboru .resources; v opačném případě začleněn není.

 Komentáře jsou nepovinné v textových souborech a před středník (;) nebo znak křížku (#) na začátku řádku. Řádky, které obsahují komentáře, může být umístěna kdekoli v souboru. Komentáře nejsou zahrnuty v souboru .resources kompilované, který je vytvořen pomocí [Resource File Generator (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md).

 Všechny prázdné řádky v textových souborech se považují za prázdné znaky a jsou ignorovány.

 Následující příklad definuje dva řetězcové prostředky s názvem `OKButton` a `CancelButton`.

```text
#Define resources for buttons in the user interface.
OKButton=OK
CancelButton=Cancel
```

 Pokud textový soubor obsahuje duplicitní výskyty prvku *název*, [Resource File Generator (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) zobrazí varování a ignoruje druhý název.

 *Hodnota* nemůže obsahovat znaky nového řádku, ale můžete použít jako řídící znaky ve stylu jazyka C `\n` představující nový řádek a `\t` představující tabulátor. Pokud není uvozeno uvozovacím znakem může také obsahovat znak zpětného lomítka (například "\\\\"). Kromě toho je povolen prázdný řetězec.

 Prostředky by měly uložit ve formátu textového souboru s použitím kódování UTF-8 nebo v obou pořadí bajtů ve formátu little endian nebo formát big-endian kódování UTF-16. Ale [Resource File Generator (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md), která převede soubor .txt do souboru .resources považuje soubory UTF-8 ve výchozím nastavení. Pokud chcete, aby Resgen.exe rozpoznal soubor, který byl zakódován pomocí kódování UTF-16, musí obsahovat Unicode značku pořadí bajtů (U + FEFF) na začátku souboru.

 Vložit soubor prostředků ve formátu textu do sestavení .NET, musíte převést soubor do souboru binárního prostředku (.resources) s použitím [Resource File Generator (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md). Potom můžete vložit do souboru .resources v sestavení .NET pomocí kompilátoru jazyka nebo ji vložit do satelitního sestavení s použitím [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md).

 Následující příklad používá soubor prostředků ve formátu textu s názvem GreetingResources.txt pro jednoduché konzolové aplikace "Hello World". Textový soubor definuje dva řetězce `prompt` a `greeting`, který vyzvat uživatele k zadejte své jméno a zobrazí pozdrav.

```text
# GreetingResources.txt
# A resource file in text format for a "Hello World" application.
#
# Initial prompt to the user.
prompt=Enter your name:
# Format string to display the result.
greeting=Hello, {0}!
```

Textový soubor je převeden na soubor .resources pomocí následujícího příkazu:

```console
resgen GreetingResources.txt
```

 Následující příklad zobrazuje zdrojový kód pro konzolovou aplikaci, která se používá k zobrazení zprávy pro uživatele do souboru .resources.

 [!code-csharp[Conceptual.Resources.TextFiles#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.textfiles/cs/greeting.cs#1)]
 [!code-vb[Conceptual.Resources.TextFiles#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.textfiles/vb/greeting.vb#1)]

 Pokud používáte Visual Basic a názvem souboru se zdrojovým kódem Greeting.vb, následující příkaz vytvoří spustitelný soubor, který obsahuje soubor .resources vložený:

```console
vbc greeting.vb -resource:GreetingResources.resources
```

 Pokud používáte C#a názvem souboru se zdrojovým kódem Greeting.cs, následující příkaz vytvoří spustitelný soubor, který obsahuje soubor .resources vložený:

 ```console
csc greeting.cs -resource:GreetingResources.resources
```

<a name="ResxFiles"></a>
## <a name="resources-in-resx-files"></a>Prostředky v souborech .resx
 Na rozdíl od textové soubory, které lze uložit pouze řetězcové prostředky, můžete ukládat soubory XML (RESX) prostředků řetězců, binární data, jako jsou obrázky, ikony a zvukových klipů a programové objekty. Soubor .resx obsahuje standardní záhlaví, která popisuje formát položky prostředků a určuje informace o verzi pro formát XML, který slouží k analýze dat. Data souboru prostředků se řídí záhlaví XML. Každá položka dat se skládá z dvojice název/hodnota, která je součástí `data` značky. Jeho `name` atribut definuje název prostředku a vnořeného `value` hodnota prostředku obsahuje značku. Pro data řetězce `value` značka obsahuje řetězec.

 Například následující `data` značky definuje řetězcový prostředek pojmenovaný `prompt` jehož hodnota je "Zadejte své jméno:".

```xml
<data name="prompt" xml:space="preserve">
  <value>Enter your name:</value>
</data>
```

> [!WARNING]
> Nepoužívejte soubory prostředků pro uložení hesel, zabezpečené informace nebo soukromá data.

 Pro objekty prostředků **data** značka zahrnuje `type` atribut, který označuje typ dat prostředku. Pro objekty, které se skládají z binární data `data` také obsahuje značku `mimetype` atribut, který označuje `base64` typu binární data.

> [!NOTE]
> Všechny soubory .resx použít pro vygenerování a analýzu binárních dat pro zadaný typ formátování binární serializace. V důsledku toho může být soubor .resx neplatný, pokud je binární serializační formát objektu se změní způsobem nekompatibilní.

 Následující příklad ukazuje část, která obsahuje soubor .resx <xref:System.Int32> prostředků a rastrový obrázek.

```xml
<data name="i1" type="System.Int32, mscorlib">
  <value>20</value>
</data>

<data name="flag" type="System.Drawing.Bitmap, System.Drawing,
    Version=1.0.5000.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"
    mimetype="application/x-microsoft.net.object.bytearray.base64">
  <value>
    AAEAAAD/////AQAAAAAAAAAMAgAAADtTeX…
  </value>
</data>
```

> [!IMPORTANT]
> Vzhledem k tomu, že musí obsahovat soubory .resx ve správném formátu XML v předdefinovanému formátu, nedoporučujeme práce se soubory .resx ručně, zejména pokud soubory .resx obsahují prostředky než řetězce. Místo toho [sady Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) nabízí transparentní rozhraní pro vytváření a manipulaci se soubory .resx. Další informace najdete v tématu [soubory prostředků v sadě Visual Studio](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md#VSResFiles) oddílu. Můžete také vytvořit a pracovat se soubory .resx programově. Další informace najdete v tématu [práce s programové soubory .resx](../../../docs/framework/resources/working-with-resx-files-programmatically.md).

<a name="ResourcesFiles"></a>
## <a name="resources-in-resources-files"></a>Prostředky v souborech .resources

Můžete použít <xref:System.Resources.ResourceWriter?displayProperty=nameWithType> třídy prostřednictvím kódu programu vytvořit soubor binární prostředek (.resources) přímo z kódu. Můžete také použít [Resource File Generator (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) vytvořte soubor .resources z textového souboru nebo souboru RESX. Soubor .resources může obsahovat binárních dat (pole bajtů) a data objektu kromě data řetězce. Programové vytvoření souboru .resources vyžaduje následující kroky:

1. Vytvoření <xref:System.Resources.ResourceWriter> objekt s jedinečným názvem souboru. Můžete to provést tak, že zadáte název souboru nebo datový proud souboru k <xref:System.Resources.ResourceWriter> konstruktoru třídy.

2. Volání jednoho z přetížení <xref:System.Resources.ResourceWriter.AddResource%2A?displayProperty=nameWithType> pro každou metodu s názvem prostředku k přidání do souboru. Prostředek může být řetězec, objekt nebo kolekci binárních dat (pole bajtů).

3. Volání <xref:System.Resources.ResourceWriter.Close%2A?displayProperty=nameWithType> metody zapsat do souboru prostředků a zavřete <xref:System.Resources.ResourceWriter> objektu.

> [!NOTE]
> Nepoužívejte soubory prostředků pro uložení hesel, zabezpečené informace nebo soukromá data.

 Následující příklad vytvoří programový soubor .resources pojmenovaný CarResources.resources, která ukládá šest řetězce, ikona a dva objekty definované aplikací (dvě `Automobile` objekty). Všimněte si, že `Automobile` třídu, která je definována a instance v příkladu, je označené <xref:System.SerializableAttribute> atribut, který umožňuje nastavit jako trvalý, binární serializace formátovacím modulem.

 [!code-csharp[Conceptual.Resources.Resources#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.resources/cs/resources1.cs#1)]
 [!code-vb[Conceptual.Resources.Resources#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.resources/vb/resources1.vb#1)]

 Když vytvoříte soubor .resources, jej můžete vložit v knihovna nebo spustitelný soubor za běhu zahrnutím kompilátor jazyka `/resource` přepnout, nebo ji vložit do satelitního sestavení s použitím [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md).

<a name="VSResFiles"></a>
## <a name="resource-files-in-visual-studio"></a>Soubory prostředků v sadě Visual Studio

Když přidáte soubor prostředků pro váš [sady Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) projektu, Visual Studio vytvoří soubor .resx v adresáři projektu. Visual Studio poskytuje editory prostředků, které vám umožní přidat řetězce, obrázky a binární objekty. Protože editorech jsou určeny ke zpracování jenom statická data, nelze je použít k ukládání programové objekty; musíte zápis dat objektů do buď soubor .resx nebo .resources souboru prostřednictvím kódu programu. Další informace najdete v tématu [práce s programové soubory .resx](../../../docs/framework/resources/working-with-resx-files-programmatically.md) a [prostředky v souborech .resources](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md#ResourcesFiles) oddílu.

Pokud přidáváte lokalizované prostředky, jim názvem kořenového souboru, hlavního souboru prostředku. Můžete také určit svoje jazykové verze v názvu souboru. Například pokud přidáte soubor prostředků pojmenovaný Resources.resx, můžete také vytvořit soubory prostředků s názvem názvy Resources.en US.resx a Resources.fr-FR.resx blokovat lokalizované prostředky pro angličtinu (Spojené státy) a Francouzština (Francie) jazykové verze, v uvedeném pořadí. Můžete také určit výchozí jazykovou verzi vaší aplikace. Toto je jazykovou verzi, jehož prostředky se použijí, pokud lze nalézt žádné lokalizované prostředky pro konkrétní jazykovou verzi. Pokud chcete zadat výchozí jazykovou verzi v Průzkumníku řešení v sadě Visual Studio, klikněte pravým tlačítkem na název projektu, přejděte na aplikace, klikněte na tlačítko **informace o sestavení**a vyberte příslušnou jazykovou verzi v **neutrální jazyk** seznamu.

V době kompilace, Visual Studio nejprve převádí soubory .resx v projektu na binární prostředek (.resources) souborů a uloží je do podadresáře projektu *obj* adresáře. Visual Studio vloží žádné soubory prostředků, které neobsahují lokalizované prostředky v hlavním sestavení, který je generován projekt. Pokud některé soubory prostředků obsahují lokalizované prostředky, je Visual Studio vloží do samostatné satelitní sestavení pro každou lokalizovanou jazykovou verzi. Pak uloží každé satelitní sestavení v adresáři, jejíž název odpovídá lokalizovanou jazykovou verzi. Například lokalizované prostředky Angličtina (Spojené státy) jsou uloženy v satelitním sestavení v podadresáři en US.

## <a name="see-also"></a>Viz také:

- <xref:System.Resources>
- [Prostředky v aplikacích klasické pracovní plochy](../../../docs/framework/resources/index.md)
- [Zabalení a nasazení prostředků](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)
