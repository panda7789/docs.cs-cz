---
title: Nastavení obrázku zobrazovaného ovládacím prvkem
ms.date: 08/20/2019
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
ms.openlocfilehash: 5df0068c8462bbaab0cb0135de1dd1b91ababe06
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746868"
---
# <a name="how-to-set-the-image-displayed-by-a-windows-forms-control"></a>Postupy: nastavení obrázku zobrazovaného ovládacím prvkem model Windows Forms

Obrázek může zobrazit několik ovládacích prvků model Windows Forms. Tyto obrázky mohou být ikony, které objasňují účel ovládacího prvku, jako je například ikona diskety na tlačítku, které označuje příkaz Save. Alternativně mohou být ikony obrázky na pozadí, aby ovládací prvek poskytoval vzhled a chování, které chcete.

## <a name="programmatic"></a>Blokují

Nastavte vlastnost `Image` nebo `BackgroundImage` ovládacího prvku na objekt typu <xref:System.Drawing.Image>. Obecně se načítá obrázek ze souboru pomocí metody <xref:System.Drawing.Image.FromFile%2A>.

V následujícím příkladu kódu je cesta nastavená pro umístění obrázku složka **obrázky** . Tento adresář zahrnuje Většina počítačů s operačním systémem Windows. To také umožňuje uživatelům s minimálními úrovněmi přístupu k systému bezpečně spustit aplikaci. Následující příklad kódu vyžaduje, abyste již měli formulář s přidaným ovládacím prvkem <xref:System.Windows.Forms.PictureBox>.

```vb
' Replace the image named below with your own icon.
PictureBox1.Image = Image.FromFile _
   (System.Environment.GetFolderPath _
   (System.Environment.SpecialFolder.MyPictures) _
   & "\Image.gif")
```

```csharp
// Replace the image named below with your own icon.
// Note the escape character used (@) when specifying the path.
pictureBox1.Image = Image.FromFile
   (System.Environment.GetFolderPath
   (System.Environment.SpecialFolder.MyPictures)
   + @"\Image.gif");
```

```cpp
// Replace the image named below with your own icon.
pictureBox1->Image = Image::FromFile(String::Concat
   (System::Environment::GetFolderPath
   (System::Environment::SpecialFolder::MyPictures),
   "\\Image.gif"));
```

## <a name="designer"></a>Návrhář

1. V okně **vlastnosti** sady Visual Studio vyberte vlastnost **Image** nebo **BackgroundImage** ovládacího prvku a potom vyberte tlačítko se třemi tečkami (![se třemi tečkami v aplikaci Visual Studio](./media/visual-studio-ellipsis-button.png)), aby se zobrazilo dialogové okno **Vybrat prostředek** .

2. Vyberte obrázek, který chcete zobrazit.

## <a name="see-also"></a>Viz také:

- <xref:System.Drawing.Image.FromFile%2A>
- <xref:System.Drawing.Image>
- <xref:System.Windows.Forms.Control.BackgroundImage%2A>
