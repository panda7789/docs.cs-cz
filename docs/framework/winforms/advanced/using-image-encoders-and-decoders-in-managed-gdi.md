---
title: Použití kodérů a dekodérů ve spravovaném GDI+
ms.date: 03/30/2017
helpviewer_keywords:
- image encoders [Windows Forms], using
- image decoders [Windows Forms], using
ms.assetid: 0e838ea1-4e7e-4334-b882-ab25df607b8b
ms.openlocfilehash: b2e51587209cb4df41ea1fd18ce5c2088ee07a2b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="using-image-encoders-and-decoders-in-managed-gdi"></a>Použití kodérů a dekodérů ve spravovaném GDI+
<xref:System.Drawing> Obor názvů obsahuje <xref:System.Drawing.Image> a <xref:System.Drawing.Bitmap> třídy pro ukládání a manipulace s nimi bitové kopie. Pomocí kódovací moduly obrázku v [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], můžete napsat bitové kopie z paměti na disk. Pomocí dekódovací moduly obrázku v [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], bitové kopie můžete načíst z disku do paměti. Kodér převádí data v <xref:System.Drawing.Image> nebo <xref:System.Drawing.Bitmap> objekt do formátu souboru určený disk. Dekodér převádí data v souboru na disku na formát vyžadovanou <xref:System.Drawing.Image> a <xref:System.Drawing.Bitmap> objekty.  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] má integrovanou kodérů a dekodérů, které podporují tyto typy souborů:  
  
-   BMP  
  
-   GIF  
  
-   JPEG  
  
-   PNG  
  
-   TIFF  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] také obsahuje integrovanou dekódovací moduly, které podporují tyto typy souborů:  
  
-   WMF  
  
-   EMF  
  
-   IKONA  
  
 Následující témata popisují kodérů a dekodérů podrobněji:  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: Vypsání seznamu instalovaných kodérů](../../../../docs/framework/winforms/advanced/how-to-list-installed-encoders.md)  
 Popisuje, jak seznam kodéry, které jsou dostupné v počítači.  
  
 [Postupy: Vypsání seznamu instalovaných dekodérů](../../../../docs/framework/winforms/advanced/how-to-list-installed-decoders.md)  
 Popisuje, jak seznam dekodérů dostupné v počítači.  
  
 [Postupy: Určení parametrů podporovaných kodérem](../../../../docs/framework/winforms/advanced/how-to-determine-the-parameters-supported-by-an-encoder.md)  
 Popisuje, jak zobrazit seznam <xref:System.Drawing.Imaging.EncoderParameters> podporovaných kodérem.  
  
 [Postupy: Převod obrázku BPM na obrázek PNG](../../../../docs/framework/winforms/advanced/how-to-convert-a-bmp-image-to-a-png-image.md)  
 Popisuje, jak uložit obrázek ve formátu, jinou bitovou kopii.  
  
 [Postupy: Nastavení úrovně komprese JPEG](../../../../docs/framework/winforms/advanced/how-to-set-jpeg-compression-level.md)  
 Popisuje, jak chcete změnit úroveň kvality obrázku.  
  
## <a name="reference"></a>Odkaz  
 <xref:System.Drawing.Image>  
  
 <xref:System.Drawing.Bitmap>  
  
 <xref:System.Drawing.Imaging.ImageCodecInfo>  
  
 <xref:System.Drawing.Imaging.EncoderParameter>  
  
 <xref:System.Drawing.Imaging.Encoder>  
  
## <a name="related-sections"></a>Související oddíly  
 [Informace o spravovaném kódu GDI+](../../../../docs/framework/winforms/advanced/about-gdi-managed-code.md)  
  
 [Obrázky, rastrové obrázky a metasoubory](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)
