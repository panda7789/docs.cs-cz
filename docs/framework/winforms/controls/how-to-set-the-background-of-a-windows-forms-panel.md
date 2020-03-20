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
ms.openlocfilehash: 36e552475334c25b9d5a6fafb82155c6ebcba266
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182099"
---
# <a name="how-to-set-the-background-of-a-windows-forms-panel"></a>Postupy: Nastavení pozadí panelu Windows Forms
Ovládací prvek <xref:System.Windows.Forms.Panel> Windows Forms může zobrazit barvu pozadí i obrázek pozadí. Vlastnost <xref:System.Windows.Forms.Control.BackColor%2A> nastaví barvu pozadí pro obsažené ovládací prvky, jako jsou popisky a přepínací tlačítka. Pokud <xref:System.Windows.Forms.Control.BackgroundImage%2A> vlastnost není nastavena, <xref:System.Windows.Forms.Control.BackColor%2A> výběr vyplní celý panel. Pokud <xref:System.Windows.Forms.Control.BackgroundImage%2A> je vlastnost nastavena, obraz se zobrazí za obsažené ovládací prvky.  
  
### <a name="to-set-the-background-programmatically"></a>Nastavení programového pozadí  
  
1. Nastavte <xref:System.Windows.Forms.Control.BackColor%2A> vlastnost panelu na hodnotu <xref:System.Drawing.Color?displayProperty=nameWithType>typu .  
  
    ```vb  
    Panel1.BackColor = Color.AliceBlue  
    ```  
  
    ```csharp  
    panel1.BackColor = Color.AliceBlue;  
    ```  
  
    ```cpp  
    panel1->BackColor = Color::AliceBlue;  
    ```  
  
2. Nastavte <xref:System.Windows.Forms.Control.BackgroundImage%2A> vlastnost panelu pomocí <xref:System.Drawing.Image.FromFile%2A> metody <xref:System.Drawing.Image?displayProperty=nameWithType> třídy.  
  
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
