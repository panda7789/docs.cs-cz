---
title: 'Postupy: Nastavení obrázku zobrazovaného ovládacím prvkem Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Button control [Windows Forms], images
- Windows Forms controls, images
- controls [Windows Forms], images
- images [Windows Forms], Windows Forms controls
- examples [Windows Forms], controls
ms.assetid: 9445af8f-4f62-48b0-a3f6-068058964b9f
ms.openlocfilehash: 031ddcb3b852e75353fed7420735350e79f23df3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59085087"
---
# <a name="how-to-set-the-image-displayed-by-a-windows-forms-control"></a>Postupy: Nastavení obrázku zobrazovaného ovládacím prvkem Windows Forms
Několik ovládacích prvků Windows Forms nemohl zobrazit obrázky. Tyto Image může být ikon, které vysvětluje účel ovládacího prvku, jako je například ikonu diskety na tlačítko, které označuje **Uložit** příkazu. Ikony, případně může být obrázky na pozadí vzhledu a chování, které chcete poskytnout ovládací prvek.  
  
### <a name="to-set-the-image-displayed-by-a-control"></a>K nastavení obrázku zobrazovaného ovládacím prvkem  
  
1.  Nastavit u tohoto prvku `Image` nebo `BackgroundImage` vlastnost na objekt typu <xref:System.Drawing.Image>. Obecně platí, můžete se načítá image ze souboru pomocí <xref:System.Drawing.Image.FromFile%2A> metody.  
  
     V následujícím příkladu kódu nastavena cesta pro umístění image je **obrázky** složky. Tento adresář bude obsahovat většinu počítačů s operačním systémem Windows. Také to umožňuje uživatelům s úrovní přístupu minimální systém bezpečně spouštět aplikace. Následující příklad kódu vyžaduje, abyste už měli formulář s <xref:System.Windows.Forms.PictureBox> přidán ovládací prvek.  
  
    ```vb  
    ' Replace the image named below  
    ' with an icon of your own choosing.  
    PictureBox1.Image = Image.FromFile _  
       (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.MyPictures) _  
       & "\Image.gif")  
    ```  
  
    ```csharp  
    // Replace the image named below  
    // with an icon of your own choosing.  
    // Note the escape character used (@) when specifying the path.  
    pictureBox1.Image = Image.FromFile  
       (System.Environment.GetFolderPath  
       (System.Environment.SpecialFolder.MyPictures)  
       + @"\Image.gif");  
    ```  
  
    ```cpp  
    // Replace the image named below  
    // with an icon of your own choosing.  
    pictureBox1->Image = Image::FromFile(String::Concat  
       (System::Environment::GetFolderPath  
       (System::Environment::SpecialFolder::MyPictures),  
       "\\Image.gif"));  
    ```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Drawing.Image.FromFile%2A>
- <xref:System.Drawing.Image>
- <xref:System.Windows.Forms.Control.BackgroundImage%2A>
