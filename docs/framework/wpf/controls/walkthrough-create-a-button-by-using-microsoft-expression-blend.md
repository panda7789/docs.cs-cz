---
title: 'Návod: Vytvoření tlačítka pomocí nástroje Microsoft Expression Blend'
ms.date: 03/30/2017
helpviewer_keywords:
- buttons [WPF]
- converting [WPF], shape to button
- Expression Blend [WPF Designer]
ms.assetid: ff5037c2-bba7-4cae-8abb-6475b686c48e
ms.openlocfilehash: 3cf9d133aee5a2c3d93c1a464c96fdaebcf230f3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59300458"
---
# <a name="walkthrough-create-a-button-by-using-microsoft-expression-blend"></a>Návod: Vytvoření tlačítka pomocí nástroje Microsoft Expression Blend
Tento názorný postup vás provede procesem vytvoření [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] přizpůsobené tlačítka pomocí Microsoft Expression Blend.  
  
> [!IMPORTANT]
>  Microsoft Expression Blend funguje tak, že generování [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] , který se potom zkompiluje aby spustitelný program. Pokud byste raději pracovat s [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] přímo, je další návod, který vytvoří stejnou aplikaci jako jeden pomocí [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pomocí sady Visual Studio místo Blend. Zobrazit [vytvoření tlačítka pomocí XAML pomocí](walkthrough-create-a-button-by-using-xaml.md) Další informace.  
  
 Následující obrázek znázorňuje vlastní tlačítko, které vytvoří.  
  
 ![Vlastní tlačítka, které vytvoříte](./media/custom-button-blend-intro.jpg "custom_button_blend_Intro")  
  
## <a name="convert-a-shape-to-a-button"></a>Převod tvaru na tlačítka  
 V první části tohoto průvodce můžete vytvořit vlastní vzhled na tlačítko Vlastní. Provedete to tak, je nejprve převést obdélníku tlačítka. Potom přidáte další tvary do šablony tlačítka, vytvoření složitější vzhledu tlačítka. Případně proč bezpečná není začínat běžné tlačítko a ho přizpůsobovat? Vzhledem k tomu, že tlačítko má integrované funkce, která není nutné; u vlastních tlačítek je jednodušší začínat obdélníku.  
  
#### <a name="to-create-a-new-project-in-expression-blend"></a>Chcete-li vytvořit nový projekt v aplikaci Expression Blend  
  
1. Začněte Expression Blend. (Klikněte na tlačítko **Start**, přejděte na **všechny programy**, přejděte na **Microsoft Expression**a potom klikněte na tlačítko **Microsoft Expression Blend**.)  
  
2. Maximalizujte aplikace v případě potřeby.  
  
3. Na **souboru** nabídky, klikněte na tlačítko **nový projekt**.  
  
4. Vyberte **standardní aplikace (.exe)**.  
  
5. Pojmenujte projekt `CustomButton` a stiskněte klávesu **OK**.  
  
 V tomto okamžiku můžete mít prázdnou hodnotu [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] projektu. Stisknutím klávesy F5 spusťte aplikaci. Jak byste asi očekávali, aplikace se skládá pouze prázdné okno. V dalším kroku vytvoříte zakulacený obdélník a převést na tlačítku.  
  
#### <a name="to-convert-a-rectangle-to-a-button"></a>Převést obdélník na tlačítka  
  
1. **Nastavte vlastnost okno pozadí na černou:** Vyberte okno, klikněte na tlačítko **karta Vlastnosti**a nastavte <xref:System.Windows.Controls.Control.Background%2A> vlastnost `Black`.  
  
     ![Nastavení pozadí tlačítku černá](./media/custom-button-blend-changebackground.png "custom_button_blend_ChangeBackground")  
  
2. **V okně nakreslete obdélník přibližně na velikost tlačítka:** Nástroj obdélník na panelu vlevo nástroj vyberte a přetáhněte obdélníku do okna.  
  
     ![Jak nakreslit obdélník](./media/custom-button-blend-drawrect.png "custom_button_blend_DrawRect")  
  
3. **Zaokrouhlete na rohů obdélníku:** Přetáhněte ovládací prvek body obdélníku nebo nastavena přímo <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> a <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> vlastnosti. Nastavte hodnoty <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> a <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> až 20.  
  
     ![Jak se zaokrouhlí rohů obdélníku](./media/custom-button-blend-roundcorners.png "custom_button_blend_RoundCorners")  
  
4. **Změna obdélníku tlačítka:** Vyberte pravoúhelník. Na **nástroje** nabídky, klikněte na tlačítko **vytvořit tlačítko**.  
  
     ![Jak je nechat obrazce na tlačítko](./media/custom-button-blend-makebutton.png "custom_button_blend_MakeButton")  
  
5. **Zadejte rozsah stylu nebo šablony:** Zobrazí se dialogové okno vypadat asi takto.  
  
     ![Dialogové okno "Vytvořit prostředek stylu"](./media/custom-button-blend-makebutton2.gif "custom_button_blend_MakeButton2")  
  
     Pro **název prostředku (klíč)** vyberte **použít u všech**.  To způsobí, že šablona tlačítka, které platí pro všechny objekty, které jsou tlačítka a výsledný styl. Pro **definovat v**vyberte **aplikace**. To způsobí, že výsledný styl a tlačítko šablony mají rozsah přes celou aplikaci. Při nastavení hodnoty v těchto dvou polích styl tlačítka a šablona platí pro všechna tlačítka v rámci celé aplikace a každé tlačítko, které vytvoříte v aplikaci použije ve výchozím nastavení, tato šablona.  
  
## <a name="edit-the-button-template"></a>Úprava šablony tlačítka  
 Teď máte obdélníku, který byl změněn na tlačítku. V této části budete upravovat šablony tlačítka a dále přizpůsobit, jak vypadá.  
  
#### <a name="to-edit-the-button-template-to-change-the-button-appearance"></a>K úpravě šablony tlačítka, chcete-li změnit vzhled tlačítka  
  
1. **Přejděte do zobrazení pro úpravy šablony:** Dále přizpůsobit vzhled našeho tlačítka, potřebujeme k úpravě šablony tlačítka. Tato šablona byla vytvořena, když jsme převést obdélník na tlačítku. Chcete-li upravit šablony tlačítka, klikněte pravým tlačítkem myši na tlačítko a vyberte **upravit části ovládacího prvku (šablona)** a potom **upravit šablonu**.  
  
     ![Úprava šablony](./media/custom-button-blend-edittemplate.jpg "custom_button_blend_EditTemplate")  
  
     V editoru šablon, Všimněte si, že je teď rozdělený na tlačítko <xref:System.Windows.Shapes.Rectangle> a <xref:System.Windows.Controls.ContentPresenter>. <xref:System.Windows.Controls.ContentPresenter> Slouží k předkládání obsahu v rámci tlačítka (například řetězec "Button"). Obě obdélníku a <xref:System.Windows.Controls.ContentPresenter> jsou rozloženy uvnitř <xref:System.Windows.Controls.Grid>.  
  
     ![Součásti v prezentaci obdélník](./media/custom-button-blend-templatepanel.png "custom_button_blend_TemplatePanel")  
  
2. **Změna názvů součásti šablony:** Klikněte pravým tlačítkem na obdélníku v šablony inventář, změna <xref:System.Windows.Shapes.Rectangle> název z "[obdélník]" na "outerRectangle" a změňte "[ContentPresenter]" na "myContentPresenter".  
  
     ![Přejmenování součást šablony](./media/custom-button-blend-renamecomponents.png "custom_button_blend_RenameComponents")  
  
3. **Příkaz ALTER obdélníku, tak, aby se prázdný uvnitř (např. prstencový):** Vyberte **outerRectangle** a nastavte <xref:System.Windows.Shapes.Shape.Fill%2A> na hodnotu "Transparent" a <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> na 5.  
  
     ![Jak je nechat prázdné obdélník](./media/custom-button-blend-changerectproperties.png "custom_button_blend_ChangeRectProperties")  
  
     Nastavte <xref:System.Windows.Shapes.Shape.Stroke%2A> barvu cokoli, co šablona bude. Chcete-li to provést, klikněte na bílý čtvereček vedle **Stroke**vyberte **CustomExpression**a v dialogovém okně zadejte "{TemplateBinding pozadí}".  
  
     ![Jak nastavit použití barev šablony](./media/custom-button-blend-templatestroke.png "custom_button_blend_TemplateStroke")  
  
4. **Vytvoření vnitřní obdélník:** Teď vytvořte jiný obdélník (vzpomenete "innerRectangle") a umístěte ho symetricky uvnitř **outerRectangle** . Pro tento druh pracovní bude pravděpodobně chtít zvětšit zvětšit tlačítko v oblasti úprav.  
  
    > [!NOTE]
    >  Obdélník může vypadat jinak, než je na obrázku (například ji může mají zaoblené rohy).  
  
     ![Jak vytvořit obdélníku v jiném obdélníku](./media/custom-button-blend-innerrectangleproperties.png "custom_button_blend_innerRectangleProperties")  
  
5. **Přesunete ContentPresenter do horní části:** V tomto okamžiku je možné, že text "Button" nebudou viditelné déle. Pokud je to tak, důvodem je, že **innerRectangle** je nahoře **myContentPresenter**. Chcete-li opravit, přetáhněte **myContentPresenter** níže **innerRectangle**. Změna umístění obdélníky a **myContentPresenter** k vypadat podobně jako následující.  
  
    > [!NOTE]
    >  Alternativně lze také umístit **myContentPresenter** v horní části tak, že pravým tlačítkem myši a stisknutí **odeslat vpřed**.  
  
     ![Postup přesunutí jedno tlačítko na jiné tlačítko](./media/custom-button-blend-innerrectangle2.png "custom_button_blend_innerRectangle2")  
  
6. **Změna vzhledu innerRectangle:** Nastavte <xref:System.Windows.Shapes.Rectangle.RadiusX%2A>, <xref:System.Windows.Shapes.Rectangle.RadiusY%2A>, a <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> hodnoty 20. In addition, nastavte <xref:System.Windows.Shapes.Shape.Fill%2A> na pozadí šablon pomocí vlastního výrazu "{TemplateBinding pozadí}") a nastavte <xref:System.Windows.Shapes.Shape.Stroke%2A> na "transparentní". Všimněte si, že nastavení <xref:System.Windows.Shapes.Shape.Fill%2A> a <xref:System.Windows.Shapes.Shape.Stroke%2A> z **innerRectangle** je opakem pro **outerRectangle**.  
  
     ![Jak změnit vzhled obdélník](./media/custom-button-blend-glassrectangleproperties1.png "custom_button_blend_glassRectangleProperties1")  
  
