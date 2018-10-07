---
title: 'Návod: Uspořádání obsahu WPF ve Windows Forms během návrhu'
ms.date: 03/30/2017
helpviewer_keywords:
- WPF user control [Windows Forms], hosting in a layout panel
- WPF content [Windows Forms], arranging at design time
- Windows Forms, arranging WPF content at design time
- WPF content [Windows Forms], hosting in Windows Forms
- Windows Forms, anchoring and docking WPF content
- interoperability [WPF]
ms.assetid: 5efb1c53-1484-43d6-aa8a-f4861b99bb8a
ms.openlocfilehash: 062b9b943d187ccd4105f3772688c563f540d696
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2018
ms.locfileid: "48846471"
---
# <a name="walkthrough-arranging-wpf-content-on-windows-forms-at-design-time"></a>Návod: Uspořádání obsahu WPF ve Windows Forms během návrhu
Tento návod ukazuje způsob použití funkcí rozložení Windows Forms, jako je například ukotvení a zarovnávacích čar, k uspořádání ovládacích prvků Windows Presentation Foundation (WPF).

 V tomto podrobném návodu můžete provádět následující úlohy:

-   Vytvoření projektu.

-   Vytvoření ovládacího prvku WPF.

-   Hostitelské ovládací prvky WPF v panelu rozložení.

-   Pomocí zarovnávacích čar Zarovnat ovládací prvky WPF.

-   Ukotvení a ovládacích prvků WPF.

> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat následující komponenty:  
  
-   Visual Studio 2012.  
  
## <a name="creating-the-project"></a>Vytvoření projektu  
 Prvním krokem je vytvoření projektu Windows Forms.  
  
> [!NOTE]
>  Při hostování obsahu WPF, jsou podporovány pouze projekty C# a Visual Basic.  
  
#### <a name="to-create-the-project"></a>Vytvoření projektu  
  
-   Vytvořte nový projekt Formulářové aplikace Windows v jazyce Visual Basic nebo Visual C# s názvem `ArrangeElementHost`.  
  
## <a name="creating-the-wpf-control"></a>Vytvoření ovládacího prvku WPF  
 Po přidání ovládacího prvku WPF do projektu, můžete je nastavit na formuláři.  
  
#### <a name="to-create-wpf-controls"></a>Chcete-li vytvořit ovládací prvky WPF  
  
1.  Přidat nový WPF <xref:System.Windows.Controls.UserControl> do projektu. Použití výchozího názvu pro typ ovládacího prvku `UserControl1.xaml`. Další informace najdete v tématu [návod: vytváření nových WPF obsahu ve Windows Forms v době návrhu](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).  
  
