---
title: 'Průvodce: Vytváření rozložení Windows Forms ovládací prvky s odsazením, okraji a s vlastností AutoSize'
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
ms.openlocfilehash: c92ea7b4cb2acbe84d9086698cdf8dfbf5f239bd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54738612"
---
# <a name="walkthrough-laying-out-windows-forms-controls-with-padding-margins-and-the-autosize-property"></a>Průvodce: Vytváření rozložení Windows Forms ovládací prvky s odsazením, okraji a s vlastností AutoSize
Přesné umístění ovládacích prvků na formuláři je důležitá pro mnoho aplikací. **Návrháře formulářů Windows** poskytuje celou řadu nástrojů rozložení, jak toho dosáhnout. Jsou tři z vašich nejdůležitějších <xref:System.Windows.Forms.Control.Margin%2A>, <xref:System.Windows.Forms.Control.Padding%2A>, a <xref:System.Windows.Forms.Control.AutoSize%2A> vlastnosti, které jsou k dispozici u všech ovládacích prvků Windows Forms.  
  
 <xref:System.Windows.Forms.Control.Margin%2A> Vlastnost definuje místa kolem ovládacího prvku, který udržuje další ovládací prvky určené vzdálenosti od ohraničení ovládacího prvku.  
  
 <xref:System.Windows.Forms.Control.Padding%2A> Vlastnost definuje pole uvnitř ovládacího prvku, který uchovává obsah ovládacího prvku (například, hodnota jeho <xref:System.Windows.Forms.Control.Text%2A> vlastnosti) určené vzdálenosti od ohraničení ovládacího prvku.  
  
 Je vidět na následujícím obrázku <xref:System.Windows.Forms.Control.Padding%2A> a <xref:System.Windows.Forms.Control.Margin%2A> vlastnosti na ovládacím prvku.  
  
 ![Odsazení a okraj Windows Forms ovládací prvky](../../../../docs/framework/winforms/controls/media/vs-winformpadmargin.gif "VS_WinFormPadMargin")  
  
 <xref:System.Windows.Forms.Control.AutoSize%2A> Vlastnost říká ovládací prvek automaticky přizpůsobovat svou velikost k jejímu obsahu. Jeho nebude sám být menší než hodnota jeho původní velikost <xref:System.Windows.Forms.Control.Size%2A> vlastnost a bude účet pro hodnoty jeho <xref:System.Windows.Forms.Control.Padding%2A> vlastnost.  
  
 Úlohy v tomto návodu zahrnují:  
  
-   Vytvoření projektu Windows Forms  
  
-   Nastavení okrajů pro vaše ovládací prvky  
  
-   Nastavení odsazení pro vaše ovládací prvky  
  
-   Automaticky Změna velikosti ovládacích prvků  
  
 Až budete hotovi, budete mít znalosti o úloze, kterou tyto funkce důležité rozložení.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat:  
  
-   Dostatečná oprávnění k vytvoření a spuštění projektů aplikace Windows Forms v počítači nainstalovanou aplikaci Visual Studio.  
  
## <a name="creating-the-project"></a>Vytvoření projektu  
 Prvním krokem je vytvoření projektu a nastavení formuláře.  
  
#### <a name="to-create-the-project"></a>Vytvoření projektu  
  
