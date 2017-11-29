---
title: "Postupy: Uspořádání ovládacích prvků na formuláři Windows s použitím ovládacího prvku FlowLayoutPanel"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- FlowLayoutPanel control [Windows Forms], walkthroughs
- Windows Forms controls, arranging
- controls [Windows Forms], arranging with FlowLayoutPanel
- layout [Windows Forms], walkthroughs
ms.assetid: a1744323-0316-49c2-992e-ebfc0a976b85
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 84b909f0c638bf0fb7c19ecc3a86c7c32bab2adb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel"></a>Postupy: Uspořádání ovládacích prvků na formuláři Windows s použitím ovládacího prvku FlowLayoutPanel
Některé aplikace vyžadují formulář s rozložení, který samotné uspořádá správně při změně velikosti formuláře nebo se mění velikosti obsahu. Pokud potřebujete dynamické rozložení a nechcete zpracovat <xref:System.Windows.Forms.Control.Layout> události explicitně v kódu, zvažte pomocí panelů rozložení.  
  
 <xref:System.Windows.Forms.FlowLayoutPanel> Řízení a <xref:System.Windows.Forms.TableLayoutPanel> řízení nabízejí intuitivní způsoby uspořádání ovládacích prvků na formuláři. Obě zadejte automatická, konfigurovat možnosti řízení relativní umístění podřízených ovládacích prvků v nich obsažená a obě získáte funkce dynamické rozložení v době běhu, takže jejich velikost a umístění můžete podřízené ovládací prvky jako rozměry nadřazeného formuláře změníte. Panelů rozložení lze začlenit do panelů rozložení, povolit provádění sofistikované uživatelská rozhraní.  
  
 <xref:System.Windows.Forms.TableLayoutPanel> Uspořádá jeho obsah v mřížce, zajištění funkcí, které jsou podobné HTML \<tabulky > elementu. Jeho buněk jsou uspořádány do řádků a sloupců, a to může mít různou velikost. Další informace najdete v tématu [návod: uspořádání ovládacích prvků ve Windows Forms pomocí ovládacího prvku TableLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).  
  
 <xref:System.Windows.Forms.FlowLayoutPanel> Uspořádá jeho obsah v směr konkrétní toku: vodorovně nebo svisle. Jeho obsah může být uzavřen z jeden řádek na další, nebo z jednoho sloupce na další. Alternativně může být jeho obsah oříznut místo uzavřen. Úkoly v tomto návodu zahrnují:  
  
-   Vytvoření projektu modelu Windows Forms  
  
-   Uspořádání ovládacích prvků vodorovně a svisle  
  
-   Změna směr toku  
  
-   Vkládání zalomení toku  
  
-   Uspořádání ovládacích prvků pomocí odsazení a okraje  
  
-   Vkládání ovládacích prvků poklepáním na tyto v panelu nástrojů  
  
-   Vložení ovládacího prvku pomocí kreslení obrysu  
  
-   Vkládání ovládacích prvků pomocí pomocí kurzoru  
  
-   Nové přiřazení existujících ovládacích prvků jinému nadřazenému prvku  
  
 Jakmile budete hotovi, budete mít představu o úloze, kterou tyto funkce důležité rozložení.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="creating-the-project"></a>Vytvoření projektu  
 Prvním krokem je vytvoření projektu a nastavte formulář.  
  
#### <a name="to-create-the-project"></a>Vytvoření projektu  
  
