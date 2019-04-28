---
title: 'Návod: Vytvoření nového obsahu WPF v modelu Windows Forms během návrhu'
ms.date: 08/18/2018
helpviewer_keywords:
- interoperability [Windows Forms], WPF and Windows Forms
- WPF content [Windows Forms], hosting in Windows Forms
- hosting WPF content in Windows Forms
- ElementHost control
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: 2e92d8e8-f0e4-4df7-9f07-2acf35cd798c
ms.openlocfilehash: ed48db399ba47f0e6be96f7bca33d3892b19e433
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61747677"
---
# <a name="walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time"></a>Návod: Vytvoření nového obsahu WPF v modelu Windows Forms během návrhu

Toto téma ukazuje, jak vytvořit ovládací prvek Windows Presentation Foundation (WPF) pro použití ve svých aplikacích pomocí formulářů Windows.

V tomto podrobném návodu můžete provádět následující úlohy:

- Vytvoření projektu.

- Vytvořte nový ovládací prvek WPF.

- Přidání nového ovládacího prvku WPF do formuláře Windows. Ovládací prvek WPF je hostován v <xref:System.Windows.Forms.Integration.ElementHost> ovládacího prvku.

## <a name="prerequisites"></a>Požadavky

K dokončení tohoto návodu budete potřebovat následující komponenty:

- Visual Studio 2017

## <a name="creating-the-project"></a>Vytvoření projektu

Prvním krokem je vytvoření projektu Windows Forms. Otevřít Visual Studio a vytvořte nový **aplikace Windows Forms (.NET Framework)** projektu v jazyce Visual Basic nebo Visual C# s názvem `HostingWpf`.

> [!NOTE]
> Při hostování obsahu WPF, jsou podporovány pouze projekty C# a Visual Basic.

## <a name="creating-a-new-wpf-control"></a>Vytvoření nového ovládacího prvku WPF

Vytvoření nového ovládacího prvku WPF a jeho přidání do projektu je stejně jednoduché jako přidání jakoukoli jinou položku do projektu. Návrhář formulářů Windows funguje s konkrétní druh ovládacího prvku s názvem *složeného ovládacího prvku*, nebo *uživatelský ovládací prvek*. Další informace o uživatelských ovládacích prvcích WPF naleznete v tématu <xref:System.Windows.Controls.UserControl>.

> [!NOTE]
> <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> Zadejte pro WPF se liší od typ ovládacího prvku uživatel k dispozici ve Windows Forms, který se také nazývá <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>.

### <a name="to-create-a-new-wpf-control"></a>Chcete-li vytvořit nový ovládací prvek WPF

1. V **Průzkumníka řešení**, přidejte novou **Knihovna uživatelských ovládacích prvků WPF (.NET Framework)** projektu do řešení. Použít výchozí název knihovny ovládacích prvků `WpfControlLibrary1`. Výchozí název ovládacího prvku je `UserControl1.xaml`.

     Přidání nového ovládacího prvku má následující důsledky:

    - Přidání souboru UserControl1.xaml.

    - Přidání souboru UserControl1.xaml.cs nebo UserControl1.xaml.vb. Tento soubor obsahuje kód na pozadí pro obslužné rutiny událostí a jiné implementace.

    - Jsou přidány odkazy na sestavení WPF.

    - Soubor UserControl1.xaml otevře [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)].

2. V návrhovém zobrazení, ujistěte se, že `UserControl1` zaškrtnuto. Další informace najdete v tématu [jak: Vyberte a přesuňte prvků na návrhové ploše](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb514527(v=vs.100)).

3. V **vlastnosti** okno, nastavte hodnotu <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A> vlastností **200**.

4. Z **nástrojů**, přetáhněte <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> ovládací prvek na návrhovou plochu.

5. V **vlastnosti** okno, nastavte hodnotu <xref:System.Windows.Controls.TextBox.Text%2A> vlastnost **hostované obsahu**.

    > [!NOTE]
    > Obecně byste neměli hostit složitější obsahu WPF. <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> Ovládací prvek se tady používá pouze pro ilustraci.

6. Sestavte projekt.

## <a name="adding-a-wpf-control-to-a-windows-form"></a>Přidání ovládacího prvku WPF na formuláři Windows

Nový ovládací prvek WPF je připravená k použití ve formuláři. Windows Forms používá <xref:System.Windows.Forms.Integration.ElementHost> ovládacího prvku na hostování obsahu WPF.

### <a name="to-add-a-wpf-control-to-a-windows-form"></a>Přidání ovládacího prvku WPF do formuláře Windows

1. Otevřít `Form1` v Návrháři formulářů Windows.

2. V **nástrojů**, najít na kartě s popiskem **uživatelské ovládací prvky WPF WPFUserControlLibrary**.

3. Přetáhněte instance `UserControl1` do formuláře.

    - <xref:System.Windows.Forms.Integration.ElementHost> Ovládací prvek je automaticky vytvořen ve formuláři pro hostování ovládacího prvku WPF.

    - <xref:System.Windows.Forms.Integration.ElementHost> Ovládací prvek má název `elementHost1` a **vlastnosti** okně můžete zobrazit jeho <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> je nastavena na **UserControl1**.

    - Do projektu přidají odkazy na sestavení WPF.

    - `elementHost1` Má ovládací prvek panelu inteligentních značek, které jsou uvedené dostupné možnosti hostování.

4. V **ElementHost úlohy** panelu inteligentních značek, vyberte **ukotvit v nadřazeném kontejneru**.

5. Stisknutím klávesy **F5** sestavíte a spustíte aplikaci.

## <a name="next-steps"></a>Další kroky

Windows Forms a WPF jsou různé technologie, ale jsou určené ke úzce spolupracovat. K poskytování bohatších vzhled a chování ve svých aplikacích, zkuste následující:

- Hostování ovládacího prvku Windows Forms na stránce WPF. Další informace najdete v tématu [názorný postup: Ovládací prvek hostování Windows Forms v subsystému WPF](../../wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md).

- Použití vizuálních stylů Windows Forms k vašemu obsahu WPF. Další informace najdete v tématu [jak: Povolení vizuálních stylů v hybridní aplikaci](../../wpf/advanced/how-to-enable-visual-styles-in-a-hybrid-application.md).

- Změna stylu obsahu WPF. Další informace najdete v tématu [názorný postup: Určení stylu obsahu WPF](walkthrough-styling-wpf-content.md).

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Migrace a interoperabilita](../../wpf/advanced/migration-and-interoperability.md)
- [Používání ovládacích prvků WPF](using-wpf-controls.md)
- [Návrh kódu XAML v sadě Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)
