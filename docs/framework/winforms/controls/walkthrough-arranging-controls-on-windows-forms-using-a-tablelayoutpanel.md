---
title: 'Návod: Uspořádání ovládacích prvků ve Windows Forms s použitím ovládacího prvku TableLayoutPanel'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], arranging with TableLayoutPanel
- TableLayoutPanel control [Windows Forms], walkthroughs
- Windows Forms controls, arranging
ms.assetid: d474885e-12cc-4ab7-b997-2a23a643049b
ms.openlocfilehash: 289a8427540c713758c3f155e72efffe9f3c85bc
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "69666806"
---
# <a name="walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel"></a>Návod: Uspořádání ovládacích prvků ve Windows Forms s použitím ovládacího prvku TableLayoutPanel

Některé aplikace vyžadují formulář s rozložením, které je uspořádáno správně, protože se změní velikost formuláře nebo se změní velikost obsahu. Pokud potřebujete dynamické rozložení a nechcete zpracovávat <xref:System.Windows.Forms.Control.Layout> události explicitně v kódu, zvažte použití panelu rozložení.

<xref:System.Windows.Forms.FlowLayoutPanel> Ovládací prvek <xref:System.Windows.Forms.TableLayoutPanel> a ovládací prvek poskytují intuitivní způsoby uspořádání ovládacích prvků ve formuláři. Obě poskytují automatickou, konfigurovatelný možnost pro řízení relativních pozic podřízených ovládacích prvků, které jsou v nich obsažené, a zároveň poskytují funkce dynamického rozložení za běhu, takže mohou změnit velikost a umístění podřízených ovládacích prvků jako rozměry nadřazeného formuláře. mění. Panely rozložení lze vnořovat do panelů rozložení, aby bylo možné provádět realizace sofistikovaných uživatelských rozhraní.

<xref:System.Windows.Forms.FlowLayoutPanel> Uspořádá obsah v určitém směru toku: vodorovně nebo svisle. Jeho obsah lze zabalit z jednoho řádku na další, nebo z jednoho sloupce na další. Alternativně lze jeho obsah oříznout místo zabalení. Další informace najdete v tématu [Návod: Uspořádání ovládacích prvků na model Windows Forms pomocí FlowLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md).

Uspořádá svůj obsah do mřížky a poskytuje funkce podobné > elementu HTML \<Table. <xref:System.Windows.Forms.TableLayoutPanel> <xref:System.Windows.Forms.TableLayoutPanel> Ovládací prvek umožňuje umístit ovládací prvky do rozložení mřížky bez nutnosti přesně zadat polohu každého jednotlivého ovládacího prvku. Buňky se uspořádají do řádků a sloupců a můžou mít různé velikosti. Buňky lze sloučit mezi řádky a sloupci. Buňky můžou obsahovat cokoli, co formulář může obsahovat a chovat se ve většině dalších hledisek jako kontejnery.

<xref:System.Windows.Forms.TableLayoutPanel> Ovládací prvek také poskytuje funkci proporcionální změny velikosti za běhu, takže rozložení se může změnit plynule, protože se změní velikost formuláře. Díky tomu je <xref:System.Windows.Forms.TableLayoutPanel> ovládací prvek vhodný pro účely, jako jsou formuláře pro zadávání dat a lokalizované aplikace. Další informace najdete v tématu [Návod: Vytvoření formuláře Windows s možností změny velikosti pro zadávání](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100)) dat [a návod: Vytváření lokalizovatelných formulářů](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7k9fa71y(v=vs.100))Windows.

Obecně platí, že byste neměli používat <xref:System.Windows.Forms.TableLayoutPanel> ovládací prvek jako kontejner pro celé rozložení. Ovládací <xref:System.Windows.Forms.TableLayoutPanel> prvky slouží k poskytnutí proporcionálních možností změny velikosti částí rozložení.

Úlohy, které jsou znázorněné v tomto návodu, zahrnují:

- Vytvoření projektu model Windows Forms

- Uspořádání ovládacích prvků v řádcích a sloupcích

- Nastavení vlastností řádků a sloupců

- Pokrývání řádků a sloupců ovládacím prvkem

- Automatické zpracování přetečení

- Vložení ovládacích prvků dvojitým kliknutím na ně v sadě nástrojů

- Vložení ovládacího prvku kreslením jeho obrysu

