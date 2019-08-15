---
title: 'Postupy: Načtení obrázku pomocí návrháře (model Windows Forms)'
ms.date: 03/30/2017
helpviewer_keywords:
- picture formats
- images [Windows Forms], displaying on Windows Forms
- pictures [Windows Forms], displaying
- forms [Windows Forms], displaying images
- PictureBox control [Windows Forms], adding pictures
ms.assetid: 4dc7b973-afb1-4276-8322-20825af96655
ms.openlocfilehash: 818bc63b5b3bea6c73804f716a72ba3cd1a62b4c
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039682"
---
# <a name="how-to-load-a-picture-using-the-designer-windows-forms"></a>Postupy: Načtení obrázku pomocí návrháře (model Windows Forms)

Pomocí ovládacího prvku <xref:System.Windows.Forms.PictureBox> model Windows Forms můžete načíst a zobrazit obrázek ve formuláři v době návrhu <xref:System.Windows.Forms.PictureBox.Image%2A> nastavením vlastnosti na platný obrázek. V následující tabulce jsou uvedeny přijatelné typy souborů.

|type|Přípona názvu souboru|
|---|---|
|Monochromatick|. bmp|
|Ikona|.ico|
|GIF|. gif|
|Soubory|.wmf|
|JPEG|.jpg|

## <a name="to-display-a-picture-at-design-time"></a>Zobrazení obrázku v době návrhu

1. Nakreslete <xref:System.Windows.Forms.PictureBox> ovládací prvek na formuláři.

2. V okně **vlastnosti** vyberte <xref:System.Windows.Forms.PictureBox.Image%2A> vlastnost a potom kliknutím na tlačítko se třemi tečkami zobrazte dialogové okno **otevřít** .

3. Pokud hledáte určitý typ souboru (například soubory. gif), vyberte ho v poli **soubory typu** .

4. Vyberte soubor, který chcete zobrazit.

## <a name="to-clear-the-picture-at-design-time"></a>Vymazání obrázku v době návrhu

1. V okně **vlastnosti** vyberte <xref:System.Windows.Forms.PictureBox.Image%2A> vlastnost. Klikněte pravým tlačítkem myši na miniaturu malého obrázku, který se zobrazí nalevo od názvu objektu obrázku, a pak zvolte možnost **obnovit**.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.PictureBox>
- [Přehled ovládacího prvku PictureBox](picturebox-control-overview-windows-forms.md)
- [Postupy: Změna velikosti nebo umístění obrázku v době běhu](how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms.md)
- [Postupy: Nastavit obrázky v době běhu](how-to-set-pictures-at-run-time-windows-forms.md)
- [Ovládací prvek PictureBox](picturebox-control-windows-forms.md)
