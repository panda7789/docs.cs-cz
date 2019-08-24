---
title: 'Návod: Uspořádání ovládacích prvků ve Windows Forms pomocí zarovnávacích čar'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], arranging with snaplines
- snaplines [Windows Forms], arranging Windows Forms controls
- SnapLine class [Windows Forms], walkthroughs
- Windows Forms controls, arranging
ms.assetid: d5c9edc7-cf30-4a97-8ebe-201d569340f8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 83f0365ffb7335cb67c729c5a113e550c119191a
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/23/2019
ms.locfileid: "69987005"
---
# <a name="walkthrough-arrange-controls-on-windows-forms-using-snaplines"></a>Návod: Uspořádání ovládacích prvků na model Windows Forms pomocí zarovnávacím čárám

Přesné umístění ovládacích prvků ve formuláři je velmi prioritní pro mnoho aplikací. Návrhář formulářů poskytuje mnoho nástrojů pro rozložení, které vám to umožní. Jednou z nejdůležitějších funkcí je tato <xref:System.Windows.Forms.Design.Behavior.SnapLine> funkce.

Zarovnávacím čárám vám ukáže přesně, kde můžete zarovnat ovládací prvky s dalšími ovládacími prvky. Také ukazují doporučené vzdálenosti pro okraje mezi ovládacími prvky, jak je určeno v pokynech [uživatelského rozhraní systému Windows](/windows/win32/uxguide/guidelines).

Zarovnávacím čárám usnadňuje zarovnání ovládacích prvků pro zajištění ostrých a profesionálních vzhledů a chování (vzhled a chování).

## <a name="create-the-project"></a>Vytvoření projektu

1. V aplikaci Visual Studio vytvořte projekt aplikace založený na systému Windows s názvem "SnaplineExample".

2. V Návrháři formulářů vyberte formulář.

## <a name="space-and-align-controls"></a>Mezery a zarovnání ovládacích prvků

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

## <a name="align-to-form-and-container-margins"></a>Zarovnat k okrajům formuláře a kontejneru

Zarovnávacím čárám vám umožní sjednotit ovládací prvky tak, aby byly v souladu s konzistentním způsobem.

1. Vyberte jeden z <xref:System.Windows.Forms.Button> ovládacích prvků a přesuňte ho blízko k pravému okraji formuláře, dokud se nezobrazí snapline. Vzdálenost snapline od pravého ohraničení je součtem <xref:System.Windows.Forms.Control.Margin%2A> vlastnosti ovládacího prvku a hodnot <xref:System.Windows.Forms.Control.Padding%2A> vlastností formuláře.

   > [!NOTE]
   > Pokud je <xref:System.Windows.Forms.Control.Padding%2A> vlastnost formuláře nastavená na 0, 0, 0, 0, Návrhář formulářů má formu <xref:System.Windows.Forms.Control.Padding%2A> stínovou hodnotu 9, 9, 9, 9. Chcete-li toto chování přepsat, přiřaďte hodnotu jinou než 0, 0, 0, 0.

2. Změňte hodnotu <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.Control.Margin%2A> vlastnosti ovládacího prvku rozbalením <xref:System.Windows.Forms.Control.Margin%2A> <xref:System.Windows.Forms.Padding.All%2A> položky v okně **vlastnosti** a nastavením vlastnosti na hodnotu 0. Podrobnosti najdete v tématu [Návod: Rozložení model Windows Forms ovládacích prvků s odsazením, okraji a vlastností](windows-forms-controls-padding-autosize.md)AutoSize.

3. <xref:System.Windows.Forms.Button> Přesuňte ovládací prvek blízko k pravému okraji formuláře, dokud se nezobrazí snapline. Tato vzdálenost je nyní dána hodnotou <xref:System.Windows.Forms.Control.Padding%2A> vlastnosti formuláře.

4. Přetáhněte ovládací prvek z **panelu nástrojů** do formuláře. <xref:System.Windows.Forms.GroupBox>

