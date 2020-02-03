---
title: Uspořádání ovládacích prvků pomocí zarovnávacím čárám
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], arranging with snaplines
- snaplines [Windows Forms], arranging Windows Forms controls
- SnapLine class [Windows Forms], walkthroughs
- Windows Forms controls, arranging
ms.assetid: d5c9edc7-cf30-4a97-8ebe-201d569340f8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3b88f64fca8d3f11308f1cbfde97de2e6c2f22cc
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740215"
---
# <a name="walkthrough-arrange-controls-on-windows-forms-using-snaplines"></a>Návod: uspořádání ovládacích prvků na model Windows Forms pomocí zarovnávacím čárám

Přesné umístění ovládacích prvků ve formuláři je velmi prioritní pro mnoho aplikací. Návrhář formulářů poskytuje mnoho nástrojů pro rozložení, které vám to umožní. Jedním z nejdůležitějších funkcí je <xref:System.Windows.Forms.Design.Behavior.SnapLine> funkce.

Zarovnávacím čárám vám ukáže přesně, kde můžete zarovnat ovládací prvky s dalšími ovládacími prvky. Také ukazují doporučené vzdálenosti pro okraje mezi ovládacími prvky, jak je určeno v [pokynech uživatelského rozhraní systému Windows](/windows/win32/uxguide/guidelines).

Zarovnávacím čárám usnadňuje zarovnání ovládacích prvků pro zajištění ostrých a profesionálních vzhledů a chování (vzhled a chování).

## <a name="create-the-project"></a>Vytvoření projektu

1. V aplikaci Visual Studio vytvořte projekt aplikace založený na systému Windows s názvem "SnaplineExample".

2. V Návrháři formulářů vyberte formulář.

## <a name="space-and-align-controls"></a>Mezery a zarovnání ovládacích prvků

Zarovnávacím čárám poskytuje přesný a intuitivní způsob, jak zarovnat ovládací prvky ve formuláři. Zobrazí se, když přesouváte vybraný ovládací prvek nebo ovládací prvky poblíž pozice, která by byla zarovnána s jiným ovládacím prvkem nebo sadou ovládacích prvků. Váš výběr bude "přichycen" do navrhované pozice při přesunu za ostatní ovládací prvky.

### <a name="to-arrange-controls-using-snaplines"></a>Uspořádání ovládacích prvků pomocí zarovnávacím čárám

1. Přetáhněte ovládací prvek <xref:System.Windows.Forms.Button> z **panelu nástrojů** do formuláře.

2. Přesuňte ovládací prvek <xref:System.Windows.Forms.Button> do pravého dolního rohu formuláře. Všimněte si, že zarovnávacím čárám, který se zobrazí jako ovládací prvek <xref:System.Windows.Forms.Button>, se blíží dolnímu a pravému okraji formuláře. Tyto zarovnávacím čárámy zobrazují doporučenou vzdálenost mezi ohraničením ovládacího prvku a formulářem.

3. Přesuňte ovládací prvek <xref:System.Windows.Forms.Button> kolem ohraničení formuláře a Všimněte si, kde se zobrazí zarovnávacím čárám. Až budete hotovi, přesuňte ovládací prvek <xref:System.Windows.Forms.Button> v blízkosti středu formuláře.

4. Přetáhněte jiný ovládací prvek <xref:System.Windows.Forms.Button> z **panelu nástrojů** do formuláře.

5. Přesuňte druhý ovládací prvek <xref:System.Windows.Forms.Button>, dokud není téměř na první úrovni s prvním. Všimněte si snapline, který se zobrazí na účaří textu obou tlačítek, a Všimněte si, že ovládací prvek, který přesouváte, se přichytí k pozici, která je přesně na úrovni s druhým ovládacím prvkem.

6. Přesuňte druhý ovládací prvek <xref:System.Windows.Forms.Button>, dokud není umístěný přímo nad první. Všimněte si zarovnávacím čárám, který se zobrazí podél levého a pravého okraje obou tlačítek, a Všimněte si, že ovládací prvek, který přesouváte, se přichytí k pozici, která je přesně zarovnána s druhým ovládacím prvkem.

