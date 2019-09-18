---
title: 'Návod: Vytvoření tlačítka použitím nástroje Microsoft Expression Blend'
ms.date: 03/30/2017
helpviewer_keywords:
- buttons [WPF]
- converting [WPF], shape to button
- Expression Blend [WPF Designer]
ms.assetid: ff5037c2-bba7-4cae-8abb-6475b686c48e
ms.openlocfilehash: 497cd520731d9a0c96ed2b7cb35fa9f53ba25245
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053468"
---
# <a name="walkthrough-create-a-button-by-using-microsoft-expression-blend"></a>Návod: Vytvoření tlačítka použitím nástroje Microsoft Expression Blend

Tento názorný postup vás provede procesem vytvoření [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] přizpůsobeného tlačítka pomocí nástroje Microsoft Expression Blend.

> [!IMPORTANT]
> Microsoft Expression Blend funguje tak, [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] že generuje, který je poté zkompilován, aby byl spustitelný program. Pokud místo toho chcete pracovat [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] přímo, je k dispozici jiný návod, který vytvoří stejnou aplikaci jako tuto pomocí [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] sady Visual Studio, nikoli Blend. Další informace najdete v tématu [Vytvoření tlačítka pomocí XAML](walkthrough-create-a-button-by-using-xaml.md) .

Následující ilustrace znázorňuje přizpůsobené tlačítko, které vytvoříte.

![Přizpůsobené tlačítko, které vytvoříte](./media/custom-button-blend-intro.jpg)

## <a name="convert-a-shape-to-a-button"></a>Převedení tvaru na tlačítko

V první části tohoto návodu vytvoříte vlastní pohled na vlastní tlačítko. Chcete-li to provést, nejprve převeďte obdélník na tlačítko. Pak přidáte další tvary do šablony tlačítka a vytvoříte složitější tlačítko pro vyhledávání. Proč nezačít s běžným tlačítkem a přizpůsobit ho? Vzhledem k tomu, že tlačítko má vestavěnou funkci, kterou nepotřebujete; pro vlastní tlačítka je snazší začít s obdélníkem.

### <a name="to-create-a-new-project-in-expression-blend"></a>Vytvoření nového projektu v Blendu výrazu

1. Spusťte Blend výrazu. (Klikněte na tlačítko **Start**, přejděte na položku **všechny programy**, na položku **Microsoft Expression**a potom klikněte na položku **Microsoft Expression Blend**.)

2. V případě potřeby Maximalizujte aplikaci.

3. V nabídce **soubor** klikněte na příkaz **Nový projekt**.

4. Vyberte **standardní aplikaci (. exe)** .

5. Pojmenujte `CustomButton` projekt a stiskněte **OK**.

V tomto okamžiku máte prázdný [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] projekt. Aplikaci můžete spustit stisknutím klávesy F5. Jak budete chtít očekávat, aplikace se skládá pouze z prázdného okna. V dalším kroku vytvoříte zaoblený obdélník a převedete ho na tlačítko.

### <a name="to-convert-a-rectangle-to-a-button"></a>Převod obdélníku na tlačítko

1. **Nastavte vlastnost pozadí okna na černou:** Vyberte okno, klikněte na **kartu vlastnosti**a nastavte <xref:System.Windows.Controls.Control.Background%2A> vlastnost na `Black`hodnotu.

    ![Nastavení pozadí tlačítka na černou](./media/custom-button-blend-changebackground.png)

2. **Nakreslete obdélník přibližně na velikost tlačítka v okně:** Na panelu nástrojů na levé straně vyberte nástroj obdélník a přetáhněte ho do okna.

    ![Vykreslení obdélníku](./media/custom-button-blend-drawrect.png)

3. **Vyzaoblení rohů obdélníku:** Buď přetáhněte ovládací body obdélníku, nebo přímo nastavte <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> vlastnosti a. <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> Nastavte hodnoty <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> a <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> na 20.

    ![Postup vytvoření rohů obdélníkového zaoblení](./media/custom-button-blend-roundcorners.png)

