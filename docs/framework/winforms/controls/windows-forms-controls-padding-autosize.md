---
title: 'Návod: Rozvrhování ovládacích prvků Windows Forms s odsazením, okraji a s vlastností AutoSize'
ms.date: 03/30/2017
f1_keywords:
- Margin.Bottom
- Margin.Left
- Margin.Top
- Margin.All
- Margin.Right
helpviewer_keywords:
- Margin property [Windows Forms], walkthroughs
- walkthroughs [Windows Forms], layout
- AutoSize property [Windows Forms], walkthroughs
- Padding property [Windows Forms], walkthroughs
- layout [Windows Forms], margins and padding
- Windows Forms, layout
ms.assetid: f8ae2a6b-db13-4630-8e25-d104091205c7
ms.openlocfilehash: 8e5763bd64049ee5f3d00c3489ec0c6a35fd58f8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33541629"
---
# <a name="walkthrough-laying-out-windows-forms-controls-with-padding-margins-and-the-autosize-property"></a>Návod: Rozvrhování ovládacích prvků Windows Forms s odsazením, okraji a s vlastností AutoSize
Přesné umístění ovládacích prvků ve formuláři je důležitá pro mnoho aplikací. **Návrhář formulářů Windows** nabízí celou řadu nástrojů rozložení toho chcete dosáhnout. Tři nejdůležitějších jsou <xref:System.Windows.Forms.Control.Margin%2A>, <xref:System.Windows.Forms.Control.Padding%2A>, a <xref:System.Windows.Forms.Control.AutoSize%2A> vlastnosti, které jsou k dispozici na všech ovládacích prvků Windows Forms.  
  
 <xref:System.Windows.Forms.Control.Margin%2A> Vlastnost definuje prostor okolo ovládacího prvku, který udržuje další ovládací prvky zadaná vzdálenost od ohraničení ovládacího prvku.  
  
 <xref:System.Windows.Forms.Control.Padding%2A> Vlastnost definuje místo uvnitř ovládacího prvku, který uchovává obsah ovládacího prvku (například hodnota jeho <xref:System.Windows.Forms.Control.Text%2A> vlastnost) zadaná vzdálenost od ohraničení ovládacího prvku.  
  
 Následující obrázek ukazuje <xref:System.Windows.Forms.Control.Padding%2A> a <xref:System.Windows.Forms.Control.Margin%2A> vlastnosti ovládacího prvku.  
  
 ![Odsazení a okrajů pro Windows Forms – ovládací prvky](../../../../docs/framework/winforms/controls/media/vs-winformpadmargin.gif "VS_WinFormPadMargin")  
  
 <xref:System.Windows.Forms.Control.AutoSize%2A> Vlastnost informuje ovládacím prvkem, který automaticky sama velikost k jejímu obsahu. Ho nebudou měnit velikost tak být menší než hodnota původních <xref:System.Windows.Forms.Control.Size%2A> vlastnost a bude účet pro hodnotu jeho <xref:System.Windows.Forms.Control.Padding%2A> vlastnost.  
  
 Úkoly v tomto návodu zahrnují:  
  
-   Vytvoření projektu modelu Windows Forms  
  
-   Nastavení okrajů pro vaše ovládací prvky  
  
-   Nastavení odsazení pro vaše ovládací prvky  
  
-   Automaticky Změna velikosti ovládacích prvků  
  
 Jakmile budete hotovi, budete mít představu o úloze, kterou tyto funkce důležité rozložení.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu, budete potřebovat:  
  
-   Dostatečná oprávnění, abyste mohli vytvořit a spustit projekty aplikací Windows Forms v počítači, kde je nainstalován Visual Studio.  
  
## <a name="creating-the-project"></a>Vytvoření projektu  
 Prvním krokem je vytvoření projektu a nastavte formulář.  
  
#### <a name="to-create-the-project"></a>Vytvoření projektu  
  
1.  Vytvoření **aplikace Windows** projekt s názvem `LayoutExample`. Další informace najdete v tématu [postupy: vytvoření projektu aplikace Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) .  
  
2.  Vybrat formuláře v **Návrhář formulářů Windows**.  
  
## <a name="setting-margins-for-your-controls"></a>Nastavení okrajů pro vaše ovládací prvky  
 Můžete nastavit výchozí vzdálenost mezi vaší ovládacích prvků pomocí <xref:System.Windows.Forms.Control.Margin%2A> vlastnost. Při přesunutí ovládacího prvku blízko jiného ovládacího prvku, zobrazí se snapline, který ukazuje okraje dvou ovládacích prvků. Ovládací prvek, který přesouváte se také přichytí k vzdálenost definované pravého okraje.  
  
#### <a name="to-arrange-controls-on-your-form-using-the-margin-property"></a>K uspořádání ovládacích prvků na formuláři pomocí vlastnosti rozpětí  
  
