---
title: 'Průvodce: Uspořádání ovládacích prvků ve Windows Forms pomocí zarovnávacích čar'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], arranging with snaplines
- snaplines [Windows Forms], arranging Windows Forms controls
- SnapLine class [Windows Forms], walkthroughs
- Windows Forms controls, arranging
ms.assetid: d5c9edc7-cf30-4a97-8ebe-201d569340f8
ms.openlocfilehash: 136a655064fc0c955cadd2f15e5900579e90187a
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2019
ms.locfileid: "56748031"
---
# <a name="walkthrough-arranging-controls-on-windows-forms-using-snaplines"></a>Průvodce: Uspořádání ovládacích prvků ve Windows Forms pomocí zarovnávacích čar
Přesné umístění ovládacích prvků na formuláři je důležitá pro mnoho aplikací. Návrhář formulářů Windows poskytuje celou řadu nástrojů rozložení, jak toho dosáhnout. Jednou z vašich nejdůležitějších je <xref:System.Windows.Forms.Design.Behavior.SnapLine> funkce.  
  
 Zarovnávacích čar zobrazí přesně, kde zarovnejte ovládací prvky s jinými ovládacími prvky. Také ukazují doporučená vzdálenosti pro okraje mezi ovládacími prvky, jak je uvedeno v pokynech uživatelské rozhraní Windows. Podrobnosti najdete v tématu [vývoj a návrh uživatelského rozhraní](https://go.microsoft.com/FWLink/?LinkId=83878).  
  
 Zarovnávacích čar usnadňují zarovnat své ovládací prvky pro ostré, profesionální vzhled a chování (vzhled a chování).  
  
 Úlohy v tomto návodu zahrnují:  
  
-   Vytvoření projektu Windows Forms  
  
-   Mezer a zarovnání ovládacích prvků pomocí zarovnávacích čar  
  
-   Zarovnání do formuláře a kontejner rozpětí  
  
-   Zarovnání seskupené ovládací prvky  
  
-   Umístit ovládací prvek sbalením jeho velikost pomocí zarovnávacích čar  
  
-   Při přetažení ovládacího prvku z panelu nástrojů pomocí zarovnávacích čar  
  
-   Změna velikosti ovládacích prvků pomocí zarovnávacích čar  
  
-   Zarovnání popisku na Text ovládacího prvku  
  
-   Pomocí zarovnávacích čar navigaci pomocí klávesnice  
  
-   Zarovnávacích čar a panely rozložení  
  
-   Zakázání zarovnávacích čar  
  
 Až budete hotovi, budete mít představu o úloze rozložení pomocí zarovnávacích čar funkce.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
## <a name="creating-the-project"></a>Vytvoření projektu  
 Prvním krokem je vytvoření projektu a nastavení formuláře.  
  
#### <a name="to-create-the-project"></a>Vytvoření projektu  
  
1.  Vytvořte projekt aplikace pro systém Windows s názvem "SnaplineExample" (**souboru** > **nový** > **projektu**  >  **Visual C#** nebo **jazyka Visual Basic** > **klasický desktopový** > **aplikaci Windows Forms**).  
  
2.  V Návrháři formulářů vyberte formulář.  
  
## <a name="spacing-and-aligning-controls-using-snaplines"></a>Mezer a zarovnání ovládacích prvků pomocí zarovnávacích čar  
 Zarovnávacích čar poskytnout přesné a intuitivní způsob zarovnání ovládacích prvků na formuláři. Zobrazí se při přesunování vybraný ovládací prvek nebo prvky v pozici, která by bylo v souladu s jiný ovládací prvek nebo sadu ovládacích prvků. Váš výběr se "přichytávat" k navrhované pozici jako přesunout za další ovládací prvky.  
  
#### <a name="to-arrange-controls-using-snaplines"></a>K uspořádání ovládacích prvků pomocí zarovnávacích čar  
  
1.  Přetáhněte <xref:System.Windows.Forms.Button> ovládacího prvku **nástrojů** do formuláře.  
  
2.  Přesunout <xref:System.Windows.Forms.Button> ovládacího prvku do pravého dolního rohu formuláře. Poznámka: zarovnávacích čar, které se zobrazí jako <xref:System.Windows.Forms.Button> ovládací prvek blíží dolní a pravé ohraničení tvaru. Tyto zarovnávacích čar zobrazit doporučené vzdálenost mezi ohraničení ovládacího prvku a formuláře.  
  
3.  Přesunout <xref:System.Windows.Forms.Button> řízení kolem okraje formulář opravdu zavřít a Všimněte si, kde se zobrazí zarovnávacích čar. Po dokončení přesunutí <xref:System.Windows.Forms.Button> ovládací prvek poblíž středu tvaru.  
  
4.  Přetáhněte další <xref:System.Windows.Forms.Button> ovládacího prvku **nástrojů** do formuláře.  
  
5.  Přesunout druhý <xref:System.Windows.Forms.Button> ovládací prvek, dokud je téměř úroveň s prvním. Mějte na paměti snapline –, který se zobrazí na základní text i tlačítek a Všimněte si, že ovládací prvek, který se přesouvají přitahuje pozici, která je právě kousek jiný ovládací prvek.  
  
6.  Přesunout druhý <xref:System.Windows.Forms.Button> ovládací prvek, dokud je umístěný přímo nad první. Všimněte si zarovnávacích čar, které se zobrazují podél levých a pravých okrajů obě tlačítka a Všimněte si, že ovládací prvek jste přesun při kolika rozehrávkách byli na pozici, která je právě v souladu s jiný ovládací prvek.  
  
7.  Vyberte jednu z <xref:System.Windows.Forms.Button> ovládací prvky a přesuňte ho blízko druhé, dokud jsou téměř zásahu. Poznámka: snapline –, který se zobrazí mezi nimi. Tato vzdálenost je doporučené vzdálenost mezi ohraničení ovládacích prvků. Všimněte si také, že ovládací prvek, který se přesouvají Připnutí na tuto pozici.  
  
8.  Přetáhněte dva <xref:System.Windows.Forms.Panel> ovládacích prvků z **nástrojů** do formuláře.  
  
9. Jak přesunout některou z <xref:System.Windows.Forms.Panel> dokud je téměř úroveň s prvním. Všimněte si zarovnávacích čar, které se zobrazují podél horní a dolní okraj oba ovládací prvky a Všimněte si, že ovládací prvek, který se přesouvají přitahuje pozici, která je právě kousek jiný ovládací prvek.  
  
## <a name="aligning-to-form-and-container-margins"></a>Zarovnání do formuláře a kontejner rozpětí  
 Zarovnávacích čar pomáhají Zarovnat ovládací prvky do formuláře a kontejner rozpětí konzistentním způsobem.  
  
#### <a name="to-align-controls-to-form-and-container-margins"></a>Chcete-li zarovnat ovládací prvky do formuláře a kontejner rozpětí  
  
1.  Vyberte jednu z <xref:System.Windows.Forms.Button> ovládací prvky a přesuňte ho blízko pravého ohraničení tvaru, dokud se nezobrazí snapline –. Vzdálenost snapline – od pravého ohraničení je součtem ovládacího prvku <xref:System.Windows.Forms.Control.Margin%2A> vlastnost a formuláře <xref:System.Windows.Forms.Control.Padding%2A> hodnot vlastností.  
  
> [!NOTE]
>  Pokud formulář <xref:System.Windows.Forms.Control.Padding%2A> je nastavena na 0,0,0,0, Návrhář formulářů Windows poskytuje formuláře stínovaný <xref:System.Windows.Forms.Control.Padding%2A> hodnotu 9,9,9,9. Chcete-li přepsat toto chování, přiřadíte jinou hodnotu než 0,0,0,0.  
  
1.  Změňte hodnotu <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Margin%2A> vlastnost tak, že rozbalíte <xref:System.Windows.Forms.Control.Margin%2A> položku v **vlastnosti** okno a nastavení <xref:System.Windows.Forms.Padding.All%2A> vlastnost na hodnotu 0. Podrobnosti najdete v tématu [názorný postup: Vytváření rozložení Windows Forms ovládací prvky s odsazením, okraji a s vlastností AutoSize](../../../../docs/framework/winforms/controls/windows-forms-controls-padding-autosize.md).  
  
2.  Přesunout <xref:System.Windows.Forms.Button> ovládací prvek blízko pravého ohraničení tvaru, dokud se nezobrazí snapline –. Tato vzdálenost je nyní dán hodnotou formuláře <xref:System.Windows.Forms.Control.Padding%2A> vlastnost.  
  
3.  Přetáhněte <xref:System.Windows.Forms.GroupBox> ovládacího prvku **nástrojů** do formuláře.  
  
4.  Změňte hodnotu <xref:System.Windows.Forms.GroupBox> ovládacího prvku <xref:System.Windows.Forms.Control.Padding%2A> vlastnost tak, že rozbalíte <xref:System.Windows.Forms.Control.Padding%2A> položku v **vlastnosti** okno a nastavení <xref:System.Windows.Forms.Padding.All%2A> vlastnost až 10.  
  
5.  Přetáhněte <xref:System.Windows.Forms.Button> ovládacího prvku **nástrojů** do <xref:System.Windows.Forms.GroupBox> ovládacího prvku.  
  
6.  Přesunout <xref:System.Windows.Forms.Button> ovládací prvek blízko pravého okraje <xref:System.Windows.Forms.GroupBox> ovládací prvek, dokud se nezobrazí snapline –. Přesunout <xref:System.Windows.Forms.Button> ovládacích prvků uvnitř <xref:System.Windows.Forms.GroupBox> ovládacího prvku a Všimněte si, kde se zobrazí zarovnávacích čar.  
  
## <a name="aligning-to-grouped-controls"></a>Zarovnání seskupené ovládací prvky  
 Vám pomůže zarovnávacích čar zarovnat seskupené ovládací prvky také jako ovládací prvky v rámci <xref:System.Windows.Forms.GroupBox> ovládacího prvku.  
  
#### <a name="to-align-to-grouped-controls"></a>Chcete-li zarovnat seskupené ovládací prvky  
  
1.  Vyberte dva ovládací prvky na formuláři. Přesunutí výběru a poznamenejte si zarovnávacích čar, které zobrazí mezi svůj výběr a další ovládací prvky.  
  
2.  Přetáhněte <xref:System.Windows.Forms.GroupBox> ovládacího prvku **nástrojů** do formuláře.  
  
3.  Přetáhněte <xref:System.Windows.Forms.Button> ovládacího prvku **nástrojů** do <xref:System.Windows.Forms.GroupBox> ovládacího prvku.  
  
4.  Vyberte jednu z <xref:System.Windows.Forms.Button> ovládací prvky a přesuňte ji <xref:System.Windows.Forms.GroupBox> ovládacího prvku. Poznámka: zarovnávacích čar, které se zobrazí na okraji <xref:System.Windows.Forms.GroupBox> ovládacího prvku. Všimněte si také zarovnávacích čar, které se zobrazí na okraji <xref:System.Windows.Forms.Button> ovládací prvek, který je obsažen <xref:System.Windows.Forms.GroupBox> ovládacího prvku. Ovládací prvky, které jsou podřízené objekty daného ovládacího prvku kontejneru také podporují zarovnávacích čar.  
  
## <a name="using-snaplines-to-place-a-control-by-outlining-its-size"></a>Umístit ovládací prvek sbalením jeho velikost pomocí zarovnávacích čar  
 Pomáhají zarovnávacích čar je Zarovnat ovládací prvky při první umístění je ve formuláři.  
  
#### <a name="to-use-snaplines-to-place-a-control-by-outlining-its-size"></a>Umístěte ovládací prvek sbalením jeho velikost pomocí zarovnávacích čar  
  
1.  V **nástrojů**, klikněte na tlačítko <xref:System.Windows.Forms.Button> ikonu ovládacího prvku. Přetáhněte není ji na formuláři.  
  
2.  Přesuňte ukazatel myši nad návrhovou plochu formuláře. Všimněte si, že se ukazatel změní na křížek s <xref:System.Windows.Forms.Button> ikonu ovládací prvek připojen. Všimněte si také zarovnávacích čar, které zobrazí navrhnout zarovnané umístění <xref:System.Windows.Forms.Button> ovládacího prvku.  
  
3.  Klepněte a podržte tlačítko myši.  
  
4.  Přetažením ukazatele myši kolem formuláře. Všimněte si, že je vykreslován osnovy, určující pozici a velikost ovládacího prvku.  
  
5.  Přetažením ukazatele, dokud nebude zarovnán s dalším ovládacím prvkem na formuláři. Všimněte si, že se zobrazí snapline – k označení zarovnání.  
  
6.  Uvolněte tlačítko myši. Ovládací prvek je vytvořen na umístění a velikost indikován osnovy.  
  
## <a name="using-snaplines-when-dragging-a-control-from-the-toolbox"></a>Při přetažení ovládacího prvku z panelu nástrojů pomocí zarovnávacích čar  
 Usnadňují zarovnávacích čar zarovnání řídí, kdy přetáhněte je z **nástrojů** do formuláře.  
  
#### <a name="to-use-snaplines-when-dragging-a-control-from-the-toolbox"></a>Chcete-li pomocí zarovnávacích čar při přetažení ovládacího prvku z panelu nástrojů  
  
1.  Přetáhněte <xref:System.Windows.Forms.Button> řízení z **nástrojů** do formuláře, ale ne uvolněte tlačítko myši.  
  
2.  Přesuňte ukazatel myši nad návrhovou plochu formuláře. Všimněte si, že ukazatel se změní pozici, na kterou nový <xref:System.Windows.Forms.Button> ovládací prvek bude vytvořen.  
  
3.  Přetažením ukazatele myši kolem formuláře. Mějte na paměti zarovnávacích čar, které zobrazí navrhnout zarovnané umístění <xref:System.Windows.Forms.Button> ovládacího prvku. Umožňuje najdete pozici, která je v souladu s další ovládací prvky.  
  
4.  Uvolněte tlačítko myši. Ovládací prvek je vytvořen na pozici zarovnávacích čar.  
  
## <a name="resizing-controls-using-snaplines"></a>Změna velikosti ovládacích prvků pomocí zarovnávacích čar  
 Zarovnávacích čar, které vám pomohou Zarovnat ovládací prvky, jak změnit jejich velikost.  
  
#### <a name="to-resize-a-control-using-snaplines"></a>Pro změnu velikosti ovládacího prvku s použitím zarovnávacích čar  
  
1.  Přetáhněte <xref:System.Windows.Forms.Button> ovládacího prvku **nástrojů** do formuláře.  
  
2.  Změnit velikost <xref:System.Windows.Forms.Button> uchopíte jeho jeden úchyty pro změnu velikosti a přetažením rohu pod kontrolou. Podrobnosti najdete v tématu [jak: Změna velikosti ovládacích prvků ve Windows Forms](../../../../docs/framework/winforms/controls/how-to-resize-controls-on-windows-forms.md).  
  
3.  Přetáhněte úchyt pro změnu velikosti dobu, než <xref:System.Windows.Forms.Button> ohraničení ovládacího prvku zarovnán s dalším ovládacím prvkem. Všimněte si, že se zobrazí snapline –. Všimněte si také, že přitahuje pozici snapline – úchyt pro změnu velikosti.  
  
4.  Změnit velikost <xref:System.Windows.Forms.Button> ovládacího prvku v různých pokynů a zarovnat úchyt pro změnu velikosti na různé ovládací prvky. Všimněte si, jak zarovnávacích čar zobrazují v různých orientace k označení zarovnání.  
  
## <a name="aligning-a-label-to-a-controls-text"></a>Zarovnání popisku na Text ovládacího prvku  
 Některé ovládací prvky nabídky snapline – pro zarovnání jiných ovládacích prvků zobrazený text.  
  
#### <a name="to-align-a-label-to-a-controls-text"></a>Chcete-li zarovnat popisek pro text ovládacího prvku  
  
1.  Přetáhněte <xref:System.Windows.Forms.TextBox> ovládacího prvku **nástrojů** do formuláře. Když přetáhnete <xref:System.Windows.Forms.TextBox> ovládací prvek na formuláři klikněte smart piktogram a vyberte **nastavit text textBox1** možnost. Podrobnosti najdete v tématu [názorný postup: Provádění obecných úloh pomocí inteligentních značek v Windows Forms ovládací prvky](../../../../docs/framework/winforms/controls/performing-common-tasks-using-smart-tags-on-wf-controls.md).  
  
2.  Přetáhněte <xref:System.Windows.Forms.Label> ovládacího prvku **nástrojů** do formuláře.  
  
3.  Změňte hodnotu <xref:System.Windows.Forms.Label> ovládacího prvku <xref:System.Windows.Forms.Control.AutoSize%2A> vlastnost `true`. Všimněte si, že ohraničení ovládacího prvku jsou přizpůsobeny zobrazení textu.  
  
4.  Přesunout <xref:System.Windows.Forms.Label> ovládacího prvku na levé straně <xref:System.Windows.Forms.TextBox> řídit, takže je zarovnáno s dolní hranou <xref:System.Windows.Forms.TextBox> ovládacího prvku. Všimněte si snapline –, který se zobrazí podél dolního okraje dvou ovládacích prvků.  
  
5.  Přesunout <xref:System.Windows.Forms.Label> ovládací prvek mírně nahoru, dokud <xref:System.Windows.Forms.Label> text a <xref:System.Windows.Forms.TextBox> je text zarovnán. Všimněte si, jinak upravený snapline –, který se zobrazí, určující, kdy jsou zarovnané textová pole ovládacích prvků.  
  
## <a name="using-snaplines-with-keyboard-navigation"></a>Pomocí zarovnávacích čar navigaci pomocí klávesnice  
 Abyste zakázali pomáhají zarovnávacích čar řídí, kdy jsou uspořádání pomocí kláves se šipkami.  
  
#### <a name="to-use-snaplines-with-keyboard-navigation"></a>Pomocí zarovnávacích čar navigaci pomocí klávesnice  
  
1.  Přetáhněte <xref:System.Windows.Forms.Button> ovládacího prvku **nástrojů** do formuláře. Umístěte ho do levého horního rohu formuláře.  
  
2.  Stisknutím klávesy CTRL + ŠIPKA DOLŮ. Všimněte si, že ovládací prvek přesune na první místo k dispozici vodorovné zarovnání dolů formuláře.  
  
3.  Stisknutím klávesy CTRL + ŠIPKA dolů, dokud nedosáhne ovládacího prvku dolní části formuláře. Poznamenejte si umístění, které zabírá při jejich přesunu dolů formuláře.  
  
4.  Stisknutím klávesy CTRL + ŠIPKA vpravo. Všimněte si, že ovládací prvek přesune na první místo k dispozici svislé zarovnání přes celý formulář.  
  
5.  Stisknutím klávesy CTRL + Šipka doprava, dokud nedosáhne stranách formuláře ovládací prvek. Poznamenejte si umístění, které zabírá při jejich přesunu přes celý formulář.  
  
6.  Přesuňte ovládání kolem formuláři pomocí kombinace kláves se šipkami. Poznamenejte si umístění, které zabírá ovládacího prvku a zarovnávacích čar, které musí být.  
  
7.  Stiskněte SHIFT + libovolná klávesa se šipkou pro změnu velikosti <xref:System.Windows.Forms.Button> ovládací prvek vždy o jeden pixel.  
  
8.  Stiskněte kombinaci kláves CTRL + SHIFT + libovolná klávesa se šipkou pro změnu velikosti <xref:System.Windows.Forms.Button> ovládacího prvku v přírůstcích po snapline –.  
  
## <a name="snaplines-and-layout-panels"></a>Zarovnávacích čar a panely rozložení  
 V rámci panely rozložení jsou zakázány zarovnávacích čar.  
  
#### <a name="to-selectively-disable-snaplines"></a>K selektivnímu zakázání zarovnávacích čar  
  
1.  Přetáhněte <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku **nástrojů** do formuláře.  
  
2.  Dvakrát klikněte <xref:System.Windows.Forms.Button> ikonu ovládacího prvku v **nástrojů**. Všimněte si, že nový ovládací prvek tlačítko se zobrazí v <xref:System.Windows.Forms.TableLayoutPanel> první buňky ovládacího prvku.  
  
3.  Dvakrát klikněte <xref:System.Windows.Forms.Button> ikonu ovládacího prvku v **nástrojů** dvakrát více. Kvůli tomu jednu prázdnou buňku v <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku.  
  
4.  Přetáhněte <xref:System.Windows.Forms.Button> řízení z **nástrojů** do prázdné buňky <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku. Všimněte si, že žádné zarovnávacích čar zobrazí.  
  
5.  Přetáhněte <xref:System.Windows.Forms.Button> řízení z celkového počtu <xref:System.Windows.Forms.TableLayoutPanel> řídit a přesuňte ji <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku. Všimněte si, že zarovnávacích čar znovu nezobrazí.  
  
## <a name="disabling-snaplines"></a>Zakázání zarovnávacích čar  
 Ve výchozím nastavení jsou zapnuté zarovnávacích čar. Zarovnávacích čar můžete zakázat jednotlivě, nebo je můžete zakázat v návrhovém prostředí.  
  
#### <a name="to-selectively-disable-snaplines"></a>K selektivnímu zakázání zarovnávacích čar  
  
-   Stiskněte klávesu ALT a při přesunutí ovládacího prvku kolem formuláře.  
  
     Všimněte si, že zobrazovat žádné zarovnávacích čar a ovládací prvek není Přichytit k všechny potenciální zarovnání pozic.  
  
#### <a name="to-disable-snaplines-in-the-design-environment"></a>Chcete-li zakázat zarovnávacích čar v prostředí návrhu  
  
1.  Z **nástroje** nabídky, otevřete **možnosti** dialogové okno. Otevřete dialogové okno návrháře formulářů Windows. Podrobnosti najdete v tématu [Obecné, Návrhář formulářů Windows, dialogové okno Možnosti](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/5aazxs78(v=vs.100)).  
  
2.  Vyberte **Obecné** uzlu. V **režim rozložení** oddíl, změna výběru z **zarovnávacích čar** k **SnapToGrid**.  
  
3.  Klikněte na tlačítko OK, použijte nastavení.  
  
4.  Vyberte ovládací prvek na formuláři a pohybujte jím další ovládací prvky. Všimněte si, že nejsou zobrazeny zarovnávacích čar.  
  
## <a name="next-steps"></a>Další kroky  
 Zarovnávacích čar nabízejí intuitivní dopravních zarovnání ovládacích prvků na formuláři. Návrhy pro další zkoumání patří:  
  
-   Zkuste vnoření <xref:System.Windows.Forms.GroupBox> ovládacího prvku v jiném <xref:System.Windows.Forms.GroupBox> ovládacího prvku. Místo <xref:System.Windows.Forms.Button> ovládací prvek v rámci podřízené <xref:System.Windows.Forms.GroupBox> ovládacího prvku a druhý v rámci nadřazené <xref:System.Windows.Forms.GroupBox> ovládacího prvku. Přesunout <xref:System.Windows.Forms.Button> kolem ovládacích prvků a v tématu Jak zarovnávacích čar překračují hranice kontejneru.  
  
-   Vytvořte sloupec <xref:System.Windows.Forms.TextBox> ovládací prvky a odpovídající sloupec <xref:System.Windows.Forms.Label> ovládacích prvků. Nastavte hodnotu <xref:System.Windows.Forms.Label> ovládacích prvků <xref:System.Windows.Forms.Control.AutoSize%2A> vlastnost `true`. Pomocí zarovnávacích čar můžete přesunout <xref:System.Windows.Forms.Label> řídí tak jejich zobrazovaného textu je v souladu s textu <xref:System.Windows.Forms.TextBox> ovládacích prvků.  
  
 Informace o návrhu uživatelských rozhraní Windows najdete v tématu knihy *činnost koncového uživatele Microsoft Windows, oficiální pokyny pro uživatelské rozhraní vývojářů a návrhářů* Redmond, WA: Microsoft Press, 1999. (USBN: 0-7356-0566-1).  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Forms.Design.Behavior.SnapLine>
- [Návod: Uspořádání ovládacích prvků na formuláři Windows s použitím ovládacího prvku FlowLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [Návod: Uspořádání ovládacích prvků na formuláři Windows s použitím ovládacího prvku TableLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [Návod: Vytváření rozložení Windows Forms ovládací prvky s odsazením, okraji a s vlastností AutoSize](../../../../docs/framework/winforms/controls/windows-forms-controls-padding-autosize.md)
- [Uspořádávání ovládacích prvků ve Windows Forms](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)