7. **Přidáte vrstvu lupy v horní části:** Přizpůsobení vzhledu tlačítka poslední část je přidání vrstvy lupy v horní části. Tato vrstva lupy se skládá z třetí obdélník. Protože skla pokryje celou tlačítko, je podobné jako u dimenze skleněného rámečku **outerRectangle**. Proto vytvořit obdélníku tím, že jednoduše zkopírovat **outerRectangle**. Zvýrazněte **outerRectangle** a vytvořit kopii pomocí kombinace kláves CTRL + C a CTRL + V. Zadejte název této nové obdélník "glassCube".  
  
8. **V případě potřeby změnit umístění glassCube:** Pokud **glassCube** je ještě není umístěný tak, aby pokrýval celou tlačítko, přetáhněte ho na místo.  
  
9. **Poskytněte glassCube obrazec trochu jinak než outerRectangle:** Změna vlastností **glassCube**. Začít tak, že změna <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> a <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> vlastnosti na 10 a <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> na 2.  
  
     ![Nastavení vzhledu glassCube](./media/custom-button-blend-glasscubeappearance.gif "custom_button_blend_GlassCubeAppearance")  
  
10. **Ujistěte se, glassCube vypadat lupy:** Nastavte <xref:System.Windows.Shapes.Shape.Fill%2A> sklovitě vzhledu pomocí lineárního přechodu, který je 75 % neprůhledných a střídá bílou barvu a Transparent více než 6 přibližně rovnoměrně rozmístěné intervalech. Toto je co mají nastavit ukončení přechodu:  
  
    -   Přechodové 1: Prázdné hodnoty alfa 75 %  
  
    -   Přechodové 2: Transparentní  
  
    -   Přechodové 3: Prázdné hodnoty alfa 75 %  
  
    -   Přechodové 4: Transparentní  
  
    -   Přechodové 5: Prázdné hodnoty alfa 75 %  
  
    -   Přechodové 6: Transparentní  
  
     Tím se vytvoří "vlnovkou" skla vzhled.  
  
     ![Obdélník, který vypadá jako skla](./media/custom-button-blend-glassrectangleproperties2.png "custom_button_blend_glassRectangleProperties2")  
  
