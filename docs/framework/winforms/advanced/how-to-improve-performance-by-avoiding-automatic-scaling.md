---
title: 'Postupy: Zvýšení výkonu zabráněním automatické změně měřítka'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- automatic scaling
- images [Windows Forms], improving performance
- images [Windows Forms], using without automatic scaling
- performance [Windows Forms], improving image
ms.assetid: 5fe2c95d-8653-4d55-bf0d-e5afa28f223b
ms.openlocfilehash: dd1a1545dce33de1ce11938db8495ebf311dadda
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2019
ms.locfileid: "67506201"
---
# <a name="how-to-improve-performance-by-avoiding-automatic-scaling"></a>Postupy: Zvýšení výkonu zabráněním automatické změně měřítka
Rozhraní GDI + může automaticky škálovat bitovou kopii při kreslení, které by snížení výkonu. Alternativně můžete řídit škálování image předáním rozměry cílového obdélníku do <xref:System.Drawing.Graphics.DrawImage%2A> metody.  
  
 Například následující volání <xref:System.Drawing.Graphics.DrawImage%2A> metody určuje levého horního rohu (50, 30), ale neurčuje cílového obdélníku.  
  
 [!code-csharp[System.Drawing.WorkingWithImages#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.WorkingWithImages#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#31)]  
  
 I když je to nejjednodušší verzi <xref:System.Drawing.Graphics.DrawImage%2A> metoda z hlediska počtu povinné argumenty, není nutně nejefektivnější. Pokud řešení používá rozhraní GDI + (obvykle 96 dpi) se liší od řešení uložené v <xref:System.Drawing.Image> objektu, pak bude <xref:System.Drawing.Graphics.DrawImage%2A> metoda bude změna měřítka obrázku. Předpokládejme například, že <xref:System.Drawing.Image> objekt má šířku 216 pixelů a hodnotou uloženou horizontální rozlišení 72 bodů na palec. Protože 216/72 je 3, <xref:System.Drawing.Graphics.DrawImage%2A> bude změna měřítka obrázku tak, aby byly šířku 3 palcích při 96 dpi rozlišení. To znamená <xref:System.Drawing.Graphics.DrawImage%2A> zobrazí bitovou kopii, která má šířku 96 x 3 = 288 pixelů.  
  
 I v případě, že vaši rozlišení obrazovky se liší od 96 dpi, rozhraní GDI + bude pravděpodobně změna měřítka obrázku jako kdyby byly 96 dpi rozlišení obrazovky. Důvodem je, že rozhraní GDI + <xref:System.Drawing.Graphics> objekt je přidružený kontext zařízení, a když rozhraní GDI + dotazuje kontext zařízení pro rozlišení obrazovky, výsledek je obvykle 96, bez ohledu na skutečné rozlišení. Zadáním cílového obdélníku v automatické škálování se můžete vyhnout <xref:System.Drawing.Graphics.DrawImage%2A> metody.  
  
## <a name="example"></a>Příklad  
 Následující příklad kreslení stejnou bitovou kopii dvakrát. V prvním případě nejsou zadané šířku a výšku cílového obdélníku a image se automaticky škálovat. V druhém případě šířky a výšky (měřeno v pixelech) cílového obdélníku zadávají být stejný jako šířku a výšku původní bitové kopie. Následující obrázek znázorňuje obrázku vykresleného dvakrát:  
  
 ![Snímek obrazovky zobrazující Image s horizontálním textury.](./media/how-to-improve-performance-by-avoiding-automatic-scaling/two-scaled-texture-images.png)  
  
 [!code-csharp[System.Drawing.WorkingWithImages#32](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.WorkingWithImages#32](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#32)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 V předchozím příkladu je určený k použití pomocí Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události. Nahraďte Texture.jpg název image a cestu, která jsou platné ve vašem systému.  
  
## <a name="see-also"></a>Viz také:

- [Obrázky, rastrové obrázky a metasoubory](images-bitmaps-and-metafiles.md)
- [Práce s obrázky, rastrovými obrázky, ikonami a metasoubory](working-with-images-bitmaps-icons-and-metafiles.md)
