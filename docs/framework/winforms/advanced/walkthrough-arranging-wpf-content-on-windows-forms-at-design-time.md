---
title: 'Návod: Uspořádání obsahu WPF v modelu Windows Forms během návrhu'
ms.date: 03/30/2017
helpviewer_keywords:
- WPF user control [Windows Forms], hosting in a layout panel
- WPF content [Windows Forms], arranging at design time
- Windows Forms, arranging WPF content at design time
- WPF content [Windows Forms], hosting in Windows Forms
- Windows Forms, anchoring and docking WPF content
- interoperability [WPF]
ms.assetid: 5efb1c53-1484-43d6-aa8a-f4861b99bb8a
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7858ffd708c78d6397d533f613ccc2ea78d6cbed
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69658525"
---
# <a name="walkthrough-arrange-wpf-content-on-windows-forms-at-design-time"></a>Návod: Uspořádání obsahu WPF v model Windows Forms v době návrhu

V tomto článku se dozvíte, jak používat funkce model Windows Forms rozložení, jako je například ukotvení a zarovnávacím čárám, k uspořádání ovládacích prvků Windows Presentation Foundation (WPF).

## <a name="prerequisites"></a>Požadavky

K dokončení tohoto Názorného postupu potřebujete Visual Studio.

## <a name="create-the-project"></a>Vytvoření projektu

Otevřete Visual Studio a vytvořte nový projekt aplikace model Windows Forms v Visual Basic nebo vizuálu C# s názvem `ArrangeElementHost`.

> [!NOTE]
> Při hostování obsahu WPF jsou podporovány C# pouze projekty a Visual Basic.

## <a name="create-the-wpf-control"></a>Vytvoření ovládacího prvku WPF

Po přidání ovládacího prvku WPF do projektu jej můžete uspořádat na formuláři.

1. Přidejte do projektu nový <xref:System.Windows.Controls.UserControl> WPF. Použijte výchozí název pro typ ovládacího prvku, `UserControl1.xaml`. Další informace najdete v tématu [Návod: Vytváření nového obsahu WPF v model Windows Forms v době](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)návrhu.

2. V zobrazení Návrh se ujistěte, že `UserControl1` je vybraná možnost.

3. V okně **vlastnosti** nastavte hodnotu <xref:System.Windows.FrameworkElement.Width%2A> vlastností a <xref:System.Windows.FrameworkElement.Height%2A> na **200**.

4. Nastavte hodnotu <xref:System.Windows.Controls.Control.Background%2A> vlastnosti na modrou.

5. Sestavte projekt.

## <a name="host-wpf-controls-in-a-layout-panel"></a>Hostování ovládacích prvků WPF na panelu rozložení

Ovládací prvky WPF lze v panelech rozložení použít stejným způsobem jako jiné ovládací prvky model Windows Forms.

1. Otevřete `Form1` v Návrhář formulářů.

2. V **sadě nástrojů**přetáhněte <xref:System.Windows.Forms.TableLayoutPanel> ovládací prvek do formuláře.

3. Na panelu inteligentních značek ovládacíhoprvkuvyberteOdebratposlední<xref:System.Windows.Forms.TableLayoutPanel> řádek.

4. Změňte velikost <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku na větší šířku a výšku.

5. V **sadě nástrojů**poklikejte na `UserControl1` `UserControl1` vytvoření instance v první buňce <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku.

   Instance `UserControl1` je hostována v novém <xref:System.Windows.Forms.Integration.ElementHost> ovládacím prvku s názvem `elementHost1`.

6. Na **panelu nástrojů**dvakrát klikněte `UserControl1` pro vytvoření další instance v <xref:System.Windows.Forms.TableLayoutPanel> druhé buňce ovládacího prvku.

7. V okně **Osnova dokumentu** vyberte `tableLayoutPanel1`.

8. V okně **vlastnosti** nastavte hodnotu <xref:System.Windows.Forms.Control.Padding%2A> vlastnosti na **10, 10, 10, 10**.

   Oba <xref:System.Windows.Forms.Integration.ElementHost> ovládací prvky se změní tak, aby se vešly do nového rozložení.

## <a name="use-snaplines-to-align-wpf-controls"></a>Použití zarovnávacím čárám k zarovnání ovládacích prvků WPF

