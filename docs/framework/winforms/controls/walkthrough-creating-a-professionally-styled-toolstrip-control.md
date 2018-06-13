---
title: 'Návod: Vytvoření ovládacího prvku ToolStrip s profesionálním vzhledem'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStripProfessionalRenderer class [Windows Forms]
- ToolStripRenderer class [Windows Forms]
- toolbars [Windows Forms], walkthroughs
- ToolStrip control [Windows Forms], creating professionally styled controls
ms.assetid: b52339ae-f1d3-494e-996e-eb455614098a
ms.openlocfilehash: 2d2443f1f7153ed35aecbbb9d69c9e1421269e24
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33541603"
---
# <a name="walkthrough-creating-a-professionally-styled-toolstrip-control"></a>Návod: Vytvoření ovládacího prvku ToolStrip s profesionálním vzhledem
Aplikace můžete udělit <xref:System.Windows.Forms.ToolStrip> řídí profesionální vzhled a chování vytvořením vlastní třídy odvozené od <xref:System.Windows.Forms.ToolStripProfessionalRenderer> typu.  
  
 Tento návod ukazuje, jak používat <xref:System.Windows.Forms.ToolStrip> ovládací prvky pro vytvoření složeného ovládacího prvku, který vypadá takto: **navigačním podokně** poskytované Microsoft® Outlook®. Následující úlohy jsou popsané v tomto návodu:  
  
-   Vytvoření projektu knihovny ovládacích prvků Windows.  
  
-   Návrh StackView ovládacího prvku.  
  
-   Implementace vlastní zobrazovací jednotky.  
  
 Jakmile budete hotovi, budete mít opakovaně použitelné vlastní ovládací prvek s profesionální vzhled ovládacího prvku Microsoft Office® XP.  
  
 Zkopírujte kód v tomto tématu v jednom seznamu, najdete v části [postupy: vytvoření profesionálním ve ovládacího prvku ToolStrip](../../../../docs/framework/winforms/controls/how-to-create-a-professionally-styled-toolstrip-control.md).  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu, budete potřebovat:  
  
-   Dostatečná oprávnění, abyste mohli vytvořit a spustit projekty aplikací Windows Forms v počítači, kde je nainstalován Visual Studio.  
  
## <a name="creating-a-windows-control-library-project"></a>Vytvoření projektu knihovny ovládacího prvku systému Windows  
 Prvním krokem je vytvoření projektu knihovny ovládacího prvku.  
  
#### <a name="to-create-the-control-library-project"></a>Vytvoření projektu knihovny ovládacího prvku  
  
1.  Vytvoření nového projektu knihovny ovládacích prvků Windows s názvem `StackViewLibrary`.  
  
