---
title: Uspořádání ovládacích prvků pomocí FlowLayoutPanel
description: Naučte se používat ovládací prvek FlowLayoutPanel a ovládací prvek TableLayoutPanel k poskytnutí intuitivních způsobů uspořádání ovládacích prvků v projektu model Windows Forms.
ms.date: 03/30/2017
helpviewer_keywords:
- FlowLayoutPanel control [Windows Forms], walkthroughs
- Windows Forms controls, arranging
- controls [Windows Forms], arranging with FlowLayoutPanel
- layout [Windows Forms], walkthroughs
ms.assetid: a1744323-0316-49c2-992e-ebfc0a976b85
ms.openlocfilehash: efcb38275be7b0cf94afb6b68aa139876f7cf5fd
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619283"
---
# <a name="walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel"></a>Postupy: Uspořádání ovládacích prvků na formuláři Windows s použitím ovládacího prvku FlowLayoutPanel

Některé aplikace vyžadují formulář s rozložením, které je uspořádáno správně, protože se změní velikost formuláře nebo se změní velikost obsahu. Pokud potřebujete dynamické rozložení a nechcete zpracovávat <xref:System.Windows.Forms.Control.Layout> události explicitně v kódu, zvažte použití panelu rozložení.

<xref:System.Windows.Forms.FlowLayoutPanel>Ovládací prvek a <xref:System.Windows.Forms.TableLayoutPanel> ovládací prvek poskytují intuitivní způsoby uspořádání ovládacích prvků ve formuláři. Obě poskytují automatickou, konfigurovatelný možnost pro řízení relativních pozic podřízených ovládacích prvků, které jsou v nich obsažené, a v době běhu poskytují funkce dynamického rozložení, takže mohou změnit velikost podřízených ovládacích prvků, aby se změnily rozměry nadřazeného formuláře. Panely rozložení lze vnořovat do panelů rozložení, aby bylo možné provádět realizace sofistikovaných uživatelských rozhraní.

<xref:System.Windows.Forms.TableLayoutPanel>Uspořádá svůj obsah do mřížky a poskytne jim podobné funkce jako HTML \<table> element. Buňky se uspořádají do řádků a sloupců a můžou mít různé velikosti. Další informace naleznete v tématu [Návod: uspořádání ovládacích prvků na model Windows Forms pomocí kontejneru TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).

<xref:System.Windows.Forms.FlowLayoutPanel>Uspořádá obsah v určitém směru toku: vodorovně nebo svisle. Jeho obsah lze zabalit z jednoho řádku na další, nebo z jednoho sloupce na další. Alternativně lze jeho obsah oříznout místo zabalení. Úlohy, které jsou znázorněné v tomto návodu, zahrnují:

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