1.  Přetáhněte dva <xref:System.Windows.Forms.Button> z ovládací prvky **sada nástrojů** do formuláře.  
  
2.  Vyberte jednu z <xref:System.Windows.Forms.Button> ovládací prvky a přesunout ho blízko dalších, dokud jsou téměř zásahu.  
  
     Sledujte snapline, který se zobrazí mezi nimi. Tato vzdálenost je součet dvou ovládacích prvků <xref:System.Windows.Forms.Control.Margin%2A> hodnoty. Ovládací prvek, který přesouváte Připnutí tento vzdálenost. Podrobnosti najdete v tématu [návod: uspořádání ovládacích prvků ve Windows Forms pomocí zarovnávacích čar](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).  
  
3.  Změna <xref:System.Windows.Forms.Control.Margin%2A> vlastnost ovládacího prvku, rozšířením <xref:System.Windows.Forms.Control.Margin%2A> položku v **vlastnosti** okno a nastavení <xref:System.Windows.Forms.Padding.All%2A> vlastnost až 20 číslic.  
  
4.  Vyberte jednu z <xref:System.Windows.Forms.Button> ovládací prvky a přesunout ho blízko dalších.  
  
     Snapline definování je delší, aby součet hodnot okraj a ovládacího prvku přichytí k větší vzdálenosti z jiných ovládacího prvku.  
  
5.  Změna <xref:System.Windows.Forms.Control.Margin%2A> vlastnost vybraný ovládací prvek rozšířením <xref:System.Windows.Forms.Control.Margin%2A> položku v **vlastnosti** okno a nastavení <xref:System.Windows.Forms.Padding.Top%2A> na 5.  
  
6.  Přesunout vybraný ovládací prvek pod ostatní ovládací prvek a zkontrolujte, zda je snapline kratší. Přesunout vybraný ovládací prvek nalevo od jiných ovládací prvek a zkontrolujte, že snapline uchovává hodnotu dodržen v kroku 4.  
  
7.  Můžete nastavit těchto aspektů <xref:System.Windows.Forms.Control.Margin%2A> vlastnost <xref:System.Windows.Forms.Padding.Left%2A>, <xref:System.Windows.Forms.Padding.Top%2A>, <xref:System.Windows.Forms.Padding.Right%2A>, <xref:System.Windows.Forms.Padding.Bottom%2A>, různé hodnoty, nebo můžete nastavit všechny na stejnou hodnotu s <xref:System.Windows.Forms.Padding.All%2A> vlastnost.  
  
## <a name="setting-padding-for-your-controls"></a>Nastavení odsazení pro vaše ovládací prvky  
 K dosažení přesné rozložení potřebné pro vaši aplikaci, bude vaše ovládací prvky často obsahují podřízených ovládacích prvků. Pokud chcete určit blízkosti ohraničení ovládacího prvku podřízené ohraničení nadřazeného ovládacího prvku, použijte nadřazeného ovládacího prvku <xref:System.Windows.Forms.Control.Padding%2A> vlastnost ve spojení s ovládacím prvkem podřízené <xref:System.Windows.Forms.Control.Margin%2A> vlastnost. <xref:System.Windows.Forms.Control.Padding%2A> Vlastnost je také použít k řízení blízko obsah ovládacího prvku (například <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Text%2A> vlastnost) k jeho hranice.  
  
#### <a name="to-arrange-controls-on-your-form-using-padding"></a>K uspořádání ovládacích prvků na formuláři pomocí odsazení  
  
1.  Přetáhněte <xref:System.Windows.Forms.Button> řídit z **sada nástrojů** do formuláře.  
  
2.  Změňte hodnotu <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.AutoSize%2A> vlastnost `true`.  
  
3.  Změna <xref:System.Windows.Forms.Control.Padding%2A> vlastnost rozšířením <xref:System.Windows.Forms.Control.Padding%2A> položku v **vlastnosti** okno a nastavení <xref:System.Windows.Forms.Padding.All%2A> na 5.  
  
     Ovládací prvek rozšíří zajistit místo pro nové odsazení.  
  
4.  Přetáhněte <xref:System.Windows.Forms.GroupBox> řídit z **sada nástrojů** do formuláře. Přetáhněte <xref:System.Windows.Forms.Button> řídit z **sada nástrojů** do <xref:System.Windows.Forms.GroupBox> ovládacího prvku. Pozice <xref:System.Windows.Forms.Button> řídit tak, aby byl roviny s pravém horním rohu <xref:System.Windows.Forms.GroupBox> ovládacího prvku.  
  
     Sledovat zarovnávací čáry, která se zobrazí jako <xref:System.Windows.Forms.Button> řízení blíží dolní a pravé okraje <xref:System.Windows.Forms.GroupBox> ovládacího prvku. Tyto zarovnávací čáry odpovídají <xref:System.Windows.Forms.Control.Margin%2A> vlastnost <xref:System.Windows.Forms.Button>.  
  
