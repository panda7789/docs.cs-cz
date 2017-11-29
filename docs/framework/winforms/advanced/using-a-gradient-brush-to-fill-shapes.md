---
title: "Použití štětce přechodu k vyplnění obrazců"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- brushes [Windows Forms], gradient brushes
- gradient brushes
- examples [Windows Forms], gradient brushes
ms.assetid: 2c6037b9-05bd-44c0-a22a-19584b722524
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5a1c4ab7c2ee6f7164b6158dcb4ca4721be12650
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="using-a-gradient-brush-to-fill-shapes"></a>Použití štětce přechodu k vyplnění obrazců
Můžete štětce přechodu k vyplnění obrazce postupně změna barvou. Například můžete vodorovné přechodu k vyplnění obrazce s barvu, která postupně změní, když přesouváte od levého okraje tvaru na pravý okraj. Představte si obdélníku s levý okraj, který je černé (znázorněná červené, zelené a modré součásti 0, 0, 0) a pravý okraj, který je červený (představované 255, 0, 0). Pokud rámeček je 256 pixelů, bude jeden znak větší než red součást pixelů na levé straně, red součást dané pixelů. Krajní levé pixelů v řádku obsahuje součásti barvu (0, 0, 0), druhý pixelů má (1, 0, 0), třetí pixelů má (2, 0, 0) a tak dále, dokud se nedostanete do úplně vpravo pixelů, která má součásti barvu (255, 0, 0). Tyto hodnoty interpolované barva tvoří přechod barev.  
  
 Lineárního přechodu změní barvu jako přesunout vodorovně, svisle nebo paralelní na zadaný zkosené řádek. Přechodu cesty změní barvu, když přesouváte o interior a hranic cesty. Cesty přechodu k dosažení širokou škálu důsledky můžete přizpůsobit.  
  
 Následující obrázek znázorňuje obdélníku, naplní se lineární štětce přechodu a elipsy plná štětce přechodu cesty.  
  
 ![Přechodu](../../../../docs/framework/winforms/advanced/media/gradient2.png "gradient2")  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: vytvoření lineárního přechodu](../../../../docs/framework/winforms/advanced/how-to-create-a-linear-gradient.md)  
 Ukazuje postup vytvoření lineárního přechodu pomocí <xref:System.Drawing.Drawing2D.LinearGradientBrush> třídy.  
  
 [Postupy: vytvoření přechodu cesty](../../../../docs/framework/winforms/advanced/how-to-create-a-path-gradient.md)  
 Popisuje postup vytvoření přechodu cesty pomocí <xref:System.Drawing.Drawing2D.PathGradientBrush> třídy.  
  
 [Postupy: použití gama korekce na přechod](../../../../docs/framework/winforms/advanced/how-to-apply-gamma-correction-to-a-gradient.md)  
 Vysvětluje, jak používat korekce gama s štětce přechodu.  
  
## <a name="reference"></a>Odkaz  
 <xref:System.Drawing.Drawing2D.LinearGradientBrush?displayProperty=nameWithType>  
 Obsahuje popis této třídy a obsahuje odkazy na všechny její členy.  
  
 <xref:System.Drawing.Drawing2D.PathGradientBrush?displayProperty=nameWithType>  
 Obsahuje popis této třídy a obsahuje odkazy na všechny její členy.