2.  V **Průzkumníku**, odstraňte výchozí řízení projektu odstraněním zdrojového souboru s názvem "UserControl1.cs" nebo "UserControl1.vb", v závislosti na vámi zvolený jazyk.  
  
     Další informace najdete v tématu [NIB: postupy: odebrání, odstranění a vyloučit položky](http://msdn.microsoft.com/library/6dffdc86-29c8-4eff-bcd8-e3a0dd9e9a73).  
  
3.  Přidejte nový <xref:System.Windows.Forms.UserControl> položkou **StackViewLibrary** projektu. Zadejte základní název nové zdrojový soubor `StackView`.  
  
## <a name="designing-the-stackview-control"></a>Navrhování StackView ovládací prvek  
 `StackView` Ovládací prvek je složeného ovládacího prvku pomocí jednu podřízenou <xref:System.Windows.Forms.ToolStrip> ovládacího prvku. Další informace o složené ovládací prvky najdete v tématu [typy vlastní prvky](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md).  
  
#### <a name="to-design-the-stackview-control"></a>Při návrhu StackView ovládací prvek  
  
1.  Z **sada nástrojů**, přetáhněte ji <xref:System.Windows.Forms.ToolStrip> ovládacího prvku na plochu návrháře.  
  
2.  V **vlastnosti** nastavte <xref:System.Windows.Forms.ToolStrip> vlastností ovládacího prvku podle následující tabulky.  
  
    |Vlastnost|Hodnota|  
    |--------------|-----------|  
    |Název|`stackStrip`|  
    |CanOverflow –|`false`|  
    |Ukotvení|<xref:System.Windows.Forms.DockStyle.Bottom>|  
    |Písma|`Tahoma, 10pt, style=Bold`|  
    |GripStyle.|<xref:System.Windows.Forms.ToolStripGripStyle.Hidden>|  
    |LayoutStyle|<xref:System.Windows.Forms.ToolStripLayoutStyle.VerticalStackWithOverflow>|  
    |Odsazení|`0, 7, 0, 0`|  
    |RenderMode –|<xref:System.Windows.Forms.ToolStripRenderMode.Professional>|  
  
3.  V Návrháři formulářů Windows, klikněte na <xref:System.Windows.Forms.ToolStrip> ovládacího prvku **přidat** tlačítko a přidejte <xref:System.Windows.Forms.ToolStripButton> k `stackStrip` ovládacího prvku.  
  
4.  V **vlastnosti** nastavte <xref:System.Windows.Forms.ToolStripButton> vlastností ovládacího prvku podle následující tabulky.  
  
    |Vlastnost|Hodnota|  
    |--------------|-----------|  
    |Název|`mailStackButton`|  
    |CheckOnClick|true|  
    |CheckState|<xref:System.Windows.Forms.CheckState.Checked>|  
    |DisplayStyle|<xref:System.Windows.Forms.ToolStripItemDisplayStyle.ImageAndText>|  
    |ImageAlign|<xref:System.Drawing.ContentAlignment.MiddleLeft>|  
    |ImageScaling|<xref:System.Windows.Forms.ToolStripItemImageScaling.None>|  
    |ImageTransparentColor|`238, 238, 238`|  
    |Okraj|`0, 0, 0, 0`|  
    |Odsazení|`3, 3, 3, 3`|  
    |Text|**E-mailu**|  
    |Zarovnání textu|<xref:System.Drawing.ContentAlignment.MiddleLeft>|  
  
5.  Opakujte krok 7 pro tři další <xref:System.Windows.Forms.ToolStripButton> ovládací prvky.  
  
     Ovládací prvky pojmenovat `calendarStackButton`, `contactsStackButton`, a `tasksStackButton`. Nastavte hodnotu <xref:System.Windows.Forms.Control.Text%2A> vlastnost **kalendáře**, **kontakty**, a **úlohy**, v uvedeném pořadí.  
  
## <a name="handling-events"></a>Zpracování událostí  
 Dvě události jsou důležité, aby `StackView` řízení chovat správně. Zpracování <xref:System.Windows.Forms.UserControl.Load> událost, která má správně umístění ovládacího prvku. Zpracování <xref:System.Windows.Forms.ToolStripItem.Click> událost pro každou <xref:System.Windows.Forms.ToolStripButton> umožnit `StackView` řídit chování stavu podobně jako <xref:System.Windows.Forms.RadioButton> ovládacího prvku.  
  
#### <a name="to-handle-events"></a>Zpracování událostí  
  
1.  V Návrháři formulářů Windows, vyberte `StackView` ovládacího prvku.  
  
2.  V **vlastnosti** okně klikněte na tlačítko **události**.  
  
3.  Dvakrát klikněte na událost zatížení ke generování `StackView_Load` obslužné rutiny události.  
  
4.  V `StackView_Load` obslužné rutiny události, zkopírujte a vložte následující kód.  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#3)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#3)]  
  
5.  V Návrháři formulářů Windows, vyberte `mailStackButton` ovládacího prvku.  
  
6.  V **vlastnosti** okně klikněte na tlačítko **události**.  
  
7.  Dvakrát klikněte na událost Click.  
  
     Návrhář formulářů Windows generuje `mailStackButton_Click` obslužné rutiny události.  
  
8.  Přejmenujte `mailStackButton_Click` obslužné rutiny události pro `stackButton_Click`.  
  
     Další informace najdete v tématu [postupy: přejmenování identifikátor (Visual Basic)](http://msdn.microsoft.com/library/e5a5edf8-3dba-4119-81f4-fc2aba180e0c).  
  
9. Vložte následující kód do `stackButton_Click` obslužné rutiny události.  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#4)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#4)]  
  
10. V Návrháři formulářů Windows, vyberte `calendarStackButton` ovládacího prvku.  
  
11. V **vlastnosti** okně nastavení klikněte na tlačítko událostí `stackButton_Click` obslužné rutiny události.  
  
12. Opakujte kroky 10 a 11 pro `contactsStackButton` a `tasksStackButton` ovládací prvky.  
  
## <a name="defining-icons"></a>Definování ikony  
 Každý `StackView` tlačítko obsahuje přidružené ikonu. Pro usnadnění práce, každá ikona je reprezentována jako řetězec s kódováním base64, pomocí kterého se deserializovat před <xref:System.Drawing.Bitmap> se vytvoří z něj. V produkčním prostředí ukládat data bitmapy jako prostředek a ikon v Návrháři formulářů. Další informace najdete v tématu [postupy: Přidání obrázky na pozadí do Windows Forms](http://msdn.microsoft.com/library/7a509ba2-055c-4ae6-b88a-54625c6d9aff).  
  
#### <a name="to-define-icons"></a>K definování ikony  
  
1.  V editoru kódu vložte následující kód do `StackView` definici třídy. Inicializuje bitmap pro tento kód <xref:System.Windows.Forms.ToolStripButton> ikony.  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#2)]  
  
2.  Přidejte volání `InitializeImages` metoda v `StackView` konstruktoru třídy.  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#5)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#5)]  
  
## <a name="implementing-a-custom-renderer"></a>Implementace vlastní zobrazovací jednotky  
 Můžete přizpůsobit většinu prvků `StackView` řízení Moje implementace třídu odvozenou z <xref:System.Windows.Forms.ToolStripRenderer> – třída. V tomto postupu budete implementovat <xref:System.Windows.Forms.ToolStripProfessionalRenderer> třídu, která se přizpůsobí úchytu a nevykresluje barevného přechodu pozadí pro <xref:System.Windows.Forms.ToolStripButton> ovládací prvky.  
  
#### <a name="to-implement-a-custom-renderer"></a>Chcete-li implementovat vlastní zobrazovací jednotky  
  
1.  Vložte následující kód do `StackView` definici ovládacího prvku.  
  
     Toto je definice `StackRenderer` třídy, která přepisuje <xref:System.Windows.Forms.ToolStripRenderer.RenderGrip>, <xref:System.Windows.Forms.ToolStripRenderer.RenderToolStripBorder>, a <xref:System.Windows.Forms.ToolStripRenderer.RenderButtonBackground> metody pro vytvoření vlastní vzhled.  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#10)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#10)]  
  
2.  V `StackView` konstruktoru ovládacího prvku, vytvořte novou instanci třídy `StackRenderer` třídy a přiřazení této instance `stackStrip` ovládacího prvku <xref:System.Windows.Forms.ToolStrip.Renderer%2A> vlastnost.  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#5)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#5)]  
  
## <a name="testing-the-stackview-control"></a>Testování StackView ovládací prvek  
 `StackView` Ovládací prvek odvozen z <xref:System.Windows.Forms.UserControl> třídy. Proto můžete otestovat pomocí ovládacího prvku **UserControl Test kontejneru**. Další informace najdete v tématu [postupy: testování běhového chování UserControl](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).  
  
#### <a name="to-test-the-stackview-control"></a>Testování StackView ovládacího prvku  
  
1.  Stiskněte klávesu F5, aby se projekt sestavil a spustit **UserControl – kontejner testů**.  
  
2.  Přesuňte ukazatel myši tlačítek `StackView` řízení a potom klikněte na tlačítko zobrazit vzhled vybraném stavu.  
  
## <a name="next-steps"></a>Další kroky  
 V tomto návodu jste vytvořili vlastní opakovaně použitelné ovládací prvek s profesionální vzhled ovládacího prvku Office XP. Můžete použít <xref:System.Windows.Forms.ToolStrip> rodiny ovládacích prvků pro mnoho jiné účely:  
  
-   Vytvořit místní nabídky pro vaše ovládací prvky s <xref:System.Windows.Forms.ContextMenuStrip>. Další informace najdete v tématu [ContextMenu – přehled komponenty](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md).  
  
-   Vytvořte formulář s automaticky zadané standardní nabídku. Další informace najdete v tématu [návod: poskytnutí standardních položek nabídky do formuláře](../../../../docs/framework/winforms/controls/walkthrough-providing-standard-menu-items-to-a-form.md).  
  
-   Vytvoření více formuláře rozhraní (MDI) dokumentu s ukotvení <xref:System.Windows.Forms.ToolStrip> ovládací prvky. Další informace najdete v tématu [postupy: vytvoření formuláře MDI s Menu Merging a ToolStrip – ovládací prvky](../../../../docs/framework/winforms/controls/how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.StatusStrip>  
 [Ovládací prvek ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)  
 [Postupy: Zajištění standardních položek nabídky pro formulář](../../../../docs/framework/winforms/controls/how-to-provide-standard-menu-items-to-a-form.md)
