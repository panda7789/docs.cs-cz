---
title: Nastavení pozadí panelu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- background colors [Windows Forms], Windows Forms Panel controls
- background images [Windows Forms], Windows Forms Panel controls
- Panel control [Windows Forms], background
- colors [Windows Forms], Windows Forms Panel controls
ms.assetid: 096cbd8d-45cc-47b8-b1ef-a27f60ea8be0
ms.openlocfilehash: ba2619354403793aea7ca15d43649da9637079a6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744740"
---
# <a name="how-to-set-the-background-of-a-windows-forms-panel"></a>Postupy: Nastavení pozadí panelu Windows Forms
Ovládací prvek model Windows Forms <xref:System.Windows.Forms.Panel> může zobrazit barvu pozadí i obrázek pozadí. Vlastnost <xref:System.Windows.Forms.Control.BackColor%2A> nastaví barvu pozadí pro obsažené ovládací prvky, například popisky a přepínače. Pokud vlastnost <xref:System.Windows.Forms.Control.BackgroundImage%2A> není nastavena, <xref:System.Windows.Forms.Control.BackColor%2A> výběr vyplní celý panel. Pokud je nastavena vlastnost <xref:System.Windows.Forms.Control.BackgroundImage%2A>, obrázek se zobrazí za obsažených ovládací prvky.  
  
### <a name="to-set-the-background-programmatically"></a>Programové nastavení pozadí  
  
1. Nastavte vlastnost <xref:System.Windows.Forms.Control.BackColor%2A> panelu na hodnotu typu <xref:System.Drawing.Color?displayProperty=nameWithType>.  
  
    ```vb  
    Panel1.BackColor = Color.AliceBlue  
    ```  
  
    ```csharp  
    panel1.BackColor = Color.AliceBlue;  
    ```  
  
    ```cpp  
    panel1->BackColor = Color::AliceBlue;  
    ```  
  
2. Nastavte vlastnost <xref:System.Windows.Forms.Control.BackgroundImage%2A> panelu pomocí metody <xref:System.Drawing.Image.FromFile%2A> třídy <xref:System.Drawing.Image?displayProperty=nameWithType>.  
  
    ```vb  
    ' You should replace the bolded image   
    ' in the sample below with an image of your own choosing.  
    Panel1.BackgroundImage = Image.FromFile _  
        (System.Environment.GetFolderPath _  
        (System.Environment.SpecialFolder.Personal) _  
        & "\Image.gif")  
    ```  
  
    ```csharp  
    // You should replace the bolded image   
    // in the sample below with an image of your own choosing.  
    // Note the escape character used (@) when specifying the path.  
    panel1.BackgroundImage = Image.FromFile  
       (System.Environment.GetFolderPath  
       (System.Environment.SpecialFolder.Personal)  
       + @"\Image.gif");  
    ```  
  
    ```cpp  
    // You should replace the bolded image   
    // in the sample below with an image of your own choosing.  
    panel1->BackgroundImage = Image::FromFile(String::Concat(  
       System::Environment::GetFolderPath  
       (System::Environment::SpecialFolder::Personal),  
       "\\Image.gif"));  
    ```  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.Control.BackColor%2A>
- <xref:System.Windows.Forms.Control.BackgroundImage%2A>
- [Ovládací prvek Panel](panel-control-windows-forms.md)
- [Přehled ovládacího prvku Panel](panel-control-overview-windows-forms.md)