4. **Změňte obdélník na tlačítko:** Vyberte obdélník. V nabídce **nástroje** klikněte na tlačítko **vytvořit**.

    ![Jak vytvořit tvar v tlačítku](./media/custom-button-blend-makebutton.png)

5. **Zadejte rozsah stylu nebo šablony:** Zobrazí se dialogové okno podobné následujícímu.

    ![Dialogové okno vytvořit prostředek stylu](./media/custom-button-blend-makebutton2.gif)

    Jako **název prostředku (klíč)** vyberte **použít u všech**.  Tím se výsledná šablona stylu a tlačítka použije na všechny objekty, které jsou tlačítky. **V nástroji definovat v**vyberte **aplikace**. Výsledkem bude, že výsledná šablona stylu a tlačítka bude mít rozsah pro celou aplikaci. Když nastavíte hodnoty v těchto dvou polích, styl tlačítka a šablona platí pro všechna tlačítka v celé aplikaci a jakékoli tlačítko, které vytvoříte v aplikaci, ve výchozím nastavení použije tuto šablonu.

## <a name="edit-the-button-template"></a>Úprava šablony tlačítka

Nyní máte obdélník, který byl změněn na tlačítko. V této části upravíte šablonu tlačítka a dále upravíte, jak vypadá.

### <a name="to-edit-the-button-template-to-change-the-button-appearance"></a>Úprava šablony tlačítka pro změnu vzhledu tlačítka

1. **Přejít do zobrazení upravit šablonu:** Abychom mohli dál přizpůsobit vzhled našeho tlačítka, musíme upravit šablonu tlačítka. Tato šablona byla vytvořena při převedení obdélníku na tlačítko. Chcete-li upravit šablonu tlačítka, klikněte pravým tlačítkem myši na tlačítko a vyberte možnost **Upravit části ovládacího prvku (šablona)** a pak **upravte šablonu**.

    ![Úprava šablony](./media/custom-button-blend-edittemplate.jpg)

    V editoru šablon si všimněte, že tlačítko je nyní rozděleno do <xref:System.Windows.Shapes.Rectangle> <xref:System.Windows.Controls.ContentPresenter>a. <xref:System.Windows.Controls.ContentPresenter> Slouží k prezentaci obsahu v rámci tlačítka (například řetězec "tlačítko"). Obdélník i <xref:System.Windows.Controls.ContentPresenter> je rozložen v <xref:System.Windows.Controls.Grid>rámci.

    ![Komponenty v prezentaci obdélníku](./media/custom-button-blend-templatepanel.png)

2. **Změňte názvy součástí šablony:** Pravým tlačítkem myši klikněte na obdélník v inventáři šablon, <xref:System.Windows.Shapes.Rectangle> změňte název z "[Rectangle]" na "outerRectangle" a změňte "[ContentPresenter]" na "myContentPresenter".

    ![Postup přejmenování součásti šablony](./media/custom-button-blend-renamecomponents.png)

3. **Změňte obdélník tak, aby byl prázdný uvnitř (jako prstenec):** Vyberte **outerRectangle** a nastavte <xref:System.Windows.Shapes.Shape.Fill%2A> na "transparentní" a <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> na 5.

    ![Jak nastavit obdélník jako prázdný](./media/custom-button-blend-changerectproperties.png)

    Pak nastavte <xref:System.Windows.Shapes.Shape.Stroke%2A> na barvu bez ohledu na to, která šablona bude. Provedete to tak, že kliknete na malé bílé pole vedle možnosti **vytáhnout**, vyberete **CustomExpression**a v dialogovém okně zadáte "{TemplateBinding Background}".

    ![Nastavení použití barvy šablony](./media/custom-button-blend-templatestroke.png)

4. **Vytvořit vnitřní obdélník:** Nyní vytvořte další obdélník (pojmenujte ho "innerRectangle") a umístěte ho symetricky na uvnitř **outerRectangle** . Pro tento druh práce budete pravděpodobně chtít zvětšit tlačítko, aby bylo tlačítko větší v oblasti úprav.

    > [!NOTE]
    > Váš obdélník může vypadat jinak než na obrázku (například může mít zaoblené rohy).

    ![Postup vytvoření obdélníku uvnitř jiného obdélníku](./media/custom-button-blend-innerrectangleproperties.png)