11. **Skryjete vrstvu lupy:** Teď, když se zobrazí, jak vypadá sklovitě vrstvy, přejděte do **vzhled podokně** z **panel vlastnosti** a nastavit neprůhlednost na 0 %, abyste ji skryli. V části dopředu použijeme aktivační procedury vlastností a událostí k zobrazení a manipulaci s vrstvou lupy.  
  
     ![Tom, jak skrýt obdélník skla](./media/custom-button-glassrectangleproperties3.gif "custom_button_glassRectangleProperties3")  
  
## <a name="customize-the-button-behavior"></a>Přizpůsobení chování tlačítka  
 V tomto okamžiku jste upravili prezentace na tlačítko úpravou šablony, ale tlačítko nereaguje na akce uživatele jako typický tlačítka (například změna vzhledu po myší nad, aktivace a kliknutí.) Následující dva postupy ukazují, jak vytvářet chování obdobné do vlastní tlačítka. Vytvoříme začínat aktivační procedury vlastností pro jednoduchý a potom přidáme aktivační události a animace.  
  
#### <a name="to-set-property-triggers"></a>Chcete-li nastavit aktivační procedury vlastností  
  
1. **Vytvořte novou aktivační proceduru vlastností:** S **glassCube** vybraný, klikněte na tlačítko **+ vlastnost** v **triggery** panelu (viz obrázek, který následuje další krok). Tím se vytvoří s výchozí vlastností aktivační událost aktivační procedura vlastností.  
  
