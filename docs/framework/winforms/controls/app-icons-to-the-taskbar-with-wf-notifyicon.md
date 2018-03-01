---
title: "Postupy: Přidání ikon aplikací do TaskBar se součástí Windows Forms NotifyIcon"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d795df8e8b514345632491fd6afdd618c2f18ec2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-application-icons-to-the-taskbar-with-the-windows-forms-notifyicon-component"></a>Postupy: Přidání ikon aplikací do TaskBar se součástí Windows Forms NotifyIcon
Windows Forms <xref:System.Windows.Forms.NotifyIcon> součást zobrazí jeden ikonu v oznamovací oblasti stav na hlavním panelu. Chcete-li zobrazit více ikony ve stavové oblasti, musíte mít více <xref:System.Windows.Forms.NotifyIcon> součásti ve formuláři. Pokud chcete nastavit ikonu zobrazí pro ovládací prvek, použijte <xref:System.Windows.Forms.NotifyIcon.Icon%2A> vlastnost. Můžete napsat kód ve <xref:System.Windows.Forms.NotifyIcon.DoubleClick> obslužné rutiny události tak, že něco se stane, když uživatel poklikáním na ikonu. Například můžete dokonce vytvářet dialogové okno zobrazí uživatele, pro konfiguraci reprezentována ikonu proces na pozadí.  
  
> [!NOTE]
>  <xref:System.Windows.Forms.NotifyIcon> Součást se používá oznámení pouze pro účely, které uživatele upozorní, akci nebo událostí došlo k chybě nebo došlo ke změně stavu některé řazení. Měli byste použít nabídky, panely nástrojů a další prvky uživatelského rozhraní pro standardní interakce s aplikacemi.  
  
### <a name="to-set-the-icon"></a>Chcete-li nastavit ikonu  
  
1.  Přiřazení hodnoty k <xref:System.Windows.Forms.NotifyIcon.Icon%2A> vlastnost. Hodnota musí být typu `System.Drawing.Icon` a ze souboru .ico, který lze načíst. Můžete určit soubor ikony v kódu nebo kliknutím na tlačítko se třemi tečkami (![VisualStudioEllipsesButton snímek](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) vedle položky <xref:System.Windows.Forms.NotifyIcon.Icon%2A> vlastnost  **Vlastnosti** okna a pak vybrat soubor v **otevřete** zobrazeném dialogu.  
  
2.  Nastavte <xref:System.Windows.Forms.NotifyIcon.Visible%2A> vlastnost `true`.  
  
3.  Nastavte <xref:System.Windows.Forms.NotifyIcon.Text%2A> vlastnost na příslušné řetězec popisku.  
  
     V následujícím příkladu kódu cesta pro umístění ikony je nastavena **dokumenty** složky. Toto umístění se používá, protože můžete předpokládat, že většina počítačů s operačním systémem Windows bude obsahovat této složky. Výběr toto umístění taky umožňuje uživatelům s minimální systém úrovně přístupu pro aplikaci bezpečně spustit. Následující příklad vyžaduje formulář s <xref:System.Windows.Forms.NotifyIcon> ovládací prvek již přidán. Také budete potřebovat soubor ikony s názvem `Icon.ico`.  
  
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
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.NotifyIcon>  
 <xref:System.Windows.Forms.NotifyIcon.Icon%2A>  
 [Postupy: Přidružení místní nabídky ke komponentě Windows Forms NotifyIcon](../../../../docs/framework/winforms/controls/how-to-associate-a-shortcut-menu-with-a-windows-forms-notifyicon-component.md)  
 [Komponenta NotifyIcon](../../../../docs/framework/winforms/controls/notifyicon-component-windows-forms.md)  
 [Přehled komponenty NotifyIcon](../../../../docs/framework/winforms/controls/notifyicon-component-overview-windows-forms.md)