5.  Změna <xref:System.Windows.Forms.GroupBox> ovládacího prvku <xref:System.Windows.Forms.Control.Padding%2A> vlastnost rozšířením <xref:System.Windows.Forms.Control.Padding%2A> položku v **vlastnosti** okno a nastavení <xref:System.Windows.Forms.Padding.All%2A> vlastnost až 20 číslic.  
  
6.  Vyberte <xref:System.Windows.Forms.Button> řízení v rámci <xref:System.Windows.Forms.GroupBox> řízení a přesunout ho na střed <xref:System.Windows.Forms.GroupBox>.  
  
     Zarovnávací čáry zobrazují ve větší vzdálenosti ohraničení <xref:System.Windows.Forms.GroupBox> ovládacího prvku. Tato vzdálenost je součet hodnot <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Margin%2A> vlastnost a <xref:System.Windows.Forms.GroupBox> ovládacího prvku <xref:System.Windows.Forms.Control.Padding%2A> vlastnost.  
  
## <a name="automatically-sizing-your-controls"></a>Automaticky Změna velikosti ovládacích prvků  
 V některých aplikacích velikosti ovládacího prvku nebudou stejná v době běhu stejně jako tomu bylo v době návrhu. Text <xref:System.Windows.Forms.Button> řízení, může provést třeba z databáze, a jeho délka nesmí být známé předem.  
  
 Když <xref:System.Windows.Forms.Control.AutoSize%2A> je nastavena na `true`, ovládacího prvku samotné velikost na jeho obsah. Další informace najdete v tématu [přehled vlastnosti AutoSize](../../../../docs/framework/winforms/controls/autosize-property-overview.md).  
  
#### <a name="to-arrange-controls-on-your-form-using-the-autosize-property"></a>K uspořádání ovládacích prvků na formuláři pomocí vlastnosti AutoSize  
  
1.  Přetáhněte <xref:System.Windows.Forms.Button> řídit z **sada nástrojů** do formuláře.  
  
2.  Změňte hodnotu <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.AutoSize%2A> vlastnost `true`.  
  
3.  Změna <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Text%2A> vlastnost "**toto tlačítko je dlouhý řetězec pro vlastnost Text**."  
  
     Pokud provedete změny, <xref:System.Windows.Forms.Button> řízení změní, aby se vešel nový text do.  
  
4.  Přetáhněte další <xref:System.Windows.Forms.Button> řídit z **sada nástrojů** do formuláře.  
  
5.  Změna <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Text%2A> vlastnost "**toto tlačítko je dlouhý řetězec pro vlastnost Text.**"  
  
     Pokud provedete změny, <xref:System.Windows.Forms.Button> ovládací prvek není velikost sebe sama a text je oříznut podle pravé hrany ovládacího prvku.  
  
6.  Změna <xref:System.Windows.Forms.Control.Padding%2A> vlastnost rozšířením <xref:System.Windows.Forms.Control.Padding%2A> položku v **vlastnosti** okno a nastavení <xref:System.Windows.Forms.Padding.All%2A> na 5.  
  
     Text v interior ovládacího prvku je oříznut na všechny čtyři strany.  
  
7.  Změna <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.AutoSize%2A> vlastnost `true`.  
  
     <xref:System.Windows.Forms.Button> Řízení změní samotné zahrnuje celý řetězec. Navíc se přidal odsazení kolem textu, způsobuje <xref:System.Windows.Forms.Button> řízení rozbalte v všechny čtyři směrech.  
  
8.  Přetáhněte <xref:System.Windows.Forms.Button> řídit z **sada nástrojů** do formuláře. Umístěním v pravém dolním rohu formuláře.  
  
9. Změňte hodnotu <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.AutoSize%2A> vlastnost `true`.  
  
10. Nastavte <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Anchor%2A> vlastnost <xref:System.Windows.Forms.AnchorStyles.Right>, <xref:System.Windows.Forms.AnchorStyles.Bottom>.  
  
11. Změna <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Text%2A> vlastnost "**toto tlačítko je dlouhý řetězec pro vlastnost Text.**"  
  
     Pokud provedete změny, <xref:System.Windows.Forms.Button> řízení změní samotné směrem doleva. Obecně platí, automatická změna velikosti zvýší velikost ovládacího prvku v opačném směru jeho <xref:System.Windows.Forms.Control.Anchor%2A> nastavení vlastnosti.  
  
## <a name="autosize-and-autosizemode-properties"></a>AutoSize a AutoSizeMode vlastnosti  
 Některé ovládací prvky podporují `AutoSizeMode` vlastnosti, která vám dává větší kontrolu nad chováním Automatická změna velikosti ovládacího prvku.  
  
