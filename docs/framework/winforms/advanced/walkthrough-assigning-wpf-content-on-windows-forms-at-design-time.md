---
title: Vybrat ovládací prvky WPF pro model Windows Forms
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- WPF content [Windows Forms], assigning at design time
- ElementHost control [Windows Forms], assigning WPF content at design time
- interoperability [WPF]
- Windows Forms, content assignments
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: b3e9ef93-7e0f-4a2f-8f1e-3437609a1eb7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 19f1dfec282b025f5a1fa367ec5fa9a52472c691
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746809"
---
# <a name="walkthrough-assign-wpf-content-on-windows-forms-at-design-time"></a>Návod: přiřazení obsahu WPF na model Windows Forms v době návrhu

Tento článek ukazuje, jak vybrat typy ovládacích prvků Windows Presentation Foundation (WPF), které chcete zobrazit ve formuláři. Můžete vybrat jakýkoli typ ovládacího prvku WPF, který je součástí projektu.

## <a name="prerequisites"></a>Požadavky

K dokončení tohoto Názorného postupu potřebujete Visual Studio.

## <a name="create-the-project"></a>Vytvoření projektu

Otevřete Visual Studio a vytvořte nový projekt aplikace model Windows Forms v Visual Basic nebo vizuálu C# s názvem `SelectingWpfContent`.

> [!NOTE]
> Při hostování obsahu WPF jsou podporovány C# pouze projekty a Visual Basic.

## <a name="create-the-wpf-control-types"></a>Vytvoření typů ovládacích prvků WPF

Po přidání typů ovládacích prvků WPF do projektu je můžete hostovat v různých <xref:System.Windows.Forms.Integration.ElementHost>ch ovládacích prvcích.

1. Přidejte do řešení nový projekt WPF <xref:System.Windows.Controls.UserControl>. Použijte výchozí název pro typ ovládacího prvku `UserControl1.xaml`. Další informace najdete v tématu [Návod: vytvoření nového obsahu WPF na model Windows Forms v době návrhu](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).

2. V zobrazení Návrh se ujistěte, že je vybrána možnost `UserControl1`.

3. V okně **vlastnosti** nastavte hodnotu <xref:System.Windows.FrameworkElement.Width%2A> a vlastnosti <xref:System.Windows.FrameworkElement.Height%2A> na **200**.

4. Do <xref:System.Windows.Controls.UserControl> přidejte ovládací prvek <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> a nastavte hodnotu vlastnosti <xref:System.Windows.Controls.TextBox.Text%2A> na **hostovaný obsah**.

5. Přidejte do projektu druhý <xref:System.Windows.Controls.UserControl> WPF. Použijte výchozí název pro typ ovládacího prvku `UserControl2.xaml`.

6. V okně **vlastnosti** nastavte hodnotu <xref:System.Windows.FrameworkElement.Width%2A> a vlastnosti <xref:System.Windows.FrameworkElement.Height%2A> na **200**.

7. Do <xref:System.Windows.Controls.UserControl> přidejte ovládací prvek <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> a nastavte hodnotu vlastnosti <xref:System.Windows.Controls.TextBox.Text%2A> na **hostovaný obsah 2**.

   > [!NOTE]
   > Obecně byste měli hostovat propracovanější obsah WPF. <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> ovládací prvek slouží pouze pro ilustrativní účely.

8. Sestavte projekt.

## <a name="select-wpf-controls"></a>Vybrat ovládací prvky WPF

Můžete přiřadit jiný obsah WPF k ovládacímu prvku <xref:System.Windows.Forms.Integration.ElementHost>, který je již hostitelem obsahu.

1. Otevřete `Form1` v Návrhář formulářů.

2. Na **panelu nástrojů**dvakrát klikněte na `UserControl1`. tím se vytvoří instance `UserControl1` ve formuláři.

   Instance `UserControl1` je hostována v novém ovládacím prvku <xref:System.Windows.Forms.Integration.ElementHost> s názvem `elementHost1`.

3. Na panelu inteligentních značek pro `elementHost1`otevřete rozevírací seznam **Vybrat hostovaný obsah** .

4. V rozevíracím seznamu vyberte **UserControl2** .

   Ovládací prvek `elementHost1` nyní hostuje instanci typu `UserControl2`.

5. V okně **vlastnosti** potvrďte, že vlastnost <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> je nastavena na hodnotu **UserControl2**.

6. Ze **sady nástrojů**ve skupině **interoperability WPF** přetáhněte ovládací prvek <xref:System.Windows.Forms.Integration.ElementHost> do formuláře.

   Výchozí název nového ovládacího prvku je `elementHost2`.

7. Na panelu inteligentních značek pro `elementHost2`otevřete rozevírací seznam **Vybrat hostovaný obsah** .

8. V rozevíracím seznamu vyberte **UserControl1** .

9. Ovládací prvek `elementHost2` nyní hostuje instanci typu `UserControl1`.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Migrace a interoperabilita](../../wpf/advanced/migration-and-interoperability.md)
- [Používání ovládacích prvků WPF](using-wpf-controls.md)
- [Návrh kódu XAML v sadě Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
