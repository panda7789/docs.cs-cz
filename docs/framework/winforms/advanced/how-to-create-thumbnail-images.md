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
ms.openlocfilehash: 79b6258e7e6d7f16cc7a1e32a0c99dfe0eaeaa0c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59144011"
---
# <a name="how-to-create-thumbnail-images"></a>Postupy: Vytváření miniatur
Obrázek miniatury je malá verze Image. Obrázek miniatury můžete vytvořit pomocí volání <xref:System.Drawing.Image.GetThumbnailImage%2A> metodu <xref:System.Drawing.Image> objektu.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří <xref:System.Drawing.Image> objekt ze souboru JPG. Původní bitové kopie je 640 pixelů šířku a výšku 479 pixelů. Kód vytvoří miniaturu, která má šířku 100 pixelů a výška 100 pixelů.  
  
 Následující obrázek znázorňuje obrázek miniatury.  
  
 ![Obrázek miniatury](./media/thumbnail1.png "Thumbnail1")  
  
> [!NOTE]
>  V tomto příkladu je metoda zpětného volání deklarovány, ale nikdy použít. Tento atribut podporuje všechny verze rozhraní GDI +.  
  
 [!code-csharp[System.Drawing.WorkingWithImages#71](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#71)]
 [!code-vb[System.Drawing.WorkingWithImages#71](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#71)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 V předchozím příkladu je určený k použití pomocí Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události. Chcete-li spustit příklad, postupujte podle těchto kroků:  
  
1.  Vytvoření nové aplikace Windows Forms.  
  
2.  Přidejte ukázkový kód do formuláře.  
  
3.  Vytvořte obslužnou rutinu pro daný formulář <xref:System.Windows.Forms.Control.Paint> událostí  
  
4.  V <xref:System.Windows.Forms.Control.Paint> obslužné rutiny, volání `GetThumbnail` a předáte `e` pro <xref:System.Windows.Forms.PaintEventArgs>.  
  
5.  Najdete soubor obrázku, který chcete vytvořit miniatury.  
  
6.  V `GetThumbnail` metoda, zadejte cestu a název do bitové kopie souboru.  
  
7.  Stiskněte klávesu F5 ke spuštění v příkladu.  
  
     Ve formuláři se zobrazí obrázek miniatury 100 x 100.  
  
## <a name="see-also"></a>Viz také:

- [Obrázky, rastrové obrázky a metasoubory](images-bitmaps-and-metafiles.md)
- [Práce s obrázky, rastrovými obrázky, ikonami a metasoubory](working-with-images-bitmaps-icons-and-metafiles.md)
