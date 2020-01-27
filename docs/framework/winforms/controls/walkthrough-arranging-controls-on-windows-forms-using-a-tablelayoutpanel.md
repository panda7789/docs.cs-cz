---
title: Uspořádání ovládacích prvků pomocí kontejneru TableLayoutPanel
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], arranging with TableLayoutPanel
- TableLayoutPanel control [Windows Forms], walkthroughs
- Windows Forms controls, arranging
ms.assetid: d474885e-12cc-4ab7-b997-2a23a643049b
ms.openlocfilehash: 803a56f6416cf3b718890e96cf9f36ae6c4ee471
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740314"
---
# <a name="walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel"></a>Postupy: Uspořádání ovládacích prvků na formuláři Windows s použitím ovládacího prvku TableLayoutPanel

Některé aplikace vyžadují formulář s rozložením, které je uspořádáno správně, protože se změní velikost formuláře nebo se změní velikost obsahu. Pokud potřebujete dynamické rozložení a nechcete zpracovávat události <xref:System.Windows.Forms.Control.Layout> explicitně ve vašem kódu, zvažte použití panelu rozložení.

Ovládací prvek <xref:System.Windows.Forms.FlowLayoutPanel> a ovládací prvek <xref:System.Windows.Forms.TableLayoutPanel> poskytují intuitivní způsoby uspořádání ovládacích prvků ve formuláři. Obě poskytují automatickou, konfigurovatelný možnost pro řízení relativních pozic podřízených ovládacích prvků, které jsou v nich obsažené, a zároveň poskytují funkce dynamického rozložení za běhu, takže mohou změnit velikost a umístění podřízených ovládacích prvků jako rozměry nadřazeného formuláře. mění. Panely rozložení lze vnořovat do panelů rozložení, aby bylo možné provádět realizace sofistikovaných uživatelských rozhraní.

<xref:System.Windows.Forms.FlowLayoutPanel> uspořádá jeho obsah v určitém směru toku: Horizontal nebo Vertical. Jeho obsah lze zabalit z jednoho řádku na další, nebo z jednoho sloupce na další. Alternativně lze jeho obsah oříznout místo zabalení. Další informace naleznete v tématu [Návod: uspořádání ovládacích prvků na model Windows Forms pomocí FlowLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md).

<xref:System.Windows.Forms.TableLayoutPanel> uspořádá jeho obsah do mřížky a poskytne funkce podobné prvku \<tabulky > HTML. Ovládací prvek <xref:System.Windows.Forms.TableLayoutPanel> umožňuje umístit ovládací prvky do rozložení mřížky, aniž by bylo nutné přesně zadat polohu každého jednotlivého ovládacího prvku. Buňky se uspořádají do řádků a sloupců a můžou mít různé velikosti. Buňky lze sloučit mezi řádky a sloupci. Buňky můžou obsahovat cokoli, co formulář může obsahovat a chovat se ve většině dalších hledisek jako kontejnery.

Ovládací prvek <xref:System.Windows.Forms.TableLayoutPanel> také poskytuje funkci proporcionální změny velikosti za běhu, takže vaše rozložení se může bezproblémově měnit, protože velikost formuláře se mění. Díky tomu je ovládací prvek <xref:System.Windows.Forms.TableLayoutPanel> vhodný pro účely, jako jsou formuláře pro zadávání dat a lokalizované aplikace. Další informace najdete v tématu [Návod: Vytvoření formuláře Windows s možností změny velikosti pro zadávání dat](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100)) a [Návod: vytváření lokalizovatelných formulářů Windows](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7k9fa71y(v=vs.100)).

Obecně platí, že byste neměli používat ovládací prvek <xref:System.Windows.Forms.TableLayoutPanel> jako kontejner pro celé rozložení. Použijte ovládací prvky <xref:System.Windows.Forms.TableLayoutPanel> k poskytnutí proporcionálních možností změny velikosti částí rozložení.

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

1. Vytvořte projekt aplikace pro Windows s názvem "TableLayoutPanelExample". Další informace naleznete v tématu [How to: Create a model Windows Forms Application Project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) .

2. Vyberte formulář v **Návrháři formulářů** **Windows** .

## <a name="arranging-controls-in-rows-and-columns"></a>Uspořádání ovládacích prvků v řádcích a sloupcích

