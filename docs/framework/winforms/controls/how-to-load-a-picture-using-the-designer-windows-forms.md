---
title: 'Postupy: Načtení obrázku pomocí Návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- picture formats
- images [Windows Forms], displaying on Windows Forms
- pictures [Windows Forms], displaying
- forms [Windows Forms], displaying images
- PictureBox control [Windows Forms], adding pictures
ms.assetid: 4dc7b973-afb1-4276-8322-20825af96655
ms.openlocfilehash: 12b90d561a18fcffaafb9c45b7fa6be6dd060215
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736328"
---
# <a name="how-to-load-a-picture-using-the-designer-windows-forms"></a>Postupy: Načtení obrázku pomocí Návrháře (Windows Forms)

Pomocí ovládacího prvku model Windows Forms <xref:System.Windows.Forms.PictureBox> můžete načíst a zobrazit obrázek ve formuláři v době návrhu nastavením vlastnosti <xref:System.Windows.Forms.PictureBox.Image%2A> na platný obrázek. V následující tabulce jsou uvedeny přijatelné typy souborů.

|Typ|Přípona názvu souboru|
|---|---|
|Monochromatick|. bmp|
|Ikona|.ico|
|GIF|. gif|
|Soubory|.wmf|
|JPEG|.jpg|

## <a name="to-display-a-picture-at-design-time"></a>Zobrazení obrázku v době návrhu

1. Nakreslete ovládací prvek <xref:System.Windows.Forms.PictureBox> na formuláři.

2. V okně **vlastnosti** vyberte vlastnost <xref:System.Windows.Forms.PictureBox.Image%2A> a potom vyberte tlačítko se třemi tečkami, aby se zobrazilo dialogové okno **otevřít** .

3. Pokud hledáte určitý typ souboru (například soubory. gif), vyberte ho v poli **soubory typu** .

4. Vyberte soubor, který chcete zobrazit.

## <a name="to-clear-the-picture-at-design-time"></a>Vymazání obrázku v době návrhu

1. V okně **vlastnosti** vyberte vlastnost <xref:System.Windows.Forms.PictureBox.Image%2A>. Klikněte pravým tlačítkem myši na miniaturu malého obrázku, který se zobrazí nalevo od názvu objektu obrázku, a pak zvolte možnost **obnovit**.

## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.PictureBox>
- [Přehled ovládacího prvku PictureBox](picturebox-control-overview-windows-forms.md)
- [Postupy: Změna velikosti či umístění obrázku za běhu](how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms.md)
- [Postupy: Nastavení obrázků za běhu](how-to-set-pictures-at-run-time-windows-forms.md)
- [Ovládací prvek PictureBox](picturebox-control-windows-forms.md)
