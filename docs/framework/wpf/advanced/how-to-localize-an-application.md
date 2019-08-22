---
title: 'Postupy: Lokalizace aplikace'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- localization [WPF], applications
- LocBaml tool [WPF]
- applications [WPF], localizing
ms.assetid: 5001227e-9326-48a4-9dcd-ba1b89ee6653
ms.openlocfilehash: 4d7271e792c96dd896d73a52a31ad136acc19e26
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666790"
---
# <a name="how-to-localize-an-application"></a>Postupy: Lokalizace aplikace
V tomto kurzu se dozvíte, jak vytvořit lokalizovanou aplikaci pomocí nástroje LocBaml.  
  
> [!NOTE]
>  Nástroj LocBaml není aplikací připravenou pro produkční prostředí. Je prezentován jako ukázka, která používá některá z rozhraní API lokalizace a ukazuje, jak můžete napsat nástroj pro lokalizaci.  
  
<a name="Introduction"></a>   
## <a name="overview"></a>Přehled  
 Tato diskuze vám poskytne podrobný přístup k lokalizaci aplikace. Nejprve připravujete aplikaci tak, aby bylo možné extrahovat text, který bude přeložen. Po překladu textu se přeložený text sloučí do nové kopie původní aplikace.  
  
<a name="Requirements"></a>   
## <a name="requirements"></a>Požadavky  
 V průběhu této diskuze použijete [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)], což je kompilátor spouštěný z příkazového řádku.  
  
 Také budete vyzváni k použití souboru projektu. Pokyny k používání [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] a projektových souborů najdete v tématu [sestavení a nasazení](../app-development/building-and-deploying-wpf-applications.md).  
  
 Všechny příklady v této diskuzi používají jako jazykovou verzi en-US (Čeština-US). To vám umožní pracovat s jednotlivými kroky v příkladech bez nutnosti instalovat jiný jazyk.  
  
