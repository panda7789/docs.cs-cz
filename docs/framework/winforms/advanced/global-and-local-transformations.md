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
ms.openlocfilehash: f62efb31e95b0797272997fadbc28459579a0de0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955188"
---
# <a name="global-and-local-transformations"></a>Globální a místní transformace
Globální transformace je transformace, která se vztahuje na všechny položky vykreslené daným <xref:System.Drawing.Graphics> objektem. Naopak lokální transformace je transformace, která se vztahuje na konkrétní položku, která se má vykreslit.  
  
## <a name="global-transformations"></a>Globální transformace  
 Chcete-li vytvořit globální transformaci, <xref:System.Drawing.Graphics> vytvořte objekt a poté proveďte manipulaci s <xref:System.Drawing.Graphics.Transform%2A> jeho vlastností. <xref:System.Drawing.Graphics.Transform%2A> Vlastnost<xref:System.Drawing.Drawing2D.Matrix> je objekt, takže může obsahovat libovolnou sekvenci transformací spřažení. Transformace uložená ve <xref:System.Drawing.Graphics.Transform%2A> vlastnosti se nazývá světová transformace. <xref:System.Drawing.Graphics.RotateTransform%2A> <xref:System.Drawing.Graphics.MultiplyTransform%2A> <xref:System.Drawing.Graphics.TranslateTransform%2A> <xref:System.Drawing.Graphics.ScaleTransform%2A>Třída poskytuje několik metod pro sestavení složené transformace světa:,, a. <xref:System.Drawing.Graphics> Následující příklad kreslí tři tečky dvakrát: jednou před vytvořením Světové transformace a jednou po. Transformace se nejprve škáluje podle faktoru 0,5 ve směru y, pak překládá 50 jednotek ve směru x a pak otočí o 30 stupňů.  
  
 [!code-csharp[System.Drawing.CoordinateSystems#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.CoordinateSystems#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#21)]  
  
 Následující ilustrace znázorňuje matice zahrnuté v transformaci.  
  
 ![Transformations](./media/aboutgdip05-art14.gif "AboutGdip05_art14")  
  
> [!NOTE]
> V předchozím příkladu se elipsa otáčí kolem počátku souřadnicového systému, který je v levém horním rohu klientské oblasti. Výsledkem je jiný výsledek než otočení elipsy o vlastním centru.  
  
## <a name="local-transformations"></a>Místní transformace  
 Místní transformace se vztahuje na konkrétní položku, která se má vykreslit. Například <xref:System.Drawing.Drawing2D.GraphicsPath> objekt<xref:System.Drawing.Drawing2D.GraphicsPath.Transform%2A> má metodu, která umožňuje transformovat datové body této cesty. Následující příklad Kreslí obdélník bez transformace a cestu s transformací otočení. (Předpokládá se, že neexistuje žádná světová transformace.)  
  
 [!code-csharp[System.Drawing.CoordinateSystems#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#22)]
 [!code-vb[System.Drawing.CoordinateSystems#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#22)]  
  
 Můžete zkombinovat transformaci po celém světě s místními transformacemi a dosáhnout tak nejrůznějších výsledků. Můžete například použít transformaci World k revizi systému souřadnic a použít místní transformace k otočení a škálování objektů nakreslených v novém systému souřadnic.  
  
 Předpokládejme, že chcete, aby systém souřadnic, který má svůj původ 200 pixelů od levého okraje oblasti klienta a 150 pixelů od horní části klientské oblasti. Kromě toho Předpokládejme, že chcete, aby jednotka míry byla pixel, přičemž osa x odkazuje na pravou a osu y ukazující nahoru. Výchozí systém souřadnic má osu y ukazující dolů, takže je nutné provést reflexi napříč vodorovnou osou. Následující ilustrace znázorňuje matici takového odrazu.  
  
 ![Transformations](./media/aboutgdip05-art15.gif "AboutGdip05_art15")  
  
 V dalším kroku předpokládáme, že potřebujete provést překlad 200 jednotek na pravé a 150 jednotky.  
  
 Následující příklad vytváří souřadnicový systém, který je právě popsán nastavením Světové transformace <xref:System.Drawing.Graphics> objektu.  
  
 [!code-csharp[System.Drawing.CoordinateSystems#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#23)]
 [!code-vb[System.Drawing.CoordinateSystems#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#23)]  
  
 Následující kód (umístěný na konci předchozího příkladu) vytvoří cestu, která se skládá z jednoho obdélníku s jeho levým dolním rohem na počátku nového systému souřadnic. Obdélník se vyplní jednou bez místní transformace a jednou s lokální transformací. Místní transformace se skládá z horizontálního škálování podle faktoru 2 následovaného otočením o 30 stupňů.  
  
 [!code-csharp[System.Drawing.CoordinateSystems#24](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#24)]
 [!code-vb[System.Drawing.CoordinateSystems#24](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#24)]  
  
 Následující ilustrace znázorňuje nový souřadnicový systém a dva obdélníky.  
  
 ![Transformations](./media/aboutgdip05-art16.gif "AboutGdip05_art16")  
  
## <a name="see-also"></a>Viz také:

- [Systém souřadnic a transformace](coordinate-systems-and-transformations.md)
- [Použití transformací ve spravovaném GDI+](using-transformations-in-managed-gdi.md)
