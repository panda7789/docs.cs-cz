---
title: "Návod: Vytvoření tlačítka použitím nástroje Microsoft Expression Blend"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- buttons [WPF]
- converting [WPF], shape to button
- Expression Blend [WPF Designer]
ms.assetid: ff5037c2-bba7-4cae-8abb-6475b686c48e
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 76025da208cc0929a20c379f76106d7e101c3358
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-create-a-button-by-using-microsoft-expression-blend"></a>Návod: Vytvoření tlačítka použitím nástroje Microsoft Expression Blend
Tento názorný postup vás provede procesem vytvoření [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] přizpůsobené tlačítko pomocí Microsoft Expression Blend.  
  
> [!IMPORTANT]
>  Microsoft Expression Blend funguje tak, že generování [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pak zkompilovat nastavit, aby spustitelný program. Pokud byste místo pracovat s [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] přímo, je další návod, který vytvoří aplikace stejný jako jeden pomocí [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] s [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] místo Blend. V tématu [vytvořit tlačítko podle pomocí XAML](../../../../docs/framework/wpf/controls/walkthrough-create-a-button-by-using-xaml.md) Další informace.  
  
 Následující obrázek znázorňuje tlačítko přizpůsobené, že vytvoříte.  
  
 ![Vlastní tlačítka, který chcete vytvořit](../../../../docs/framework/wpf/controls/media/custom-button-blend-intro.jpg "custom_button_blend_Intro")  
  
## <a name="convert-a-shape-to-a-button"></a>Převést obrazce na tlačítka  
 V první části tohoto návodu můžete vytvořit vlastní vzhled tlačítko Vlastní. Uděláte to tak, nejdřív převést obdélník na tlačítko. Potom přidáte další obrazců do šablony na tlačítko vytváření složitějších vypadající tlačítko. Proč ne začínat regulární tlačítko a přizpůsobit? Vzhledem k tomu tlačítko má integrovanou funkci, která není nutné; pro vlastní tlačítka je snazší začínat obdélníku.  
  
#### <a name="to-create-a-new-project-in-expression-blend"></a>Chcete-li vytvořit nový projekt v Expression Blend  
  
1.  Spusťte Expression Blend. (Klikněte na tlačítko **spustit**, přejděte na příkaz **všechny programy**, přejděte na příkaz **Microsoft Expression**a potom klikněte na **Microsoft Expression Blend**.)  
  
2.  V případě potřeby, maximalizujte aplikace.  
  
3.  Na **soubor** nabídky, klikněte na tlačítko **nový projekt**.  
  
4.  Vyberte **standardní aplikace (.exe)**.  
  
5.  Název projektu `CustomButton` a stiskněte klávesu **OK**.  
  
 V tuto chvíli máte prázdný [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] projektu. Můžete stisknutím klávesy F5 spusťte aplikaci. Podle očekávání, aplikace se skládá z prázdné okno. Dále vytvořte zaoblený obdélník a převádět je do tlačítko.  
  
#### <a name="to-convert-a-rectangle-to-a-button"></a>Převést obdélník na tlačítka  
  
1.  **Nastavte vlastnost pozadí okna na černé:** vyberte okna, klikněte na **karta Vlastnosti**a nastavte <xref:System.Windows.Controls.Control.Background%2A> vlastnost `Black`.  
  
     ![Jak nastavit na pozadí tlačítka na černé](../../../../docs/framework/wpf/controls/media/custom-button-blend-changebackground.png "custom_button_blend_ChangeBackground")  
  
2.  **Kreslení obdélníku přibližně velikosti tlačítka v okně:** vyberte nástroj obdélník na levé straně nástroj panelu a přetáhněte rámeček na okno.  
  
     ![Postupy: kreslení obdélníku](../../../../docs/framework/wpf/controls/media/custom-button-blend-drawrect.png "custom_button_blend_DrawRect")  
  
3.  **Zaokrouhlí na rozích rámeček:** přetáhněte ovládací prvek body obdélníku nebo nastavit přímo <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> a <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> vlastnosti. Nastavení hodnot <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> a <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> až 20 číslic.  
  
     ![Postup ověření rozích obdélníku, zaokrouhlí](../../../../docs/framework/wpf/controls/media/custom-button-blend-roundcorners.png "custom_button_blend_RoundCorners")  
  
4.  **Změňte rámeček na tlačítko:** vyberte rámeček. Na **nástroje** nabídky, klikněte na tlačítko **zkontrolujte tlačítko**.  
  
     ![Jak provádět obrazce do tlačítka](../../../../docs/framework/wpf/controls/media/custom-button-blend-makebutton.png "custom_button_blend_MakeButton")  
  
5.  **Zadejte rozsah styl či šablonu:** dialogové okno, jako se zobrazí následující.  
  
     ![Dialogové okno "Vytvořit styl prostředek"](../../../../docs/framework/wpf/controls/media/custom-button-blend-makebutton2.gif "custom_button_blend_MakeButton2")  
  
     Pro **název prostředků (klíč)**, vyberte **použít u všech**.  Bude výsledný style a tlačítko šablonu použít pro všechny objekty, které jsou tlačítka. Pro **definovat v**, vyberte **aplikace**. Bude výsledný style a tlačítko šablony mají oboru v celé aplikaci. Pokud nastavíte hodnoty v těchto dvou polích, stylů tlačítek a šablonu použít pro všechny tlačítka v celé aplikaci a každé tlačítko, které vytvoříte v aplikaci se ve výchozím nastavení, použijte tuto šablonu.  
  
## <a name="edit-the-button-template"></a>Úprava šablony tlačítko  
 Nyní máte obdélníku, která byla změněna na tlačítko. V této části můžete šablonu na tlačítko změnit a přizpůsobit, jak vypadá.  
  
#### <a name="to-edit-the-button-template-to-change-the-button-appearance"></a>Chcete-li upravit šablonu tlačítko změnit vzhled tlačítka  
  
1.  **Přejděte do zobrazení šablony:** k dalšímu přizpůsobení vzhledu naše tlačítka, musíme šablonu tlačítko Upravit. Tato šablona byla vytvořena, když jsme převést obdélník na tlačítko. Tlačítko šablony upravit, klikněte pravým tlačítkem na tlačítko a vyberte **upravit řízení částí (šablony)** a potom **upravit šablonu**.  
  
     ![Úprava šablony](../../../../docs/framework/wpf/controls/media/custom-button-blend-edittemplate.jpg "custom_button_blend_EditTemplate")  
  
     V editoru šablony, Všimněte si, že je tlačítko teď rozdělené na <xref:System.Windows.Shapes.Rectangle> a <xref:System.Windows.Controls.ContentPresenter>. <xref:System.Windows.Controls.ContentPresenter> Je použito pro zobrazení obsahu v rámci tlačítko (například řetězec "Button"). Obě rámeček a <xref:System.Windows.Controls.ContentPresenter> jsou nastíněny uvnitř <xref:System.Windows.Controls.Grid>.  
  
     ![Součásti v prezentaci obdélníku](../../../../docs/framework/wpf/controls/media/custom-button-blend-templatepanel.png "custom_button_blend_TemplatePanel")  
  
2.  **Změna názvů součásti šablony:** klikněte pravým tlačítkem na obdélníku v inventáři šablony, změny <xref:System.Windows.Shapes.Rectangle> název z "[obdélník]" pro "outerRectangle" a změňte "[ContentPresenter]" na "myContentPresenter".  
  
     ![Postup přejmenování komponenty šablonu](../../../../docs/framework/wpf/controls/media/custom-button-blend-renamecomponents.png "custom_button_blend_RenameComponents")  
  
3.  **Příkaz ALTER rámeček tak, aby se prázdný uvnitř (např. prstenec):** vyberte **outerRectangle** a nastavte <xref:System.Windows.Shapes.Shape.Fill%2A> na hodnotu "Průhledný" a <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> 5.  
  
     ![Postup vyprázdnění obdélníku](../../../../docs/framework/wpf/controls/media/custom-button-blend-changerectproperties.png "custom_button_blend_ChangeRectProperties")  
  
     Nastavte <xref:System.Windows.Shapes.Shape.Stroke%2A> k barva jakýmikoliv šablona bude. K tomu, klikněte na malé bílé políčko vedle možnosti **tahu**, vyberte **CustomExpression**a v dialogovém okně zadejte "{TemplateBinding pozadí}".  
  
     ![Jak nastavit použití barvu šablony](../../../../docs/framework/wpf/controls/media/custom-button-blend-templatestroke.png "custom_button_blend_TemplateStroke")  
  
4.  **Vytvořit vnitřní obdélníku:** nyní vytvořte jiný obdélníku (název "innerRectangle") a umístěte ho symetricky uvnitř **outerRectangle** . Pro tento typ pracovní budete pravděpodobně chtít vytvořit větší tlačítka v oblasti úpravy zvětšení.  
  
    > [!NOTE]
    >  Vaše obdélníku může vypadat jinak než ten, který na obrázku (například se může mít zaokrouhlí rozích).  
  
     ![Postup vytvoření obdélníku v jiném obdélníku](../../../../docs/framework/wpf/controls/media/custom-button-blend-innerrectangleproperties.png "custom_button_blend_innerRectangleProperties")  
  
5.  **Přesunout na začátek ContentPresenter:** v tomto okamžiku je možné, že text "Button" nebudou viditelné už. Pokud je to tak, je to proto **innerRectangle** je na **myContentPresenter**. Chcete-li odstranit tento problém, přetáhněte **myContentPresenter** pod **innerRectangle**. Změna umístění obdélníků a **myContentPresenter** podobným níže.  
  
    > [!NOTE]
    >  Alternativně můžete taky umístit **myContentPresenter** nahoře pravým tlačítkem myši a stisknutím klávesy **odeslat dál**.  
  
     ![Postup přesunutí tlačítka na jiné tlačítko](../../../../docs/framework/wpf/controls/media/custom-button-blend-innerrectangle2.png "custom_button_blend_innerRectangle2")  
  
6.  **Změna vzhledu innerRectangle:** nastavit <xref:System.Windows.Shapes.Rectangle.RadiusX%2A>, <xref:System.Windows.Shapes.Rectangle.RadiusY%2A>, a <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> hodnoty až 20 číslic. In addition, nastavte <xref:System.Windows.Shapes.Shape.Fill%2A> na pozadí šablony pomocí vlastního výrazu "{TemplateBinding pozadí}") a nastavte <xref:System.Windows.Shapes.Shape.Stroke%2A> na "průhledné". Všimněte si, že nastavení <xref:System.Windows.Shapes.Shape.Fill%2A> a <xref:System.Windows.Shapes.Shape.Stroke%2A> z **innerRectangle** je opakem masky pro **outerRectangle**.  
  
     ![Jak změnit vzhled obdélníku](../../../../docs/framework/wpf/controls/media/custom-button-blend-glassrectangleproperties1.png "custom_button_blend_glassRectangleProperties1")  
  