- Změna přiřazení existujících ovládacích prvků jinému nadřazenému prvku

Až budete hotovi, budete obeznámeni s tím, že role hraje tyto důležité funkce rozložení.

## <a name="creating-the-project"></a>Vytvoření projektu

Prvním krokem je vytvoření projektu a nastavení formuláře.

#### <a name="to-create-the-project"></a>Vytvoření projektu

1. Vytvořte projekt aplikace pro Windows s názvem "TableLayoutPanelExample". Další informace najdete v tématu [jak: Vytvořte projekt](/visualstudio/ide/step-1-create-a-windows-forms-application-project) aplikace model Windows Forms.

2. Vyberte formulář v **Návrháři formulářů** **Windows** .

## <a name="arranging-controls-in-rows-and-columns"></a>Uspořádání ovládacích prvků v řádcích a sloupcích

<xref:System.Windows.Forms.TableLayoutPanel> Ovládací prvek umožňuje snadno uspořádat ovládací prvky do řádků a sloupců.

#### <a name="to-arrange-controls-in-rows-and-columns-using-a-tablelayoutpanel"></a>Uspořádání ovládacích prvků v řádcích a sloupcích pomocí kontejneru TableLayoutPanel

1. Přetáhněte ovládací prvek z **panelu nástrojů** do formuláře. <xref:System.Windows.Forms.TableLayoutPanel> Všimněte si, že ve výchozím nastavení <xref:System.Windows.Forms.TableLayoutPanel> má ovládací prvek čtyři buňky.

2. Přetáhněte ovládací prvek ze <xref:System.Windows.Forms.TableLayoutPanel> **sady nástrojů** do ovládacího prvku a umístěte jej do jedné z buněk. <xref:System.Windows.Forms.Button> Všimněte si, <xref:System.Windows.Forms.Button> že ovládací prvek je vytvořen v rámci vybrané buňky.

3. Přetáhněte tři další <xref:System.Windows.Forms.Button> ovládací prvky ze <xref:System.Windows.Forms.TableLayoutPanel> sady nástrojů do ovládacího prvku tak, aby každá buňka obsahovala tlačítko.

4. Umožňuje přesunout úchyt svislé velikosti mezi dvěma sloupci a přesunout ho doleva. Všimněte si, <xref:System.Windows.Forms.Button> že ovládací prvky v prvním sloupci jsou zmenšeny na menší šířku, zatímco velikost <xref:System.Windows.Forms.Button> ovládacích prvků ve druhém sloupci zůstane beze změny.

5. Umožňuje přemístit vertikální úchyt mezi dvěma sloupci a přesunout ho doprava. Všimněte si, <xref:System.Windows.Forms.Button> že ovládací prvky v prvním sloupci se vrátí do původní velikosti, <xref:System.Windows.Forms.Button> zatímco ovládací prvky ve druhém sloupci se přesunou doprava.

6. Chcete-li zobrazit efekt ovládacích prvků na panelu, přesuňte úchyt vodorovné velikosti nahoru a dolů.

## <a name="positioning-controls-within-cells-using-docking-and-anchoring"></a>Umístění ovládacích prvků v buňkách pomocí ukotvení a ukotvení

Chování při ukotvení podřízených ovládacích prvků v <xref:System.Windows.Forms.TableLayoutPanel> se liší od chování v jiných ovládacích prvcích kontejneru. Chování při ukotvení podřízených ovládacích prvků je stejné jako jiné ovládací prvky kontejneru.

#### <a name="positioning-controls-within-cells"></a>Umístění ovládacích prvků v buňkách

1. Vyberte první <xref:System.Windows.Forms.Button> ovládací prvek. Změňte hodnotu <xref:System.Windows.Forms.Control.Dock%2A> vlastnosti na <xref:System.Windows.Forms.DockStyle.Fill>. Všimněte si, <xref:System.Windows.Forms.Button> že se ovládací prvek rozbalí a vyplní jeho buňku.

2. Vyberte jeden z dalších <xref:System.Windows.Forms.Button> ovládacích prvků. Změňte hodnotu <xref:System.Windows.Forms.Control.Anchor%2A> vlastnosti na <xref:System.Windows.Forms.AnchorStyles.Right>. Všimněte si, že je přesunutý tak, aby jeho pravé ohraničení bylo poblíž pravého ohraničení buňky. Vzdálenost mezi ohraničením je součet <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.Control.Margin%2A> <xref:System.Windows.Forms.Control.Padding%2A> vlastnosti ovládacího prvku a vlastnosti panelu.

