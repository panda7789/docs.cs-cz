---
title: Vytvoření souborů prostředků pro aplikace .NET
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
# <a name="create-resource-files-for-net-apps"></a>Vytvoření souborů prostředků pro aplikace .NET

Do souborů prostředků můžete zahrnout prostředky, například řetězce, obrázky nebo data objektů, aby byly snadno dostupné pro vaši aplikaci. Rozhraní .NET Framework nabízí pět způsobů vytváření souborů prostředků:

- Vytvořte textový soubor, který obsahuje prostředky řetězce. [Generátor souborů prostředků (Resgen.exe)](../tools/resgen-exe-resource-file-generator.md) můžete použít k převodu textového souboru do binárního souboru prostředků (.resources). Potom můžete vložit binární soubor prostředků do spustitelného souboru aplikace nebo knihovny aplikací pomocí kompilátoru jazyka, nebo jej můžete vložit do satelitního sestavení pomocí [propojovacího modulu sestavení (Al.exe).](../tools/al-exe-assembly-linker.md) Další informace naleznete v části [Zdroje v textových souborech.](creating-resource-files-for-desktop-apps.md#TextFiles)

- Vytvořte soubor prostředku XML (.resx), který obsahuje data řetězce, obrazu nebo objektu. [Generátor souborů prostředků (Resgen.exe)](../tools/resgen-exe-resource-file-generator.md) můžete použít k převodu souboru Resx na binární soubor prostředků (.resources). Potom můžete vložit binární soubor prostředků do spustitelného souboru aplikace nebo knihovny aplikací pomocí kompilátoru jazyka, nebo jej můžete vložit do satelitního sestavení pomocí [propojovacího modulu sestavení (Al.exe).](../tools/al-exe-assembly-linker.md) Další informace naleznete v části Zdroje v části [Soubory .resx.](creating-resource-files-for-desktop-apps.md#ResxFiles)

- Vytvořte soubor prostředku XML (.resx) programově <xref:System.Resources> pomocí typů v oboru názvů. Můžete vytvořit soubor RESX, vytvořit výčet jeho prostředků a načíst konkrétní prostředky podle názvu. Další informace naleznete v [tématu Programová práce se soubory RESX](working-with-resx-files-programmatically.md).

- Programově vytvořte soubor binárního prostředku (.resources). Potom můžete vložit soubor do spustitelného souboru aplikace nebo knihovny aplikací pomocí kompilátoru jazyka, nebo jej můžete vložit do satelitního sestavení pomocí [propojovacího modulu sestavení (Al.exe).](../tools/al-exe-assembly-linker.md) Další informace naleznete v části Zdroje v souboru [Soubory ..](creating-resource-files-for-desktop-apps.md#ResourcesFiles)

- Pomocí [sady Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) vytvořte soubor prostředků a zahrňte jej do projektu. Visual Studio poskytuje editor prostředků, který umožňuje přidávat, odstraňovat a upravovat prostředky. V době kompilace je soubor prostředků automaticky převeden na binární soubor .resources a vložen do sestavení aplikace nebo satelitního sestavení. Další informace naleznete v části [Resource Files v sadě Visual Studio.](creating-resource-files-for-desktop-apps.md#VSResFiles)

<a name="TextFiles"></a>
## <a name="resources-in-text-files"></a>Zdroje v textových souborech

Soubory textu (.txt nebo restext) můžete použít pouze k ukládání prostředků řetězce. Pro prostředky bez řetězce použijte soubory RESX nebo je vytvořte programově. Textové soubory, které obsahují prostředky řetězce mají následující formát:

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

 Formát souboru prostředků txt a restext souborů je totožný. Přípona souboru .restext slouží pouze k tomu, aby textové soubory okamžitě identifikovatelné jako textové soubory prostředků.

 Prostředky řetězce se zobrazí jako dvojice *název/hodnota,* kde *název* je řetězec, který identifikuje prostředek a *hodnota* je řetězec prostředku, <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType>který je vrácen při předání *názvu* metodě načítání prostředků, například . *název* a *hodnota* musí být odděleny rovnítkem (=). Například:

```text
FileMenuName=File
EditMenuName=Edit
ViewMenuName=View
HelpMenuName=Help
```

> [!CAUTION]
> Nepoužívejte soubory prostředků k ukládání hesel, citlivých informací o zabezpečení nebo soukromých dat.

 Prázdné řetězce (tj. prostředek, jehož hodnota je <xref:System.String.Empty?displayProperty=nameWithType>) jsou povoleny v textových souborech. Například:

```text
EmptyString=
```

 Počínaje rozhraním .NET Framework 4.5 a ve všech verzích rozhraní `#ifdef`.NET Core podporují textové soubory podmíněnou kompilaci se *symbolem*... `#endif` a `#if !` *symbol*... `#endif` konstrukce. Potom můžete použít `/define` přepínač s [generátorem souborů prostředků (Resgen.exe)](../tools/resgen-exe-resource-file-generator.md) k definování symbolů. Každý zdroj vyžaduje `#ifdef`svůj vlastní *symbol*... `#endif` nebo `#if !` *symbol*... `#endif` konstrukce. Pokud použijete `#ifdef` příkaz a *symbol* je definován, přidružený prostředek je zahrnut v souboru .resources; v opačném případě není zahrnuta. Pokud použijete `#if !` příkaz a *symbol* není definován, přidružený prostředek je zahrnut v souboru .resources; v opačném případě není zahrnuta.

 Komentáře jsou v textových souborech volitelné a předchází mu středník (;) nebo znakem libry (#) na začátku řádku. Řádky, které obsahují komentáře, lze umístit kdekoli v souboru. Komentáře nejsou zahrnuty do zkompilovaného souboru .resources, který je vytvořen pomocí [generátoru souborů prostředků (Resgen.exe).](../tools/resgen-exe-resource-file-generator.md)

 Všechny prázdné řádky v textových souborech jsou považovány za prázdné znaky a jsou ignorovány.

 Následující příklad definuje dva řetězcové prostředky s názvem `OKButton` a `CancelButton`.

```text
#Define resources for buttons in the user interface.
OKButton=OK
CancelButton=Cancel
```

 Pokud textový soubor obsahuje duplicitní výskyty *názvu*, [generátor souborů prostředků (Resgen.exe)](../tools/resgen-exe-resource-file-generator.md) zobrazí upozornění a ignoruje druhý název.

 *hodnota* nemůže obsahovat nové znaky řádku, ale můžete použít `\n` řídicí znaky jazyka `\t` C, například představují nový řádek a představují kartu. Znak zpětného lomítka můžete zahrnout také v\\\\případě, že je uvozen (například " "). Kromě toho je povolen prázdný řetězec.

 Ukládejte prostředky ve formátu textového souboru pomocí kódování UTF-8 nebo Kódování UTF-16 v pořadí malých endianů nebo velkých endianů. Generátor [souborů prostředků (Resgen.exe),](../tools/resgen-exe-resource-file-generator.md)který převádí soubor TXT na soubor .resources, však ve výchozím nastavení považuje soubory za UTF-8. Pokud chcete, aby program Resgen.exe rozpoznal soubor, který byl kódován pomocí UTF-16, musíte na začátek souboru zahrnout značku pořadí bajtů Unicode (U+FEFF).

 Chcete-li vložit soubor prostředků v textovém formátu do sestavení .NET, je nutné jej převést na binární soubor prostředků (.resources) pomocí [generátoru souborů prostředků (Resgen.exe).](../tools/resgen-exe-resource-file-generator.md) Soubor .resources pak můžete vložit do sestavení .NET pomocí kompilátoru jazyka nebo jej vložit do satelitního sestavení pomocí [propojovacího systému sestavení (Al.exe).](../tools/al-exe-assembly-linker.md)

 Následující příklad používá soubor prostředků v textovém formátu s názvem GreetingResources.txt pro jednoduchou konzolovou aplikaci "Hello World". Textový soubor definuje dva řetězce `prompt` `greeting`a , které vyzve uživatele k zadání jejich jména a zobrazení pozdravu.

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

 Následující příklad ukazuje zdrojový kód konzolové aplikace, která používá soubor .resources k zobrazení zpráv uživateli.

 [!code-csharp[Conceptual.Resources.TextFiles#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.textfiles/cs/greeting.cs#1)]
 [!code-vb[Conceptual.Resources.TextFiles#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.textfiles/vb/greeting.vb#1)]

 Pokud používáte jazyk Visual Basic a soubor zdrojového kódu se jmenuje Greeting.vb, vytvoří následující příkaz spustitelný soubor obsahující vložený soubor .resources:

```console
vbc greeting.vb -resource:GreetingResources.resources
```

 Pokud používáte c# a soubor zdrojového kódu je pojmenován Greeting.cs, následující příkaz vytvoří spustitelný soubor, který obsahuje vložený soubor .resources:

```console
csc greeting.cs -resource:GreetingResources.resources
```

<a name="ResxFiles"></a>
## <a name="resources-in-resx-files"></a>Zdroje v souborech Resx
 Na rozdíl od textových souborů, které mohou ukládat pouze prostředky řetězce, mohou soubory prostředků XML (.resx) ukládat řetězce, binární data, jako jsou obrázky, ikony a zvukové klipy, a programové objekty. Soubor RESX obsahuje standardní záhlaví, které popisuje formát položek prostředků a určuje informace o správě verzí pro jazyk XML, který se používá k analýzě dat. Data souboru prostředků se řídí hlavičkou XML. Každá datová položka se skládá z dvojice název/hodnota, která je obsažena ve značce. `data` Jeho `name` atribut definuje název prostředku a `value` vnořená značka obsahuje hodnotu prostředku. Pro data řetězce `value` značka obsahuje řetězec.

 Například následující `data` značka definuje řetězec s `prompt` názvem prostředku, jehož hodnota je "Zadejte své jméno:".

```xml
<data name="prompt" xml:space="preserve">
  <value>Enter your name:</value>
</data>
```

> [!WARNING]
> Nepoužívejte soubory prostředků k ukládání hesel, citlivých informací o zabezpečení nebo soukromých dat.

 Pro objekty prostředků obsahuje `type` **datová** značka atribut, který označuje datový typ prostředku. Pro objekty, které se `data` skládají `mimetype` z binárních `base64` dat, značka také obsahuje atribut, který označuje typ binárních dat.

> [!NOTE]
> Všechny soubory RESX používají formátovací modul binární serializace ke generování a analýzě binárních dat pro zadaný typ. V důsledku toho může být soubor RESX neplatný, pokud se binární formát serializace objektu změní nekompatibilním způsobem.

 Následující příklad ukazuje část souboru Resx, <xref:System.Int32> která obsahuje prostředek a bitmapový obraz.

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
> Vzhledem k tomu, že soubory RESX se musí skládat z dobře formátovaného formátu XML v předdefinovaném formátu, nedoporučujeme pracovat se soubory RESX ručně, zejména pokud soubory RESX obsahují jiné prostředky než řetězce. Místo toho [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) poskytuje transparentní rozhraní pro vytváření a manipulaci s soubory RESX. Další informace naleznete v části [Resource Files v sadě Visual Studio.](creating-resource-files-for-desktop-apps.md#VSResFiles) Soubory RESX můžete také vytvářet a manipulovat s nimi programově. Další informace naleznete v [tématu Programová práce se soubory RESX](working-with-resx-files-programmatically.md).

<a name="ResourcesFiles"></a>
## <a name="resources-in-resources-files"></a>Prostředky v souborech .resources

Třídu <xref:System.Resources.ResourceWriter?displayProperty=nameWithType> můžete použít k programovému vytvoření binárního souboru prostředků (.resources) přímo z kódu. Generátor souborů [prostředků (Resgen.exe)](../tools/resgen-exe-resource-file-generator.md) můžete také použít k vytvoření souboru .resources z textového souboru nebo souboru Resx. Soubor .resources může obsahovat binární data (bajtová pole) a data objektů kromě řetězcových dat. Programové vytvoření souboru .resources vyžaduje následující kroky:

1. Vytvořte <xref:System.Resources.ResourceWriter> objekt s jedinečným názvem souboru. To lze provést zadáním názvu souboru nebo datového proudu souboru do konstruktoru <xref:System.Resources.ResourceWriter> třídy.

2. Volání jednoho z přetížení <xref:System.Resources.ResourceWriter.AddResource%2A?displayProperty=nameWithType> metody pro každý pojmenovaný prostředek přidat do souboru. Prostředek může být řetězec, objekt nebo kolekce binárních dat (bajtové pole).

3. Volání <xref:System.Resources.ResourceWriter.Close%2A?displayProperty=nameWithType> metody zapsat prostředky do souboru <xref:System.Resources.ResourceWriter> a zavřete objekt.

> [!NOTE]
> Nepoužívejte soubory prostředků k ukládání hesel, citlivých informací o zabezpečení nebo soukromých dat.

 Následující příklad programově vytvoří soubor .resources s názvem CarResources.resources, který ukládá šest řetězců, `Automobile` ikonu a dva objekty definované aplikací (dva objekty). Třída, `Automobile` která je definována a vytvořena instance v příkladu, je <xref:System.SerializableAttribute> označenatributem, který umožňuje, aby byla trvalá formátovacím formátovacím formátovacím formátem binární serializace.

 [!code-csharp[Conceptual.Resources.Resources#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.resources/cs/resources1.cs#1)]
 [!code-vb[Conceptual.Resources.Resources#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.resources/vb/resources1.vb#1)]

 Po vytvoření souboru .resources jej můžete vložit do spustitelného souboru nebo knihovny `/resource` za běhu zahrnutím přepínače kompilátoru jazyka nebo jeho vložením do satelitního sestavení pomocí [propojovacího modulu sestavení (Al.exe).](../tools/al-exe-assembly-linker.md)

<a name="VSResFiles"></a>
## <a name="resource-files-in-visual-studio"></a>Soubory prostředků v sadě Visual Studio

Když přidáte soubor prostředků do projektu [sady Visual Studio,](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) Visual Studio vytvoří soubor Resx v adresáři projektu. Visual Studio poskytuje editory prostředků, které umožňují přidat řetězce, obrázky a binární objekty. Vzhledem k tomu, že editory jsou navrženy pouze pro zpracování statických dat, nelze je použít k ukládání programových objektů; Je nutné zapsat data objektu do souboru Resx nebo do souboru .resources programově. Další informace naleznete [v tématu Programová práce se soubory Resx](working-with-resx-files-programmatically.md) a v části [Zdroje v souborech .resources](creating-resource-files-for-desktop-apps.md#ResourcesFiles) Files.

Pokud přidáváte lokalizované prostředky, přiřaďte jim stejný kořenový název jako hlavní soubor prostředků. Měli byste také určit jejich jazykovou verzi v názvu souboru. Pokud například přidáte soubor prostředků s názvem Resources.resx, můžete také vytvořit soubory prostředků s názvem Resources.en-US.resx a Resources.fr-FR.resx, které budou obsahovat lokalizované prostředky pro jazykovou verzi Angličtina (Spojené státy) a Francouzština (Francie). Měli byste také určit výchozí jazykovou verzi aplikace. Toto je jazyková verze, jejíž prostředky se používají, pokud nelze nalézt žádné lokalizované prostředky pro určitou jazykovou verzi. Chcete-li určit výchozí jazykovou verzi, klikněte v Průzkumníkovi řešení v sadě Visual Studio pravým tlačítkem myši na název projektu, přejděte na položku Aplikace, klepněte na příkaz **Informace o sestavení**a vyberte příslušný jazyk nebo jazykovou verzi v seznamu Neutrální **jazyk.**

V době kompilace visual studio nejprve převede soubory .resx v projektu na binární zdroje (.zdroje) soubory a uloží je do podadresáře adresáře *obj* projektu. Visual Studio vloží všechny soubory prostředků, které neobsahují lokalizované prostředky v hlavním sestavení, které je generováno v projektu. Pokud některé soubory prostředků obsahují lokalizované prostředky, Visual Studio vloží je do samostatných satelitních sestavení pro každou lokalizovanou jazykovou verzi. Potom ukládá každé satelitní sestavení v adresáři, jehož název odpovídá lokalizované jazykové verzi. Například lokalizované prostředky angličtiny (Spojené státy) jsou uloženy v satelitním sestavení v podadresáři en-US.

## <a name="see-also"></a>Viz také

- <xref:System.Resources>
- [Prostředky v aplikacích klasické pracovní plochy](index.md)
- [Zabalení a nasazení prostředků](packaging-and-deploying-resources-in-desktop-apps.md)
