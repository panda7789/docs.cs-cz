---
title: Použití transformací pro škálování barev
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- transformations [Windows Forms], for scaling colors
- colors [Windows Forms], scaling
ms.assetid: df23c887-7fd6-4b15-ad94-e30b5bd4b849
ms.openlocfilehash: 9c8f2392137d04f56096120cec64b60c42c47419
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59107977"
---
# <a name="using-transformations-to-scale-colors"></a>Použití transformací pro škálování barev
Transformace měřítka vynásobí jeden nebo více součástí čtyři barvy podle čísla. V následující tabulce jsou uvedeny položek matice barev, které představují škálování.  
  
|Komponenta škálování|Přehled vstupu|  
|----------------------------|------------------|  
|Červená|[0][0]|  
|Zelená|[1][1]|  
|Modrá|[2][2]|  
|Alpha|[3][3]|  
  
## <a name="scaling-one-color"></a>Škálování jedné barvy  
 Následující příklad vytvoří <xref:System.Drawing.Image> objekt ze souboru ColorBars2.bmp. Kód pak škáluje faktorem 2 modré každý pixel na obrázku. Původní bitové kopie nakreslen spolu s transformovaný bitové kopie.  
  
 [!code-csharp[System.Drawing.RecoloringImages#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.RecoloringImages#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#41)]  
  
 Následující obrázek znázorňuje původní obrázek na levé straně a obrazu se změněnou velikostí na pravé straně:  
  
 ![Snímek obrazovky, který porovnává barvy původní a měřítkem.](./media/using-transformations-to-scale-colors/four-bar-scale-one-color.png)  
  
 Následující tabulka uvádí vektory barvu pro čtyři pruhy před a po modré škálování. Všimněte si, že hodnota modré ve čtvrtém pruhu barev absolvovanou z 0,8 0.6. Důvodem je, že [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] zachová pouze desetinná část výsledku. Například (2)(0.8) = 1.6, a zlomkovou část 1.6 je 0.6. Ponechá pouze zlomkové části zajistí, že výsledek je vždy v intervalu [0, 1].  
  
|Původní|Škálovat|  
|--------------|------------|  
|(0.4, 0.4, 0.4, 1)|(0.4, 0.4, 0.8, 1)|  
|(0.4, 0.2, 0.2, 1)|(0.4, 0.2, 0.4, 1)|  
|(0.2, 0.4, 0.2, 1)|(0.2, 0.4, 0.4, 1)|  
|(0.4, 0.4, 0.8, 1)|(0.4, 0.4, 0.6, 1)|  
  
## <a name="scaling-multiple-colors"></a>Škálování několika barev  
 Následující příklad vytvoří <xref:System.Drawing.Image> objekt ze souboru ColorBars2.bmp. Potom kód škáluje komponenty červené, zelené a modré každý pixel na obrázku. Červené komponenty jsou kapacitu vertikálně snížit 25 procent, zelenou komponenty jsou kapacitu vertikálně snížit 35 procent a modré komponenty jsou kapacitu vertikálně snížit 50 procent.  
  
 [!code-csharp[System.Drawing.RecoloringImages#42](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#42)]
 [!code-vb[System.Drawing.RecoloringImages#42](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#42)]  
  
 Následující obrázek znázorňuje původní obrázek na levé straně a obrazu se změněnou velikostí na pravé straně:  
  
 ![Snímek obrazovky, který porovnává barvy původní a měřítkem.](./media/using-transformations-to-scale-colors/four-bar-scale-multiple-colors.png)  
  
 Následující tabulka uvádí vektory barvu pro čtyři pruhy před a po červené, zelené a modré škálování.  
  
|Původní|Škálovat|  
|--------------|------------|  
|(0.6, 0.6, 0.6, 1)|(0.45, 0.39, 0.3, 1)|  
|(0, 1, 1, 1)|(0, 0.65, 0.5, 1)|  
|(1, 1, 0, 1)|(0.75, 0.65, 0, 1)|  
|(1, 0, 1, 1)|(0.75, 0, 0.5, 1)|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Drawing.Imaging.ColorMatrix>
- <xref:System.Drawing.Imaging.ImageAttributes>
- [Grafika a kreslení v rozhraní Windows Forms](graphics-and-drawing-in-windows-forms.md)
- [Přebarvení obrázků](recoloring-images.md)