1.  Vytvoření **aplikace Windows** projekt s názvem `LayoutExample`. Další informace najdete v tématu [jak: Vytvoření projektu aplikace Windows](https://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) .  
  
2.  Vyberte formulář v nástrojích pro **Návrháře formulářů Windows**.  
  
## <a name="setting-margins-for-your-controls"></a>Nastavení okrajů pro vaše ovládací prvky  
 Můžete nastavit výchozí vzdálenost mezi pomocí ovládacích prvků <xref:System.Windows.Forms.Control.Margin%2A> vlastnost. Při přesunutí ovládacího prvku blízko k jinému ovládacímu prvku, zobrazí se snapline –, který zobrazuje okraje dvou ovládacích prvků. Ovládací prvek, který se přesouvají také přichycena k vzdálenost určené okraje.  
  
#### <a name="to-arrange-controls-on-your-form-using-the-margin-property"></a>Chcete-li uspořádat ovládací prvky na formuláři pomocí vlastnosti okraj  
  
1.  Přetáhněte dva <xref:System.Windows.Forms.Button> ovládacích prvků z **nástrojů** do formuláře.  
  
2.  Vyberte jednu z <xref:System.Windows.Forms.Button> ovládací prvky a přesuňte ho blízko druhé, dokud jsou téměř zásahu.  
  
     Sledujte snapline –, který se zobrazí mezi nimi. Toto je součet dvou ovládacích prvků <xref:System.Windows.Forms.Control.Margin%2A> hodnoty. Ovládací prvek, který se přesouvají přichytí k této vzdálenosti. Podrobnosti najdete v tématu [názorný postup: Uspořádání ovládacích prvků ve Windows Forms pomocí zarovnávacích čar](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).  
  
3.  Změnit <xref:System.Windows.Forms.Control.Margin%2A> vlastnosti ovládacích prvků tak, že rozbalíte <xref:System.Windows.Forms.Control.Margin%2A> položku v **vlastnosti** okno a nastavení <xref:System.Windows.Forms.Padding.All%2A> nastavte na 20.  
  
4.  Vyberte jednu z <xref:System.Windows.Forms.Button> ovládací prvky a přesuňte ho blízko druhé.  
  
     Snapline – definování je delší, aby součet hodnot okraj a ovládací prvek přichytí k větší vzdálenosti od jiného ovládacího prvku.  
  
5.  Změnit <xref:System.Windows.Forms.Control.Margin%2A> vlastností vybraného ovládacího prvku tak, že rozbalíte <xref:System.Windows.Forms.Control.Margin%2A> položku v **vlastnosti** okno a nastavení <xref:System.Windows.Forms.Padding.Top%2A> na 5.  
  
6.  Přesunout vybraný ovládací prvek pod ovládací prvek a podívejte se, že je snapline – kratší. Přesunout vybraný ovládací prvek vlevo od jiného ovládacího prvku a podívejte se, že snapline – uchovává hodnotu zjištěnou v kroku 4.  
  
7.  Můžete nastavit všech aspektů <xref:System.Windows.Forms.Control.Margin%2A> vlastnost <xref:System.Windows.Forms.Padding.Left%2A>, <xref:System.Windows.Forms.Padding.Top%2A>, <xref:System.Windows.Forms.Padding.Right%2A>, <xref:System.Windows.Forms.Padding.Bottom%2A>, různé hodnoty, nebo můžete nastavit vše na stejnou hodnotu s <xref:System.Windows.Forms.Padding.All%2A> vlastnost.  
  
## <a name="setting-padding-for-your-controls"></a>Nastavení odsazení pro vaše ovládací prvky  
 K dosažení požadované pro vaší aplikaci přesné rozložení ovládacích prvků často obsahovat podřízené ovládací prvky. Pokud chcete zadat blízkosti podřízený ovládací prvek ohraničení okraj nadřazený ovládací prvek, pomocí ovládacího prvku nadřazené <xref:System.Windows.Forms.Control.Padding%2A> vlastnost ve spojení s podřízený ovládací prvek <xref:System.Windows.Forms.Control.Margin%2A> vlastnost. <xref:System.Windows.Forms.Control.Padding%2A> Vlastnost se také používá k řízení blízkosti obsah ovládacího prvku (například <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Text%2A> vlastnosti) do jeho okrajů.  
  
#### <a name="to-arrange-controls-on-your-form-using-padding"></a>Chcete-li uspořádat ovládací prvky na formuláři pomocí odsazení  
  
1.  Přetáhněte <xref:System.Windows.Forms.Button> ovládacího prvku **nástrojů** do formuláře.  
  
2.  Změňte hodnotu <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.AutoSize%2A> vlastnost `true`.  
  
3.  Změnit <xref:System.Windows.Forms.Control.Padding%2A> vlastnost tak, že rozbalíte <xref:System.Windows.Forms.Control.Padding%2A> položku v **vlastnosti** okno a nastavení <xref:System.Windows.Forms.Padding.All%2A> na 5.  
  
     Ovládací prvek dá rozbalit, aby uvolnil prostor pro nové odsazení.  
  
4.  Přetáhněte <xref:System.Windows.Forms.GroupBox> ovládacího prvku **nástrojů** do formuláře. Přetáhněte <xref:System.Windows.Forms.Button> ovládacího prvku **nástrojů** do <xref:System.Windows.Forms.GroupBox> ovládacího prvku. Pozice <xref:System.Windows.Forms.Button> řídit tak, aby byl vyprázdnění se v pravém horním rohu <xref:System.Windows.Forms.GroupBox> ovládacího prvku.  
  
     Sledujte zarovnávacích čar, které se zobrazí jako <xref:System.Windows.Forms.Button> ovládací prvek blíží dolní a pravé ohraničení <xref:System.Windows.Forms.GroupBox> ovládacího prvku. Tyto zarovnávacích čar odpovídají <xref:System.Windows.Forms.Control.Margin%2A> vlastnost <xref:System.Windows.Forms.Button>.  
  
5.  Změnit <xref:System.Windows.Forms.GroupBox> ovládacího prvku <xref:System.Windows.Forms.Control.Padding%2A> vlastnost tak, že rozbalíte <xref:System.Windows.Forms.Control.Padding%2A> položku v **vlastnosti** okno a nastavení <xref:System.Windows.Forms.Padding.All%2A> nastavte na 20.  
  
6.  Vyberte <xref:System.Windows.Forms.Button> ovládacích prvků uvnitř <xref:System.Windows.Forms.GroupBox> ovládací prvek a jeho přesun směrem k středu <xref:System.Windows.Forms.GroupBox>.  
  
     Zarovnávacích čar budou zobrazovat ve větší vzdálenosti v ohraničení <xref:System.Windows.Forms.GroupBox> ovládacího prvku. Toto je součtem <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Margin%2A> vlastnost a <xref:System.Windows.Forms.GroupBox> ovládacího prvku <xref:System.Windows.Forms.Control.Padding%2A> vlastnost.  
  
## <a name="automatically-sizing-your-controls"></a>Automaticky Změna velikosti ovládacích prvků  
 V některých aplikacích velikosti ovládacího prvku nebudou stejné v době běhu jako byl v době návrhu. Text <xref:System.Windows.Forms.Button> ovládacího prvku, například může být přijata z databáze a jeho délka nesmí být předem známý.  
  
 Když <xref:System.Windows.Forms.Control.AutoSize%2A> je nastavena na `true`, ovládací prvek svoji velikost na jeho obsah. Další informace najdete v tématu [přehled vlastnosti AutoSize](../../../../docs/framework/winforms/controls/autosize-property-overview.md).  
  
#### <a name="to-arrange-controls-on-your-form-using-the-autosize-property"></a>Chcete-li uspořádat ovládací prvky na formuláři pomocí vlastnosti AutoSize  
  
1.  Přetáhněte <xref:System.Windows.Forms.Button> ovládacího prvku **nástrojů** do formuláře.  
  
2.  Změňte hodnotu <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.AutoSize%2A> vlastnost `true`.  
  
3.  Změnit <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Text%2A> vlastnost "**toto tlačítko má dlouhý řetězec pro vlastnost Text**."  
  
     Při potvrzení změn, <xref:System.Windows.Forms.Button> ovládací prvek mění podle nového textu.  
  
4.  Přetáhněte další <xref:System.Windows.Forms.Button> ovládacího prvku **nástrojů** do formuláře.  
  
5.  Změnit <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Text%2A> vlastnost "**toto tlačítko má dlouhý řetězec pro vlastnost Text.**"  
  
     Při potvrzení změn, <xref:System.Windows.Forms.Button> ovládací prvek není velikost sebe sama a text je oříznutý ořezovou pravým okrajem ovládacího prvku.  
  
6.  Změnit <xref:System.Windows.Forms.Control.Padding%2A> vlastnost tak, že rozbalíte <xref:System.Windows.Forms.Control.Padding%2A> položku v **vlastnosti** okno a nastavení <xref:System.Windows.Forms.Padding.All%2A> na 5.  
  
     Text v uvnitř ovládacího prvku se ořízne na všechny čtyři strany.  
  
7.  Změnit <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.AutoSize%2A> vlastnost `true`.  
  
     <xref:System.Windows.Forms.Button> Ovládací prvek mění zahrnuje celý řetězec. Navíc se přidala výplně kolem textu, což způsobí <xref:System.Windows.Forms.Button> ovládací prvek rozšíření ve všech čtyř směrů.  
  
8.  Přetáhněte <xref:System.Windows.Forms.Button> ovládacího prvku **nástrojů** do formuláře. V pravém horním rohu formuláře, umístěte ho.  
  
9. Změňte hodnotu <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.AutoSize%2A> vlastnost `true`.  
  
10. Nastavte <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Anchor%2A> vlastnost <xref:System.Windows.Forms.AnchorStyles.Right>, <xref:System.Windows.Forms.AnchorStyles.Bottom>.  
  
11. Změnit <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Text%2A> vlastnost "**toto tlačítko má dlouhý řetězec pro vlastnost Text.**"  
  
     Při potvrzení změn, <xref:System.Windows.Forms.Button> ovládací prvek změní velikost sebe sama směrem doleva. Obecně platí, automatické velikosti zvýší velikost ovládacího prvku v opačném směru jeho <xref:System.Windows.Forms.Control.Anchor%2A> nastavení vlastnosti.  
  
## <a name="autosize-and-autosizemode-properties"></a>AutoSize a AutoSizeMode – vlastnosti  
 Některé ovládací prvky podporují `AutoSizeMode` vlastnost, která poskytuje jemněji odstupňovanou kontrolu nad chováním automatické velikosti ovládacího prvku.  
  
#### <a name="to-use-the-autosizemode-property"></a>Chcete-li použít AutoSizeMode – vlastnost  
  
1.  Přetáhněte <xref:System.Windows.Forms.Panel> ovládacího prvku **nástrojů** do formuláře.  
  
2.  Nastavte hodnotu <xref:System.Windows.Forms.Panel> ovládacího prvku <xref:System.Windows.Forms.Control.AutoSize%2A> vlastnost `true`.  
  
3.  Přetáhněte <xref:System.Windows.Forms.Button> ovládacího prvku **nástrojů** do <xref:System.Windows.Forms.Panel> ovládacího prvku.  
  
4.  Místo <xref:System.Windows.Forms.Button> ovládacího prvku v pravém horním rohu <xref:System.Windows.Forms.Panel> ovládacího prvku.  
  
5.  Vyberte <xref:System.Windows.Forms.Panel> řídit a získejte pravý dolní úchyt. Změnit velikost <xref:System.Windows.Forms.Panel> ovládací prvek bude větší a menší.  
  
    > [!NOTE]
    >  Můžete libovolně změnit velikost <xref:System.Windows.Forms.Panel> ovládacího prvku, ale nemůže velikost je menší než pozice <xref:System.Windows.Forms.Button> pravého dolního rohu ovládacího prvku. Toto chování je určená výchozí hodnota `AutoSizeMode` vlastnost, která je <xref:System.Windows.Forms.AutoSizeMode.GrowOnly>.  
  
6.  Nastavte hodnotu <xref:System.Windows.Forms.Panel> ovládacího prvku `AutoSizeMode` vlastnost <xref:System.Windows.Forms.AutoSizeMode.GrowAndShrink>.  
  
     <xref:System.Windows.Forms.Panel> Samotný ohraničit velikosti ovládacího prvku <xref:System.Windows.Forms.Button> ovládacího prvku. Nelze změnit velikost <xref:System.Windows.Forms.Panel> ovládacího prvku.  
  
7.  Přetáhněte <xref:System.Windows.Forms.Button> ovládací prvek směrem k horním levém horním rohu <xref:System.Windows.Forms.Panel> ovládacího prvku.  
  
     <xref:System.Windows.Forms.Panel> Změní velikost ovládacího prvku <xref:System.Windows.Forms.Button> nové pozice ovládacího prvku.  
  
## <a name="next-steps"></a>Další kroky  
 Existuje mnoho dalších funkcí rozložení pro uspořádání ovládacích prvků v aplikacích Windows Forms. Tady jsou některé kombinace, který můžete vyzkoušet:  
  
-   Vytvoření tvaru pomocí <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku. Podrobnosti najdete v tématu [názorný postup: Uspořádání ovládacích prvků na formuláři Windows s použitím ovládacího prvku TableLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md). Zkuste změnit hodnoty <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku <xref:System.Windows.Forms.Control.Padding%2A> vlastnost, stejně jako <xref:System.Windows.Forms.Control.Margin%2A> vlastnost na jeho podřízených ovládacích prvků.  
  
-   Zkuste stejném experimentu pomocí <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku. Podrobnosti najdete v tématu [názorný postup: Uspořádání ovládacích prvků na formuláři Windows s použitím ovládacího prvku FlowLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md).  
  
-   Experiment s ukotvení podřízených ovládacích prvků <xref:System.Windows.Forms.Panel> ovládacího prvku. <xref:System.Windows.Forms.Control.Padding%2A> Vlastnost je obecnější realizaci <xref:System.Windows.Forms.ScrollableControl.DockPadding%2A> vlastnost a dokáže uspokojit požadavky sami, že tomu tak, že vložíte podřízeného ovládacího prvku <xref:System.Windows.Forms.Panel> ovládacího prvku a nastavením podřízený ovládací prvek <xref:System.Windows.Forms.Control.Dock%2A> vlastnost <xref:System.Windows.Forms.DockStyle.Fill>. Nastavte <xref:System.Windows.Forms.Panel> ovládacího prvku <xref:System.Windows.Forms.Control.Padding%2A> na různé hodnoty a Poznámka efekt.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Forms.Control.AutoSize%2A>
- <xref:System.Windows.Forms.ScrollableControl.DockPadding%2A>
- <xref:System.Windows.Forms.Control.Margin%2A>
- <xref:System.Windows.Forms.Control.Padding%2A>
- [Přehled vlastnosti AutoSize](../../../../docs/framework/winforms/controls/autosize-property-overview.md)
- [Návod: Uspořádání ovládacích prvků na formuláři Windows s použitím ovládacího prvku TableLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [Návod: Uspořádání ovládacích prvků na formuláři Windows s použitím ovládacího prvku FlowLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [Návod: Uspořádání ovládacích prvků ve Windows Forms pomocí zarovnávacích čar](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
