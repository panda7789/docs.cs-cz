---
title: 'Návod: Uspořádání ovládacích prvků na formuláři Windows Forms s použitím ovládacího prvku FlowLayoutPanel'
ms.date: 03/30/2017
helpviewer_keywords:
- FlowLayoutPanel control [Windows Forms], walkthroughs
- Windows Forms controls, arranging
- controls [Windows Forms], arranging with FlowLayoutPanel
- layout [Windows Forms], walkthroughs
ms.assetid: a1744323-0316-49c2-992e-ebfc0a976b85
ms.openlocfilehash: 81a19d063f31b3c28fc15a061b5173495e83f6fc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62009120"
---
# <a name="walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel"></a>Návod: Uspořádání ovládacích prvků na formuláři Windows Forms s použitím ovládacího prvku FlowLayoutPanel
Některé aplikace vyžadují formulář pomocí rozložení, který uspořádá samotné správně při změně velikosti formuláře, nebo jako obsah změnit velikost. Pokud potřebujete dynamické rozložení a nechcete zpracovat <xref:System.Windows.Forms.Control.Layout> události explicitně v kódu, zvažte použití panelu rozložení.  
  
 <xref:System.Windows.Forms.FlowLayoutPanel> Ovládacího prvku a <xref:System.Windows.Forms.TableLayoutPanel> řízení poskytují intuitivní způsoby, jak uspořádat ovládací prvky na formuláři. Umožňují automatické, konfigurovatelné možnosti řízení relativní pozice podřízených ovládacích prvků v nich obsažené, a obě získáte funkce dynamické rozložení v době běhu, aby jejich velikost a umístění podřízených ovládacích prvků jako dimenze nadřazený formulář Změňte. Panely rozložení může být vnořena do panely rozložení, aby realizace propracovaná uživatelská rozhraní.  
  
 <xref:System.Windows.Forms.TableLayoutPanel> Uspořádá její obsah do mřížky, poskytuje funkce podobné HTML \<tabulky > element. Jeho buňky jsou uspořádány do řádků a sloupců, a ty mají různé velikosti. Další informace najdete v tématu [názorný postup: Uspořádání ovládacích prvků na formuláři Windows s použitím ovládacího prvku TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).  
  
 <xref:System.Windows.Forms.FlowLayoutPanel> Uspořádá jeho obsah v konkrétní směr: vodorovný nebo svislý. Dá zabalit obsah z jednoho řádku na další nebo z jednoho sloupce na další. Alternativně můžete místo oříznutí jeho obsah zabalena. Úlohy v tomto návodu zahrnují:  
  
- Vytvoření projektu Windows Forms  
  
- Uspořádání ovládacích prvků vodorovně a svisle  
  
- Změna směru toku  
  
- Vložení toku konce  
  
- Uspořádání ovládacích prvků pomocí odsazení a okraje  
  
- Vkládání ovládacích prvků na něj poklikejte na panelu nástrojů  
  
- Vložení ovládacího prvku kreslením obrysu  
  
- Vkládání ovládacích prvků pomocí kurzoru  
  
- Opětovné přiřazení existujících ovládacích prvků jinému nadřazenému prvku  
  
 Až budete hotovi, budete mít znalosti o úloze, kterou tyto funkce důležité rozložení.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
## <a name="creating-the-project"></a>Vytvoření projektu  
 Prvním krokem je vytvoření projektu a nastavení formuláře.  
  
#### <a name="to-create-the-project"></a>Vytvoření projektu  
  
