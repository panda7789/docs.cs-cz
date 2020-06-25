---
title: 'Postupy: Načtení obrázku pomocí Návrháře'
description: Naučte se, jak pomocí ovládacího prvku model Windows Forms PictureBox načíst a zobrazit obrázek ve formuláři v době návrhu.
ms.date: 03/30/2017
helpviewer_keywords:
- picture formats
- images [Windows Forms], displaying on Windows Forms
- pictures [Windows Forms], displaying
- forms [Windows Forms], displaying images
- PictureBox control [Windows Forms], adding pictures
ms.assetid: 4dc7b973-afb1-4276-8322-20825af96655
ms.openlocfilehash: a05ffe19412fc7a4e3e02f01336d89cce39fac8a
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325599"
---
# <a name="how-to-load-a-picture-using-the-designer-windows-forms"></a>Postupy: Načtení obrázku pomocí Návrháře (Windows Forms)

Pomocí <xref:System.Windows.Forms.PictureBox> ovládacího prvku model Windows Forms můžete načíst a zobrazit obrázek ve formuláři v době návrhu nastavením <xref:System.Windows.Forms.PictureBox.Image%2A> vlastnosti na platný obrázek. V následující tabulce jsou uvedeny přijatelné typy souborů.

|Typ|Přípona názvu souboru|
|---|---|
|Monochromatick|.bmp|
|Ikona|Přípona. ico|
|GIF|.gif|
|Soubory|. WMF|
|JPEG|.jpg|

## <a name="to-display-a-picture-at-design-time"></a>Zobrazení obrázku v době návrhu

1. Nakreslete <xref:System.Windows.Forms.PictureBox> ovládací prvek na formuláři.

2. V okně **vlastnosti** vyberte <xref:System.Windows.Forms.PictureBox.Image%2A> vlastnost a potom kliknutím na tlačítko se třemi tečkami zobrazte dialogové okno **otevřít** .

3. Pokud hledáte určitý typ souboru (například soubory. gif), vyberte ho v poli **soubory typu** .

4. Vyberte soubor, který chcete zobrazit.

## <a name="to-clear-the-picture-at-design-time"></a>Vymazání obrázku v době návrhu

1. V okně **vlastnosti** vyberte <xref:System.Windows.Forms.PictureBox.Image%2A> vlastnost. Klikněte pravým tlačítkem myši na miniaturu malého obrázku, který se zobrazí nalevo od názvu objektu obrázku, a pak zvolte možnost **obnovit**.

## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.PictureBox>
- [PictureBox – přehled ovládacího prvku](picturebox-control-overview-windows-forms.md)
- [Postupy: Změna velikosti či umístění obrázku za běhu](how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms.md)
- [Postupy: Nastavení obrázků za běhu](how-to-set-pictures-at-run-time-windows-forms.md)
- [PictureBox – ovládací prvek](picturebox-control-windows-forms.md)
