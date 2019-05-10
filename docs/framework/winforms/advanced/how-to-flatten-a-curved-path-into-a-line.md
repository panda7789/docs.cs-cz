---
title: 'Postupy: Narovnání zakřivené cesty na čáru'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms], flattening curves into lines
- curves [Windows Forms], flattening
- GraphicsPath object
- paths [Windows Forms], flattening
- drawing [Windows Forms], flattening curves
ms.assetid: e654b8de-25f4-4735-9208-42e4514a589c
ms.openlocfilehash: d59a802618ddd5080c651e822ed4c09641f7f170
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64645370"
---
# <a name="how-to-flatten-a-curved-path-into-a-line"></a>Postupy: Narovnání zakřivené cesty na čáru
A <xref:System.Drawing.Drawing2D.GraphicsPath> ukládá posloupnost řádky a Bézierovy křivky. Několik typů křivky (symbol tří teček, elipsy, základní křivky vyhlazení) můžete přidat do cesty, ale každý křivka je převést na Bézierovy křivky před jejich uložením v cestě. Sloučení cesta se skládá z převodu jednotlivých Bézierovy křivky v cestě na řadu rovné čáry. Následující obrázek zobrazuje cestu, před a po sloučení.  
  
 ![Přímých čar a křivek](./media/aboutgdip02-art32a.gif "AboutGdip02_Art32A")  
  
### <a name="to-flatten-a-path"></a>Chcete-li narovnání cesty  
  
- volání <xref:System.Drawing.Drawing2D.GraphicsPath.Flatten%2A> metodu <xref:System.Drawing.Drawing2D.GraphicsPath> objektu. <xref:System.Drawing.Drawing2D.GraphicsPath.Flatten%2A> Metoda obdrží plochosti argument, který určuje maximální vzdálenost mezi plochá cestu a původní cestu.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Drawing.Drawing2D.GraphicsPath?displayProperty=nameWithType>
- [Čáry, křivky a obrazce](lines-curves-and-shapes.md)
- [Sestavování a kreslení cest](constructing-and-drawing-paths.md)