5. **Přesunout ContentPresenter nahoru:** V tomto okamžiku je možné, že text "tlačítko" nebude vidět déle. Pokud je to tak, je to proto, že **innerRectangle** je nad **myContentPresenter**. Pokud to chcete opravit, přetáhněte **myContentPresenter** pod **innerRectangle**. Přesuňte obdélníky a **myContentPresenter** tak, aby vypadaly podobně jako v následujícím příkladu.

    > [!NOTE]
    > Alternativně můžete také umístit **myContentPresenter** nahoru tak, že na něj kliknete pravým tlačítkem myši a stisknete **Odeslat dál**.

    ![Přesunutí jednoho tlačítka nad jiným tlačítkem](./media/custom-button-blend-innerrectangle2.png)

6. **Změňte vzhled innerRectangle:** Nastavte hodnoty <xref:System.Windows.Shapes.Rectangle.RadiusX%2A>, <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> a<xref:System.Windows.Shapes.Shape.StrokeThickness%2A> na 20. Kromě toho nastavte <xref:System.Windows.Shapes.Shape.Fill%2A> na pozadí šablony pomocí vlastního výrazu "{TemplateBinding Background}") a nastavte <xref:System.Windows.Shapes.Shape.Stroke%2A> na "Transparent". Všimněte si, že nastavení pro <xref:System.Windows.Shapes.Shape.Fill%2A> a <xref:System.Windows.Shapes.Shape.Stroke%2A> z **innerRectangle** jsou opakem těch pro **outerRectangle**.

    ![Změna vzhledu obdélníku](./media/custom-button-blend-glassrectangleproperties1.png)

7. **Přidat skleněnou vrstvu nahoru:** Poslední část přizpůsobení vzhledu tlačítka je přidat skleněnou vrstvu nahoru. Tato skleněná vrstva se skládá z třetího obdélníku. Vzhledem k tomu, že se skleněný rámeček bude pokrývat celé tlačítko, je skleněný obdélník podobný jako v rozměrech **outerRectangle**. Proto vytvořte obdélník pouhým vytvořením kopie **outerRectangle**. Zvýrazněte **outerRectangle** a vytvořte kopii pomocí kombinace kláves CTRL + C a CTRL + V. Pojmenujte tento nový obdélník "glassCube".

8. **V případě potřeby změňte umístění glassCube:** Pokud **glassCube** ještě není umístěné, takže pokrývá celé tlačítko, přetáhněte ho na pozici.

9. **Poskytněte glassCube trochu odlišný tvar než outerRectangle:** Změňte vlastnosti **glassCube**. Začněte tím, že změníte <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> vlastnosti <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> a vlastností na 10 a na 2.

    ![Nastavení vzhledu pro glassCube](./media/custom-button-blend-glasscubeappearance.gif)

10. **Nastavit glassCube jako skleněný vzhled:** <xref:System.Windows.Shapes.Shape.Fill%2A> Nastavte na skleněnou prohledáním pomocí lineárního přechodu, který je 75% neprůhledný a střídavě mezi barvou bílé a transparentní v 6 přibližně rovnoměrně rozmístěné intervaly. Toto je postup nastavení zastavení přechodu na:

    - Zastavení přechodu 1: Bílá s hodnotou Alpha 75%

    - Zastavení přechodu 2: Transparentní

    - Přechodová zastávka 3: Bílá s hodnotou Alpha 75%

    - Zastavení přechodu 4: Transparentní

    - Zastavení přechodu 5: Bílá s hodnotou Alpha 75%

    - Zastavení přechodu 6: Transparentní

    Tím se vytvoří skleněný vzhled "vlnité".

    ![Obdélník, který vypadá jako skleněný](./media/custom-button-blend-glassrectangleproperties2.png)

