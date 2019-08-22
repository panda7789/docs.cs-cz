---
title: 'Návod: Přiřazení obsahu WPF v modelu Windows Forms během návrhu'
ms.date: 03/30/2017
helpviewer_keywords:
- WPF content [Windows Forms], assigning at design time
- ElementHost control [Windows Forms], assigning WPF content at design time
- interoperability [WPF]
- Windows Forms, content assignments
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: b3e9ef93-7e0f-4a2f-8f1e-3437609a1eb7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: bc5f5e2d8808c0a60df721bf2c0ed76b45ef49a0
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666250"
---
# <a name="walkthrough-assign-wpf-content-on-windows-forms-at-design-time"></a>Návod: Přiřazení obsahu WPF na model Windows Forms v době návrhu

Tento článek ukazuje, jak vybrat typy ovládacích prvků Windows Presentation Foundation (WPF), které chcete zobrazit ve formuláři. Můžete vybrat jakýkoli typ ovládacího prvku WPF, který je součástí projektu.

## <a name="prerequisites"></a>Požadavky

K dokončení tohoto Názorného postupu potřebujete Visual Studio.

## <a name="create-the-project"></a>Vytvoření projektu

Otevřete Visual Studio a vytvořte nový projekt aplikace model Windows Forms v Visual Basic nebo vizuálu C# s názvem `SelectingWpfContent`.

> [!NOTE]
> Při hostování obsahu WPF jsou podporovány C# pouze projekty a Visual Basic.

## <a name="create-the-wpf-control-types"></a>Vytvoření typů ovládacích prvků WPF

Po přidání typů ovládacích prvků WPF do projektu je můžete hostovat v různých <xref:System.Windows.Forms.Integration.ElementHost> ovládacích prvcích.

1. Přidejte do řešení nový <xref:System.Windows.Controls.UserControl> projekt WPF. Použijte výchozí název pro typ ovládacího prvku, `UserControl1.xaml`. Další informace najdete v tématu [Návod: Vytváření nového obsahu WPF v model Windows Forms v době](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)návrhu.

2. V zobrazení Návrh se ujistěte, že `UserControl1` je vybraná možnost.

3. V okně **vlastnosti** nastavte hodnotu <xref:System.Windows.FrameworkElement.Width%2A> vlastností a <xref:System.Windows.FrameworkElement.Height%2A> na **200**.

4. Přidejte ovládací prvek <xref:System.Windows.Controls.UserControl> do a <xref:System.Windows.Controls.TextBox.Text%2A> nastavte hodnotu vlastnosti na **hostovaný obsah.** <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType>

5. Přidejte do projektu druhý <xref:System.Windows.Controls.UserControl> WPF. Použijte výchozí název pro typ ovládacího prvku, `UserControl2.xaml`.

6. V okně **vlastnosti** nastavte hodnotu <xref:System.Windows.FrameworkElement.Width%2A> vlastností a <xref:System.Windows.FrameworkElement.Height%2A> na **200**.

7. Přidejte ovládací prvek <xref:System.Windows.Controls.UserControl> do a <xref:System.Windows.Controls.TextBox.Text%2A> nastavte hodnotu vlastnosti na **hostovaný obsah 2.** <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType>

   > [!NOTE]
   > Obecně byste měli hostovat propracovanější obsah WPF. <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> Ovládací prvek slouží pouze pro ilustrativní účely.

8. Sestavte projekt.

## <a name="select-wpf-controls"></a>Vybrat ovládací prvky WPF

<xref:System.Windows.Forms.Integration.ElementHost> Ovládacímu prvku, který je již hostitelem obsahu, můžete přiřadit jiný obsah WPF.

1. Otevřete `Form1` v Návrhář formulářů.

2. Na **panelu nástrojů**poklikejte na `UserControl1` `UserControl1` vytvoření instance ve formuláři.

   Instance `UserControl1` je hostována v novém <xref:System.Windows.Forms.Integration.ElementHost> ovládacím prvku s názvem `elementHost1`.

3. V panelu inteligentních značek pro `elementHost1`otevřete rozevírací seznam **Vybrat hostovaný obsah** .

4. V rozevíracím seznamu vyberte **UserControl2** .

   Ovládací `elementHost1` prvek je nyní hostitelem instance `UserControl2` typu.

5. V okně **vlastnosti** potvrďte, že <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> vlastnost je nastavená na **UserControl2**.

6. Ze **sady nástrojů**ve skupině **interoperability WPF** přetáhněte <xref:System.Windows.Forms.Integration.ElementHost> ovládací prvek do formuláře.

   Výchozí název nového ovládacího prvku je `elementHost2`.

7. V panelu inteligentních značek pro `elementHost2`otevřete rozevírací seznam **Vybrat hostovaný obsah** .

8. V rozevíracím seznamu vyberte **UserControl1** .

9. Ovládací `elementHost2` prvek je nyní hostitelem instance `UserControl1` typu.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Migrace a interoperabilita](../../wpf/advanced/migration-and-interoperability.md)
- [Používání ovládacích prvků WPF](using-wpf-controls.md)
- [Návrh kódu XAML v sadě Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)