7. Vyberte jeden z ovládacích prvků <xref:System.Windows.Forms.Button> a přesuňte ho blízko k druhému, dokud nebudou skoro dotek. Všimněte si snapline, který se mezi nimi objevuje. Tato vzdálenost je doporučená vzdálenost mezi ohraničením ovládacích prvků. Všimněte si také, že ovládací prvek, který přesouváte, se přichytí k této pozici.

8. Přetáhněte ze sady **nástrojů** do formuláře dva ovládací prvky <xref:System.Windows.Forms.Panel>.

9. Přesuňte jeden z ovládacích prvků <xref:System.Windows.Forms.Panel>, dokud není téměř na první úrovni. Všimněte si zarovnávacím čárám, který se zobrazí podél horního a dolního okraje obou ovládacích prvků, a Všimněte si, že ovládací prvek, který přesouváte, se přichytí k pozici, která je přesně na úrovni s druhým ovládacím prvkem.

## <a name="align-to-form-and-container-margins"></a>Zarovnat k okrajům formuláře a kontejneru

Zarovnávacím čárám vám umožní sjednotit ovládací prvky tak, aby byly v souladu s konzistentním způsobem.

1. Vyberte jeden z ovládacích prvků <xref:System.Windows.Forms.Button> a přesuňte ho blízko k pravému okraji formuláře, dokud se nezobrazí snapline. Vzdálenost snapline od pravého ohraničení je součtem vlastnosti <xref:System.Windows.Forms.Control.Margin%2A> ovládacího prvku a hodnot <xref:System.Windows.Forms.Control.Padding%2A> vlastností formuláře.

   > [!NOTE]
   > Pokud je vlastnost <xref:System.Windows.Forms.Control.Padding%2A> formuláře nastavená na 0, 0, 0, 0, Návrhář formulářů vytvoří vystínovou <xref:System.Windows.Forms.Control.Padding%2A> hodnotu 9, 9, 9, 9. Chcete-li toto chování přepsat, přiřaďte hodnotu jinou než 0, 0, 0, 0.

2. Rozbalením položky <xref:System.Windows.Forms.Control.Margin%2A> v okně **vlastnosti** změňte hodnotu vlastnosti <xref:System.Windows.Forms.Control.Margin%2A> ovládacího prvku <xref:System.Windows.Forms.Button> a nastavte vlastnost <xref:System.Windows.Forms.Padding.All%2A> na hodnotu 0. Podrobnosti najdete v tématu [Návod: rozvržení model Windows Forms ovládacích prvků s odsazením, okraji a vlastností AutoSize](windows-forms-controls-padding-autosize.md).

3. Přesuňte ovládací prvek <xref:System.Windows.Forms.Button> blízko k pravému okraji formuláře, dokud se nezobrazí snapline. Tato vzdálenost je teď dána hodnotou vlastnosti <xref:System.Windows.Forms.Control.Padding%2A> formuláře.

4. Přetáhněte ovládací prvek <xref:System.Windows.Forms.GroupBox> z **panelu nástrojů** do formuláře.

5. Rozbalením položky <xref:System.Windows.Forms.Control.Padding%2A> v okně **vlastnosti** změňte hodnotu vlastnosti <xref:System.Windows.Forms.Control.Padding%2A> ovládacího prvku <xref:System.Windows.Forms.GroupBox> a nastavte vlastnost <xref:System.Windows.Forms.Padding.All%2A> na hodnotu 10.

6. Přetáhněte ovládací prvek <xref:System.Windows.Forms.Button> z **panelu nástrojů** do ovládacího prvku <xref:System.Windows.Forms.GroupBox>.

7. Přesuňte ovládací prvek <xref:System.Windows.Forms.Button> blízko pravého okraje ovládacího prvku <xref:System.Windows.Forms.GroupBox>, dokud se nezobrazí snapline. Přesuňte ovládací prvek <xref:System.Windows.Forms.Button> v rámci ovládacího prvku <xref:System.Windows.Forms.GroupBox> a poznamenejte si, kde se zarovnávacím čárám zobrazí.

## <a name="align-to-grouped-controls"></a>Zarovnat ke seskupeným ovládacím prvkům