2. **Ujistěte se, IsMouseOver vlastnost používá aktivační události:** Změnit vlastnosti, která má <xref:System.Windows.UIElement.IsMouseOver%2A>. Díky tomu aktivační procedura vlastností aktivován, když <xref:System.Windows.UIElement.IsMouseOver%2A> vlastnost `true` (když uživatel odkazuje na tlačítka myši).  
  
     ![Jak nastavit aktivační událost u vlastnosti](./media/custom-button-blend-ismousedoverpropertytrigger.png "custom_button_blend_IsMousedOverPropertyTrigger")  
  
3. **Aktivační události krytí IsMouseOver 100 % glassCube:** Všimněte si, **aktivační události – nahrávání je zapnuté** (viz předchozí obrázek). To znamená, že všechny změny hodnot vlastností **glassCube** při nahrávání je zapnuté se stane, že probíhá při akci <xref:System.Windows.UIElement.IsMouseOver%2A> je `true`. Při nahrávání změnit <xref:System.Windows.UIElement.Opacity%2A> z **glassCube** na 100 %.  
  
     ![Jak nastavit neprůhlednost tlačítko](./media/custom-button-blend-ismousedoverpropertytrigger2.gif "custom_button_blend_IsMousedOverPropertyTrigger2")  
  
     Nyní jste vytvořili první aktivační procedura vlastností. Všimněte si, že **triggery panel** editoru je zaznamenána <xref:System.Windows.UIElement.Opacity%2A> mění na 100 %.  
  
     ![Na panelu "Triggery"](./media/custom-button-blend-propertytriggerinfo.png "custom_button_blend_PropertyTriggerInfo")  
  
     Stisknutím klávesy F5 spusťte aplikaci a přesuňte ukazatel myši nad a mimo tlačítko. Měli byste vidět vrstvě lupy se zobrazí, když jste myší nad tlačítko a zmizet, když ukazatel opustí.  
  
4. **Triggery IsMouseOver obtažení změna hodnoty:** Umožňuje přidružit jiné akce s <xref:System.Windows.UIElement.IsMouseOver%2A> aktivační události. Při nahrávání bude pokračovat, přepněte podle výběru v **glassCube** k **outerRectangle**. Nastavte <xref:System.Windows.Shapes.Shape.Stroke%2A> z **outerRectangle** vlastní výraz "{DynamicResource {x: Static SystemColors.HighlightBrushKey}}". Tím se nastaví <xref:System.Windows.Shapes.Shape.Stroke%2A> na typické zvýraznit barvy tlačítka. Stiskněte klávesu F5 a vidět její účinek, když myší na tlačítko.  
  
     ![Jak nastavit barvu zvýraznění tahu](./media/custom-button-blend-ismousedoverpropertytrigger3.png "custom_button_blend_IsMousedOverPropertyTrigger3")  
  