3. <xref:System.Windows.Forms.Button> Změňte hodnotu <xref:System.Windows.Forms.Control.Anchor%2A> vlastnosti ovládacího prvku na <xref:System.Windows.Forms.AnchorStyles.Right> a <xref:System.Windows.Forms.AnchorStyles.Left>. Všimněte si, že ovládací prvek má velikost na šířku buňky, přičemž hodnoty a <xref:System.Windows.Forms.Control.Margin%2A> <xref:System.Windows.Forms.Control.Padding%2A> se přijímají v úvahu.

4. Opakujte kroky 2 a 3 s <xref:System.Windows.Forms.AnchorStyles.Top> styly a. <xref:System.Windows.Forms.AnchorStyles.Bottom>

## <a name="setting-row-and-column-properties"></a>Nastavení vlastností řádků a sloupců

Jednotlivé vlastnosti řádků a sloupců můžete nastavit pomocí <xref:System.Windows.Forms.TableLayoutPanel.RowStyles%2A> kolekcí a. <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A>

#### <a name="to-set-row-and-column-properties"></a>Nastavení vlastností řádků a sloupců

1. Vyberte ovládací prvek v **Návrhář formulářů.** <xref:System.Windows.Forms.TableLayoutPanel>

2. V oknech **vlastnosti** otevřete <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> kolekci![kliknutím na tlačítko se třemi tečkami (tři tečky (...) v okno Vlastnosti sady Visual Studio.](./media/visual-studio-ellipsis-button.png)) vedle položky **sloupce** .

3. Vyberte první sloupec a změňte hodnotu <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> vlastnosti na. <xref:System.Windows.Forms.SizeType.AutoSize> Potvrďte změnu kliknutím na tlačítko **OK** . Všimněte si, že šířka prvního sloupce je zmenšena tak, aby <xref:System.Windows.Forms.Button> odpovídala ovládacímu prvku. Všimněte si také, že šířku sloupce nelze měnit.

4. V okně **vlastnosti** otevřete <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> kolekci a vyberte první sloupec. Změňte hodnotu <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> vlastnosti na <xref:System.Windows.Forms.SizeType.Percent>. Potvrďte změnu kliknutím na tlačítko **OK** . Změňte velikost <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku na větší šířku a Všimněte si, že se Šířka prvního sloupce rozšíří. Změňte velikost <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku na menší šířku a Všimněte si, že tlačítka v prvním sloupci mají velikost tak, aby odpovídala buňce. Všimněte si také, že šířku sloupce lze měnit.

5. V okně **vlastnosti** otevřete <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> kolekci a vyberte všechny uvedené sloupce. Nastavte hodnotu každé <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> vlastnosti na <xref:System.Windows.Forms.SizeType.Percent>. Potvrďte změnu kliknutím na tlačítko **OK** . Opakujte s <xref:System.Windows.Forms.TableLayoutPanel.RowStyles%2A> kolekcí.

6. Přitáhněte jeden z rohových úchytů změny velikosti a změňte šířku i výšku <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku. Všimněte si, že při změně velikosti <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku se změní velikost řádků a sloupců. Všimněte si také, že řádky a sloupce lze měnit pomocí vodorovných a svislých úchytů pro změnu velikosti.

## <a name="spanning-rows-and-columns-with-a-control"></a>Pokrývání řádků a sloupců ovládacím prvkem

<xref:System.Windows.Forms.TableLayoutPanel> Ovládací prvek přidá k ovládacím prvkům v době návrhu několik nových vlastností. Dvě z těchto vlastností jsou `RowSpan` a `ColumnSpan`. Tyto vlastnosti můžete použít k vytvoření ovládacího prvku v rozpětí více než jednoho řádku nebo sloupce.

#### <a name="to-span-rows-and-columns-with-a-control"></a>Postup pro rozsah řádků a sloupců pomocí ovládacího prvku

1. <xref:System.Windows.Forms.Button> Vyberte ovládací prvek v prvním řádku a prvním sloupci.

2. V oknech **vlastnosti** změňte hodnotu `ColumnSpan` vlastnosti na **2**. Všimněte si, <xref:System.Windows.Forms.Button> že ovládací prvek vyplní první sloupec a druhý sloupec. Všimněte si také, že byl přidán další řádek, který tuto změnu přizpůsobil.

