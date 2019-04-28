---
title: 'Postupy: Přidání ikon aplikací do TaskBar s komponentou Windows Forms NotifyIcon'
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
ms.openlocfilehash: 52c18b959361079aac6b95dc5d4584bf464a306a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61640320"
---
# <a name="how-to-add-application-icons-to-the-taskbar-with-the-windows-forms-notifyicon-component"></a>Postupy: Přidání ikon aplikací do TaskBar s komponentou Windows Forms NotifyIcon
Windows Forms <xref:System.Windows.Forms.NotifyIcon> součást zobrazuje jednu ikonu v oznamovací oblasti na hlavním panelu Stav. Chcete-li zobrazit více ikony ve stavové oblasti, musí mít více <xref:System.Windows.Forms.NotifyIcon> komponenty na formuláři. Pokud chcete nastavit ikony zobrazené pro ovládací prvek, použijte <xref:System.Windows.Forms.NotifyIcon.Icon%2A> vlastnost. Můžete také napsat kód <xref:System.Windows.Forms.NotifyIcon.DoubleClick> obslužná rutina události tak, že něco se stane, když uživatel dvakrát klikne na ikonu. Například může vytvořit dialogové okno se zobrazí uživateli konfigurovat proces na pozadí, který je reprezentován ikonou.  
  
> [!NOTE]
>  <xref:System.Windows.Forms.NotifyIcon> Komponenty se používá oznámení pouze pro účely, které uživatele upozorní, akce nebo událostí došlo k chybě nebo došlo ke změně stavu nějaké. Abyste používali nabídky, panely nástrojů a další prvky uživatelského rozhraní pro standardní interakce s aplikacemi.  
  
### <a name="to-set-the-icon"></a>Chcete-li nastavit ikonu  
  
1. Přiřaďte hodnotu <xref:System.Windows.Forms.NotifyIcon.Icon%2A> vlastnost. Hodnota musí být typu `System.Drawing.Icon` a ze souboru .ico, který lze načíst. Můžete určit soubor ikony v kódu nebo kliknutím na tlačítko se třemi tečkami (![VisualStudioEllipsesButton snímek obrazovky](../media/vbellipsesbutton.png "vbEllipsesButton")) vedle položky <xref:System.Windows.Forms.NotifyIcon.Icon%2A> vlastnost  **Vlastnosti** okna a pak vyberete soubor v **otevřít** dialogové okno, které se zobrazí.  
  
2. Nastavte <xref:System.Windows.Forms.NotifyIcon.Visible%2A> vlastnost `true`.  
  
3. Nastavte <xref:System.Windows.Forms.NotifyIcon.Text%2A> vlastnosti k odpovídající řetězec popisku.  
  
     V následujícím příkladu kódu nastavena cesta pro umístění ikony **dokumenty** složky. Toto umístění se používá, protože můžete předpokládat, že většina počítačů s operačním systémem Windows bude obsahovat této složky. Výběrem tohoto umístění taky umožňuje uživatelům s úrovní přístupu minimální systém bezpečně spouštět aplikace. V následujícím příkladu vyžaduje formulář s <xref:System.Windows.Forms.NotifyIcon> ovládací prvek již přidán. Také budete potřebovat soubor ikony s názvem `Icon.ico`.  
  
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
- [Postupy: Přidružení místní nabídky s komponentou Windows Forms NotifyIcon](how-to-associate-a-shortcut-menu-with-a-windows-forms-notifyicon-component.md)
- [Komponenta NotifyIcon](notifyicon-component-windows-forms.md)
- [Přehled komponenty NotifyIcon](notifyicon-component-overview-windows-forms.md)
