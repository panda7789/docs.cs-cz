---
title: 'Postupy: Zkopírování a vložení ovládacího prvku ElementHost během návrhu'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, content copying and pasting
- interoperability [WPF]
- ElementHost control [Windows Forms], copying and pasting at design time
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: e570375d-2a68-44ba-b4f7-c781af2d20e8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: dfe5244e0c5b61fdf6d940dd16d8c280f013b12c
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666184"
---
# <a name="how-to-copy-and-paste-an-elementhost-control"></a>Postupy: Zkopírování a vložení ovládacího prvku ElementHost

Tento postup ukazuje, jak zkopírovat ovládací prvek Windows Presentation Foundation (WPF) do formuláře Windows v aplikaci Visual Studio.

1. V aplikaci Visual Studio přidejte nový WPF <xref:System.Windows.Controls.UserControl> do projektu model Windows Forms. Použijte výchozí název pro typ ovládacího prvku, `UserControl1.xaml`. Další informace najdete v tématu [Návod: Vytváření nového obsahu WPF v model Windows Forms v době](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)návrhu.

2. V okně **vlastnosti** nastavte hodnotu vlastností <xref:System.Windows.FrameworkElement.Width%2A> `UserControl1` a <xref:System.Windows.FrameworkElement.Height%2A> na hodnotu **200**.

3. Nastavte hodnotu <xref:System.Windows.Controls.Control.Background%2A> vlastnosti na modrou.

4. Sestavte projekt.

5. Otevřete `Form1` v Návrhář formulářů.

6. Z **panelu nástrojů**přetáhněte instanci `UserControl1` do formuláře.

   Instance `UserControl1` je hostována v novém <xref:System.Windows.Forms.Integration.ElementHost> ovládacím prvku s názvem `elementHost1`.

7. Když vyberete tuto možnost, zkopírujte ji do schránky stisknutím **kombinace kláves CTRL +** +**C.** `elementHost1`

8. Stisknutím klávesy **CTRL**+**V** vložte zkopírovaný ovládací prvek do formuláře.

   Ve formuláři <xref:System.Windows.Forms.Integration.ElementHost> se vytvoří `elementHost2` nový ovládací prvek s názvem.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Migrace a interoperabilita](../../wpf/advanced/migration-and-interoperability.md)
- [Používání ovládacích prvků WPF](using-wpf-controls.md)
- [Návrh kódu XAML v sadě Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)
