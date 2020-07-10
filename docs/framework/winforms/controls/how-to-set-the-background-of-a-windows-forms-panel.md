---
title: Nastavení pozadí panelu
description: Naučte se, jak nastavit barvu pozadí a obrázek pozadí model Windows Forms panelu pomocí návrháře.
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
ms.openlocfilehash: 109ff6184de9c79d1576207bbeb29ad939670b6f
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2020
ms.locfileid: "86173377"
---
# <a name="how-to-set-the-background-of-a-windows-forms-panel"></a>Postupy: Nastavení pozadí panelu Windows Forms
<xref:System.Windows.Forms.Panel>Ovládací prvek model Windows Forms může zobrazit barvu pozadí i obrázek pozadí. <xref:System.Windows.Forms.Control.BackColor%2A>Vlastnost nastavuje barvu pozadí pro obsažené ovládací prvky, jako jsou například popisky a přepínací tlačítka. Pokud <xref:System.Windows.Forms.Control.BackgroundImage%2A> vlastnost není nastavena, <xref:System.Windows.Forms.Control.BackColor%2A> Výběr vyplní celý panel. Pokud <xref:System.Windows.Forms.Control.BackgroundImage%2A> je vlastnost nastavena, bude obrázek zobrazen za obsažených ovládací prvky.  
  
### <a name="to-set-the-background-programmatically"></a>Programové nastavení pozadí  
  
1. Nastavte <xref:System.Windows.Forms.Control.BackColor%2A> vlastnost panelu na hodnotu typu <xref:System.Drawing.Color?displayProperty=nameWithType> .  
  
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
