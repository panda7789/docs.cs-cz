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
ms.openlocfilehash: 1190fb739e7c1873532e96b50399ac0deb6bb51c
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/20/2018
ms.locfileid: "46478594"
---
# <a name="how-to-localize-an-application"></a>Postupy: Lokalizace aplikace
Tento kurz vysvětluje vytvoření lokalizované aplikace s použitím locbaml – nástroj.  
  
> [!NOTE]
>  Locbaml – nástroj není aplikace připravené pro produkční prostředí. Zobrazí se jako ukázka, která používá některé lokalizace rozhraní API a ukazuje, jak můžete například napsat lokalizační nástroj.  
  
<a name="Introduction"></a>   
## <a name="overview"></a>Přehled  
 Tato diskuse poskytuje podrobný postup k lokalizace aplikace. Nejprve se připravte aplikaci tak, aby může být extrahována text, který bude fungovat. Poté, co je přeložen text, sloučí přeložený text do novou kopii původní aplikace.  
  
<a name="Requirements"></a>   
## <a name="requirements"></a>Požadavky  
 V průběhu této diskuse, budete používat [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)], což je kompilátor, který se spustí z příkazového řádku.  
  
 Navíc vám bude nastaven na použití souboru projektu. Pokyny k používání [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] a soubory projektu, přečtěte si [sestavovat a nasazovat](../../../../docs/framework/wpf/app-development/building-and-deploying-wpf-applications.md).  
  
 Všechny příklady v této diskuzi použít jako jazykové verze en US (angličtina-USA). To umožňuje seznámení se základními kroky příklady bez instalace jiný jazyk.  
  
