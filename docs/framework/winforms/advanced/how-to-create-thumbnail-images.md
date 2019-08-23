---
title: 'Postupy: Vytváření miniatur'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- thumbnail images [Windows Forms], creating
- images [Windows Forms], creating thumbnails
ms.assetid: e956242a-1e5b-4217-a3cf-5f3fb45d00ba
ms.openlocfilehash: 786a92d99f5e7a0c27f502efa9a5fe617ac4d4d6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923759"
---
# <a name="how-to-create-thumbnail-images"></a>Postupy: Vytváření miniatur
Obrázek miniatury je malá verze obrázku. Můžete vytvořit miniaturu obrázku voláním <xref:System.Drawing.Image.GetThumbnailImage%2A> metody <xref:System.Drawing.Image> objektu.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří <xref:System.Drawing.Image> objekt ze souboru jpg. Původní obrázek má šířku 640 pixelů a výšku 479 pixelů. Kód Vytvoří miniaturu obrázku s šířkou 100 pixelů a výškou 100 pixelů.  
  
 Miniatura obrázku je znázorněna na následujícím obrázku:  
  
 ![Snímek obrazovky zobrazující výstupní miniaturu](./media/how-to-create-thumbnail-images/construct-thumbnail-image.png)  
  
> [!NOTE]
> V tomto příkladu je metoda zpětného volání deklarovaná, ale nikdy se nepoužívá. Tato podpora podporuje všechny verze rozhraní GDI+.  
  
 [!code-csharp[System.Drawing.WorkingWithImages#71](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#71)]
 [!code-vb[System.Drawing.WorkingWithImages#71](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#71)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Předchozí příklad je navržen pro použití s model Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což <xref:System.Windows.Forms.Control.Paint> je parametr obslužné rutiny události. Chcete-li spustit příklad, postupujte podle následujících kroků:  
  
1. Vytvořte novou model Windows Forms aplikaci.  
  
2. Přidejte vzorový kód do formuláře.  
  
3. Vytvoření obslužné rutiny pro <xref:System.Windows.Forms.Control.Paint> událost formuláře  
  
4. V obslužné rutině volejte metodu `GetThumbnail` a předejte `e` <xref:System.Windows.Forms.PaintEventArgs>ji. <xref:System.Windows.Forms.Control.Paint>  
  
5. Vyhledejte soubor obrázku, který chcete vytvořit jako miniaturu.  
  
6. `GetThumbnail` V metodě zadejte cestu a název souboru k imagi.  
  
7. Stisknutím klávesy F5 spusťte příklad.  
  
     Ve formuláři se zobrazí obrázek miniatury 100 až 100.  
  
## <a name="see-also"></a>Viz také:

- [Obrázky, rastrové obrázky a metasoubory](images-bitmaps-and-metafiles.md)
- [Práce s obrázky, rastrovými obrázky, ikonami a metasoubory](working-with-images-bitmaps-icons-and-metafiles.md)
