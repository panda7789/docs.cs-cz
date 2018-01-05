---
title: "Postupy: Řízení alfa míchání pomocí režimu skládání"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- alpha blending [Windows Forms], compositing
- colors [Windows Forms], blending
- colors [Windows Forms], controlling transparency
ms.assetid: f331df2d-b395-4b0a-95be-24fec8c9bbb5
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 40461ddb3fdae8076df5290afe669a8eca9f6a8d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-compositing-mode-to-control-alpha-blending"></a>Postupy: Řízení alfa míchání pomocí režimu skládání
Mohou nastat situace, kdy budete chtít vytvořit mimo obrazovku rastrový obrázek, který má následující vlastnosti:  
  
-   Barvy mají alfanumerické hodnoty, které jsou menší než 255.  
  
-   Barvy nejsou alfa smíšení mezi sebou, jako je vytváření bitové mapy.  
  
-   Při zobrazení dokončení rastrového obrázku jsou barvy v souboru bitové mapy s barvy pozadí v zobrazení zařízení smíšení alfa.  
  
 K vytvoření takové rastrového obrázku, vytvořit prázdnou <xref:System.Drawing.Bitmap> objektu a pak vytvořit <xref:System.Drawing.Graphics> objektu podle této bitové mapy. Nastavení režimu skládání <xref:System.Drawing.Graphics> do objektu <xref:System.Drawing.Drawing2D.CompositingMode.SourceCopy?displayProperty=nameWithType>.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří <xref:System.Drawing.Graphics> na základě objektu <xref:System.Drawing.Bitmap> objektu. Kód používá <xref:System.Drawing.Graphics> objekt spolu se dvěma poloprůhledných štětců (alpha = 160) pro malování bitové mapy. Kód doplní red elipsy a zelené elipsy pomocí poloprůhledných štětců. Zelené elipsy překrývá red elipsy, ale není zeleným smíšení s červeným, protože režimu skládání <xref:System.Drawing.Graphics> objektu na hodnotu <xref:System.Drawing.Drawing2D.CompositingMode.SourceCopy>.  
  
 Kód nevykresluje bitmapy na obrazovce dvakrát: jednou na bílé pozadí a jednou na barevné pozadí. Pixelů v souboru bitové mapy, které jsou součástí na dva výpustky mají alfa součást 160, takže na symbol tří teček jsou smíšené s barvy pozadí na obrazovce.  
  
 Následující obrázek znázorňuje příklad kódu výstup. Všimněte si, že jsou na symbol tří teček smíšený s na pozadí, ale nejsou smíšení mezi sebou.  
  
 ![Zdroj kopírování](../../../../docs/framework/winforms/advanced/media/sourcecopy.png "sourcecopy")  
  
 Příklad kódu obsahuje tento příkaz:  
  
 [!code-csharp[System.Drawing.AlphaBlending#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.AlphaBlending#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#41)]  
  
 Pokud chcete na symbol tří teček, chcete-li být smíšení mezi sebou můžou mít na pozadí, změňte na následující tento příkaz:  
  
 [!code-csharp[System.Drawing.AlphaBlending#42](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#42)]
 [!code-vb[System.Drawing.AlphaBlending#42](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#42)]  
  
 Následující obrázek znázorňuje výstup revidovaný kód.  
  
 ![Zdroj přes](../../../../docs/framework/winforms/advanced/media/sourceover.png "sourceover")  
  
 [!code-csharp[System.Drawing.AlphaBlending#43](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#43)]
 [!code-vb[System.Drawing.AlphaBlending#43](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#43)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 V předchozím příkladu je určen k použití s modelem Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Drawing.Color.FromArgb%2A>  
 [Alfa míchání čar a výplní](../../../../docs/framework/winforms/advanced/alpha-blending-lines-and-fills.md)