1. V aplikaci Visual Studio vytvořte projekt aplikace pro systém Windows s názvem "FlowLayoutPanelExample" (**soubor**  >  **Nový**  >  **projekt**  >  **Visual C#** nebo **Visual Basic**  >  **klasický Desktop**  >  **model Windows Forms aplikace**).

2. V **Návrháři formulářů**vyberte formulář.

## <a name="arranging-controls-horizontally-and-vertically"></a>Uspořádání ovládacích prvků vodorovně a svisle
 <xref:System.Windows.Forms.FlowLayoutPanel>Ovládací prvek umožňuje umístit ovládací prvky do řádků nebo sloupců bez nutnosti přesně zadat polohu každého jednotlivého ovládacího prvku.

 <xref:System.Windows.Forms.FlowLayoutPanel>Ovládací prvek může změnit velikost nebo přesměrovat své podřízené ovládací prvky jako rozměry změny nadřazeného formuláře.

### <a name="to-arrange-controls-horizontally-and-vertically-using-a-flowlayoutpanel"></a>Uspořádání ovládacích prvků vodorovně a svisle pomocí FlowLayoutPanel

1. Přetáhněte <xref:System.Windows.Forms.FlowLayoutPanel> ovládací prvek z **panelu nástrojů** do formuláře.

2. Přetáhněte <xref:System.Windows.Forms.Button> ovládací prvek ze **sady nástrojů** na <xref:System.Windows.Forms.FlowLayoutPanel> . Všimněte si, že je automaticky přesunut do levého horního rohu <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku.

3. Přetáhněte jiný <xref:System.Windows.Forms.Button> ovládací prvek ze **sady nástrojů** do <xref:System.Windows.Forms.FlowLayoutPanel> . Všimněte si, že <xref:System.Windows.Forms.Button> ovládací prvek je automaticky přesunut na pozici vedle prvního <xref:System.Windows.Forms.Button> ovládacího prvku. Pokud <xref:System.Windows.Forms.FlowLayoutPanel> je příliš úzký, aby se dva ovládací prvky vešly na stejný řádek, nový <xref:System.Windows.Forms.Button> ovládací prvek se automaticky přesune na další řádek.

4. Přetáhněte několik dalších <xref:System.Windows.Forms.Button> ovládacích prvků ze **sady nástrojů** do <xref:System.Windows.Forms.FlowLayoutPanel> . Pokračujte v umísťování <xref:System.Windows.Forms.Button> ovládacích prvků, dokud jeden řádek nezalomí do dalšího řádku.

5. Změňte hodnotu <xref:System.Windows.Forms.FlowLayoutPanel> vlastnosti ovládacího prvku <xref:System.Windows.Forms.FlowLayoutPanel.WrapContents%2A> na `false` . Všimněte si, že podřízené ovládací prvky již nejsou předávány dalšímu řádku. Místo toho jsou přesunuty do prvního řádku a oříznuty.

6. Změňte hodnotu <xref:System.Windows.Forms.FlowLayoutPanel> vlastnosti ovládacího prvku <xref:System.Windows.Forms.FlowLayoutPanel.WrapContents%2A> na `true` . Všimněte si, že podřízené ovládací prvky se znovu zalomí na další řádek.

7. Zmenšete šířku <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku, dokud nebudou všechny <xref:System.Windows.Forms.Button> ovládací prvky přesunuty do prvního sloupce.

8. Zvětšete šířku <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku, dokud <xref:System.Windows.Forms.Button> nebudou všechny ovládací prvky přesunuty do prvního řádku. Možná budete muset změnit velikost formuláře, aby odpovídal větší šířce.

## <a name="changing-flow-direction"></a>Změna směru toku
 <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>Vlastnost umožňuje změnit směr, ve kterém jsou ovládací prvky uspořádány. Můžete uspořádat podřízené ovládací prvky zleva doprava, zprava doleva, shora dolů nebo zdola nahoru.

### <a name="to-change-the-flow-direction-in-a-flowlayoutpanel"></a>Změna směru toku v kontejneru FlowLayoutPanel

1. Změňte hodnotu <xref:System.Windows.Forms.FlowLayoutPanel> vlastnosti ovládacího prvku <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> na <xref:System.Windows.Forms.FlowDirection.TopDown> . Všimněte si, že podřízené ovládací prvky jsou přeuspořádány do jednoho nebo více sloupců v závislosti na výšce ovládacího prvku.

2. Změňte velikost <xref:System.Windows.Forms.FlowLayoutPanel> tak, aby její výška byla kratší než sloupec <xref:System.Windows.Forms.Button> ovládacích prvků. Všimněte si, že <xref:System.Windows.Forms.FlowLayoutPanel> přeuspořádání podřízených ovládacích prvků na tok do dalšího sloupce. Pokračujte v Zmenšení výšky a Všimněte si, že podřízené ovládací prvky přecházejí do po sobě jdoucích sloupců. Změňte hodnotu <xref:System.Windows.Forms.FlowLayoutPanel> vlastnosti ovládacího prvku <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> na <xref:System.Windows.Forms.FlowDirection.RightToLeft> . Všimněte si, že pozice podřízených ovládacích prvků jsou obráceny. Sledujte rozložení při změně hodnoty <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> vlastnosti na <xref:System.Windows.Forms.FlowDirection.BottomUp> .

## <a name="inserting-flow-breaks"></a>Vkládání konců toků
 <xref:System.Windows.Forms.FlowLayoutPanel>Ovládací prvek poskytuje vlastnost FlowBreak svým podřízeným ovládacím prvkům. Nastavením hodnoty vlastnosti FlowBreak dojde k tomu `true` , že <xref:System.Windows.Forms.FlowLayoutPanel> ovládací prvek přestane rozvádět ovládací prvky v aktuálním směru toku a zabalit je do dalšího řádku nebo sloupce.

### <a name="to-insert-flow-breaks"></a>Vložení konců toků

1. Změňte hodnotu <xref:System.Windows.Forms.FlowLayoutPanel> vlastnosti ovládacího prvku <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> na <xref:System.Windows.Forms.FlowDirection.TopDown> .

2. Vyberte jeden z <xref:System.Windows.Forms.Button> ovládacích prvků uprostřed sloupce úplně vlevo.

3. Nastavte hodnotu <xref:System.Windows.Forms.Button> vlastnosti FlowBreak ovládacího prvku na `true` . Všimněte si, že sloupec je porušený a ovládací prvky, které následují pod vybraným <xref:System.Windows.Forms.Button> tokem, do dalšího sloupce. Nastavte hodnotu <xref:System.Windows.Forms.Button> vlastnosti FlowBreak ovládacího prvku na hodnotu, chcete-li se `false` vrátit k původnímu chování.

## <a name="positioning-controls-using-docking-and-anchoring"></a>Umístění ovládacích prvků pomocí ukotvení a ukotvení
 Chování při ukotvení a ukotvení podřízených ovládacích prvků se liší od chování v jiných ovládacích prvcích kontejneru. Ukotvení i ukotvení jsou relativní vzhledem k největšímu ovládacímu prvku ve směru toku.

### <a name="to-position-controls-using-docking-and-anchoring"></a>Chcete-li umístit ovládací prvky pomocí ukotvení a ukotvení

1. Zvětšete velikost, <xref:System.Windows.Forms.FlowLayoutPanel> dokud <xref:System.Windows.Forms.Button> ovládací prvky nebudou uspořádány do sloupce.

2. Vyberte <xref:System.Windows.Forms.Button> ovládací prvek nejvyšší úrovně. Zvětšete svou šířku tak, aby byla přibližně dvojnásobná, jako ostatní <xref:System.Windows.Forms.Button> ovládací prvky.

3. Vyberte druhý <xref:System.Windows.Forms.Button> ovládací prvek. Změňte hodnotu <xref:System.Windows.Forms.Control.Anchor%2A> vlastnosti na <xref:System.Windows.Forms.AnchorStyles.Right> . Všimněte si, že je přesunutý, takže jeho pravé ohraničení je zarovnáno s <xref:System.Windows.Forms.Button> pravým ohraničením prvního ovládacího prvku.

4. Změňte hodnotu <xref:System.Windows.Forms.Control.Anchor%2A> vlastnosti na <xref:System.Windows.Forms.AnchorStyles.Right> a <xref:System.Windows.Forms.AnchorStyles.Left> . Všimněte si, že má velikost na stejnou šířku jako první <xref:System.Windows.Forms.Button> ovládací prvek.

5. Vyberte třetí <xref:System.Windows.Forms.Button> ovládací prvek. Změňte hodnotu <xref:System.Windows.Forms.Control.Dock%2A> vlastnosti na <xref:System.Windows.Forms.DockStyle.Fill> . Všimněte si, že má velikost na stejnou šířku jako první <xref:System.Windows.Forms.Button> ovládací prvek.

## <a name="arranging-controls-using-padding-and-margins"></a>Uspořádání ovládacích prvků pomocí odsazení a okrajů
 Můžete také uspořádat ovládací prvky v <xref:System.Windows.Forms.FlowLayoutPanel> ovládacím prvku změnou <xref:System.Windows.Forms.Control.Padding%2A> <xref:System.Windows.Forms.Control.Margin%2A> vlastností a.

 <xref:System.Windows.Forms.Control.Padding%2A>Vlastnost umožňuje řídit umístění ovládacích prvků v <xref:System.Windows.Forms.FlowLayoutPanel> buňce ovládacího prvku. Určuje mezery mezi podřízenými ovládacími prvky a <xref:System.Windows.Forms.FlowLayoutPanel> ohraničením ovládacího prvku.

 <xref:System.Windows.Forms.Control.Margin%2A>Vlastnost umožňuje řídit mezery mezi ovládacími prvky.

### <a name="to-arrange-controls-using-the-padding-and-margin-properties"></a>Uspořádání ovládacích prvků pomocí vlastností odsazení a okraj

1. Změňte hodnotu <xref:System.Windows.Forms.FlowLayoutPanel> vlastnosti ovládacího prvku <xref:System.Windows.Forms.Control.Dock%2A> na <xref:System.Windows.Forms.DockStyle.Fill> . Je-li formulář dostatečně velký, <xref:System.Windows.Forms.Button> ovládací prvky budou přesunuty do prvního sloupce <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku.

2. <xref:System.Windows.Forms.FlowLayoutPanel> <xref:System.Windows.Forms.Control.Padding%2A> Rozbalením <xref:System.Windows.Forms.Control.Padding%2A> položky v okně **vlastnosti** a nastavením <xref:System.Windows.Forms.Padding.All%2A> vlastnosti na hodnotu **20**změňte hodnotu vlastnosti ovládacího prvku. Další informace naleznete v tématu [Návod: rozvržení model Windows Forms ovládacích prvků s odsazením, okraji a vlastností AutoSize](windows-forms-controls-padding-autosize.md). Všimněte si, že podřízené ovládací prvky jsou přesunuty směrem do středu <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku. Zvýšená hodnota vlastnosti přenáší <xref:System.Windows.Forms.Control.Padding%2A> podřízené ovládací prvky pryč z <xref:System.Windows.Forms.FlowLayoutPanel> ohraničení ovládacího prvku.

3. Vyberte všechny <xref:System.Windows.Forms.Button> ovládací prvky v <xref:System.Windows.Forms.FlowLayoutPanel> a nastavte hodnotu <xref:System.Windows.Forms.Control.Margin%2A> vlastnosti na **20**. Všimněte si, že mezery mezi <xref:System.Windows.Forms.Button> ovládacími prvky se zvyšují, takže se dále od sebe přesunou. Možná budete muset změnit velikost <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku tak, aby se zobrazily všechny podřízené ovládací prvky.

## <a name="inserting-controls-by-double-clicking-them-in-the-toolbox"></a>Vložení ovládacích prvků dvojitým kliknutím na ně v sadě nástrojů
 Ovládací prvek lze naplnit <xref:System.Windows.Forms.FlowLayoutPanel> dvojitým kliknutím na ovládací prvky v **sadě nástrojů**.

### <a name="to-insert-controls-by-double-clicking-in-the-toolbox"></a>Vložení ovládacích prvků dvojitým kliknutím na panel nástrojů

1. Dvakrát klikněte na <xref:System.Windows.Forms.Button> ikonu ovládacího prvku v **sadě nástrojů**. Všimněte si, že <xref:System.Windows.Forms.Button> v ovládacím prvku se zobrazí nový ovládací prvek <xref:System.Windows.Forms.FlowLayoutPanel> .

2. Dvakrát klikněte na více ovládacích prvků v **sadě nástrojů**. Všimněte si, že nové ovládací prvky se v <xref:System.Windows.Forms.FlowLayoutPanel> ovládacím prvku zobrazí postupně.

## <a name="inserting-a-control-by-drawing-its-outline"></a>Vložení ovládacího prvku kreslením jeho obrysu
 Ovládací prvek můžete vložit do <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku a zadat jeho velikost vykreslením jeho obrysu v buňce.

### <a name="to-insert-a-control-by-drawing-its-outline"></a>Vložení ovládacího prvku kreslením jeho obrysu

1. Na **panelu nástrojů**klikněte na <xref:System.Windows.Forms.Button> ikonu ovládacího prvku. Nepřetáhněte ho do formuláře.

2. Přesuňte ukazatel myši nad <xref:System.Windows.Forms.FlowLayoutPanel> ovládací prvek. Všimněte si, že se ukazatel změní na vlasovou čáru s <xref:System.Windows.Forms.Button> připojenou ikonou ovládacího prvku.

3. Klikněte a podržte tlačítko myši.

4. Přetažením ukazatele myši nakreslete obrys <xref:System.Windows.Forms.Button> ovládacího prvku. Až budete s velikostí spokojeni, uvolněte tlačítko myši. Všimněte si, že <xref:System.Windows.Forms.Button> ovládací prvek je vytvořen v dalším otevřeném umístění <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku.

## <a name="inserting-controls-using-the-insertion-bar"></a>Vložení ovládacích prvků pomocí panelu vložení
 Ovládací prvky lze vložit na konkrétní pozici v <xref:System.Windows.Forms.FlowLayoutPanel> ovládacím prvku. Při přetažení ovládacího prvku do <xref:System.Windows.Forms.FlowLayoutPanel> klientské oblasti ovládacího prvku se zobrazí panel vložení, který označuje, kam bude ovládací prvek vložen.

### <a name="to-insert-a-control-using-the-caret"></a>Vložení ovládacího prvku pomocí stříšky

1. Přetáhněte <xref:System.Windows.Forms.Button> ovládací prvek z **panelu nástrojů** do <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku a najeďte na místo mezi dvěma <xref:System.Windows.Forms.Button> ovládacími prvky. Všimněte si, že je vykreslen panel vložení, který označuje, kde <xref:System.Windows.Forms.Button> bude umístěn při jeho přetažení do <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku. Před vyřazením nového <xref:System.Windows.Forms.Button> ovládacího prvku do <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku přesuňte ukazatel myši v okolí a sledujte, jak se panel vložení přesouvá.

2. Nový <xref:System.Windows.Forms.Button> ovládací prvek přetáhněte do <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku. Všimněte si, že nový <xref:System.Windows.Forms.Button> ovládací prvek není zarovnán s ostatními, protože jeho <xref:System.Windows.Forms.Control.Margin%2A> vlastnost má jinou hodnotu.

## <a name="reassigning-existing-controls-to-a-different-parent"></a>Změna přiřazení existujících ovládacích prvků jinému nadřazenému prvku
 Ovládací prvky, které existují na formuláři, můžete přiřadit novému <xref:System.Windows.Forms.FlowLayoutPanel> ovládacímu prvku.

### <a name="to-reparent-existing-controls"></a>Jak znovu zařadit existující ovládací prvky

1. Přetáhněte tři <xref:System.Windows.Forms.Button> ovládací prvky z **panelu nástrojů** do formuláře. Umístěte je blízko k sobě, ale nechte je nezarovnané.

2. Na **panelu nástrojů**klikněte na <xref:System.Windows.Forms.FlowLayoutPanel> ikonu ovládacího prvku. Nepřetáhněte ho do formuláře.

3. Přesuňte ukazatel myši blízko k třem <xref:System.Windows.Forms.Button> ovládacím prvkům. Všimněte si, že se ukazatel změní na vlasovou čáru s <xref:System.Windows.Forms.FlowLayoutPanel> připojenou ikonou ovládacího prvku.

4. Klikněte a podržte tlačítko myši.

5. Přetažením ukazatele myši nakreslete obrys <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku. Vykreslete obrys kolem tří <xref:System.Windows.Forms.Button> ovládacích prvků.

6. Uvolněte tlačítko myši. Všimněte si, že tři <xref:System.Windows.Forms.Button> ovládací prvky jsou vloženy do <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku.

## <a name="next-steps"></a>Další kroky
 Můžete dosáhnout složitých rozložení pomocí kombinace panelů rozložení a ovládacích prvků. Mezi návrhy pro další zkoumání patří:

- Změňte velikost jednoho z <xref:System.Windows.Forms.Button> ovládacích prvků na větší velikost a poznamenejte si efekt v rozložení.

- Panely rozložení mohou obsahovat další panely rozložení. Experimentujte s vyřazením <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku do existujícího ovládacího prvku.

- Ukotvěte <xref:System.Windows.Forms.FlowLayoutPanel> ovládací prvek do nadřazeného formuláře. Změňte velikost formuláře a poznamenejte si efekt v rozložení.

- Nastavte <xref:System.Windows.Forms.Control.Visible%2A> vlastnost jednoho z ovládacích prvků na `false` a poznamenejte si, jak <xref:System.Windows.Forms.FlowLayoutPanel> probíhá přetečení v reakci.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.FlowLayoutPanel>
- <xref:System.Windows.Forms.TableLayoutPanel>
- [Postupy: Uspořádání ovládacích prvků na Windows Forms s použitím ovládacího prvku TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [Návod: Uspořádání ovládacích prvků ve Windows Forms pomocí zarovnávacích čar](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [Přehled vlastnosti AutoSize](autosize-property-overview.md)
- [Postupy: Vložení ovládacích prvků ve Windows Forms do doku](how-to-dock-controls-on-windows-forms.md)
- [Postupy: Ukotvení ovládacích prvků ve Windows Forms](how-to-anchor-controls-on-windows-forms.md)
- [Návod: Rozvrhování ovládacích prvků Windows Forms s odsazením, okraji a s vlastností AutoSize](windows-forms-controls-padding-autosize.md)
