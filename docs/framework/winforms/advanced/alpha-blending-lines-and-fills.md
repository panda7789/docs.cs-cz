---
title: Alfa míchání čar a výplní
ms.date: 03/30/2017
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
ms.openlocfilehash: 66061341ee6539e2172c537a0b2a6ec9ff87565c
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2019
ms.locfileid: "67506120"
---
# <a name="alpha-blending-lines-and-fills"></a>Alfa míchání čar a výplní
V rozhraní GDI + je barva hodnotu 32 bitů s 8 bity pro platformu alpha, červené, zelené a modré. Určuje hodnotu alfa průhlednost barvy – v rozsahu, do které jsou prolnuty barva barvou pozadí. Hodnoty alfa v rozmezí 0 až 255, kde 0 představuje plně průhlednou barvu, a 255 představuje barvu úplně neprůhledné.  
  
 Alfa míchání je – obrazový prolnutí data o barvách zdroj a na pozadí. Všechny tři komponenty (červená, zelená, modrá) barvu daného zdroje jsou prolnuty pomocí odpovídající komponenty barvu pozadí podle následující vzorec:  
  
 displayColor = sourceColor × alfa / 255 + x backgroundColor (255 – alfa) / 255  
  
 Předpokládejme například, hodnota červené ze zdrojové barvy je 150 a červené barvu pozadí je 100. Pokud je hodnota alpha 200, červené výsledné barvy se vypočítává takto:  
  
 150 × 200 / 255 + 100 × (255 – 200) / 255 = 139  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: Kreslení neprůhledných a poloprůhledných čar](how-to-draw-opaque-and-semitransparent-lines.md)  
 Ukazuje, jak kreslení čar prolnutí alfa.  
  
 [Postupy: Kreslení pomocí neprůhledných a poloprůhledných štětců](how-to-draw-with-opaque-and-semitransparent-brushes.md)  
 Vysvětluje, jak pomocí štětců prolnutí alfa.  
  
 [Postupy: Pomocí řízení funkce alfa Blending pomocí režimu skládání](how-to-use-compositing-mode-to-control-alpha-blending.md)  
 Popisuje, jak řízení alfa míchání pomocí <xref:System.Drawing.Drawing2D.CompositingMode>.  
  
 [Postupy: Použití matice barev k nastavení alfa hodnot v obrázcích](how-to-use-a-color-matrix-to-set-alpha-values-in-images.md)  
 Vysvětluje způsob používání <xref:System.Drawing.Imaging.ColorMatrix> objekt pro řízení alfa míchání.