7.  **Přidat vrstvu pohotovostní nahoře:** poslední díl přizpůsobení vzhledu tlačítka je přidat vrstvu pohotovostní nahoře. Tato vrstva pohotovostní se skládá z třetí obdélníku. Protože skla se budou vztahovat na celou tlačítko, přehledné rámeček je podobný v dimenze **outerRectangle**. Proto vytvořit rámeček pouhou kopii **outerRectangle**. Zvýrazněte **outerRectangle** a používat kombinace kláves CTRL + C a CTRL + V k vytvoření kopie. Název nové obdélníku "glassCube".  
  
8.  **V případě potřeby změnit umístění glassCube:** Pokud **glassCube** je ještě není nastavený tak, aby zahrnoval tlačítko celý, přetáhněte ji do pozice.  
  
9. **Poskytnout glassCube mírně odlišné obrazce než outerRectangle:** změna vlastností **glassCube**. Začít tak, že změna <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> a <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> vlastnosti na 10 a <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> 2.  
  
     ![Nastavení vzhledu glassCube](../../../../docs/framework/wpf/controls/media/custom-button-blend-glasscubeappearance.gif "custom_button_blend_GlassCubeAppearance")  
  
10. **Ujistěte se, glassCube vypadat pohotovostní:** nastavit <xref:System.Windows.Shapes.Shape.Fill%2A> k sklovitě vzhled pomocí lineárního přechodu, který je 75 % neprůhledných a střídá barvu prázdné a průhledný víc než 6 přibližně rovnoměrně rozmístěny intervalech. Toto je co nastavit zarážky přechodu na:  
  
    -   Přechodové zarážky 1: White s hodnotou Alpha 75 %  
  
    -   Přechodu zastavit 2: transparentní  
  
    -   Přechodové zarážky 3: White s hodnotou Alpha 75 %  
  
    -   Přechodu zastavit 4: transparentní  
  
    -   Přechodové zarážky 5: White s hodnotou Alpha 75 %  
  
    -   Přechodu zastavit 6: transparentní  
  
     Tím se vytvoří "vlnovkami" pohotovostní vzhled.  
  
     ![Obdélníku, která vypadá jako pohotovostní](../../../../docs/framework/wpf/controls/media/custom-button-blend-glassrectangleproperties2.png "custom_button_blend_glassRectangleProperties2")  
  