11. **Skrýt skleněnou vrstvu:** Teď, když vidíte, jak vypadá skleněná vrstva, přejděte do **podokna vzhled** na **panelu Vlastnosti** a nastavte neprůhlednost na 0%, aby ji bylo možné skrýt. V částech dopředu použijeme triggery vlastností a události k zobrazení a manipulaci se skleněnou vrstvou.

    ![Jak skrýt skleněný obdélník](./media/custom-button-glassrectangleproperties3.gif)

## <a name="customize-the-button-behavior"></a>Přizpůsobení chování tlačítka

V tuto chvíli jste přizpůsobili prezentaci tlačítka úpravou šablony, ale toto tlačítko nereaguje na akce uživatele jako na typických tlačítkách (například změna vzhledu při přetažení myší, přijímání fokusu a kliknutí). Následující dva postupy ukazují, jak tyto chování sestavovat jako vlastní tlačítko. Začneme s jednoduchými triggery vlastností a potom přidáte triggery událostí a animace.

### <a name="to-set-property-triggers"></a>Nastavení triggerů vlastností

1. **Vytvořit novou aktivační událost vlastnosti:** Když vyberete **glassCube** , klikněte na **+ vlastnost** na panelu **aktivační události** (podívejte se na obrázek, který následuje po dalším kroku). Tím se vytvoří aktivační událost vlastnosti s výchozí triggerovou vlastností.

2. **IsMouseOver vlastnost, kterou používá aktivační událost:** Změňte vlastnost na <xref:System.Windows.UIElement.IsMouseOver%2A>. Tím se aktivuje aktivační událost vlastnosti, <xref:System.Windows.UIElement.IsMouseOver%2A> když je `true` vlastnost (když uživatel odkazuje na tlačítko pomocí myši).

    ![Nastavení triggeru u vlastnosti](./media/custom-button-blend-ismousedoverpropertytrigger.png)

3. **IsMouseOver aktivuje neprůhlednost 100% pro glassCube:** Všimněte si, že **je zapnutý záznam triggeru** (viz předchozí obrázek). To znamená, že všechny změny, které provedete v hodnotách vlastností **glassCube** při nahrávání, se změní na akci, ke <xref:System.Windows.UIElement.IsMouseOver%2A> které `true`dojde, když je. Při nahrávání změňte <xref:System.Windows.UIElement.Opacity%2A> **glassCube** na 100%.

    ![Nastavení neprůhlednosti tlačítka](./media/custom-button-blend-ismousedoverpropertytrigger2.gif)

    Nyní jste vytvořili svou první aktivační událost vlastnosti. Všimněte si, že **panel aktivačních událostí** editoru zaznamenal <xref:System.Windows.UIElement.Opacity%2A> změny, které se změnily na 100%.

    ![Panel triggery](./media/custom-button-blend-propertytriggerinfo.png)

    Stiskněte klávesu F5 ke spuštění aplikace a přesunutí ukazatele myši nad a za tlačítko. Měla by se zobrazit skleněná vrstva při přesunutí ukazatele myši na tlačítko a zmizí, když ukazatel opustí.

4. **IsMouseOver aktivuje změnu hodnoty tahu:** Pojďme k <xref:System.Windows.UIElement.IsMouseOver%2A> triggeru přidružit nějaké další akce. I když pokračujete v nahrávání, přepněte svůj výběr z **glassCube** na **outerRectangle**. Pak nastavte <xref:System.Windows.Shapes.Shape.Stroke%2A> **outerRectangle** na vlastní výraz "{DynamicResource {x:static SystemColors. HighlightBrushKey}}". To nastaví <xref:System.Windows.Shapes.Shape.Stroke%2A> na typickou barvu zvýraznění používanou tlačítky. Stisknutím klávesy F5 zobrazíte efekt při pohybu myši nad tlačítkem.

    ![Nastavení tahu na barvu zvýraznění](./media/custom-button-blend-ismousedoverpropertytrigger3.png)

