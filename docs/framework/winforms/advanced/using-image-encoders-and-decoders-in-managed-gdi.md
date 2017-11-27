---
title: "Použití kodérů a dekodérů ve spravovaném GDI+"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- image encoders [Windows Forms], using
- image decoders [Windows Forms], using
ms.assetid: 0e838ea1-4e7e-4334-b882-ab25df607b8b
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 64384e3c283b6596e36d5b2bd583a304faf080b4
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="using-image-encoders-and-decoders-in-managed-gdi"></a>Použití kodérů a dekodérů ve spravovaném GDI+
<xref:System.Drawing> Obor názvů obsahuje <xref:System.Drawing.Image> a <xref:System.Drawing.Bitmap> třídy pro ukládání a manipulace s nimi bitové kopie. Pomocí kódovací moduly obrázku v [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], můžete napsat bitové kopie z paměti na disk. Pomocí dekódovací moduly obrázku v [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], bitové kopie můžete načíst z disku do paměti. Kodér převádí data v <xref:System.Drawing.Image> nebo <xref:System.Drawing.Bitmap> objekt do formátu souboru určený disk. Dekodér převádí data v souboru na disku na formát vyžadovanou <xref:System.Drawing.Image> a <xref:System.Drawing.Bitmap> objekty.  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]má integrovanou kodérů a dekodérů, které podporují tyto typy souborů:  
  
-   BMP  
  
-   GIF  
  
-   JPEG  
  
-   PNG  
  
-   TIFF  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]také obsahuje integrovanou dekódovací moduly, které podporují tyto typy souborů:  
  
-   WMF  
  
-   EMF  
  
-   IKONA  
  
 Následující témata popisují kodérů a dekodérů podrobněji:  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: vypsání seznamu instalovaných kodérů](../../../../docs/framework/winforms/advanced/how-to-list-installed-encoders.md)  
 Popisuje, jak seznam kodéry, které jsou dostupné v počítači.  
  
 [Postupy: vypsání seznamu instalovaných dekodérů](../../../../docs/framework/winforms/advanced/how-to-list-installed-decoders.md)  
 Popisuje, jak seznam dekodérů dostupné v počítači.  
  
 [Postupy: určení parametrů podporovaných kodérem](../../../../docs/framework/winforms/advanced/how-to-determine-the-parameters-supported-by-an-encoder.md)  
 Popisuje, jak zobrazit seznam <xref:System.Drawing.Imaging.EncoderParameters> podporovaných kodérem.  
  
 [Postupy: převod obrázku Bpm na obrázek na obrázek PNG](../../../../docs/framework/winforms/advanced/how-to-convert-a-bmp-image-to-a-png-image.md)  
 Popisuje, jak uložit obrázek ve formátu, jinou bitovou kopii.  
  
 [Postupy: nastavení úrovně komprese JPEG](../../../../docs/framework/winforms/advanced/how-to-set-jpeg-compression-level.md)  
 Popisuje, jak chcete změnit úroveň kvality obrázku.  
  
## <a name="reference"></a>Odkaz  
 <xref:System.Drawing.Image>  
  
 <xref:System.Drawing.Bitmap>  
  
 <xref:System.Drawing.Imaging.ImageCodecInfo>  
  
 <xref:System.Drawing.Imaging.EncoderParameter>  
  
 <xref:System.Drawing.Imaging.Encoder>  
  
## <a name="related-sections"></a>Související oddíly  
 [O GDI + spravovaný kód](../../../../docs/framework/winforms/advanced/about-gdi-managed-code.md)  
  
 [Obrázky, rastrové obrázky a metasoubory](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)
