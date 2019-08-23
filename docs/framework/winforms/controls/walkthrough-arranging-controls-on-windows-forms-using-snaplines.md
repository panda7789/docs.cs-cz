---
title: 'Návod: Uspořádání ovládacích prvků ve Windows Forms pomocí zarovnávacích čar'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], arranging with snaplines
- snaplines [Windows Forms], arranging Windows Forms controls
- SnapLine class [Windows Forms], walkthroughs
- Windows Forms controls, arranging
ms.assetid: d5c9edc7-cf30-4a97-8ebe-201d569340f8
ms.openlocfilehash: 8ac1ba6b8121aabea3c992ca5b943f231fc19ce2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950062"
---
# <a name="walkthrough-arranging-controls-on-windows-forms-using-snaplines"></a>Návod: Uspořádání ovládacích prvků ve Windows Forms pomocí zarovnávacích čar
Přesné umístění ovládacích prvků ve formuláři je velmi prioritní pro mnoho aplikací. Návrhář formulářů poskytuje mnoho nástrojů pro rozložení, které vám to umožní. Jednou z nejdůležitějších funkcí je tato <xref:System.Windows.Forms.Design.Behavior.SnapLine> funkce.

 Zarovnávacím čárám vám ukáže přesně, kde můžete zarovnat ovládací prvky s dalšími ovládacími prvky. Také ukazují doporučené vzdálenosti pro okraje mezi ovládacími prvky, jak je určeno v pokynech uživatelského rozhraní systému Windows. Podrobnosti najdete v tématu [Návrh a vývoj uživatelského rozhraní](https://go.microsoft.com/FWLink/?LinkId=83878).

 Zarovnávacím čárám usnadňuje zarovnání ovládacích prvků pro zajištění ostrých a profesionálních vzhledů a chování (vzhled a chování).

 Úlohy, které jsou znázorněné v tomto návodu, zahrnují:

- Vytvoření projektu model Windows Forms

- Mezery a zarovnání ovládacích prvků pomocí zarovnávacím čárám

- Zarovnání na okraje formuláře a kontejneru

- Zarovnání na seskupené ovládací prvky

- Použití zarovnávacím čárám k umístění ovládacího prvku po sbalení jeho velikosti

- Použití zarovnávacím čárám při přetahování ovládacího prvku ze sady nástrojů

- Změna velikosti ovládacích prvků pomocí zarovnávacím čárám

- Zarovnání popisku na text ovládacího prvku

- Použití zarovnávacím čárám s navigací klávesnice

- Zarovnávacím čárám a panely rozložení

- Zakázání zarovnávacím čárám

 Až budete hotovi, budete obeznámeni s tím, jak se role rozložení hraje funkcí zarovnávacím čárám.

## <a name="creating-the-project"></a>Vytvoření projektu
 Prvním krokem je vytvoření projektu a nastavení formuláře.

### <a name="to-create-the-project"></a>Vytvoření projektu

1. Vytvoření projektu aplikace založeného na systému Windows s názvem "SnaplineExample" (**soubor** > **nového** > **projektu** >  **C# Visual** nebo **Visual Basic** > **Classic Desktopová** > **aplikace model Windows Forms**).

2. V Návrháři formulářů vyberte formulář.

## <a name="spacing-and-aligning-controls-using-snaplines"></a>Mezery a zarovnání ovládacích prvků pomocí zarovnávacím čárám
 Zarovnávacím čárám poskytuje přesný a intuitivní způsob, jak zarovnat ovládací prvky ve formuláři. Zobrazí se, když přesouváte vybraný ovládací prvek nebo ovládací prvky poblíž pozice, která by byla zarovnána s jiným ovládacím prvkem nebo sadou ovládacích prvků. Váš výběr bude "přichycen" do navrhované pozice při přesunu za ostatní ovládací prvky.

### <a name="to-arrange-controls-using-snaplines"></a>Uspořádání ovládacích prvků pomocí zarovnávacím čárám

1. Přetáhněte ovládací prvek z **panelu nástrojů** do formuláře. <xref:System.Windows.Forms.Button>

2. <xref:System.Windows.Forms.Button> Přesuňte ovládací prvek do pravého dolního rohu formuláře. Všimněte si, že zarovnávacím čárám, který <xref:System.Windows.Forms.Button> se zobrazí jako ovládací prvek, přistupuje k dolnímu a pravému okraji formuláře. Tyto zarovnávacím čárámy zobrazují doporučenou vzdálenost mezi ohraničením ovládacího prvku a formulářem.

3. <xref:System.Windows.Forms.Button> Přesuňte ovládací prvek kolem ohraničení formuláře a Všimněte si, kde se zobrazí zarovnávacím čárám. Až budete hotovi, přesuňte <xref:System.Windows.Forms.Button> ovládací prvek poblíž středu formuláře.

4. Přetáhněte jiný <xref:System.Windows.Forms.Button> ovládací prvek z **panelu nástrojů** do formuláře.

5. Přesuňte druhý <xref:System.Windows.Forms.Button> ovládací prvek, dokud není téměř na první úrovni s prvním. Všimněte si snapline, který se zobrazí na účaří textu obou tlačítek, a Všimněte si, že ovládací prvek, který přesouváte, se přichytí k pozici, která je přesně na úrovni s druhým ovládacím prvkem.

6. Přesuňte druhý <xref:System.Windows.Forms.Button> ovládací prvek do umístění přímo nad první. Všimněte si zarovnávacím čárám, který se zobrazí podél levého a pravého okraje obou tlačítek, a Všimněte si, že ovládací prvek, který přesouváte, se přichytí k pozici, která je přesně zarovnána s druhým ovládacím prvkem.

7. Vyberte jeden z <xref:System.Windows.Forms.Button> ovládacích prvků a přesuňte ho blízko k druhému, dokud nebudou skoro dotek. Všimněte si snapline, který se mezi nimi objevuje. Tato vzdálenost je doporučená vzdálenost mezi ohraničením ovládacích prvků. Všimněte si také, že ovládací prvek, který přesouváte, se přichytí k této pozici.

8. Přetáhněte dva <xref:System.Windows.Forms.Panel> ovládací prvky ze **sady nástrojů** do formuláře.

9. Přesuňte jeden z <xref:System.Windows.Forms.Panel> ovládacích prvků, dokud není téměř na první úrovni s prvním. Všimněte si zarovnávacím čárám, který se zobrazí podél horního a dolního okraje obou ovládacích prvků, a Všimněte si, že ovládací prvek, který přesouváte, se přichytí k pozici, která je přesně na úrovni s druhým ovládacím prvkem.

## <a name="aligning-to-form-and-container-margins"></a>Zarovnání na okraje formuláře a kontejneru
 Zarovnávacím čárám vám umožní sjednotit ovládací prvky tak, aby byly v souladu s konzistentním způsobem.

### <a name="to-align-controls-to-form-and-container-margins"></a>Zarovnání ovládacích prvků na okraje formuláře a kontejneru

1. Vyberte jeden z <xref:System.Windows.Forms.Button> ovládacích prvků a přesuňte ho blízko k pravému okraji formuláře, dokud se nezobrazí snapline. Vzdálenost snapline od pravého ohraničení je součtem <xref:System.Windows.Forms.Control.Margin%2A> vlastnosti ovládacího prvku a hodnot <xref:System.Windows.Forms.Control.Padding%2A> vlastností formuláře.

> [!NOTE]
> Pokud je <xref:System.Windows.Forms.Control.Padding%2A> vlastnost formuláře nastavená na 0, 0, 0, 0, Návrhář formulářů má formu <xref:System.Windows.Forms.Control.Padding%2A> stínovou hodnotu 9, 9, 9, 9. Chcete-li toto chování přepsat, přiřaďte hodnotu jinou než 0, 0, 0, 0.

1. Změňte hodnotu <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.Control.Margin%2A> vlastnosti ovládacího prvku rozbalením <xref:System.Windows.Forms.Control.Margin%2A> <xref:System.Windows.Forms.Padding.All%2A> položky v okně **vlastnosti** a nastavením vlastnosti na hodnotu 0. Podrobnosti najdete v tématu [Návod: Rozložení model Windows Forms ovládacích prvků s odsazením, okraji a vlastností](windows-forms-controls-padding-autosize.md)AutoSize.

2. <xref:System.Windows.Forms.Button> Přesuňte ovládací prvek blízko k pravému okraji formuláře, dokud se nezobrazí snapline. Tato vzdálenost je nyní dána hodnotou <xref:System.Windows.Forms.Control.Padding%2A> vlastnosti formuláře.

3. Přetáhněte ovládací prvek z **panelu nástrojů** do formuláře. <xref:System.Windows.Forms.GroupBox>

4. Rozbalením <xref:System.Windows.Forms.GroupBox> <xref:System.Windows.Forms.Control.Padding%2A> <xref:System.Windows.Forms.Control.Padding%2A> položkyvokněVlastnostianastavenímvlastnostinahodnotu10<xref:System.Windows.Forms.Padding.All%2A> změňte hodnotu vlastnosti ovládacího prvku.

5. Přetáhněte ovládací prvek ze <xref:System.Windows.Forms.GroupBox> **sady nástrojů** do ovládacího prvku. <xref:System.Windows.Forms.Button>

6. Přesuňte ovládací prvek blízko k pravému okraji <xref:System.Windows.Forms.GroupBox> ovládacího prvku, dokud se nezobrazí snapline. <xref:System.Windows.Forms.Button> Přesuňte ovládací prvek <xref:System.Windows.Forms.GroupBox> v ovládacím prvku a Všimněte si, kde se zobrazí zarovnávacím čárám. <xref:System.Windows.Forms.Button>

## <a name="aligning-to-grouped-controls"></a>Zarovnání na seskupené ovládací prvky
 Pomocí zarovnávacím čárám můžete zarovnat seskupené ovládací prvky i ovládací prvky v rámci <xref:System.Windows.Forms.GroupBox> ovládacího prvku.

### <a name="to-align-to-grouped-controls"></a>Zarovnání na seskupené ovládací prvky

1. Vyberte dva ovládací prvky ve formuláři. Posuňte výběr kolem a poznamenejte si zarovnávacím čárám, který se zobrazí mezi vaším výběrem a dalšími ovládacími prvky.

2. Přetáhněte ovládací prvek z **panelu nástrojů** do formuláře. <xref:System.Windows.Forms.GroupBox>

3. Přetáhněte ovládací prvek ze <xref:System.Windows.Forms.GroupBox> **sady nástrojů** do ovládacího prvku. <xref:System.Windows.Forms.Button>

4. Vyberte jeden z <xref:System.Windows.Forms.Button> ovládacích prvků a přesuňte jej <xref:System.Windows.Forms.GroupBox> kolem ovládacího prvku. Všimněte si zarovnávacím čárám, který se zobrazí na okrajích <xref:System.Windows.Forms.GroupBox> ovládacího prvku. Všimněte si také zarovnávacím čárám, který se zobrazí na okrajích <xref:System.Windows.Forms.Button> ovládacího prvku, který je obsažen <xref:System.Windows.Forms.GroupBox> v ovládacím prvku. Ovládací prvky, které jsou podřízené ovládacímu prvku kontejneru, také podporují zarovnávacím čárám.

## <a name="using-snaplines-to-place-a-control-by-outlining-its-size"></a>Použití zarovnávacím čárám k umístění ovládacího prvku po sbalení jeho velikosti
 Zarovnávacím čárám vám pomůžou Zarovnat ovládací prvky při jejich prvním umístění na formuláři.

### <a name="to-use-snaplines-to-place-a-control-by-outlining-its-size"></a>Použití zarovnávacím čárám k umístění ovládacího prvku po sbalení jeho velikosti

1. Na **panelu nástrojů**klikněte <xref:System.Windows.Forms.Button> na ikonu ovládacího prvku. Nepřetáhněte ho do formuláře.

2. Přesuňte ukazatel myši nad návrhovou plochu formuláře. Všimněte si, že se ukazatel změní na vlasovou <xref:System.Windows.Forms.Button> čáru s připojenou ikonou ovládacího prvku. Všimněte si také zarovnávacím čárám, který se zobrazí pro návrh zarovnané pozice <xref:System.Windows.Forms.Button> ovládacího prvku.

3. Klikněte a podržte tlačítko myši.

4. Přetáhněte ukazatel myši kolem formuláře. Všimněte si, že je vykreslen obrys, který označuje polohu a velikost ovládacího prvku.

5. Přetáhněte ukazatel, dokud není zarovnán k jinému ovládacímu prvku ve formuláři. Všimněte si, že k označení zarovnání se zobrazí snapline.

6. Uvolněte tlačítko myši. Ovládací prvek je vytvořen na pozici a velikosti vyznačené obrysem.

## <a name="using-snaplines-when-dragging-a-control-from-the-toolbox"></a>Použití zarovnávacím čárám při přetahování ovládacího prvku ze sady nástrojů
 Zarovnávacím čárám vám pomůžou Zarovnat ovládací prvky při jejich přetahování z **panelu nástrojů** do formuláře.

### <a name="to-use-snaplines-when-dragging-a-control-from-the-toolbox"></a>Použití zarovnávacím čárám při přetahování ovládacího prvku ze sady nástrojů

1. Přetáhněte ovládací prvek z **panelu nástrojů** do formuláře, ale neuvolní tlačítko myši. <xref:System.Windows.Forms.Button>

2. Přesuňte ukazatel myši nad návrhovou plochu formuláře. Všimněte si, že se ukazatel změní, aby označoval pozici, na <xref:System.Windows.Forms.Button> které bude nový ovládací prvek vytvořen.

3. Přetáhněte ukazatel myši kolem formuláře. Všimněte si zarovnávacím čárám, který se zobrazí pro návrh zarovnané pozice <xref:System.Windows.Forms.Button> ovládacího prvku. Najde pozici, která je zarovnána s jinými ovládacími prvky.

4. Uvolněte tlačítko myši. Ovládací prvek se vytvoří na pozici označené zarovnávacím čárámem.

## <a name="resizing-controls-using-snaplines"></a>Změna velikosti ovládacích prvků pomocí zarovnávacím čárám
 Zarovnávacím čárám vám pomůžou Zarovnat ovládací prvky podle jejich velikosti.

### <a name="to-resize-a-control-using-snaplines"></a>Změna velikosti ovládacího prvku pomocí zarovnávacím čárám

1. Přetáhněte ovládací prvek z **panelu nástrojů** do formuláře. <xref:System.Windows.Forms.Button>

2. Změňte velikost <xref:System.Windows.Forms.Button> ovládacího prvku tak, že přetáhnete jeden z rohových úchytů pro změnu velikosti a přetažením. Podrobnosti najdete v tématu [How to: Změna velikosti ovládacích prvků](how-to-resize-controls-on-windows-forms.md)na model Windows Forms.

3. Přetáhněte úchyt pro změnu velikosti, dokud jedna <xref:System.Windows.Forms.Button> z ohraničení ovládacího prvku není zarovnána k jinému ovládacímu prvku. Všimněte si, že se zobrazí snapline. Všimněte si také, že se úchyt pro změnu velikosti přitahuje na pozici určenou v snapline.

4. Změňte velikost <xref:System.Windows.Forms.Button> ovládacího prvku v různých směrech a Zarovnejte úchyt pro různé ovládací prvky. Všimněte si, jak se zarovnávacím čárám zobrazuje v různých orientech k označení zarovnání.

## <a name="aligning-a-label-to-a-controls-text"></a>Zarovnání popisku na text ovládacího prvku
 Některé ovládací prvky nabízejí snapline pro zarovnání jiných ovládacích prvků na zobrazený text.

### <a name="to-align-a-label-to-a-controls-text"></a>Zarovnání popisku na text ovládacího prvku

1. Přetáhněte ovládací prvek z **panelu nástrojů** do formuláře. <xref:System.Windows.Forms.TextBox> Když <xref:System.Windows.Forms.TextBox> ovládací prvek vyřadíte do formuláře, klikněte na glyf inteligentních značek a vyberte možnost **nastavit text na TextBox1** . Podrobnosti najdete v tématu [Návod: Provádění běžných úloh pomocí inteligentních značek v ovládacích](performing-common-tasks-using-smart-tags-on-wf-controls.md)prvcích model Windows Forms.

2. Přetáhněte ovládací prvek z **panelu nástrojů** do formuláře. <xref:System.Windows.Forms.Label>

3. Změňte hodnotu <xref:System.Windows.Forms.Label> <xref:System.Windows.Forms.Control.AutoSize%2A> vlastnosti ovládacího prvku na `true`. Všimněte si, že ohraničení ovládacího prvku jsou upraveny tak, aby odpovídaly zobrazovanému textu.

4. Přesune ovládací prvek nalevo <xref:System.Windows.Forms.TextBox> od ovládacího prvku, takže je zarovnán s dolním okrajem <xref:System.Windows.Forms.TextBox> ovládacího prvku. <xref:System.Windows.Forms.Label> Všimněte si snapline, který se zobrazí podél dolních hran dvou ovládacích prvků.

5. Posune <xref:System.Windows.Forms.Label> <xref:System.Windows.Forms.TextBox> ovládací prvek mírně nahoru, dokud text a text nebudou zarovnány. <xref:System.Windows.Forms.Label> Všimněte si, že se zobrazí různé snapline styly, které označují, kdy jsou textová pole obou ovládacích prvků zarovnána.

## <a name="using-snaplines-with-keyboard-navigation"></a>Použití zarovnávacím čárám s navigací klávesnice
 Zarovnávacím čárám vám pomůžou Zarovnat ovládací prvky při jejich uspořádání pomocí kláves se šipkami.

### <a name="to-use-snaplines-with-keyboard-navigation"></a>Použití zarovnávacím čárám s navigací klávesnice

1. Přetáhněte ovládací prvek z **panelu nástrojů** do formuláře. <xref:System.Windows.Forms.Button> Umístěte ho do levého horního rohu formuláře.

2. Stiskněte klávesovou zkratku CTRL + šipka dolů. Všimněte si, že ovládací prvek se přesune do prvního dostupné pozice vodorovného zarovnání dolů ve formuláři.

3. Stiskněte kombinaci kláves CTRL + šipka dolů, dokud ovládací prvek nedosáhne spodní části formuláře. Poznamenejte si pozice, které zabírají při přesunu formuláře.

4. Stiskněte klávesovou zkratku CTRL + ŠIPKA vpravo. Všimněte si, že ovládací prvek se přesune mezi formulářem na první dostupnou pozici svislého zarovnání.

5. Stiskněte kombinaci kláves CTRL + ŠIPKA vpravo, dokud ovládací prvek nedosáhne strany formuláře. Poznamenejte si pozice, které zabírají při přesunu napříč formulářem.

6. Přesuňte ovládací prvek kolem formuláře s kombinací kláves se šipkami. Všimněte si pozic, které ovládací prvek zabírá, a zarovnávacím čárám, které jim doprovází.

7. Stisknutím klávesy SHIFT + libovolné klávesy se šipkou <xref:System.Windows.Forms.Button> změňte velikost ovládacího prvku o krok po jednom pixelu.

8. Stisknutím kombinace kláves CTRL + SHIFT + Kterákoli klávesa se <xref:System.Windows.Forms.Button> šipkou změníte velikost ovládacího prvku v snapline přírůstcích.

## <a name="snaplines-and-layout-panels"></a>Zarovnávacím čárám a panely rozložení
 Zarovnávacím čárám jsou v panelech rozložení zakázané.

### <a name="to-selectively-disable-snaplines"></a>Selektivní zakázání zarovnávacím čárám

1. Přetáhněte ovládací prvek z **panelu nástrojů** do formuláře. <xref:System.Windows.Forms.TableLayoutPanel>

2. Dvakrát klikněte <xref:System.Windows.Forms.Button> na ikonu ovládacího prvku v **sadě nástrojů**. Všimněte si, že nový ovládací prvek tlačítko se <xref:System.Windows.Forms.TableLayoutPanel> zobrazí v první buňce ovládacího prvku.

3. Dvakrát klikněte <xref:System.Windows.Forms.Button> na ikonu ovládacího prvku na **panelu nástrojů** . Tím se <xref:System.Windows.Forms.TableLayoutPanel> v ovládacím prvku opustí jedna prázdná buňka.

4. Přetáhněte ovládací prvek ze **sady nástrojů** do <xref:System.Windows.Forms.TableLayoutPanel> prázdné buňky ovládacího prvku. <xref:System.Windows.Forms.Button> Všimněte si, že se nezobrazí žádná zarovnávacím čárám.

5. Přetáhněte ovládací prvek <xref:System.Windows.Forms.TableLayoutPanel> z ovládacího prvku <xref:System.Windows.Forms.TableLayoutPanel> a přesuňte ho kolem ovládacího prvku. <xref:System.Windows.Forms.Button> Všimněte si, že se znovu zobrazí zarovnávacím čárám.

## <a name="disabling-snaplines"></a>Zakázání zarovnávacím čárám
 Zarovnávacím čárám jsou ve výchozím nastavení zapnuté. Můžete zakázat zarovnávacím čárám selektivně nebo je můžete zakázat v prostředí pro návrh.

### <a name="to-selectively-disable-snaplines"></a>Selektivní zakázání zarovnávacím čárám

- Stiskněte klávesu ALT a při přesunu ovládacího prvku kolem formuláře.

     Všimněte si, že se nezobrazí žádné zarovnávacím čárám a ovládací prvek se nepřichytí k žádným potenciálním polohám zarovnání.

### <a name="to-disable-snaplines-in-the-design-environment"></a>Zakázání zarovnávacím čárám v prostředí pro návrh

1. V nabídce **nástroje** otevřete dialogové okno **Možnosti** . Otevřete dialogové okno Návrhář formulářů. Podrobnosti najdete v tématu [Obecné, Návrhář formulářů, dialogové okno Možnosti](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/5aazxs78(v=vs.100)).

2. Vyberte uzel **Obecné** . V části **Režim rozložení** změňte výběr z **zarovnávacím čárám** na **SnapToGrid**.

3. Kliknutím na OK nastavení použijte.

4. Vyberte ovládací prvek ve formuláři a přesuňte ho kolem dalších ovládacích prvků. Všimněte si, že zarovnávacím čárám se nezobrazí.

## <a name="next-steps"></a>Další kroky
 Zarovnávacím čárám nabízí intuitivní způsob zarovnání ovládacích prvků na formuláři. Mezi návrhy pro další zkoumání patří:

- Zkuste vnořit <xref:System.Windows.Forms.GroupBox> ovládací prvek do jiného <xref:System.Windows.Forms.GroupBox> ovládacího prvku. Umístěte ovládací prvek do podřízeného <xref:System.Windows.Forms.GroupBox> ovládacího prvku a druhý v rámci nadřazeného <xref:System.Windows.Forms.GroupBox> ovládacího prvku. <xref:System.Windows.Forms.Button> Přesunutím <xref:System.Windows.Forms.Button> ovládacích prvků kolem zobrazíte, jak zarovnávacím čárám hranice mezi kontejnery.

- Vytvořte sloupec <xref:System.Windows.Forms.TextBox> ovládacích prvků a odpovídající <xref:System.Windows.Forms.Label> sloupec ovládacích prvků. Nastavte hodnotu <xref:System.Windows.Forms.Label> <xref:System.Windows.Forms.Control.AutoSize%2A> vlastnosti Controls na `true`. Použijte zarovnávacím čárám k přesunutí <xref:System.Windows.Forms.Label> ovládacích prvků tak, aby byl zobrazený text zarovnán s textem <xref:System.Windows.Forms.TextBox> v ovládacích prvcích.

 Informace o návrhu uživatelského rozhraní systému Windows najdete v tématu Příručka *pro uživatele Microsoft Windows, oficiální pokyny pro vývojáře a návrháře uživatelského rozhraní* Redmond, WA: Microsoft Press, 1999. (USBN: 0-7356-0566-1).

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.Design.Behavior.SnapLine>
- [Návod: Uspořádání ovládacích prvků na model Windows Forms pomocí FlowLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [Návod: Uspořádání ovládacích prvků na model Windows Forms pomocí kontejneru TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [Návod: Rozložení model Windows Forms ovládacích prvků s odsazením, okraji a vlastností AutoSize](windows-forms-controls-padding-autosize.md)
- [Uspořádávání ovládacích prvků ve Windows Forms](arranging-controls-on-windows-forms.md)