1.  Vytvořte projekt aplikace pro systém Windows s názvem "FlowLayoutPanelExample". Další informace najdete v tématu [postupy: vytvoření projektu aplikace Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
2.  Vybrat formuláře v **Návrhář formulářů**.  
  
## <a name="arranging-controls-horizontally-and-vertically"></a>Uspořádání ovládacích prvků vodorovně a svisle  
 <xref:System.Windows.Forms.FlowLayoutPanel> Řízení umožňuje umístit ovládací prvky k řádky nebo sloupce, aniž by bylo potřeba přesněji určit umístění každého jednotlivého ovládacího prvku.  
  
 <xref:System.Windows.Forms.FlowLayoutPanel> Řízení můžete změnit velikost nebo přeformátování jeho podřízených ovládacích prvků jako dimenze pro změnu nadřazené formuláře.  
  
#### <a name="to-arrange-controls-horizontally-and-vertically-using-a-flowlayoutpanel"></a>K uspořádání ovládacích prvků vodorovně a svisle pomocí ovládacího prvku FlowLayoutPanel  
  
1.  Přetáhněte <xref:System.Windows.Forms.FlowLayoutPanel> řídit z **sada nástrojů** do formuláře.  
  
2.  Přetáhněte <xref:System.Windows.Forms.Button> řídit z **sada nástrojů** do <xref:System.Windows.Forms.FlowLayoutPanel>. Všimněte si, že se automaticky přesune do levého horního rohu <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku.  
  
3.  Přetáhněte další <xref:System.Windows.Forms.Button> řídit z **sada nástrojů** do <xref:System.Windows.Forms.FlowLayoutPanel>. Všimněte si, že <xref:System.Windows.Forms.Button> ovládací prvek se automaticky přesune do polohy vedle první <xref:System.Windows.Forms.Button> ovládacího prvku. Pokud vaše <xref:System.Windows.Forms.FlowLayoutPanel> je příliš úzké podle dvou ovládacích prvků na stejném řádku nové <xref:System.Windows.Forms.Button> řízení se automaticky přesune na další řádek.  
  
4.  Přetáhněte několik dalších <xref:System.Windows.Forms.Button> z ovládací prvky **sada nástrojů** do <xref:System.Windows.Forms.FlowLayoutPanel>. Pokračovat v umístění <xref:System.Windows.Forms.Button> prvky, dokud jeden zabalí na další řádek.  
  
5.  Změňte hodnotu <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku <xref:System.Windows.Forms.FlowLayoutPanel.WrapContents%2A> vlastnost `false`. Všimněte si, že podřízené prvky už toku na další řádek. Místo toho se přesunout na první řádek a oříznuta.  
  
6.  Změňte hodnotu <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku <xref:System.Windows.Forms.FlowLayoutPanel.WrapContents%2A> vlastnost `true`. Všimněte si, že podřízené prvky znovu wrap na další řádek.  
  
7.  Snížit šířku <xref:System.Windows.Forms.FlowLayoutPanel> řízení až všechny <xref:System.Windows.Forms.Button> ovládací prvky přesunou do prvního sloupce.  
  
8.  Zvětšit šířku <xref:System.Windows.Forms.FlowLayoutPanel> řízení až všechny <xref:System.Windows.Forms.Button> ovládací prvky přesunou do prvního řádku. Budete muset změnit velikost formuláře aby dokázala pojmout větší šířku.  
  
## <a name="changing-flow-direction"></a>Změna směr toku  
 <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> Vlastnost vám umožní změnit směr, ve kterém jsou uspořádány ovládací prvky. Podřízené ovládací prvky zleva doprava, můžete z uspořádat zprava doleva od začátku do konce nebo zdola nahoru.  
  
#### <a name="to-change-the-flow-direction-in-a-flowlayoutpanel"></a>Chcete-li změnit směr toku v ovládacího prvku FlowLayoutPanel  
  
1.  Změňte hodnotu <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> vlastnost <xref:System.Windows.Forms.FlowDirection.TopDown>. Všimněte si, že jsou přeskupení podřízených ovládacích prvků do jednoho nebo více sloupců, v závislosti na výšku ovládacího prvku.  
  
2.  Změnit velikost <xref:System.Windows.Forms.FlowLayoutPanel> tak jeho výšku je kratší než sloupec <xref:System.Windows.Forms.Button> ovládací prvky. Všimněte si, že <xref:System.Windows.Forms.FlowLayoutPanel> Přeuspořádá podřízených ovládacích prvků, které jsou předávány do další sloupce. I nadále snížení výšku a Všimněte si, že podřízená řídí tok do po sobě jdoucích sloupců. Změňte hodnotu <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> vlastnost <xref:System.Windows.Forms.FlowDirection.RightToLeft>. Všimněte si, že jsou obrácený pozic podřízených ovládacích prvků. Sledovat rozložení, když změníte hodnotu <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> vlastnost <xref:System.Windows.Forms.FlowDirection.BottomUp>.  
  
## <a name="inserting-flow-breaks"></a>Vkládání zalomení toku  
 <xref:System.Windows.Forms.FlowLayoutPanel> Řízení poskytuje vlastnosti FlowBreak a jeho podřízených ovládacích prvků. Nastavení hodnoty vlastnosti FlowBreak `true` způsobí, že <xref:System.Windows.Forms.FlowLayoutPanel> řízení zastavit rozložení ovládacích prvků v aktuální směr toku a wrap na další řádek nebo sloupec.  
  
#### <a name="to-insert-flow-breaks"></a>Chcete-li vložit zalomení toku  
  
1.  Změňte hodnotu <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> vlastnost <xref:System.Windows.Forms.FlowDirection.TopDown>.  
  
2.  Vyberte jednu z <xref:System.Windows.Forms.Button> ovládací prvky průběhu levém sloupci.  
  
3.  Nastavte hodnotu <xref:System.Windows.Forms.Button> FlowBreak ovládacího prvku na `true`. Všimněte si, sloupec je poškozený a ovládací prvky následující vybraný <xref:System.Windows.Forms.Button> řízení toku v dalším sloupci. Nastavte hodnotu <xref:System.Windows.Forms.Button> FlowBreak ovládacího prvku na `false` se vraťte do původní chování.  
  
## <a name="positioning-controls-using-docking-and-anchoring"></a>Umístění ovládacích prvků pomocí ukotvení a ukotvení  
 Ukotvení a ukotvení podřízených ovládacích prvků chování se liší od chování v další ovládací prvky kontejneru. Ukotvení i ukotvení jsou relativní vzhledem k největší ovládacího prvku směr toku.  
  
#### <a name="to-position-controls-using-docking-and-anchoring"></a>Na pozici ovládacích prvků pomocí ukotvení a ukotvení  
  
1.  Zvětšete velikost <xref:System.Windows.Forms.FlowLayoutPanel> dokud <xref:System.Windows.Forms.Button> ovládací prvky jsou uspořádány ve sloupci.  
  
2.  Vyberte horní <xref:System.Windows.Forms.Button> ovládacího prvku. Zvětšit šířku tak, aby se o dvakrát širší jako druhý <xref:System.Windows.Forms.Button> ovládací prvky.  
  
3.  Vyberte druhý <xref:System.Windows.Forms.Button> ovládacího prvku. Změna hodnoty jeho <xref:System.Windows.Forms.Control.Anchor%2A> vlastnost <xref:System.Windows.Forms.AnchorStyles.Right>. Všimněte si, že se přesune tak, aby jeho pravého okraje. je zarovnán s prvním <xref:System.Windows.Forms.Button> pravého ohraničení ovládacího prvku.  
  
4.  Změna hodnoty jeho <xref:System.Windows.Forms.Control.Anchor%2A> vlastnost <xref:System.Windows.Forms.AnchorStyles.Right> a <xref:System.Windows.Forms.AnchorStyles.Left>. Všimněte si, že je velikost stejné šířky jako první <xref:System.Windows.Forms.Button> ovládacího prvku.  
  
5.  Vyberte třetí <xref:System.Windows.Forms.Button> ovládacího prvku. Změna hodnoty jeho <xref:System.Windows.Forms.Control.Dock%2A> vlastnost <xref:System.Windows.Forms.DockStyle.Fill>. Všimněte si, že je velikost stejné šířky jako první <xref:System.Windows.Forms.Button> ovládacího prvku.  
  
## <a name="arranging-controls-using-padding-and-margins"></a>Uspořádání ovládacích prvků pomocí odsazení a okraje  
 Můžete také uspořádat ovládacích prvků v vaše <xref:System.Windows.Forms.FlowLayoutPanel> řízení změnou <xref:System.Windows.Forms.Control.Padding%2A> a <xref:System.Windows.Forms.Control.Margin%2A> vlastnosti.  
  
 <xref:System.Windows.Forms.Control.Padding%2A> Vlastnost umožňuje řídit umístění ovládacích prvků v rámci <xref:System.Windows.Forms.FlowLayoutPanel> buňky ovládacího prvku. Určuje mezery mezi podřízených ovládacích prvků a <xref:System.Windows.Forms.FlowLayoutPanel> ohraničení ovládacího prvku.  
  
 <xref:System.Windows.Forms.Control.Margin%2A> Vlastnost umožňuje řídit mezer mezi ovládacími prvky.  
  
#### <a name="to-arrange-controls-using-the-padding-and-margin-properties"></a>K uspořádání ovládacích prvků pomocí vlastnosti odsazení a okraje  
  
1.  Změňte hodnotu <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku <xref:System.Windows.Forms.Control.Dock%2A> vlastnost <xref:System.Windows.Forms.DockStyle.Fill>. Pokud daný formulář je dostatečně velký <xref:System.Windows.Forms.Button> ovládací prvky budou přesunuty do první sloupec <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku.  
  
2.  Změňte hodnotu <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku <xref:System.Windows.Forms.Control.Padding%2A> vlastnost rozšířením <xref:System.Windows.Forms.Control.Padding%2A> položku v **vlastnosti** okno a nastavení <xref:System.Windows.Forms.Padding.All%2A> vlastnost **20**. Další informace najdete v tématu [návod:, kterým se ovládacích prvků Windows Forms s odsazením, okraji a s vlastností AutoSize](../../../../docs/framework/winforms/controls/windows-forms-controls-padding-autosize.md). Všimněte si, že podřízené ovládací prvky přesunou do středu <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku. Vyšší hodnota <xref:System.Windows.Forms.Control.Padding%2A> vlastnost nabízených oznámení podřízených ovládacích prvků směrem od <xref:System.Windows.Forms.FlowLayoutPanel> ohraničení ovládacího prvku.  
  
3.  Vyberte všechny <xref:System.Windows.Forms.Button> ovládacích prvků do <xref:System.Windows.Forms.FlowLayoutPanel> a nastavte hodnotu <xref:System.Windows.Forms.Control.Margin%2A> vlastnost **20**. Všimněte si, že mezery mezi <xref:System.Windows.Forms.Button> řídí nárůst, takže jejich přesunu dál od sebe. Budete muset změnit velikost <xref:System.Windows.Forms.FlowLayoutPanel> řízení musí být větší, aby se zobrazily všechny podřízené ovládací prvky.  
  
## <a name="inserting-controls-by-double-clicking-them-in-the-toolbox"></a>Vkládání ovládacích prvků poklepáním na tyto v panelu nástrojů  
 Jej můžete naplnit vaše <xref:System.Windows.Forms.FlowLayoutPanel> řízení ovládacích prvků v dvojitým kliknutím **sada nástrojů**.  
  
#### <a name="to-insert-controls-by-double-clicking-in-the-toolbox"></a>Chcete-li vložit ovládací prvky dvojitým kliknutím na soubor v panelu nástrojů  
  
1.  Dvakrát klikněte <xref:System.Windows.Forms.Button> ikonu ovládacího prvku v **sada nástrojů**. Všimněte si, že nový <xref:System.Windows.Forms.Button> zobrazí ovládací prvek v <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku.  
  
2.  Klikněte dvakrát na několik dalších ovládacích prvků v **sada nástrojů**. Zobrazit postupně v nových ovládacích prvků <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku.  
  
## <a name="inserting-a-control-by-drawing-its-outline"></a>Vložení ovládacího prvku pomocí kreslení obrysu  
 Můžete vložit do ovládacího prvku <xref:System.Windows.Forms.FlowLayoutPanel> řízení a kreslení obrysu v buňce zadejte jeho velikost.  
  
#### <a name="to-insert-a-control-by-drawing-its-outline"></a>Vložení ovládacího prvku pomocí kreslení obrysu  
  
1.  V **sada nástrojů**, klikněte na tlačítko <xref:System.Windows.Forms.Button> ikonu ovládacího prvku. Přetáhněte není jej do formuláře.  
  
2.  Přesuňte ukazatel myši <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku. Všimněte si, že se nezmění na záměrný kříž s <xref:System.Windows.Forms.Button> řízení ikonu připojen.  
  
3.  Klikněte na tlačítko a podržte tlačítko myši.  
  
4.  Přetáhněte ukazatel myši k vykreslení obrys <xref:System.Windows.Forms.Button> ovládacího prvku. Jakmile budete spokojeni s velikostí, uvolnění tlačítka myši. Všimněte si, že <xref:System.Windows.Forms.Button> ovládací prvek je vytvořen v další Otevřít umístění <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku.  
  
## <a name="inserting-controls-using-the-insertion-bar"></a>Vkládání ovládacích prvků pomocí panelu vložení  
 Ovládací prvky můžete vložit na konkrétní pozici v <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku. Při přetažení ovládacího prvku do <xref:System.Windows.Forms.FlowLayoutPanel> se zobrazí pruh pro vložení ovládacího prvku klientské oblasti, k označení, budou vloženy ovládacího prvku.  
  
#### <a name="to-insert-a-control-using-the-caret"></a>Vložení ovládacího prvku s použitím pomocí kurzoru  
  
1.  Přetáhněte <xref:System.Windows.Forms.Button> řídit z **sada nástrojů** do <xref:System.Windows.Forms.FlowLayoutPanel> řízení a přejděte do prostoru mezi dvěma <xref:System.Windows.Forms.Button> ovládací prvky. Všimněte si, že je vykreslován vložení řádku, která určuje, kde <xref:System.Windows.Forms.Button> budou umístěny při umístění do <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku. Před vyřazením nové <xref:System.Windows.Forms.Button> řízení do <xref:System.Windows.Forms.FlowLayoutPanel> řídit, přesuňte ukazatel myši přibližně, abyste viděli, jak přesune panelu vložení.  
  
2.  Vyřaďte nové <xref:System.Windows.Forms.Button> řízení do <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku. Všimněte si, že nové <xref:System.Windows.Forms.Button> ovládací prvek není zarovnána s ostatními, protože jeho <xref:System.Windows.Forms.Control.Margin%2A> vlastnost má jinou hodnotu.  
  
## <a name="reassigning-existing-controls-to-a-different-parent"></a>Nové přiřazení existujících ovládacích prvků jinému nadřazenému prvku  
 Můžete přiřadit ovládací prvky, které existují ve formuláři na nový <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku.  
  
#### <a name="to-reparent-existing-controls"></a>Chcete-li Nadřadit existujících ovládacích prvků  
  
1.  Přetáhněte tři <xref:System.Windows.Forms.Button> z ovládací prvky **sada nástrojů** do formuláře. Umístit je blízko sebe, ale nechte je nezarovnané.  
  
2.  V **sada nástrojů**, klikněte na tlačítko <xref:System.Windows.Forms.FlowLayoutPanel> ikonu ovládacího prvku. Přetáhněte není jej do formuláře.  
  
3.  Přesunutí ukazatele myši blízko tří <xref:System.Windows.Forms.Button> ovládací prvky. Všimněte si, že se nezmění na záměrný kříž s <xref:System.Windows.Forms.FlowLayoutPanel> řízení ikonu připojen.  
  
4.  Klikněte na tlačítko a podržte tlačítko myši.  
  
5.  Přetáhněte ukazatel myši k vykreslení obrys <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku. Kreslení obrys kolem tří <xref:System.Windows.Forms.Button> ovládací prvky.  
  
6.  Uvolnění tlačítka myši. Všimněte si, že tří <xref:System.Windows.Forms.Button> ovládací prvky jsou vloženy do <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku.  
  
## <a name="next-steps"></a>Další kroky  
 Komplexní rozložení pomocí kombinace panelů rozložení a ovládací prvky můžete dosáhnout. Návrhy na další průzkum patří:  
  
-   Změňte velikost jednoho z <xref:System.Windows.Forms.Button> ovládací prvky na větší velikost a Poznámka vliv na rozložení.  
  
-   Panelů rozložení může obsahovat další panely rozložení. Experiment s vyřazování <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku do existujícího ovládacího prvku.  
  
-   Ukotvení <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku do nadřazené formuláře. Změnit velikost formuláře a poznamenejte si vliv na rozložení.  
  
-   Nastavte <xref:System.Windows.Forms.Control.Visible%2A> vlastnost ovládací prvky `false` a Všimněte si, jak <xref:System.Windows.Forms.FlowLayoutPanel> přeteče v odpovědi.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.FlowLayoutPanel>  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 [Návod: Uspořádání ovládacích prvků na formuláři Windows s použitím ovládacího prvku TableLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  
 [Návod: Uspořádání ovládacích prvků ve Windows Forms pomocí zarovnávacích čar](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)  
 [Uživatelské prostředí pro Microsoft Windows, oficiální pokyny pro uživatelské rozhraní vývojářů a návrhářů. Brno: Společnosti Microsoft Press, 1999. (USBN: 0-7356-0566-1)](http://www.microsoft.com/mspress/southpacific/books/book11588.htm)  
 [Přehled vlastnosti AutoSize](../../../../docs/framework/winforms/controls/autosize-property-overview.md)  
 [Postupy: Ukotvování ovládacích prvků ve Windows Forms](../../../../docs/framework/winforms/controls/how-to-dock-controls-on-windows-forms.md)  
 [Postupy: Ukotvování ovládacích prvků ve Windows Forms](../../../../docs/framework/winforms/controls/how-to-anchor-controls-on-windows-forms.md)  
 [Návod: Rozvrhování Windows Forms – ovládací prvky s odsazením, okraji a s vlastností AutoSize](../../../../docs/framework/winforms/controls/windows-forms-controls-padding-autosize.md)