#### <a name="to-use-the-autosizemode-property"></a>Použít AutoSizeMode – vlastnost  
  
1.  Přetáhněte <xref:System.Windows.Forms.Panel> řídit z **sada nástrojů** do formuláře.  
  
2.  Nastavte hodnotu <xref:System.Windows.Forms.Panel> ovládacího prvku <xref:System.Windows.Forms.Control.AutoSize%2A> vlastnost `true`.  
  
3.  Přetáhněte <xref:System.Windows.Forms.Button> řídit z **sada nástrojů** do <xref:System.Windows.Forms.Panel> ovládacího prvku.  
  
4.  Místo <xref:System.Windows.Forms.Button> ovládací prvek v pravém dolním rohu <xref:System.Windows.Forms.Panel> ovládacího prvku.  
  
5.  Vyberte <xref:System.Windows.Forms.Panel> řízení a získat pravém úchyt. Změnit velikost <xref:System.Windows.Forms.Panel> ovládacího prvku větší a menší.  
  
    > [!NOTE]
    >  Můžete libovolně změnit velikost <xref:System.Windows.Forms.Panel> řízení, ale nemůže velikost je menší než pozici <xref:System.Windows.Forms.Button> ovládacího prvku pravém dolním rohu. Toto chování je zadána výchozí hodnota `AutoSizeMode` vlastnost, která je <xref:System.Windows.Forms.AutoSizeMode.GrowOnly>.  
  
6.  Nastavte hodnotu <xref:System.Windows.Forms.Panel> ovládacího prvku `AutoSizeMode` vlastnost <xref:System.Windows.Forms.AutoSizeMode.GrowAndShrink>.  
  
     <xref:System.Windows.Forms.Panel> Řízení velikosti samotné obklopit <xref:System.Windows.Forms.Button> ovládacího prvku. Nelze změnit velikost <xref:System.Windows.Forms.Panel> ovládacího prvku.  
  
7.  Přetáhněte <xref:System.Windows.Forms.Button> řízení směrem k levém horním rohu <xref:System.Windows.Forms.Panel> ovládacího prvku.  
  
     <xref:System.Windows.Forms.Panel> Řízení změní tak, aby <xref:System.Windows.Forms.Button> nové pozice ovládacího prvku.  
  
## <a name="next-steps"></a>Další kroky  
 Existuje mnoho dalších funkcí rozložení pro uspořádání ovládacích prvků v aplikacích Windows Forms. Zde jsou některé kombinace, které můžete vyzkoušet:  
  
-   Sestavení formuláře pomocí <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku. Podrobnosti najdete v tématu [návod: uspořádání ovládacích prvků ve Windows Forms pomocí ovládacího prvku TableLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md). Změňte hodnoty <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku <xref:System.Windows.Forms.Control.Padding%2A> vlastnost, a taky <xref:System.Windows.Forms.Control.Margin%2A> vlastnost na jeho podřízených ovládacích prvků.  
  
-   Zkuste na stejném experimentu pomocí <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku. Podrobnosti najdete v tématu [návod: uspořádání ovládacích prvků ve Windows Forms pomocí ovládacího prvku FlowLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md).  
  
-   Experiment s ukotvení podřízených ovládacích prvků v <xref:System.Windows.Forms.Panel> ovládacího prvku. <xref:System.Windows.Forms.Control.Padding%2A> Vlastnost je obecnější realizaci <xref:System.Windows.Forms.ScrollableControl.DockPadding%2A> vlastnost a může stát odpovědí na sami, je-li tomu umístěním podřízený ovládací prvek <xref:System.Windows.Forms.Panel> řízení a nastavení podřízeného ovládacího prvku <xref:System.Windows.Forms.Control.Dock%2A> vlastnost <xref:System.Windows.Forms.DockStyle.Fill>. Nastavte <xref:System.Windows.Forms.Panel> ovládacího prvku <xref:System.Windows.Forms.Control.Padding%2A> vlastnost různé hodnoty a Poznámka účinek.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.Control.AutoSize%2A>  
 <xref:System.Windows.Forms.ScrollableControl.DockPadding%2A>  
 <xref:System.Windows.Forms.Control.Margin%2A>  
 <xref:System.Windows.Forms.Control.Padding%2A>  
 [Přehled vlastnosti AutoSize](../../../../docs/framework/winforms/controls/autosize-property-overview.md)  
 [Postupy: Uspořádání ovládacích prvků na Windows Forms s použitím ovládacího prvku TableLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  
 [Postupy: Uspořádání ovládacích prvků na formuláři Windows Forms s použitím ovládacího prvku FlowLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)  
 [Návod: Uspořádání ovládacích prvků ve Windows Forms pomocí zarovnávacích čar](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