Pomocí zarovnávacím čárám můžete zarovnat seskupené ovládací prvky i ovládací prvky v rámci ovládacího prvku <xref:System.Windows.Forms.GroupBox>.

1. Vyberte dva ovládací prvky ve formuláři. Posuňte výběr kolem a poznamenejte si zarovnávacím čárám, který se zobrazí mezi vaším výběrem a dalšími ovládacími prvky.

2. Přetáhněte ovládací prvek <xref:System.Windows.Forms.GroupBox> z **panelu nástrojů** do formuláře.

3. Přetáhněte ovládací prvek <xref:System.Windows.Forms.Button> z **panelu nástrojů** do ovládacího prvku <xref:System.Windows.Forms.GroupBox>.

4. Vyberte jeden z ovládacích prvků <xref:System.Windows.Forms.Button> a přesuňte ho kolem ovládacího prvku <xref:System.Windows.Forms.GroupBox>. Všimněte si zarovnávacím čárám, který se zobrazí na okrajích ovládacího prvku <xref:System.Windows.Forms.GroupBox>. Všimněte si také zarovnávacím čárám, který se objeví na okrajích ovládacího prvku <xref:System.Windows.Forms.Button>, který je obsažený v ovládacím prvku <xref:System.Windows.Forms.GroupBox>. Ovládací prvky, které jsou podřízené ovládacímu prvku kontejneru, také podporují zarovnávacím čárám.

## <a name="use-snaplines-to-place-a-control-by-outlining-its-size"></a>Použití zarovnávacím čárám k umístění ovládacího prvku po sbalení jeho velikosti

1. Na **panelu nástrojů**klikněte na ikonu ovládacího prvku <xref:System.Windows.Forms.Button>. Nepřetáhněte ho do formuláře.

2. Přesuňte ukazatel myši nad návrhovou plochu formuláře. Všimněte si, že se ukazatel změní na vlasovou čáru s připojenou ikonou ovládacího prvku <xref:System.Windows.Forms.Button>. Všimněte si také zarovnávacím čárám, který se zobrazí pro návrh zarovnané pozice pro ovládací prvek <xref:System.Windows.Forms.Button>.

3. Klikněte a podržte tlačítko myši.

4. Přetáhněte ukazatel myši kolem formuláře. Všimněte si, že je vykreslen obrys, který označuje polohu a velikost ovládacího prvku.

5. Přetáhněte ukazatel, dokud není zarovnán k jinému ovládacímu prvku ve formuláři. Všimněte si, že k označení zarovnání se zobrazí snapline.

6. Uvolněte tlačítko myši. Ovládací prvek je vytvořen na pozici a velikosti vyznačené obrysem.

## <a name="use-snaplines-when-dragging-a-control-from-the-toolbox"></a>Použití zarovnávacím čárám při přetahování ovládacího prvku ze sady nástrojů

1. Přetáhněte ovládací prvek <xref:System.Windows.Forms.Button> z **panelu nástrojů** do formuláře, ale neuvolní tlačítko myši.

2. Přesuňte ukazatel myši nad návrhovou plochu formuláře. Všimněte si, že se ukazatel změní, aby označoval pozici, na které bude nový ovládací prvek <xref:System.Windows.Forms.Button> vytvořen.

3. Přetáhněte ukazatel myši kolem formuláře. Všimněte si zarovnávacím čárám, který se zobrazí pro návrh zarovnané pozice pro ovládací prvek <xref:System.Windows.Forms.Button>. Najde pozici, která je zarovnána s jinými ovládacími prvky.

4. Uvolněte tlačítko myši. Ovládací prvek se vytvoří na pozici označené zarovnávacím čárámem.

## <a name="resize-a-control-using-snaplines"></a>Změna velikosti ovládacího prvku pomocí zarovnávacím čárám

1. Přetáhněte ovládací prvek <xref:System.Windows.Forms.Button> z **panelu nástrojů** do formuláře.

2. Změňte velikost ovládacího prvku <xref:System.Windows.Forms.Button> tím, že zachytíte jeden z rohových úchytů pro změnu velikosti a přetažením. Podrobnosti najdete v tématu [Postup: Změna velikosti ovládacích prvků na model Windows Forms](how-to-resize-controls-on-windows-forms.md).

