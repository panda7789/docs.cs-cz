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
ms.openlocfilehash: f2e7e5e8879e89806cfd457a1af80f51b91871cb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174209"
---
# <a name="how-to-localize-an-application"></a>Postupy: Lokalizace aplikace
Tento kurz vysvětluje, jak vytvořit lokalizovanou aplikaci pomocí nástroje LocBaml.  
  
> [!NOTE]
> Nástroj LocBaml není aplikace připravená k výrobě. Je prezentována jako ukázka, která používá některá lokalizační api a ukazuje, jak můžete napsat nástroj lokalizace.  
  
<a name="Introduction"></a>
## <a name="overview"></a>Přehled  
 Tato diskuse poskytuje podrobný přístup k lokalizaci aplikace. Nejprve připravíte aplikaci tak, aby text, který bude přeložen, mohl být extrahován. Po překladu textu sloučíte přeložený text do nové kopie původní aplikace.  
  
<a name="Requirements"></a>
## <a name="requirements"></a>Požadavky  
 V průběhu této diskuse budete používat modul sestavení Společnosti Microsoft (MSBuild), což je kompilátor, který běží z příkazového řádku.  
  
 Také budete vyzváni k použití souboru projektu. Pokyny k použití souborů MSBuild a project naleznete v tématu [Sestavení a nasazení](../app-development/building-and-deploying-wpf-applications.md).  
  
 Všechny příklady v této diskusi použít en US (anglicky-US) jako jazykovou verzi. To umožňuje pracovat prostřednictvím kroků příkladů bez instalace jiného jazyka.  
  
