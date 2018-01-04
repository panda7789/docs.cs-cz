---
title: "Postupy: Narovnání zakřivené cesty na čáru"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- graphics [Windows Forms], flattening curves into lines
- curves [Windows Forms], flattening
- GraphicsPath object
- paths [Windows Forms], flattening
- drawing [Windows Forms], flattening curves
ms.assetid: e654b8de-25f4-4735-9208-42e4514a589c
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 334fc0fee7166f8f8c5c1db61d3b9e370da72f87
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-flatten-a-curved-path-into-a-line"></a>Postupy: Narovnání zakřivené cesty na čáru
A <xref:System.Drawing.Drawing2D.GraphicsPath> objekt ukládá posloupnost čar a Bézierovy křivky. Můžete přidat několik typů křivek (tři tečky, oblouky, základní křivky vyhlazení) na cestu, ale každý křivky jsou převedeny na Bézierovy křivky předtím, než je uložen v cestě. Vyrovnání cestu se skládá převodu každý Bézierovy křivky v cestě k posloupnost úseček. Následující obrázek znázorňuje cestu před a po shrnutí.  
  
 ![Přímých čar a křivek](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art32a.gif "AboutGdip02_Art32A")  
  
### <a name="to-flatten-a-path"></a>Chcete-li narovnání cesty  
  
-   volání <xref:System.Drawing.Drawing2D.GraphicsPath.Flatten%2A> metodu <xref:System.Drawing.Drawing2D.GraphicsPath> objektu. <xref:System.Drawing.Drawing2D.GraphicsPath.Flatten%2A> Metoda přijímá plochosti argument, který určuje maximální vzdálenost mezi plochou cestu a původní cestu.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Drawing.Drawing2D.GraphicsPath?displayProperty=nameWithType>  
 [Čáry, křivky a obrazce](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [Sestavování a kreslení cest](../../../../docs/framework/winforms/advanced/constructing-and-drawing-paths.md)