5. **IsMouseOver aktivuje fuzzy text:** Umožňuje přidružit jednu další akce, aby <xref:System.Windows.UIElement.IsMouseOver%2A> aktivační procedura vlastností. Zajistit pro obsah na tlačítko Zobrazit něco fuzzy při skla se zobrazí nad ním. K tomuto účelu můžete použít rozostření <xref:System.Windows.Media.Effects.BitmapEffect> k <xref:System.Windows.Controls.ContentPresenter> (**myContentPresenter**).  
  
     ![Rozostření obsah tlačítko](./media/custom-button-blend-propertytriggerwithbitmapeffect.png "custom_button_blend_PropertyTriggerWithBitMapEffect")  
  
    > [!NOTE]
    >  Se vraťte **panel vlastnosti** zpět na co správce it se předtím, než jste to udělali hledání <xref:System.Windows.Media.Effects.BitmapEffect>, vymažte text z **vyhledávacího pole**.  
  
     V tuto chvíli jsme použili aktivační procedura vlastností s několika přidružené akce vytvoření zvýraznění chování při umístění ukazatele myši přejde do a z oblasti tlačítko. Jiné chování typické pro tlačítko je zvýraznit, když má fokus (stejně jako po kliknutí). Přidáme takové chování tak, že přidáte další aktivační procedura vlastností pro <xref:System.Windows.UIElement.IsFocused%2A> vlastnost.  
  
6. **Vytvořte aktivační proceduru vlastností pro IsFocused:** Stejným postupem jako u <xref:System.Windows.UIElement.IsMouseOver%2A> (viz prvním krokem v této části), vytvořte jinou aktivační procedura vlastností pro <xref:System.Windows.UIElement.IsFocused%2A> vlastnost. Zatímco **aktivační události – nahrávání je zapnuté**, přidejte následující akce aktivační události:  
  
    -   **glassCube** získá <xref:System.Windows.UIElement.Opacity%2A> 100 %.  
  
    -   **outerRectangle** získá <xref:System.Windows.Shapes.Shape.Stroke%2A> hodnota vlastní vlastnosti "{DynamicResource {x: Static SystemColors.HighlightBrushKey}}".  
  
 Jako poslední krok v tomto podrobném návodu přidáme animace k tlačítku. Tyto animace budete se aktivuje událostmi – konkrétně <xref:System.Windows.UIElement.MouseEnter> a <xref:System.Windows.Controls.Primitives.ButtonBase.Click> události.  
  
#### <a name="to-use-event-triggers-and-animations-to-add-interactivity"></a>Chcete-li použít k přidání interaktivity aktivačních procedur událostí a animace  
  
1. **Vytvoření aktivační události MouseEnter – událost:** Přidat novou aktivační událost a vyberte <xref:System.Windows.UIElement.MouseEnter> jako událost v triggeru.  
  
     ![Vytvoření aktivační události MouseEnter](./media/custom-button-blend-mouseovereventtrigger.png "custom_button_blend_MouseOverEventTrigger")  
  
2. **Vytvořte časové osy animace:** V dalším kroku přidružte časovou osu animace k <xref:System.Windows.UIElement.MouseEnter> událostí.  
  
     ![Postup přidání časovou osu animace události](./media/custom-button-blend-mouseovereventtrigger2.png "custom_button_blend_MouseOverEventTrigger2")  
  
     Po stisknutí klávesy **OK** vytvořte nové časové osy **Panel časové osy** se zobrazí a je viditelný v panelu návrhu "Časové osy – nahrávání je zapnuté". To znamená, že můžeme začít záznam změn vlastnosti v časové ose (Animovat vlastnost změny).  
  
    > [!NOTE]
    >  Budete muset změnit velikost okna nebo panelů najdete v zobrazení.  
  
     ![Časová osa panel](./media/custom-button-blend-mouseovereventtrigger3.png "custom_button_blend_MouseOverEventTrigger3")  
  
3. **Vytvoření klíčového snímku:** Pokud chcete vytvořit animaci, vyberte objekt, který chcete animovat, vytvořte dva nebo více klíčové snímky na časové ose a pro tyto klíčové snímky, nastavit hodnoty vlastností chcete animaci lze interpolovat mezi. Na následujícím obrázku provede vás procesem vytvoření klíčového snímku.  
  
     ![Vytvoření klíčového snímku](./media/custom-button-blend-mouseovereventtrigger4.png "custom_button_blend_MouseOverEventTrigger4")  
  
4. **Zmenšit glassCube na tomto klíčového snímku:** Pomocí druhého klíčový snímek vybraný zmenšení velikosti **glassCube** 90 % pomocí jeho plnou velikost **velikost transformace**.  
  
     ![Tom, jak zmenšit velikost tlačítka](./media/custom-button-blend-sizetransform.png "custom_button_blend_SizeTransform")  
  
     Stisknutím klávesy F5 spusťte aplikaci. Přesuňte ukazatel myši nad tlačítkem. Všimněte si, že zmenšuje skla vrstvu nad tlačítko.  
  
