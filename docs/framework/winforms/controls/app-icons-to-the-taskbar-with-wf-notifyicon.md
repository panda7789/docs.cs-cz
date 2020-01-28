---
title: Přidání ikon aplikace na hlavní panel se součástí NotifyIcon
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- TrayIcon
helpviewer_keywords:
- status area icons
- icons [Windows Forms], adding to taskbar
- NotifyIcon component
- taskbar [Windows Forms], adding icons
ms.assetid: d28c0fe6-aaf2-4df7-ad74-928d861a8510
ms.openlocfilehash: 46b50ecaabe75dba08fea922d7b5639031692269
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746245"
---
# <a name="how-to-add-application-icons-to-the-taskbar-with-the-windows-forms-notifyicon-component"></a>Postupy: Přidání ikon aplikací do TaskBar se součástí Windows Forms NotifyIcon

Komponenta model Windows Forms <xref:System.Windows.Forms.NotifyIcon> zobrazí v oznamovací oblasti hlavního panelu jednu ikonu. Chcete-li zobrazit více ikon ve stavové oblasti, je nutné mít na formuláři více <xref:System.Windows.Forms.NotifyIcon>ch součástí. Chcete-li nastavit ikonu zobrazenou pro ovládací prvek, použijte vlastnost <xref:System.Windows.Forms.NotifyIcon.Icon%2A>. Můžete také napsat kód v obslužné rutině události <xref:System.Windows.Forms.NotifyIcon.DoubleClick>, aby k nějakému problému došlo, když uživatel dvakrát klikne na ikonu. Můžete například vytvořit dialogové okno pro uživatele, aby se nakonfiguroval proces na pozadí reprezentovaný ikonou.

> [!NOTE]
> Komponenta <xref:System.Windows.Forms.NotifyIcon> se používá pouze pro účely oznámení, aby bylo možné upozornit uživatele, že došlo k akci nebo události, nebo došlo ke změně stavu nějakého řazení. Pro standardní interakci s aplikacemi byste měli použít nabídky, panely nástrojů a jiné prvky uživatelského rozhraní.

### <a name="to-set-the-icon"></a>Nastavení ikony

1. Přiřaďte hodnotu k vlastnosti <xref:System.Windows.Forms.NotifyIcon.Icon%2A>. Hodnota musí být typu `System.Drawing.Icon` a může být načtena ze souboru. ico. Můžete určit soubor ikony v kódu nebo kliknutím na tlačítko se třemi tečkami (![tlačítko se třemi tečkami (...) v okno Vlastnosti sady Visual Studio.](./media/visual-studio-ellipsis-button.png)) vedle vlastnosti <xref:System.Windows.Forms.NotifyIcon.Icon%2A> v okně **vlastnosti** a pak tento soubor vybrat v dialogovém okně **otevřít** , které se zobrazí.

2. Nastavte <xref:System.Windows.Forms.NotifyIcon.Visible%2A> vlastnost `true`.

3. Vlastnost <xref:System.Windows.Forms.NotifyIcon.Text%2A> nastavte na odpovídající řetězec popisu tlačítka.

     V následujícím příkladu kódu je cesta nastavená pro umístění ikony složka **dokumenty** . Toto umístění se používá, protože můžete předpokládat, že většina počítačů, na kterých běží operační systém Windows, bude obsahovat tuto složku. Volba tohoto umístění také umožňuje uživatelům s minimálními úrovněmi přístupu k systému bezpečně spustit aplikaci. Následující příklad vyžaduje formulář s již přidaným ovládacím prvkem <xref:System.Windows.Forms.NotifyIcon>. Také vyžaduje soubor ikony s názvem `Icon.ico`.

    ```vb
    ' You should replace the bold icon in the sample below
    ' with an icon of your own choosing.
    NotifyIcon1.Icon = New _
       System.Drawing.Icon(System.Environment.GetFolderPath _
       (System.Environment.SpecialFolder.Personal) _
       & "\Icon.ico")
    NotifyIcon1.Visible = True
    NotifyIcon1.Text = "Antivirus program"
    ```

    ```csharp
    // You should replace the bold icon in the sample below
    // with an icon of your own choosing.
    // Note the escape character used (@) when specifying the path.
    notifyIcon1.Icon =
       new System.Drawing.Icon (System.Environment.GetFolderPath
       (System.Environment.SpecialFolder.Personal)
       + @"\Icon.ico");
    notifyIcon1.Visible = true;
    notifyIcon1.Text = "Antivirus program";
    ```

    ```cpp
    // You should replace the bold icon in the sample below
    // with an icon of your own choosing.
    notifyIcon1->Icon = gcnew
       System::Drawing::Icon(String::Concat
       (System::Environment::GetFolderPath
       (System::Environment::SpecialFolder::Personal),
       "\\Icon.ico"));
    notifyIcon1->Visible = true;
    notifyIcon1->Text = "Antivirus program";
    ```

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.NotifyIcon>
- <xref:System.Windows.Forms.NotifyIcon.Icon%2A>
- [Postupy: Přidružení místní nabídky ke komponentě Windows Forms NotifyIcon](how-to-associate-a-shortcut-menu-with-a-windows-forms-notifyicon-component.md)
- [Komponenta NotifyIcon](notifyicon-component-windows-forms.md)
- [Přehled komponenty NotifyIcon](notifyicon-component-overview-windows-forms.md)