3. Přetáhněte úchyt pro změnu velikosti, dokud jedna z okrajů ovládacího prvku <xref:System.Windows.Forms.Button> není zarovnána s jiným ovládacím prvkem. Všimněte si, že se zobrazí snapline. Všimněte si také, že se úchyt pro změnu velikosti přitahuje na pozici určenou v snapline.

4. Změňte velikost ovládacího prvku <xref:System.Windows.Forms.Button> v různých směrech a Zarovnejte úchyt změny velikosti různým ovládacím prvkům. Všimněte si, jak se zarovnávacím čárám zobrazuje v různých orientech k označení zarovnání.

## <a name="align-a-label-to-a-controls-text"></a>Zarovnání popisku na text ovládacího prvku

1. Přetáhněte ovládací prvek <xref:System.Windows.Forms.TextBox> z **panelu nástrojů** do formuláře. Po zrušení ovládacího prvku <xref:System.Windows.Forms.TextBox> do formuláře klikněte na glyf inteligentních značek a vyberte možnost **nastavit text na TextBox1** . Podrobnosti najdete v tématu [Návod: provádění běžných úloh pomocí inteligentních značek v ovládacích prvcích model Windows Forms](performing-common-tasks-using-smart-tags-on-wf-controls.md).

2. Přetáhněte ovládací prvek <xref:System.Windows.Forms.Label> z **panelu nástrojů** do formuláře.

3. Změňte hodnotu vlastnosti <xref:System.Windows.Forms.Control.AutoSize%2A> ovládacího prvku <xref:System.Windows.Forms.Label> na `true`. Všimněte si, že ohraničení ovládacího prvku jsou upraveny tak, aby odpovídaly zobrazovanému textu.

4. Přesuňte ovládací prvek <xref:System.Windows.Forms.Label> nalevo od ovládacího prvku <xref:System.Windows.Forms.TextBox>, takže je zarovnán s dolním okrajem ovládacího prvku <xref:System.Windows.Forms.TextBox>. Všimněte si snapline, který se zobrazí podél dolních hran dvou ovládacích prvků.

5. Přesuňte ovládací prvek <xref:System.Windows.Forms.Label> mírně vzhůru, dokud není zarovnán text <xref:System.Windows.Forms.Label> a text <xref:System.Windows.Forms.TextBox>. Všimněte si, že se zobrazí různé snapline styly, které označují, kdy jsou textová pole obou ovládacích prvků zarovnána.

## <a name="use-snaplines-with-keyboard-navigation"></a>Použití zarovnávacím čárám s navigací klávesnice

1. Přetáhněte ovládací prvek <xref:System.Windows.Forms.Button> z **panelu nástrojů** do formuláře. Umístěte ho do levého horního rohu formuláře.

2. Stiskněte klávesu **Ctrl**+**šipku dolů**. Všimněte si, že ovládací prvek se přesune do prvního dostupné pozice vodorovného zarovnání dolů ve formuláři.

3. Stiskněte klávesu **Ctrl**+**šipku dolů** , dokud ovládací prvek nedosáhne spodní části formuláře. Poznamenejte si pozice, které zabírají při přesunu formuláře.

4. Stiskněte klávesu **Ctrl**+**šipku doprava**. Všimněte si, že ovládací prvek se přesune mezi formulářem na první dostupnou pozici svislého zarovnání.

5. Stiskněte klávesu **Ctrl**+**šipku vpravo** , dokud ovládací prvek nedosáhne strany formuláře. Poznamenejte si pozice, které zabírají při přesunu napříč formulářem.

6. Přesuňte ovládací prvek kolem formuláře s kombinací kláves se šipkami. Všimněte si pozic, které ovládací prvek zabírá, a zarovnávacím čárám, které jim doprovází.

7. Stisknutím klávesy **Shift**+**šipkových kláves** změňte velikost ovládacího prvku <xref:System.Windows.Forms.Button> o krok po jednom pixelu.

8. Stisknutím **kombinace kláves Ctrl**+**SHIFT**+**šipkové klávesy** změňte velikost ovládacího prvku <xref:System.Windows.Forms.Button> v přírůstcích snapline.

## <a name="selectively-disable-snaplines"></a>Selektivní zakázání zarovnávacím čárám