<a name="create_sample_app"></a>   
## <a name="create-a-sample-application"></a>Vytvoření ukázkové aplikace  
 V tomto kroku se připravíte aplikace pro lokalizaci. V [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] ukázky HelloApp ukázky pochází, který se použije pro příklady v této diskuzi. Pokud chcete tuto ukázku použít, stáhněte si [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] souborů z doručené pošty [locbaml – nástroj ukázka](https://go.microsoft.com/fwlink/?LinkID=160016).  
  
1.  Vývoj vaší aplikace do bodu, ve kterém chcete spustit lokalizace.  
  
2.  Zadejte jazyk pro vývoj v souboru projektu tak, aby [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] generuje do hlavního sestavení a satelitní sestavení (soubor s. resources.dll rozšíření) tak, aby obsahovala neutrální jazyk prostředků. Soubor projektu v ukázce HelloApp je HelloApp.csproj. V tomto souboru najdete vývojový jazyk identifikována takto:  
  
     `<UICulture>en-US</UICulture>`  
  
3.  Přidat identifikátory UID byly pro vaši [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubory. Identifikátory UID byly se používají ke sledování změn souborů a k identifikaci položky, které se musí přeložit. Chcete-li přidat identifikátory UID byly k souborům, spusťte **updateuid** v souboru projektu:  
  
     **MSBuild – t: updateuid helloapp.csproj**  
  
     Chcete-li ověřit, zda máte žádné chybějící nebo duplicitní identifikátory UID, spusťte **checkuid**:  
  
     **MSBuild – t: checkuid helloapp.csproj**  
  
     Po spuštění **updateuid**, vaše soubory by měly obsahovat identifikátory UID. Například v souboru Pane1.xaml HelloApp byste měli najít následující:  
  
     `<StackPanel x:Uid="StackPanel_1">`  
  
     `<TextBlock x:Uid="TextBlock_1">Hello World</TextBlock>`  
  
     `<TextBlock x:Uid="TextBlock_2">Goodbye World</TextBlock>`  
  
     `</StackPanel>`  
  
<a name="create_dll"></a>   
## <a name="create-the-neutral-language-resources-satellite-assembly"></a>Vytvořit satelitní sestavení prostředků neutrální jazyk  
 Po aplikaci bylo nakonfigurováno pro generování satelitního sestavení neutrální jazyk prostředků, sestavte aplikaci. Tím se vytvoří sestavení hlavní aplikace, stejně jako neutrální jazyk prostředků satelitní sestavení, který vyžaduje locbaml – pro lokalizaci. K sestavení aplikace:  
  
1.  Kompilace HelloApp k vytvoření [!INCLUDE[TLA#tla_dll](../../../../includes/tlasharptla-dll-md.md)]:  
  
     **MSBuild helloapp.csproj**  
  
2.  Sestavení nově vytvořeného hlavní aplikace HelloApp.exe, se vytvoří v následující složce:  
  
     `C:\HelloApp\Bin\Debug\`  
  
3.  Satelitní sestavení nově vytvořeného neutrální jazyk prostředků, HelloApp.resources.dll, se vytvoří v následující složce:  
  
     `C:\HelloApp\Bin\Debug\en-US\`  
  
<a name="build_locbaml"></a>   
## <a name="build-the-locbaml-tool"></a>Sestavení locbaml – nástroj  
  
1.  Všechny soubory potřebné k vývoji locbaml – jsou umístěny v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ukázky. Stáhnout soubory jazyka C# z [locbaml – nástroj ukázka](https://go.microsoft.com/fwlink/?LinkID=160016).  
  
2.  Z příkazového řádku spusťte soubor projektu (locbaml.csproj) pro sestavení nástroje:  
  
     **MSBuild locbaml.csproj**  
  
3.  Přejděte do adresáře Bin\Release nově vytvořený spustitelný soubor (locbaml.exe) se nenašel. Example:C:\LocBaml\Bin\Release\locbaml.exe.  
  
4.  Možnosti, které můžete zadat při spuštění locbaml – jsou následující:  
  
    -   **analyzovat** nebo **-p:** analyzuje Baml prostředky, nebo [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] soubory vygenerovat soubor CSV nebo .txt.  
  
    -   **Generovat** nebo **-g:** generuje lokalizované binární soubor s použitím přeložený soubor.  
  
    -   **navýšení kapacity** nebo **-o** {*filedirectory*] **:** název výstupního souboru.  
  
    -   **jazyková verze** nebo **- cul** {*jazykovou verzi*] **:** národního prostředí z výstupu sestavení.  
  
    -   **překlad** nebo **- trans** {*translation.csv*] **:** přeložena nebo lokalizovaný soubor.  
  
    -   **asmpath** nebo **- asmpath:** {*filedirectory*] **:** Pokud vaše [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kód obsahuje vlastní ovládací prvky, je nutné zadat  **asmpath** sestavení vlastního ovládacího prvku.  
  
    -   **nologo:** zobrazuje informace bez logo nebo autorských práv.  
  
    -   **verbose:** zobrazí informace o režimu s komentářem.  
  
    > [!NOTE]
    >  Pokud potřebujete seznam možností, pokud spouštíte nástroj, zadejte **LocBaml.exe** a stiskněte klávesu ENTER.  
  
<a name="parse_dll"></a>   
## <a name="use-locbaml-to-parse-a-file"></a>Locbaml – použít k analýze souboru  
 Teď, když jste vytvořili locbaml – nástroj, budete chtít použít k analýze HelloApp.resources.dll extrahování textového obsahu, který bude lokalizovaný.  
  
1.  Zkopírujte LocBaml.exe bin\debug složky vaší aplikace, kde byl vytvořen sestavení hlavní aplikace.  
  
2.  K analýze souboru satelitní sestavení a výstup uložit jako soubor .csv, použijte následující příkaz:  
  
     **LocBaml.exe /parse HelloApp.resources.dll /out:Hello.csv**  
  
    > [!NOTE]
    >  Pokud vstupní soubor HelloApp.resources.dll, není v přesunout do stejného adresáře jako LocBaml.exe jeden ze souborů tak, že oba soubory jsou ve stejném adresáři.  
  
3.  Když spustíte locbaml – analyzovat soubory, výstup se skládá z sedm polí oddělených čárkami (CSV soubory) nebo karty (soubory s příponou .txt). Následuje ukázka soubor .csv analyzovanou klauzuli pro HelloApp.resources.dll:

   | |
   |-|
   |HelloApp.g.en US.resources:window1.baml, Stack1:System.Windows.Controls.StackPanel. $Content, ignorovat FALSE; hodnota FALSE, #Text1; #Text2;|
   |HelloApp.g.en US.resources:window1.baml, Text1:System.Windows.Controls.TextBlock. $Content, None, TRUE, TRUE, Hello World|
   |HelloApp.g.en US.resources:window1.baml, Text2:System.Windows.Controls.TextBlock. $Content, None, TRUE, TRUE, Goodbye World|

   Sedm pole jsou:  
  
   1.  **Název BAML**. Název prostředku BAML s ohledem na zdrojový jazyk satelitní sestavení.  
  
   2.  **Klíč prostředku**. Identifikátor lokalizovaný prostředek.  
  
   3.  **Kategorie**. Typ hodnoty. Zobrazit [atributy a komentáře lokalizace](../../../../docs/framework/wpf/advanced/localization-attributes-and-comments.md).  
  
   4.  **Lepší čitelnost**. Hodnota určuje, zda mohou být přečteny lokalizátora. Zobrazit [atributy a komentáře lokalizace](../../../../docs/framework/wpf/advanced/localization-attributes-and-comments.md).  
  
   5.  **Modifiability**. Určuje, zda můžete změnit hodnotu lokalizátora. Zobrazit [atributy a komentáře lokalizace](../../../../docs/framework/wpf/advanced/localization-attributes-and-comments.md).  
  
   6.  **Komentáře**. Další popis hodnotu sloužící k určení, jak je lokalizován hodnotu. Zobrazit [atributy a komentáře lokalizace](../../../../docs/framework/wpf/advanced/localization-attributes-and-comments.md).  
  
   7.  **Hodnota**. Textová hodnota pro převod na požadovanou jazykovou verzi.  
  
   Následující tabulka ukazuje, jak tato pole se mapují na hodnoty s oddělovači souboru CSV:  
  
   |Název BAML|Klíč prostředku|Kategorie|Lepší čitelnost|Modifiability|Komentáře|Hodnota|  
   |---------------|------------------|--------------|-----------------|-------------------|--------------|-----------|
   |HelloApp.g.en US.resources:window1.baml|Stack1:System.Windows.Controls.StackPanel.$Content|Ignorovat|FALSE|FALSE||#Text1; #Text2|
   |HelloApp.g.en US.resources:window1.baml|Text1:System.Windows.Controls.TextBlock.$Content|Žádné|HODNOTA TRUE|HODNOTA TRUE||Hello World|
   |HelloApp.g.en US.resources:window1.baml|Text2:System.Windows.Controls.TextBlock.$Content|Žádné|HODNOTA TRUE|HODNOTA TRUE||Goodbye World|
  
   Všimněte si, že všechny hodnoty **komentáře** pole neobsahují žádné hodnoty; Pokud pole nemá hodnotu, je prázdný. Všimněte si také, že položka v prvním řádku není ani čitelná ani měnit a má "Ignorovat" jako jeho **kategorie** hodnoty, které označuje, že hodnota není lokalizovatelné.  
  
4.  Aby se usnadnilo zjišťování lokalizovatelné položek v analyzované soubory, zejména ve velkých souborech si seřadíte nebo vyfiltrujete položky podle **kategorie**, **čitelnost**, a **Modifiability**. Můžete například vyfiltrovat hodnoty nejde přečíst a neupravitelných.  
  
<a name="translate_loc_content"></a>   
## <a name="translate-the-localizable-content"></a>Přeložit lokalizovatelné obsahu  
 Použijte jakýkoli nástroj, že máte k dispozici pro převod extrahovaného obsahu. Je dobrým způsobem, jak to provést pro zápis souboru prostředky, které soubor .csv a zobrazit v [!INCLUDE[TLA#tla_xl](../../../../includes/tlasharptla-xl-md.md)], aby překlad změní na poslední sloupec (hodnota).  
  
<a name="merge_translations"></a>   
## <a name="use-locbaml-to-generate-a-new-resourcesdll-file"></a>Locbaml – použít ke generování nové. resources.dll souboru  
 Obsah, který byl identifikován analýzou HelloApp.resources.dll s locbaml – byl přeložen a musí být sloučeny zpět do původní aplikace. Použití **generovat** nebo **-g** možnost k vygenerování nového. resources.dll souboru.  
  
1.  Použijte následující syntaxi pro vytvoření nového souboru HelloApp.resources.dll. Označit jazykovou verzi jako en US (/ cul:en-US).  
  
     **LocBaml.exe / generovat HelloApp.resources.dll /trans:Hello.csv /out:c: \ /cul:en-USA**  
  
    > [!NOTE]
    >  Pokud vstupní soubor Hello.csv, není ve stejném adresáři jako spustitelný soubor, LocBaml.exe, přesuňte jeden ze souborů tak, že oba soubory jsou ve stejném adresáři.  
  
2.  Nahraďte původní soubor v adresáři C:\HelloApp\Bin\Debug\en-US\HelloApp.resources.dll HelloApp.resources.dll váš nově vytvořený soubor HelloApp.resources.dll.  
  
3.  "Hello World" a "Goodbye World" by měl nyní přeložený do vaší aplikace.  
  
4.  Pro převod na jinou jazykovou verzi, pomocí jazyka, který se překládá na jazykovou verzi. Následující příklad ukazuje, jak převést French-Canadian:  
  
     **LocBaml.exe / generovat HelloApp.resources.dll /trans:Hellofr-CA.csv /out:c: \ /cul:fr-certifikační Autority**  
  
5.  Ve stejném sestavení jako sestavení hlavní aplikace vytvořte novou složku specifické pro jazykovou verzi k umístění nového satelitní sestavení. U French-Canadian bude složka fr-CA.  
  
6.  Zkopírujte do nové složky generovaných satelitních sestavení.  
  
7.  Otestovat nové satelitní sestavení, budete muset změnit jazykové verze, ve kterém aplikace poběží. Toto lze provést jedním ze dvou způsobů:  
  
    -   Změnit místní nastavení operačního systému (**Start** &#124; **ovládací panely** &#124; **místní a jazykové nastavení**).  
  
    -   Ve vaší aplikaci přidejte následující kód do souboru App.xaml.cs:  
  
   [!code-xaml[LocBamlChangeCultureSnippets#LocBamlChangeCultureMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/CSharp/App.xaml#locbamlchangeculturemarkup)]
   [!code-csharp[LocBamlChangeCultureSnippets#LocBamlChangeCultureCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/CSharp/App.xaml.cs#locbamlchangeculturecodebehind)]
   [!code-vb[LocBamlChangeCultureSnippets#LocBamlChangeCultureCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/VisualBasic/Application.xaml.vb#locbamlchangeculturecodebehind)]  
  
<a name="Some_Tips_for_Using_LocBaml"></a>   
## <a name="some-tips-for-using-locbaml"></a>Některé tipy pro používání locbaml –  
  
-   Všechna závislá sestavení, definující vlastní ovládací prvky musí být zkopírován do místního adresáře locbaml – nebo instaluje se do mezipaměti GAC. To je nezbytné, protože lokalizace rozhraní API musí mít přístup k závislé sestavení při čtení [!INCLUDE[TLA#tla_baml](../../../../includes/tlasharptla-baml-md.md)].  
  
-   Pokud hlavní sestavení je podepsáno, musí být vygenerovaný knihovna DLL prostředků podepsané také v pořadí, který se má načíst.  
  
-   Verze lokalizovaný prostředek knihovny DLL musí být synchronizovány s hlavním sestavením.  
  
<a name="Whats_Next"></a>   
## <a name="whats-next"></a>Co se chystá  
 Nyní byste měli mít základní znalosti o tom, jak používat locbaml – nástroj.  Můžete by měl být schopen provést soubor obsahující identifikátory UID. S použitím locbaml – nástroj, byste měli analyzovat soubor, který chcete extrahovat lokalizovatelné obsah a po obsahu se kombinují, by měla být schopna generovat. resources.dll soubor, který sloučí přeloženého obsahu. Toto téma neobsahuje všechny možné podrobnosti, ale Teď máte znalosti, které jsou nezbytné pro účely locbaml – lokalizace vašich aplikací.  
  
## <a name="see-also"></a>Viz také  
 [Globalizace pro WPF](../../../../docs/framework/wpf/advanced/globalization-for-wpf.md)  
 [Přehled automatického rozložení](../../../../docs/framework/wpf/advanced/use-automatic-layout-overview.md)