<a name="create_sample_app"></a>   
## <a name="create-a-sample-application"></a>Vytvoření ukázkové aplikace  
 V tomto kroku připravíte aplikaci k lokalizaci. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] V ukázkách je dodána ukázka HelloApp, která bude použita pro příklady kódu v této diskuzi. Chcete-li použít tuto ukázku, stáhněte [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] soubory z [ukázky nástroje LocBaml](https://github.com/microsoft/WPF-Samples/tree/master/Tools/LocBaml).  
  
1. Vyvine aplikaci do bodu, kde chcete spustit lokalizaci.  
  
2. Určete vývojový jazyk v souboru projektu tak, [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] aby vygeneroval hlavní sestavení a satelitní sestavení (soubor s příponou. Resources. dll), který obsahuje prostředky neutrálního jazyka. Soubor projektu v ukázce HelloApp je HelloApp. csproj. V tomto souboru najdete jazyk vývoje identifikovaný následujícím způsobem:  
  
     `<UICulture>en-US</UICulture>`  
  
3. Přidejte do [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] souborů UID. Identifikátory UID se používají ke sledování změn souborů a identifikaci položek, které je nutné přeložit. Chcete-li do souborů přidat identifikátor UID, spusťte v souboru projektu **updateuid** :  
  
     **MSBuild-t:updateuid helloapp. csproj**  
  
     Pokud chcete ověřit, že nemáte žádné nebo duplicitní identifikátory UID, spusťte **checkuid**:  
  
     **MSBuild-t:checkuid helloapp. csproj**  
  
     Po spuštění **updateuid**by vaše soubory měly obsahovat identifikátory UID. Například v souboru Pane1. XAML HelloApp byste měli najít následující:  
  
     `<StackPanel x:Uid="StackPanel_1">`  
  
     `<TextBlock x:Uid="TextBlock_1">Hello World</TextBlock>`  
  
     `<TextBlock x:Uid="TextBlock_2">Goodbye World</TextBlock>`  
  
     `</StackPanel>`  
  
<a name="create_dll"></a>   
## <a name="create-the-neutral-language-resources-satellite-assembly"></a>Vytvoření satelitního sestavení pro prostředky v neutrálním jazyce  
 Po nakonfigurování aplikace pro generování satelitního sestavení prostředků v neutrálním jazyce sestavíte aplikaci. Tím se vygeneruje hlavní sestavení aplikace, stejně jako satelitní sestavení pro prostředky neutrálních jazyků, které je vyžadováno LocBaml pro lokalizaci. Sestavení aplikace:  
  
1. Zkompiluje HelloApp a vytvoří dynamickou knihovnu (DLL):  
  
     **MSBuild helloapp. csproj**  
  
2. Nově vytvořené sestavení hlavní aplikace, HelloApp. exe, je vytvořeno v následující složce:  
  
     `C:\HelloApp\Bin\Debug\`  
  
3. Nově vytvořené satelitní sestavení v neutrálních jazycích (HelloApp. Resources. dll) se vytvoří v následující složce:  
  
     `C:\HelloApp\Bin\Debug\en-US\`  
  
<a name="build_locbaml"></a>   
## <a name="build-the-locbaml-tool"></a>Sestavení nástroje LocBaml  
  
1. Všechny soubory potřebné k sestavení LocBaml jsou umístěné v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ukázkách. Stáhněte si C# soubory z [ukázky nástroje LocBaml](https://go.microsoft.com/fwlink/?LinkID=160016).  
  
2. Z příkazového řádku spusťte soubor projektu (LocBaml. csproj) pro sestavení nástroje:  
  
     **MSBuild LocBaml. csproj**  
  
3. Pokud chcete najít nově vytvořený spustitelný soubor (LocBaml. exe), otevřete adresář Bin\Release. Příklad: C: \LocBaml\Bin\Release\locbaml.exe.  
  
4. Možnosti, které můžete zadat při spuštění LocBaml, jsou následující:  
  
    - **analyzovat** nebo **-p:** Analyzuje soubory BAML, prostředků nebo DLL pro vygenerování souboru. csv nebo. txt.  
  
    - **Generovat** nebo **-g:** Generuje lokalizovaný binární soubor pomocí přeloženého souboru.  
  
    - **výstupní** nebo **-o** {*adresář adresáře*] **:** Název výstupního souboru.  
  
    - **jazyková verze** nebo **-CUL** {*culture*] **:** Národní prostředí výstupních sestavení.  
  
    - **Překlad** nebo **-trans** {*Translation. csv*] **:** Přeložený nebo lokalizovaný soubor.  
  
    - **asmPath** nebo **-asmPath:** {*adresář*] **:** Pokud váš [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kód obsahuje vlastní ovládací prvky, je nutné dodat **asmPath** sestavení vlastního ovládacího prvku.  
  
    - **nologo** Nezobrazí žádné logo ani informace o autorských právech.  
  
    - **Podrobné** Zobrazí podrobné informace o režimu.  
  
    > [!NOTE]
    >  Pokud při spuštění nástroje potřebujete seznam možností, zadejte **LocBaml. exe** a stiskněte klávesu ENTER.  
  
<a name="parse_dll"></a>   
## <a name="use-locbaml-to-parse-a-file"></a>Použití LocBaml k analýze souboru  
 Nyní, když jste vytvořili nástroj LocBaml, jste připraveni ho použít k analýze souboru HelloApp. Resources. dll pro extrakci textového obsahu, který bude lokalizován.  
  
1. Zkopírujte LocBaml. exe do složky bin\Debug vaší aplikace, kde bylo vytvořeno hlavní sestavení aplikace.  
  
2. Chcete-li analyzovat soubor satelitního sestavení a uložit výstup do souboru. csv, použijte následující příkaz:  
  
     **LocBaml. exe/Parse HelloApp. Resources. dll/out: Hello. csv**  
  
    > [!NOTE]
    >  Pokud vstupní soubor HelloApp. Resources. dll není ve stejném adresáři jako LocBaml. exe, přesuňte jeden ze souborů tak, aby oba soubory byly ve stejném adresáři.  
  
3. Když spustíte LocBaml k analýze souborů, výstup se skládá ze sedmi polí oddělených čárkami (soubory. csv) nebo karet (soubory. txt). Následující příklad ukazuje analyzovaný soubor. CSV pro HelloApp. Resources. dll:

   | |
   |-|
   |HelloApp.g.en-US.resources:window1.baml,Stack1:System.Windows.Controls.StackPanel.$Content,Ignore,FALSE, FALSE,,#Text1;#Text2;|
   |HelloApp. g. en-US. Resources: Window1. BAML, Text1: System. Windows. Controls. TextBlock. $Content, None, TRUE, TRUE, Hello World|
   |HelloApp. g. en-US. Resources: Window1. BAML, Text2: System. Windows. Controls. TextBlock. $Content, None, true, true, World|

   Sedm polí:  
  
   1. **Název BAML** Název prostředku BAML s ohledem na satelitní sestavení zdrojového jazyka.  
  
   2. **Klíč prostředku**. Lokalizovaný identifikátor prostředku.  
  
   3. **Kategorie**. Typ hodnoty. Viz [lokalizace atributů a komentářů](localization-attributes-and-comments.md).  
  
   4. **Čitelnost**. Určuje, zda je možné hodnotu číst pomocí lokalizátora. Viz [lokalizace atributů a komentářů](localization-attributes-and-comments.md).  
  
   5. **Upravitelnost**. Určuje, zda lze hodnotu upravit pomocí lokalizátora. Viz [lokalizace atributů a komentářů](localization-attributes-and-comments.md).  
  
   6. **Komentáře**. Další popis hodnoty, která vám pomůže určit, jak je hodnota lokalizována. Viz [lokalizace atributů a komentářů](localization-attributes-and-comments.md).  
  
   7. **Hodnota**. Textová hodnota, která se má přeložit na požadovanou jazykovou verzi.  
  
   Následující tabulka ukazuje, jak se tato pole mapují na hodnoty oddělené v souboru. CSV:  
  
   |Název BAML|Klíč prostředku|Kategorie|Čitelnost|Upravitelnost|Komentáře|Value|  
   |---------------|------------------|--------------|-----------------|-------------------|--------------|-----------|
   |HelloApp.g.en-US.resources:window1.baml|Stack1:System.Windows.Controls.StackPanel.$Content|Ignorovat|CHYBNÉ|CHYBNÉ||#Text1;#Text2|
   |HelloApp.g.en-US.resources:window1.baml|Text1:System.Windows.Controls.TextBlock.$Content|Žádné|PODMÍNKA|PODMÍNKA||Hello World|
   |HelloApp.g.en-US.resources:window1.baml|Text2:System.Windows.Controls.TextBlock.$Content|Žádné|PODMÍNKA|PODMÍNKA||Vylučte ze světa|
  
   Všimněte si, že všechny hodnoty pole **Komentáře** neobsahují žádné hodnoty; Pokud pole nemá hodnotu, je prázdné. Všimněte si také, že položka v prvním řádku není čitelná ani upravitelná a má "Ignore" jako hodnotu **kategorie** , všechny, které označují, že hodnotu nelze lokalizovat.  
  
4. Chcete-li usnadnit zjišťování lokalizovatelných položek v analyzovaných souborech, zejména ve velkých souborech, můžete položky řadit nebo filtrovat podle **kategorie**, **čitelnosti**a volby. Můžete například vyfiltrovat nečitelný a neupravitelné hodnoty.  
  
<a name="translate_loc_content"></a>   
## <a name="translate-the-localizable-content"></a>Přeložit Lokalizovatelný obsah  
 Použijte libovolný nástroj, který máte k dispozici pro překlad extrahovaný obsah. Dobrým způsobem, jak to provést, je zapsání prostředků do souboru. csv a jejich zobrazení [!INCLUDE[TLA#tla_xl](../../../../includes/tlasharptla-xl-md.md)]v nástroji, provádění změn v překladu na poslední sloupec (hodnota).  
  
<a name="merge_translations"></a>   
## <a name="use-locbaml-to-generate-a-new-resourcesdll-file"></a>Použití LocBaml k vygenerování nového souboru. Resources. dll  
 Obsah, který byl identifikován analýzou HelloApp. Resources. dll s LocBaml, byl přeložen a musí být sloučen zpět do původní aplikace. K vygenerování nového souboru. Resources. dll použijte možnost **Generate** nebo **-g** .  
  
1. Pomocí následující syntaxe Vygenerujte nový soubor HelloApp. Resources. dll. Označte jazykovou verzi jako en-US (/CUL: en-US).  
  
     **LocBaml. exe/Generate HelloApp. Resources. dll/trans: Hello. csv/out: c:\/CUL: en-US**  
  
    > [!NOTE]
    >  Pokud vstupní soubor Hello. csv není ve stejném adresáři jako spustitelný soubor LocBaml. exe, přesuňte jeden ze souborů tak, aby oba soubory byly ve stejném adresáři.  
  
2. Nahraďte starý soubor HelloApp. Resources. dll v adresáři C:\HelloApp\Bin\Debug\en-US\HelloApp.resources.dll nově vytvořeným souborem HelloApp. Resources. dll.  
  
3. V aplikaci by se teď měly přeložit "Hello World" a "rozvažovat World".  
  
4. Chcete-li přeložit na jinou jazykovou verzi, použijte jazykovou verzi jazyka, na který překládáte. Následující příklad ukazuje, jak převést na francouzština – kanadská:  
  
     **LocBaml.exe /generate HelloApp.resources.dll /trans:Hellofr-CA.csv /out:c:\ /cul:fr-CA**  
  
5. Ve stejném sestavení jako hlavní sestavení aplikace vytvořte novou složku specifickou pro jazykovou verzi, která bude zaustájena nové satelitní sestavení. V případě francouzštiny (kanadská) by tato složka byla fr-CA.  
  
6. Zkopírujte vygenerované satelitní sestavení do nové složky.  
  
7. Chcete-li otestovat nové satelitní sestavení, je nutné změnit jazykovou verzi, ve které bude aplikace spuštěna. Toto lze provést jedním ze dvou způsobů:  
  
    - Změňte místní nastavení operačního systému (možnost**Spustit** &#124; **Ovládací panely** &#124; v nabídce **místní a jazyk**).  
  
    - Do App.xaml.cs přidejte do aplikace následující kód:  
  
   [!code-xaml[LocBamlChangeCultureSnippets#LocBamlChangeCultureMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/CSharp/App.xaml#locbamlchangeculturemarkup)]
   [!code-csharp[LocBamlChangeCultureSnippets#LocBamlChangeCultureCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/CSharp/App.xaml.cs#locbamlchangeculturecodebehind)]
   [!code-vb[LocBamlChangeCultureSnippets#LocBamlChangeCultureCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/VisualBasic/Application.xaml.vb#locbamlchangeculturecodebehind)]  
  
<a name="Some_Tips_for_Using_LocBaml"></a>   
## <a name="some-tips-for-using-locbaml"></a>Několik tipů pro použití LocBaml  
  
- Všechna závislá sestavení, která definují vlastní ovládací prvky, musí být zkopírována do místního adresáře LocBaml nebo nainstalována do mezipaměti GAC. To je nezbytné, protože rozhraní API pro lokalizaci musí mít přístup k závislým sestavením při čtení binárního XAML (BAML).  
  
- Pokud je hlavní sestavení podepsáno, vygenerované DLL prostředku musí být také podepsáno, aby bylo možné ho načíst.  
  
- Verze lokalizované knihovny DLL prostředku musí být synchronizována s hlavním sestavením.  
  
<a name="Whats_Next"></a>   
## <a name="whats-next"></a>Co dál  
 Nyní byste měli mít základní informace o tom, jak používat nástroj LocBaml.  Měli byste být schopni vytvořit soubor, který obsahuje identifikátory UID. Pomocí nástroje LocBaml byste měli být schopni analyzovat soubor pro extrakci lokalizovatelné obsahu a po překladu obsahu byste měli být schopni vygenerovat soubor. Resources. dll, který slučuje přeložený obsah. Toto téma neobsahuje všechny možné podrobnosti, ale nyní máte znalosti potřebné k použití LocBaml pro lokalizaci vašich aplikací.  
  
## <a name="see-also"></a>Viz také:

- [Globalizace pro WPF](globalization-for-wpf.md)
- [Přehled automatického rozložení](use-automatic-layout-overview.md)