3. Opakujte krok 2 pro `RowSpan` vlastnost.

## <a name="inserting-controls-by-double-clicking-them-in-the-toolbox"></a>Vložení ovládacích prvků dvojitým kliknutím na ně v sadě nástrojů

<xref:System.Windows.Forms.TableLayoutPanel> Ovládací prvek lze naplnit dvojitým kliknutím na ovládací prvky v **sadě nástrojů**.

#### <a name="to-insert-controls-by-double-clicking-in-the-toolbox"></a>Vložení ovládacích prvků dvojitým kliknutím na panel nástrojů

1. Přetáhněte ovládací prvek z **panelu nástrojů** do formuláře. <xref:System.Windows.Forms.TableLayoutPanel>

2. Dvakrát klikněte <xref:System.Windows.Forms.Button> na ikonu ovládacího prvku v **sadě nástrojů**. Všimněte si, že nový ovládací prvek tlačítko se <xref:System.Windows.Forms.TableLayoutPanel> zobrazí v první buňce ovládacího prvku.

3. Dvakrát klikněte na více ovládacích prvků v **sadě nástrojů**. Všimněte si, že nové ovládací prvky se budou postupně <xref:System.Windows.Forms.TableLayoutPanel> zobrazovat v neobsazených buňkách ovládacího prvku. Všimněte si také, <xref:System.Windows.Forms.TableLayoutPanel> že se ovládací prvek rozbalí a přizpůsobí nové ovládací prvky, pokud nejsou k dispozici žádné otevřené buňky.

## <a name="automatic-handling-of-overflows"></a>Automatické zpracování přetečení

Když vkládáte ovládací prvky do <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku, můžete vyprázdnit prázdné buňky pro nové ovládací prvky. <xref:System.Windows.Forms.TableLayoutPanel> Ovládací prvek zpracovává tuto situaci automaticky zvýšením počtu buněk.

#### <a name="to-observe-automatic-handling-of-overflows"></a>Sledování automatického zpracování přetečení

1. Pokud v <xref:System.Windows.Forms.TableLayoutPanel> ovládacím prvku stále existují prázdné buňky, pokračujte v vkládání nových <xref:System.Windows.Forms.Button> ovládacích prvků, <xref:System.Windows.Forms.TableLayoutPanel> dokud není ovládací prvek plný.

2. Jakmile je <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.Button> ovládací prvek plný, dvakrát klikněte na ikonu v **sadě nástrojů** a vložte další ovládací prvek. <xref:System.Windows.Forms.TableLayoutPanel> Všimněte si, <xref:System.Windows.Forms.TableLayoutPanel> že ovládací prvek vytvoří nové buňky pro přizpůsobení nového ovládacího prvku. Vložte několik dalších ovládacích prvků a sledujte chování při změně velikosti.

3. Změňte hodnotu <xref:System.Windows.Forms.TableLayoutPanel> <xref:System.Windows.Forms.TableLayoutPanel.GrowStyle%2A> vlastnosti ovládacího prvku na <xref:System.Windows.Forms.TableLayoutPanelGrowStyle.FixedSize>. Dvojitým kliknutím <xref:System.Windows.Forms.Button> na ikonu v **panelu nástrojů** <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.TableLayoutPanel> vložte ovládací prvky, dokud není ovládací prvek plný. Dvakrát klikněte <xref:System.Windows.Forms.Button> na ikonu na **panelu nástrojů** . Všimněte si, že se zobrazí chybová zpráva od **Návrhář formulářů** informující o tom, že nelze vytvořit další řádky a sloupce.

## <a name="inserting-a-control-by-drawing-its-outline"></a>Vložení ovládacího prvku kreslením jeho obrysu

Ovládací prvek můžete vložit do <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku a zadat jeho velikost vykreslením jeho obrysu v buňce.

#### <a name="to-insert-a-control-by-drawing-its-outline"></a>Vložení ovládacího prvku kreslením jeho obrysu

1. Přetáhněte ovládací prvek z **panelu nástrojů** do formuláře. <xref:System.Windows.Forms.TableLayoutPanel>

2. Na **panelu nástrojů**klikněte <xref:System.Windows.Forms.Button> na ikonu ovládacího prvku. Nepřetáhněte ho do formuláře.