Ovládací prvek <xref:System.Windows.Forms.TableLayoutPanel> umožňuje snadno uspořádat ovládací prvky do řádků a sloupců.

#### <a name="to-arrange-controls-in-rows-and-columns-using-a-tablelayoutpanel"></a>Uspořádání ovládacích prvků v řádcích a sloupcích pomocí kontejneru TableLayoutPanel

1. Přetáhněte ovládací prvek <xref:System.Windows.Forms.TableLayoutPanel> z **panelu nástrojů** do formuláře. Všimněte si, že ve výchozím nastavení má ovládací prvek <xref:System.Windows.Forms.TableLayoutPanel> čtyři buňky.

2. Přetáhněte ovládací prvek <xref:System.Windows.Forms.Button> z **panelu nástrojů** do ovládacího prvku <xref:System.Windows.Forms.TableLayoutPanel> a umístěte jej do jedné z buněk. Všimněte si, že <xref:System.Windows.Forms.Button> ovládací prvek je vytvořen v rámci vybrané buňky.

3. Přetáhněte tři další <xref:System.Windows.Forms.Button> ovládací prvky ze **sady nástrojů** do ovládacího prvku <xref:System.Windows.Forms.TableLayoutPanel>, aby každá buňka obsahovala tlačítko.

4. Umožňuje přesunout úchyt svislé velikosti mezi dvěma sloupci a přesunout ho doleva. Všimněte si, že <xref:System.Windows.Forms.Button> ovládací prvky v prvním sloupci mají velikost zmenšenou na menší šířku, zatímco velikost <xref:System.Windows.Forms.Button>ch ovládacích prvků ve druhém sloupci zůstane beze změny.

5. Umožňuje přemístit vertikální úchyt mezi dvěma sloupci a přesunout ho doprava. Všimněte si, že <xref:System.Windows.Forms.Button> ovládací prvky v prvním sloupci se vrátí do původní velikosti, zatímco <xref:System.Windows.Forms.Button> ovládací prvky ve druhém sloupci se přesunou doprava.

6. Chcete-li zobrazit efekt ovládacích prvků na panelu, přesuňte úchyt vodorovné velikosti nahoru a dolů.

## <a name="positioning-controls-within-cells-using-docking-and-anchoring"></a>Umístění ovládacích prvků v buňkách pomocí ukotvení a ukotvení

Chování při ukotvení podřízených ovládacích prvků v <xref:System.Windows.Forms.TableLayoutPanel> se liší od chování v jiných ovládacích prvcích kontejneru. Chování při ukotvení podřízených ovládacích prvků je stejné jako jiné ovládací prvky kontejneru.

#### <a name="positioning-controls-within-cells"></a>Umístění ovládacích prvků v buňkách

1. Vyberte první ovládací prvek <xref:System.Windows.Forms.Button>. Změňte hodnotu vlastnosti <xref:System.Windows.Forms.Control.Dock%2A> na <xref:System.Windows.Forms.DockStyle.Fill>. Všimněte si, že se ovládací prvek <xref:System.Windows.Forms.Button> rozbalí a vyplní jeho buňku.

2. Vyberte jeden z dalších <xref:System.Windows.Forms.Button> ovládacích prvků. Změňte hodnotu vlastnosti <xref:System.Windows.Forms.Control.Anchor%2A> na <xref:System.Windows.Forms.AnchorStyles.Right>. Všimněte si, že je přesunutý tak, aby jeho pravé ohraničení bylo poblíž pravého ohraničení buňky. Vzdálenost mezi ohraničením je součtem vlastnosti <xref:System.Windows.Forms.Control.Margin%2A> ovládacího prvku <xref:System.Windows.Forms.Button> a vlastnosti <xref:System.Windows.Forms.Control.Padding%2A> panelu.

3. Změňte hodnotu vlastnosti <xref:System.Windows.Forms.Control.Anchor%2A> ovládacího prvku <xref:System.Windows.Forms.Button> na <xref:System.Windows.Forms.AnchorStyles.Right> a <xref:System.Windows.Forms.AnchorStyles.Left>. Všimněte si, že ovládací prvek má velikost na šířku buňky, přičemž hodnoty <xref:System.Windows.Forms.Control.Margin%2A> a <xref:System.Windows.Forms.Control.Padding%2A> v úvahu.

