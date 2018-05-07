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
ms.openlocfilehash: e1c46f805b7ba2e2f2a1eb52042cc2ca08e63e03
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-improve-performance-by-avoiding-automatic-scaling"></a>Postupy: Zvýšení výkonu zabráněním automatické změně měřítka
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] může automaticky škálovat bitovou kopii, při kreslení, které by snížení výkonu. Alternativně můžete řídit škálování bitovou kopii pomocí předání dimenze cílové obdélníku, které <xref:System.Drawing.Graphics.DrawImage%2A> metoda.  
  
 Například následující volání do <xref:System.Drawing.Graphics.DrawImage%2A> metoda určuje levého horního rohu (50, 30), ale neurčuje obdélníku cílový.  
  
 [!code-csharp[System.Drawing.WorkingWithImages#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.WorkingWithImages#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#31)]  
  
 I když je to nejjednodušší verze <xref:System.Drawing.Graphics.DrawImage%2A> metoda z hlediska počtu povinnými argumenty, není nutně nejúčinnější. Pokud řešení používá [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] (obvykle 96 bodů na palec) se liší od řešení uložené v <xref:System.Drawing.Image> objekt, pak se <xref:System.Drawing.Graphics.DrawImage%2A> metoda bude změna měřítka obrázku. Předpokládejme například, že <xref:System.Drawing.Image> objekt má šířka 216 pixelů a hodnota uložené horizontální rozlišení 72 bodů na palec. Protože 216/72 je 3, <xref:System.Drawing.Graphics.DrawImage%2A> bude změna měřítka obrázku tak, aby měl šířku 3 palce s rozlišením 96 dpi. To znamená <xref:System.Drawing.Graphics.DrawImage%2A> zobrazí obrázek, který obsahuje šířku 96 x 3 = 288 pixelů.  
  
 I když se liší od 96 bodů na palec, rozlišení obrazovky [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] bude pravděpodobně škálování bitovou kopii jako kdyby k rozlišení 96 dpi. Je to způsobeno [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <xref:System.Drawing.Graphics> objekt je přidružený ke kontextu zařízení a kdy [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] dotazy kontext zařízení pro rozlišení obrazovky, výsledek je obvykle 96, bez ohledu na skutečné rozlišení. Automatické škálování zadáním cílového obdélníku v se můžete vyhnout <xref:System.Drawing.Graphics.DrawImage%2A> metoda.  
  
## <a name="example"></a>Příklad  
 Následující příklad nevykresluje stejnou bitovou kopii dvakrát. V prvním případě nejsou zadané šířky a výšky obdélníku cílové a bitovou kopii je automaticky škálovat. V druhém případě šířka a výška (měřeno v pixelech) rámeček cílové zadat být stejné jako šířka a výška původní bitové kopie. Následující obrázek znázorňuje obrázek se vykresluje dvakrát.  
  
 ![Škálovat Texture](../../../../docs/framework/winforms/advanced/media/csscaledtexture1.png "csscaledtexture1")  
  
 [!code-csharp[System.Drawing.WorkingWithImages#32](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.WorkingWithImages#32](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#32)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 V předchozím příkladu je určen k použití s modelem Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události. Nahraďte Texture.jpg s název bitové kopie a cestu, která jsou platné ve vašem systému.  
  
## <a name="see-also"></a>Viz také  
 [Obrázky, rastrové obrázky a metasoubory](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [Práce s obrázky, rastrovými obrázky, ikonami a metasoubory](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
