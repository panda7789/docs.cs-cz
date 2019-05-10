---
title: 'Postupy: Zkopírování a vložení ovládacího prvku ElementHost během návrhu'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, content copying and pasting
- interoperability [WPF]
- ElementHost control [Windows Forms], copying and pasting at design time
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: e570375d-2a68-44ba-b4f7-c781af2d20e8
ms.openlocfilehash: 0f3367deaaec04744a3f812d7f2d08047d7eb588
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211371"
---
# <a name="how-to-copy-and-paste-an-elementhost-control-at-design-time"></a>Postupy: Zkopírování a vložení ovládacího prvku ElementHost během návrhu

Tento postup ukazuje, jak zkopírovat Windows Presentation Foundation (WPF) ovládací prvek na formuláři Windows v sadě Visual Studio.

## <a name="copy-and-paste-an-elementhost-control-at-design-time"></a>Kopírování a vložení ovládacího prvku ElementHost během návrhu

1. Přidat nový WPF <xref:System.Windows.Controls.UserControl> do projektu Windows Forms. Použití výchozího názvu pro typ ovládacího prvku `UserControl1.xaml`. Další informace najdete v tématu [názorný postup: Vytvoření nového obsahu WPF ve Windows Forms v době návrhu](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).

2. V **vlastnosti** okno, nastavte hodnotu <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A> vlastnosti `UserControl1` k `200`.

3. Nastavte hodnotu <xref:System.Windows.Controls.Control.Background%2A> vlastnost `Blue`.

4. Sestavte projekt.

5. Otevřít `Form1` v Návrháři formulářů Windows.

6. Z **nástrojů**, přetáhněte instance `UserControl1` do formuláře.

   Instance `UserControl1` hostována v novém <xref:System.Windows.Forms.Integration.ElementHost> ovládací prvek s názvem `elementHost1`.

7. S `elementHost1` vybrána, stiskněte CTRL + C zkopírujte do schránky.

8. Stisknutím kláves CTRL + V vložte zkopírovaný ovládací prvek na formuláři.

   Nový <xref:System.Windows.Forms.Integration.ElementHost> ovládací prvek s názvem `elementHost2` se vytvoří ve formuláři.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Migrace a interoperabilita](../../wpf/advanced/migration-and-interoperability.md)
- [Používání ovládacích prvků WPF](using-wpf-controls.md)
- [Návrh kódu XAML v sadě Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)