5. Rozbalením <xref:System.Windows.Forms.GroupBox> <xref:System.Windows.Forms.Control.Padding%2A> <xref:System.Windows.Forms.Control.Padding%2A> položkyvokněVlastnostianastavenímvlastnostinahodnotu10<xref:System.Windows.Forms.Padding.All%2A> změňte hodnotu vlastnosti ovládacího prvku.

6. Přetáhněte ovládací prvek ze <xref:System.Windows.Forms.GroupBox> **sady nástrojů** do ovládacího prvku. <xref:System.Windows.Forms.Button>

7. Přesuňte ovládací prvek blízko k pravému okraji <xref:System.Windows.Forms.GroupBox> ovládacího prvku, dokud se nezobrazí snapline. <xref:System.Windows.Forms.Button> Přesuňte ovládací prvek <xref:System.Windows.Forms.GroupBox> v ovládacím prvku a Všimněte si, kde se zobrazí zarovnávacím čárám. <xref:System.Windows.Forms.Button>

## <a name="align-to-grouped-controls"></a>Zarovnat ke seskupeným ovládacím prvkům

Pomocí zarovnávacím čárám můžete zarovnat seskupené ovládací prvky i ovládací prvky v rámci <xref:System.Windows.Forms.GroupBox> ovládacího prvku.

1. Vyberte dva ovládací prvky ve formuláři. Posuňte výběr kolem a poznamenejte si zarovnávacím čárám, který se zobrazí mezi vaším výběrem a dalšími ovládacími prvky.

2. Přetáhněte ovládací prvek z **panelu nástrojů** do formuláře. <xref:System.Windows.Forms.GroupBox>

3. Přetáhněte ovládací prvek ze <xref:System.Windows.Forms.GroupBox> **sady nástrojů** do ovládacího prvku. <xref:System.Windows.Forms.Button>

4. Vyberte jeden z <xref:System.Windows.Forms.Button> ovládacích prvků a přesuňte jej <xref:System.Windows.Forms.GroupBox> kolem ovládacího prvku. Všimněte si zarovnávacím čárám, který se zobrazí na okrajích <xref:System.Windows.Forms.GroupBox> ovládacího prvku. Všimněte si také zarovnávacím čárám, který se zobrazí na okrajích <xref:System.Windows.Forms.Button> ovládacího prvku, který je obsažen <xref:System.Windows.Forms.GroupBox> v ovládacím prvku. Ovládací prvky, které jsou podřízené ovládacímu prvku kontejneru, také podporují zarovnávacím čárám.

## <a name="use-snaplines-to-place-a-control-by-outlining-its-size"></a>Použití zarovnávacím čárám k umístění ovládacího prvku po sbalení jeho velikosti

1. Na **panelu nástrojů**klikněte <xref:System.Windows.Forms.Button> na ikonu ovládacího prvku. Nepřetáhněte ho do formuláře.

2. Přesuňte ukazatel myši nad návrhovou plochu formuláře. Všimněte si, že se ukazatel změní na vlasovou <xref:System.Windows.Forms.Button> čáru s připojenou ikonou ovládacího prvku. Všimněte si také zarovnávacím čárám, který se zobrazí pro návrh zarovnané pozice <xref:System.Windows.Forms.Button> ovládacího prvku.

3. Klikněte a podržte tlačítko myši.

4. Přetáhněte ukazatel myši kolem formuláře. Všimněte si, že je vykreslen obrys, který označuje polohu a velikost ovládacího prvku.

5. Přetáhněte ukazatel, dokud není zarovnán k jinému ovládacímu prvku ve formuláři. Všimněte si, že k označení zarovnání se zobrazí snapline.

6. Uvolněte tlačítko myši. Ovládací prvek je vytvořen na pozici a velikosti vyznačené obrysem.

## <a name="use-snaplines-when-dragging-a-control-from-the-toolbox"></a>Použití zarovnávacím čárám při přetahování ovládacího prvku ze sady nástrojů

1. Přetáhněte ovládací prvek z **panelu nástrojů** do formuláře, ale neuvolní tlačítko myši. <xref:System.Windows.Forms.Button>

2. Přesuňte ukazatel myši nad návrhovou plochu formuláře. Všimněte si, že se ukazatel změní, aby označoval pozici, na <xref:System.Windows.Forms.Button> které bude nový ovládací prvek vytvořen.