5. **Vytvořte další aktivační události a přidružit různé animace:** Přidejme jeden další kroky animace. Použijte podobným způsobem můžete použít k vytvoření předchozí animace aktivační události:  
  
    1.  Vytvořit novou pomocí aktivační události <xref:System.Windows.Controls.Primitives.ButtonBase.Click> událostí.  
  
    2.  Přidružit nové časové osy s <xref:System.Windows.Controls.Primitives.ButtonBase.Click> událostí.  
  
     ![Jak vytvořit nové časové osy](./media/custom-button-blend-clickeventtrigger1.png "custom_button_blend_ClickEventTrigger1")  
  
    1.  Pro tato časová osa vytvořte dva klíčové snímky, zrovna 0.0 sekund a druhý na 0,3 sekund.  
  
    2.  Klíčový snímek na zvýrazněnou 0,3 sekund, nastavte **úhel otočení transformace** do 360 stupňů.  
  
     ![Postup vytvoření transformace rotace](./media/custom-button-blend-rotatetransform.gif "custom_button_blend_RotateTransform")  
  
    1.  Stisknutím klávesy F5 spusťte aplikaci. Klikněte na tlačítko. Všimněte si, že vrstvy skla přede kolem.  
  
## <a name="conclusion"></a>Závěr  
 Dokončili jste vlastní tlačítka. Provedli jste pomocí šablony tlačítka, které byly použity na všechny tlačítka v aplikaci. Pokud necháte režimu úprav šablony (viz následující obrázek) a vytvořit další tlačítka, zobrazí se, že jejich vzhled a chování jako vlastní tlačítko, nikoli jako výchozího tlačítka.  
  
 ![Šablona vlastního tlačítka](./media/custom-button-blend-scopeup.gif "custom_button_blend_ScopeUp")  
  
 ![Více tlačítek, které používají stejnou šablonu](./media/custom-button-blend-createmultiplebuttons.png "custom_button_blend_CreateMultipleButtons")  
  
 Stisknutím klávesy F5 spusťte aplikaci. Pomocí tlačítek a Všimněte si, jak všechny se chová stejně.  
  
 Mějte na paměti, že když se přizpůsobuje šablony, je nastavit <xref:System.Windows.Shapes.Shape.Fill%2A> vlastnost **innerRectangle** a <xref:System.Windows.Shapes.Shape.Stroke%2A> vlastnost **outerRectangle** na pozadí šablony ({ TemplateBinding pozadí}). Kvůli tomu když nastavíte barvu pozadí jednotlivá tlačítka na pozadí, které nastavíte, se použije pro tyto příslušné vlastnosti. Zkuste nyní změnit pozadí. Na následujícím obrázku se používají různé přechody. Proto i když šablona je užitečná pro celkové přizpůsobení ovládacích prvků jako tlačítko, ovládacích prvků pomocí šablon lze stále upravit a lišit od sebe navzájem.  
  
 ![Tlačítka s stejnou šablonu, která vypadají diferent](./media/custom-button-blend-blendconclusion.jpg "custom_button_blend_BlendConclusion")  
  
 Na závěr právě přizpůsobení šablony tlačítka jste se naučili, jak proveďte postup v aplikaci Microsoft Expression Blend:  
  
-   Přizpůsobení vzhledu ovládacího prvku.  
  
-   Nastavit aktivační procedury vlastností. Aktivační procedury vlastností jsou velmi užitečné, protože je možné u většiny objektů, ne jen ovládací prvky.  
  
-   Nastavení aktivační události. Aktivační události jsou velmi užitečné, protože je možné u většiny objektů, ne jen ovládací prvky.  
  
-   Vytváření animací.  
  
-   Různé: vytvoření přechody, přidejte BitmapEffects, použití transformací a nastavte základní vlastnosti objektů.  
  
## <a name="see-also"></a>Viz také:

- [Vytvoření tlačítka pomocí XAML](walkthrough-create-a-button-by-using-xaml.md)
- [Styly a šablony](styling-and-templating.md)
- [Přehled animace](../graphics-multimedia/animation-overview.md)
- [Přehled malování plnými barvami a přechody](../graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)
- [Přehled efektů bitmap](../graphics-multimedia/bitmap-effects-overview.md)
