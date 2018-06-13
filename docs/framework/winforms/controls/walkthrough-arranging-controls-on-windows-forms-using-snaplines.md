---
title: 'Návod: Uspořádání ovládacích prvků ve Windows Forms pomocí zarovnávacích čar'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], arranging with snaplines
- snaplines [Windows Forms], arranging Windows Forms controls
- SnapLine class [Windows Forms], walkthroughs
- Windows Forms controls, arranging
ms.assetid: d5c9edc7-cf30-4a97-8ebe-201d569340f8
ms.openlocfilehash: f8e8122f82bc6a8c4fab17b8b73c07d08bab4d26
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33541587"
---
# <a name="walkthrough-arranging-controls-on-windows-forms-using-snaplines"></a>Návod: Uspořádání ovládacích prvků ve Windows Forms pomocí zarovnávacích čar
Přesné umístění ovládacích prvků ve formuláři je důležitá pro mnoho aplikací. Návrhář formulářů Windows poskytuje celou řadu nástrojů rozložení toho chcete dosáhnout. Jedním z nejdůležitějších je <xref:System.Windows.Forms.Design.Behavior.SnapLine> funkce.  
  
 Zarovnávací čáry zobrazit přesněji místo sestavení ovládacích prvků s dalšími kontrolami. Také ukazují doporučené vzdálenosti pro okraje mezi ovládacími prvky podle specifikace rozhraní pokyny pro uživatele systému Windows. Podrobnosti najdete v tématu [uživatelské rozhraní návrh a vývoj](http://go.microsoft.com/FWLink/?LinkId=83878).  
  
 Zarovnávací čáry usnadňují zarovnat vaše ovládací prvky pro ostré, profesionální vzhled a chování (vzhled a chování).  
  
 Úkoly v tomto návodu zahrnují:  
  
-   Vytvoření projektu modelu Windows Forms  
  
-   Mezer a zarovnání ovládacích prvků pomocí zarovnávacích čar  
  
-   Zarovnání formuláře a okraje kontejneru  
  
-   Zarovnání na seskupené ovládací prvky  
  
-   Pomocí zarovnávacích čar umístíte ovládací prvek seznamu vytvořit jeho velikost  
  
-   Pomocí zarovnávacích čar při přetažení ovládacího prvku z panelu nástrojů  
  
-   Změna velikosti ovládacích prvků pomocí zarovnávacích čar  
  
-   Zarovnání štítek pro Text ovládacího prvku  
  
-   Zarovnávací čáry pomocí klávesnice navigace  
  
-   Zarovnávací čáry a panelů rozložení  
  
-   Zakázání zarovnávací čáry  
  
 Jakmile budete hotovi, budete mít představu o rozložení úloze, kterou funkci zarovnávací čáry.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="creating-the-project"></a>Vytvoření projektu  
 Prvním krokem je vytvoření projektu a nastavte formulář.  
  
#### <a name="to-create-the-project"></a>Vytvoření projektu  
  
1.  Vytvořte projekt aplikace pro systém Windows s názvem "SnaplineExample". Podrobnosti najdete v tématu [postupy: vytvoření projektu aplikace Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
2.  Vyberte formuláře v Návrháři formulářů.  
  
## <a name="spacing-and-aligning-controls-using-snaplines"></a>Mezer a zarovnání ovládacích prvků pomocí zarovnávacích čar  
 Zarovnávací čáry poskytují přesné a intuitivní způsob zarovnání ovládacích prvků formuláře. Zobrazí se při přesunování vybraný ovládací prvek nebo ovládací prvky blízkosti pozice, který by zarovnané s další ovládací prvek nebo sadu ovládacích prvků. Výběr "přichyceno" navrhované pozici při přemísťování za jiných ovládacích prvků.  
  
#### <a name="to-arrange-controls-using-snaplines"></a>K uspořádání ovládacích prvků pomocí zarovnávacích čar  
  
1.  Přetáhněte <xref:System.Windows.Forms.Button> řídit z **sada nástrojů** do formuláře.  
  
2.  Přesunout <xref:System.Windows.Forms.Button> řízení pravém dolním rohu formuláře. Poznámka: zarovnávací čáry, která se zobrazí jako <xref:System.Windows.Forms.Button> řízení blíží dolní a pravé ohraničení tvaru. Tyto zarovnávací čáry zobrazit doporučené vzdálenost mezi ohraničení ovládacího prvku a formuláře.  
  
3.  Přesunout <xref:System.Windows.Forms.Button> řízení kolem ohraničení tvaru a Všimněte si, kde se zobrazí zarovnávací čáry. Po dokončení přesunout <xref:System.Windows.Forms.Button> řízení téměř středu tvaru.  
  
4.  Přetáhněte další <xref:System.Windows.Forms.Button> řídit z **sada nástrojů** do formuláře.  
  
5.  Přesunout druhý <xref:System.Windows.Forms.Button> řízení, dokud je téměř úroveň s prvním. Poznamenejte si snapline, které se zobrazuje v textu účaří obě tlačítka a Všimněte si, že ovládací prvek, který přesouváte Připnutí do pozice, který je právě úroveň s další ovládací prvek.  
  
6.  Přesunout druhý <xref:System.Windows.Forms.Button> řízení, dokud je umístěný přímo nad první. Všimněte si zarovnávací čáry, která se zobrazují podél levé a pravé hrany obě tlačítka a poznamenejte si, že ovládací prvek jste přesunutí rozehrávkách byli do pozice, který je právě v souladu s další ovládací prvek.  
  
7.  Vyberte jednu z <xref:System.Windows.Forms.Button> ovládací prvky a přesunout ho blízko dalších, dokud jsou téměř zásahu. Poznámka: snapline, který se zobrazí mezi nimi. Tato vzdálenost je doporučené vzdálenost mezi ohraničením ovládacích prvků. Všimněte si také, že ovládací prvek, který přesouváte Připnutí do tohoto umístění.  
  
8.  Přetáhněte dva <xref:System.Windows.Forms.Panel> z ovládací prvky **sada nástrojů** do formuláře.  
  
9. Přesunutí mezi <xref:System.Windows.Forms.Panel> prvky, dokud je téměř úroveň s prvním. Všimněte si zarovnávací čáry, která se zobrazují podél horní a dolní hrany oba ovládací prvky a Všimněte si, že ovládací prvek, který přesouváte Připnutí do pozice, který je právě úroveň s další ovládací prvek.  
  
## <a name="aligning-to-form-and-container-margins"></a>Zarovnání formuláře a okraje kontejneru  
 Zarovnávací čáry slouží k zarovnání vaše ovládací prvky na formuláři a kontejner okraje konzistentním způsobem.  
  
#### <a name="to-align-controls-to-form-and-container-margins"></a>Chcete-li zarovnat ovládací prvky na formuláři a kontejner okraje  
  
1.  Vyberte jednu z <xref:System.Windows.Forms.Button> ovládací prvky a přesunout ho blízko pravého ohraničení tvaru, dokud se nezobrazí snapline. Snapline vzdálenost od pravého okraje. je součet hodnot ovládacího prvku <xref:System.Windows.Forms.Control.Margin%2A> vlastnost a formuláře <xref:System.Windows.Forms.Control.Padding%2A> hodnot vlastností.  
  
> [!NOTE]
>  Pokud formuláře <xref:System.Windows.Forms.Control.Padding%2A> je nastavena na 0,0,0,0, Návrhář formulářů Windows poskytuje formuláře stíněné <xref:System.Windows.Forms.Control.Padding%2A> hodnotu 9,9,9,9. Chcete-li toto chování potlačit přiřadíte jinou hodnotu než 0,0,0,0.  
  
1.  Změňte hodnotu <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Margin%2A> vlastnost rozšířením <xref:System.Windows.Forms.Control.Margin%2A> položku v **vlastnosti** okno a nastavení <xref:System.Windows.Forms.Padding.All%2A> vlastnost na hodnotu 0. Podrobnosti najdete v tématu [návod:, kterým se ovládacích prvků Windows Forms s odsazením, okraji a s vlastností AutoSize](../../../../docs/framework/winforms/controls/windows-forms-controls-padding-autosize.md).  
  
2.  Přesunout <xref:System.Windows.Forms.Button> řízení blízko pravého ohraničení tvaru, dokud se nezobrazí snapline. Tato vzdálenost je nyní dána hodnotou formuláře <xref:System.Windows.Forms.Control.Padding%2A> vlastnost.  
  
3.  Přetáhněte <xref:System.Windows.Forms.GroupBox> řídit z **sada nástrojů** do formuláře.  
  
4.  Změňte hodnotu <xref:System.Windows.Forms.GroupBox> ovládacího prvku <xref:System.Windows.Forms.Control.Padding%2A> vlastnost rozšířením <xref:System.Windows.Forms.Control.Padding%2A> položku v **vlastnosti** okno a nastavení <xref:System.Windows.Forms.Padding.All%2A> vlastnost na hodnotu 10.  
  
5.  Přetáhněte <xref:System.Windows.Forms.Button> řídit z **sada nástrojů** do <xref:System.Windows.Forms.GroupBox> ovládacího prvku.  
  
6.  Přesunout <xref:System.Windows.Forms.Button> řízení blízko na pravý okraj <xref:System.Windows.Forms.GroupBox> řízení, dokud se nezobrazí snapline. Přesunout <xref:System.Windows.Forms.Button> řízení v rámci <xref:System.Windows.Forms.GroupBox> řízení a Všimněte si, kde se zobrazí zarovnávací čáry.  
  
## <a name="aligning-to-grouped-controls"></a>Zarovnání na seskupené ovládací prvky  
 Zarovnávací čáry můžete zarovnat skupina ovládacích prvků také jako ovládací prvky v rámci <xref:System.Windows.Forms.GroupBox> ovládacího prvku.  
  
#### <a name="to-align-to-grouped-controls"></a>Chcete-li zarovnat na seskupené ovládací prvky  
  
1.  Vyberte dva ovládacích prvků na formuláři. Posun výběru a Všimněte si zarovnávací čáry, která se objeví mezi výběr a jiných ovládacích prvků.  
  
2.  Přetáhněte <xref:System.Windows.Forms.GroupBox> řídit z **sada nástrojů** do formuláře.  
  
3.  Přetáhněte <xref:System.Windows.Forms.Button> řídit z **sada nástrojů** do <xref:System.Windows.Forms.GroupBox> ovládacího prvku.  
  
4.  Vyberte jednu z <xref:System.Windows.Forms.Button> ovládací prvky a přesunout ji <xref:System.Windows.Forms.GroupBox> ovládacího prvku. Poznámka: zarovnávací čáry, která se zobrazí na okrajích <xref:System.Windows.Forms.GroupBox> ovládacího prvku. Všimněte si také zarovnávací čáry, která se zobrazí na okrajích <xref:System.Windows.Forms.Button> ovládací prvek, který je obsažený v <xref:System.Windows.Forms.GroupBox> ovládacího prvku. Ovládací prvky, které jsou podřízené položky ovládacího prvku kontejner také podporují zarovnávací čáry.  
  
## <a name="using-snaplines-to-place-a-control-by-outlining-its-size"></a>Pomocí zarovnávacích čar umístíte ovládací prvek seznamu vytvořit jeho velikost  
 Zarovnávací čáry nápovědy, které můžete zarovnat řídí, kdy nejprve jejich umístění na formuláři.  
  
#### <a name="to-use-snaplines-to-place-a-control-by-outlining-its-size"></a>Umístěte ovládací prvek seznamu vytvořit jeho velikost pomocí zarovnávacích čar  
  
1.  V **sada nástrojů**, klikněte na tlačítko <xref:System.Windows.Forms.Button> ikonu ovládacího prvku. Přetáhněte není jej do formuláře.  
  
2.  Přesuňte ukazatel myši nad formuláře návrhovou plochu. Všimněte si, že se nezmění na záměrný kříž s <xref:System.Windows.Forms.Button> řízení ikonu připojen. Všimněte si také zarovnávací čáry, která zobrazí navrhovat zarovnaný pozice pro <xref:System.Windows.Forms.Button> ovládacího prvku.  
  
3.  Klikněte na tlačítko a podržte tlačítko myši.  
  
4.  Přetáhněte ukazatel myši kolem formuláře. Všimněte si, že je vykreslován přehled, znamenající pozice a velikosti ovládacího prvku.  
  
5.  Přetáhněte ukazatele, dokud nebude zarovnán s další ovládací prvek na formuláři. Všimněte si, že se zobrazí snapline udávajících zarovnání.  
  
6.  Uvolnění tlačítka myši. Ovládací prvek se vytvoří v umístění a velikost indikován obrys.  
  
## <a name="using-snaplines-when-dragging-a-control-from-the-toolbox"></a>Pomocí zarovnávacích čar při přetažení ovládacího prvku z panelu nástrojů  
 Zarovnávací čáry usnadňují zarovnání ovládací prvky při přetažení z **sada nástrojů** do formuláře.  
  
#### <a name="to-use-snaplines-when-dragging-a-control-from-the-toolbox"></a>Použití zarovnávací čáry při přetažení ovládacího prvku z panelu nástrojů  
  
1.  Přetáhněte <xref:System.Windows.Forms.Button> řídit z **sada nástrojů** do formuláře, ale není uvolnění tlačítka myši.  
  
2.  Přesuňte ukazatel myši nad formuláře návrhovou plochu. Upozorňujeme, že má ukazatel změní označující pozici, na kterou nový <xref:System.Windows.Forms.Button> ovládací prvek bude vytvořen.  
  
3.  Přetáhněte ukazatel myši kolem formuláře. Všimněte si zarovnávací čáry, která zobrazí navrhovat zarovnaný pozice pro <xref:System.Windows.Forms.Button> ovládacího prvku. Najít pozice, který je v souladu s další ovládací prvky.  
  
4.  Uvolnění tlačítka myši. Ovládací prvek je vytvořen v pozici zarovnávací čáry.  
  
## <a name="resizing-controls-using-snaplines"></a>Změna velikosti ovládacích prvků pomocí zarovnávacích čar  
 Zarovnávací čáry, které vám pomohou při změně velikosti je zarovnání ovládacích prvků.  
  
#### <a name="to-resize-a-control-using-snaplines"></a>Ke změně velikosti ovládacího prvku s použitím zarovnávacích čar  
  
1.  Přetáhněte <xref:System.Windows.Forms.Button> řídit z **sada nástrojů** do formuláře.  
  
2.  Změnit velikost <xref:System.Windows.Forms.Button> kontrola s metodou jeden rohu úchyty a přetažením. Podrobnosti najdete v tématu [postupy: Změna velikosti ovládacích prvků ve Windows Forms](../../../../docs/framework/winforms/controls/how-to-resize-controls-on-windows-forms.md).  
  
3.  Přetažením úchytu dobu, než <xref:System.Windows.Forms.Button> ohraničení ovládacího prvku je zarovnáno s další ovládací prvek. Všimněte si, že se zobrazí snapline. Všimněte si také, že úchyt Připnutí na pozici snapline.  
  
4.  Změnit velikost <xref:System.Windows.Forms.Button> řízení v různých směrech a align úchyt na různých ovládacích prvků. Všimněte si, jak se zobrazují zarovnávací čáry v různých orientaci označíte, zarovnání.  
  
## <a name="aligning-a-label-to-a-controls-text"></a>Zarovnání štítek pro Text ovládacího prvku  
 Některé ovládací prvky nabízejí snapline pro zarovnání dalších ovládacích prvků zobrazený text.  
  
#### <a name="to-align-a-label-to-a-controls-text"></a>Chcete-li zarovnat štítek pro text ovládacího prvku  
  
1.  Přetáhněte <xref:System.Windows.Forms.TextBox> řídit z **sada nástrojů** do formuláře. Když je vyřadit <xref:System.Windows.Forms.TextBox> na formuláři ovládací prvek, klikněte na tlačítko glyfy chytré značky a vyberte **nastavte text na textBox1** možnost. Podrobnosti najdete v tématu [návod: provádění běžných úloh pomocí inteligentních značek v ovládacích prvcích Windows Forms](../../../../docs/framework/winforms/controls/performing-common-tasks-using-smart-tags-on-wf-controls.md).  
  
2.  Přetáhněte <xref:System.Windows.Forms.Label> řídit z **sada nástrojů** do formuláře.  
  
3.  Změňte hodnotu <xref:System.Windows.Forms.Label> ovládacího prvku <xref:System.Windows.Forms.Control.AutoSize%2A> vlastnost `true`. Všimněte si, že ohraničení ovládacího prvku tak, aby vyhovovaly zobrazovaný text.  
  
4.  Přesunout <xref:System.Windows.Forms.Label> řízení nalevo od <xref:System.Windows.Forms.TextBox> řídit, takže je zarovnáno s dolní hranou <xref:System.Windows.Forms.TextBox> ovládacího prvku. Poznámka: snapline, který se zobrazí podél dolního okraje dvou ovládacích prvků.  
  
5.  Přesunout <xref:System.Windows.Forms.Label> řízení mírně nahoru, dokud <xref:System.Windows.Forms.Label> text a <xref:System.Windows.Forms.TextBox> text je zarovnán. Všimněte si, jinak stylem snapline, který se zobrazí, která udává, kdy je zarovnán textová pole ovládacích prvků.  
  
## <a name="using-snaplines-with-keyboard-navigation"></a>Zarovnávací čáry pomocí klávesnice navigace  
 Zarovnávací čáry nápovědy, které můžete zarovnat řídí, kdy jsou uspořádání pomocí klávesy se šipkami na klávesnici.  
  
#### <a name="to-use-snaplines-with-keyboard-navigation"></a>Pro použití s navigační klávesnice zarovnávací čáry  
  
1.  Přetáhněte <xref:System.Windows.Forms.Button> řídit z **sada nástrojů** do formuláře. Umístěte jej v levém horním rohu formuláře.  
  
2.  Stisknutím kombinace kláves CTRL + ŠIPKA DOLŮ. Všimněte si, že ovládací prvek se posouvá směrem dolů formuláře na první pozici k dispozici vodorovné zarovnání.  
  
3.  Stisknutím CTRL + ŠIPKA dolů, dokud nedosáhne dolní části formuláře ovládacího prvku. Všimněte si, pozice, kterou zabírá při jejich přesunu dolů formuláře.  
  
4.  Stiskněte kombinaci kláves CTRL + ŠIPKA vpravo. Všimněte si, že ovládací prvek přesune mezi formuláři na první pozici k dispozici svislé zarovnání.  
  
5.  Stisknutím CTRL + ŠIPKA vpravo, dokud nedosáhne ovládacího prvku na straně formuláře. Všimněte si, pozice, kterou zabírá při jejich přesunu napříč formuláře.  
  
6.  Přesuňte kolem formuláře ovládacího prvku s kombinací klávesy se šipkami. Poznamenejte si umístění, které zabírá ovládacího prvku a zarovnávací čáry, která musí být.  
  
7.  Stiskněte SHIFT + libovolná klávesa se šipkou ke změně velikosti <xref:System.Windows.Forms.Button> řízení vždy o jeden pixel.  
  
8.  Stiskněte kombinaci kláves CTRL + SHIFT + libovolná klávesa se šipkou ke změně velikosti <xref:System.Windows.Forms.Button> ovládací prvek v přírůstcích po snapline.  
  
## <a name="snaplines-and-layout-panels"></a>Zarovnávací čáry a panelů rozložení  
 Zarovnávací čáry jsou zakázané v rámci panelů rozložení.  
  
#### <a name="to-selectively-disable-snaplines"></a>Chcete-li selektivně zakázat zarovnávací čáry  
  
1.  Přetáhněte <xref:System.Windows.Forms.TableLayoutPanel> řídit z **sada nástrojů** do formuláře.  
  
2.  Dvakrát klikněte <xref:System.Windows.Forms.Button> ikonu ovládacího prvku v **sada nástrojů**. Všimněte si, že nový ovládací prvek tlačítko se zobrazí v <xref:System.Windows.Forms.TableLayoutPanel> první buňky ovládacího prvku.  
  
3.  Dvakrát klikněte <xref:System.Windows.Forms.Button> ikonu ovládacího prvku v **sada nástrojů** dvakrát Další. Zůstane jeden prázdné buňky v <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku.  
  
4.  Přetáhněte <xref:System.Windows.Forms.Button> řídit z **sada nástrojů** do prázdné buňky <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku. Všimněte si, že žádné zarovnávací čáry zobrazí.  
  
5.  Přetáhněte <xref:System.Windows.Forms.Button> řízení mimo <xref:System.Windows.Forms.TableLayoutPanel> řízení a přesunout ji <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku. Všimněte si, že zarovnávací čáry objeví znovu.  
  
## <a name="disabling-snaplines"></a>Zakázání zarovnávací čáry  
 Zarovnávací čáry jsou ve výchozím nastavení zapnuté. Můžete selektivně zakázat zarovnávací čáry, nebo je můžete zakázat v prostředí návrhu.  
  
#### <a name="to-selectively-disable-snaplines"></a>Chcete-li selektivně zakázat zarovnávací čáry  
  
-   Stisknutím klávesy ALT a při přesunutím ovládacího prvku kolem formuláře.  
  
     Všimněte si, že zobrazovat žádné zarovnávacích čar a ovládací prvek není Přichytit k všechny potenciální pozic zarovnání.  
  
#### <a name="to-disable-snaplines-in-the-design-environment"></a>Chcete-li zakázat zarovnávací čáry v prostředí návrhu  
  
1.  Z **nástroje** nabídky, otevřete **možnosti** dialogové okno. Otevřete dialogové okno Návrhář formulářů Windows. Podrobnosti najdete v tématu [Návrhář formulářů Windows Obecné, dialogové okno Možnosti](http://msdn.microsoft.com/library/8dd170af-72f0-4212-b04b-034ceee92834).  
  
2.  Vyberte **Obecné** uzlu. V **rozložení režimu** část, změňte výběr z **zarovnávacích čar** k **SnapToGrid**.  
  
3.  Klikněte na tlačítko OK a použijte nastavení.  
  
4.  Vyberte ovládací prvek na formuláři a pohyb jiných ovládacích prvků. Všimněte si, že se nezobrazí zarovnávací čáry.  
  
## <a name="next-steps"></a>Další kroky  
 Zarovnávací čáry nabízejí intuitivní způsob zarovnání ovládacích prvků na formuláři. Návrhy na další průzkum patří:  
  
-   Zkuste vnoření <xref:System.Windows.Forms.GroupBox> ovládací prvek v rámci jiného <xref:System.Windows.Forms.GroupBox> ovládacího prvku. Místní <xref:System.Windows.Forms.Button> ovládací prvek v rámci podřízených <xref:System.Windows.Forms.GroupBox> řízení a jiné v rámci nadřazeného <xref:System.Windows.Forms.GroupBox> ovládacího prvku. Přesunout <xref:System.Windows.Forms.Button> ovládací prvky přibližně chcete zjistit, jak zarovnávací čáry mezi hranice kontejneru.  
  
-   Vytvořit sloupec <xref:System.Windows.Forms.TextBox> ovládacích prvků a odpovídající sloupec <xref:System.Windows.Forms.Label> ovládací prvky. Nastavte hodnotu <xref:System.Windows.Forms.Label> ovládací prvky se <xref:System.Windows.Forms.Control.AutoSize%2A> vlastnost `true`. Pokud chcete přesunout pomocí zarovnávacích čar <xref:System.Windows.Forms.Label> ovládací prvky, jejich zobrazený text je zarovnán s textem v <xref:System.Windows.Forms.TextBox> ovládací prvky.  
  
 Informace o návrh uživatelského rozhraní systému Windows, najdete v příručce *uživatelské prostředí Microsoft Windows, oficiální pokyny pro uživatelské rozhraní vývojářů a návrhářů,* Brno: společnosti Microsoft Press, 1999. (USBN: 0-7356-0566-1).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.Design.Behavior.SnapLine>  
 [Postupy: Uspořádání ovládacích prvků na formuláři Windows Forms s použitím ovládacího prvku FlowLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)  
 [Postupy: Uspořádání ovládacích prvků na Windows Forms s použitím ovládacího prvku TableLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  
 [Návod: Rozvrhování ovládacích prvků Windows Forms s odsazením, okraji a s vlastností AutoSize](../../../../docs/framework/winforms/controls/windows-forms-controls-padding-autosize.md)  
 [Uspořádávání ovládacích prvků ve Windows Forms](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)
