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
ms.openlocfilehash: 3d1887eb1161f714962c2c26d6fe618749b26c0f
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197475"
---
# <a name="how-to-copy-and-paste-an-elementhost-control"></a>Postupy: zkopírování a vložení ovládacího prvku ElementHost

Tento postup ukazuje, jak zkopírovat ovládací prvek Windows Presentation Foundation (WPF) do formuláře Windows v aplikaci Visual Studio.

1. V aplikaci Visual Studio přidejte novou <xref:System.Windows.Controls.UserControl> WPF do projektu model Windows Forms. Použijte výchozí název pro typ ovládacího prvku `UserControl1.xaml`. Další informace najdete v tématu [Návod: vytvoření nového obsahu WPF na model Windows Forms v době návrhu](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).

2. V okně **vlastnosti** nastavte hodnotu vlastnosti <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A> `UserControl1` na **200**.

3. Nastavte hodnotu vlastnosti <xref:System.Windows.Controls.Control.Background%2A> na **modrou**.

4. Sestavte projekt.

5. Otevřete `Form1` v Návrhář formulářů.

6. Z **panelu nástrojů**přetáhněte instanci `UserControl1` do formuláře.

   Instance `UserControl1` je hostována v novém ovládacím prvku <xref:System.Windows.Forms.Integration.ElementHost> s názvem `elementHost1`.

7. Pokud je vybrána možnost `elementHost1`, stiskněte klávesu **Ctrl**+**C** a zkopírujte ji do schránky.

8. Stisknutím **kombinace kláves Ctrl**+**V** vložte zkopírovaný ovládací prvek do formuláře.

   Ve formuláři se vytvoří nový ovládací prvek <xref:System.Windows.Forms.Integration.ElementHost> s názvem `elementHost2`.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Migrace a interoperabilita](../../wpf/advanced/migration-and-interoperability.md)
- [Používání ovládacích prvků WPF](using-wpf-controls.md)
- [Návrh kódu XAML v sadě Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
