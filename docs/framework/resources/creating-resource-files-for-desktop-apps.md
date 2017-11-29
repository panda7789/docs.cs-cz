---
title: "Vytváření zdrojových souborů pro aplikace klasické pracovní plochy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- resource files, .resources files
- .resources files
- application resources, creating files
- resource files, creating
ms.assetid: 6c5ad891-66a0-4e7a-adcf-f41863ba6d8d
caps.latest.revision: "25"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 10f714f5793fff4d6081c9fc910159a02e34e53b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="creating-resource-files-for-desktop-apps"></a>Vytváření zdrojových souborů pro aplikace klasické pracovní plochy
Můžete zahrnout prostředky, například řetězce, Image nebo dat objektů, soubory prostředků, aby je bylo možné snadno do vaší aplikace. Rozhraní .NET Framework nabízí pět způsoby, jak vytvářet soubory prostředků:  
  
-   Vytvořte textový soubor, který obsahuje řetězec prostředky. Můžete použít [Generátor zdrojových souborů (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) převést textový soubor do souboru binárního prostředku (.resources). Poté můžete vložit soubor binárního prostředku v spustitelný soubor aplikace nebo do knihovny aplikace pomocí kompilátoru jazyka, nebo je můžete vložit satelitní sestavení pomocí [Linker sestavení (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md). Další informace najdete v tématu [prostředky v textovém souboru](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md#TextFiles) části.  
  
-   Vytvořte soubor XML prostředků (RESX), který obsahuje řetězec, image nebo data objektu. Můžete použít [Generátor zdrojových souborů (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) převést soubor .resx do souboru binárního prostředku (.resources). Poté můžete vložit soubor binárního prostředku v spustitelný soubor aplikace nebo do knihovny aplikace pomocí kompilátoru jazyka, nebo je můžete vložit satelitní sestavení pomocí [Linker sestavení (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md). Další informace najdete v tématu [prostředky v soubory RESX](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md#ResxFiles) části.  
  
-   Vytvořit prostředek (RESX) soubor XML programově pomocí typy v <xref:System.Resources> oboru názvů. Můžete vytvořit soubor .resx, výčet její prostředky a načíst konkrétní zdroje podle názvu. Další informace naleznete v tématu [práce s .resx programově soubory](../../../docs/framework/resources/working-with-resx-files-programmatically.md).  
  
-   Vytvořte soubor binárního prostředku (.resources) prostřednictvím kódu programu. Poté můžete vložit soubor v aplikaci spustitelný soubor nebo do knihovny aplikace pomocí kompilátoru jazyka, nebo je můžete vložit satelitní sestavení pomocí [Linker sestavení (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md). Další informace najdete v tématu [prostředky v soubory .resources](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md#ResourcesFiles) části.  
  
-   Pomocí sady Visual Studio k vytvoření souboru prostředků a její zahrnutí do projektu. Visual Studio poskytuje editor prostředků, která umožňuje přidat, odstranit a úpravám prostředků. Při kompilaci soubor prostředků je automaticky převeden do souboru .resources binární a vložených v sestavení aplikace nebo satelitní sestavení. Další informace najdete v tématu [soubory prostředků v sadě Visual Studio](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md#VSResFiles) části.  
  
<a name="TextFiles"></a>   
## <a name="resources-in-text-files"></a>Prostředky v textových souborů  
 Textové soubory (s příponou TXT nebo .restext) můžete použít k uložení řetězcové prostředky jenom; pro jiné než řetězec prostředky soubory RESX použít nebo vytvořit prostřednictvím kódu programu. Textové soubory, které obsahují řetězec prostředky mít následující formát:  
  
```  
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
  
 Formát souboru prostředků soubory TXT a .restext se shoduje. Přípona souboru .restext slouží jenom k bylo textové soubory okamžitě identifikovat jako soubory prostředků založený na textu.  
  
 Prostředky řetězců se zobrazí jako *název hodnota* páry, kde *název* je řetězec, který identifikuje prostředek, a *hodnota* je řetězec prostředku, který je vrácena, pokud předáte *název* na metodu načtení prostředků, jako <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType>. *název* a *hodnota* musí být odděleny symbolem rovná se (=). Příklad:  
  
```  
FileMenuName=File  
EditMenuName=Edit  
ViewMenuName=View  
HelpMenuName=Help  
```  
  
> [!CAUTION]
>  Nepoužívejte soubory prostředků pro uložení hesla, informace citlivé na zabezpečení nebo osobní data.  
  
 Prázdné řetězce (to znamená, jehož hodnota je prostředek <xref:System.String.Empty?displayProperty=nameWithType>) jsou povoleny v textových souborů. Příklad:  
  
```  
EmptyString=  
```  
  
 Od verze [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], textové soubory podporují Podmíněná kompilace s `#ifdef` *symbol*... `#endif` a `#if !` *symbol*... `#endif` vytvoří. Pak můžete použít `/define` přepínač s [Generátor zdrojových souborů (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) pro definování symbolů. Každý prostředek, vyžaduje vlastní `#ifdef` *symbol*... `#endif` nebo `#if !` *symbol*... `#endif` vytvořit. Pokud používáte `#ifdef` příkaz a *symbol* je definován, přidružených prostředků je součástí souboru .resources; jinak, není součástí. Pokud používáte `#if !` příkaz a *symbol* není definována, přidružených prostředků je součástí souboru .resources; jinak, není součástí.  
  
 Komentáře jsou volitelné v textových souborů a jsou uvedeny středníkem (;) nebo znak křížku (#) na začátku řádku. Řádky, které obsahují komentáře můžete umístit kdekoli v souboru. Komentáře nejsou zahrnuty do souboru .resources kompilované, který se vytvoří pomocí [Generátor zdrojových souborů (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md).  
  
 Všechny prázdné řádky v textové soubory se považují za mezer a budou ignorovány.  
  
 V následujícím příkladu definuje dva řetězce prostředků s názvem `OKButton` a `CancelButton`.  
  
```  
#Define resources for buttons in the user interface.  
OKButton=OK  
CancelButton=Cancel  
```  
  
 Pokud k textovému souboru obsahuje duplicitní výskyty *název*, [Generátor zdrojových souborů (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) zobrazí varování a ignoruje druhý název.  
  
 *Hodnota* nesmí obsahovat znaky nového řádku, ale můžete použít jako řídící znaky ve stylu jazyka C `\n` představují nový řádek a `\t` představující tabulátor. Pokud není uvozené řídicím lze také vložit znak zpětného lomítka (například "\\\\"). Kromě toho je povolená prázdný řetězec.  
  
 Prostředky byste měli uložit ve formátu textového souboru pomocí kódování UTF-8 nebo v obou pořadí bajtů little endian nebo big endian kódování UTF-16. Ale [Generátor zdrojových souborů (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md), která převede soubor .txt do souboru .resources, zpracovává soubory jako ve formátu UTF-8 ve výchozím nastavení. Pokud chcete, aby Resgen.exe rozpoznal soubor, který byl zakódován pomocí kódování UTF-16, musíte zahrnout značka pořadí bajtů (U + FEFF) Unicode na začátku souboru.  
  
 Pro vložení zdrojového souboru ve formátu textu do sestavení rozhraní .NET Framework, je nutné převést soubor do souboru binárního prostředku (.resources) pomocí [Generátor zdrojových souborů (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md). Potom můžete vložit souboru .resources v sestavení rozhraní .NET Framework pomocí jazyka kompilátoru nebo vložit satelitní sestavení pomocí [Linker sestavení (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md).  
  
 Následující příklad používá soubor prostředků ve formátu textu s názvem GreetingResources.txt pro jednoduché konzolové aplikace "Hello World". Textový soubor definuje dva řetězce `prompt` a `greeting`, který vyzvat uživatele k zadejte své jméno a zobrazí pozdrav.  
  
```  
# GreetingResources.txt   
# A resource file in text format for a "Hello World" application.  
#  
# Initial prompt to the user.  
prompt=Enter your name:   
# Format string to display the result.  
greeting=Hello, {0}!  
```  
  
 Textový soubor je převeden do souboru .resources pomocí následujícího příkazu:  
  
 **Nástroj Resgen GreetingResources.txt**  
  
 Následující příklad ukazuje zdrojový kód pro konzolovou aplikaci, která používá souboru .resources pro zobrazení zprávy pro uživatele.  
  
 [!code-csharp[Conceptual.Resources.TextFiles#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.textfiles/cs/greeting.cs#1)]
 [!code-vb[Conceptual.Resources.TextFiles#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.textfiles/vb/greeting.vb#1)]  
  
 Pokud používáte Visual Basic a souboru se zdrojovým kódem je pojmenován Greeting.vb, následující příkaz vytvoří spustitelný soubor, který obsahuje vložený soubor Resources:  
  
 **Vbc – greeting.vb /resource:GreetingResources.resources**  
  
 Pokud používáte C# a souboru se zdrojovým kódem je pojmenován Greeting.cs, následující příkaz vytvoří spustitelný soubor, který obsahuje vložený soubor Resources:  
  
 **CSC greeting.cs /resource:GreetingResources.resources**  
  
<a name="ResxFiles"></a>   
## <a name="resources-in-resx-files"></a>Prostředky v soubory RESX  
 Na rozdíl od textových souborů, které lze uložit pouze řetězcové prostředky, můžete ukládat soubory XML prostředků (RESX) řetězce, binární data, jako jsou bitové kopie, ikony a zvukových klipů a programové objekty. Soubor .resx obsahuje standardní hlavičku, která popisuje formát položek prostředků a určuje informace pro formát XML, který slouží k analýze dat. Data souboru prostředků dodržovat záhlaví XML. Každá položka dat se skládá z dvojice název hodnota, která je součástí `data` značky. Jeho `name` atribut definuje název prostředku a vnořeného `value` značka obsahuje hodnotu zdroje. Řetězec dat `value` značka obsahuje řetězec.  
  
 Například následující `data` značky definuje řetězec prostředek s názvem `prompt` jehož hodnota je "Zadejte své jméno:".  
  
```xml  
<data name="prompt" xml:space="preserve">  
  <value>Enter your name:</value>  
</data>  
```  
  
> [!WARNING]
>  Nepoužívejte soubory prostředků pro uložení hesla, informace citlivé na zabezpečení nebo osobní data.  
  
 Objektů prostředků **data** zahrnuje značky `type` atribut, který určuje datový typ prostředku. Pro objekty, které se skládají z binárních dat `data` značky také zahrnuje `mimetype` atribut, který určuje, `base64` typ binární data.  
  
> [!NOTE]
>  Všechny soubory RESX použít k vytvoření a analyzovat binární data pro zadaný typ formátování binární serializace. V důsledku toho se může stát souboru RESX neplatný, pokud se změní formát binární serializace objektu nekompatibilním způsobem.  
  
 Následující příklad ukazuje část souboru RESX, která zahrnuje <xref:System.Int32> prostředků a rastrový obrázek.  
  
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
>  Protože soubory RESX musí obsahovat ve správném formátu XML v předdefinovaném formátu, nedoporučujeme práce se soubory .resx ručně, zejména v případě, že obsahují prostředky než řetězce. Místo toho Visual Studio poskytuje transparentní rozhraní pro vytváření a manipulace se soubory .resx; Další informace najdete v tématu [soubory prostředků v sadě Visual Studio](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md#VSResFiles) části. Můžete také vytvořit a pracovat se soubory .resx programově. Další informace najdete v tématu [práce s .resx programově soubory](../../../docs/framework/resources/working-with-resx-files-programmatically.md).  
  
<a name="ResourcesFiles"></a>   
## <a name="resources-in-resources-files"></a>Prostředky v soubory .resources  
 Můžete použít <xref:System.Resources.ResourceWriter?displayProperty=nameWithType> třída prostřednictvím kódu programu vytvořte soubor binárního prostředku (.resources) přímo z kódu. Můžete také použít [Generátor zdrojových souborů (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) k vytvoření souboru .resources z textového souboru nebo souboru RESX. Souboru .resources může obsahovat binární data (pole bajtů) a data objektu kromě dat řetězce. Programové vytvoření souboru .resources vyžaduje následující kroky:  
  
1.  Vytvoření <xref:System.Resources.ResourceWriter> objekt s jedinečným názvem souboru. To provedete tak, že zadáte název souboru nebo datový proud souboru k <xref:System.Resources.ResourceWriter> konstruktoru třídy.  
  
2.  Volání jednoho z přetížení <xref:System.Resources.ResourceWriter.AddResource%2A?displayProperty=nameWithType> metoda pro každou s názvem prostředku k přidání do souboru. Prostředek může být řetězec, objekt nebo kolekci binárních dat (pole bajtů).  
  
3.  Volání <xref:System.Resources.ResourceWriter.Close%2A?displayProperty=nameWithType> metoda zapisovat do souboru prostředků a zavřete <xref:System.Resources.ResourceWriter> objektu.  
  
> [!NOTE]
>  Nepoužívejte soubory prostředků pro uložení hesla, informace citlivé na zabezpečení nebo osobní data.  
  
 Následující příklad vytvoří prostřednictvím kódu programu .resources soubor s názvem CarResources.resources, která ukládá šest řetězců, ikonu a dva objekty definované aplikací (dva `Automobile` objektů). Všimněte si, že `Automobile` třída, která je definována a vytvoření instance v příkladu, je označené <xref:System.SerializableAttribute> atribut, který umožňuje nastavit jako trvalý, formátováním binární serializace.  
  
 [!code-csharp[Conceptual.Resources.Resources#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.resources/cs/resources1.cs#1)]
 [!code-vb[Conceptual.Resources.Resources#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.resources/vb/resources1.vb#1)]  
  
 Po vytvoření souboru .resources jej můžete vložit spuštění spustitelného souboru nebo knihovny zahrnutím kompilátor jazyka `/resource` přepínač, nebo vložit satelitní sestavení pomocí [Linker sestavení (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md).  
  
<a name="VSResFiles"></a>   
## <a name="resource-files-in-visual-studio"></a>Soubory prostředků v sadě Visual Studio  
 Když přidáte zdrojového souboru do projektu sady Visual Studio, Visual Studio vytvoří soubor .resx v adresáři projektu. Visual Studio poskytuje editory prostředků, které vám umožní přidat řetězce, Image a binární objekty. Protože editory jsou určeny ke zpracování pouze statických dat, nelze je použít k uložení programové objekty; musíte zápis dat objektů do buď soubor .resx nebo do souboru RESOURCES prostřednictvím kódu programu. Najdete v článku [práce s .resx programově soubory](../../../docs/framework/resources/working-with-resx-files-programmatically.md) tématu a [prostředky v soubory .resources](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md#ResourcesFiles) části Další informace.  
  
 Pokud přidáváte lokalizované prostředky, měli byste jim přidělit stejný název souboru kořenové jako soubor hlavní prostředků a můžete také určit jejich jazykové verzi v názvu souboru. Například pokud přidáte soubor prostředků s názvem Resources.resx, můžete také vytvořit soubory prostředků s názvem názvy Resources.en-US.resx a Resources.fr-FR.resx s lokalizovanými prostředky pro angličtinu (Spojené státy) a Francouzština (Francie) jazykové verze, v uvedeném pořadí. Můžete také určit výchozí jazykovou verzi vaší aplikace. Toto je jazyková verze, jejichž zdroje se použijí, pokud lze nalézt žádné lokalizované prostředky pro konkrétní jazykovou verzi. Chcete-li zadat výchozí jazykovou verzi v Průzkumníku řešení v sadě Visual Studio, klikněte pravým tlačítkem na název projektu, přejděte na aplikace, klikněte na **informací o sestavení**a vyberte příslušné jazyků a kultur v **neutrální jazyk** seznamu.  
  
 Při kompilaci Visual Studio nejprve převede soubory RESX v projektu na soubory binárního prostředku (.resources) a ukládá je v podadresáři obj adresáře projektu. Visual Studio vloží všechny soubory prostředků, které neobsahují lokalizované prostředky v hlavní sestavení, který je generovaný projektu. Pokud některý ze souborů prostředků obsahuje lokalizované prostředky, Visual Studio je vloží do samostatné satelitní sestavení pro jednotlivé lokalizované jazykové verze. Pak uloží každé satelitní sestavení v adresáři, jejíž název odpovídá thelocalized jazykovou verzi. Například lokalizované prostředky Czech (Czech Republic) jsou uloženy v satelitní sestavení v podadresáři en US.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Resources>  
 [Prostředky v aplikacích klasické pracovní plochy](../../../docs/framework/resources/index.md)  
 [Zabalení a nasazení prostředků](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)