1. Vytvořte projekt aplikace pro systém Windows s názvem "FlowLayoutPanelExample" (**souboru** > **nový** > **projektu**  >  **Visual C#** nebo **jazyka Visual Basic** > **klasický desktopový** > **Windows Forms aplikace**).  
  
2. Vyberte formulář v nástrojích pro **Návrháře formulářů**.  
  
## <a name="arranging-controls-horizontally-and-vertically"></a>Uspořádání ovládacích prvků vodorovně a svisle  
 <xref:System.Windows.Forms.FlowLayoutPanel> Ovládací prvek umožňuje umístit ovládací prvky řádky nebo sloupce, aniž by bylo potřeba přesně určit umístění jednotlivých ovládacích prvků.  
  
 <xref:System.Windows.Forms.FlowLayoutPanel> Ovládací prvek můžete změnit velikost nebo přeformátování jeho podřízených ovládacích prvků jako dimenze změnou nadřazené formuláře.  
  
#### <a name="to-arrange-controls-horizontally-and-vertically-using-a-flowlayoutpanel"></a>Chcete-li uspořádat ovládací prvky vodorovně a svisle pomocí ovládacího prvku FlowLayoutPanel  
  
1. Přetáhněte <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku **nástrojů** do formuláře.  
  
2. Přetáhněte <xref:System.Windows.Forms.Button> ovládacího prvku **nástrojů** do <xref:System.Windows.Forms.FlowLayoutPanel>. Všimněte si, že se automaticky přesune do levého horního rohu <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku.  
  
3. Přetáhněte další <xref:System.Windows.Forms.Button> ovládacího prvku **nástrojů** do <xref:System.Windows.Forms.FlowLayoutPanel>. Všimněte si, že <xref:System.Windows.Forms.Button> ovládací prvek automaticky přesunut do polohy vedle první <xref:System.Windows.Forms.Button> ovládacího prvku. Pokud vaše <xref:System.Windows.Forms.FlowLayoutPanel> je příliš úzký, aby se vešel dvou ovládacích prvků na stejném řádku, nové <xref:System.Windows.Forms.Button> ovládací prvek automaticky přesunut do dalšího řádku.  
  
4. Přetáhněte několik dalších <xref:System.Windows.Forms.Button> ovládacích prvků z **nástrojů** do <xref:System.Windows.Forms.FlowLayoutPanel>. Pokračovat v umístění <xref:System.Windows.Forms.Button> dokud jeden zalamuje na další řádek.  
  
5. Změňte hodnotu <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku <xref:System.Windows.Forms.FlowLayoutPanel.WrapContents%2A> vlastnost `false`. Všimněte si, že podřízené ovládací prvky už tok na další řádek. Místo toho se přesunout na první řádek a oříznut.  
  
6. Změňte hodnotu <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku <xref:System.Windows.Forms.FlowLayoutPanel.WrapContents%2A> vlastnost `true`. Všimněte si, že podřízené ovládací prvky znovu wrap na dalším řádku.  
  
7. Zúžení <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku, dokud všichni <xref:System.Windows.Forms.Button> ovládací prvky, které jsou přesunuty do prvního sloupce.  
  
8. Zvětšete šířku <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku, dokud všichni <xref:System.Windows.Forms.Button> ovládací prvky se přesouvají do prvního řádku. Budete muset změnit velikost formuláře tak, aby vyhovovaly větší šířku.  
  
## <a name="changing-flow-direction"></a>Změna směru toku  
 <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> Vlastnost vám umožní změnit směr, ve kterém jsou uspořádány ovládací prvky. Z můžete uspořádat podřízené ovládací prvky zleva doprava, zprava doleva, shora dolů nebo zdola nahoru.  
  
#### <a name="to-change-the-flow-direction-in-a-flowlayoutpanel"></a>Chcete-li změnit směr toku do ovládacího prvku FlowLayoutPanel  
  
1. Změňte hodnotu <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> vlastnost <xref:System.Windows.Forms.FlowDirection.TopDown>. Všimněte si, že jsou podřízené ovládací prvky změnit jejich uspořádání do jednoho nebo více sloupců, v závislosti na výšku ovládacího prvku.  
  
2. Změnit velikost <xref:System.Windows.Forms.FlowLayoutPanel> tak jeho výška je kratší než sloupec <xref:System.Windows.Forms.Button> ovládacích prvků. Všimněte si, že <xref:System.Windows.Forms.FlowLayoutPanel> znovu uspořádá podřízené ovládací prvky, které jsou předávány do dalšího sloupce. Pokračovat, snížení výšky a Všimněte si, že podřízené řídí tok do po sobě jdoucích sloupcích. Změňte hodnotu <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> vlastnost <xref:System.Windows.Forms.FlowDirection.RightToLeft>. Všimněte si, že jsou v obráceném pořadí pozice podřízených ovládacích prvků. Sledujte rozložení při změně hodnoty <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> vlastnost <xref:System.Windows.Forms.FlowDirection.BottomUp>.  
  
## <a name="inserting-flow-breaks"></a>Vložení toku konce  
 <xref:System.Windows.Forms.FlowLayoutPanel> Ovládací prvek obsahuje vlastnosti FlowBreak a jeho podřízených ovládacích prvků. Nastavení hodnoty vlastnosti FlowBreak k `true` způsobí, že <xref:System.Windows.Forms.FlowLayoutPanel> ovládací prvek zastavit rozvrhování ovládacích prvků v aktuální směr toku a zalomení na další řádek nebo sloupec.  
  
#### <a name="to-insert-flow-breaks"></a>Vložit zalomení toku  
  
1. Změňte hodnotu <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> vlastnost <xref:System.Windows.Forms.FlowDirection.TopDown>.  
  
2. Vyberte jednu z <xref:System.Windows.Forms.Button> ovládací prvky průběhu sloupci nejvíce vlevo.  
  
3. Nastavte hodnotu <xref:System.Windows.Forms.Button> FlowBreak vlastnosti ovládacího prvku na `true`. Všimněte si, že sloupec je poškozený a ovládací prvky podle vybraného <xref:System.Windows.Forms.Button> řídit tok do dalšího sloupce. Nastavte hodnotu <xref:System.Windows.Forms.Button> FlowBreak vlastnosti ovládacího prvku na `false` se vraťte k původní chování.  
  
## <a name="positioning-controls-using-docking-and-anchoring"></a>Umístění ovládacích prvků pomocí ukotvení a ukotvení  
 Ukotvitelné a chování podřízených ovládacích prvků ukotvení se liší od chování v další ovládací prvky kontejneru. Ukotvení i ukotvení jsou relativní vzhledem k největší ovládacího prvku ve směru toku.  
  
#### <a name="to-position-controls-using-docking-and-anchoring"></a>Pokud chcete umístit ovládací prvky pomocí ukotvení a ukotvení  
  
1. Zvětšete velikost <xref:System.Windows.Forms.FlowLayoutPanel> až <xref:System.Windows.Forms.Button> ovládací prvky jsou uspořádány ve sloupci.  
  
2. Vyberte horní <xref:System.Windows.Forms.Button> ovládacího prvku. Zvyšte jeho šířku tak, aby se o dvakrát stejně široká jako druhý <xref:System.Windows.Forms.Button> ovládacích prvků.  
  
3. Vyberte druhou <xref:System.Windows.Forms.Button> ovládacího prvku. Změňte hodnotu vlastnosti jeho <xref:System.Windows.Forms.Control.Anchor%2A> vlastnost <xref:System.Windows.Forms.AnchorStyles.Right>. Všimněte si, že se přesune tak, aby jeho pravého ohraničení zarovnán s prvním <xref:System.Windows.Forms.Button> pravého ohraničení ovládacího prvku.  
  
4. Změňte hodnotu vlastnosti jeho <xref:System.Windows.Forms.Control.Anchor%2A> vlastnost <xref:System.Windows.Forms.AnchorStyles.Right> a <xref:System.Windows.Forms.AnchorStyles.Left>. Všimněte si, že je velikost na stejnou šířku jako první <xref:System.Windows.Forms.Button> ovládacího prvku.  
  
5. Vyberte třetí <xref:System.Windows.Forms.Button> ovládacího prvku. Změňte hodnotu vlastnosti jeho <xref:System.Windows.Forms.Control.Dock%2A> vlastnost <xref:System.Windows.Forms.DockStyle.Fill>. Všimněte si, že je velikost na stejnou šířku jako první <xref:System.Windows.Forms.Button> ovládacího prvku.  
  
## <a name="arranging-controls-using-padding-and-margins"></a>Uspořádání ovládacích prvků pomocí odsazení a okraje  
 Můžete také uspořádat ovládací prvky ve vašich <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku tak, že změníte <xref:System.Windows.Forms.Control.Padding%2A> a <xref:System.Windows.Forms.Control.Margin%2A> vlastnosti.  
  
 <xref:System.Windows.Forms.Control.Padding%2A> Vlastnost umožňuje řídit umístění ovládacích prvků v rámci <xref:System.Windows.Forms.FlowLayoutPanel> buňky ovládacího prvku. Určuje mezery mezi podřízených ovládacích prvků a <xref:System.Windows.Forms.FlowLayoutPanel> ohraničení ovládacího prvku.  
  
 <xref:System.Windows.Forms.Control.Margin%2A> Vlastnost umožňuje řídit mezer mezi ovládacími prvky.  
  
#### <a name="to-arrange-controls-using-the-padding-and-margin-properties"></a>Chcete-li uspořádat ovládací prvky pomocí vlastnosti odsazení a okraj  
  
1. Změňte hodnotu <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku <xref:System.Windows.Forms.Control.Dock%2A> vlastnost <xref:System.Windows.Forms.DockStyle.Fill>. Pokud formuláře je příliš velká, <xref:System.Windows.Forms.Button> ovládací prvky se přesunou na první sloupec <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku.  
  
2. Změňte hodnotu <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku <xref:System.Windows.Forms.Control.Padding%2A> vlastnost tak, že rozbalíte <xref:System.Windows.Forms.Control.Padding%2A> položku v **vlastnosti** okno a nastavení <xref:System.Windows.Forms.Padding.All%2A> vlastnost **20**. Další informace najdete v tématu [názorný postup: Vytváření rozložení Windows Forms ovládací prvky s odsazením, okraji a s vlastností AutoSize](windows-forms-controls-padding-autosize.md). Všimněte si, že podřízené ovládací prvky se přesouvají směrem k středu <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku. Vyšší hodnota <xref:System.Windows.Forms.Control.Padding%2A> vlastnost nabízených oznámení podřízených ovládacích prvků ze <xref:System.Windows.Forms.FlowLayoutPanel> ohraničení ovládacího prvku.  
  
3. Vyberte všechny <xref:System.Windows.Forms.Button> ovládacích prvků v <xref:System.Windows.Forms.FlowLayoutPanel> a nastavte hodnotu <xref:System.Windows.Forms.Control.Margin%2A> vlastnost **20**. Všimněte si, že mezery mezi <xref:System.Windows.Forms.Button> řídí zvyšuje, aby se přesunuly další od sebe. Možná budete muset změnit velikost <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku větší, aby se zobrazily všechny podřízené ovládací prvky.  
  
## <a name="inserting-controls-by-double-clicking-them-in-the-toolbox"></a>Vkládání ovládacích prvků na něj poklikejte na panelu nástrojů  
 Můžete naplnit vaše <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku na něj poklikejte ovládacích prvků v **nástrojů**.  
  
#### <a name="to-insert-controls-by-double-clicking-in-the-toolbox"></a>Chcete-li vložit ovládací prvky na něj poklikejte na panelu nástrojů  
  
1. Dvakrát klikněte <xref:System.Windows.Forms.Button> ikonu ovládacího prvku v **nástrojů**. Všimněte si, že nový <xref:System.Windows.Forms.Button> ovládací prvek zobrazí <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku.  
  
2. Klikněte dvakrát na několik dalších ovládacích prvků v **nástrojů**. Všimněte si, že nové ovládací prvky zobrazí postupně v <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku.  
  
## <a name="inserting-a-control-by-drawing-its-outline"></a>Vložení ovládacího prvku kreslením obrysu  
 Můžete vložit do ovládacího prvku <xref:System.Windows.Forms.FlowLayoutPanel> řídit a určit jeho velikost kreslením obrysu v buňce.  
  
#### <a name="to-insert-a-control-by-drawing-its-outline"></a>Chcete-li vložit ovládací prvek kreslením obrysu  
  
1. V **nástrojů**, klikněte na tlačítko <xref:System.Windows.Forms.Button> ikonu ovládacího prvku. Přetáhněte není ji na formuláři.  
  
2. Přesuňte ukazatel myši <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku. Všimněte si, že se ukazatel změní na křížek s <xref:System.Windows.Forms.Button> ikonu ovládací prvek připojen.  
  
3. Klepněte a podržte tlačítko myši.  
  
4. Přetažením ukazatele myši nakreslete obrysu <xref:System.Windows.Forms.Button> ovládacího prvku. Pokud jste spokojeni s velikostí, uvolněte tlačítko myši. Všimněte si, že <xref:System.Windows.Forms.Button> ovládací prvek je vytvořen v dalším Otevřít umístění <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku.  
  
## <a name="inserting-controls-using-the-insertion-bar"></a>Vkládání ovládacích prvků pomocí vložení řádku  
 Ovládací prvky můžete vložit na konkrétní pozici v <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku. Při přetažení do ovládacího prvku <xref:System.Windows.Forms.FlowLayoutPanel> klientské oblasti ovládacího prvku, vložení panelu se zobrazí označení vloženy ovládacího prvku.  
  
#### <a name="to-insert-a-control-using-the-caret"></a>Chcete-li vložit ovládací prvek pomocí kurzoru  
  
1. Přetáhněte <xref:System.Windows.Forms.Button> ovládacího prvku **nástrojů** do <xref:System.Windows.Forms.FlowLayoutPanel> řídit a přejděte do prostoru mezi dvěma <xref:System.Windows.Forms.Button> ovládacích prvků. Mějte na paměti, že je vykreslován indikátor vložení, udává, odkud <xref:System.Windows.Forms.Button> bude umístěn, když je přetáhnout do <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku. Před vyřazením nové <xref:System.Windows.Forms.Button> ovládací prvek do <xref:System.Windows.Forms.FlowLayoutPanel> řídit, přesuňte ukazatel myši přibližně chcete sledovat, jak Přesune panel vložení.  
  
2. Vyřadit nové <xref:System.Windows.Forms.Button> ovládací prvek do <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku. Všimněte si, že nový <xref:System.Windows.Forms.Button> ovládací prvek není zarovnána s jinými uživateli, protože jeho <xref:System.Windows.Forms.Control.Margin%2A> vlastnost má jinou hodnotu.  
  
## <a name="reassigning-existing-controls-to-a-different-parent"></a>Opětovné přiřazení existujících ovládacích prvků jinému nadřazenému prvku  
 Můžete přiřadit ovládací prvky, které existují ve formuláři na nový <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku.  
  
#### <a name="to-reparent-existing-controls"></a>Chcete-li změnit nadřazenou položku existující ovládací prvky  
  
1. Přetáhněte tři <xref:System.Windows.Forms.Button> ovládacích prvků z **nástrojů** do formuláře. Umístěte blízko sobě navzájem, ale nechat nezarovnaných.  
  
2. V **nástrojů**, klikněte na tlačítko <xref:System.Windows.Forms.FlowLayoutPanel> ikonu ovládacího prvku. Přetáhněte není ji na formuláři.  
  
3. Přesuňte ukazatel myši blízko tři <xref:System.Windows.Forms.Button> ovládacích prvků. Všimněte si, že se ukazatel změní na křížek s <xref:System.Windows.Forms.FlowLayoutPanel> ikonu ovládací prvek připojen.  
  
4. Klepněte a podržte tlačítko myši.  
  
5. Přetažením ukazatele myši nakreslete obrysu <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku. Nakreslit obrys kolem tři <xref:System.Windows.Forms.Button> ovládacích prvků.  
  
6. Uvolněte tlačítko myši. Všimněte si, že tři <xref:System.Windows.Forms.Button> ovládací prvky jsou vloženy do <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku.  
  
## <a name="next-steps"></a>Další kroky  
 Složitá rozložení pomocí kombinace panely rozložení a ovládacích prvků můžete dosáhnout. Návrhy pro další zkoumání patří:  
  
- Změna velikosti mezi <xref:System.Windows.Forms.Button> ovládacích prvků pro větší velikost a Všimněte si vliv na rozložení.  
  
- Panely rozložení může obsahovat jiné panely rozložení. Experimentu se vyřazování <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku do existujícího ovládacího prvku.  
  
- Ukotvit <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku na nadřazený formulář. Změnit velikost formuláře a sledujte vliv na rozložení.  
  
- Nastavte <xref:System.Windows.Forms.Control.Visible%2A> vlastnost ovládací prvky pro `false` a Všimněte si, jak <xref:System.Windows.Forms.FlowLayoutPanel> přeformátuje v odpovědi.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.FlowLayoutPanel>
- <xref:System.Windows.Forms.TableLayoutPanel>
- [Návod: Uspořádání ovládacích prvků na formuláři Windows s použitím ovládacího prvku TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [Návod: Uspořádání ovládacích prvků ve Windows Forms pomocí zarovnávacích čar](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [Microsoft Windows uživatelské prostředí, oficiální pokyny pro uživatelské rozhraní vývojářů a návrhářů. Redmond, WA: Microsoft Press, 1999. (USBN: 0-7356-0566-1)](https://www.microsoft.com/mspress/southpacific/books/book11588.htm)
- [Přehled vlastnosti AutoSize](autosize-property-overview.md)
- [Postupy: Ukotvování ovládacích prvků ve Windows Forms](how-to-dock-controls-on-windows-forms.md)
- [Postupy: Ukotvení ovládacích prvků ve Windows Forms](how-to-anchor-controls-on-windows-forms.md)
- [Návod: Vytváření rozložení Windows Forms ovládací prvky s odsazením, okraji a s vlastností AutoSize](windows-forms-controls-padding-autosize.md)
