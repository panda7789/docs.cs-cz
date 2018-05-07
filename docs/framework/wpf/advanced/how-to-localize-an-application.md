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
ms.openlocfilehash: ae73ab92ebf3089eebf51f40b0c144f3dbea44da
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-localize-an-application"></a>Postupy: Lokalizace aplikace
Tento kurz vysvětluje vytvoření lokalizované aplikace pomocí nástroje LocBaml.  
  
> [!NOTE]
>  Nástroj LocBaml není aplikace produkční prostředí. Zobrazí se jako ukázku, která se využívá část lokalizace rozhraní API a ukazuje, jak může nástroj lokalizace zapsat.  
  
<a name="Introduction"></a>   
## <a name="overview"></a>Přehled  
 Tato diskuse poskytuje podrobný postup k lokalizace aplikace. Nejprve připravte aplikaci tak, aby lze extrahovat text, který bude převeden. Po text přeloženy, bude sloučit přeložený text do novou kopii původní aplikace.  
  
<a name="Requirements"></a>   
## <a name="requirements"></a>Požadavky  
 V průběhu toto pojednání bude používat [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)], což je kompilátoru, která se spouští z příkazového řádku.  
  
 Také budete vyzváni k použít soubor projektu. Pokyny, jak používat [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] a soubory projektu, najdete v části [sestavení a nasazení](../../../../docs/framework/wpf/app-development/building-and-deploying-wpf-applications.md).  
  
 V příkladech v toto pojednání použít en US (angličtina-US) jako jazykovou verzi. To umožňuje pracovat provede příklady bez instalace v jiném jazyce.  
  
