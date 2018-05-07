---
title: Globální a místní transformace
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- matrices [Windows Forms], using transformations
- transformations [Windows Forms], global
- transformations [Windows Forms], local
ms.assetid: b601d66d-d572-4f11-9d2e-92f0dc8893f3
ms.openlocfilehash: a5a8201f0adb44347bdd42081e0263176d179321
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="global-and-local-transformations"></a>Globální a místní transformace
Globální transformaci je transformaci, která platí pro každou položku vykreslovány pomocí danou <xref:System.Drawing.Graphics> objektu. Místní transformace spočívá v tom, transformaci, která platí pro konkrétní položky, které se mají vykreslovat.  
  
## <a name="global-transformations"></a>Globální transformace  
 Pokud chcete vytvořit globální transformace, vytvořit <xref:System.Drawing.Graphics> objektu a poté pracovat s jeho <xref:System.Drawing.Graphics.Transform%2A> vlastnost. <xref:System.Drawing.Graphics.Transform%2A> Vlastnost je <xref:System.Drawing.Drawing2D.Matrix> objektu, takže může uchovávat žádné pořadí afinní transformace. Transformace uložené v <xref:System.Drawing.Graphics.Transform%2A> vlastnost nazývá Světové transformace. <xref:System.Drawing.Graphics> Třída poskytuje několik metod pro vytváření kompozitních Světové transformace: <xref:System.Drawing.Graphics.MultiplyTransform%2A>, <xref:System.Drawing.Graphics.RotateTransform%2A>, <xref:System.Drawing.Graphics.ScaleTransform%2A>, a <xref:System.Drawing.Graphics.TranslateTransform%2A>. Následující příklad nevykresluje elipsy dvakrát: jednou před vytvořením Světové transformace a jednou po. Transformace nejprve škáluje faktorem 0,5 ve směru osy y, pak překládá 50 jednotky ve směru osy x a pak otočí 30 stupňů.  
  
 [!code-csharp[System.Drawing.CoordinateSystems#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.CoordinateSystems#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#21)]  
  
 Následující obrázek znázorňuje matic zahrnutých v transformaci.  
  
 ![Transformace](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art14.gif "AboutGdip05_art14")  
  
> [!NOTE]
>  V předchozím příkladu se třemi tečkami otočen o původu souřadnicový systém, který je v levém horním rohu klientské oblasti. To vytváří jiné výsledky než otáčení se třemi tečkami o vlastní center.  
  
## <a name="local-transformations"></a>Místní transformace  
 Místní transformace platí pro konkrétní položky, které se mají vykreslovat. Například <xref:System.Drawing.Drawing2D.GraphicsPath> objekt má <xref:System.Drawing.Drawing2D.GraphicsPath.Transform%2A> metoda, která umožňuje transformovat datových bodů dané cesty. Následující příklad nevykresluje obdélník se žádná transformace a cestu otočení transformace. (Předpokládá, že neexistuje žádná Světové transformace malá a velká písmena.)  
  
 [!code-csharp[System.Drawing.CoordinateSystems#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#22)]
 [!code-vb[System.Drawing.CoordinateSystems#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#22)]  
  
 Světové transformace s místní transformace k dosažení různých výsledků můžete kombinovat. Například můžete Světové transformace revidování souřadnicový systém a místní transformace použít otočit a škálovat objekty vykreslovat na nový systém souřadnic.  
  
 Předpokládejme, že chcete souřadnicový systém, který má jeho počátek 200 pixelů od levého okraje klientské oblasti a 150 pixelů z horní části oblasti klienta. Kromě toho předpokládá, že chcete jednotku, která se pixelů, s osou x tvořenou hodnotami odkazující na ose y míří nahoru a doprava. Výchozí souřadnicový systém má osy y míří dolů, takže budete muset provádět odraz na vodorovné ose. Následující obrázek znázorňuje matice takové reflexe.  
  
 ![Transformace](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art15.gif "AboutGdip05_art15")  
  
 V dalším kroku předpokládá, že je třeba provést 200 jednotky překladu napravo a 150 jednotky dolů.  
  
 Následující příklad určuje souřadnicový systém právě popsaného nastavení Světové transformace <xref:System.Drawing.Graphics> objektu.  
  
 [!code-csharp[System.Drawing.CoordinateSystems#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#23)]
 [!code-vb[System.Drawing.CoordinateSystems#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#23)]  
  
 Následující kód (umístit na konci v předchozím příkladu) vytvoří cestu, která se skládá z jedné obdélníku s jeho levém dolním rohu na počátku nové souřadnicový systém. Rámeček je vyplněna jednou se žádná místní transformace a jednou s místní transformace. Místní transformace se skládá z vodorovné škálování faktorem 2 následuje rotaci 30 stupňů.  
  
 [!code-csharp[System.Drawing.CoordinateSystems#24](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#24)]
 [!code-vb[System.Drawing.CoordinateSystems#24](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#24)]  
  
 Následující obrázek znázorňuje nový systém souřadnic a dva obdélníky.  
  
 ![Transformace](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art16.gif "AboutGdip05_art16")  
  
## <a name="see-also"></a>Viz také  
 [Systém souřadnic a transformace](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md)  
 [Použití transformací ve spravovaném GDI+](../../../../docs/framework/winforms/advanced/using-transformations-in-managed-gdi.md)