1. Přetáhněte ovládací prvek <xref:System.Windows.Forms.TableLayoutPanel> z **panelu nástrojů** do formuláře.

2. Dvakrát klikněte na ikonu ovládacího prvku <xref:System.Windows.Forms.Button> v **sadě nástrojů**. Všimněte si, že nový ovládací prvek tlačítko se zobrazí v první buňce ovládacího prvku <xref:System.Windows.Forms.TableLayoutPanel>.

3. Dvakrát klikněte na ikonu ovládacího prvku <xref:System.Windows.Forms.Button> na **panelu nástrojů** . Tím se v ovládacím prvku <xref:System.Windows.Forms.TableLayoutPanel> opustí jedna prázdná buňka.

4. Přetáhněte ovládací prvek <xref:System.Windows.Forms.Button> z **panelu nástrojů** do prázdné buňky ovládacího prvku <xref:System.Windows.Forms.TableLayoutPanel>. Všimněte si, že se nezobrazí žádná zarovnávacím čárám.

5. Přetáhněte ovládací prvek <xref:System.Windows.Forms.Button> z ovládacího prvku <xref:System.Windows.Forms.TableLayoutPanel> a přesuňte jej kolem ovládacího prvku <xref:System.Windows.Forms.TableLayoutPanel>. Všimněte si, že se znovu zobrazí zarovnávacím čárám.

## <a name="disable-snaplines"></a>Zakázat zarovnávacím čárám

Stiskněte klávesu **ALT** a při přesunu ovládacího prvku kolem formuláře.

Neobjeví se žádné zarovnávacím čárám a ovládací prvek se nepřichytí k žádným potenciálním polohám zarovnání.

### <a name="to-disable-snaplines-in-the-design-environment"></a>Zakázání zarovnávacím čárám v prostředí pro návrh

1. V nabídce **nástroje** otevřete dialogové okno **Možnosti** . Vyberte **Návrhář formulářů**.

2. Vyberte uzel **Obecné** . V části **Režim rozložení** změňte výběr z **zarovnávacím čárám** na **SnapToGrid**.

3. Vyberte **OK** , aby se nastavení projevilo.

4. Vyberte ovládací prvek ve formuláři a přesuňte ho kolem dalších ovládacích prvků. Všimněte si, že zarovnávacím čárám se nezobrazí.

## <a name="next-steps"></a>Další kroky

Zarovnávacím čárám nabízí intuitivní způsob zarovnání ovládacích prvků na formuláři. Mezi návrhy pro další zkoumání patří:

- Zkuste vnořit ovládací prvek <xref:System.Windows.Forms.GroupBox> v rámci jiného ovládacího prvku <xref:System.Windows.Forms.GroupBox>. Umístěte ovládací prvek <xref:System.Windows.Forms.Button> v rámci podřízeného ovládacího prvku <xref:System.Windows.Forms.GroupBox> a druhý v rámci nadřazeného ovládacího prvku <xref:System.Windows.Forms.GroupBox>. Přesuňte <xref:System.Windows.Forms.Button> ovládací prvky, abyste viděli, jak zarovnávacím čárám hranice mezi kontejnery.

- Vytvoření sloupce <xref:System.Windows.Forms.TextBox> ovládacích prvků a odpovídajícího sloupce <xref:System.Windows.Forms.Label> ovládacích prvků. Nastavte hodnotu vlastnosti <xref:System.Windows.Forms.Control.AutoSize%2A> <xref:System.Windows.Forms.Label> Controls na `true`. Použijte zarovnávacím čárám k přesunutí ovládacích prvků <xref:System.Windows.Forms.Label> tak, aby byl zobrazený text zarovnán s textem v ovládacích prvcích <xref:System.Windows.Forms.TextBox>.

## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.Design.Behavior.SnapLine>
- [Postupy: Uspořádání ovládacích prvků na formuláři Windows Forms s použitím ovládacího prvku FlowLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [Postupy: Uspořádání ovládacích prvků na Windows Forms s použitím ovládacího prvku TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [Návod: Rozvrhování ovládacích prvků Windows Forms s odsazením, okraji a s vlastností AutoSize](windows-forms-controls-padding-autosize.md)
