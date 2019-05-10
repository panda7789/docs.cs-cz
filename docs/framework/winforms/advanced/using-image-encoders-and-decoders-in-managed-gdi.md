---
title: Použití kodérů a dekodérů ve spravovaném GDI+
ms.date: 03/30/2017
helpviewer_keywords:
- image encoders [Windows Forms], using
- image decoders [Windows Forms], using
ms.assetid: 0e838ea1-4e7e-4334-b882-ab25df607b8b
ms.openlocfilehash: e56bc20eb55d694d19b25d9e94e5c9d9e3952628
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64666446"
---
# <a name="using-image-encoders-and-decoders-in-managed-gdi"></a>Použití kodérů a dekodérů ve spravovaném GDI+
<xref:System.Drawing> Obor názvů poskytuje <xref:System.Drawing.Image> a <xref:System.Drawing.Bitmap> třídy pro ukládání a manipulaci s obrázky. S použitím kodérů v [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], můžete zaznamenat bitové kopie z paměti na disk. S použitím dekódovací moduly obrázku v [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], můžete načíst obrázky z disku do paměti. Kodér převádí data do <xref:System.Drawing.Image> nebo <xref:System.Drawing.Bitmap> objektu do souboru ve formátu určený disk. Dekodér převádí data v souboru na disku na formát vyžadované <xref:System.Drawing.Image> a <xref:System.Drawing.Bitmap> objekty.  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] má integrovanou kodérů a dekodérů, které podporují následující typy souborů:  
  
- BMP  
  
- GIF  
  
- JPEG  
  
- PNG  
  
- TIFF  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] obsahuje také integrované dekodérů, které podporují následující typy souborů:  
  
- WMF  
  
- EMF  
  
- IKONA  
  
 Následující témata popisují kodérů a dekodérů podrobněji:  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: Vypsání seznamu instalovaných kodérů](how-to-list-installed-encoders.md)  
 Popisuje, jak zobrazit seznam u kodérů dostupných na počítači.  
  
 [Postupy: Vypsání seznamu instalovaných dekodérů](how-to-list-installed-decoders.md)  
 Popisuje, jak zobrazit seznam dostupných na počítači dekodérů.  
  
 [Postupy: Určuje parametry podporuje kodéru](how-to-determine-the-parameters-supported-by-an-encoder.md)  
 Popisuje, jak zobrazit seznam <xref:System.Drawing.Imaging.EncoderParameters> podporuje kodéru.  
  
 [Postupy: Převod obrázku Bpm na obrázek PNG](how-to-convert-a-bmp-image-to-a-png-image.md)  
 Popisuje, jak uložit do image ve formátu jiný obrázek.  
  
 [Postupy: Nastavení úrovně komprese JPEG](how-to-set-jpeg-compression-level.md)  
 Popisuje, jak změnit úroveň kvality obrázku.  
  
## <a name="reference"></a>Odkaz  
 <xref:System.Drawing.Image>  
  
 <xref:System.Drawing.Bitmap>  
  
 <xref:System.Drawing.Imaging.ImageCodecInfo>  
  
 <xref:System.Drawing.Imaging.EncoderParameter>  
  
 <xref:System.Drawing.Imaging.Encoder>  
  
## <a name="related-sections"></a>Související oddíly  
 [Informace o spravovaném kódu GDI+](about-gdi-managed-code.md)  
  
 [Obrázky, rastrové obrázky a metasoubory](images-bitmaps-and-metafiles.md)
