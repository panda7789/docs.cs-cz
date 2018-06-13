---
title: 'Postupy: Vytváření miniatur obrázků'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- thumbnail images [Windows Forms], creating
- images [Windows Forms], creating thumbnails
ms.assetid: e956242a-1e5b-4217-a3cf-5f3fb45d00ba
ms.openlocfilehash: 870ea223698e48438bd4dd08597d0a6ab79cec27
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33521482"
---
# <a name="how-to-create-thumbnail-images"></a>Postupy: Vytváření miniatur obrázků
Miniatury je malá verze bitové kopie. Miniatury můžete vytvořit voláním <xref:System.Drawing.Image.GetThumbnailImage%2A> metodu <xref:System.Drawing.Image> objektu.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří <xref:System.Drawing.Image> objekt ze souboru JPG. Původní bitové kopie má 640 pixelů šířka a výška 479 pixelů. Kód vytvoří miniaturu, který má 100 pixelů šířka a výška 100 pixelů.  
  
 Následující obrázek ukazuje na miniaturu.  
  
 ![Miniaturu](../../../../docs/framework/winforms/advanced/media/thumbnail1.png "Thumbnail1")  
  
> [!NOTE]
>  V tomto příkladu je metoda zpětného volání deklarovat, ale nikdy použity. To podporuje všechny verze rozhraní GDI +.  
  
 [!code-csharp[System.Drawing.WorkingWithImages#71](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#71)]
 [!code-vb[System.Drawing.WorkingWithImages#71](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#71)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 V předchozím příkladu je určen k použití s modelem Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události. Pokud chcete spustit v příkladu, postupujte takto:  
  
1.  Vytvořte novou aplikaci Windows Forms.  
  
2.  Přidejte ukázkový kód pro formulář.  
  
3.  Vytvořte obslužnou rutinu pro daný formulář <xref:System.Windows.Forms.Control.Paint> událostí  
  
4.  V <xref:System.Windows.Forms.Control.Paint> obslužná rutina, volání `GetThumbnail` metoda a předejte jí `e` pro <xref:System.Windows.Forms.PaintEventArgs>.  
  
5.  Najít soubor obrázku, který má být miniaturu.  
  
6.  V `GetThumbnail` metoda, zadejte cestu a název do bitové kopie souboru.  
  
7.  Stisknutím klávesy F5 spusťte v příkladu.  
  
     100 podle 100 miniaturu se zobrazí na formuláři.  
  
## <a name="see-also"></a>Viz také  
 [Obrázky, rastrové obrázky a metasoubory](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [Práce s obrázky, rastrovými obrázky, ikonami a metasoubory](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