11. **Skrýt vrstvu pohotovostní:** teď, když se zobrazí, jak vypadá sklovitě vrstvy, přejděte do **vzhled podokně** z **panel vlastnosti** a nastavte krytí 0 % ho chcete skrýt. V části dopředu použijeme vlastnost aktivační události a události zobrazit a upravit vrstvě pohotovostní.  
  
     ![Skrytí obdélníku pohotovostní](../../../../docs/framework/wpf/controls/media/custom-button-glassrectangleproperties3.gif "custom_button_glassRectangleProperties3")  
  
## <a name="customize-the-button-behavior"></a>Přizpůsobení chování tlačítka  
 V tomto okamžiku jste upravili prezentace tlačítko úpravou její šablonu, ale tlačítko nereaguje na akce uživatele jako typický tlačítka proveďte (například změna vzhledu při myší nad, aktivace a kliknutím na tlačítko.) Následující dva postupy ukazují, jak sestavit chování takovéto do tlačítko Vlastní. Jsme budete začínat jednoduché vlastnosti aktivační události a poté přidejte aktivačních událostí a animace.  
  
#### <a name="to-set-property-triggers"></a>Chcete-li nastavit vlastnost aktivační události  
  
1.  **Vytvořit novou aktivační událost vlastnost:** s **glassCube** vybraný, klikněte na tlačítko **+ vlastnost** v **aktivační události** panel (viz obrázek, který následuje další krok). Tím se vytvoří aktivační událost vlastnost s výchozí vlastnost aktivační událost.  
  
