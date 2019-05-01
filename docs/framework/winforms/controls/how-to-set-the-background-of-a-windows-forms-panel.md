---
title: 'Postupy: Nastavení pozadí panelu Windows Forms'
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
ms.openlocfilehash: 9336be2aebb10e5c0bd0bf4648cae34a3b5fe7c3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62013176"
---
# <a name="how-to-set-the-background-of-a-windows-forms-panel"></a>Postupy: Nastavení pozadí panelu Windows Forms
Windows Forms <xref:System.Windows.Forms.Panel> ovládací prvek mohl zobrazit barvu pozadí a obrázek na pozadí. <xref:System.Windows.Forms.Control.BackColor%2A> Vlastnost nastaví barvu pozadí pro obsažené ovládací prvky, například s popisky a přepínače. Pokud <xref:System.Windows.Forms.Control.BackgroundImage%2A> vlastnost není nastavená, <xref:System.Windows.Forms.Control.BackColor%2A> výběr vyplní celý panelu. Pokud <xref:System.Windows.Forms.Control.BackgroundImage%2A> je hodnota nastavena, zobrazí se na obrázku za obsažené ovládací prvky.  
  
### <a name="to-set-the-background-programmatically"></a>Programové nastavení na pozadí  
  
1. Nastavení panelu <xref:System.Windows.Forms.Control.BackColor%2A> vlastnost na hodnotu typu <xref:System.Drawing.Color?displayProperty=nameWithType>.  
  
    ```vb  
    Panel1.BackColor = Color.AliceBlue  
    ```  
  
    ```csharp  
    panel1.BackColor = Color.AliceBlue;  
    ```  
  
    ```cpp  
    panel1->BackColor = Color::AliceBlue;  
    ```  
  
2. Nastavení panelu <xref:System.Windows.Forms.Control.BackgroundImage%2A> pomocí vlastnosti <xref:System.Drawing.Image.FromFile%2A> metodu <xref:System.Drawing.Image?displayProperty=nameWithType> třídy.  
  
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.Control.BackColor%2A>
- <xref:System.Windows.Forms.Control.BackgroundImage%2A>
- [Ovládací prvek Panel](panel-control-windows-forms.md)
- [Přehled ovládacího prvku Panel](panel-control-overview-windows-forms.md)
