---
title: 'Návod: Vytvoření nového obsahu WPF ve Windows Forms během návrhu'
ms.date: 08/18/2018
helpviewer_keywords:
- interoperability [Windows Forms], WPF and Windows Forms
- WPF content [Windows Forms], hosting in Windows Forms
- hosting WPF content in Windows Forms
- ElementHost control
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: 2e92d8e8-f0e4-4df7-9f07-2acf35cd798c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: fc6f988d6ffd270eba4abe277ca34fa2eeec56fd
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197421"
---
# <a name="walkthrough-create-new-wpf-content-on-windows-forms-at-design-time"></a>Návod: vytvoření nového obsahu WPF v model Windows Forms v době návrhu

V tomto článku se dozvíte, jak vytvořit ovládací prvek Windows Presentation Foundation (WPF) pro použití v aplikacích založených na model Windows Forms.

## <a name="prerequisites"></a>Požadavky

K dokončení tohoto Názorného postupu potřebujete Visual Studio.

## <a name="create-the-project"></a>Vytvoření projektu

Otevřete Visual Studio a vytvořte nový projekt **aplikace model Windows Forms (.NET Framework)** v Visual Basic nebo vizuálu C# s názvem `HostingWpf`.

> [!NOTE]
> Při hostování obsahu WPF jsou podporovány C# pouze projekty a Visual Basic.

## <a name="create-a-new-wpf-control"></a>Vytvořit nový ovládací prvek WPF

Vytvoření nového ovládacího prvku WPF a jeho přidání do projektu je stejně snadné jako přidání jakékoli jiné položky do projektu. Návrhář formulářů pracuje s konkrétním druhem ovládacího prvku s názvem *složený ovládací*prvek nebo *uživatelským ovládacím prvkem*. Další informace o uživatelských ovládacích prvcích WPF naleznete v tématu <xref:System.Windows.Controls.UserControl>.

> [!NOTE]
> Typ <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> pro WPF je odlišný od typu uživatelského ovládacího prvku, který poskytuje model Windows Forms, který je také pojmenován <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>.

Vytvoření nového ovládacího prvku WPF:

1. V **Průzkumník řešení**přidejte do řešení nový projekt **knihovny uživatelských ovládacích prvků WPF (.NET Framework)** . Použijte výchozí název knihovny ovládacích prvků `WpfControlLibrary1`. Výchozí název ovládacího prvku je `UserControl1.xaml`.

   Přidání nového ovládacího prvku má následující důsledky:

   - Byl přidán soubor UserControl1. XAML.

   - Přidal se soubor UserControl1.xaml.cs (nebo UserControl1. XAML. vb). Tento soubor obsahuje kód na pozadí pro obslužné rutiny událostí a další implementace.

   - Přidaly se odkazy na sestavení WPF.

   - Soubor UserControl1. XAML se otevře v Návrháři WPF pro Visual Studio.

2. V zobrazení Návrh se ujistěte, že je vybrána možnost `UserControl1`.

3. V okně **vlastnosti** nastavte hodnotu <xref:System.Windows.FrameworkElement.Width%2A> a vlastnosti <xref:System.Windows.FrameworkElement.Height%2A> na **200**.

4. Z **panelu nástrojů**přetáhněte ovládací prvek <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> na návrhovou plochu.

5. V okně **vlastnosti** nastavte hodnotu vlastnosti <xref:System.Windows.Controls.TextBox.Text%2A> na **hostovaný obsah**.

   > [!NOTE]
   > Obecně byste měli hostovat propracovanější obsah WPF. <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> ovládací prvek slouží pouze pro ilustrativní účely.

6. Sestavte projekt.

## <a name="add-a-wpf-control-to-a-windows-form"></a>Přidání ovládacího prvku WPF do formuláře Windows

Nový ovládací prvek WPF je připravený k použití ve formuláři. Model Windows Forms používá ovládací prvek <xref:System.Windows.Forms.Integration.ElementHost> k hostování obsahu WPF.

Přidání ovládacího prvku WPF do formuláře Windows:

1. Otevřete `Form1` v Návrhář formulářů.

2. V **sadě nástrojů**Najděte kartu s názvem **WPFUserControlLibrary uživatelské ovládací prvky WPF**.

3. Přetáhněte instanci `UserControl1` do formuláře.

    - <xref:System.Windows.Forms.Integration.ElementHost> ovládací prvek je automaticky vytvořen na formuláři pro hostování ovládacího prvku WPF.

    - Ovládací prvek <xref:System.Windows.Forms.Integration.ElementHost> je pojmenován `elementHost1` a v okně **vlastnosti** lze zobrazit jeho vlastnost <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> je nastavena na hodnotu **UserControl1**.

    - Odkazy na sestavení WPF jsou přidány do projektu.

    - Ovládací prvek `elementHost1` má panel inteligentních značek, který zobrazuje dostupné možnosti hostování.

4. Na panelu inteligentních značek **úlohy ElementHost** vyberte **Dock v nadřazeném kontejneru**.

5. Stisknutím klávesy **F5** Sestavte a spusťte aplikaci.

## <a name="next-steps"></a>Další kroky

Model Windows Forms a WPF jsou různé technologie, ale jsou navržené tak, aby úzce fungovaly. Pokud chcete ve svých aplikacích zajistit rozsáhlejší vzhled a chování, vyzkoušejte následující:

- Hostování ovládacího prvku model Windows Forms na stránce WPF. Další informace naleznete v tématu [Návod: hostování ovládacího prvku model Windows Forms v](../../wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)subsystému WPF.

- Použijte model Windows Forms vizuální styly pro obsah WPF. Další informace najdete v tématu [Postup: Povolení vizuálních stylů v hybridní aplikaci](../../wpf/advanced/how-to-enable-visual-styles-in-a-hybrid-application.md).

- Změňte styl obsahu WPF. Další informace najdete v tématu [Návod: určení stylu obsahu WPF](walkthrough-styling-wpf-content.md).

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Migrace a interoperabilita](../../wpf/advanced/migration-and-interoperability.md)
- [Používání ovládacích prvků WPF](using-wpf-controls.md)
- [Návrh kódu XAML v sadě Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