2.  **Zkontrolujte IsMouseOver vlastnost používá aktivační události:** změnit vlastnost, která má <xref:System.Windows.UIElement.IsMouseOver%2A>. Díky tomu vlastnost aktivační událost aktivovat, pokud <xref:System.Windows.UIElement.IsMouseOver%2A> vlastnost je `true` (když uživatel odkazuje na tlačítko myši).  
  
     ![Jak nastavit aktivační události u vlastnosti](../../../../docs/framework/wpf/controls/media/custom-button-blend-ismousedoverpropertytrigger.png "custom_button_blend_IsMousedOverPropertyTrigger")  
  
3.  **IsMouseOver aktivuje krytí 100 % glassCube:** Všimněte si, že **záznam aktivační události je na** (viz předchozí obrázek). To znamená, že všechny změny do hodnoty vlastnosti **glassCube** při na záznam se stane akci, dojde při <xref:System.Windows.UIElement.IsMouseOver%2A> je `true`. Při nahrávání, změnit <xref:System.Windows.UIElement.Opacity%2A> z **glassCube** na 100 %.  
  
     ![Jak nastavit krytí tlačítko](../../../../docs/framework/wpf/controls/media/custom-button-blend-ismousedoverpropertytrigger2.gif "custom_button_blend_IsMousedOverPropertyTrigger2")  
  
     Nyní jste vytvořili první vlastnost aktivační událost. Všimněte si, že **panely aktivační události** editoru se zaznamenávají <xref:System.Windows.UIElement.Opacity%2A> se změnil na 100 %.  
  
     ![Panel "Aktivační události"](../../../../docs/framework/wpf/controls/media/custom-button-blend-propertytriggerinfo.png "custom_button_blend_PropertyTriggerInfo")  
  
     Stisknutím klávesy F5 spusťte aplikaci a přesuňte ukazatel myši nad a tlačítko Vypnout. Měli byste vidět vrstvě pohotovostní zobrazí, když jste na tlačítko myší nad a zmizí, když ukazatel opustí.  
  