5. **IsMouseOver aktivuje rozmazaný text:** Pojďme k <xref:System.Windows.UIElement.IsMouseOver%2A> triggeru vlastnosti přidružit ještě jednu akci. Nastavit obsah tlačítka jako rozmazaný, pokud se na něm zobrazuje sklo. K tomu můžete použít rozostření <xref:System.Windows.Media.Effects.BitmapEffect> <xref:System.Windows.Controls.ContentPresenter> na (**myContentPresenter**).

    ![Postup rozostření obsahu tlačítka](./media/custom-button-blend-propertytriggerwithbitmapeffect.png)

    > [!NOTE]
    > Chcete-li vrátit **panel vlastnosti** zpět na to <xref:System.Windows.Media.Effects.BitmapEffect>, co bylo dříve předtím hledání, vymažte text z **vyhledávacího pole**.

    V tuto chvíli jsme použili aktivační událost vlastnosti s několika přidruženými akcemi k vytvoření zvýraznění chování, když ukazatel myši přejde do oblasti tlačítka a opustí ho. Dalším typickým chováním tlačítka je zvýraznit, když má fokus (jako po kliknutí). Takové chování můžeme přidat přidáním další triggeru vlastnosti pro <xref:System.Windows.UIElement.IsFocused%2A> vlastnost.

6. **Aktivační událost vytvoření vlastnosti pro:** Použijte stejný postup jako u pro <xref:System.Windows.UIElement.IsMouseOver%2A> (viz první krok v této části), vytvořte další aktivační proceduru vlastnosti <xref:System.Windows.UIElement.IsFocused%2A> pro vlastnost. I když **je nahrávání aktivační události zapnuté**, přidejte k triggeru následující akce:

    - **glassCube** získá <xref:System.Windows.UIElement.Opacity%2A> 100%.

    - **outerRectangle** získá <xref:System.Windows.Shapes.Shape.Stroke%2A> vlastní hodnotu výrazu {DynamicResource {x:static SystemColors. HighlightBrushKey}}.

V posledním kroku tohoto návodu přidáme k tlačítku animace. Tyto animace budou aktivovány událostmi, konkrétně <xref:System.Windows.UIElement.MouseEnter> události a. <xref:System.Windows.Controls.Primitives.ButtonBase.Click>

### <a name="to-use-event-triggers-and-animations-to-add-interactivity"></a>Přidání interaktivity pomocí aktivačních událostí a animací

1. **Vytvoření triggeru události MouseEnter:** Přidejte novou aktivační proceduru události a <xref:System.Windows.UIElement.MouseEnter> vyberte jako událost, která má být použita v aktivační události.

     ![Postup vytvoření triggeru události MouseEnter](./media/custom-button-blend-mouseovereventtrigger.png)

2. **Vytvořit časovou osu animace:** Pak přidružte časovou osu animace k <xref:System.Windows.UIElement.MouseEnter> události.

    ![Postup přidání časové osy animace k události](./media/custom-button-blend-mouseovereventtrigger2.png)

    Po stisknutí tlačítka **OK** k vytvoření nové časové osy se zobrazí **panel Časová** osa a na panelu návrh se zobrazí "nahrávání na časovou osu". To znamená, že můžeme začít nahrávat změny vlastností na časové ose (změny vlastností animovat).

    > [!NOTE]
    > Možná budete muset změnit velikost okna nebo panelů, aby se zobrazila obrazovka.

    ![Panel Časová osa](./media/custom-button-blend-mouseovereventtrigger3.png)

3. **Vytvoření klíčového snímku:** Chcete-li vytvořit animaci, vyberte objekt, který chcete animovat, vytvořte dva nebo více klíčových snímků na časové ose a pro tyto klíčové snímky nastavte hodnoty vlastností, které má animace interpolovat. Následující obrázek vás provede vytvořením klíčového snímku.

    ![Postup vytvoření klíčového snímku](./media/custom-button-blend-mouseovereventtrigger4.png)

4. **Zmenšit glassCube v tomto klíčovém snímku:** Když vyberete druhý klíčový snímek, zmenšete velikost **glassCube** na 90% jeho plné velikosti s použitím **transformace Size**.

    ![Zmenšení velikosti tlačítka](./media/custom-button-blend-sizetransform.png)

    Stisknutím klávesy F5 spusťte aplikaci. Přesuňte ukazatel myši nad tlačítko. Všimněte si, že se skleněná vrstva zmenší nad tlačítko.

