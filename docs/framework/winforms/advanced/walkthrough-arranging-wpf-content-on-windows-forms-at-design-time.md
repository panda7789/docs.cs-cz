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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 9062a3da9a6020762114702b6cce6b42414ab92d
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197457"
---
# <a name="walkthrough-arrange-wpf-content-on-windows-forms-at-design-time"></a>Návod: uspořádání obsahu WPF v model Windows Forms v době návrhu

V tomto článku se dozvíte, jak používat funkce model Windows Forms rozložení, jako je například ukotvení a zarovnávacím čárám, k uspořádání ovládacích prvků Windows Presentation Foundation (WPF).

## <a name="prerequisites"></a>Požadavky

K dokončení tohoto Názorného postupu potřebujete Visual Studio.

## <a name="create-the-project"></a>Vytvoření projektu

Otevřete Visual Studio a vytvořte nový projekt aplikace model Windows Forms v Visual Basic nebo vizuálu C# s názvem `ArrangeElementHost`.

> [!NOTE]
> Při hostování obsahu WPF jsou podporovány C# pouze projekty a Visual Basic.

## <a name="create-the-wpf-control"></a>Vytvoření ovládacího prvku WPF

Po přidání ovládacího prvku WPF do projektu jej můžete uspořádat na formuláři.

1. Přidejte do projektu novou <xref:System.Windows.Controls.UserControl> WPF. Použijte výchozí název pro typ ovládacího prvku `UserControl1.xaml`. Další informace najdete v tématu [Návod: vytvoření nového obsahu WPF na model Windows Forms v době návrhu](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).

2. V zobrazení Návrh se ujistěte, že je vybrána možnost `UserControl1`.

3. V okně **vlastnosti** nastavte hodnotu <xref:System.Windows.FrameworkElement.Width%2A> a vlastnosti <xref:System.Windows.FrameworkElement.Height%2A> na **200**.

4. Nastavte hodnotu vlastnosti <xref:System.Windows.Controls.Control.Background%2A> na **modrou**.

5. Sestavte projekt.

## <a name="host-wpf-controls-in-a-layout-panel"></a>Hostování ovládacích prvků WPF na panelu rozložení

Ovládací prvky WPF lze v panelech rozložení použít stejným způsobem jako jiné ovládací prvky model Windows Forms.

1. Otevřete `Form1` v Návrhář formulářů.

2. V **sadě nástrojů**přetáhněte ovládací prvek <xref:System.Windows.Forms.TableLayoutPanel> do formuláře.

3. Na panelu inteligentních značek ovládacího prvku <xref:System.Windows.Forms.TableLayoutPanel> vyberte **Odebrat poslední řádek**.

4. Změňte velikost ovládacího prvku <xref:System.Windows.Forms.TableLayoutPanel> na větší šířku a výšku.

5. V sadě **nástrojů**poklikejte na `UserControl1` pro vytvoření instance `UserControl1` v první buňce ovládacího prvku <xref:System.Windows.Forms.TableLayoutPanel>.

   Instance `UserControl1` je hostována v novém ovládacím prvku <xref:System.Windows.Forms.Integration.ElementHost> s názvem `elementHost1`.

6. V **sadě nástrojů**poklikejte na `UserControl1` pro vytvoření další instance v druhé buňce ovládacího prvku <xref:System.Windows.Forms.TableLayoutPanel>.

7. V okně **Osnova dokumentu** vyberte `tableLayoutPanel1`.

8. V okně **vlastnosti** nastavte hodnotu vlastnosti <xref:System.Windows.Forms.Control.Padding%2A> na **10, 10, 10, 10**.

   Velikost obou <xref:System.Windows.Forms.Integration.ElementHost>ch ovládacích prvků se přizpůsobí novému rozložení.

## <a name="use-snaplines-to-align-wpf-controls"></a>Použití zarovnávacím čárám k zarovnání ovládacích prvků WPF

Zarovnávacím čárám umožňuje snadné zarovnání ovládacích prvků na formuláři. Zarovnávacím čárám můžete použít i k zarovnání ovládacích prvků WPF. Další informace najdete v tématu [Návod: uspořádání ovládacích prvků na model Windows Forms pomocí zarovnávacím čárám](../controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).

