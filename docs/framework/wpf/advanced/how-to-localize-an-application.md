---
title: Lokalizace aplikace
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- localization [WPF], applications
- LocBaml tool [WPF]
- applications [WPF], localizing
ms.assetid: 5001227e-9326-48a4-9dcd-ba1b89ee6653
ms.openlocfilehash: dc7d8f4f56b26fffbd883e1e1d6e420026e1f94f
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209679"
---
# <a name="how-to-localize-an-application"></a>Postupy: lokalizace aplikace

V tomto kurzu se dozvíte, jak vytvořit lokalizovanou aplikaci pomocí nástroje LocBaml.  
  
> [!NOTE]
> Nástroj LocBaml není aplikací připravenou pro produkční prostředí. Je prezentován jako ukázka, která používá některá z rozhraní API lokalizace a ukazuje, jak můžete napsat nástroj pro lokalizaci.  
  
## <a name="overview"></a>Přehled

Tento článek poskytuje podrobný přístup k lokalizaci aplikace. Nejprve připravujete aplikaci tak, aby bylo možné extrahovat text, který bude přeložen. Po překladu textu se přeložený text sloučí do nové kopie původní aplikace.
  
## <a name="create-a-sample-application"></a>Vytvoření ukázkové aplikace

V tomto kroku připravíte aplikaci k lokalizaci. V ukázkách Windows Presentation Foundation (WPF) je dodána ukázka HelloApp, která bude použita pro příklady kódu v této diskuzi. Chcete-li použít tuto ukázku, Stáhněte soubory jazyk Extensible Application Markup Language (XAML) (XAML) z [ukázky nástroje LocBaml](https://github.com/microsoft/WPF-Samples/tree/master/Tools/LocBaml).  
  
1. Vyvine aplikaci do bodu, kde chcete spustit lokalizaci.  
  
2. Určete vývojový jazyk v souboru projektu tak, aby nástroj MSBuild vygeneroval hlavní sestavení a satelitní sestavení (soubor s příponou. Resources. dll), aby obsahoval prostředky neutrálního jazyka. Soubor projektu v ukázce HelloApp je HelloApp. csproj. V tomto souboru najdete jazyk vývoje identifikovaný následujícím způsobem:  
  
   `<UICulture>en-US</UICulture>`  
  
3. Přidejte identifikátory UID do souborů XAML. Identifikátory UID se používají ke sledování změn souborů a identifikaci položek, které je nutné přeložit. Chcete-li do souborů přidat UID, spusťte `updateuid` soubor projektu:  

   `msbuild -t:updateuid helloapp.csproj`

   Chcete-li ověřit, zda nemáte žádné nebo duplicitní identifikátory UID, spusťte příkaz `checkuid` :  

   `msbuild -t:checkuid helloapp.csproj`

   Po spuštění `updateuid` by vaše soubory měly obsahovat identifikátory UID. Například v souboru *Pane1. XAML* HelloApp byste měli najít následující:  

   ```xaml
   <StackPanel x:Uid="StackPanel_1">
     <TextBlock x:Uid="TextBlock_1">Hello World</TextBlock>
     <TextBlock x:Uid="TextBlock_2">Goodbye World</TextBlock>
   </StackPanel>
   ```

## <a name="create-the-neutral-language-resources-satellite-assembly"></a>Vytvoření satelitního sestavení prostředků neutrálního jazyka

Jakmile je aplikace nakonfigurována tak, aby vygenerovala satelitní sestavení prostředků neutrálního jazyka, sestavíte aplikaci. Tím se vygeneruje hlavní sestavení aplikace, stejně jako prostředky v neutrálním jazyce, které jsou požadovány LocBaml pro lokalizaci.

Sestavení aplikace:  
  
1. Zkompiluje HelloApp a vytvoří dynamickou knihovnu (DLL):  
  
   `msbuild helloapp.csproj`
  
2. Nově vytvořené sestavení hlavní aplikace, HelloApp. exe, je vytvořeno v následující složce: *C:\HelloApp\Bin\Debug*
  
3. Nově vytvořené prostředky neutrálního cloudového sestavení HelloApp. Resources. dll se vytvoří v následující složce: *C:\HelloApp\Bin\Debug\en-US*
  
## <a name="build-the-locbaml-tool"></a>Sestavení nástroje LocBaml  
  
1. Všechny soubory, které jsou nezbytné pro sestavení LocBaml, jsou umístěny v ukázkách WPF. Stažení souborů C# z [ukázky nástroje LocBaml](https://github.com/microsoft/WPF-Samples/tree/master/Tools/LocBaml)  
  
2. Z příkazového řádku spusťte soubor projektu (LocBaml. csproj) pro sestavení nástroje:  

   `msbuild locbaml.csproj`
  
3. Pokud chcete najít nově vytvořený spustitelný soubor (LocBaml. exe), otevřete adresář *bin\Release* . Příklad: *C:\LocBaml\Bin\Release\locbaml.exe*
  
4. Možnosti, které můžete zadat při spuštění LocBaml, jsou následující.

   | Možnost | Popis|
   | - | - |
   | `parse` nebo `-p` | Analyzuje soubory BAML, prostředků nebo DLL pro vygenerování souboru. csv nebo. txt. |
   | `generate` nebo `-g` | Generuje lokalizovaný binární soubor pomocí přeloženého souboru. |
   | `out`nebo `-o` {*adresář*] | Název výstupního souboru. |
   | `culture`nebo `-cul` {*culture*] | Národní prostředí výstupních sestavení. |
   | `translation`nebo `-trans` {*Translation. csv*] | Přeložený nebo lokalizovaný soubor. |
   | `asmpath`nebo `-asmpath` {*adresář*] | Pokud váš kód jazyka XAML obsahuje vlastní ovládací prvky, je nutné dodat `asmpath` sestavení vlastního ovládacího prvku. |
   | `nologo` | Nezobrazí žádné logo ani informace o autorských právech. |
   | `verbose` | Zobrazí podrobné informace o režimu. |
  
   > [!NOTE]
   > Pokud při spuštění nástroje potřebujete seznam možností, zadejte `LocBaml.exe` a stiskněte klávesu **ENTER**.
  
## <a name="use-locbaml-to-parse-a-file"></a>Použití LocBaml k analýze souboru

Nyní, když jste vytvořili nástroj LocBaml, jste připraveni ho použít k analýze souboru HelloApp. Resources. dll pro extrakci textového obsahu, který bude lokalizován.  
  
1. Zkopírujte LocBaml. exe do složky bin\Debug vaší aplikace, kde bylo vytvořeno hlavní sestavení aplikace.  
  
2. Chcete-li analyzovat soubor satelitního sestavení a uložit výstup do souboru. csv, použijte následující příkaz:  
  
   `LocBaml.exe /parse HelloApp.resources.dll /out:Hello.csv`
  
   > [!NOTE]
   > Pokud vstupní soubor HelloApp. Resources. dll není ve stejném adresáři jako LocBaml. exe, přesuňte jeden ze souborů tak, aby oba soubory byly ve stejném adresáři.  
  
3. Když spustíte LocBaml k analýze souborů, výstup se skládá ze sedmi polí oddělených čárkami (soubory. csv) nebo karet (soubory. txt). Následující příklad ukazuje analyzovaný soubor. CSV pro HelloApp. Resources. dll:

   | |
   |-|
   |HelloApp. g. en-US. Resources: Window1. BAML, Stack1: System. Windows. Controls. StackPanel. $Content, ignore, FALSE, FALSE, #Text1; #Text2;|
   |HelloApp. g. en-US. Resources: Window1. BAML, Text1: System. Windows. Controls. TextBlock. $Content, None, TRUE, TRUE, Hello World|
   |HelloApp. g. en-US. Resources: Window1. BAML, Text2: System. Windows. Controls. TextBlock. $Content, None, true, true, World|

   Sedm polí:  
  
   - **Název BAML** Název prostředku BAML s ohledem na satelitní sestavení zdrojového jazyka.  
  
   - **Klíč prostředku**. Lokalizovaný identifikátor prostředku.  
  
   - **Kategorie**. Typ hodnoty. Viz [lokalizace atributů a komentářů](localization-attributes-and-comments.md).  
  
   - **Čitelnost**. Určuje, zda je možné hodnotu číst pomocí lokalizátora. Viz [lokalizace atributů a komentářů](localization-attributes-and-comments.md).  
  
   - **Upravitelnost**. Určuje, zda lze hodnotu upravit pomocí lokalizátora. Viz [lokalizace atributů a komentářů](localization-attributes-and-comments.md).  
  
   - **Komentáře**. Další popis hodnoty, která vám pomůže určit, jak je hodnota lokalizována. Viz [lokalizace atributů a komentářů](localization-attributes-and-comments.md).  
  
   - **Hodnota**. Textová hodnota, která se má přeložit na požadovanou jazykovou verzi.  
  
   Následující tabulka ukazuje, jak se tato pole mapují na hodnoty oddělené v souboru. CSV:  
  
   |Název BAML|Klíč prostředku|Kategorie|Čitelnost|Upravitelnost|Komentáře|Hodnota|  
   |---------------|------------------|--------------|-----------------|-------------------|--------------|-----------|
   |HelloApp. g. en-US. Resources: Window1. BAML|Stack1: System. Windows. Controls. StackPanel. $Content|Ignorovat|FALSE|FALSE||#Text1; #Text2|
   |HelloApp. g. en-US. Resources: Window1. BAML|Text1: System. Windows. Controls. TextBlock. $Content|Žádné|TRUE|TRUE||Hello World|
   |HelloApp. g. en-US. Resources: Window1. BAML|Text2: System. Windows. Controls. TextBlock. $Content|Žádné|TRUE|TRUE||Vylučte ze světa|
  
   Všimněte si, že všechny hodnoty pole **Komentáře** neobsahují žádné hodnoty; Pokud pole nemá hodnotu, je prázdné. Všimněte si také, že položka v prvním řádku není čitelná ani upravitelná a má "Ignore" jako hodnotu **kategorie** , všechny, které označují, že hodnotu nelze lokalizovat.  
  
4. Chcete-li usnadnit zjišťování lokalizovatelných položek v analyzovaných souborech, zejména ve velkých souborech, můžete položky řadit nebo filtrovat podle **kategorie**, **čitelnosti**a **volby.** Můžete například vyfiltrovat nečitelný a neupravitelné hodnoty.  
  
## <a name="translate-the-localizable-content"></a>Přeložit Lokalizovatelný obsah

Použijte libovolný nástroj, který máte k dispozici pro překlad extrahovaný obsah. Dobrým způsobem, jak to provést, je zapsání prostředků do souboru. csv a jejich zobrazení v aplikaci Microsoft Excel a provádění změn v překladu na poslední sloupec (hodnota).  
  
## <a name="use-locbaml-to-generate-a-new-resourcesdll-file"></a>Použití LocBaml k vygenerování nového souboru. Resources. dll

Obsah, který byl identifikován analýzou HelloApp. Resources. dll s LocBaml, byl přeložen a musí být sloučen zpět do původní aplikace. Pomocí `generate` Možnosti nebo `-g` Vygenerujte nový soubor. Resources. dll.  
  
1. Pomocí následující syntaxe Vygenerujte nový soubor HelloApp. Resources. dll. Označte jazykovou verzi jako en-US (/CUL: en-US).  
  
   `LocBaml.exe /generate HelloApp.resources.dll /trans:Hello.csv /out:c:\ /cul:en-US`  

   > [!NOTE]
   > Pokud vstupní soubor Hello. csv není ve stejném adresáři jako spustitelný soubor LocBaml. exe, přesuňte jeden ze souborů tak, aby oba soubory byly ve stejném adresáři.  
  
2. Nahraďte starý soubor *HelloApp. Resources. dll* v adresáři *C:\HelloApp\Bin\Debug\en-US\HelloApp.Resources.dll* nově vytvořeným souborem *HelloApp. Resources. dll* .  
  
3. V aplikaci by se teď měly přeložit "Hello World" a "rozvažovat World".  
  
4. Chcete-li přeložit na jinou jazykovou verzi, použijte jazykovou verzi jazyka, na který překládáte. Následující příklad ukazuje, jak převést na francouzština – kanadská:  
  
   `LocBaml.exe /generate HelloApp.resources.dll /trans:Hellofr-CA.csv /out:c:\ /cul:fr-CA`  
  
5. Ve stejném sestavení jako hlavní sestavení aplikace vytvořte novou složku specifickou pro jazykovou verzi, která bude zaustájena nové satelitní sestavení. V případě francouzštiny (kanadská) by tato složka byla fr-CA.  
  
6. Zkopírujte vygenerované satelitní sestavení do nové složky.  
  
7. Chcete-li otestovat nové satelitní sestavení, je nutné změnit jazykovou verzi, ve které bude aplikace spuštěna. Toto lze provést jedním ze dvou způsobů:  
  
   - Změnit místní nastavení operačního systému.
  
   - Do App.xaml.cs přidejte do aplikace následující kód:  
  
     [!code-xaml[LocBamlChangeCultureSnippets#LocBamlChangeCultureMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/CSharp/App.xaml#locbamlchangeculturemarkup)]
     [!code-csharp[LocBamlChangeCultureSnippets#LocBamlChangeCultureCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/CSharp/App.xaml.cs#locbamlchangeculturecodebehind)]
     [!code-vb[LocBamlChangeCultureSnippets#LocBamlChangeCultureCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/VisualBasic/Application.xaml.vb#locbamlchangeculturecodebehind)]  
  
## <a name="tips-for-using-locbaml"></a>Tipy pro použití LocBaml  
  
- Všechna závislá sestavení, která definují vlastní ovládací prvky, musí být zkopírována do místního adresáře LocBaml nebo nainstalována do mezipaměti GAC. To je nezbytné, protože rozhraní API pro lokalizaci musí mít přístup k závislým sestavením při čtení binárního XAML (BAML).  
  
- Pokud je hlavní sestavení podepsáno, vygenerované DLL prostředku musí být také podepsáno, aby bylo možné ho načíst.  
  
- Verze lokalizované knihovny DLL prostředku musí být synchronizována s hlavním sestavením.
  
## <a name="see-also"></a>Viz také

- [Globalizace pro WPF](globalization-for-wpf.md)
- [Přehled automatického rozložení](use-automatic-layout-overview.md)