3. Přesuňte ukazatel myši nad <xref:System.Windows.Forms.TableLayoutPanel> ovládací prvek. Všimněte si, že se ukazatel změní na vlasovou <xref:System.Windows.Forms.Button> čáru s připojenou ikonou ovládacího prvku.

4. Klikněte a podržte tlačítko myši.

5. Přetažením ukazatele myši nakreslete obrys <xref:System.Windows.Forms.Button> ovládacího prvku. Až budete s velikostí spokojeni, uvolněte tlačítko myši. Všimněte si, <xref:System.Windows.Forms.Button> že ovládací prvek je vytvořen v buňce, ve které jste nakreslili osnovu ovládacího prvku.

## <a name="multiple-controls-within-cells-are-not-permitted"></a>Více ovládacích prvků v buňkách není povoleno.

<xref:System.Windows.Forms.TableLayoutPanel> Ovládací prvek může obsahovat pouze jeden podřízený ovládací prvek na buňku.

#### <a name="to-demonstrate-that-multiple-controls-within-cells-are-not-permitted"></a>Předvedení nedovoleného více ovládacích prvků v buňkách

- Přetáhněte ovládací prvek ze <xref:System.Windows.Forms.TableLayoutPanel> **sady nástrojů** do ovládacího prvku a umístěte jej do jedné z obsazených buněk. <xref:System.Windows.Forms.Button> Všimněte si, <xref:System.Windows.Forms.TableLayoutPanel> že ovládací prvek neumožňuje <xref:System.Windows.Forms.Button> odpustit ovládací prvek do obsazené buňky.

## <a name="swapping-controls"></a>Výměna ovládacích prvků

<xref:System.Windows.Forms.TableLayoutPanel> Ovládací prvek umožňuje přepnout ovládací prvky, které zabírají dvě různé buňky.

#### <a name="to-swap-controls"></a>Postup při prohození ovládacích prvků

- Přetáhněte jeden z <xref:System.Windows.Forms.Button> ovládacích prvků z obsazené buňky na jinou obsazenou buňku. Všimněte si, že dva ovládací prvky jsou přesunuty z jedné buňky do druhé.

## <a name="next-steps"></a>Další kroky

Můžete dosáhnout složitých rozložení pomocí kombinace panelů rozložení a ovládacích prvků. Mezi návrhy pro další zkoumání patří:

- Zkuste změnit velikost jednoho z <xref:System.Windows.Forms.Button> ovládacích prvků na větší velikost a poznamenejte si efekt v rozložení.

- Vložte do <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku Výběr více ovládacích prvků a Všimněte si, jak jsou ovládací prvky vloženy.

- Panely rozložení mohou obsahovat další panely rozložení. Experimentujte s vyřazením <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku do existujícího ovládacího prvku.

- <xref:System.Windows.Forms.TableLayoutPanel> Ukotvěte ovládací prvek do nadřazeného formuláře. Změňte velikost formuláře a poznamenejte si efekt v rozložení.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.FlowLayoutPanel>
- <xref:System.Windows.Forms.TableLayoutPanel>
- [Návod: Uspořádání ovládacích prvků na model Windows Forms pomocí FlowLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [Návod: Uspořádání ovládacích prvků na model Windows Forms pomocí zarovnávacím čárám](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [Uživatelské prostředí systému Microsoft Windows, oficiální pokyny pro vývojáře a návrháře uživatelského rozhraní. Redmond, WA: Microsoft Press, 1999. (USBN: 0-7356-0566-1)](https://www.microsoft.com/mspress/southpacific/books/book11588.htm)
- [Návod: Vytvoření formuláře Windows s možností změny velikosti pro zadávání dat](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100))
- [Návod: Vytváření lokalizovatelných formulářů Windows](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7k9fa71y(v=vs.100))
- [Doporučené postupy pro ovládací prvek TableLayoutPanel](best-practices-for-the-tablelayoutpanel-control.md)
- [Přehled vlastnosti AutoSize](autosize-property-overview.md)
- [Postupy: Ukotvit ovládací prvky na model Windows Forms](how-to-dock-controls-on-windows-forms.md)
- [Postupy: Ovládací prvky ukotvení na model Windows Forms](how-to-anchor-controls-on-windows-forms.md)
- [Návod: Rozložení model Windows Forms ovládacích prvků s odsazením, okraji a vlastností AutoSize](windows-forms-controls-padding-autosize.md)
