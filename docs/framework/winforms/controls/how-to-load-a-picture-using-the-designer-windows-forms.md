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
ms.openlocfilehash: 1d95d5baafa42c7dea40933ba837b684d90b7b2b
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972376"
---
# <a name="how-to-load-a-picture-using-the-designer-windows-forms"></a>Postupy: Načtení obrázku pomocí návrháře (model Windows Forms)

Pomocí ovládacího prvku <xref:System.Windows.Forms.PictureBox> model Windows Forms můžete načíst a zobrazit obrázek ve formuláři v době návrhu <xref:System.Windows.Forms.PictureBox.Image%2A> nastavením vlastnosti na platný obrázek. V následující tabulce jsou uvedeny přijatelné typy souborů.

|type|Přípona názvu souboru|
|----------|-------------------------|
|Monochromatick|. bmp|
|Ikona|.ico|
|GIF|. gif|
|Soubory|.wmf|
|JPEG|.jpg|

> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [Přizpůsobení integrovaného vývojového prostředí (IDE) sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).

## <a name="to-display-a-picture-at-design-time"></a>Zobrazení obrázku v době návrhu

1. Nakreslete <xref:System.Windows.Forms.PictureBox> ovládací prvek na formuláři.

2. V okno Vlastnosti vyberte <xref:System.Windows.Forms.PictureBox.Image%2A> vlastnost a potom klikněte na tlačítko se třemi tečkami. zobrazí se dialogové okno **otevřít** .

3. Pokud hledáte určitý typ souboru (například soubory. gif), vyberte ho v poli **soubory typu** .

4. Vyberte soubor, který chcete zobrazit.

## <a name="to-clear-the-picture-at-design-time"></a>Vymazání obrázku v době návrhu

1. V okně **vlastnosti** vyberte <xref:System.Windows.Forms.PictureBox.Image%2A> vlastnost a klikněte pravým tlačítkem myši na miniaturu malého obrázku, který se zobrazí nalevo od názvu objektu obrázku. Vyberte možnost **obnovit**.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.PictureBox>
- [Přehled ovládacího prvku PictureBox](picturebox-control-overview-windows-forms.md)
- [Postupy: Změna velikosti nebo umístění obrázku v době běhu](how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms.md)
- [Postupy: Nastavit obrázky v době běhu](how-to-set-pictures-at-run-time-windows-forms.md)
- [Ovládací prvek PictureBox](picturebox-control-windows-forms.md)
