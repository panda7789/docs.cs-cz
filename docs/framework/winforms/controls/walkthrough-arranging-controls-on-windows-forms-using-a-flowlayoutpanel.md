---
title: Uspořádání ovládacích prvků pomocí FlowLayoutPanel
ms.date: 03/30/2017
helpviewer_keywords:
- FlowLayoutPanel control [Windows Forms], walkthroughs
- Windows Forms controls, arranging
- controls [Windows Forms], arranging with FlowLayoutPanel
- layout [Windows Forms], walkthroughs
ms.assetid: a1744323-0316-49c2-992e-ebfc0a976b85
ms.openlocfilehash: 6df0a910ee346f319fbee835e5e632808630a99e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745401"
---
# <a name="walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel"></a>Postupy: Uspořádání ovládacích prvků na formuláři Windows s použitím ovládacího prvku FlowLayoutPanel

Některé aplikace vyžadují formulář s rozložením, které je uspořádáno správně, protože se změní velikost formuláře nebo se změní velikost obsahu. Pokud potřebujete dynamické rozložení a nechcete zpracovávat události <xref:System.Windows.Forms.Control.Layout> explicitně ve vašem kódu, zvažte použití panelu rozložení.

Ovládací prvek <xref:System.Windows.Forms.FlowLayoutPanel> a ovládací prvek <xref:System.Windows.Forms.TableLayoutPanel> poskytují intuitivní způsoby uspořádání ovládacích prvků ve formuláři. Obě poskytují automatickou, konfigurovatelný možnost pro řízení relativních pozic podřízených ovládacích prvků, které jsou v nich obsažené, a zároveň poskytují funkce dynamického rozložení za běhu, takže mohou změnit velikost a umístění podřízených ovládacích prvků jako rozměry nadřazeného formuláře. mění. Panely rozložení lze vnořovat do panelů rozložení, aby bylo možné provádět realizace sofistikovaných uživatelských rozhraní.

<xref:System.Windows.Forms.TableLayoutPanel> uspořádá jeho obsah do mřížky a poskytne funkce podobné prvku \<tabulky > HTML. Buňky se uspořádají do řádků a sloupců a můžou mít různé velikosti. Další informace naleznete v tématu [Návod: uspořádání ovládacích prvků na model Windows Forms pomocí kontejneru TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).

<xref:System.Windows.Forms.FlowLayoutPanel> uspořádá jeho obsah v určitém směru toku: Horizontal nebo Vertical. Jeho obsah lze zabalit z jednoho řádku na další, nebo z jednoho sloupce na další. Alternativně lze jeho obsah oříznout místo zabalení. Úlohy, které jsou znázorněné v tomto návodu, zahrnují:

- Vytvoření projektu model Windows Forms

- Uspořádání ovládacích prvků vodorovně a svisle

- Změna směru toku

- Vkládání konců toků

- Uspořádání ovládacích prvků pomocí odsazení a okrajů

- Vložení ovládacích prvků dvojitým kliknutím na ně v sadě nástrojů

- Vložení ovládacího prvku kreslením jeho obrysu

- Vložení ovládacích prvků pomocí stříšky

- Změna přiřazení existujících ovládacích prvků jinému nadřazenému prvku

Až budete hotovi, budete obeznámeni s tím, že role hraje tyto důležité funkce rozložení.

## <a name="create-the-project"></a>Vytvoření projektu

