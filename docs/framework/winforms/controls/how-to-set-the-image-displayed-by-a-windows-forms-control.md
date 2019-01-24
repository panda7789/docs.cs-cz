---
title: 'Postupy: Nastavení obrázku zobrazovaného podle ovládací prvek Windows Forms'
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
ms.openlocfilehash: 93bc7970ce7c287273f8bd7ff50b07c6658e2a08
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54644921"
---
# <a name="how-to-set-the-image-displayed-by-a-windows-forms-control"></a>Postupy: Nastavení obrázku zobrazovaného podle ovládací prvek Windows Forms
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