3. Přetáhněte ukazatel myši kolem formuláře. Všimněte si zarovnávacím čárám, který se zobrazí pro návrh zarovnané pozice <xref:System.Windows.Forms.Button> ovládacího prvku. Najde pozici, která je zarovnána s jinými ovládacími prvky.

4. Uvolněte tlačítko myši. Ovládací prvek se vytvoří na pozici označené zarovnávacím čárámem.

## <a name="resize-a-control-using-snaplines"></a>Změna velikosti ovládacího prvku pomocí zarovnávacím čárám

1. Přetáhněte ovládací prvek z **panelu nástrojů** do formuláře. <xref:System.Windows.Forms.Button>

2. Změňte velikost <xref:System.Windows.Forms.Button> ovládacího prvku tak, že přetáhnete jeden z rohových úchytů pro změnu velikosti a přetažením. Podrobnosti najdete v tématu [How to: Změna velikosti ovládacích prvků](how-to-resize-controls-on-windows-forms.md)na model Windows Forms.

3. Přetáhněte úchyt pro změnu velikosti, dokud jedna <xref:System.Windows.Forms.Button> z ohraničení ovládacího prvku není zarovnána k jinému ovládacímu prvku. Všimněte si, že se zobrazí snapline. Všimněte si také, že se úchyt pro změnu velikosti přitahuje na pozici určenou v snapline.

4. Změňte velikost <xref:System.Windows.Forms.Button> ovládacího prvku v různých směrech a Zarovnejte úchyt pro různé ovládací prvky. Všimněte si, jak se zarovnávacím čárám zobrazuje v různých orientech k označení zarovnání.

## <a name="align-a-label-to-a-controls-text"></a>Zarovnání popisku na text ovládacího prvku

1. Přetáhněte ovládací prvek z **panelu nástrojů** do formuláře. <xref:System.Windows.Forms.TextBox> Když <xref:System.Windows.Forms.TextBox> ovládací prvek vyřadíte do formuláře, klikněte na glyf inteligentních značek a vyberte možnost **nastavit text na TextBox1** . Podrobnosti najdete v tématu [Návod: Provádění běžných úloh pomocí inteligentních značek v ovládacích](performing-common-tasks-using-smart-tags-on-wf-controls.md)prvcích model Windows Forms.

2. Přetáhněte ovládací prvek z **panelu nástrojů** do formuláře. <xref:System.Windows.Forms.Label>

3. Změňte hodnotu <xref:System.Windows.Forms.Label> <xref:System.Windows.Forms.Control.AutoSize%2A> vlastnosti ovládacího prvku na `true`. Všimněte si, že ohraničení ovládacího prvku jsou upraveny tak, aby odpovídaly zobrazovanému textu.

4. Přesune ovládací prvek nalevo <xref:System.Windows.Forms.TextBox> od ovládacího prvku, takže je zarovnán s dolním okrajem <xref:System.Windows.Forms.TextBox> ovládacího prvku. <xref:System.Windows.Forms.Label> Všimněte si snapline, který se zobrazí podél dolních hran dvou ovládacích prvků.

5. Posune <xref:System.Windows.Forms.Label> <xref:System.Windows.Forms.TextBox> ovládací prvek mírně nahoru, dokud text a text nebudou zarovnány. <xref:System.Windows.Forms.Label> Všimněte si, že se zobrazí různé snapline styly, které označují, kdy jsou textová pole obou ovládacích prvků zarovnána.

## <a name="use-snaplines-with-keyboard-navigation"></a>Použití zarovnávacím čárám s navigací klávesnice

1. Přetáhněte ovládací prvek z **panelu nástrojů** do formuláře. <xref:System.Windows.Forms.Button> Umístěte ho do levého horního rohu formuláře.

2. Stiskněte **kombinaci kláves CTRL +** +**šipka dolů**. Všimněte si, že ovládací prvek se přesune do prvního dostupné pozice vodorovného zarovnání dolů ve formuláři.

3. Stiskněte klávesovou **zkratku CTRL +** +**šipka dolů** , dokud ovládací prvek nedosáhne spodní části formuláře. Poznamenejte si pozice, které zabírají při přesunu formuláře.

