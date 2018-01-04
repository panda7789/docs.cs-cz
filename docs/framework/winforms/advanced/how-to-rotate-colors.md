---
title: "Postupy: Otáčení barev"
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
- colors [Windows Forms], rotating
- examples [Windows Forms], rotating colors
ms.assetid: e2e4c300-159c-4f4a-9b56-103b0f7cbc05
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 81b022011bd5613b8e956aa83482d2836508a4f1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-rotate-colors"></a>Postupy: Otáčení barev
Otočení v four-dimensional barevný prostor je obtížné vizualizace. Jsme můžete usnadňují vizualizaci otočení souhlasit a jedna z komponent Barva pevné zachovat. Předpokládejme, že jsme souhlas s zachovat komponentu alfa pevné na 1 (plně neprůhledný). Potom jsme vizualizovat trojrozměrné barevný prostor s červenou, zelené a modré osy, jak je znázorněno na následujícím obrázku.  
  
 ![Přebarvení](../../../../docs/framework/winforms/advanced/media/recoloring03.gif "recoloring03")  
  
 Barvu, která lze považovat za bod v 3D prostoru. Například bodu (1, 0, 0) v prostoru představuje červenou barvu a bodem (0, 1, 0) v prostoru představuje zelenou barvu.  
  
 Následující obrázek znázorňuje, co znamená otočit barvu (1, 0, 0) prostřednictvím úhel 60 stupňů v rovině Red zeleně. Otočení paralelně roviny rovinou Red zelená lze považovat za otočení blue osy.  
  
 ![Přebarvení](../../../../docs/framework/winforms/advanced/media/recoloring04.gif "recoloring04")  
  
 Následující obrázek ukazuje, jak k chybě při inicializaci matice barev k provedení otočení o jednotlivých tři souřadnice osy (červená, zelená, modrá).  
  
 ![Přebarvení](../../../../docs/framework/winforms/advanced/media/recoloring05.gif "recoloring05")  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu má obrázek, který je všechny jedné barvy (1, 0, 0,6) a použije rotaci 60 stupeň blue osy. Úhel otočení je, jež se v rovině rovnoběžné roviny red zeleně.  
  
 Následující obrázek znázorňuje původní bitové kopie na levé straně a obrázek otočen barva na pravé straně.  
  
 ![Otáčení barev](../../../../docs/framework/winforms/advanced/media/colortrans5.png "colortrans5")  
  
 Následující obrázek znázorňuje vizualizaci otočení barev provést v následujícím kódu.  
  
 ![Přebarvení](../../../../docs/framework/winforms/advanced/media/recoloring06.gif "recoloring06")  
  
 [!code-csharp[System.Drawing.RotateColors#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RotateColors/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.RotateColors#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RotateColors/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 V předchozím příkladu je určen k použití s modelem Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události. Nahraďte `RotationInput.bmp` s název souboru obrázku a cesta platné ve vašem systému.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Drawing.Imaging.ColorMatrix>  
 <xref:System.Drawing.Imaging.ImageAttributes>  
 [Grafika a kreslení v modelu Windows Forms](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [Přebarvení obrázků](../../../../docs/framework/winforms/advanced/recoloring-images.md)