4.  **Změna hodnoty obtažení IsMouseOver aktivační události:** umožňuje přidružit další akce s <xref:System.Windows.UIElement.IsMouseOver%2A> aktivační události. Zatímco záznam, přepínač Výběr z **glassCube** k **outerRectangle**. Nastavte <xref:System.Windows.Shapes.Shape.Stroke%2A> z **outerRectangle** na vlastní výraz "{DynamicResource {x: Static SystemColors.HighlightBrushKey}}". Tím se nastaví <xref:System.Windows.Shapes.Shape.Stroke%2A> k typické zvýrazněte barvu použitou tlačítka. Stisknutím klávesy F5 projevily při myší na tlačítko.  
  
     ![Postup nastavení tahu barva zvýraznění](../../../../docs/framework/wpf/controls/media/custom-button-blend-ismousedoverpropertytrigger3.png "custom_button_blend_IsMousedOverPropertyTrigger3")  
  
5.  **IsMouseOver aktivuje rozmazaně text:** umožňuje přidružit jeden další akce, aby <xref:System.Windows.UIElement.IsMouseOver%2A> vlastnost aktivační události. Zkontrolujte obsah na tlačítko zobrazí trochu rozmazaně, jakmile se zobrazí skla nad ním. K tomuto účelu použijeme rozostření <xref:System.Windows.Media.Effects.BitmapEffect> k <xref:System.Windows.Controls.ContentPresenter> (**myContentPresenter**).  
  
     ![Rozostření obsahu tlačítka](../../../../docs/framework/wpf/controls/media/custom-button-blend-propertytriggerwithbitmapeffect.png "custom_button_blend_PropertyTriggerWithBitMapEffect")  
  
    > [!NOTE]
    >  Vrátit **panel vlastnosti** zpět na co se předtím, než jste to udělali hledání <xref:System.Windows.Media.Effects.BitmapEffect>, odstraňte text z **vyhledávacího pole**.  
  
     V tuto chvíli jsme použili vlastnost aktivační událost s několika přidružené akce k vytvoření zvýraznění chování, když ukazatel myši vstoupí do a z oblasti tlačítko. Jiné chování typické pro tlačítko je zvýrazněte je zaměřen (stejně jako po klepnutí). Přidáme takové chování můžete přidat další vlastnosti aktivační události pro <xref:System.Windows.UIElement.IsFocused%2A> vlastnost.  
  