<a name="create_sample_app"></a>
## <a name="create-a-sample-application"></a>Vytvoření ukázkové aplikace  
 V tomto kroku připravíte aplikaci pro lokalizaci. Ve [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] vzorcích helloapp ukázka je zadána, která bude použita pro příklady kódu v této diskusi. Pokud chcete použít tuto ukázku, [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] stáhněte soubory z [ukázky nástroje LocBaml](https://github.com/microsoft/WPF-Samples/tree/master/Tools/LocBaml).  
  
1. Vývoj aplikace do bodu, kde chcete spustit lokalizaci.  
  
2. Zadejte vývojový jazyk v souboru projektu tak, aby MSBuild generuje hlavní sestavení a satelitní sestavení (soubor s příponou .resources.dll) obsahující neutrální jazykové prostředky. Soubor projektu v helloapp vzorku je HelloApp.csproj. V tomto souboru najdete vývojový jazyk identifikovaný takto:  
  
     `<UICulture>en-US</UICulture>`  
  
3. Přidejte do [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] souborů uidy. Uids se používají ke sledování změn v souborech a k identifikaci položek, které musí být přeloženy. Chcete-li do souborů přidat uidy, spusťte **updateuid** v souboru projektu:  
  
     **msbuild -t:updateuid helloapp.csproj**  
  
     Chcete-li ověřit, zda nechybí žádné duplicitní identifikátory UID, spusťte **příkaz checkuid**:  
  
     **msbuild -t:checkuid helloapp.csproj**  
  
     Po spuštění **updateuid**, soubory by měly obsahovat UIDs. Například v souboru Pane1.xaml HelloApp byste měli najít následující:  
  
     `<StackPanel x:Uid="StackPanel_1">`  
  
     `<TextBlock x:Uid="TextBlock_1">Hello World</TextBlock>`  
  
     `<TextBlock x:Uid="TextBlock_2">Goodbye World</TextBlock>`  
  
     `</StackPanel>`  
  
<a name="create_dll"></a>
## <a name="create-the-neutral-language-resources-satellite-assembly"></a>Vytvoření satelitního sestavení neutrálních jazykových prostředků  
 Po nakonfigurován aplikace generovat neutrální jazyk prostředky satelitní sestavení, sestavení aplikace. To generuje sestavení hlavní aplikace, stejně jako neutrální jazykové prostředky satelitní sestavení, které je vyžadováno LocBaml pro lokalizaci. Vytvoření aplikace:  
  
1. Kompilace HelloApp pro vytvoření dynamické knihovny (DLL):  
  
     **msbuild helloapp.csproj**  
  
2. Nově vytvořené sestavení hlavní aplikace HelloApp.exe je vytvořeno v následující složce:  
  
     `C:\HelloApp\Bin\Debug\`  
  
3. Nově vytvořené satelitní sestavení prostředků neutrálního jazyka HelloApp.resources.dll je vytvořeno v následující složce:  
  
     `C:\HelloApp\Bin\Debug\en-US\`  
  
<a name="build_locbaml"></a>
## <a name="build-the-locbaml-tool"></a>Sestavení nástroje LocBaml  
  
1. Všechny soubory potřebné k sestavení LocBaml [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jsou umístěny ve vzorcích. Stáhněte soubory C# z [ukázky nástroje LocBaml](https://github.com/microsoft/WPF-Samples/tree/master/Tools/LocBaml).  
  
2. Z příkazového řádku spusťte soubor projektu (locbaml.csproj) a vytvořte nástroj:  
  
     **msbuild locbaml.csproj**  
  
3. Přejděte do adresáře Bin\Release a vyhledejte nově vytvořený spustitelný soubor (locbaml.exe). Příklad:C:\LocBaml\Bin\Release\locbaml.exe.  
  
4. Možnosti, které můžete zadat při spuštění LocBaml, jsou následující:  
  
    - **parse** nebo **-p:** Analyzuje soubory Baml, prostředky nebo DLL a vygeneruje soubor .csv nebo .txt.  
  
    - **generate** or **-g:** Generuje lokalizovaný binární soubor pomocí přeloženého souboru.  
  
    - **nebo** **-o** {*filedirectory*] **:** Název výstupního souboru.  
  
    - **culture** nebo **-cul** {*culture*] **:** Národní prostředí výstupních sestavení.  
  
    - **překlad** nebo **-trans** {*translation.csv*] **:** Přeložený nebo lokalizovaný soubor.  
  
    - **asmpath** nebo **-asmpath:** {*filedirectory*] **:** Pokud váš [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kód obsahuje vlastní ovládací prvky, musíte dodat **asmpath** do sestavení vlastního ovládacího prvku.  
  
    - **nologo:** Nezobrazuje žádné logo ani informace o autorských právech.  
  
    - **podrobné:** Zobrazí podrobné informace o režimu.  
  
    > [!NOTE]
    > Pokud potřebujete seznam možností při spuštění nástroje, zadejte **LocBaml.exe** a stiskněte klávesu ENTER.  
  
<a name="parse_dll"></a>
## <a name="use-locbaml-to-parse-a-file"></a>Analýza souboru pomocí LocBamlu  
 Nyní, když jste vytvořili nástroj LocBaml, jste připraveni jej použít k analýzě HelloApp.resources.dll extrahovat textový obsah, který bude lokalizován.  
  
1. Zkopírujte soubor LocBaml.exe do složky bin\debug aplikace, kde bylo vytvořeno sestavení hlavní aplikace.  
  
2. Chcete-li analyzovat soubor satelitního sestavení a uložit výstup jako soubor .csv, použijte následující příkaz:  
  
     **LocBaml.exe /analyzovat HelloApp.resources.dll /out:Hello.csv**  
  
    > [!NOTE]
    > Pokud vstupní soubor HelloApp.resources.dll není ve stejném adresáři jako LocBaml.exe přesunout jeden ze souborů tak, aby oba soubory jsou ve stejném adresáři.  
  
3. Při spuštění LocBaml analyzovat soubory, výstup se skládá ze sedmi polí oddělených čárkami (.csv soubory) nebo karty (.txt soubory). Následující text ukazuje analyzovaný soubor .csv pro soubor HelloApp.resources.dll:

   | |
   |-|
   |HelloApp.g.en-US.resources:window1.baml,Stack1:System.Windows.Controls.StackPanel.$Content,Ignorovat,FALSE, FALSE,,#Text1;#Text2;|
   |HelloApp.g.en-US.resources:window1.baml,Text1:System.Windows.Controls.TextBlock.$Content,None,TRUE, TRUE,,Hello World|
   |HelloApp.g.en-US.resources:window1.baml,Text2:System.Windows.Controls.TextBlock.$Content,None,TRUE, TRUE,,Goodbye World|

   Sedm polí je:  
  
   1. **Název BAML**. Název prostředku BAML s ohledem na satelitní sestavení zdrojového jazyka.  
  
   2. **Klíč zdroje**. Lokalizovaný identifikátor prostředku.  
  
   3. **Kategorie**. Typ hodnoty. Viz [Atributy lokalizace a komentáře](localization-attributes-and-comments.md).  
  
   4. **Čitelnost**. Zda lze hodnotu číst lokalizátorem. Viz [Atributy lokalizace a komentáře](localization-attributes-and-comments.md).  
  
   5. **Modifikovatelnost**. Určuje, zda lze hodnotu změnit lokalizátorem. Viz [Atributy lokalizace a komentáře](localization-attributes-and-comments.md).  
  
   6. **Komentáře**. Další popis hodnoty, která má pomoci určit, jak je hodnota lokalizována. Viz [Atributy lokalizace a komentáře](localization-attributes-and-comments.md).  
  
   7. **Hodnota**. Textová hodnota přeložit do požadované jazykové verze.  
  
   Následující tabulka ukazuje, jak se tato pole mapují na oddělené hodnoty souboru CSV:  
  
   |Název BAML|Klíč prostředku|Kategorie|Čitelnost|Modifiability|Komentáře|Hodnota|  
   |---------------|------------------|--------------|-----------------|-------------------|--------------|-----------|
   |HelloApp.g.en-US.resources:window1.baml|Stack1:System.Windows.Controls.StackPanel.$Content|Ignorovat|FALSE|FALSE||#Text1;#Text2|
   |HelloApp.g.en-US.resources:window1.baml|Text1:System.Windows.Controls.TextBlock.$Content|Žádný|TRUE|TRUE||Hello World|
   |HelloApp.g.en-US.resources:window1.baml|Text2:System.Windows.Controls.TextBlock.$Content|Žádný|TRUE|TRUE||Sbohem svět|
  
   Všimněte si, že všechny hodnoty pro **pole Komentáře** neobsahují žádné hodnoty; Pokud pole nemá hodnotu, je prázdné. Všimněte si také, že položka v prvním řádku není čitelná ani upravitelná a má jako hodnotu **Kategorie** hodnotu "Ignorovat", což znamená, že hodnota není lokalizovatelná.  
  
4. Chcete-li usnadnit zjišťování lokalizovatelných položek v analyzovaných souborech, zejména ve velkých souborech, můžete položky seřadit nebo filtrovat podle **kategorie**, **čitelnosti**a **upravitelnosti**. Můžete například odfiltrovat nečitelné a neupravitelné hodnoty.  
  
<a name="translate_loc_content"></a>
## <a name="translate-the-localizable-content"></a>Přeložit lokalizovatelný obsah  
 K překladu extrahovaného obsahu použijte libovolný nástroj, který máte k dispozici. Dobrým způsobem, jak to provést, je zapsat prostředky do souboru .csv a zobrazit je v aplikaci Microsoft Excel, takže překlad změny posledního sloupce (hodnota).  
  
<a name="merge_translations"></a>
## <a name="use-locbaml-to-generate-a-new-resourcesdll-file"></a>Použití LocBamlu ke generování nového souboru .resources.dll  
 Obsah, který byl identifikován analýzou HelloApp.resources.dll s LocBaml byl přeložen a musí být sloučeny zpět do původní aplikace. Pomocí možnosti **generate** nebo **-g** vygenerujte nový soubor .resources.dll.  
  
1. Následující syntaxe slouží ke generování nového souboru HelloApp.resources.dll. Označte jazykovou verzi jako en US (/cul:en-US).  
  
     **LocBaml.exe /generate HelloApp.resources.dll /trans:Hello.csv /out:c:\ /cul:en-US**  
  
    > [!NOTE]
    > Pokud vstupní soubor Hello.csv není ve stejném adresáři jako spustitelný soubor LocBaml.exe, přesuňte jeden ze souborů tak, aby oba soubory byly ve stejném adresáři.  
  
2. Nahraďte starý soubor HelloApp.resources.dll v adresáři C:\HelloApp\Bin\Debug\en-US\HelloApp.resources.dll nově vytvořeným souborem HelloApp.resources.dll.  
  
3. "Hello World" a "Goodbye World" by nyní měly být přeloženy do vaší aplikace.  
  
4. Chcete-li přeložit do jiné jazykové verze, použijte jazykovou verzi jazyka, do kterého překládáte. Následující příklad ukazuje, jak přeložit do francouzština-kanadská:  
  
     **LocBaml.exe /generate HelloApp.resources.dll /trans:Hellofr-CA.csv /out:c:\ /cul:fr-CA**  
  
5. Ve stejném sestavení jako sestavení hlavní aplikace vytvořte novou složku specifickou pro jazykovou verzi pro nové satelitní sestavení. Pro francouzsko-kanadské, složka by fr-CA.  
  
6. Zkopírujte generované satelitní sestavení do nové složky.  
  
7. Chcete-li otestovat nové satelitní sestavení, je třeba změnit jazykovou verzi, pod kterou bude aplikace spuštěna. Toto lze provést jedním ze dvou způsobů:  
  
    - Změňte místní nastavení operačního systému **(Spustit** &#124; **Ovládací panely** &#124; **místní a jazykové možnosti).**  
  
    - Do aplikace přidejte do App.xaml.cs následující kód:  
  
   [!code-xaml[LocBamlChangeCultureSnippets#LocBamlChangeCultureMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/CSharp/App.xaml#locbamlchangeculturemarkup)]
   [!code-csharp[LocBamlChangeCultureSnippets#LocBamlChangeCultureCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/CSharp/App.xaml.cs#locbamlchangeculturecodebehind)]
   [!code-vb[LocBamlChangeCultureSnippets#LocBamlChangeCultureCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/VisualBasic/Application.xaml.vb#locbamlchangeculturecodebehind)]  
  
<a name="Some_Tips_for_Using_LocBaml"></a>
## <a name="some-tips-for-using-locbaml"></a>Několik tipů pro použití LocBaml  
  
- Všechna závislá sestavení, která definují vlastní ovládací prvky, musí být zkopírována do místního adresáře LocBamlu nebo nainstalována do gac. To je nezbytné, protože rozhraní API lokalizace musí mít přístup k závislým sestavením při čtení binárního XAML (BAML).  
  
- Pokud je hlavní sestavení podepsáno, musí být také podepsána vygenerovaná dll prostředku, aby mohla být načtena.  
  
- Verze lokalizované dll prostředku musí být synchronizována s hlavním sestavením.  
  
<a name="Whats_Next"></a>
## <a name="whats-next"></a>Co bude dál  
 Nyní byste měli mít základní znalosti o tom, jak používat nástroj LocBaml.  Měli byste být schopni vytvořit soubor, který obsahuje UIDs. Pomocí nástroje LocBaml byste měli být schopni analyzovat soubor, abyste extrahovali lokalizovatelný obsah, a po překladu obsahu byste měli být schopni vygenerovat soubor .resources.dll, který slučuje přeložený obsah. Toto téma neobsahuje všechny možné podrobnosti, ale nyní máte znalosti potřebné k použití LocBaml pro lokalizaci aplikací.  
  
## <a name="see-also"></a>Viz také

- [Globalizace pro WPF](globalization-for-wpf.md)
- [Přehled automatického rozložení](use-automatic-layout-overview.md)