2.  V návrhovém zobrazení, ujistěte se, že `UserControl1` zaškrtnuto. Další informace najdete v tématu [postupy: výběr a přesunutí prvků na návrhové ploše](https://msdn.microsoft.com/library/54cb70b6-b35b-46e4-a0cc-65189399c474).  
  
3.  V **vlastnosti** okno, nastavte hodnotu <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A> vlastností `200`.  
  
4.  Nastavte hodnotu <xref:System.Windows.Controls.Control.Background%2A> vlastnost `Blue`.  
  
5.  Sestavte projekt.  
  
## <a name="hosting-wpf-controls-in-a-layout-panel"></a>Hostování ovládacích prvků WPF na panelu rozložení  
 Ovládací prvky WPF v panely rozložení můžete použít stejným způsobem, jakým používáte další ovládací prvky Windows Forms.  
  
#### <a name="to-host-wpf-controls-in-a-layout-panel"></a>Na hostitelských ovládacích prvků WPF na panelu rozložení  
  
1.  Otevřít `Form1` v Návrháři formulářů Windows.  
  
2.  V **nástrojů**, přetáhněte <xref:System.Windows.Forms.TableLayoutPanel> ovládací prvek na formuláři.  
  
3.  Na <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku panelu inteligentních značek, vyberte **odebrat poslední řádek**.  
  
4.  Změnit velikost <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku na větší šířku a výšku.  
  
5.  V **nástrojů**, dvakrát klikněte na panel `UserControl1` k vytvoření instance `UserControl1` do první buňky <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku.  
  
     Instance `UserControl1` hostována v novém <xref:System.Windows.Forms.Integration.ElementHost> ovládací prvek s názvem `elementHost1`.  
  
6.  V **nástrojů**, dvakrát klikněte na panel `UserControl1` pro vytvoření další instance v druhé buňce <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku.  
  
7.  V **Osnova dokumentu** okně `tableLayoutPanel1`. Další informace najdete v tématu [Osnova dokumentu – okno](https://msdn.microsoft.com/library/9054f2bc-f6f8-4242-9fe0-be71089b12f8).  
  
8.  V **vlastnosti** okno, nastavte hodnotu <xref:System.Windows.Forms.Control.Padding%2A> vlastnost `10, 10, 10, 10`.  
  
     Obě <xref:System.Windows.Forms.Integration.ElementHost> ovládací prvky se přizpůsobí do nového rozložení.  
  
## <a name="using-snaplines-to-align-wpf-controls"></a>Zarovnání ovládacích prvků WPF pomocí zarovnávacích čar  
 Zarovnávacích čar bylo možné snadno zarovnání ovládacích prvků ve formuláři. Zarovnání ovládacích prvků WPF také můžete použít zarovnávacích čar. Další informace najdete v tématu [návod: uspořádání ovládacích prvků ve Windows Forms pomocí zarovnávacích čar](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).  
  
#### <a name="to-use-snaplines-to-align-wpf-controls"></a>Určuje zarovnání WPF pomocí zarovnávacích čar  
  
1.  Z **nástrojů**, přetáhněte instance `UserControl1` do formuláře a umístěte ji v prostoru pod <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku.  
  
     Instance `UserControl1` hostována v novém <xref:System.Windows.Forms.Integration.ElementHost> ovládací prvek s názvem `elementHost3`.  
  
2.  Pomocí zarovnávacích čar, zarovnání na levý okraj `elementHost3` s levým okrajem <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku.  
  
3.  Pomocí zarovnávacích čar, velikost `elementHost3` podle stejné šířky, jako <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku.  
  
4.  Přesunout `elementHost3` směrem k <xref:System.Windows.Forms.TableLayoutPanel> ovládací prvek, dokud se nezobrazí snapline – System center mezi ovládacími prvky.  
  
5.  V **vlastnosti** okno, nastavte hodnotu vlastnosti okraj k `20, 20, 20, 20`.  
  
6.  Přesunout `elementHost3` klávesou <xref:System.Windows.Forms.TableLayoutPanel> ovládací snapline – System center, zobrazí se znovu. Snapline – System center teď uvádí rozpětí od 20.  
  
7.  Přesunout `elementHost3` doprava, dokud jeho levé hrany v souladu s levým okrajem `elementHost1`.  
  
8.  Umožňuje změnit šířku `elementHost3` až do jeho pravé hrany v souladu s pravým okrajem `elementHost2`.  
  
## <a name="anchoring-and-docking-wpf-controls"></a>Ukotvení a dokování ovládacích prvků WPF  
 Ovládací prvek WPF hostované ve formuláři obsahuje stejné ukotvení a dokování chování jako ostatní ovládací prvky Windows Forms.  
  
#### <a name="to-anchor-and-dock-wpf-controls"></a>Ukotvení a ovládacích prvků WPF  
  
1.  Vyberte `elementHost1`.  
  
2.  V **vlastnosti** okno, nastaveno <xref:System.Windows.Forms.Control.Anchor%2A> vlastnost **nahoře, dole, vlevo, vpravo**.  
  
3.  Změnit velikost <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku na větší velikost.  
  
     `elementHost1` Řídit změní tak, aby vyplnil buňku.  
  
4.  Vyberte `elementHost2`.  
  
5.  V **vlastnosti** okno, nastavte hodnotu <xref:System.Windows.Forms.Control.Dock%2A> vlastnost <xref:System.Windows.Forms.DockStyle.Fill>.  
  
     `elementHost2` Řídit změní tak, aby vyplnil buňku.  
  
6.  Vyberte <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku.  
  
7.  Nastavte hodnotu jeho <xref:System.Windows.Forms.Control.Dock%2A> vlastnost <xref:System.Windows.Forms.DockStyle.Top>.  
  
8.  Vyberte `elementHost3`.  
  
9. Nastavte hodnotu jeho <xref:System.Windows.Forms.Control.Dock%2A> vlastnost <xref:System.Windows.Forms.DockStyle.Fill>.  
  
     `elementHost3` Řídit změní tak, aby vyplnil zbývající místo na formuláři.  
  
10. Změnit velikost formuláře.  
  
     Všechny tři <xref:System.Windows.Forms.Integration.ElementHost> odpovídajícím způsobem změňte velikost ovládacích prvků.  
  
     Další informace najdete v tématu [postupy: ukotvení a ukotvení podřízených ovládacích prvků v ovládacím prvku TableLayoutPanel](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Postupy: Ukotvení podřízených ovládacích prvků v ovládacím prvku TableLayoutPanel](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)  
 [Postupy: Zarovnání ovládacího prvku k okrajům formulářů během návrhu](../../../../docs/framework/winforms/controls/how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)  
 [Návod: Uspořádání ovládacích prvků ve Windows Forms pomocí zarovnávacích čar](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)  
 [Migrace a interoperabilita](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 [Používání ovládacích prvků WPF](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)  
 [Návrh kódu XAML v sadě Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)