6.  **Vytvořit vlastnost aktivační událost pro IsFocused:** stejným postupem jako u <xref:System.Windows.UIElement.IsMouseOver%2A> (viz prvním krokem v této části) a vytvořit jinou vlastnost aktivační událost pro <xref:System.Windows.UIElement.IsFocused%2A> vlastnost. Při **záznam aktivační události je na**, přidejte následující akce k aktivační události:  
  
    -   **glassCube** získá <xref:System.Windows.UIElement.Opacity%2A> 100 %.  
  
    -   **outerRectangle** získá <xref:System.Windows.Shapes.Shape.Stroke%2A> vlastního výrazu hodnotu "{DynamicResource {x: Static SystemColors.HighlightBrushKey}}".  
  
 Jako poslední krok v tomto průvodci přidáme animací pro tlačítko. Aktivuje se tyto animací událostmi – konkrétně <xref:System.Windows.UIElement.MouseEnter> a <xref:System.Windows.Controls.Primitives.ButtonBase.Click> události.  
  
#### <a name="to-use-event-triggers-and-animations-to-add-interactivity"></a>Použijete k přidání interaktivity aktivačních událostí a animací  
  
1.  **Vytvoření události MouseEnter:** přidejte novou aktivační událost a vyberte <xref:System.Windows.UIElement.MouseEnter> jako událost pro použití v aktivační události.  
  
     ![Postup vytvoření události MouseEnter](../../../../docs/framework/wpf/controls/media/custom-button-blend-mouseovereventtrigger.png "custom_button_blend_MouseOverEventTrigger")  
  
2.  **Vytvoření časové osy animace:** dále přidružit časové osy animace do <xref:System.Windows.UIElement.MouseEnter> událostí.  
  
     ![Postup přidání časové osy animace do událost](../../../../docs/framework/wpf/controls/media/custom-button-blend-mouseovereventtrigger2.png "custom_button_blend_MouseOverEventTrigger2")  
  
     Po stisknutí klávesy **OK** k vytvoření nové časové osy **Panel časové osy** se zobrazí a "Časové osy je záznam na" se zobrazí na panelu návrhu. To znamená, že můžeme začít záznam změny vlastností v časové ose (postupné animaci vlastnost změny).  
  
    > [!NOTE]
    >  Budete muset změnit velikost okna nebo panelů zobrazíte zobrazení.  
  
     ![Časová osa panelu](../../../../docs/framework/wpf/controls/media/custom-button-blend-mouseovereventtrigger3.png "custom_button_blend_MouseOverEventTrigger3")  
  
3.  **Vytvořit klíčový snímek:** vytvořit animace, vyberte objekt, který chcete animace, vytvořte dva nebo více klíčových snímků na časové ose a pro tyto klíčové snímky, nastavování hodnot vlastností, které má animace promítnout mezi. Následující obrázek provede vás procesem vytvoření klíčový snímek.  
  
     ![Jak vytvořit klíčový](../../../../docs/framework/wpf/controls/media/custom-button-blend-mouseovereventtrigger4.png "custom_button_blend_MouseOverEventTrigger4")  
  
4.  **Zmenšit glassCube na tento klíčový snímek:** s druhou snímkem vybrána, zmenšení velikosti **glassCube** na 90 % jeho použití v plné velikosti **transformace velikost**.  
  
     ![Tom, jak zmenšit velikost tlačítko](../../../../docs/framework/wpf/controls/media/custom-button-blend-sizetransform.png "custom_button_blend_SizeTransform")  
  
     Stisknutím klávesy F5 spusťte aplikaci. Přesuňte ukazatel myši nad tlačítko. Všimněte si, že se zmenší pohotovostní vrstvu nad tlačítko.  
  