4. Opakujte kroky 2 a 3 se styly <xref:System.Windows.Forms.AnchorStyles.Top> a <xref:System.Windows.Forms.AnchorStyles.Bottom>.

## <a name="setting-row-and-column-properties"></a>Nastavení vlastností řádků a sloupců

Jednotlivé vlastnosti řádků a sloupců můžete nastavit pomocí kolekcí <xref:System.Windows.Forms.TableLayoutPanel.RowStyles%2A> a <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A>.

#### <a name="to-set-row-and-column-properties"></a>Nastavení vlastností řádků a sloupců

1. Vyberte ovládací prvek <xref:System.Windows.Forms.TableLayoutPanel> v **Návrhář formulářů**.

2. V oknech **vlastnosti** otevřete kolekci <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> kliknutím na tři tečky (![tlačítko se třemi tečkami (...) v okno Vlastnosti tlačítko sady Visual Studio.](./media/visual-studio-ellipsis-button.png)) vedle položky **sloupce** .

3. Vyberte první sloupec a změňte hodnotu vlastnosti <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> na <xref:System.Windows.Forms.SizeType.AutoSize>. Potvrďte změnu kliknutím na tlačítko **OK** . Všimněte si, že šířka prvního sloupce je zmenšena tak, aby odpovídala ovládacímu prvku <xref:System.Windows.Forms.Button>. Všimněte si také, že šířku sloupce nelze měnit.

4. V okně **vlastnosti** otevřete kolekci <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> a vyberte první sloupec. Změňte hodnotu vlastnosti <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> na <xref:System.Windows.Forms.SizeType.Percent>. Potvrďte změnu kliknutím na tlačítko **OK** . Změňte velikost ovládacího prvku <xref:System.Windows.Forms.TableLayoutPanel> na větší šířku a Všimněte si, že se Šířka prvního sloupce rozšíří. Změňte velikost ovládacího prvku <xref:System.Windows.Forms.TableLayoutPanel> na menší šířku a Všimněte si, že tlačítka v prvním sloupci mají velikost tak, aby odpovídala buňce. Všimněte si také, že šířku sloupce lze měnit.

5. V okně **vlastnosti** otevřete kolekci <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> a vyberte všechny uvedené sloupce. Nastavte hodnotu každé vlastnosti <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> na <xref:System.Windows.Forms.SizeType.Percent>. Potvrďte změnu kliknutím na tlačítko **OK** . Opakujte s kolekcí <xref:System.Windows.Forms.TableLayoutPanel.RowStyles%2A>.

6. Přitáhněte jeden z rohových úchytů pro změnu velikosti a změňte šířku i výšku ovládacího prvku <xref:System.Windows.Forms.TableLayoutPanel>. Všimněte si, že se změní velikost řádků a sloupců při změně velikosti ovládacího prvku <xref:System.Windows.Forms.TableLayoutPanel>. Všimněte si také, že řádky a sloupce lze měnit pomocí vodorovných a svislých úchytů pro změnu velikosti.

## <a name="spanning-rows-and-columns-with-a-control"></a>Pokrývání řádků a sloupců ovládacím prvkem

Ovládací prvek <xref:System.Windows.Forms.TableLayoutPanel> přidá k ovládacím prvkům v době návrhu několik nových vlastností. Dvě z těchto vlastností jsou `RowSpan` a `ColumnSpan`. Tyto vlastnosti můžete použít k vytvoření ovládacího prvku v rozpětí více než jednoho řádku nebo sloupce.

#### <a name="to-span-rows-and-columns-with-a-control"></a>Postup pro rozsah řádků a sloupců pomocí ovládacího prvku

1. Vyberte ovládací prvek <xref:System.Windows.Forms.Button> v prvním řádku a prvním sloupci.

2. V oknech **vlastnosti** změňte hodnotu vlastnosti `ColumnSpan` na **2**. Všimněte si, že ovládací prvek <xref:System.Windows.Forms.Button> vyplní první sloupec a druhý sloupec. Všimněte si také, že byl přidán další řádek, který tuto změnu přizpůsobil.

3. Opakujte krok 2 pro vlastnost `RowSpan`.

## <a name="inserting-controls-by-double-clicking-them-in-the-toolbox"></a>Vložení ovládacích prvků dvojitým kliknutím na ně v sadě nástrojů

