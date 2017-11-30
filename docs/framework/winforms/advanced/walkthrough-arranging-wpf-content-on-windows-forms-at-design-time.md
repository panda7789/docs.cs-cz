---
title: "Návod: Uspořádání obsahu WPF ve Windows Forms během návrhu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WPF user control [Windows Forms], hosting in a layout panel
- WPF content [Windows Forms], arranging at design time
- Windows Forms, arranging WPF content at design time
- WPF content [Windows Forms], hosting in Windows Forms
- Windows Forms, anchoring and docking WPF content
- interoperability [WPF]
ms.assetid: 5efb1c53-1484-43d6-aa8a-f4861b99bb8a
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9ae86989489ec4c50a4234eeb4a0950a71e53b0a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-arranging-wpf-content-on-windows-forms-at-design-time"></a>Návod: Uspořádání obsahu WPF ve Windows Forms během návrhu
Tento návod ukazuje, jak používat funkce rozložení Windows Forms, jako je například ukotvení a zarovnávací čáry, k uspořádání ovládacích prvků Windows Presentation Foundation (WPF).  
  
 V tomto návodu můžete provádět následující úlohy:  
  
-   Vytvoření projektu.  
  
-   Vytvoření ovládacího prvku WPF.  
  
-   Hostitelské ovládací prvky WPF panelu rozložení.  
  
-   Zarovnávací čáry použijte k zarovnání ovládacích prvků WPF.  
  
-   Ukotvení a dokování ovládacích prvků WPF.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat následující komponenty:  
  
-   [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)].  
  
## <a name="creating-the-project"></a>Vytvoření projektu  
 Prvním krokem je vytvoření projektu modelu Windows Forms.  
  
> [!NOTE]
>  Pokud hostování obsahu subsystému WPF, jsou podporovány pouze projekty C# a Visual Basic.  
  
#### <a name="to-create-the-project"></a>Vytvoření projektu  
  
-   Vytvořte nový projekt aplikace Windows Forms v jazyce Visual Basic a Visual C# s názvem `ArrangeElementHost`.  
  
## <a name="creating-the-wpf-control"></a>Vytvoření ovládacího prvku WPF  
 Po přidání ovládací prvek WPF do projektu, můžete ho uspořádat na formuláři.  
  
#### <a name="to-create-wpf-controls"></a>Chcete-li vytvořit ovládacích prvků WPF  
  
1.  Přidat nové WPF <xref:System.Windows.Controls.UserControl> do projektu. Použití výchozího názvu pro typ ovládacího prvku `UserControl1.xaml`. Další informace najdete v tématu [návod: vytvoření nové WPF obsahu v aplikaci Windows Forms v době návrhu](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).  
  