5.  **Vytvořte další aktivační události a přidružit jiný animace:** přidejme jeden další animace. Použijte podobným způsobem můžete použít k vytvoření předchozí animace aktivační události:  
  
    1.  Vytvořit novou aktivační událost pomocí <xref:System.Windows.Controls.Primitives.ButtonBase.Click> událostí.  
  
    2.  Přidružit nový časovou osu s <xref:System.Windows.Controls.Primitives.ButtonBase.Click> událostí.  
  
     ![Postup vytvoření nové časové osy](../../../../docs/framework/wpf/controls/media/custom-button-blend-clickeventtrigger1.png "custom_button_blend_ClickEventTrigger1")  
  
    1.  Pro tuto časovou osu vytvořte dvě klíčové snímky, u 0.0 sekund a druhý na 0,3 sekund.  
  
    2.  S klíčového snímku na 0,3 sekund zvýrazní, nastavte **úhel otočení transformace** do 360 stupňů.  
  
     ![Postup vytvoření rotační transformace](../../../../docs/framework/wpf/controls/media/custom-button-blend-rotatetransform.gif "custom_button_blend_RotateTransform")  
  
    1.  Stisknutím klávesy F5 spusťte aplikaci. Klikněte na tlačítko. Všimněte si, že pohotovostní vrstvy otáčí kolem.  
  
## <a name="conclusion"></a>Závěr  
 Když jste dokončili vlastní tlačítko. Provedli jste pomocí tlačítka šablony, které bylo použito pro všechny tlačítka v aplikaci. Pokud necháte režimu úprav šablony (viz následující obrázek) a vytvořit více tlačítek, uvidíte, že jejich vzhled a chování jako vlastní tlačítko a nikoli jako výchozího tlačítka.  
  
 ![Tlačítko Vlastní šablony](../../../../docs/framework/wpf/controls/media/custom-button-blend-scopeup.gif "custom_button_blend_ScopeUp")  
  
 ![Více tlačítek, který stejnou šablonu využít](../../../../docs/framework/wpf/controls/media/custom-button-blend-createmultiplebuttons.png "custom_button_blend_CreateMultipleButtons")  
  
 Stisknutím klávesy F5 spusťte aplikaci. Klikněte na tlačítka a Všimněte si, jak spolu se chovají stejně.  
  
 Mějte na paměti, zatímco byly přizpůsobení šablony, abyste nastavili <xref:System.Windows.Shapes.Shape.Fill%2A> vlastnost **innerRectangle** a <xref:System.Windows.Shapes.Shape.Stroke%2A> vlastnost **outerRectangle** na pozadí šablony ({ TemplateBinding pozadí}). Z toho důvodu při nastavení barvy pozadí jednotlivých tlačítek na pozadí, které nastavíte, se použije pro tyto příslušné vlastnosti. Zkuste nyní změnit pozadí. Na následujícím obrázku se používají různé přechody. Proto sice užitečná pro celkovou vlastní ovládací prvky, jako tlačítko šablonu ovládacích prvků pomocí šablony můžete dál upravit tak, aby lišit od sebe navzájem.  
  
 ![Tlačítka pomocí stejné šablony, která vypadají diferent](../../../../docs/framework/wpf/controls/media/custom-button-blend-blendconclusion.jpg "custom_button_blend_BlendConclusion")  
  
 Na závěr právě přizpůsobení šablony tlačítko jste se naučili postup proveďte v Microsoft Expression Blend následující:  
  
-   Přizpůsobení vzhledu ovládacího prvku.  
  
-   Nastavte vlastnost aktivační události. Vlastnost aktivační události jsou velmi užitečná, protože je možné použít u většiny objektů, ne jenom ovládací prvky.  
  
-   Nastavit aktivačních událostí. Aktivační události jsou velmi užitečná, protože je možné použít u většiny objektů, ne jenom ovládací prvky.  
  
-   Vytvořte animace.  
  
-   Různé: vytvoření přechodu, přidejte BitmapEffects, použijte transformací a nastavit základní vlastnosti objektů.  
  
## <a name="see-also"></a>Viz také  
 [Vytvoření tlačítka pomocí XAML](../../../../docs/framework/wpf/controls/walkthrough-create-a-button-by-using-xaml.md)  
 [Styly a šablony](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [Přehled animace](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Přehled malování plnými barvami a přechody](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)  
 [Přehled efektů bitmap](../../../../docs/framework/wpf/graphics-multimedia/bitmap-effects-overview.md)