Ovládací prvek <xref:System.Windows.Forms.TableLayoutPanel> lze naplnit dvojitým kliknutím na ovládací prvky v **sadě nástrojů**.

#### <a name="to-insert-controls-by-double-clicking-in-the-toolbox"></a>Vložení ovládacích prvků dvojitým kliknutím na panel nástrojů

1. Přetáhněte ovládací prvek <xref:System.Windows.Forms.TableLayoutPanel> z **panelu nástrojů** do formuláře.

2. Dvakrát klikněte na ikonu ovládacího prvku <xref:System.Windows.Forms.Button> v **sadě nástrojů**. Všimněte si, že nový ovládací prvek tlačítko se zobrazí v první buňce ovládacího prvku <xref:System.Windows.Forms.TableLayoutPanel>.

3. Dvakrát klikněte na více ovládacích prvků v **sadě nástrojů**. Všimněte si, že nové ovládací prvky se budou postupně zobrazovat v neobsazených buňkách ovládacího prvku <xref:System.Windows.Forms.TableLayoutPanel>. Všimněte si také, že ovládací prvek <xref:System.Windows.Forms.TableLayoutPanel> se rozbalí a přizpůsobí nové ovládací prvky, pokud nejsou k dispozici žádné otevřené buňky.

## <a name="automatic-handling-of-overflows"></a>Automatické zpracování přetečení

Když vkládáte ovládací prvky do ovládacího prvku <xref:System.Windows.Forms.TableLayoutPanel>, mohou být vyplněné prázdné buňky pro nové ovládací prvky. Ovládací prvek <xref:System.Windows.Forms.TableLayoutPanel> zpracovává tuto situaci automaticky zvýšením počtu buněk.

#### <a name="to-observe-automatic-handling-of-overflows"></a>Sledování automatického zpracování přetečení

1. Pokud v ovládacím prvku <xref:System.Windows.Forms.TableLayoutPanel> stále existují prázdné buňky, pokračujte v vkládání nových ovládacích prvků <xref:System.Windows.Forms.Button>, dokud není ovládací prvek <xref:System.Windows.Forms.TableLayoutPanel> plný.

2. Po zaplnění ovládacího prvku <xref:System.Windows.Forms.TableLayoutPanel> dvakrát klikněte na ikonu <xref:System.Windows.Forms.Button> v **sadě nástrojů** a vložte další ovládací prvek <xref:System.Windows.Forms.Button>. Všimněte si, že ovládací prvek <xref:System.Windows.Forms.TableLayoutPanel> vytvoří nové buňky pro přizpůsobení nového ovládacího prvku. Vložte několik dalších ovládacích prvků a sledujte chování při změně velikosti.

3. Změňte hodnotu vlastnosti <xref:System.Windows.Forms.TableLayoutPanel.GrowStyle%2A> ovládacího prvku <xref:System.Windows.Forms.TableLayoutPanel> na <xref:System.Windows.Forms.TableLayoutPanelGrowStyle.FixedSize>. Dvojitým kliknutím na ikonu <xref:System.Windows.Forms.Button> v **panelu nástrojů** vložte <xref:System.Windows.Forms.Button> ovládací prvky, dokud není ovládací prvek <xref:System.Windows.Forms.TableLayoutPanel> plný. Dvakrát klikněte na ikonu <xref:System.Windows.Forms.Button> znovu v **sadě nástrojů** . Všimněte si, že se zobrazí chybová zpráva od **Návrhář formulářů** informující o tom, že nelze vytvořit další řádky a sloupce.

## <a name="inserting-a-control-by-drawing-its-outline"></a>Vložení ovládacího prvku kreslením jeho obrysu

Ovládací prvek můžete vložit do ovládacího prvku <xref:System.Windows.Forms.TableLayoutPanel> a zadat jeho velikost vykreslením jeho obrysu v buňce.

#### <a name="to-insert-a-control-by-drawing-its-outline"></a>Vložení ovládacího prvku kreslením jeho obrysu

1. Přetáhněte ovládací prvek <xref:System.Windows.Forms.TableLayoutPanel> z **panelu nástrojů** do formuláře.

2. Na **panelu nástrojů**klikněte na ikonu ovládacího prvku <xref:System.Windows.Forms.Button>. Nepřetáhněte ho do formuláře.

