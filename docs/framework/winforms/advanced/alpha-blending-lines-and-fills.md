---
title: "Alfa míchání čar a výplní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- lines [Windows Forms], adding transparency
- examples [Windows Forms], alpha blending
- alpha blending [Windows Forms], using with lines
- alpha blending
- lines [Windows Forms], alpha blending
- fills [Windows Forms], alpha blending
- alpha blending [Windows Forms], using with fills
- shapes [Windows Forms], adding transparency
ms.assetid: 5440f48c-3ac9-44c3-b170-c1c110bdbab8
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5b3c0ee3ec82d4d8447c43b7dc9b275591ebe890
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="alpha-blending-lines-and-fills"></a>Alfa míchání čar a výplní
V [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], barvu, která je hodnotu 32-bit s 8 bitů každý pro platformu alpha, červená, zelená a modrá. Určuje hodnotu alfa průhlednost barvy – v rozsahu, ke kterému je barvu smíšení barvou pozadí. Hodnoty alfa rozsahu od 0 do 255, kde 0 představuje plně průhlednou barvu, a 255 představuje plně neprůhledné barvy.  
  
 Prolnutí alfa je x pixelů míchání dat barva zdroje a pozadí. Všechny tři komponenty (červená, zelená, modrá) zadaná zdrojová barvu, která je smíšený s odpovídající součást barvu pozadí podle následujícího vzorce:  
  
 displayColor = sourceColor × alpha / 255 + backgroundColor × (255 – alfa) / 255  
  
 Předpokládejme například, red součástí zdrojové barvy je 150 a červenou barvu pozadí komponenta je 100. Pokud je alfa hodnota 200, komponentu červenou barvu výsledné se vypočítává takto:  
  
 150 × 200 / 255 + 100 × (255 – 200) / 255 = 139  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: kreslení neprůhledných a poloprůhledných čar](../../../../docs/framework/winforms/advanced/how-to-draw-opaque-and-semitransparent-lines.md)  
 Ukazuje, jak kreslení smíšení alfa čar.  
  
 [Postupy: kreslení pomocí neprůhledných a poloprůhledných štětců](../../../../docs/framework/winforms/advanced/how-to-draw-with-opaque-and-semitransparent-brushes.md)  
 Vysvětluje, jak alpha blend s štětce.  
  
 [Postupy: použití řízení alfa míchání pomocí režimu skládání](../../../../docs/framework/winforms/advanced/how-to-use-compositing-mode-to-control-alpha-blending.md)  
 Popisuje, jak k řízení alfa míchání pomocí <xref:System.Drawing.Drawing2D.CompositingMode>.  
  
 [Postupy: použití matice barev k nastavení alfa hodnot v obrázcích](../../../../docs/framework/winforms/advanced/how-to-use-a-color-matrix-to-set-alpha-values-in-images.md)  
 Vysvětluje, jak používat <xref:System.Drawing.Imaging.ColorMatrix> objektu k řízení alfa míchání.