1. V aplikaci Visual Studio vytvořte projekt aplikace pro Windows s názvem "FlowLayoutPanelExample" (**soubor** > **New** > **Project** > **Visual C#**  nebo **Visual Basic** > **Classic Desktop** > **model Windows Forms aplikace**).

2. V **Návrháři formulářů**vyberte formulář.

## <a name="arranging-controls-horizontally-and-vertically"></a>Uspořádání ovládacích prvků vodorovně a svisle
 Ovládací prvek <xref:System.Windows.Forms.FlowLayoutPanel> umožňuje umístit ovládací prvky do řádků nebo sloupců bez nutnosti přesně zadat polohu každého jednotlivého ovládacího prvku.

 Ovládací prvek <xref:System.Windows.Forms.FlowLayoutPanel> může změnit velikost nebo přesměrovat své podřízené ovládací prvky jako rozměry změny nadřazeného formuláře.

### <a name="to-arrange-controls-horizontally-and-vertically-using-a-flowlayoutpanel"></a>Uspořádání ovládacích prvků vodorovně a svisle pomocí FlowLayoutPanel

1. Přetáhněte ovládací prvek <xref:System.Windows.Forms.FlowLayoutPanel> z **panelu nástrojů** do formuláře.

2. Přetáhněte ovládací prvek <xref:System.Windows.Forms.Button> ze **sady nástrojů** do <xref:System.Windows.Forms.FlowLayoutPanel>. Všimněte si, že je automaticky přesunut do levého horního rohu ovládacího prvku <xref:System.Windows.Forms.FlowLayoutPanel>.

3. Přetáhněte jiný ovládací prvek <xref:System.Windows.Forms.Button> ze **sady nástrojů** do <xref:System.Windows.Forms.FlowLayoutPanel>. Všimněte si, že <xref:System.Windows.Forms.Button> ovládací prvek je automaticky přesunut na pozici vedle prvního ovládacího prvku <xref:System.Windows.Forms.Button>. Pokud je <xref:System.Windows.Forms.FlowLayoutPanel> příliš úzký, aby se vešly dva ovládací prvky na stejný řádek, nový ovládací prvek <xref:System.Windows.Forms.Button> se automaticky přesune na další řádek.

4. Přetáhněte několik dalších <xref:System.Windows.Forms.Button> ovládacích prvků ze **sady nástrojů** do <xref:System.Windows.Forms.FlowLayoutPanel>. Pokračujte v umísťování <xref:System.Windows.Forms.Button> ovládacích prvků až do jednoho zalomení na další řádek.

5. Změňte hodnotu vlastnosti <xref:System.Windows.Forms.FlowLayoutPanel.WrapContents%2A> ovládacího prvku <xref:System.Windows.Forms.FlowLayoutPanel> na `false`. Všimněte si, že podřízené ovládací prvky již nejsou předávány dalšímu řádku. Místo toho jsou přesunuty do prvního řádku a oříznuty.

6. Změňte hodnotu vlastnosti <xref:System.Windows.Forms.FlowLayoutPanel.WrapContents%2A> ovládacího prvku <xref:System.Windows.Forms.FlowLayoutPanel> na `true`. Všimněte si, že podřízené ovládací prvky se znovu zalomí na další řádek.

7. Zmenšete šířku ovládacího prvku <xref:System.Windows.Forms.FlowLayoutPanel>, dokud nebudou všechny ovládací prvky <xref:System.Windows.Forms.Button> přesunuty do prvního sloupce.

8. Zvětšete šířku ovládacího prvku <xref:System.Windows.Forms.FlowLayoutPanel>, dokud nebudou všechny ovládací prvky <xref:System.Windows.Forms.Button> přesunuty do prvního řádku. Možná budete muset změnit velikost formuláře, aby odpovídal větší šířce.

## <a name="changing-flow-direction"></a>Změna směru toku
 Vlastnost <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> umožňuje změnit směr, ve kterém jsou ovládací prvky uspořádány. Můžete uspořádat podřízené ovládací prvky zleva doprava, zprava doleva, shora dolů nebo zdola nahoru.

### <a name="to-change-the-flow-direction-in-a-flowlayoutpanel"></a>Změna směru toku v kontejneru FlowLayoutPanel

1. Změňte hodnotu vlastnosti <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> ovládacího prvku <xref:System.Windows.Forms.FlowLayoutPanel> na <xref:System.Windows.Forms.FlowDirection.TopDown>. Všimněte si, že podřízené ovládací prvky jsou přeuspořádány do jednoho nebo více sloupců v závislosti na výšce ovládacího prvku.

2. Změňte velikost <xref:System.Windows.Forms.FlowLayoutPanel> tak, aby její výška byla kratší než sloupec <xref:System.Windows.Forms.Button> ovládací prvky. Všimněte si, že <xref:System.Windows.Forms.FlowLayoutPanel> mění uspořádání podřízených ovládacích prvků na tok do dalšího sloupce. Pokračujte v Zmenšení výšky a Všimněte si, že podřízené ovládací prvky přecházejí do po sobě jdoucích sloupců. Změňte hodnotu vlastnosti <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> ovládacího prvku <xref:System.Windows.Forms.FlowLayoutPanel> na <xref:System.Windows.Forms.FlowDirection.RightToLeft>. Všimněte si, že pozice podřízených ovládacích prvků jsou obráceny. Sledujte rozložení při změně hodnoty vlastnosti <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> na <xref:System.Windows.Forms.FlowDirection.BottomUp>.

## <a name="inserting-flow-breaks"></a>Vkládání konců toků
 Ovládací prvek <xref:System.Windows.Forms.FlowLayoutPanel> poskytuje svým podřízeným ovládacím prvkům vlastnost FlowBreak. Nastavením hodnoty vlastnosti FlowBreak na `true` dojde k tomu, že ovládací prvek <xref:System.Windows.Forms.FlowLayoutPanel> zastavil rozložení ovládacích prvků v aktuálním směru toku a zalomení na další řádek nebo sloupec.

### <a name="to-insert-flow-breaks"></a>Vložení konců toků

1. Změňte hodnotu vlastnosti <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> ovládacího prvku <xref:System.Windows.Forms.FlowLayoutPanel> na <xref:System.Windows.Forms.FlowDirection.TopDown>.

2. Vyberte jeden z ovládacích prvků <xref:System.Windows.Forms.Button> uprostřed sloupce úplně vlevo.

3. Nastavte hodnotu vlastnosti FlowBreak ovládacího prvku <xref:System.Windows.Forms.Button> na `true`. Všimněte si, že sloupec je přerušen a ovládací prvky, které následují pod vybraným ovládacím prvkem <xref:System.Windows.Forms.Button>, přesměrují do dalšího sloupce. Nastavte hodnotu vlastnosti FlowBreak ovládacího prvku <xref:System.Windows.Forms.Button> na `false` pro návrat k původnímu chování.

## <a name="positioning-controls-using-docking-and-anchoring"></a>Umístění ovládacích prvků pomocí ukotvení a ukotvení
 Chování při ukotvení a ukotvení podřízených ovládacích prvků se liší od chování v jiných ovládacích prvcích kontejneru. Ukotvení i ukotvení jsou relativní vzhledem k největšímu ovládacímu prvku ve směru toku.

### <a name="to-position-controls-using-docking-and-anchoring"></a>Chcete-li umístit ovládací prvky pomocí ukotvení a ukotvení

1. Zvětšete velikost <xref:System.Windows.Forms.FlowLayoutPanel>, dokud nejsou všechny ovládací prvky <xref:System.Windows.Forms.Button> uspořádány do sloupce.

2. Vyberte horní <xref:System.Windows.Forms.Button> ovládací prvek. Zvětšete svou šířku tak, aby byla přibližně dvojnásobná, jako ostatní ovládací prvky <xref:System.Windows.Forms.Button>.

3. Vyberte druhý ovládací prvek <xref:System.Windows.Forms.Button>. Změňte hodnotu vlastnosti <xref:System.Windows.Forms.Control.Anchor%2A> na <xref:System.Windows.Forms.AnchorStyles.Right>. Všimněte si, že je přesunutý, takže jeho pravé ohraničení je zarovnáno s prvním pravým okrajem ovládacího prvku <xref:System.Windows.Forms.Button>.

4. Změňte hodnotu vlastnosti <xref:System.Windows.Forms.Control.Anchor%2A> na <xref:System.Windows.Forms.AnchorStyles.Right> a <xref:System.Windows.Forms.AnchorStyles.Left>. Všimněte si, že má velikost na stejnou šířku jako první ovládací prvek <xref:System.Windows.Forms.Button>.

5. Vyberte třetí ovládací prvek <xref:System.Windows.Forms.Button>. Změňte hodnotu vlastnosti <xref:System.Windows.Forms.Control.Dock%2A> na <xref:System.Windows.Forms.DockStyle.Fill>. Všimněte si, že má velikost na stejnou šířku jako první ovládací prvek <xref:System.Windows.Forms.Button>.

## <a name="arranging-controls-using-padding-and-margins"></a>Uspořádání ovládacích prvků pomocí odsazení a okrajů
 Můžete také uspořádat ovládací prvky v ovládacím prvku <xref:System.Windows.Forms.FlowLayoutPanel> změnou vlastností <xref:System.Windows.Forms.Control.Padding%2A> a <xref:System.Windows.Forms.Control.Margin%2A>.

 Vlastnost <xref:System.Windows.Forms.Control.Padding%2A> umožňuje řídit umístění ovládacích prvků v buňce ovládacího prvku <xref:System.Windows.Forms.FlowLayoutPanel>. Určuje mezery mezi podřízenými ovládacími prvky a ohraničením ovládacího prvku <xref:System.Windows.Forms.FlowLayoutPanel>.

 Vlastnost <xref:System.Windows.Forms.Control.Margin%2A> umožňuje řídit mezery mezi ovládacími prvky.

### <a name="to-arrange-controls-using-the-padding-and-margin-properties"></a>Uspořádání ovládacích prvků pomocí vlastností odsazení a okraj

1. Změňte hodnotu vlastnosti <xref:System.Windows.Forms.Control.Dock%2A> ovládacího prvku <xref:System.Windows.Forms.FlowLayoutPanel> na <xref:System.Windows.Forms.DockStyle.Fill>. Je-li formulář dostatečně velký, ovládací prvky <xref:System.Windows.Forms.Button> budou přesunuty do prvního sloupce ovládacího prvku <xref:System.Windows.Forms.FlowLayoutPanel>.

2. Rozbalením položky <xref:System.Windows.Forms.Control.Padding%2A> v okně **vlastnosti** změňte hodnotu vlastnosti <xref:System.Windows.Forms.Control.Padding%2A> ovládacího prvku <xref:System.Windows.Forms.FlowLayoutPanel> a nastavte vlastnost <xref:System.Windows.Forms.Padding.All%2A> na hodnotu **20**. Další informace naleznete v tématu [Návod: rozvržení model Windows Forms ovládacích prvků s odsazením, okraji a vlastností AutoSize](windows-forms-controls-padding-autosize.md). Všimněte si, že podřízené ovládací prvky jsou přesunuty směrem ke středu ovládacího prvku <xref:System.Windows.Forms.FlowLayoutPanel>. Zvýšená hodnota vlastnosti <xref:System.Windows.Forms.Control.Padding%2A> přenáší podřízené ovládací prvky mimo hranice ovládacího prvku <xref:System.Windows.Forms.FlowLayoutPanel>.

3. Vyberte všechny ovládací prvky <xref:System.Windows.Forms.Button> v <xref:System.Windows.Forms.FlowLayoutPanel> a nastavte hodnotu vlastnosti <xref:System.Windows.Forms.Control.Margin%2A> na **20**. Všimněte si, že mezery mezi ovládacími prvky <xref:System.Windows.Forms.Button> se zvyšují, takže se od sebe přesunou dál. Možná budete muset změnit velikost ovládacího prvku <xref:System.Windows.Forms.FlowLayoutPanel> tak, aby bylo větší, aby se zobrazily všechny podřízené ovládací prvky.

## <a name="inserting-controls-by-double-clicking-them-in-the-toolbox"></a>Vložení ovládacích prvků dvojitým kliknutím na ně v sadě nástrojů
 Ovládací prvek <xref:System.Windows.Forms.FlowLayoutPanel> lze naplnit dvojitým kliknutím na ovládací prvky v **sadě nástrojů**.

### <a name="to-insert-controls-by-double-clicking-in-the-toolbox"></a>Vložení ovládacích prvků dvojitým kliknutím na panel nástrojů

1. Dvakrát klikněte na ikonu ovládacího prvku <xref:System.Windows.Forms.Button> v **sadě nástrojů**. Všimněte si, že v ovládacím prvku <xref:System.Windows.Forms.FlowLayoutPanel> se zobrazí nový ovládací prvek <xref:System.Windows.Forms.Button>.

2. Dvakrát klikněte na více ovládacích prvků v **sadě nástrojů**. Všimněte si, že nové ovládací prvky se zobrazí postupně v ovládacím prvku <xref:System.Windows.Forms.FlowLayoutPanel>.

## <a name="inserting-a-control-by-drawing-its-outline"></a>Vložení ovládacího prvku kreslením jeho obrysu
 Ovládací prvek můžete vložit do ovládacího prvku <xref:System.Windows.Forms.FlowLayoutPanel> a zadat jeho velikost vykreslením jeho obrysu v buňce.

### <a name="to-insert-a-control-by-drawing-its-outline"></a>Vložení ovládacího prvku kreslením jeho obrysu

1. Na **panelu nástrojů**klikněte na ikonu ovládacího prvku <xref:System.Windows.Forms.Button>. Nepřetáhněte ho do formuláře.

2. Přesuňte ukazatel myši nad ovládací prvek <xref:System.Windows.Forms.FlowLayoutPanel>. Všimněte si, že se ukazatel změní na vlasovou čáru s připojenou ikonou ovládacího prvku <xref:System.Windows.Forms.Button>.

3. Klikněte a podržte tlačítko myši.

4. Přetažením ukazatele myši nakreslete obrys ovládacího prvku <xref:System.Windows.Forms.Button>. Až budete s velikostí spokojeni, uvolněte tlačítko myši. Všimněte si, že <xref:System.Windows.Forms.Button> ovládací prvek je vytvořen v dalším otevřeném umístění ovládacího prvku <xref:System.Windows.Forms.FlowLayoutPanel>.

## <a name="inserting-controls-using-the-insertion-bar"></a>Vložení ovládacích prvků pomocí panelu vložení
 Ovládací prvky lze vložit na konkrétní pozici v ovládacím prvku <xref:System.Windows.Forms.FlowLayoutPanel>. Při přetažení ovládacího prvku do klientské oblasti ovládacího prvku <xref:System.Windows.Forms.FlowLayoutPanel> se zobrazí panel vložení, který označuje, kam bude ovládací prvek vložen.

### <a name="to-insert-a-control-using-the-caret"></a>Vložení ovládacího prvku pomocí stříšky

1. Přetáhněte ovládací prvek <xref:System.Windows.Forms.Button> z **panelu nástrojů** do ovládacího prvku <xref:System.Windows.Forms.FlowLayoutPanel> a nastavte ukazatel na místo mezi dvěma ovládacími prvky <xref:System.Windows.Forms.Button>. Všimněte si, že je vykreslen panel vložení, který označuje, kam bude <xref:System.Windows.Forms.Button> umístěn při jeho přetažení do ovládacího prvku <xref:System.Windows.Forms.FlowLayoutPanel>. Před vyřazením nového ovládacího prvku <xref:System.Windows.Forms.Button> do ovládacího prvku <xref:System.Windows.Forms.FlowLayoutPanel> přesunutím ukazatele myši v rozevíracím seznamu Sledujte, jak se panel vložení přesouvá.

2. Nový ovládací prvek <xref:System.Windows.Forms.Button> přetáhněte do ovládacího prvku <xref:System.Windows.Forms.FlowLayoutPanel>. Všimněte si, že nový ovládací prvek <xref:System.Windows.Forms.Button> není zarovnán s ostatními, protože jeho vlastnost <xref:System.Windows.Forms.Control.Margin%2A> má jinou hodnotu.

## <a name="reassigning-existing-controls-to-a-different-parent"></a>Změna přiřazení existujících ovládacích prvků jinému nadřazenému prvku
 Ovládací prvky, které existují na formuláři, můžete přiřadit novému ovládacímu prvku <xref:System.Windows.Forms.FlowLayoutPanel>.

### <a name="to-reparent-existing-controls"></a>Jak znovu zařadit existující ovládací prvky

1. Přetáhněte ze **sady nástrojů** do formuláře tři ovládací prvky <xref:System.Windows.Forms.Button>. Umístěte je blízko k sobě, ale nechte je nezarovnané.

2. Na **panelu nástrojů**klikněte na ikonu ovládacího prvku <xref:System.Windows.Forms.FlowLayoutPanel>. Nepřetáhněte ho do formuláře.

3. Přesuňte ukazatel myši blízko k třem ovládacím prvkům <xref:System.Windows.Forms.Button>. Všimněte si, že se ukazatel změní na vlasovou čáru s připojenou ikonou ovládacího prvku <xref:System.Windows.Forms.FlowLayoutPanel>.

4. Klikněte a podržte tlačítko myši.

5. Přetažením ukazatele myši nakreslete obrys ovládacího prvku <xref:System.Windows.Forms.FlowLayoutPanel>. Vykreslete obrys kolem tří <xref:System.Windows.Forms.Button>ch ovládacích prvků.

6. Uvolněte tlačítko myši. Všimněte si, že do ovládacího prvku <xref:System.Windows.Forms.FlowLayoutPanel> jsou vloženy tři <xref:System.Windows.Forms.Button> ovládací prvky.

## <a name="next-steps"></a>Další kroky
 Můžete dosáhnout složitých rozložení pomocí kombinace panelů rozložení a ovládacích prvků. Mezi návrhy pro další zkoumání patří:

- Změňte velikost jednoho z <xref:System.Windows.Forms.Button> ovládacích prvků na větší velikost a poznamenejte si efekt v rozložení.

- Panely rozložení mohou obsahovat další panely rozložení. Experimentujte s vyřazením ovládacího prvku <xref:System.Windows.Forms.TableLayoutPanel> do existujícího ovládacího prvku.

- Ukotvěte ovládací prvek <xref:System.Windows.Forms.FlowLayoutPanel> do nadřazeného formuláře. Změňte velikost formuláře a poznamenejte si efekt v rozložení.

- Nastavte vlastnost <xref:System.Windows.Forms.Control.Visible%2A> jednoho z ovládacích prvků na `false` a Všimněte si, jak <xref:System.Windows.Forms.FlowLayoutPanel> přetéká v reakci.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.FlowLayoutPanel>
- <xref:System.Windows.Forms.TableLayoutPanel>
- [Postupy: Uspořádání ovládacích prvků na Windows Forms s použitím ovládacího prvku TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [Návod: Uspořádání ovládacích prvků ve Windows Forms pomocí zarovnávacích čar](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [Přehled vlastnosti AutoSize](autosize-property-overview.md)
- [Postupy: Vložení ovládacích prvků ve Windows Forms do doku](how-to-dock-controls-on-windows-forms.md)
- [Postupy: Ukotvení ovládacích prvků ve Windows Forms](how-to-anchor-controls-on-windows-forms.md)
- [Návod: Rozvrhování ovládacích prvků Windows Forms s odsazením, okraji a s vlastností AutoSize](windows-forms-controls-padding-autosize.md)
