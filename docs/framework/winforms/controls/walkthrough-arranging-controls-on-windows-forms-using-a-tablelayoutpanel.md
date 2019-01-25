---
title: 'Průvodce: Uspořádání ovládacích prvků na formuláři Windows s použitím ovládacího prvku TableLayoutPanel'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], arranging with TableLayoutPanel
- TableLayoutPanel control [Windows Forms], walkthroughs
- Windows Forms controls, arranging
ms.assetid: d474885e-12cc-4ab7-b997-2a23a643049b
ms.openlocfilehash: d058fd43649b8096ce2a65d8537cf4b663f58594
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54585416"
---
# <a name="walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel"></a>Průvodce: Uspořádání ovládacích prvků na formuláři Windows s použitím ovládacího prvku TableLayoutPanel
Některé aplikace vyžadují formulář pomocí rozložení, který uspořádá samotné správně při změně velikosti formuláře, nebo jako obsah změnit velikost. Pokud potřebujete dynamické rozložení a nechcete zpracovat <xref:System.Windows.Forms.Control.Layout> události explicitně v kódu, zvažte použití panelu rozložení.  
  
 <xref:System.Windows.Forms.FlowLayoutPanel> Ovládacího prvku a <xref:System.Windows.Forms.TableLayoutPanel> řízení poskytují intuitivní způsoby, jak uspořádat ovládací prvky na formuláři. Umožňují automatické, konfigurovatelné možnosti řízení relativní pozice podřízených ovládacích prvků v nich obsažené, a obě získáte funkce dynamické rozložení v době běhu, aby jejich velikost a umístění podřízených ovládacích prvků jako dimenze nadřazený formulář Změňte. Panely rozložení může být vnořena do panely rozložení, aby realizace propracovaná uživatelská rozhraní.  
  
 <xref:System.Windows.Forms.FlowLayoutPanel> Uspořádá jeho obsah v konkrétní směr: vodorovný nebo svislý. Dá zabalit obsah z jednoho řádku na další nebo z jednoho sloupce na další. Alternativně můžete místo oříznutí jeho obsah zabalena. Další informace najdete v tématu [názorný postup: Uspořádání ovládacích prvků na formuláři Windows s použitím ovládacího prvku FlowLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md).  
  
 <xref:System.Windows.Forms.TableLayoutPanel> Uspořádá její obsah do mřížky, poskytuje funkce podobné HTML \<tabulky > element. <xref:System.Windows.Forms.TableLayoutPanel> Ovládací prvek umožňuje umístit ovládací prvky v případě rozložení mřížky, aniž by bylo potřeba přesně určit umístění jednotlivých ovládacích prvků. Jeho buňky jsou uspořádány do řádků a sloupců, a ty mají různé velikosti. Sloučením buněk mezi řádky a sloupce. Buňky může obsahovat cokoli, formulář může obsahovat a chovat ve většině ostatních ohledech jako kontejnery.  
  
 <xref:System.Windows.Forms.TableLayoutPanel> Řízení také poskytuje přímo úměrná velikosti funkce v době běhu, takže rozložení můžete plynule změnit při změně velikosti formuláře. Díky tomu <xref:System.Windows.Forms.TableLayoutPanel> ovládací prvek vhodná pro účely, jako je formulářích pro zadávání dat a lokalizovaných aplikací. Další informace najdete v tématu [názorný postup: Vytvoření formuláře Windows s možností změny velikosti pro zadávání dat](https://msdn.microsoft.com/library/e193b4fc-912a-4917-b036-b76c7a6f58ab) a [názorný postup: Vytvoření formuláře Windows lokalizovatelné](https://msdn.microsoft.com/library/c5240b6e-aaca-4286-9bae-778a416edb9c).  
  
 Obecně platí, neměli byste používat <xref:System.Windows.Forms.TableLayoutPanel> ovládací prvek jako kontejner pro celé rozložení. Použití <xref:System.Windows.Forms.TableLayoutPanel> ovládací prvky pro poskytování přímo úměrná velikosti možností k různým částem rozložení.  
  
 Úlohy v tomto návodu zahrnují:  
  
-   Vytvoření projektu Windows Forms  
  
-   Uspořádání ovládacích prvků do řádků a sloupců  
  
-   Řádek nastavení a vlastnosti sloupce  
  
-   Rozložení řádků a sloupců s ovládacím prvkem  
  
-   Automatické zpracování přetečení  
  
-   Vkládání ovládacích prvků na něj poklikejte na panelu nástrojů  
  
-   Vložení ovládacího prvku kreslením obrysu  
  
-   Opětovné přiřazení existujících ovládacích prvků jinému nadřazenému prvku  
  
 Až budete hotovi, budete mít znalosti o úloze, kterou tyto funkce důležité rozložení.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
## <a name="creating-the-project"></a>Vytvoření projektu  
 Prvním krokem je vytvoření projektu a nastavení formuláře.  
  
#### <a name="to-create-the-project"></a>Vytvoření projektu  
  
1.  Vytvořte projekt aplikace Windows s názvem "TableLayoutPanelExample". Další informace najdete v tématu [jak: Vytvoření projektu aplikace Windows](https://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) .  
  
2.  Vyberte formulář v nástrojích pro **Windows** **Návrháře formulářů**.  
  
## <a name="arranging-controls-in-rows-and-columns"></a>Uspořádání ovládacích prvků do řádků a sloupců  
 <xref:System.Windows.Forms.TableLayoutPanel> Ovládací prvek umožňuje snadno uspořádání ovládacích prvků do řádků a sloupců.  
  
#### <a name="to-arrange-controls-in-rows-and-columns-using-a-tablelayoutpanel"></a>Chcete-li uspořádat ovládací prvky do řádků a sloupců pomocí ovládacího prvku TableLayoutPanel  
  
1.  Přetáhněte <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku **nástrojů** do formuláře. Všimněte si, že se ve výchozím nastavení, <xref:System.Windows.Forms.TableLayoutPanel> ovládací prvek má čtyři buňky.  
  
2.  Přetáhněte <xref:System.Windows.Forms.Button> řízení z **nástrojů** do <xref:System.Windows.Forms.TableLayoutPanel> řídit a umístěte ho do jedné buňky. Všimněte si, <xref:System.Windows.Forms.Button> ovládací prvek je vytvořen v rámci buňky, které jste vybrali.  
  
3.  Přetáhněte další tři <xref:System.Windows.Forms.Button> ovládacích prvků z **nástrojů** do <xref:System.Windows.Forms.TableLayoutPanel> řídit tak, aby každá buňka obsahuje tlačítko.  
  
4.  Svislé úchyt mezi dvěma sloupci vzít a přesunout ho na levé straně. Všimněte si, že <xref:System.Windows.Forms.Button> ovládacích prvků v prvním sloupci se mění velikost menší šířku, při velikosti <xref:System.Windows.Forms.Button> ovládacích prvků ve druhém sloupci je beze změny.  
  
5.  Svislé úchyt mezi dvěma sloupci vzít a přesunout ho na pravé straně. Všimněte si, že <xref:System.Windows.Forms.Button> ovládacích prvků v prvním sloupci vrátit na původní velikost, zatímco <xref:System.Windows.Forms.Button> ovládacích prvků ve druhém sloupci se přesouvají na pravé straně.  
  
6.  Přesuňte úchyt horizontální navýšení nebo snížení kapacity a vidět její účinek na ovládací prvky v panelu.  
  
## <a name="positioning-controls-within-cells-using-docking-and-anchoring"></a>Umístění ovládacích prvků v buňkách pomocí ukotvení a ukotvení  
 Kotvícího chování podřízených ovládacích prvků <xref:System.Windows.Forms.TableLayoutPanel> se liší od chování v další ovládací prvky kontejneru. Chování ukotvení podřízených ovládacích prvků je stejný jako další ovládací prvky kontejneru.  
  
#### <a name="positioning-controls-within-cells"></a>Umístění ovládacích prvků v buňkách  
  
1.  Vyberte první <xref:System.Windows.Forms.Button> ovládacího prvku. Změňte hodnotu vlastnosti jeho <xref:System.Windows.Forms.Control.Dock%2A> vlastnost <xref:System.Windows.Forms.DockStyle.Fill>. Všimněte si, že <xref:System.Windows.Forms.Button> ovládací prvek roztáhne a vyplní buňku.  
  
2.  Vyberte jednu z nich <xref:System.Windows.Forms.Button> ovládacích prvků. Změňte hodnotu vlastnosti jeho <xref:System.Windows.Forms.Control.Anchor%2A> vlastnost <xref:System.Windows.Forms.AnchorStyles.Right>. Všimněte si, že se přesune tak, aby jeho pravého ohraničení poblíž pravého ohraničení buňky. Vzdálenost mezi ohraničením je součet <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Margin%2A> vlastnosti a na panelu <xref:System.Windows.Forms.Control.Padding%2A> vlastnost.  
  
3.  Změňte hodnotu <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Anchor%2A> vlastnost <xref:System.Windows.Forms.AnchorStyles.Right> a <xref:System.Windows.Forms.AnchorStyles.Left>. Všimněte si, že ovládací prvek je velikost na šířku na buňku <xref:System.Windows.Forms.Control.Margin%2A> a <xref:System.Windows.Forms.Control.Padding%2A> hodnoty vzít v úvahu.  
  
4.  Opakujte kroky 2 a 3 se <xref:System.Windows.Forms.AnchorStyles.Top> a <xref:System.Windows.Forms.AnchorStyles.Bottom> styly.  
  
## <a name="setting-row-and-column-properties"></a>Řádek nastavení a vlastnosti sloupce  
 Můžete nastavit vlastnosti jednotlivých řádků a sloupců pomocí <xref:System.Windows.Forms.TableLayoutPanel.RowStyles%2A> a <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> kolekce.  
  
#### <a name="to-set-row-and-column-properties"></a>Chcete-li nastavit vlastnosti řádků a sloupců  
  
1.  Vyberte <xref:System.Windows.Forms.TableLayoutPanel> v ovládacím prvku **Návrháře formulářů Windows**.  
  
2.  V **vlastnosti** windows, otevřete <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> kolekci kliknutím tlačítko se třemi tečkami (![snímek obrazovky VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) tlačítko vedle položky **sloupce** položka.  
  
3.  Vyberte první sloupec a změňte hodnotu z jeho <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> vlastnost <xref:System.Windows.Forms.SizeType.AutoSize>. Klikněte na tlačítko **OK** pro potvrzení změny. Všimněte si, že se snižuje šířku prvního sloupce podle <xref:System.Windows.Forms.Button> ovládacího prvku. Všimněte si také, že šířka sloupce není umožňující změnu velikosti.  
  
4.  V **vlastnosti** otevřené okno <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> kolekci a vyberte v prvním sloupci. Změňte hodnotu vlastnosti jeho <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> vlastnost <xref:System.Windows.Forms.SizeType.Percent>. Klikněte na tlačítko **OK** pro potvrzení změny. Změnit velikost <xref:System.Windows.Forms.TableLayoutPanel> mít pod kontrolou větší šířku a Všimněte si, že rozšiřuje šířku prvního sloupce. Změnit velikost <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku menší šířku a Všimněte si, že je nastavena velikost tlačítka v prvním sloupci podle buňku. Všimněte si také, že je šířka sloupce umožňující změnu velikosti.  
  
5.  V **vlastnosti** otevřené okno <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> kolekci a vyberte všechny sloupců v seznamu. Nastavte hodnotu vlastnosti každé <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> vlastnost <xref:System.Windows.Forms.SizeType.Percent>. Klikněte na tlačítko **OK** pro potvrzení změny. Opakování s <xref:System.Windows.Forms.TableLayoutPanel.RowStyles%2A> kolekce.  
  
6.  Stáhnout si jednu horního úchyty pro změnu velikosti a změňte jeho velikost šířku a výšku <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku. Všimněte si, že řádky a sloupce se mění velikost jako <xref:System.Windows.Forms.TableLayoutPanel> změny velikosti ovládacího prvku. Všimněte si také, že řádky i sloupce jsou umožňující změnu velikosti s vodorovné a svislé úchyty pro změnu velikosti.  
  
## <a name="spanning-rows-and-columns-with-a-control"></a>Rozložení řádků a sloupců s ovládacím prvkem  
 <xref:System.Windows.Forms.TableLayoutPanel> Ovládacího prvku přidá několik nových vlastností k ovládacím prvkům v době návrhu. Dva z těchto vlastností jsou `RowSpan` a `ColumnSpan`. Tyto vlastnosti můžete vytvořit ovládací prvek rozpětí více než jeden řádek nebo sloupec.  
  
#### <a name="to-span-rows-and-columns-with-a-control"></a>Chcete-li rozpětí řádků a sloupců s ovládacím prvkem  
  
1.  Vyberte <xref:System.Windows.Forms.Button> ovládacího prvku v prvním řádku a první sloupec.  
  
2.  V **vlastnosti** windows, změňte hodnotu `ColumnSpan` vlastnost **2**. Všimněte si, <xref:System.Windows.Forms.Button> ovládací prvek vyplní druhé a první sloupec. Všimněte si také, než byla přidána na další řádek přizpůsobil této změně.  
  
3.  Krok 2 opakujte pro `RowSpan` vlastnost.  
  
## <a name="inserting-controls-by-double-clicking-them-in-the-toolbox"></a>Vkládání ovládacích prvků na něj poklikejte na panelu nástrojů  
 Můžete naplnit vaše <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku na něj poklikejte ovládacích prvků v **nástrojů**.  
  
#### <a name="to-insert-controls-by-double-clicking-in-the-toolbox"></a>Chcete-li vložit ovládací prvky na něj poklikejte na panelu nástrojů  
  
1.  Přetáhněte <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku **nástrojů** do formuláře.  
  
2.  Dvakrát klikněte <xref:System.Windows.Forms.Button> ikonu ovládacího prvku v **nástrojů**. Všimněte si, že nový ovládací prvek tlačítko se zobrazí v <xref:System.Windows.Forms.TableLayoutPanel> první buňky ovládacího prvku.  
  
3.  Klikněte dvakrát na několik dalších ovládacích prvků v **nástrojů**. Všimněte si, že nové ovládací prvky zobrazí postupně v <xref:System.Windows.Forms.TableLayoutPanel> neobsazený buňky ovládacího prvku. Všimněte si také, <xref:System.Windows.Forms.TableLayoutPanel> rozšíří ovládací prvek tak, aby vyhovovaly nové ovládací prvky, pokud nejsou k dispozici žádné otevřené buňky.  
  
## <a name="automatic-handling-of-overflows"></a>Automatické zpracování přetečení  
 Při vkládání ovládacích prvků do <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku, můžete spustit z prázdných buněk pro nové ovládací prvky. <xref:System.Windows.Forms.TableLayoutPanel> Této situaci ovládací prvek automaticky zpracovává zvýšením počtu buněk.  
  
#### <a name="to-observe-automatic-handling-of-overflows"></a>Sledovat automatické zpracování přetečení  
  
1.  Pokud jsou stále prázdných buněk v <xref:System.Windows.Forms.TableLayoutPanel> řídit, pokračovat vkládání nových <xref:System.Windows.Forms.Button> ovládací prvky do <xref:System.Windows.Forms.TableLayoutPanel> ovládací prvek je plný.  
  
2.  Jednou <xref:System.Windows.Forms.TableLayoutPanel> ovládací prvek je plná, dvakrát klikněte <xref:System.Windows.Forms.Button> ikonu v **nástrojů** vložit další <xref:System.Windows.Forms.Button> ovládacího prvku. Všimněte si, že <xref:System.Windows.Forms.TableLayoutPanel> ovládací prvek vytvoří nové buňky tak, aby vyhovovaly novým ovládacím prvkem. Vložit několik dalších ovládacích prvků a sledovat chování změny velikosti.  
  
3.  Změňte hodnotu <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku <xref:System.Windows.Forms.TableLayoutPanel.GrowStyle%2A> vlastnost <xref:System.Windows.Forms.TableLayoutPanelGrowStyle.FixedSize>. Dvakrát klikněte na panel <xref:System.Windows.Forms.Button> ikonu v **nástrojů** vložit <xref:System.Windows.Forms.Button> ovládací prvky do <xref:System.Windows.Forms.TableLayoutPanel> ovládací prvek je plný. Dvakrát klikněte <xref:System.Windows.Forms.Button> ikonu v **nástrojů** znovu. Všimněte si, že se zobrazí chybová zpráva z **Návrháře formulářů Windows** oznamující, že nelze vytvořit další řádky a sloupce.  
  
## <a name="inserting-a-control-by-drawing-its-outline"></a>Vložení ovládacího prvku kreslením obrysu  
 Můžete vložit do ovládacího prvku <xref:System.Windows.Forms.TableLayoutPanel> řídit a určit jeho velikost kreslením obrysu v buňce.  
  
#### <a name="to-insert-a-control-by-drawing-its-outline"></a>Chcete-li vložit ovládací prvek kreslením obrysu  
  
1.  Přetáhněte <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku **nástrojů** do formuláře.  
  
2.  V **nástrojů**, klikněte na tlačítko <xref:System.Windows.Forms.Button> ikonu ovládacího prvku. Přetáhněte není ji na formuláři.  
  
3.  Přesuňte ukazatel myši <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku. Všimněte si, že se ukazatel změní na křížek s <xref:System.Windows.Forms.Button> ikonu ovládací prvek připojen.  
  
4.  Klepněte a podržte tlačítko myši.  
  
5.  Přetažením ukazatele myši nakreslete obrysu <xref:System.Windows.Forms.Button> ovládacího prvku. Pokud jste spokojeni s velikostí, uvolněte tlačítko myši. Všimněte si, <xref:System.Windows.Forms.Button> ovládací prvek je vytvořen v buňce, ve kterém nakreslili osnovy ovládacího prvku.  
  
## <a name="multiple-controls-within-cells-are-not-permitted"></a>Není povoleno více ovládacích prvků v buňkách  
 <xref:System.Windows.Forms.TableLayoutPanel> Ovládacího prvku může obsahovat pouze jeden podřízený ovládací prvek na buňky.  
  
#### <a name="to-demonstrate-that-multiple-controls-within-cells-are-not-permitted"></a>K předvedení toho, aby více ovládacích prvků v buňkách nejsou povolené.  
  
-   Přetáhněte <xref:System.Windows.Forms.Button> řízení z **nástrojů** do <xref:System.Windows.Forms.TableLayoutPanel> řídit a umístěte ho na jednu z buněk, obsazené. Všimněte si, že <xref:System.Windows.Forms.TableLayoutPanel> ovládací prvek neumožňuje vyřadit <xref:System.Windows.Forms.Button> ovládacího prvku do buňky obsazené.  
  
## <a name="swapping-controls"></a>Vzájemná záměna ovládacích prvků  
 <xref:System.Windows.Forms.TableLayoutPanel> Ovládací prvek umožňuje vám přepínat ovládací prvky zabírá dvě různé buňky.  
  
#### <a name="to-swap-controls"></a>Pro ovládací prvky  
  
-   Přetáhněte jednu z <xref:System.Windows.Forms.Button> ovládací prvky ze obsazené buňky a drop do do jiné buňky obsazené. Všimněte si, že dva ovládací prvky jsou přemístěné z jedné buňky do druhé.  
  
## <a name="next-steps"></a>Další kroky  
 Složitá rozložení pomocí kombinace panely rozložení a ovládacích prvků můžete dosáhnout. Návrhy pro další zkoumání patří:  
  
-   Zkuste jednu z změnit velikost <xref:System.Windows.Forms.Button> ovládacích prvků pro větší velikost a Všimněte si vliv na rozložení.  
  
-   Vložit výběr více ovládacích prvků do <xref:System.Windows.Forms.TableLayoutPanel> řídit a Všimněte si, jak jsou ovládací prvky vloženy.  
  
-   Panely rozložení může obsahovat jiné panely rozložení. Experimentu se vyřazování <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku do existujícího ovládacího prvku.  
  
-   Ukotvit <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku na nadřazený formulář. Změnit velikost formuláře a sledujte vliv na rozložení.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Forms.FlowLayoutPanel>
- <xref:System.Windows.Forms.TableLayoutPanel>
- [Návod: Uspořádání ovládacích prvků na formuláři Windows s použitím ovládacího prvku FlowLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [Návod: Uspořádání ovládacích prvků ve Windows Forms pomocí zarovnávacích čar](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [Microsoft Windows uživatelské prostředí, oficiální pokyny pro uživatelské rozhraní vývojářů a návrhářů. Redmond, WA: Microsoft Press, 1999. (USBN: 0-7356-0566-1)](https://www.microsoft.com/mspress/southpacific/books/book11588.htm)
- [Návod: Vytvoření formuláře Windows s možností změny velikosti pro zadávání dat](https://msdn.microsoft.com/library/e193b4fc-912a-4917-b036-b76c7a6f58ab)
- [Návod: Vytvoření formuláře Windows lokalizovatelné](https://msdn.microsoft.com/library/c5240b6e-aaca-4286-9bae-778a416edb9c)
- [Doporučené postupy pro ovládací prvek TableLayoutPanel](../../../../docs/framework/winforms/controls/best-practices-for-the-tablelayoutpanel-control.md)
- [Přehled vlastnosti AutoSize](../../../../docs/framework/winforms/controls/autosize-property-overview.md)
- [Postupy: Ukotvování ovládacích prvků ve Windows Forms](../../../../docs/framework/winforms/controls/how-to-dock-controls-on-windows-forms.md)
- [Postupy: Ukotvení ovládacích prvků ve Windows Forms](../../../../docs/framework/winforms/controls/how-to-anchor-controls-on-windows-forms.md)
- [Návod: Vytváření rozložení Windows Forms ovládací prvky s odsazením, okraji a s vlastností AutoSize](../../../../docs/framework/winforms/controls/windows-forms-controls-padding-autosize.md)
