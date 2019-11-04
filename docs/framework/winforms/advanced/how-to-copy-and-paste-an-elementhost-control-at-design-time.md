---
title: 'Postupy: Zkopírování a vložení ovládacího prvku ElementHost během návrhu'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, content copying and pasting
- interoperability [WPF]
- ElementHost control [Windows Forms], copying and pasting at design time
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: e570375d-2a68-44ba-b4f7-c781af2d20e8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e89510558274558e560bf810afe746e250ff26a4
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459227"
---
# <a name="how-to-copy-and-paste-an-elementhost-control"></a>Postupy: zkopírování a vložení ovládacího prvku ElementHost

Tento postup ukazuje, jak zkopírovat ovládací prvek Windows Presentation Foundation (WPF) do formuláře Windows v aplikaci Visual Studio.

1. V aplikaci Visual Studio přidejte novou <xref:System.Windows.Controls.UserControl> WPF do projektu model Windows Forms. Použijte výchozí název pro typ ovládacího prvku `UserControl1.xaml`. Další informace najdete v tématu [Návod: vytvoření nového obsahu WPF na model Windows Forms v době návrhu](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).

2. V okně **vlastnosti** nastavte hodnotu vlastnosti <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A> `UserControl1` na **200**.

3. Set the value of the <xref:System.Windows.Controls.Control.Background%2A> property to **Blue**.

4. Sestavte projekt.

5. Open `Form1` in the Windows Forms Designer.

6. From the **Toolbox**, drag an instance of `UserControl1` onto the form.

   An instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.

7. With `elementHost1` selected, press **Ctrl**+**C** to copy it to the clipboard.

8. Press **Ctrl**+**V** to paste the copied control onto the form.

   A new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost2` is created on the form.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Migrace a interoperabilita](../../wpf/advanced/migration-and-interoperability.md)
- [Používání ovládacích prvků WPF](using-wpf-controls.md)
- [Návrh kódu XAML v sadě Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