3. Přesuňte ukazatel myši nad ovládací prvek <xref:System.Windows.Forms.TableLayoutPanel>. Všimněte si, že se ukazatel změní na vlasovou čáru s připojenou ikonou ovládacího prvku <xref:System.Windows.Forms.Button>.

4. Klikněte a podržte tlačítko myši.

5. Přetažením ukazatele myši nakreslete obrys ovládacího prvku <xref:System.Windows.Forms.Button>. Až budete s velikostí spokojeni, uvolněte tlačítko myši. Všimněte si, že ovládací prvek <xref:System.Windows.Forms.Button> je vytvořen v buňce, ve které jste nakreslili osnovu ovládacího prvku.

## <a name="multiple-controls-within-cells-are-not-permitted"></a>Více ovládacích prvků v buňkách není povoleno.

Ovládací prvek <xref:System.Windows.Forms.TableLayoutPanel> může obsahovat pouze jeden podřízený ovládací prvek na buňku.

#### <a name="to-demonstrate-that-multiple-controls-within-cells-are-not-permitted"></a>Předvedení nedovoleného více ovládacích prvků v buňkách

- Přetáhněte ovládací prvek <xref:System.Windows.Forms.Button> z **panelu nástrojů** do ovládacího prvku <xref:System.Windows.Forms.TableLayoutPanel> a umístěte jej do jedné z obsazených buněk. Všimněte si, že ovládací prvek <xref:System.Windows.Forms.TableLayoutPanel> neumožňuje vyřadit ovládací prvek <xref:System.Windows.Forms.Button> do obsazené buňky.

## <a name="swapping-controls"></a>Výměna ovládacích prvků

Ovládací prvek <xref:System.Windows.Forms.TableLayoutPanel> umožňuje přepínat ovládací prvky, které zabírají dvě různé buňky.

#### <a name="to-swap-controls"></a>Postup při prohození ovládacích prvků

- Přetáhněte jeden z <xref:System.Windows.Forms.Button>ch ovládacích prvků z obsazené buňky do jiné obsazené buňky. Všimněte si, že dva ovládací prvky jsou přesunuty z jedné buňky do druhé.

## <a name="next-steps"></a>Další kroky

Můžete dosáhnout složitých rozložení pomocí kombinace panelů rozložení a ovládacích prvků. Mezi návrhy pro další zkoumání patří:

- Zkuste změnit velikost jednoho z <xref:System.Windows.Forms.Button> ovládacích prvků na větší velikost a poznamenejte si efekt v rozložení.

- Vložte výběr více ovládacích prvků do ovládacího prvku <xref:System.Windows.Forms.TableLayoutPanel> a Všimněte si, jak jsou ovládací prvky vloženy.

- Panely rozložení mohou obsahovat další panely rozložení. Experimentujte s vyřazením ovládacího prvku <xref:System.Windows.Forms.TableLayoutPanel> do existujícího ovládacího prvku.

- Ukotvěte ovládací prvek <xref:System.Windows.Forms.TableLayoutPanel> do nadřazeného formuláře. Změňte velikost formuláře a poznamenejte si efekt v rozložení.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.FlowLayoutPanel>
- <xref:System.Windows.Forms.TableLayoutPanel>
- [Postupy: Uspořádání ovládacích prvků na formuláři Windows Forms s použitím ovládacího prvku FlowLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [Návod: Uspořádání ovládacích prvků ve Windows Forms pomocí zarovnávacích čar](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [Návod: Vytvoření formuláře Windows s možností změny velikosti pro zadávání dat](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100))
- [Návod: vytvoření Lokalizovatelnýho formuláře Windows](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7k9fa71y(v=vs.100))
- [Doporučené postupy pro ovládací prvek TableLayoutPanel](best-practices-for-the-tablelayoutpanel-control.md)
- [Přehled vlastnosti AutoSize](autosize-property-overview.md)
- [Postupy: Vložení ovládacích prvků ve Windows Forms do doku](how-to-dock-controls-on-windows-forms.md)
- [Postupy: Ukotvení ovládacích prvků ve Windows Forms](how-to-anchor-controls-on-windows-forms.md)
- [Návod: Rozvrhování ovládacích prvků Windows Forms s odsazením, okraji a s vlastností AutoSize](windows-forms-controls-padding-autosize.md)