Zarovnávacím čárám umožňuje snadné zarovnání ovládacích prvků na formuláři. Zarovnávacím čárám můžete použít i k zarovnání ovládacích prvků WPF. Další informace najdete v tématu [Návod: Uspořádání ovládacích prvků na model Windows Forms pomocí](../controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)zarovnávacím čárám.

1. Z **panelu nástrojů**přetáhněte instanci `UserControl1` do formuláře a umístěte ji do prostoru pod <xref:System.Windows.Forms.TableLayoutPanel> ovládacím prvkem.

   Instance `UserControl1` je hostována v novém <xref:System.Windows.Forms.Integration.ElementHost> ovládacím prvku s názvem `elementHost3`.

2. Pomocí zarovnávacím čárám zarovnejte levý okraj `elementHost3` s levým <xref:System.Windows.Forms.TableLayoutPanel> okrajem ovládacího prvku.

3. Pomocí zarovnávacím čárám můžete nastavit `elementHost3` stejnou šířku <xref:System.Windows.Forms.TableLayoutPanel> jako ovládací prvek.

4. Přejděte `elementHost3` k ovládacímu prvku, <xref:System.Windows.Forms.TableLayoutPanel> dokud se mezi ovládacími prvky snapline střed.

5. V okně **vlastnosti** nastavte hodnotu vlastnosti okraj na **20, 20, 20, 20**.

6. Přesuňte se<xref:System.Windows.Forms.TableLayoutPanel> od ovládacího prvku jinam,dokudse`elementHost3` znovu snapline Center. Centrum snapline nyní indikuje okraj 20.

7. Přejděte `elementHost3` do pravého okraje, dokud jeho levý okraj není zarovnán s levým `elementHost1`okrajem.

8. Změní šířku `elementHost3` , dokud její pravý okraj není zarovnán s pravým `elementHost2`okrajem.

## <a name="anchor-and-dock-wpf-controls"></a>Ukotvení a ukotvení ovládacích prvků WPF

Ovládací prvek WPF hostovaný na formuláři má stejné chování při ukotvení a ukotvení jako jiné ovládací prvky model Windows Forms.

1. Vyberte `elementHost1`.

2. V okně **vlastnosti** nastavte <xref:System.Windows.Forms.Control.Anchor%2A> vlastnost na **horní, dolní, levou, pravou**.

3. Změňte velikost <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku na větší velikost.

   `elementHost1` Ovládací prvek mění velikost, aby bylo možné vyplnit buňku.

4. Vyberte `elementHost2`.

5. V okně **vlastnosti** nastavte hodnotu <xref:System.Windows.Forms.Control.Dock%2A> vlastnosti na <xref:System.Windows.Forms.DockStyle.Fill>.

   `elementHost2` Ovládací prvek mění velikost, aby bylo možné vyplnit buňku.

6. <xref:System.Windows.Forms.TableLayoutPanel> Vyberte ovládací prvek.

7. Nastavte hodnotu <xref:System.Windows.Forms.Control.Dock%2A> vlastnosti na <xref:System.Windows.Forms.DockStyle.Top>.

8. Vyberte `elementHost3`.

9. Nastavte hodnotu <xref:System.Windows.Forms.Control.Dock%2A> vlastnosti na <xref:System.Windows.Forms.DockStyle.Fill>.

   `elementHost3` Ovládací prvek mění velikost, aby vyplnil zbývající místo ve formuláři.

10. Změňte velikost formuláře.

    Všechny tři <xref:System.Windows.Forms.Integration.ElementHost> ovládací prvky mají patřičnou velikost.

    Další informace najdete v tématu [jak: Podřízené ovládací prvky ukotvení a ukotvení v](../controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)ovládacím prvku TableLayoutPanel.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Postupy: Podřízené ovládací prvky ukotvení a ukotvení v ovládacím prvku TableLayoutPanel](../controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [Postupy: Zarovnání ovládacího prvku na okraje formulářů v době návrhu](../controls/how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)
- [Návod: Uspořádání ovládacích prvků na model Windows Forms pomocí zarovnávacím čárám](../controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [Migrace a interoperabilita](../../wpf/advanced/migration-and-interoperability.md)
- [Používání ovládacích prvků WPF](using-wpf-controls.md)
- [Návrh kódu XAML v sadě Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)