2.  V návrhovém zobrazení, ujistěte se, že `UserControl1` je vybrána. Další informace najdete v tématu [postup: vyberte a přesunout elementů na návrhovou plochu](http://msdn.microsoft.com/en-us/54cb70b6-b35b-46e4-a0cc-65189399c474).  
  
3.  V **vlastnosti** okno, nastavte hodnotu <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A> vlastnosti, které chcete `200`.  
  
4.  Nastavte hodnotu <xref:System.Windows.Controls.Control.Background%2A> vlastnost `Blue`.  
  
5.  Sestavte projekt.  
  
## <a name="hosting-wpf-controls-in-a-layout-panel"></a>Hostování ovládacích prvků WPF panelu rozložení  
 Můžete v panelů rozložení ovládacích prvků WPF stejným způsobem, jakým používáte další ovládací prvky Windows Forms.  
  
#### <a name="to-host-wpf-controls-in-a-layout-panel"></a>Na hostiteli ovládacích prvků WPF panelu rozložení  
  
1.  Otevřete `Form1` v Návrháři formulářů.  
  
2.  V **sada nástrojů**, přetáhněte ji <xref:System.Windows.Forms.TableLayoutPanel> ovládací prvek na formuláři.  
  
3.  Na <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku inteligentní panel, vyberte **odebere poslední řádek**.  
  
4.  Změnit velikost <xref:System.Windows.Forms.TableLayoutPanel> řízení větší šířku a výšku.  
  
5.  V **sada nástrojů**, dvakrát klikněte na `UserControl1` k vytvoření instance `UserControl1` v první buňky <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku.  
  
     Instance `UserControl1` je hostován v nové <xref:System.Windows.Forms.Integration.ElementHost> ovládací prvek s názvem `elementHost1`.  
  
6.  V **sada nástrojů**, dvakrát klikněte na `UserControl1` vytvořit jiná instance do druhé buňky <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku.  
  
7.  V **Osnova dokumentu** vyberte `tableLayoutPanel1`. Další informace najdete v tématu [Osnova dokumentu – okno](http://msdn.microsoft.com/en-us/9054f2bc-f6f8-4242-9fe0-be71089b12f8).  
  
8.  V **vlastnosti** okno, nastavte hodnotu <xref:System.Windows.Forms.Control.Padding%2A> vlastnost `10, 10, 10, 10`.  
  
     Obě <xref:System.Windows.Forms.Integration.ElementHost> ovládací prvky jsou po změně velikosti a nevejde se do nové rozložení.  
  
## <a name="using-snaplines-to-align-wpf-controls"></a>Chcete-li zarovnat ovládacích prvků WPF pomocí zarovnávacích čar  
 Zarovnávací čáry povolit snadno zarovnání ovládacích prvků na formuláři. Chcete-li zarovnat vaší ovládacích prvků WPF také můžete zarovnávací čáry. Další informace najdete v tématu [návod: uspořádání ovládacích prvků ve Windows Forms pomocí zarovnávacích čar](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).  
  
#### <a name="to-use-snaplines-to-align-wpf-controls"></a>Zarovnat WPF pomocí zarovnávacích čar ovládací prvky  
  
1.  Z **sada nástrojů**, přetáhněte instanci `UserControl1` do formuláře a umístěte jej do prostoru pod <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku.  
  
     Instance `UserControl1` je hostován v nové <xref:System.Windows.Forms.Integration.ElementHost> ovládací prvek s názvem `elementHost3`.  
  
2.  Pomocí zarovnávacích čar, Zarovnat je levý okraj `elementHost3` s levým okrajem <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku.  
  
3.  Pomocí zarovnávacích čar, velikost `elementHost3` stejné šířky, jako <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku.  
  
4.  Přesunout `elementHost3` směrem k <xref:System.Windows.Forms.TableLayoutPanel> řízení, dokud se nezobrazí center snapline mezi ovládacími prvky.  
  
5.  V **vlastnosti** okno, nastavte hodnotu vlastnosti okraj `20, 20, 20, 20`.  
  
6.  Přesunout `elementHost3` směrem od <xref:System.Windows.Forms.TableLayoutPanel> řízení dokud center snapline se znovu nezobrazí. Center snapline nyní označuje okraj 20.  
  
7.  Přesunout `elementHost3` vpravo, dokud jeho levé hrany zarovnaná s levým okrajem `elementHost1`.  
  
8.  Umožňuje změnit šířku `elementHost3` dokud jeho pravé hrany zarovnán podle pravé hrany `elementHost2`.  
  
## <a name="anchoring-and-docking-wpf-controls"></a>Ukotvení a dokování ovládacích prvků WPF  
 Ovládací prvek WPF hostované ve formuláři má stejné ukotvení a dokování chování jako další ovládací prvky Windows Forms.  
  
#### <a name="to-anchor-and-dock-wpf-controls"></a>Chcete-li ukotvení a dokování ovládacích prvků WPF  
  
1.  Vyberte `elementHost1`.  
  
2.  V **vlastnosti** nastavte <xref:System.Windows.Forms.Control.Anchor%2A> vlastnost **nahoru, dolů, doleva a doprava**.  
  
3.  Změnit velikost <xref:System.Windows.Forms.TableLayoutPanel> řízení větší velikost.  
  
     `elementHost1` Změní velikost vyplníte buňku řízení.  
  
4.  Vyberte `elementHost2`.  
  
5.  V **vlastnosti** okno, nastavte hodnotu <xref:System.Windows.Forms.Control.Dock%2A> vlastnost <xref:System.Windows.Forms.DockStyle.Fill>.  
  
     `elementHost2` Změní velikost vyplníte buňku řízení.  
  
6.  Vyberte <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku.  
  
7.  Nastavte hodnotu jeho <xref:System.Windows.Forms.Control.Dock%2A> vlastnost <xref:System.Windows.Forms.DockStyle.Top>.  
  
8.  Vyberte `elementHost3`.  
  
9. Nastavte hodnotu jeho <xref:System.Windows.Forms.Control.Dock%2A> vlastnost <xref:System.Windows.Forms.DockStyle.Fill>.  
  
     `elementHost3` Řízení změní velikost k vyplnění zbývající místo na formuláři.  
  
10. Změnit velikost formuláře.  
  
     Všechny tři <xref:System.Windows.Forms.Integration.ElementHost> správně Změna velikosti ovládacích prvků.  
  
     Další informace najdete v tématu [postupy: ukotvení a ukotvení podřízených ovládacích prvků v ovládacím prvku TableLayoutPanel](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Postupy: ukotvení a dokování podřízených ovládacích prvků v ovládacím prvku TableLayoutPanel](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)  
 [Postupy: zarovnání ovládacího prvku k okrajům formuláře během návrhu](../../../../docs/framework/winforms/controls/how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)  
 [Návod: Uspořádání ovládacích prvků ve Windows Forms pomocí zarovnávacích čar](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)  
 [Migrace a vzájemná funkční spolupráce](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 [Pomocí ovládacích prvků WPF](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)  
 [Návrhář WPF](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)