1. Z **panelu nástrojů**přetáhněte instanci `UserControl1` do formuláře a umístěte ji do prostoru pod ovládacím prvkem <xref:System.Windows.Forms.TableLayoutPanel>.

   Instance `UserControl1` je hostována v novém ovládacím prvku <xref:System.Windows.Forms.Integration.ElementHost> s názvem `elementHost3`.

2. Pomocí zarovnávacím čárám zarovnejte levý okraj `elementHost3` s levým okrajem ovládacího prvku <xref:System.Windows.Forms.TableLayoutPanel>.

3. Pomocí zarovnávacím čárám velikost `elementHost3` se stejnou šířkou jako <xref:System.Windows.Forms.TableLayoutPanel> ovládací prvek.

4. Přesuňte `elementHost3` směrem k ovládacímu prvku <xref:System.Windows.Forms.TableLayoutPanel> dokud se mezi ovládacími prvky snapline střed.

5. V okně **vlastnosti** nastavte hodnotu vlastnosti okraj na **20, 20, 20, 20**.

6. Přesuňte `elementHost3` pryč od ovládacího prvku <xref:System.Windows.Forms.TableLayoutPanel>, dokud se znovu neobjeví snapline Center. Centrum snapline nyní indikuje okraj 20.

7. Přesune `elementHost3` doprava, dokud její levý okraj není zarovnán s levým okrajem `elementHost1`.

8. Změní šířku `elementHost3`, dokud její pravý okraj není zarovnán s pravým okrajem `elementHost2`.

## <a name="anchor-and-dock-wpf-controls"></a>Ukotvení a ukotvení ovládacích prvků WPF

Ovládací prvek WPF hostovaný na formuláři má stejné chování při ukotvení a ukotvení jako jiné ovládací prvky model Windows Forms.

1. Vyberte `elementHost1`.

2. V okně **vlastnosti** nastavte vlastnost <xref:System.Windows.Forms.Control.Anchor%2A> na **nahoře, dole, vlevo, vpravo**.

3. Změňte velikost ovládacího prvku <xref:System.Windows.Forms.TableLayoutPanel> na větší velikost.

   Ovládací prvek `elementHost1` mění velikost pro vyplnění buňky.

4. Vyberte `elementHost2`.

5. V okně **vlastnosti** nastavte hodnotu vlastnosti <xref:System.Windows.Forms.Control.Dock%2A> na <xref:System.Windows.Forms.DockStyle.Fill>.

   Ovládací prvek `elementHost2` mění velikost pro vyplnění buňky.

6. Vyberte ovládací prvek <xref:System.Windows.Forms.TableLayoutPanel>.

7. Nastavte hodnotu vlastnosti <xref:System.Windows.Forms.Control.Dock%2A> na <xref:System.Windows.Forms.DockStyle.Top>.

8. Vyberte `elementHost3`.

9. Nastavte hodnotu vlastnosti <xref:System.Windows.Forms.Control.Dock%2A> na <xref:System.Windows.Forms.DockStyle.Fill>.

   Ovládací prvek `elementHost3` mění velikost, aby vyplnil zbývající místo ve formuláři.

10. Změňte velikost formuláře.

    Všechny tři <xref:System.Windows.Forms.Integration.ElementHost> řídí správné přizpůsobení velikosti.

    Další informace naleznete v tématu [Postupy: ukotvení a ukotvení podřízených ovládacích prvků v ovládacím prvku TableLayoutPanel](../controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md).

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Postupy: Ukotvení podřízených ovládacích prvků v ovládacím prvku TableLayoutPanel](../controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [Postupy: Zarovnání ovládacího prvku k okrajům formulářů během návrhu](../controls/how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)
- [Návod: Uspořádání ovládacích prvků ve Windows Forms pomocí zarovnávacích čar](../controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [Migrace a interoperabilita](../../wpf/advanced/migration-and-interoperability.md)
- [Používání ovládacích prvků WPF](using-wpf-controls.md)
- [Návrh kódu XAML v sadě Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