4. Stiskněte klávesu **CTRL**+**šipka vpravo**. Všimněte si, že ovládací prvek se přesune mezi formulářem na první dostupnou pozici svislého zarovnání.

5. Stiskněte klávesu **CTRL**+**šipka vpravo** , dokud ovládací prvek nedosáhne strany formuláře. Poznamenejte si pozice, které zabírají při přesunu napříč formulářem.

6. Přesuňte ovládací prvek kolem formuláře s kombinací kláves se šipkami. Všimněte si pozic, které ovládací prvek zabírá, a zarovnávacím čárám, které jim doprovází.

7. Chcete-li změnit velikost <xref:System.Windows.Forms.Button> ovládacího prvku stisknutím klávesy **SHIFT**+v přírůstcích po jednom pixelu.

8. Stisknutím **kombinace kláves CTRL**+**SHIFT +** +**šipka** změňte <xref:System.Windows.Forms.Button> velikost ovládacího prvku v snapline přírůstcích.

## <a name="selectively-disable-snaplines"></a>Selektivní zakázání zarovnávacím čárám

1. Přetáhněte ovládací prvek z **panelu nástrojů** do formuláře. <xref:System.Windows.Forms.TableLayoutPanel>

2. Dvakrát klikněte <xref:System.Windows.Forms.Button> na ikonu ovládacího prvku v **sadě nástrojů**. Všimněte si, že nový ovládací prvek tlačítko se <xref:System.Windows.Forms.TableLayoutPanel> zobrazí v první buňce ovládacího prvku.

3. Dvakrát klikněte <xref:System.Windows.Forms.Button> na ikonu ovládacího prvku na **panelu nástrojů** . Tím se <xref:System.Windows.Forms.TableLayoutPanel> v ovládacím prvku opustí jedna prázdná buňka.

4. Přetáhněte ovládací prvek ze **sady nástrojů** do <xref:System.Windows.Forms.TableLayoutPanel> prázdné buňky ovládacího prvku. <xref:System.Windows.Forms.Button> Všimněte si, že se nezobrazí žádná zarovnávacím čárám.

5. Přetáhněte ovládací prvek <xref:System.Windows.Forms.TableLayoutPanel> z ovládacího prvku <xref:System.Windows.Forms.TableLayoutPanel> a přesuňte ho kolem ovládacího prvku. <xref:System.Windows.Forms.Button> Všimněte si, že se znovu zobrazí zarovnávacím čárám.

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

- Zkuste vnořit <xref:System.Windows.Forms.GroupBox> ovládací prvek do jiného <xref:System.Windows.Forms.GroupBox> ovládacího prvku. Umístěte ovládací prvek do podřízeného <xref:System.Windows.Forms.GroupBox> ovládacího prvku a druhý v rámci nadřazeného <xref:System.Windows.Forms.GroupBox> ovládacího prvku. <xref:System.Windows.Forms.Button> Přesunutím <xref:System.Windows.Forms.Button> ovládacích prvků kolem zobrazíte, jak zarovnávacím čárám hranice mezi kontejnery.

- Vytvořte sloupec <xref:System.Windows.Forms.TextBox> ovládacích prvků a odpovídající <xref:System.Windows.Forms.Label> sloupec ovládacích prvků. Nastavte hodnotu <xref:System.Windows.Forms.Label> <xref:System.Windows.Forms.Control.AutoSize%2A> vlastnosti Controls na `true`. Použijte zarovnávacím čárám k přesunutí <xref:System.Windows.Forms.Label> ovládacích prvků tak, aby byl zobrazený text zarovnán s textem <xref:System.Windows.Forms.TextBox> v ovládacích prvcích.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.Design.Behavior.SnapLine>
- [Návod: Uspořádání ovládacích prvků na model Windows Forms pomocí FlowLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [Návod: Uspořádání ovládacích prvků na model Windows Forms pomocí kontejneru TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [Návod: Rozložení model Windows Forms ovládacích prvků s odsazením, okraji a vlastností AutoSize](windows-forms-controls-padding-autosize.md)
