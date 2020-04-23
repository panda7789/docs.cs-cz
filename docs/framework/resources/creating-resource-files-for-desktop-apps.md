---
title: Vytváření souborů prostředků pro aplikace .NET
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
ms.openlocfilehash: b679539be1aeb593124eb35a235bcc578decb4c0
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111774"
---
# <a name="create-resource-files-for-net-apps"></a>Vytváření souborů prostředků pro aplikace .NET

Do souborů prostředků můžete zahrnout prostředky, jako jsou řetězce, obrázky nebo data objektů, aby byly pro vaši aplikaci snadno dostupné. .NET Framework nabízí pět způsobů, jak vytvářet soubory prostředků:

- Vytvořte textový soubor, který obsahuje řetězcové prostředky. Pomocí [generátoru souboru prostředků (Resgen. exe)](../tools/resgen-exe-resource-file-generator.md) můžete převést textový soubor na binární soubor prostředků (. Resources). Pak můžete vložit binární soubor prostředků do spustitelného souboru aplikace nebo knihovny aplikace pomocí kompilátoru jazyka, nebo jej můžete vložit do satelitního sestavení pomocí [linkeru sestavení (Al. exe)](../tools/al-exe-assembly-linker.md). Další informace najdete v části [prostředky v textových souborech](creating-resource-files-for-desktop-apps.md#TextFiles) .

- Vytvořte soubor prostředků XML (. resx), který obsahuje data o řetězci, obrázku nebo objektu. Můžete použít [generátor souboru prostředků (Resgen. exe)](../tools/resgen-exe-resource-file-generator.md) k převedení souboru. resx na binární soubor prostředků (. Resources). Pak můžete vložit binární soubor prostředků do spustitelného souboru aplikace nebo knihovny aplikace pomocí kompilátoru jazyka, nebo jej můžete vložit do satelitního sestavení pomocí [linkeru sestavení (Al. exe)](../tools/al-exe-assembly-linker.md). Další informace naleznete v části [prostředky v souborech. resx](creating-resource-files-for-desktop-apps.md#ResxFiles) .

- Vytvořte soubor prostředků XML (. resx) programově pomocí typů v <xref:System.Resources> oboru názvů. Můžete vytvořit soubor. resx, zobrazit výčet jeho prostředků a načíst konkrétní prostředky podle názvu. Další informace naleznete v tématu [práce se soubory. resx programově](working-with-resx-files-programmatically.md).

- Vytvořte soubor binárního prostředku (. Resources) programově. Pak můžete soubor vložit do spustitelného souboru aplikace nebo knihovny aplikace pomocí kompilátoru jazyka, nebo jej můžete vložit do satelitního sestavení pomocí [linkeru sestavení (Al. exe)](../tools/al-exe-assembly-linker.md). Další informace najdete v části [prostředky v souborech. Resources](creating-resource-files-for-desktop-apps.md#ResourcesFiles) .

- Pomocí sady [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) vytvořte soubor prostředků a přidejte ho do projektu. Visual Studio poskytuje editor prostředků, který umožňuje přidávat, odstraňovat a upravovat prostředky. V době kompilace je soubor prostředků automaticky převeden do binárního souboru. Resources a vložen do sestavení aplikace nebo satelitního sestavení. Další informace naleznete v části [soubory prostředků v aplikaci Visual Studio](creating-resource-files-for-desktop-apps.md#VSResFiles) .

<a name="TextFiles"></a>
## <a name="resources-in-text-files"></a>Prostředky v textových souborech

Soubory textu (. txt nebo. restext) můžete použít pouze k uložení řetězcových prostředků. Pro prostředky, které nejsou řetězcem, použijte soubory. resx nebo je vytvořte programově. Textové soubory, které obsahují řetězcové prostředky, mají následující formát:

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

 Formát souboru prostředků souborů. txt a. restext je identický. Přípona souboru. restext slouží pouze k okamžité identifikaci textových souborů jako souborů prostředků založených na textu.

 Prostředky řetězců se zobrazí jako páry *název-hodnota* , kde *název* je řetězec, který identifikuje prostředek, a *hodnota* je řetězec prostředku, který je vrácen při předání *názvu* metodě načtení prostředku, jako je například <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType>. *název* a *hodnota* musí být odděleny symbolem rovná se (=). Příklad:

```text
FileMenuName=File
EditMenuName=Edit
ViewMenuName=View
HelpMenuName=Help
```

> [!CAUTION]
> Nepoužívejte soubory prostředků k ukládání hesel, informací citlivých na zabezpečení nebo soukromých dat.

 Prázdné řetězce (tj. prostředek, jehož hodnota je <xref:System.String.Empty?displayProperty=nameWithType>) jsou povoleny v textových souborech. Příklad:

```text
EmptyString=
```

 Počínaje .NET Framework 4,5 a ve všech verzích .NET Core podporuje textové soubory podmíněnou kompilaci se `#ifdef` *symbolem*... `#endif` a `#if !` *symbol*... `#endif` konstrukce. Pak můžete použít `/define` přepínač se [generátorem souboru prostředků (Resgen. exe)](../tools/resgen-exe-resource-file-generator.md) k definování symbolů. Každý prostředek vyžaduje vlastní `#ifdef` *symbol*... `#endif` nebo `#if !` *symbol*... `#endif` konstrukce. Pokud použijete `#ifdef` příkaz a *symbol* , je přidružený prostředek zahrnut do souboru. Resources; v opačném případě není zahrnutý. Použijete-li `#if !` příkaz a *symbol* není definován, je přidružený prostředek zahrnut do souboru. Resources; v opačném případě není zahrnutý.

 Komentáře jsou v textových souborech volitelné a předcházejí středníkem (;) nebo znak křížku (#) na začátku řádku. Řádky, které obsahují komentáře, mohou být umístěny kdekoli v souboru. Komentáře nejsou zahrnuty v kompilovaném souboru. Resources, který je vytvořen pomocí [generátoru souboru prostředků (Resgen. exe)](../tools/resgen-exe-resource-file-generator.md).

 Všechny prázdné řádky v textových souborech jsou považovány za prázdné znaky a jsou ignorovány.

 Následující příklad definuje dva řetězcové prostředky s `OKButton` názvem `CancelButton`a.

```text
#Define resources for buttons in the user interface.
OKButton=OK
CancelButton=Cancel
```

 Pokud textový soubor obsahuje duplicitní výskyty *názvu*, [generátor souboru prostředků (Resgen. exe)](../tools/resgen-exe-resource-file-generator.md) zobrazí upozornění a ignoruje druhý název.

 *hodnota* nesmí obsahovat znaky nového řádku, ale můžete použít řídicí znaky jazyka C, jako je například `\n` , aby představovaly nový řádek a `\t` představovala kartu. Znak zpětného lomítka můžete také zahrnout, pokud je řídicí sekvence (například "\\\\"). Kromě toho je povolen prázdný řetězec.

 Pomocí kódování UTF-8 nebo UTF-16 můžete ukládat prostředky ve formátu textového souboru v řádu Little endian nebo big-endian bajtů. [Resource File Generator (Resgen. exe)](../tools/resgen-exe-resource-file-generator.md), který převede soubor. txt na soubor. Resources, považuje ve výchozím nastavení soubory jako UTF-8. Pokud chcete, aby nástroj Resgen. exe rozpoznal soubor, který byl kódovaný pomocí kódování UTF-16, musíte na začátku souboru použít znak pořadí bajtů Unicode (U + FEFF).

 Chcete-li vložit soubor prostředků v textovém formátu do sestavení .NET, je nutné převést soubor do binárního souboru prostředků (. Resources) pomocí [generátoru souboru prostředků (Resgen. exe)](../tools/resgen-exe-resource-file-generator.md). Pak můžete vložit soubor. Resources do sestavení .NET pomocí kompilátoru jazyka nebo ho vložit do satelitního sestavení pomocí [linkeru sestavení (Al. exe)](../tools/al-exe-assembly-linker.md).

 Následující příklad používá soubor prostředků v textovém formátu s názvem GreetingResources. txt pro jednoduchou konzolovou aplikaci "Hello World". Textový soubor definuje dva řetězce, `prompt` a `greeting`, které vyzvat uživatele k zadání jména a zobrazení pozdravu.

```text
# GreetingResources.txt
# A resource file in text format for a "Hello World" application.
#
# Initial prompt to the user.
prompt=Enter your name:
# Format string to display the result.
greeting=Hello, {0}!
```

Textový soubor je převeden na soubor. Resources pomocí následujícího příkazu:

```console
resgen GreetingResources.txt
```

 Následující příklad ukazuje zdrojový kód pro konzolovou aplikaci, která používá soubor. Resources pro zobrazení zpráv uživateli.

 [!code-csharp[Conceptual.Resources.TextFiles#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.textfiles/cs/greeting.cs#1)]
 [!code-vb[Conceptual.Resources.TextFiles#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.textfiles/vb/greeting.vb#1)]

 Pokud používáte Visual Basic a soubor zdrojového kódu se nazývá pozdrav. vb, následující příkaz vytvoří spustitelný soubor, který obsahuje vložený soubor. Resources:

```console
vbc greeting.vb -resource:GreetingResources.resources
```

 Pokud používáte jazyk C# a soubor zdrojového kódu má název Greeting.cs, následující příkaz vytvoří spustitelný soubor, který obsahuje soubor vloženého souboru. Resources:

```console
csc greeting.cs -resource:GreetingResources.resources
```

<a name="ResxFiles"></a>
## <a name="resources-in-resx-files"></a>Prostředky v souborech. resx
 Na rozdíl od textových souborů, které mohou ukládat pouze řetězcové prostředky, soubory prostředků XML (. resx) mohou ukládat řetězce, binární data, jako jsou obrázky, ikony, zvukové klipy a programové objekty. Soubor. resx obsahuje standardní hlavičku, která popisuje formát položek prostředku a určuje informace o verzích pro XML, které se používají k analýze dat. Data souboru prostředků se řídí hlavičkou XML. Každá datová položka se skládá z dvojice název/hodnota, která je obsažena `data` ve značce. Jeho `name` atribut definuje název prostředku a vnořená `value` značka obsahuje hodnotu prostředku. V `value` případě řetězcových dat značka obsahuje řetězec.

 Například následující `data` značka definuje prostředek řetězce s názvem `prompt` , jehož hodnota je "zadejte vaše jméno:".

```xml
<data name="prompt" xml:space="preserve">
  <value>Enter your name:</value>
</data>
```

> [!WARNING]
> Nepoužívejte soubory prostředků k ukládání hesel, informací citlivých na zabezpečení nebo soukromých dat.

 Pro objekty prostředků obsahuje **datová** značka `type` atribut, který označuje datový typ prostředku. Pro objekty, které se skládají z binárních `data` dat, značka také `mimetype` obsahuje atribut, který označuje `base64` typ binárních dat.

> [!NOTE]
> Všechny soubory RESX používají formátovací modul binární serializace pro generování a analýzu binárních dat zadaného typu. V důsledku toho může být soubor. resx neplatným, pokud se formát binární serializace objektu změní nekompatibilním způsobem.

 Následující příklad ukazuje část souboru. resx, který obsahuje <xref:System.Int32> prostředek a rastrový obrázek.

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
> Vzhledem k tomu, že soubory. resx musí být ve správném formátu XML, nedoporučujeme pracovat se soubory. resx ručně, zejména v případě, že soubory. resx obsahují jiné prostředky než řetězce. Místo toho [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) poskytuje transparentní rozhraní pro vytváření a manipulaci se soubory. resx. Další informace naleznete v části [soubory prostředků v aplikaci Visual Studio](creating-resource-files-for-desktop-apps.md#VSResFiles) . Můžete také vytvořit a manipulovat soubory. resx programově. Další informace naleznete v tématu [práce se soubory. resx programově](working-with-resx-files-programmatically.md).

<a name="ResourcesFiles"></a>
## <a name="resources-in-resources-files"></a>Prostředky v souborech. Resources

<xref:System.Resources.ResourceWriter?displayProperty=nameWithType> Třídu můžete použít k programovému vytvoření binárního souboru prostředků (. Resources) přímo z kódu. Nástroj [Resource File Generator (Resgen. exe)](../tools/resgen-exe-resource-file-generator.md) můžete také použít k vytvoření souboru. Resources z textového souboru nebo souboru. resx. Soubor. Resources může obsahovat binární data (pole bajtů) a data objektů kromě řetězcových dat. Programové vytváření souboru. resources vyžaduje následující kroky:

1. Vytvořte <xref:System.Resources.ResourceWriter> objekt s jedinečným názvem souboru. To lze provést zadáním názvu souboru nebo datového proudu souboru konstruktoru <xref:System.Resources.ResourceWriter> třídy.

2. Zavolejte jedno z přetížení <xref:System.Resources.ResourceWriter.AddResource%2A?displayProperty=nameWithType> metody pro každý pojmenovaný prostředek, který chcete přidat do souboru. Prostředkem může být řetězec, objekt nebo kolekce binárních dat (bajtové pole).

3. Zavolejte <xref:System.Resources.ResourceWriter.Close%2A?displayProperty=nameWithType> metodu pro zápis prostředků do souboru a pro zavření <xref:System.Resources.ResourceWriter> objektu.

> [!NOTE]
> Nepoužívejte soubory prostředků k ukládání hesel, informací citlivých na zabezpečení nebo soukromých dat.

 Následující příklad programově vytvoří soubor. Resources s názvem CarResources. Resources, který ukládá šest řetězců, ikonu a dva objekty definované aplikací ( `Automobile` dva objekty). `Automobile` Třída, která je definována a vytvořena v příkladu, je označena <xref:System.SerializableAttribute> atributem, který umožňuje trvalé formátování binární serializace.

 [!code-csharp[Conceptual.Resources.Resources#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.resources/cs/resources1.cs#1)]
 [!code-vb[Conceptual.Resources.Resources#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.resources/vb/resources1.vb#1)]

 Až vytvoříte soubor. Resources, můžete ho vložit do spustitelného souboru run-time nebo knihovny, a to tak, že `/resource` zahrnete přepínač kompilátoru jazyka nebo ho vložíte do satelitního sestavení pomocí [linkeru sestavení (Al. exe)](../tools/al-exe-assembly-linker.md).

<a name="VSResFiles"></a>
## <a name="resource-files-in-visual-studio"></a>Soubory prostředků v aplikaci Visual Studio

Když přidáte soubor prostředků do projektu aplikace [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) , Visual Studio vytvoří soubor. resx v adresáři projektu. Visual Studio poskytuje editory prostředků, které umožňují přidat řetězce, obrázky a binární objekty. Vzhledem k tomu, že editory jsou navržené výhradně pro zpracování statických dat, nelze je použít k ukládání programových objektů. data objektu je nutné zapsat do souboru. resx nebo do souboru. Resources programově. Další informace naleznete v tématu [práce se soubory. resx prostřednictvím kódu programu](working-with-resx-files-programmatically.md) a [prostředky v oddílu soubory. Resources](creating-resource-files-for-desktop-apps.md#ResourcesFiles) .

Pokud přidáváte lokalizované prostředky, přidělte jim stejný název kořenového souboru jako hlavní zdrojový soubor. V názvu souboru byste také měli určit svou jazykovou verzi. Například pokud přidáte soubor prostředků s názvem Resources. resx, můžete také vytvořit soubory prostředků s názvem Resources. en-US. resx a Resources.fr-FR. resx pro uložení lokalizovaných prostředků pro anglickou (USA) a francouzštinu (Francii) kultur. Měli byste také určit výchozí jazykovou verzi vaší aplikace. Jedná se o jazykovou verzi, jejíž prostředky se používají, pokud nelze najít žádné lokalizované prostředky pro konkrétní jazykovou verzi. Chcete-li určit výchozí jazykovou verzi, v Průzkumník řešení v aplikaci Visual Studio, klikněte pravým tlačítkem myši na název projektu, přejděte na aplikace, klikněte na položku **informace o sestavení**a v seznamu **neutrální jazyk** vyberte příslušný jazyk nebo jazykovou verzi.

V době kompilace Visual Studio nejprve převede soubory RESX v projektu na binární soubory prostředků (. Resources) a uloží je do podadresáře adresáře *obj* projektu. Visual Studio vloží všechny soubory prostředků, které v hlavním sestavení neobsahují lokalizované prostředky, které jsou generovány projektem. Pokud nějaké soubory prostředků obsahují lokalizované prostředky, Visual Studio je vloží do samostatných satelitních sestavení pro každou lokalizovanou jazykovou verzi. Pak uloží každé satelitní sestavení v adresáři, jehož název odpovídá lokalizované jazykové verzi. Například lokalizované prostředky v angličtině (USA) jsou uloženy v satelitním sestavení v podadresáři en-US.

## <a name="see-also"></a>Viz také

- <xref:System.Resources>
- [Prostředky v aplikacích klasické pracovní plochy](index.md)
- [Zabalení a nasazení prostředků](packaging-and-deploying-resources-in-desktop-apps.md)