<a name="create_sample_app"></a>   
## <a name="create-a-sample-application"></a>Vytvoření ukázkové aplikace  
 V tomto kroku se připravíte aplikace pro lokalizaci. V [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] ukázky HelloApp poskytnut vzorek, který se použije pro příklady kódu v toto pojednání. Pokud chcete použít tuto ukázku, stáhněte si [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] souborů z [ukázkový nástroj LocBaml](http://go.microsoft.com/fwlink/?LinkID=160016).  
  
1.  Vývoj aplikace do bodu, kde chcete spustit lokalizace.  
  
2.  Zadejte jazyk vývoj v souboru projektu tak, aby [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] vygeneruje hlavní sestavení a satelitní sestavení (soubor s. rozšíření resources.dll) tak, aby obsahovala neutrální jazykové prostředky. Soubor projektu v ukázce HelloApp je HelloApp.csproj. V tomto souboru zjistíte, vývoj jazyk identifikovat následujícím způsobem:  
  
     `<UICulture>en-US</UICulture>`  
  
3.  Přidat UID k vaší [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubory. UID se používají ke sledování změn souborů a k identifikaci položek, které se musí přeložit. Chcete-li přidat UID vaše soubory, spusťte **updateuid** v souboru projektu:  
  
     **helloapp.csproj /t:updateuid nástroje MSBuild**  
  
     Pokud chcete ověřit, zda máte žádné chybějící nebo duplicitní UID, spusťte **checkuid**:  
  
     **helloapp.csproj /t:checkuid nástroje MSBuild**  
  
     Po spuštění **updateuid**, vaše soubory by měly obsahovat UID. Například v souboru Pane1.xaml HelloApp, byste měli najít následující:  
  
     `<StackPanel x:Uid="StackPanel_1">`  
  
     `<TextBlock x:Uid="TextBlock_1">Hello World</TextBlock>`  
  
     `<TextBlock x:Uid="TextBlock_2">Goodbye World</TextBlock>`  
  
     `</StackPanel>`  
  
<a name="create_dll"></a>   
## <a name="create-the-neutral-language-resources-satellite-assembly"></a>Vytvořit neutrální jazyk prostředky satelitní sestavení  
 Po dokončení konfigurace aplikace k vygenerování satelitní sestavení prostředky neutrální jazyk, je sestavení aplikace. Tím se vytvoří sestavení hlavní aplikace, stejně jako neutrální jazyk prostředky satelitní sestavení, které vyžadují LocBaml pro lokalizaci. K vytvoření aplikace:  
  
1.  Kompilace HelloApp k vytvoření [!INCLUDE[TLA#tla_dll](../../../../includes/tlasharptla-dll-md.md)]:  
  
     **helloapp.csproj nástroje MSBuild**  
  
2.  Nově vytvořená hlavní aplikace sestavení, HelloApp.exe, je vytvořen v následující složce:  
  
     `C:\HelloApp\Bin\Debug\`  
  
3.  Vytváření satelitních sestavení prostředky nově vytvořený neutrální jazyk, HelloApp.resources.dll, v následující složce:  
  
     `C:\HelloApp\Bin\Debug\en-US\`  
  
<a name="build_locbaml"></a>   
## <a name="build-the-locbaml-tool"></a>Nástroj LocBaml sestavení  
  
1.  Všechny soubory potřebné k vytvoření LocBaml jsou umístěny v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ukázky. Stáhnout soubory C# z [ukázkový nástroj LocBaml](http://go.microsoft.com/fwlink/?LinkID=160016).  
  
2.  Z příkazového řádku spusťte soubor projektu (locbaml.csproj) k vytvoření nástroje:  
  
     **locbaml.csproj nástroje MSBuild**  
  
3.  Přejděte do adresáře Bin\Release nově vytvořený spustitelný soubor (locbaml.exe). Example:C:\LocBaml\Bin\Release\locbaml.exe.  
  
4.  Možnosti, které můžete zadat, když spustíte LocBaml jsou následující:  
  
    -   **analyzovat** nebo **-p:** analyzuje Baml prostředky, nebo [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] soubory můžete vytvořit soubor .csv nebo .txt.  
  
    -   **Generovat** nebo **-g:** generuje lokalizované binárního souboru pomocí přeložený souboru.  
  
    -   **out** nebo **-o** {*filedirectory*] **:** názvu výstupního souboru.  
  
    -   **jazyková verze** nebo **- cul** {*jazykovou verzi*] **:** národního prostředí výstupu sestavení.  
  
    -   **překlad** nebo **- napříč** {*translation.csv*] **:** překládané nebo lokalizované souboru.  
  
    -   **asmpath** nebo **- asmpath:** {*filedirectory*] **:** Pokud vaše [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kód obsahuje vlastní ovládací prvky, je nutné zadat  **asmpath** sestavení vlastního ovládacího prvku.  
  
    -   **nologo:** zobrazí žádné logo nebo copyright informace.  
  
    -   **verbose:** zobrazí informace o podrobné režimu.  
  
    > [!NOTE]
    >  Pokud potřebujete seznam možností, pokud používáte nástroj, zadejte **LocBaml.exe** a stiskněte klávesu ENTER.  
  
<a name="parse_dll"></a>   
## <a name="use-locbaml-to-parse-a-file"></a>Použití LocBaml analyzovat soubor  
 Teď, když jste vytvořili nástroj LocBaml, budete chtít použít k analýze HelloApp.resources.dll k extrahování obsahu text, který bude možné lokalizovat.  
  
1.  Zkopírujte LocBaml.exe do složky bin\debug vaší aplikace, které bylo vytvořeno sestavení hlavní aplikace.  
  
2.  Pokud chcete analyzovat soubor satelitní sestavení a uložit jako soubor CSV, použijte následující příkaz:  
  
     **LocBaml.exe /parse HelloApp.resources.dll /out:Hello.csv**  
  
    > [!NOTE]
    >  Pokud vstupní soubor HelloApp.resources.dll, není v přesunout do stejného adresáře jako LocBaml.exe jeden ze souborů tak, aby byly oba soubory ve stejném adresáři.  
  
3.  Při spuštění LocBaml analyzovat soubory výstup se skládá z sedm pole oddělený čárkami (.csv soubory) nebo karty (soubory s příponou .txt). Na obrázku je soubor .csv Analyzovaná pro HelloApp.resources.dll:

   | |
   |-|
   |HelloApp.g.en US.resources:window1.baml, Stack1:System.Windows.Controls.StackPanel. $Content, FALSE, FALSE,, ignorovat #Text1; #Text2;|
   |HelloApp.g.en US.resources:window1.baml, Text1:System.Windows.Controls.TextBlock. $Content, None, nastavena hodnota TRUE, TRUE,, Hello World|
   |HelloApp.g.en US.resources:window1.baml, Text2:System.Windows.Controls.TextBlock. $Content, None, TRUE, TRUE,, dát sbohem všem World|

   Pole sedm jsou:  
  
   1.  **Název BAML**. Název prostředku BAML s ohledem na satelitní sestavení jazyka zdroje.  
  
   2.  **Klíč prostředku**. Identifikátor lokalizovaný prostředek.  
  
   3.  **Kategorie**. Typ hodnoty. V tématu [atributů lokalizace a komentáře](../../../../docs/framework/wpf/advanced/localization-attributes-and-comments.md).  
  
   4.  **Čitelnost**. Hodnota zda mohou být přečteny lokalizátora. V tématu [atributů lokalizace a komentáře](../../../../docs/framework/wpf/advanced/localization-attributes-and-comments.md).  
  
   5.  **Modifiability**. Jestli může být hodnota upravit lokalizátora. V tématu [atributů lokalizace a komentáře](../../../../docs/framework/wpf/advanced/localization-attributes-and-comments.md).  
  
   6.  **Komentáře**. Další popis hodnoty, které vám pomohou určit, jak je lokalizované hodnotu. V tématu [atributů lokalizace a komentáře](../../../../docs/framework/wpf/advanced/localization-attributes-and-comments.md).  
  
   7.  **Hodnota**. Textové hodnoty nepřeloží na požadovanou jazykovou verzi.  
  
   Následující tabulka ukazuje, jak mapování těchto polí na hodnoty s oddělovači souboru CSV:  
  
   |Název BAML|Klíč prostředku|Kategorie|Čitelnost|Modifiability|Komentáře|Hodnota|  
   |---------------|------------------|--------------|-----------------|-------------------|--------------|-----------|
   |HelloApp.g.en US.resources:window1.baml|Stack1:System.Windows.Controls.StackPanel.$Content|Ignorovat|FALSE|FALSE||#Text1; #Text2|
   |HelloApp.g.en US.resources:window1.baml|Text1:System.Windows.Controls.TextBlock.$Content|Žádné|HODNOTA TRUE|HODNOTA TRUE||Hello World|
   |HelloApp.g.en US.resources:window1.baml|Text2:System.Windows.Controls.TextBlock.$Content|Žádné|HODNOTA TRUE|HODNOTA TRUE||Dát sbohem všem World|
  
   Všimněte si, že všechny hodnoty **komentáře** pole neobsahují žádné hodnoty; Pokud pole nemá hodnotu, je prázdný. Všimněte si také že položky v prvním řádku není čitelný ani upravitelnými a že má "Ignorovat" jako jeho **kategorie** hodnotu, což znamená, že hodnota není lokalizovatelný.  
  
4.  K usnadnění zjišťování lokalizovatelný položek v analyzované soubory, zejména ve velkých souborech, můžete řazení nebo filtrovat položky dle **kategorie**, **čitelnost**, a **Modifiability**. Například můžete odfiltrovat nečitelná a unmodifiable hodnoty.  
  
<a name="translate_loc_content"></a>   
## <a name="translate-the-localizable-content"></a>Převede lokalizovatelný obsahu  
 Pomocí libovolného nástroje, která je k dispozici přeložit extrahovaného obsahu. Dobrým způsobem, jak to udělat je napsat prostředky do CSV souborů a jejich zobrazením v [!INCLUDE[TLA#tla_xl](../../../../includes/tlasharptla-xl-md.md)], což překlad změní na poslední sloupec (hodnota).  
  
<a name="merge_translations"></a>   
## <a name="use-locbaml-to-generate-a-new-resourcesdll-file"></a>Můžete vygenerovat nový pomocí LocBaml. resources.dll souboru  
 Obsah, kterou identifikovalo analýza HelloApp.resources.dll s LocBaml byl přeložen a je potřeba sloučit zpět do původní aplikace. Použití **generovat** nebo **-g** možnost k vygenerování nového. resources.dll souboru.  
  
1.  Pomocí následující syntaxe vygenerujte nový soubor HelloApp.resources.dll. Označit jako en US jazykovou verzi (nebo cul:en-USA).  
  
     **LocBaml.exe / generovat HelloApp.resources.dll /trans:Hello.csv /out:c: \ /cul:en-USA**  
  
    > [!NOTE]
    >  Pokud vstupní soubor Hello.csv, není ve stejném adresáři jako spustitelný soubor, LocBaml.exe, přesuňte jeden ze souborů tak, aby byly oba soubory ve stejném adresáři.  
  
2.  Nahraďte starý HelloApp.resources.dll soubor v adresáři C:\HelloApp\Bin\Debug\en-US\HelloApp.resources.dll vaše nově vytvořený soubor HelloApp.resources.dll.  
  
3.  "Hello, World" a "Goodbye World" by měl nyní přeložený do vaší aplikace.  
  
4.  Chcete-li převede na jinou jazykovou verzi, použijte jazyka, který se překladu pro jazykovou verzi. Následující příklad ukazuje, jak nepřeloží na French-Canadian:  
  
     **LocBaml.exe / generovat HelloApp.resources.dll /trans:Hellofr-CA.csv /out:c: \ /cul:fr-certifikační Autority**  
  
5.  Ve stejném sestavení jako sestavení hlavní aplikace vytvořte novou složku specifické pro jazykovou verzi pro uložení nové satelitní sestavení. Pro French-Canadian bude složka fr-CA.  
  
6.  Zkopírujte vygenerovaný satelitní sestavení do nové složky.  
  
7.  Pokud chcete vyzkoušet nové satelitní sestavení, potřebujete změnit jazykové verze, ve kterém aplikace poběží. Toto lze provést jedním ze dvou způsobů:  
  
    -   Změnit místní nastavení operačního systému (**spustit** &#124; **ovládací panely** &#124; **místní a jazykové nastavení**).  
  
    -   V aplikaci přidejte následující kód do souboru App.xaml.cs:  
  
   [!code-xaml[LocBamlChangeCultureSnippets#LocBamlChangeCultureMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/CSharp/App.xaml#locbamlchangeculturemarkup)]
   [!code-csharp[LocBamlChangeCultureSnippets#LocBamlChangeCultureCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/CSharp/App.xaml.cs#locbamlchangeculturecodebehind)]
   [!code-vb[LocBamlChangeCultureSnippets#LocBamlChangeCultureCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/VisualBasic/Application.xaml.vb#locbamlchangeculturecodebehind)]  
  
<a name="Some_Tips_for_Using_LocBaml"></a>   
## <a name="some-tips-for-using-locbaml"></a>Tipy pro používání LocBaml  
  
-   Všechny závislé sestavení, které definují vlastní ovládací prvky, musí být zkopírován do místního adresáře LocBaml nebo nainstalovat do mezipaměti GAC. To je nezbytné proto lokalizace rozhraní API musí mít přístup k závislá sestavení, při čtení [!INCLUDE[TLA#tla_baml](../../../../includes/tlasharptla-baml-md.md)].  
  
-   Pokud hlavní sestavení je podepsaný, musí v pořadí pro něj má být načten podepsané generovaného DLL prostředků.  
  
-   Verze lokalizovaný prostředek DLL musí být synchronizovány s hlavní sestavení.  
  
<a name="Whats_Next"></a>   
## <a name="whats-next"></a>Co je další  
 Teď byste měli mít základní znalosti o tom, jak používat nástroj LocBaml.  Byste měli mít zkontrolujte soubor, který obsahuje UID. Pomocí nástroje LocBaml by měl být schopen analyzovat soubor k extrahování obsahu lokalizovatelný a po obsah přeloženy, byste měli dokáže generovat. resources.dll soubor, který sloučí přeložený obsah. Toto téma neobsahuje všechny možné podrobností, ale Teď máte znalosti nezbytných k používání LocBaml pro lokalizace aplikací.  
  
## <a name="see-also"></a>Viz také  
 [Globalizace pro WPF](../../../../docs/framework/wpf/advanced/globalization-for-wpf.md)  
 [Přehled automatického rozložení](../../../../docs/framework/wpf/advanced/use-automatic-layout-overview.md)
