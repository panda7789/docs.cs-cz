---
title: Použití štětce přechodu k vyplnění obrazců
ms.date: 03/30/2017
helpviewer_keywords:
- brushes [Windows Forms], gradient brushes
- gradient brushes
- examples [Windows Forms], gradient brushes
ms.assetid: 2c6037b9-05bd-44c0-a22a-19584b722524
ms.openlocfilehash: 7ff555ba4fd81e9123e5f9e9feed38a0ec9d0a08
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2019
ms.locfileid: "65063595"
---
# <a name="using-a-gradient-brush-to-fill-shapes"></a>Použití štětce přechodu k vyplnění obrazců
Můžete použít štětce přechodu k vyplnění obrazce postupně měnící barvou. Například můžete použít vodorovný přechodu k vyplnění obrazce pomocí barev, která se mění postupně při přesunu z levého okraje tvaru do pravého okraje. Představte si obdélníku s levého okraje, která je černá (reprezentovaný identifikátorem komponenty červené, zelené a modré 0, 0, 0) a pravý okraj, který je red (reprezentovaný identifikátorem 255, 0, 0). Pokud obdélníku je 256 pixelů na šířku, bude hodnota červené dané pixelu větší než hodnota červené pixelu na levé straně. Úplně vlevo obrazových bodů za sebou má barevným (0, 0, 0), je druhý pixel má (1, 0, 0), třetí pixel má (2, 0, 0) a tak dále, dokud se nedostanete na úplně vpravo pixel, který má barevným (255, 0, 0). Tyto hodnoty interpolovaná barva tvoří barev přechodu.  
  
 Lineární přechod změní barvu, jak přesunout vodorovně, svisle, nebo paralelní na určený řádek zkosené. Cesty přechodu změní barvu při přesunu o vnitřních a hranice cesty. Můžete přizpůsobit cesty přechodu k dosažení širokou škálu účinky.  
  
 Následující obrázek znázorňuje obdélník vyplněny štětec lineárního přechodu a elipsa se štětce přechodu cesty:  
  
 ![Obdélník vyplněny štětce přechodu s elipsu.](./media/using-a-gradient-brush-to-fill-shapes/rectangle-ellipse-gradient-brush.png)  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: Vytvoření lineárního přechodu](how-to-create-a-linear-gradient.md)  
 Ukazuje, jak vytvořit lineárního přechodu pomocí <xref:System.Drawing.Drawing2D.LinearGradientBrush> třídy.  
  
 [Postupy: Vytvoření přechodu cesty](how-to-create-a-path-gradient.md)  
 Popisuje, jak vytvořit cestu přechodu pomocí <xref:System.Drawing.Drawing2D.PathGradientBrush> třídy.  
  
 [Postupy: Použití gama korekce na přechod](how-to-apply-gamma-correction-to-a-gradient.md)  
 Vysvětluje způsob použití gama korekce s štětce přechodu.  
  
## <a name="reference"></a>Odkaz  
 <xref:System.Drawing.Drawing2D.LinearGradientBrush?displayProperty=nameWithType>  
 Obsahuje popis této třídy a obsahuje odkazy na všechny její členy.  
  
 <xref:System.Drawing.Drawing2D.PathGradientBrush?displayProperty=nameWithType>  
 Obsahuje popis této třídy a obsahuje odkazy na všechny její členy.