5. **Vytvořte další aktivační proceduru události a přidružte k ní jinou animaci:** Pojďme přidat ještě jednu animaci. Použijte podobný postup k tomu, co jste použili k vytvoření předchozí animace triggeru událostí:

    1. Pomocí <xref:System.Windows.Controls.Primitives.ButtonBase.Click> události vytvořte novou aktivační proceduru události.

    2. Přidružit k <xref:System.Windows.Controls.Primitives.ButtonBase.Click> události novou časovou osu

        ![Jak vytvořit novou časovou osu](./media/custom-button-blend-clickeventtrigger1.png)

    3. Pro tuto časovou osu vytvořte dva klíčové snímky, jeden v 0,0 sekund a druhý v 0,3 sekund.

    4. S vybraným klíčovým snímkem v 0,3 sekundách nastavte **úhel otočení transformace** na 360 stupňů.

        ![Postup vytvoření rotace transformace](./media/custom-button-blend-rotatetransform.gif)

    5. Stisknutím klávesy F5 spusťte aplikaci. Klikněte na tlačítko. Všimněte si, že se skleněná vrstva otáčí.

## <a name="conclusion"></a>Závěr

Dokončili jste přizpůsobené tlačítko. Použili jste šablonu tlačítek, která byla použita na všechna tlačítka v aplikaci. Pokud necháte režim úprav šablony (viz následující obrázek) a vytvoříte více tlačítek, uvidíte, že vypadají a chovají se jako vlastní tlačítko, a ne jako výchozí tlačítko.

![Šablona vlastního tlačítka](./media/custom-button-blend-scopeup.gif)

![Několik tlačítek, která používají stejnou šablonu](./media/custom-button-blend-createmultiplebuttons.png)

Stisknutím klávesy F5 spusťte aplikaci. Klikněte na tlačítka a Všimněte si, jak se všechny chovají.

Mějte na paměti, že při přizpůsobování šablony jste nastavili <xref:System.Windows.Shapes.Shape.Fill%2A> vlastnost <xref:System.Windows.Shapes.Shape.Stroke%2A> innerRectangle a vlastnost **outerRectangle** na pozadí šablony ({TemplateBinding Background}). Z tohoto důvodu se při nastavení barvy pozadí jednotlivých tlačítek použije pozadí, které nastavíte pro příslušné vlastnosti. Zkuste změnit pozadí hned teď. Na následujícím obrázku jsou použity různé přechody. Proto i když je šablona užitečná pro celkové přizpůsobení ovládacích prvků jako tlačítko, ovládací prvky s šablonami lze stále upravovat, aby se vzájemně lišily.

![Tlačítka se stejnou šablonou, která vypadá diferent](./media/custom-button-blend-blendconclusion.jpg "custom_button_blend_BlendConclusion")

V závěru v rámci přizpůsobení šablony tlačítka, kterou jste zjistili, jak v nástroji Microsoft Expression Blend provést následující akce:

- Přizpůsobení vzhledu ovládacího prvku.

- Nastavte triggery vlastností. Triggery vlastností jsou velmi užitečné, protože je lze použít pro většinu objektů, nikoli pouze pro ovládací prvky.

- Nastavte triggery událostí. Triggery událostí jsou velmi užitečné, protože je lze použít pro většinu objektů, nikoli pouze pro ovládací prvky.

- Vytváření animací.

- Různé: vytváření přechodů, přidávání BitmapEffects, použití transformací a nastavení základních vlastností objektů.

## <a name="see-also"></a>Viz také:

- [Vytvoření tlačítka pomocí XAML](walkthrough-create-a-button-by-using-xaml.md)
- [Styly a šablony](styling-and-templating.md)
- [Přehled animace](../graphics-multimedia/animation-overview.md)
- [Přehled malování plnými barvami a přechody](../graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)
- [Přehled efektů bitmap](../graphics-multimedia/bitmap-effects-overview.md)
